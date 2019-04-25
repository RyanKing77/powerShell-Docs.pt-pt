---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Get-Test-Set
ms.openlocfilehash: 6d059518a49926bc5fb56e37e7d3d4d2c66bddec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076604"
---
# <a name="get-test-set"></a><span data-ttu-id="e531a-103">Get-Test-Set</span><span class="sxs-lookup"><span data-stu-id="e531a-103">Get-Test-Set</span></span>

><span data-ttu-id="e531a-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e531a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

![Métodos Get, Test e Set](/media/get-test-set.png)

<span data-ttu-id="e531a-106">PowerShell Desired State Configuration é construído em torno de um **Obtenha**, **teste**, e **definir** processo.</span><span class="sxs-lookup"><span data-stu-id="e531a-106">PowerShell Desired State Configuration is constructed around a **Get**, **Test**, and **Set** process.</span></span> <span data-ttu-id="e531a-107">DSC [recursos](resources.md) cada contém métodos para concluir cada uma destas operações.</span><span class="sxs-lookup"><span data-stu-id="e531a-107">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span> <span data-ttu-id="e531a-108">Num [Configuration](../configurations/configurations.md), define blocos de recurso para preencher as chaves que tornam-se de parâmetros para um recurso **obter**, **teste**, e **definir** métodos.</span><span class="sxs-lookup"><span data-stu-id="e531a-108">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get**, **Test**, and **Set** methods.</span></span>

<span data-ttu-id="e531a-109">Esta é a sintaxe para uma **serviço** bloco de recursos.</span><span class="sxs-lookup"><span data-stu-id="e531a-109">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="e531a-110">O **serviço** recursos configura os serviços do Windows.</span><span class="sxs-lookup"><span data-stu-id="e531a-110">The **Service** resource configures Windows services.</span></span>

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

<span data-ttu-id="e531a-111">O **obter**, **teste**, e **definir** métodos para o **serviço** recurso terão os blocos de parâmetro que aceitam estes valores.</span><span class="sxs-lookup"><span data-stu-id="e531a-111">The **Get**, **Test**, and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

```powershell
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [System.String]
        $Name,

        [System.String]
        [ValidateSet("Automatic", "Manual", "Disabled")]
        $StartupType,

        [System.String]
        [ValidateSet("LocalSystem", "LocalService", "NetworkService")]
        $BuiltInAccount,

        [System.Management.Automation.PSCredential]
        [ValidateNotNull()]
        $Credential,

        [System.String]
        [ValidateSet("Running", "Stopped")]
        $State="Running",

        [System.String]
        [ValidateNotNullOrEmpty()]
        $DisplayName,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Description,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Path,

        [System.String[]]
        [ValidateNotNullOrEmpty()]
        $Dependencies,

        [System.String]
        [ValidateSet("Present", "Absent")]
        $Ensure="Present"
    )
```

> [!NOTE]
> <span data-ttu-id="e531a-112">O idioma e o método usado para definir o recurso determina como o **Obtenha**, **teste**, e **definir** métodos serão definidos.</span><span class="sxs-lookup"><span data-stu-id="e531a-112">The language and method used to define the resource determines how the **Get**, **Test**, and **Set** methods will be defined.</span></span>

<span data-ttu-id="e531a-113">Uma vez que o **serviço** recurso tem apenas uma chave necessária (`Name`), um **serviço** bloquear recursos podem ser tão simples como este:</span><span class="sxs-lookup"><span data-stu-id="e531a-113">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

```powershell
Configuration TestConfig
{
    Import-DSCResource -Name Service
    Node localhost
    {
        Service "MyService"
        {
            Name = "Spooler"
        }
    }
}
```

<span data-ttu-id="e531a-114">Quando compilar a configuração acima, os valores que especificou para uma chave são armazenados no arquivo ". MOF" que é gerado.</span><span class="sxs-lookup"><span data-stu-id="e531a-114">When you compile the Configuration above, the values you specify for a key are stored in the ".mof" file that is generated.</span></span> <span data-ttu-id="e531a-115">Para obter mais informações, consulte [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="e531a-115">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

```
instance of MSFT_ServiceResource as $MSFT_ServiceResource1ref
{
SourceInfo = "::5::1::Service";
 ModuleName = "PsDesiredStateConfiguration";
 ResourceID = "[Service]MyService";
 Name = "Spooler";

ModuleVersion = "1.0";

 ConfigurationName = "Test";

};
```

<span data-ttu-id="e531a-116">Quando aplicada, o [Gestor de configuração Local](../managing-nodes/metaConfig.md) irá ler o valor "Spooler" a partir do ficheiro ". MOF" e passá-lo para o `-Name` parâmetro do **obter**, **teste**, e **definir** métodos para a instância "MyService" a **serviço** recursos.</span><span class="sxs-lookup"><span data-stu-id="e531a-116">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) will read the value "Spooler" from the ".mof" file, and pass it to the `-Name` parameter of the **Get**, **Test**, and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="e531a-117">Obter</span><span class="sxs-lookup"><span data-stu-id="e531a-117">Get</span></span>

