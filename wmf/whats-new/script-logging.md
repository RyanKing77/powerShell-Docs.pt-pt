---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Registo e Rastreio de Scripts
ms.openlocfilehash: 6b7e5022cb4c974da5ddb3d670b5808dc9fb7bdc
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856155"
---
# <a name="script-tracing-and-logging"></a>Registo e Rastreio de Scripts

Enquanto PowerShell já tem o **LogPipelineExecutionDetails** diretiva de grupo na definição de invocação de cmdlets de registo, o linguagem de script do PowerShell que possui vários recursos que pode querer iniciar sessão e de auditoria. O novo recurso de rastreamento detalhadas de Script fornece detalhadas de controlo e a análise da atividade de script do PowerShell num sistema. Depois de ativar o rastreio de detalhado de script, PowerShell regista todos os blocos de script para o registo de eventos do ETW **Microsoft-Windows-PowerShell/Operational**. Se um bloco de scripts cria outro bloco de scripts, por exemplo, ao chamar `Invoke-Expression`, o bloco de script invocado também registada.

O registo está ativado por meio da **ativar o registo de bloco de Script do PowerShell** definição de política de grupo na **modelos administrativos** -> **componentes do Windows**  ->  **Windows PowerShell**.

Os eventos são:

| Canal |                               Operacional                               |
| ------- | ----------------------------------------------------------------------- |
| Nível   | Verbose                                                                 |
| Opcode  | Criar                                                                  |
| Tarefa    | CommandStart                                                            |
| Palavra-chave | espaço de execução                                                                |
| EventId | Engine_ScriptBlockCompiled (0x1008 = 4104)                              |
| Mensagem | Criação de texto de Scriptblock (%1 de %2): </br> %3 </br> ID de ScriptBlock: %4 |


O texto incorporado na mensagem é a extensão do bloco de script compilado. O ID é um GUID que é retido durante o ciclo de vida do bloco de script.

Quando ativar o registo verboso, as gravações de funcionalidade begin e end marcadores:

| Canal |                                 Operacional                                |
| ------- | -------------------------------------------------------------------------- |
| Nível   | Verbose                                                                    |
| Opcode  | Abrir / fechar                                                               |
| Tarefa    | CommandStart / CommandStop                                                 |
| Palavra-chave | espaço de execução                                                                   |
| EventId | O ScriptBlock\_invocar\_iniciar\_detalhes (0x1009 = 4105) / </br> O ScriptBlock\_invocar\_completa\_detalhes (0x100A = 4106) |
| Mensagem | Iniciou / concluída a invocação do ID de ScriptBlock: %1 </br> ID do espaço de execução: %2 |

O ID é o GUID que representa o bloco de script (que pode ser correlacionado com o ID de evento 0x1008) e o ID do espaço de execução representa o espaço de execução no qual este bloco de script foi executado.

Símbolos de percentagem na mensagem de invocação representam estruturadas propriedades ETW. Enquanto são substituídos pelos valores reais no texto da mensagem, uma maneira mais robusta para aceder aos mesmos é obter a mensagem com o cmdlet Get-WinEvent e, em seguida, utilizar o **propriedades** matriz da mensagem.

Eis um exemplo de como essa funcionalidade pode ajudar a anular a moldagem de uma tentativa de maliciosa para encriptar e oculte um script:

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)
}

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

Executando isso gera as seguintes entradas de registo:

```Output
Compiling Scriptblock text (1 of 1):
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)
    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)

}
ScriptBlock ID: ad8ae740-1f33-42aa-8dfc-1314411877e3

Compiling Scriptblock text (1 of 1):
$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
ScriptBlock ID: ba11c155-d34c-4004-88e3-6502ecb50f52

Compiling Scriptblock text (1 of 1):
Invoke-Expression $decrypted
ScriptBlock ID: 856c01ca-85d7-4989-b47f-e6a09ee4eeb3

Compiling Scriptblock text (1 of 1):
Write-Host 'Pwnd'
ScriptBlock ID: 5e618414-4e77-48e3-8f65-9a863f54b4c8
```

Se o tamanho do bloco de script exceder a capacidade de um único evento, o PowerShell divide o script em várias partes. Aqui está o código de exemplo para voltar um script de suas mensagens de registo:

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

Tal como acontece com todos os sistemas de Registro em log com um buffer de retenção limitada, uma forma de atacar esta infraestrutura é inundar o registo com eventos falsos para ocultar evidências anteriores. Para proteger-se contra este ataque, certifique-se de que tem alguma forma de configurar o reencaminhamento de eventos do Windows de recolha de registos de eventos. Para obter mais informações, consulte [detetar o adversário com a monitorização de registo de eventos do Windows](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).