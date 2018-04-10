---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: b440ea4a8208d5c576fa566a19e2de377bf5f475
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="bd1cb-102">Registo e Rastreio de Scripts</span><span class="sxs-lookup"><span data-stu-id="bd1cb-102">Script Tracing and Logging</span></span>

<span data-ttu-id="bd1cb-103">Enquanto o Windows PowerShell já tem o **LogPipelineExecutionDetails** política de grupo de definições a invocação dos cmdlets de registo, linguagem de script do PowerShell tem muitos das funcionalidades que pode querer iniciar sessão e/ou de auditoria.</span><span class="sxs-lookup"><span data-stu-id="bd1cb-103">While Windows PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell’s scripting language has plenty of features that you might want to log and/or audit.</span></span> <span data-ttu-id="bd1cb-104">A nova funcionalidade de rastreio de Script de detalhado permite-lhe ativar análise de utilização de script do Windows PowerShell num sistema e detalhadas de controlo.</span><span class="sxs-lookup"><span data-stu-id="bd1cb-104">The new Detailed Script Tracing feature lets you enable detailed tracking and analysis of Windows PowerShell scripting use on a system.</span></span> <span data-ttu-id="bd1cb-105">Depois de ativar o rastreio de script detalhado, do Windows PowerShell regista todos os blocos de script para o registo de eventos do ETW, **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="bd1cb-105">After you enable detailed script tracing, Windows PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="bd1cb-106">Se um bloco de script cria outro bloco de script (por exemplo, um script que chama o cmdlet Invoke-Expression numa cadeia), bloco script resultante é registado bem.</span><span class="sxs-lookup"><span data-stu-id="bd1cb-106">If a script block creates another script block (for example, a script that calls the Invoke-Expression cmdlet on a string), that resulting script block is logged as well.</span></span>

