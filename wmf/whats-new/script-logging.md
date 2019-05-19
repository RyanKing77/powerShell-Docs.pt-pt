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
# <a name="script-tracing-and-logging"></a><span data-ttu-id="c4c8a-103">Registo e Rastreio de Scripts</span><span class="sxs-lookup"><span data-stu-id="c4c8a-103">Script Tracing and Logging</span></span>

<span data-ttu-id="c4c8a-104">Enquanto PowerShell já tem o **LogPipelineExecutionDetails** diretiva de grupo na definição de invocação de cmdlets de registo, o linguagem de script do PowerShell que possui vários recursos que pode querer iniciar sessão e de auditoria.</span><span class="sxs-lookup"><span data-stu-id="c4c8a-104">While PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell's scripting language has several features that you might want to log and audit.</span></span> <span data-ttu-id="c4c8a-105">O novo recurso de rastreamento detalhadas de Script fornece detalhadas de controlo e a análise da atividade de script do PowerShell num sistema.</span><span class="sxs-lookup"><span data-stu-id="c4c8a-105">The new Detailed Script Tracing feature provides detailed tracking and analysis of PowerShell script activity on a system.</span></span> <span data-ttu-id="c4c8a-106">Depois de ativar o rastreio de detalhado de script, PowerShell regista todos os blocos de script para o registo de eventos do ETW **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="c4c8a-106">After enabling detailed script tracing, PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="c4c8a-107">Se um bloco de scripts cria outro bloco de scripts, por exemplo, ao chamar `Invoke-Expression`, o bloco de script invocado também registada.</span><span class="sxs-lookup"><span data-stu-id="c4c8a-107">If a script block creates another script block, for example, by calling `Invoke-Expression`, the invoked script block also logged.</span></span>

<span data-ttu-id="c4c8a-108">O registo está ativado por meio da **ativar o registo de bloco de Script do PowerShell** definição de política de grupo na **modelos administrativos** -> **componentes do Windows**  ->  **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="c4c8a-108">Logging is enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting in **Administrative Templates** -> **Windows Components** -> **Windows PowerShell**.</span></span>

<span data-ttu-id="c4c8a-109">Os eventos são:</span><span class="sxs-lookup"><span data-stu-id="c4c8a-109">The events are:</span></span>

