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
# <a name="script-tracing-and-logging"></a><span data-ttu-id="7df25-102">Registo e Rastreio de Scripts</span><span class="sxs-lookup"><span data-stu-id="7df25-102">Script Tracing and Logging</span></span>

<span data-ttu-id="7df25-103">Embora o Windows PowerShell já tem o **LogPipelineExecutionDetails** diretiva de grupo na definição de registo a invocação dos cmdlets, linguagem de script do PowerShell tem muitas funcionalidades que pode querer iniciar e/ou de auditoria.</span><span class="sxs-lookup"><span data-stu-id="7df25-103">While Windows PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell’s scripting language has plenty of features that you might want to log and/or audit.</span></span> <span data-ttu-id="7df25-104">O novo recurso de rastreamento detalhadas de Script permite-lhe ativar o controlo detalhado e análise de utilização de criação de scripts de Windows PowerShell num sistema.</span><span class="sxs-lookup"><span data-stu-id="7df25-104">The new Detailed Script Tracing feature lets you enable detailed tracking and analysis of Windows PowerShell scripting use on a system.</span></span> <span data-ttu-id="7df25-105">Depois de ativar o rastreio de detalhado de script, Windows PowerShell regista todos os blocos de script para o registo de eventos do ETW **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="7df25-105">After you enable detailed script tracing, Windows PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="7df25-106">Se um bloco de scripts cria outro bloco de script (por exemplo, um script que chama o cmdlet Invoke-Expression numa cadeia de caracteres), esse bloco de script resultante é registado também.</span><span class="sxs-lookup"><span data-stu-id="7df25-106">If a script block creates another script block (for example, a script that calls the Invoke-Expression cmdlet on a string), that resulting script block is logged as well.</span></span>

