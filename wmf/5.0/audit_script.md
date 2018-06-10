---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: b8f175cee0a1de501b64890fdc2798f4f6421a14
ms.sourcegitcommit: 2ffb9fa92129c2001379ca2c17646466721f7165
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251488"
---
# <a name="script-tracing-and-logging"></a>Registo e Rastreio de Scripts

Enquanto o Windows PowerShell já tem o **LogPipelineExecutionDetails** política de grupo de definições a invocação dos cmdlets de registo, linguagem de script do PowerShell tem muitos das funcionalidades que pode querer iniciar sessão e/ou de auditoria. A nova funcionalidade de rastreio de Script de detalhado permite-lhe ativar análise de utilização de script do Windows PowerShell num sistema e detalhadas de controlo. Depois de ativar o rastreio de script detalhado, do Windows PowerShell regista todos os blocos de script para o registo de eventos do ETW, **Microsoft-Windows-PowerShell/Operational**. Se um bloco de script cria outro bloco de script (por exemplo, um script que chama o cmdlet Invoke-Expression numa cadeia), bloco script resultante é registado bem.

Registar estes eventos pode ser ativado através de **ativar o registo de bloco de Script do PowerShell** definição de política de grupo (modelos administrativos -> componentes do Windows -> Windows PowerShell).

Os eventos são:

| Canal | Operacional                                 |
|---------|---------------------------------------------|
| Nível   | Verbose                                     |
| Opcode  | Criar                                      |
| Tarefa    | CommandStart                                |
| Palavra-chave | Espaço de execução                                    |
| EventId | Engine_ScriptBlockCompiled (0x1008 = 4104)  |
| Mensagem | Criar Scriptblock texto (%1 de %2): </br> %3 </br> ID de ScriptBlock: %4 |


O texto incorporado na mensagem é o grau de bloco de script compilado. O ID é um GUID que é mantido durante a vigência de bloco de script.

Quando ativar o registo verboso, as escritas de funcionalidade começarem e terminar marcadores:

| Canal | Operacional                                            |
|---------|--------------------------------------------------------|
| Nível   | Verbose                                                |
| Opcode  | Abrir (/ Fechar)                                         |
| Tarefa    | CommandStart (/ CommandStop)                           |
| Palavra-chave | Espaço de execução                                               |
| EventId | O ScriptBlock\_invocar\_iniciar\_detalhe (0x1009 = 4105) / </br> O ScriptBlock\_invocar\_concluída\_detalhe (0x100A = 4106) |
| Mensagem | Invocação de introdução (/ concluída) do ID de ScriptBlock: %1 </br> ID de espaço de execução: %2 |

O ID é o GUID que representa o bloco de script (o que pode ser correlacionado com o ID de evento 0x1008) e o ID de espaço de execução representa o espaço de execução no qual este bloco de script foi executado.

Percentagem sinais na mensagem de invocação representam as propriedades ETW structured. Enquanto são substituídos por valores reais no texto da mensagem, uma forma mais robusta para aceder aos mesmos é obter a mensagem com o cmdlet Get-WinEvent e, em seguida, utilizar o **propriedades** matriz da mensagem.

Eis um exemplo de como esta funcionalidade pode ajudá-lo a desenrolar uma tentativa de maliciosa para encriptar e obfuscate um script:

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

Executar Isto gera as entradas de registo seguinte:

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

Se o comprimento do bloco de script exceder o que é capaz de retenção num único evento ETW, o Windows PowerShell interrompe o script em várias partes. Eis o código de exemplo para recombine um script no respetivos mensagens de registo:

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

Tal como acontece com todos os sistemas de registo que tenham uma retenção limitada de memória intermédia (ou seja, registos ETW), um ataque contra esta infraestrutura é inundar o registo de eventos spurious para ocultar provas anterior. Para proteger-se contra este ataque, certifique-se de que tem alguma forma de recolha de registos de eventos de multimédia (ou seja, Windows reencaminhamento de eventos, [Spotting o adversário com a monitorização de registo de eventos do Windows](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) para mover os registos de eventos retire o computador como logo que possível.