<span data-ttu-id="bd1cb-107">Registar estes eventos pode ser ativado através de **ativar o registo de bloco de Script do PowerShell** definição de política de grupo (modelos administrativos -> componentes do Windows -> Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="bd1cb-107">Logging of these events can be enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting (in Administrative Templates -> Windows Components -> Windows PowerShell).</span></span>

<span data-ttu-id="bd1cb-108">Os eventos são:</span><span class="sxs-lookup"><span data-stu-id="bd1cb-108">The events are:</span></span>

| <span data-ttu-id="bd1cb-109">Canal</span><span class="sxs-lookup"><span data-stu-id="bd1cb-109">Channel</span></span> | <span data-ttu-id="bd1cb-110">Operacional</span><span class="sxs-lookup"><span data-stu-id="bd1cb-110">Operational</span></span>                                 |
|---------|---------------------------------------------|
| <span data-ttu-id="bd1cb-111">Nível</span><span class="sxs-lookup"><span data-stu-id="bd1cb-111">Level</span></span>   | <span data-ttu-id="bd1cb-112">Verbose</span><span class="sxs-lookup"><span data-stu-id="bd1cb-112">Verbose</span></span>                                     |
| <span data-ttu-id="bd1cb-113">Opcode</span><span class="sxs-lookup"><span data-stu-id="bd1cb-113">Opcode</span></span>  | <span data-ttu-id="bd1cb-114">Criar</span><span class="sxs-lookup"><span data-stu-id="bd1cb-114">Create</span></span>                                      |
| <span data-ttu-id="bd1cb-115">Tarefa</span><span class="sxs-lookup"><span data-stu-id="bd1cb-115">Task</span></span>    | <span data-ttu-id="bd1cb-116">CommandStart</span><span class="sxs-lookup"><span data-stu-id="bd1cb-116">CommandStart</span></span>                                |
| <span data-ttu-id="bd1cb-117">Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="bd1cb-117">Keyword</span></span> | <span data-ttu-id="bd1cb-118">Espaço de execução</span><span class="sxs-lookup"><span data-stu-id="bd1cb-118">Runspace</span></span>                                    |
| <span data-ttu-id="bd1cb-119">EventId</span><span class="sxs-lookup"><span data-stu-id="bd1cb-119">EventId</span></span> | <span data-ttu-id="bd1cb-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="bd1cb-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>  |
| <span data-ttu-id="bd1cb-121">Mensagem</span><span class="sxs-lookup"><span data-stu-id="bd1cb-121">Message</span></span> | <span data-ttu-id="bd1cb-122">Criar Scriptblock texto (%1 de %2):</span><span class="sxs-lookup"><span data-stu-id="bd1cb-122">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="bd1cb-123">%3</span><span class="sxs-lookup"><span data-stu-id="bd1cb-123">%3</span></span> </br> <span data-ttu-id="bd1cb-124">ID de ScriptBlock: %4</span><span class="sxs-lookup"><span data-stu-id="bd1cb-124">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="bd1cb-125">O texto incorporado na mensagem é o grau de bloco de script compilado.</span><span class="sxs-lookup"><span data-stu-id="bd1cb-125">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="bd1cb-126">O ID é um GUID que é mantido durante a vigência de bloco de script.</span><span class="sxs-lookup"><span data-stu-id="bd1cb-126">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="bd1cb-127">Quando ativar o registo verboso, as escritas de funcionalidade começarem e terminar marcadores:</span><span class="sxs-lookup"><span data-stu-id="bd1cb-127">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="bd1cb-128">Canal</span><span class="sxs-lookup"><span data-stu-id="bd1cb-128">Channel</span></span> | <span data-ttu-id="bd1cb-129">Operacional</span><span class="sxs-lookup"><span data-stu-id="bd1cb-129">Operational</span></span>                                            |
|---------|--------------------------------------------------------|
| <span data-ttu-id="bd1cb-130">Nível</span><span class="sxs-lookup"><span data-stu-id="bd1cb-130">Level</span></span>   | <span data-ttu-id="bd1cb-131">Verbose</span><span class="sxs-lookup"><span data-stu-id="bd1cb-131">Verbose</span></span>                                                |
| <span data-ttu-id="bd1cb-132">Opcode</span><span class="sxs-lookup"><span data-stu-id="bd1cb-132">Opcode</span></span>  | <span data-ttu-id="bd1cb-133">Abrir (/ Fechar)</span><span class="sxs-lookup"><span data-stu-id="bd1cb-133">Open (/ Close)</span></span>                                         |
| <span data-ttu-id="bd1cb-134">Tarefa</span><span class="sxs-lookup"><span data-stu-id="bd1cb-134">Task</span></span>    | <span data-ttu-id="bd1cb-135">CommandStart (/ CommandStop)</span><span class="sxs-lookup"><span data-stu-id="bd1cb-135">CommandStart (/ CommandStop)</span></span>                           |
| <span data-ttu-id="bd1cb-136">Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="bd1cb-136">Keyword</span></span> | <span data-ttu-id="bd1cb-137">Espaço de execução</span><span class="sxs-lookup"><span data-stu-id="bd1cb-137">Runspace</span></span>                                               |
| <span data-ttu-id="bd1cb-138">EventId</span><span class="sxs-lookup"><span data-stu-id="bd1cb-138">EventId</span></span> | <span data-ttu-id="bd1cb-139">O ScriptBlock\_invocar\_iniciar\_detalhe (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="bd1cb-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="bd1cb-140">O ScriptBlock\_invocar\_concluída\_detalhe (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="bd1cb-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="bd1cb-141">Mensagem</span><span class="sxs-lookup"><span data-stu-id="bd1cb-141">Message</span></span> | <span data-ttu-id="bd1cb-142">Invocação de introdução (/ concluída) do ID de ScriptBlock: %1</span><span class="sxs-lookup"><span data-stu-id="bd1cb-142">Started (/ Completed) invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="bd1cb-143">ID de espaço de execução: %2</span><span class="sxs-lookup"><span data-stu-id="bd1cb-143">Runspace ID: %2</span></span> |

<span data-ttu-id="bd1cb-144">O ID é o GUID que representa o bloco de script (o que pode ser correlacionado com o ID de evento 0x1008) e o ID de espaço de execução representa o espaço de execução no qual este bloco de script foi executado.</span><span class="sxs-lookup"><span data-stu-id="bd1cb-144">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="bd1cb-145">Percentagem sinais na mensagem de invocação representam as propriedades ETW structured.</span><span class="sxs-lookup"><span data-stu-id="bd1cb-145">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="bd1cb-146">Enquanto são substituídos por valores reais no texto da mensagem, uma forma mais robusta para aceder aos mesmos é obter a mensagem com o cmdlet Get-WinEvent e, em seguida, utilizar o **propriedades** matriz da mensagem.</span><span class="sxs-lookup"><span data-stu-id="bd1cb-146">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="bd1cb-147">Eis um exemplo de como esta funcionalidade pode ajudá-lo a desenrolar uma tentativa de maliciosa para encriptar e obfuscate um script:</span><span class="sxs-lookup"><span data-stu-id="bd1cb-147">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

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

<span data-ttu-id="bd1cb-148">Executar Isto gera as entradas de registo seguinte:</span><span class="sxs-lookup"><span data-stu-id="bd1cb-148">Running this generates the following log entries:</span></span>

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

Se o comprimento do bloco de script exceder o que é capaz de retenção num único evento ETW, o Windows PowerShell interrompe o script em várias partes. <span data-ttu-id="bd1cb-150">Eis o código de exemplo para recombine um script no respetivos mensagens de registo:</span><span class="sxs-lookup"><span data-stu-id="bd1cb-150">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="bd1cb-151">Tal como acontece com todos os sistemas de registo que tenham uma retenção limitada de memória intermédia (ou seja, registos ETW), um ataque contra esta infraestrutura é inundar o registo de eventos spurious para ocultar provas anterior.</span><span class="sxs-lookup"><span data-stu-id="bd1cb-151">As with all logging systems that have a limited retention buffer (i.e. ETW logs), one attack against this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="bd1cb-152">Para proteger-se contra este ataque, certifique-se de que tem alguma forma de recolha de registos de eventos de multimédia (ou seja, Windows reencaminhamento de eventos, [Spotting o adversário com a monitorização de registo de eventos do Windows](http://www.nsa.gov/ia/_files/app/Spotting_the_Adversary_with_Windows_Event_Log_Monitoring.pdf)) para mover os registos de eventos retire o computador como logo que possível.</span><span class="sxs-lookup"><span data-stu-id="bd1cb-152">To protect yourself from this attack, ensure that you have some form of event log collection set up (i.e., Windows Event Forwarding, [Spotting the Adversary with Windows Event Log Monitoring](http://www.nsa.gov/ia/_files/app/Spotting_the_Adversary_with_Windows_Event_Log_Monitoring.pdf)) to move event logs off of the computer as soon as possible.</span></span>