| <span data-ttu-id="c4c8a-110">Canal</span><span class="sxs-lookup"><span data-stu-id="c4c8a-110">Channel</span></span> |                               <span data-ttu-id="c4c8a-111">Operacional</span><span class="sxs-lookup"><span data-stu-id="c4c8a-111">Operational</span></span>                               |
| ------- | ----------------------------------------------------------------------- |
| <span data-ttu-id="c4c8a-112">Nível</span><span class="sxs-lookup"><span data-stu-id="c4c8a-112">Level</span></span>   | <span data-ttu-id="c4c8a-113">Verbose</span><span class="sxs-lookup"><span data-stu-id="c4c8a-113">Verbose</span></span>                                                                 |
| <span data-ttu-id="c4c8a-114">Opcode</span><span class="sxs-lookup"><span data-stu-id="c4c8a-114">Opcode</span></span>  | <span data-ttu-id="c4c8a-115">Criar</span><span class="sxs-lookup"><span data-stu-id="c4c8a-115">Create</span></span>                                                                  |
| <span data-ttu-id="c4c8a-116">Tarefa</span><span class="sxs-lookup"><span data-stu-id="c4c8a-116">Task</span></span>    | <span data-ttu-id="c4c8a-117">CommandStart</span><span class="sxs-lookup"><span data-stu-id="c4c8a-117">CommandStart</span></span>                                                            |
| <span data-ttu-id="c4c8a-118">Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="c4c8a-118">Keyword</span></span> | <span data-ttu-id="c4c8a-119">espaço de execução</span><span class="sxs-lookup"><span data-stu-id="c4c8a-119">Runspace</span></span>                                                                |
| <span data-ttu-id="c4c8a-120">EventId</span><span class="sxs-lookup"><span data-stu-id="c4c8a-120">EventId</span></span> | <span data-ttu-id="c4c8a-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="c4c8a-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>                              |
| <span data-ttu-id="c4c8a-122">Mensagem</span><span class="sxs-lookup"><span data-stu-id="c4c8a-122">Message</span></span> | <span data-ttu-id="c4c8a-123">Criação de texto de Scriptblock (%1 de %2):</span><span class="sxs-lookup"><span data-stu-id="c4c8a-123">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="c4c8a-124">%3</span><span class="sxs-lookup"><span data-stu-id="c4c8a-124">%3</span></span> </br> <span data-ttu-id="c4c8a-125">ID de ScriptBlock: %4</span><span class="sxs-lookup"><span data-stu-id="c4c8a-125">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="c4c8a-126">O texto incorporado na mensagem é a extensão do bloco de script compilado.</span><span class="sxs-lookup"><span data-stu-id="c4c8a-126">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="c4c8a-127">O ID é um GUID que é retido durante o ciclo de vida do bloco de script.</span><span class="sxs-lookup"><span data-stu-id="c4c8a-127">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="c4c8a-128">Quando ativar o registo verboso, as gravações de funcionalidade begin e end marcadores:</span><span class="sxs-lookup"><span data-stu-id="c4c8a-128">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="c4c8a-129">Canal</span><span class="sxs-lookup"><span data-stu-id="c4c8a-129">Channel</span></span> |                                 <span data-ttu-id="c4c8a-130">Operacional</span><span class="sxs-lookup"><span data-stu-id="c4c8a-130">Operational</span></span>                                |
| ------- | -------------------------------------------------------------------------- |
| <span data-ttu-id="c4c8a-131">Nível</span><span class="sxs-lookup"><span data-stu-id="c4c8a-131">Level</span></span>   | <span data-ttu-id="c4c8a-132">Verbose</span><span class="sxs-lookup"><span data-stu-id="c4c8a-132">Verbose</span></span>                                                                    |
| <span data-ttu-id="c4c8a-133">Opcode</span><span class="sxs-lookup"><span data-stu-id="c4c8a-133">Opcode</span></span>  | <span data-ttu-id="c4c8a-134">Abrir / fechar</span><span class="sxs-lookup"><span data-stu-id="c4c8a-134">Open / Close</span></span>                                                               |
| <span data-ttu-id="c4c8a-135">Tarefa</span><span class="sxs-lookup"><span data-stu-id="c4c8a-135">Task</span></span>    | <span data-ttu-id="c4c8a-136">CommandStart / CommandStop</span><span class="sxs-lookup"><span data-stu-id="c4c8a-136">CommandStart / CommandStop</span></span>                                                 |
| <span data-ttu-id="c4c8a-137">Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="c4c8a-137">Keyword</span></span> | <span data-ttu-id="c4c8a-138">espaço de execução</span><span class="sxs-lookup"><span data-stu-id="c4c8a-138">Runspace</span></span>                                                                   |
| <span data-ttu-id="c4c8a-139">EventId</span><span class="sxs-lookup"><span data-stu-id="c4c8a-139">EventId</span></span> | <span data-ttu-id="c4c8a-140">O ScriptBlock\_invocar\_iniciar\_detalhes (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="c4c8a-140">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="c4c8a-141">O ScriptBlock\_invocar\_completa\_detalhes (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="c4c8a-141">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="c4c8a-142">Mensagem</span><span class="sxs-lookup"><span data-stu-id="c4c8a-142">Message</span></span> | <span data-ttu-id="c4c8a-143">Iniciou / concluída a invocação do ID de ScriptBlock: %1</span><span class="sxs-lookup"><span data-stu-id="c4c8a-143">Started / Completed invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="c4c8a-144">ID do espaço de execução: %2</span><span class="sxs-lookup"><span data-stu-id="c4c8a-144">Runspace ID: %2</span></span> |

<span data-ttu-id="c4c8a-145">O ID é o GUID que representa o bloco de script (que pode ser correlacionado com o ID de evento 0x1008) e o ID do espaço de execução representa o espaço de execução no qual este bloco de script foi executado.</span><span class="sxs-lookup"><span data-stu-id="c4c8a-145">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="c4c8a-146">Símbolos de percentagem na mensagem de invocação representam estruturadas propriedades ETW.</span><span class="sxs-lookup"><span data-stu-id="c4c8a-146">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="c4c8a-147">Enquanto são substituídos pelos valores reais no texto da mensagem, uma maneira mais robusta para aceder aos mesmos é obter a mensagem com o cmdlet Get-WinEvent e, em seguida, utilizar o **propriedades** matriz da mensagem.</span><span class="sxs-lookup"><span data-stu-id="c4c8a-147">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="c4c8a-148">Eis um exemplo de como essa funcionalidade pode ajudar a anular a moldagem de uma tentativa de maliciosa para encriptar e oculte um script:</span><span class="sxs-lookup"><span data-stu-id="c4c8a-148">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

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

<span data-ttu-id="c4c8a-149">Executando isso gera as seguintes entradas de registo:</span><span class="sxs-lookup"><span data-stu-id="c4c8a-149">Running this generates the following log entries:</span></span>

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

Se o tamanho do bloco de script exceder a capacidade de um único evento, o PowerShell divide o script em várias partes. <span data-ttu-id="c4c8a-151">Aqui está o código de exemplo para voltar um script de suas mensagens de registo:</span><span class="sxs-lookup"><span data-stu-id="c4c8a-151">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="c4c8a-152">Tal como acontece com todos os sistemas de Registro em log com um buffer de retenção limitada, uma forma de atacar esta infraestrutura é inundar o registo com eventos falsos para ocultar evidências anteriores.</span><span class="sxs-lookup"><span data-stu-id="c4c8a-152">As with all logging systems that have a limited retention buffer, one way to attack this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="c4c8a-153">Para proteger-se contra este ataque, certifique-se de que tem alguma forma de configurar o reencaminhamento de eventos do Windows de recolha de registos de eventos.</span><span class="sxs-lookup"><span data-stu-id="c4c8a-153">To protect yourself from this attack, ensure that you have some form of event log collection set up Windows Event Forwarding.</span></span> <span data-ttu-id="c4c8a-154">Para obter mais informações, consulte [detetar o adversário com a monitorização de registo de eventos do Windows](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span><span class="sxs-lookup"><span data-stu-id="c4c8a-154">For more information, see [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span></span>