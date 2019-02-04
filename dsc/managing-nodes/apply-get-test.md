---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Aplicar, Obter e Testar Configurações num Nó
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684340"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a><span data-ttu-id="92ea0-103">Aplicar, Obter e Testar Configurações num Nó</span><span class="sxs-lookup"><span data-stu-id="92ea0-103">Apply, Get, and Test Configurations on a Node</span></span>

<span data-ttu-id="92ea0-104">Este guia irá mostrar como trabalhar com configurações num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="92ea0-104">This guide will show you how to work with Configurations on a target Node.</span></span> <span data-ttu-id="92ea0-105">Este guia é dividido nos seguintes passos:</span><span class="sxs-lookup"><span data-stu-id="92ea0-105">This guide is broken up into the following steps:</span></span>

## <a name="apply-a-configuration"></a><span data-ttu-id="92ea0-106">Aplicar uma configuração</span><span class="sxs-lookup"><span data-stu-id="92ea0-106">Apply a Configuration</span></span>

<span data-ttu-id="92ea0-107">Para aplicar e gerir uma configuração, é necessário gerar um arquivo de ". MOF".</span><span class="sxs-lookup"><span data-stu-id="92ea0-107">In order to apply and manage a Configuration, we need to generate a ".mof" file.</span></span> <span data-ttu-id="92ea0-108">O código a seguir representará uma configuração simples que será utilizada ao longo deste guia.</span><span class="sxs-lookup"><span data-stu-id="92ea0-108">The following code will represent a simple Configuration that will be used throughout this guide.</span></span>

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

<span data-ttu-id="92ea0-109">Compilar esta configuração resultará em dois arquivos ". MOF".</span><span class="sxs-lookup"><span data-stu-id="92ea0-109">Compiling this configuration will yield two ".mof" files.</span></span>

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

