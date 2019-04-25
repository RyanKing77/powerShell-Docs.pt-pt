---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 28cd186ab3a08a0da4ff81f5a21514f239770d13
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058085"
---
# <a name="script-tracing-and-logging"></a>Registo e Rastreio de Scripts

Embora o Windows PowerShell já tem o **LogPipelineExecutionDetails** diretiva de grupo na definição de registo a invocação dos cmdlets, linguagem de script do PowerShell tem muitas funcionalidades que pode querer iniciar e/ou de auditoria. O novo recurso de rastreamento detalhadas de Script permite-lhe ativar o controlo detalhado e análise de utilização de criação de scripts de Windows PowerShell num sistema. Depois de ativar o rastreio de detalhado de script, Windows PowerShell regista todos os blocos de script para o registo de eventos do ETW **Microsoft-Windows-PowerShell/Operational**. Se um bloco de scripts cria outro bloco de script (por exemplo, um script que chama o cmdlet Invoke-Expression numa cadeia de caracteres), esse bloco de script resultante é registado também.

O registo desses eventos pode ser ativado através da **ativar o registo de bloco de Script do PowerShell** definição de política de grupo (modelos administrativos -> componentes do Windows -> Windows PowerShell).

Os eventos são:

| Canal | Operacional                                 |
|---------|---------------------------------------------|
| Nível   | Verboso                                     |
| Opcode  | Criar                                      |
| Tarefa    | CommandStart                                |
| Palavra-chave | espaço de execução                                    |
| EventId | Engine_ScriptBlockCompiled (0x1008 = 4104)  |
| Mensagem | Criação de texto de Scriptblock (%1 de %2): </br> %3 </br> ID de ScriptBlock: %4 |


O texto incorporado na mensagem é a extensão do bloco de script compilado. O ID é um GUID que é retido durante o ciclo de vida do bloco de script.

Quando ativar o registo verboso, as gravações de funcionalidade begin e end marcadores:

| Canal | Operacional                                            |
|---------|--------------------------------------------------------|
| Nível   | Verboso                                                |
| Opcode  | Abrir (/ Fechar)                                         |
| Tarefa    | CommandStart (/ CommandStop)                           |
| Palavra-chave | espaço de execução                                               |
| EventId | O ScriptBlock\_invocar\_iniciar\_detalhes (0x1009 = 4105) / </br> O ScriptBlock\_invocar\_completa\_detalhes (0x100A = 4106) |
| Mensagem | Invocação de introdução (/ concluída) do ID de ScriptBlock: %1 </br> ID do espaço de execução: %2 |

O ID é o GUID que representa o bloco de script (que pode ser correlacionado com o ID de evento 0x1008) e o ID do espaço de execução representa o espaço de execução no qual este bloco de script foi executado.

Símbolos de percentagem na mensagem de invocação representam estruturadas propriedades ETW. Enquanto são substituídos pelos valores reais no texto da mensagem, uma maneira mais robusta para aceder aos mesmos é obter a mensagem com o cmdlet Get-WinEvent e, em seguida, utilizar o **propriedades** matriz da mensagem.

Eis um exemplo de como essa funcionalidade pode ajudar a anular a moldagem de uma tentativa de maliciosa para encriptar e oculte um script:

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR “encryption”
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

```
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

Se o tamanho do bloco de script exceder o que é capaz de retenção num único evento ETW, o Windows PowerShell divide o script em várias partes. Aqui está o código de exemplo para voltar um script de suas mensagens de registo:

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

Tal como acontece com todos os sistemas de Registro em log com um buffer de retenção limitado (ou seja, os registos ETW), um ataque contra esta infraestrutura é inundar o registo com eventos falsos para ocultar evidências anteriores. Para proteger-se contra este ataque, certifique-se de que tem alguma forma de configurar de recolha de registos de eventos (ou seja, Windows reencaminhamento de eventos, [detetar o adversário com a monitorização de registo de eventos do Windows](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) para mover os logs de eventos logoff no computador como mais rapidamente possível.