<span data-ttu-id="e531a-118">O **obter** método de um recurso, obtém o estado do recurso, porque esta está configurada no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="e531a-118">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="e531a-119">Este estado é retornado como um [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="e531a-119">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span> <span data-ttu-id="e531a-120">As chaves do **hashtable** será o configuráveis valores ou parâmetros, aceita o recurso.</span><span class="sxs-lookup"><span data-stu-id="e531a-120">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="e531a-121">O **Obtenha** método é mapeado diretamente para o [Get-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e531a-121">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="e531a-122">Quando chama `Get-DSCConfiguration`, as execuções de LCM a **obter** método de cada recurso na configuração atualmente aplicada.</span><span class="sxs-lookup"><span data-stu-id="e531a-122">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="e531a-123">O LCM utiliza os valores de chave armazenados no ficheiro ". MOF" como parâmetros para cada instância de recurso correspondente.</span><span class="sxs-lookup"><span data-stu-id="e531a-123">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="e531a-124">Esta é a saída de exemplo de um **serviço** recurso que configura o serviço de "Spooler".</span><span class="sxs-lookup"><span data-stu-id="e531a-124">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

```output
ConfigurationName    : Test
DependsOn            :
ModuleName           : PsDesiredStateConfiguration
ModuleVersion        : 1.1
PsDscRunAsCredential :
ResourceId           : [Service]Spooler
SourceInfo           :
BuiltInAccount       : LocalSystem
Credential           :
Dependencies         : {RPCSS, http}
Description          : This service spools print jobs and handles interaction with the printer.  If you turn off
                       this service, you won’t be able to print or see your printers.
DisplayName          : Print Spooler
Ensure               :
Name                 : Spooler
Path                 : C:\WINDOWS\System32\spoolsv.exe
StartupType          : Automatic
State                : Running
Status               :
PSComputerName       :
CimClassName         : MSFT_ServiceResource
```

<span data-ttu-id="e531a-125">O resultado mostra as propriedades do valor atual configurável, o **serviço** recursos.</span><span class="sxs-lookup"><span data-stu-id="e531a-125">The output shows the current value properties configurable by the **Service** resource.</span></span>

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

## <a name="test"></a><span data-ttu-id="e531a-126">Teste</span><span class="sxs-lookup"><span data-stu-id="e531a-126">Test</span></span>

<span data-ttu-id="e531a-127">O **teste** método de um recurso determina se o nó de destino está atualmente em conformidade com o recurso *pretendido estado*.</span><span class="sxs-lookup"><span data-stu-id="e531a-127">The **Test** method of a resource determines if the target node is currently compliant with the resource's *desired state*.</span></span> <span data-ttu-id="e531a-128">O **teste** retorno do método `$True` ou `$False` apenas para indicar se o nó está em conformidade.</span><span class="sxs-lookup"><span data-stu-id="e531a-128">The **Test** method returns `$True` or `$False` only to indicate whether the Node is compliant.</span></span>
<span data-ttu-id="e531a-129">Quando chama [Test-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), as chamadas de LCM a **teste** método de cada recurso na configuração atualmente aplicada.</span><span class="sxs-lookup"><span data-stu-id="e531a-129">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="e531a-130">O LCM utiliza os valores de chave armazenados no ficheiro ". MOF" como parâmetros para cada instância de recurso correspondente.</span><span class="sxs-lookup"><span data-stu-id="e531a-130">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="e531a-131">Se o resultado de qualquer recurso individual **teste** é `$False`, `Test-DSCConfiguration` devolve `$False` que indica que o nó não está em conformidade.</span><span class="sxs-lookup"><span data-stu-id="e531a-131">If the result of any individual resource's **Test** is `$False`, `Test-DSCConfiguration` returns `$False` indicating that the Node is not compliant.</span></span> <span data-ttu-id="e531a-132">Se todos os recursos **teste** métodos retornam `$True`, `Test-DSCConfiguration` devolve `$True` para indicar que o nó está em conformidade.</span><span class="sxs-lookup"><span data-stu-id="e531a-132">If all resource's **Test** methods return `$True`, `Test-DSCConfiguration` returns `$True` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="e531a-133">A partir do PowerShell 5.0, o `-Detailed` foi adicionado o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e531a-133">Beginning in PowerShell 5.0, the `-Detailed` parameter was added.</span></span> <span data-ttu-id="e531a-134">Especificar `-Detailed` faz com que `Test-DSCConfiguration` retorne um objeto que contém coleções de resultados para os recursos em conformidade e não conformes.</span><span class="sxs-lookup"><span data-stu-id="e531a-134">Specifying `-Detailed` causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="e531a-135">Para obter mais informações, consulte [Test-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span><span class="sxs-lookup"><span data-stu-id="e531a-135">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span></span>

## <a name="set"></a><span data-ttu-id="e531a-136">Definir</span><span class="sxs-lookup"><span data-stu-id="e531a-136">Set</span></span>

<span data-ttu-id="e531a-137">O **definir** método de um recurso tenta forçar o nó para ficarem em conformidade com o recurso *pretendido estado*.</span><span class="sxs-lookup"><span data-stu-id="e531a-137">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="e531a-138">O **definir** método destina-se a ser **idempotentes**, que significa que **definir** poderia ser executado múltiplas vezes e obter sempre o mesmo resultado sem erros.</span><span class="sxs-lookup"><span data-stu-id="e531a-138">The **Set** method is meant to be **idempotent**, which means that **Set** could be run multiple times and always get the same result without errors.</span></span>  <span data-ttu-id="e531a-139">Quando executa [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), os ciclos de LCM por meio de cada recurso na configuração atualmente aplicada.</span><span class="sxs-lookup"><span data-stu-id="e531a-139">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="e531a-140">O LCM recupera valores de chave para a instância atual do recurso do ficheiro ". MOF" e utiliza-as como parâmetros para o **teste** método.</span><span class="sxs-lookup"><span data-stu-id="e531a-140">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="e531a-141">Se o **teste** retorno do método `$True`, o nó está em conformidade com o recurso atual e o **definir** método é ignorado.</span><span class="sxs-lookup"><span data-stu-id="e531a-141">If the **Test** method returns `$True`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="e531a-142">Se o **teste** devolve `$False`, o nó está em conformidade.</span><span class="sxs-lookup"><span data-stu-id="e531a-142">If the **Test** returns `$False`, the Node is non-compliant.</span></span>  <span data-ttu-id="e531a-143">O LCM passa o recurso de valores de chave da instância como parâmetros para o recurso **definir** método, restaurar o nó para conformidade.</span><span class="sxs-lookup"><span data-stu-id="e531a-143">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="e531a-144">Ao especificar os `-Verbose` e `-Wait` parâmetros, pode ver o progresso do `Start-DSCConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e531a-144">By specifying the `-Verbose` and `-Wait` parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="e531a-145">Neste exemplo, o nó já está em conformidade.</span><span class="sxs-lookup"><span data-stu-id="e531a-145">In this example, the Node is already compliant.</span></span> <span data-ttu-id="e531a-146">O `Verbose` resultado indica que o **definir** método foi ignorado.</span><span class="sxs-lookup"><span data-stu-id="e531a-146">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

```
PS> Start-DSCConfiguration -Verbose -Wait -UseExisting

VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
ApplyConfiguration,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer SERVER01 with user sid
S-1-5-21-124525095-708259637-1543119021-1282804.
VERBOSE: [SERVER01]:                            [] Starting consistency engine.
VERBOSE: [SERVER01]:                            [] Checking consistency for current configuration.
VERBOSE: [SERVER01]:                            [DSCEngine] Importing the module
C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\DscResources\MSFT_ServiceResource\MSFT
_ServiceResource.psm1 in force mode.
VERBOSE: [SERVER01]: LCM:  [ Start  Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ Start  Test     ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [[Service]Spooler] Importing the module MSFT_ServiceResource in
force mode.
VERBOSE: [SERVER01]: LCM:  [ End    Test     ]  [[Service]Spooler]  in 0.2540 seconds.
VERBOSE: [SERVER01]: LCM:  [ Skip   Set      ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ End    Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [] Consistency check completed.
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Time taken for configuration job to complete is 1.379 seconds
```

## <a name="see-also"></a><span data-ttu-id="e531a-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e531a-147">See also</span></span>

- [<span data-ttu-id="e531a-148">Descrição geral de DSC de automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="e531a-148">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="e531a-149">Como configurar um servidor de solicitação SMB</span><span class="sxs-lookup"><span data-stu-id="e531a-149">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="e531a-150">Configurar um cliente de solicitação</span><span class="sxs-lookup"><span data-stu-id="e531a-150">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