<span data-ttu-id="92ea0-110">Para aplicar uma configuração, utilize o [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="92ea0-110">To apply a Configuration, use the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="92ea0-111">O `-Path` parâmetro especifica um diretório onde residem os arquivos ". MOF".</span><span class="sxs-lookup"><span data-stu-id="92ea0-111">The `-Path` parameter specifies a directory where ".mof" files reside.</span></span> <span data-ttu-id="92ea0-112">Se nenhum `-Computername` for especificado, `Start-DSCConfiguration` irá tentar aplicar a cada configuração para o nome do computador especificado pelo nome do ficheiro ". MOF" (\<computername\>. mof).</span><span class="sxs-lookup"><span data-stu-id="92ea0-112">If no `-Computername` is specified, `Start-DSCConfiguration` will attempt to apply each Configuration to the computer name specified by the name of the '.mof' file (\<computername\>.mof).</span></span> <span data-ttu-id="92ea0-113">Especifique `-Verbose` para `Start-DSCConfiguration` para ver a saída mais detalhada.</span><span class="sxs-lookup"><span data-stu-id="92ea0-113">Specify `-Verbose` to `Start-DSCConfiguration` to see more verbose output.</span></span>

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

<span data-ttu-id="92ea0-114">Se `-Wait` não for especificado, verá uma tarefa que criou.</span><span class="sxs-lookup"><span data-stu-id="92ea0-114">If `-Wait` is not specified, you see one job created.</span></span> <span data-ttu-id="92ea0-115">A tarefa criada terá um **ChildJob** para cada ficheiro de ". MOF" processados pelo `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="92ea0-115">The job created will have one **ChildJob** for each ".mof" file processed by `Start-DSCConfiguration`.</span></span>

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

<span data-ttu-id="92ea0-116">Se uma configuração está a demorar muito tempo e que pretende parar ele, pode usar [Stop-dscconfiguration para](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) para parar a aplicação no nó local.</span><span class="sxs-lookup"><span data-stu-id="92ea0-116">If a Configuration is taking a long time and you want to stop it, you can use [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) to stop application on the local Node.</span></span>

```powershell
Stop-DSCConfiguration -Force
```

<span data-ttu-id="92ea0-117">Depois de concluído, pode ver o estado das tarefas por meio do objeto de tarefa devolvido pelo [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span><span class="sxs-lookup"><span data-stu-id="92ea0-117">Once complete, you can view the status of the jobs through the job object returned by [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span></span>

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

<span data-ttu-id="92ea0-118">Para ver os **verboso** saídas, utilize os seguintes comandos para ver a **verboso** stream para cada **ChildJob**.</span><span class="sxs-lookup"><span data-stu-id="92ea0-118">To see the **Verbose** output, use the following commands to view the **Verbose** stream for each **ChildJob**.</span></span> <span data-ttu-id="92ea0-119">Para mais informações sobre tarefas do PowerShell, consulte [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span><span class="sxs-lookup"><span data-stu-id="92ea0-119">For more about PowerShell jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="92ea0-120">A partir do PowerShell 5.0, o `-UseExisting` parâmetro foi adicionado ao `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="92ea0-120">Beginning in PowerShell 5.0, the `-UseExisting` parameter was added to `Start-DSCConfiguration`.</span></span> <span data-ttu-id="92ea0-121">Ao especificar `-UseExisting`, instruir o cmdlet para utilizar a configuração de aplicado existente em vez de um especificado pelo `-Path` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="92ea0-121">By specifying `-UseExisting`, you instruct the cmdlet to use the existing applied Configuration instead of one specified by the `-Path` parameter.</span></span>

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a><span data-ttu-id="92ea0-122">Uma configuração de teste</span><span class="sxs-lookup"><span data-stu-id="92ea0-122">Test a Configuration</span></span>

<span data-ttu-id="92ea0-123">Pode testar uma configuração atualmente aplicada através de [Test-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="92ea0-123">You can test a currently applied Configuration using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span> <span data-ttu-id="92ea0-124">`Test-DSCConfiguration` irá devolver `True` se o nó está em conformidade, e `False` se não for.</span><span class="sxs-lookup"><span data-stu-id="92ea0-124">`Test-DSCConfiguration` will return `True` if the Node is compliant, and `False` if it is not.</span></span>

```powershell
Test-DSCConfiguration
```

<span data-ttu-id="92ea0-125">A partir do PowerShell 5.0, o `-Detailed` parâmetro foi adicionado, que retorna um objeto com coleções para **ResourcesInDesiredState** e **ResourcesNotInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="92ea0-125">Beginning in PowerShell 5.0, the `-Detailed` parameter was added which returns an object with collections for **ResourcesInDesiredState** and **ResourcesNotInDesiredState**</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

<span data-ttu-id="92ea0-126">Começando no PowerShell 5.0, pode testar uma configuração sem aplicá-lo.</span><span class="sxs-lookup"><span data-stu-id="92ea0-126">Beginning in PowerShell 5.0 you can test a Configuration without applying it.</span></span> <span data-ttu-id="92ea0-127">O `-ReferenceConfiguration` parâmetro aceita o caminho de um ficheiro de ". MOF" para testar o nó contra.</span><span class="sxs-lookup"><span data-stu-id="92ea0-127">The `-ReferenceConfiguration` parameter accepts the path of a ".mof" file to test the Node against.</span></span> <span data-ttu-id="92ea0-128">Não **definir** ações são executadas no nó.</span><span class="sxs-lookup"><span data-stu-id="92ea0-128">No **Set** actions are taken against the Node.</span></span> <span data-ttu-id="92ea0-129">No PowerShell 4.0, existem soluções alternativas para testar uma configuração sem aplicá-lo, mas não são discutidas aqui.</span><span class="sxs-lookup"><span data-stu-id="92ea0-129">In PowerShell 4.0, there are workarounds to test a Configuration without applying it, but they are not discussed here.</span></span>

## <a name="get-configuration-values"></a><span data-ttu-id="92ea0-130">Obter valores de configuração</span><span class="sxs-lookup"><span data-stu-id="92ea0-130">Get Configuration Values</span></span>

<span data-ttu-id="92ea0-131">O [Get-dscconfiguration para](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet devolve os valores atuais para todos os recursos configurados na configuração atualmente aplicada.</span><span class="sxs-lookup"><span data-stu-id="92ea0-131">The [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returns the current values for any configured resources in the currently applied Configuration.</span></span>

```powershell
Get-DSCConfiguration
```

<span data-ttu-id="92ea0-132">Saída do nosso exemplo de configuração teria o seguinte aspeto se aplicadas com êxito.</span><span class="sxs-lookup"><span data-stu-id="92ea0-132">Output from our sample Configuration would look like this if applied successfully.</span></span>

```output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a><span data-ttu-id="92ea0-133">Obter o estado de configuração</span><span class="sxs-lookup"><span data-stu-id="92ea0-133">Get Configuration Status</span></span>

<span data-ttu-id="92ea0-134">A partir do PowerShell 5.0 a [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet permite-lhe ver o histórico de configurações aplicados ao nó.</span><span class="sxs-lookup"><span data-stu-id="92ea0-134">Beginning in PowerShell 5.0 the [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet allows you to see the history of applied Configurations to the node.</span></span> <span data-ttu-id="92ea0-135">DSC de PowerShell mantém um registro de últimas configurações de {{N}} aplicadas **Push** ou **extrair** modo.</span><span class="sxs-lookup"><span data-stu-id="92ea0-135">PowerShell DSC keeps track of the last {{N}} Configurations applied in **Push** or **Pull** mode.</span></span> <span data-ttu-id="92ea0-136">Isso inclui qualquer *consistência* verificações executadas pelo LCM.</span><span class="sxs-lookup"><span data-stu-id="92ea0-136">This includes any *consistency* checks executed by the LCM.</span></span> <span data-ttu-id="92ea0-137">Por predefinição, `Get-DSCConfigurationStatus` mostra-lhe apenas a última entrada do histórico.</span><span class="sxs-lookup"><span data-stu-id="92ea0-137">By default, `Get-DSCConfigurationStatus` shows you the last history entry only.</span></span>

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

<span data-ttu-id="92ea0-138">Utilize o `-All` parâmetro para ver todo o histórico de estado de configuração.</span><span class="sxs-lookup"><span data-stu-id="92ea0-138">Use the `-All` parameter to see all Configuration Status history.</span></span>

> [!NOTE]
> <span data-ttu-id="92ea0-139">Saída é truncada para fins de brevidade.</span><span class="sxs-lookup"><span data-stu-id="92ea0-139">Output is truncated for brevity.</span></span>

```powershell
Get-DSCConfigurationStatus -All
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a><span data-ttu-id="92ea0-140">Gerir documentos de configuração</span><span class="sxs-lookup"><span data-stu-id="92ea0-140">Manage Configuration Documents</span></span>

<span data-ttu-id="92ea0-141">O LCM gerencia a configuração do nó ao trabalhar com **documentos de configuração**.</span><span class="sxs-lookup"><span data-stu-id="92ea0-141">The LCM manages the Configuration of the Node by working with **Configuration Documents**.</span></span> <span data-ttu-id="92ea0-142">Esses arquivos de ". MOF" residem no diretório "C:\Windows\System32\Configuration".</span><span class="sxs-lookup"><span data-stu-id="92ea0-142">These ".mof" files reside in the "C:\Windows\System32\Configuration" directory.</span></span>

<span data-ttu-id="92ea0-143">A partir do PowerShell 5.0 a [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) permite-lhe remover os ficheiros de ". MOF" para parar a verificação de consistência futuros ou remover uma configuração de que tem erros quando aplicada.</span><span class="sxs-lookup"><span data-stu-id="92ea0-143">Beginning in PowerShell 5.0 the [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) allows you to remove the ".mof" files to stop future consistency checks or remove a Configuration that has errors when applied.</span></span> <span data-ttu-id="92ea0-144">O `-Stage` parâmetro permite-lhe especificar qual pretende remover o ficheiro ". MOF".</span><span class="sxs-lookup"><span data-stu-id="92ea0-144">The `-Stage` parameter allows you to specify which ".mof" file you want to remove.</span></span>

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> <span data-ttu-id="92ea0-145">No PowerShell 4.0, ainda pode remover esses arquivos ". MOF" diretamente usando [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span><span class="sxs-lookup"><span data-stu-id="92ea0-145">In PowerShell 4.0, you can still remove these ".mof" files directly using [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span></span>

## <a name="publish-configurations"></a><span data-ttu-id="92ea0-146">Configurações de publicação</span><span class="sxs-lookup"><span data-stu-id="92ea0-146">Publish Configurations</span></span>

<span data-ttu-id="92ea0-147">A partir do PowerShell 5.0, o [Publish-dscconfiguration para](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) foi adicionado o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="92ea0-147">Beginning in PowerShell 5.0, the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet was added.</span></span> <span data-ttu-id="92ea0-148">Este cmdlet permite-lhe publicar um ficheiro de ". MOF" computadores remotos, sem aplicá-lo.</span><span class="sxs-lookup"><span data-stu-id="92ea0-148">This cmdlet allows you to publish a ".mof" file to remote computers, without applying it.</span></span>

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a><span data-ttu-id="92ea0-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92ea0-149">See also</span></span>

- [<span data-ttu-id="92ea0-150">Obter, teste e definir</span><span class="sxs-lookup"><span data-stu-id="92ea0-150">Get, Test, and Set</span></span>](../resources/get-test-set.md)