<span data-ttu-id="7df25-107">O registo desses eventos pode ser ativado através da **ativar o registo de bloco de Script do PowerShell** definição de política de grupo (modelos administrativos -> componentes do Windows -> Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="7df25-107">Logging of these events can be enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting (in Administrative Templates -> Windows Components -> Windows PowerShell).</span></span>

<span data-ttu-id="7df25-108">Os eventos são:</span><span class="sxs-lookup"><span data-stu-id="7df25-108">The events are:</span></span>

| <span data-ttu-id="7df25-109">Canal</span><span class="sxs-lookup"><span data-stu-id="7df25-109">Channel</span></span> | <span data-ttu-id="7df25-110">Operacional</span><span class="sxs-lookup"><span data-stu-id="7df25-110">Operational</span></span>                                 |
|---------|---------------------------------------------|
| <span data-ttu-id="7df25-111">Nível</span><span class="sxs-lookup"><span data-stu-id="7df25-111">Level</span></span>   | <span data-ttu-id="7df25-112">Verboso</span><span class="sxs-lookup"><span data-stu-id="7df25-112">Verbose</span></span>                                     |
| <span data-ttu-id="7df25-113">Opcode</span><span class="sxs-lookup"><span data-stu-id="7df25-113">Opcode</span></span>  | <span data-ttu-id="7df25-114">Criar</span><span class="sxs-lookup"><span data-stu-id="7df25-114">Create</span></span>                                      |
| <span data-ttu-id="7df25-115">Tarefa</span><span class="sxs-lookup"><span data-stu-id="7df25-115">Task</span></span>    | <span data-ttu-id="7df25-116">CommandStart</span><span class="sxs-lookup"><span data-stu-id="7df25-116">CommandStart</span></span>                                |
| <span data-ttu-id="7df25-117">Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="7df25-117">Keyword</span></span> | <span data-ttu-id="7df25-118">espaço de execução</span><span class="sxs-lookup"><span data-stu-id="7df25-118">Runspace</span></span>                                    |
| <span data-ttu-id="7df25-119">EventId</span><span class="sxs-lookup"><span data-stu-id="7df25-119">EventId</span></span> | <span data-ttu-id="7df25-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="7df25-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>  |
| <span data-ttu-id="7df25-121">Mensagem</span><span class="sxs-lookup"><span data-stu-id="7df25-121">Message</span></span> | <span data-ttu-id="7df25-122">Criação de texto de Scriptblock (%1 de %2):</span><span class="sxs-lookup"><span data-stu-id="7df25-122">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="7df25-123">%3</span><span class="sxs-lookup"><span data-stu-id="7df25-123">%3</span></span> </br> <span data-ttu-id="7df25-124">ID de ScriptBlock: %4</span><span class="sxs-lookup"><span data-stu-id="7df25-124">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="7df25-125">O texto incorporado na mensagem é a extensão do bloco de script compilado.</span><span class="sxs-lookup"><span data-stu-id="7df25-125">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="7df25-126">O ID é um GUID que é retido durante o ciclo de vida do bloco de script.</span><span class="sxs-lookup"><span data-stu-id="7df25-126">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="7df25-127">Quando ativar o registo verboso, as gravações de funcionalidade begin e end marcadores:</span><span class="sxs-lookup"><span data-stu-id="7df25-127">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="7df25-128">Canal</span><span class="sxs-lookup"><span data-stu-id="7df25-128">Channel</span></span> | <span data-ttu-id="7df25-129">Operacional</span><span class="sxs-lookup"><span data-stu-id="7df25-129">Operational</span></span>                                            |
|---------|--------------------------------------------------------|
| <span data-ttu-id="7df25-130">Nível</span><span class="sxs-lookup"><span data-stu-id="7df25-130">Level</span></span>   | <span data-ttu-id="7df25-131">Verboso</span><span class="sxs-lookup"><span data-stu-id="7df25-131">Verbose</span></span>                                                |
| <span data-ttu-id="7df25-132">Opcode</span><span class="sxs-lookup"><span data-stu-id="7df25-132">Opcode</span></span>  | <span data-ttu-id="7df25-133">Abrir (/ Fechar)</span><span class="sxs-lookup"><span data-stu-id="7df25-133">Open (/ Close)</span></span>                                         |
| <span data-ttu-id="7df25-134">Tarefa</span><span class="sxs-lookup"><span data-stu-id="7df25-134">Task</span></span>    | <span data-ttu-id="7df25-135">CommandStart (/ CommandStop)</span><span class="sxs-lookup"><span data-stu-id="7df25-135">CommandStart (/ CommandStop)</span></span>                           |
| <span data-ttu-id="7df25-136">Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="7df25-136">Keyword</span></span> | <span data-ttu-id="7df25-137">espaço de execução</span><span class="sxs-lookup"><span data-stu-id="7df25-137">Runspace</span></span>                                               |
| <span data-ttu-id="7df25-138">EventId</span><span class="sxs-lookup"><span data-stu-id="7df25-138">EventId</span></span> | <span data-ttu-id="7df25-139">O ScriptBlock\_invocar\_iniciar\_detalhes (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="7df25-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="7df25-140">O ScriptBlock\_invocar\_completa\_detalhes (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="7df25-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="7df25-141">Mensagem</span><span class="sxs-lookup"><span data-stu-id="7df25-141">Message</span></span> | <span data-ttu-id="7df25-142">Invocação de introdução (/ concluída) do ID de ScriptBlock: %1</span><span class="sxs-lookup"><span data-stu-id="7df25-142">Started (/ Completed) invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="7df25-143">ID do espaço de execução: %2</span><span class="sxs-lookup"><span data-stu-id="7df25-143">Runspace ID: %2</span></span> |

<span data-ttu-id="7df25-144">O ID é o GUID que representa o bloco de script (que pode ser correlacionado com o ID de evento 0x1008) e o ID do espaço de execução representa o espaço de execução no qual este bloco de script foi executado.</span><span class="sxs-lookup"><span data-stu-id="7df25-144">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="7df25-145">Símbolos de percentagem na mensagem de invocação representam estruturadas propriedades ETW.</span><span class="sxs-lookup"><span data-stu-id="7df25-145">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="7df25-146">Enquanto são substituídos pelos valores reais no texto da mensagem, uma maneira mais robusta para aceder aos mesmos é obter a mensagem com o cmdlet Get-WinEvent e, em seguida, utilizar o **propriedades** matriz da mensagem.</span><span class="sxs-lookup"><span data-stu-id="7df25-146">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="7df25-147">Eis um exemplo de como essa funcionalidade pode ajudar a anular a moldagem de uma tentativa de maliciosa para encriptar e oculte um script:</span><span class="sxs-lookup"><span data-stu-id="7df25-147">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

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

<span data-ttu-id="7df25-148">Executando isso gera as seguintes entradas de registo:</span><span class="sxs-lookup"><span data-stu-id="7df25-148">Running this generates the following log entries:</span></span>

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

Se o tamanho do bloco de script exceder o que é capaz de retenção num único evento ETW, o Windows PowerShell divide o script em várias partes. <span data-ttu-id="7df25-150">Aqui está o código de exemplo para voltar um script de suas mensagens de registo:</span><span class="sxs-lookup"><span data-stu-id="7df25-150">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="7df25-151">Tal como acontece com todos os sistemas de Registro em log com um buffer de retenção limitado (ou seja, os registos ETW), um ataque contra esta infraestrutura é inundar o registo com eventos falsos para ocultar evidências anteriores.</span><span class="sxs-lookup"><span data-stu-id="7df25-151">As with all logging systems that have a limited retention buffer (i.e. ETW logs), one attack against this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="7df25-152">Para proteger-se contra este ataque, certifique-se de que tem alguma forma de configurar de recolha de registos de eventos (ou seja, Windows reencaminhamento de eventos, [detetar o adversário com a monitorização de registo de eventos do Windows](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) para mover os logs de eventos logoff no computador como mais rapidamente possível.</span><span class="sxs-lookup"><span data-stu-id="7df25-152">To protect yourself from this attack, ensure that you have some form of event log collection set up (i.e., Windows Event Forwarding, [Spotting the Adversary with Windows Event Log Monitoring](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) to move event logs off of the computer as soon as possible.</span></span>
