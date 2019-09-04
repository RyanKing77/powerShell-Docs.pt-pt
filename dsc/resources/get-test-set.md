---
ms.date: 12/12/2018
keywords: DSC, PowerShell, configuração, instalação
title: Conjunto de testes Get
ms.openlocfilehash: 68738107cd4a222a13dd4afa158f0370953158ad
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215422"
---
# <a name="get-test-set"></a><span data-ttu-id="52d75-103">Conjunto de testes Get</span><span class="sxs-lookup"><span data-stu-id="52d75-103">Get-Test-Set</span></span>

><span data-ttu-id="52d75-104">Aplica-se a: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="52d75-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

![Métodos Get, Test e Set](../media/get-test-set.png)

<span data-ttu-id="52d75-106">A configuração de estado desejado do PowerShell é construída em um processo **Get**, **Test**e **set** .</span><span class="sxs-lookup"><span data-stu-id="52d75-106">PowerShell Desired State Configuration is constructed around a **Get**, **Test**, and **Set** process.</span></span> <span data-ttu-id="52d75-107">Os [recursos](resources.md) de DSC contêm métodos para concluir cada uma dessas operações.</span><span class="sxs-lookup"><span data-stu-id="52d75-107">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span> <span data-ttu-id="52d75-108">Em uma [configuração](../configurations/configurations.md), você define os blocos de recursos para preencher as chaves que se tornam parâmetros para os métodos **Get**, **Test**e **set** de um recurso.</span><span class="sxs-lookup"><span data-stu-id="52d75-108">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get**, **Test**, and **Set** methods.</span></span>

<span data-ttu-id="52d75-109">Esta é a sintaxe para um bloco de recursos de **serviço** .</span><span class="sxs-lookup"><span data-stu-id="52d75-109">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="52d75-110">O recurso de **serviço** configura os serviços do Windows.</span><span class="sxs-lookup"><span data-stu-id="52d75-110">The **Service** resource configures Windows services.</span></span>

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

<span data-ttu-id="52d75-111">Os métodos **Get**, **Test**e **set** do recurso de **serviço** terão blocos de parâmetro que aceitam esses valores.</span><span class="sxs-lookup"><span data-stu-id="52d75-111">The **Get**, **Test**, and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

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
> <span data-ttu-id="52d75-112">O idioma e o método usados para definir o recurso determinam como os métodos **Get**, **Test**e **set** serão definidos.</span><span class="sxs-lookup"><span data-stu-id="52d75-112">The language and method used to define the resource determines how the **Get**, **Test**, and **Set** methods will be defined.</span></span>

<span data-ttu-id="52d75-113">Como o recurso de **serviço** tem apenas uma chave necessária`Name`(), um recurso de bloco de **serviço** pode ser tão simples quanto isto:</span><span class="sxs-lookup"><span data-stu-id="52d75-113">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

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

<span data-ttu-id="52d75-114">Quando você compila a configuração acima, os valores que você especifica para uma chave são armazenados no arquivo ". mof" que é gerado.</span><span class="sxs-lookup"><span data-stu-id="52d75-114">When you compile the Configuration above, the values you specify for a key are stored in the ".mof" file that is generated.</span></span> <span data-ttu-id="52d75-115">Para obter mais informações, consulte [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="52d75-115">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

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

<span data-ttu-id="52d75-116">Quando aplicado, o [Configuration Manager local](../managing-nodes/metaConfig.md) (LCM) lerá o valor "spooler" do arquivo " `-Name` . mof" e o passará para o parâmetro dos métodos **Get**, **Test**e **set** para a instância "MyService" doRecurso de serviço.</span><span class="sxs-lookup"><span data-stu-id="52d75-116">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) (LCM) will read the value "Spooler" from the ".mof" file, and pass it to the `-Name` parameter of the **Get**, **Test**, and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="52d75-117">Obter</span><span class="sxs-lookup"><span data-stu-id="52d75-117">Get</span></span>

<span data-ttu-id="52d75-118">O método **Get** de um recurso recupera o estado do recurso conforme ele é configurado no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="52d75-118">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="52d75-119">Esse estado é retornado como uma [tabela de hash](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="52d75-119">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span> <span data-ttu-id="52d75-120">As chaves da **tabela de hash** serão os valores configuráveis, ou parâmetros, que o recurso aceita.</span><span class="sxs-lookup"><span data-stu-id="52d75-120">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="52d75-121">O método **Get** mapeia diretamente para o cmdlet [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="52d75-121">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="52d75-122">Quando você chama `Get-DSCConfiguration`, o LCM executa o método **Get** de cada recurso na configuração aplicada no momento.</span><span class="sxs-lookup"><span data-stu-id="52d75-122">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="52d75-123">O LCM usa os valores de chave armazenados no arquivo ". mof" como parâmetros para cada instância de recurso correspondente.</span><span class="sxs-lookup"><span data-stu-id="52d75-123">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="52d75-124">Essa é uma saída de exemplo de um recurso de **serviço** que configura o serviço de "spooler".</span><span class="sxs-lookup"><span data-stu-id="52d75-124">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

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

<span data-ttu-id="52d75-125">A saída mostra as propriedades de valor atual configuráveis pelo recurso de **serviço** .</span><span class="sxs-lookup"><span data-stu-id="52d75-125">The output shows the current value properties configurable by the **Service** resource.</span></span>

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

## <a name="test"></a><span data-ttu-id="52d75-126">Teste</span><span class="sxs-lookup"><span data-stu-id="52d75-126">Test</span></span>

<span data-ttu-id="52d75-127">O método de **teste** de um recurso determina se o nó de destino está em conformidade no momento com o *estado desejado*do recurso.</span><span class="sxs-lookup"><span data-stu-id="52d75-127">The **Test** method of a resource determines if the target node is currently compliant with the resource's *desired state*.</span></span> <span data-ttu-id="52d75-128">O método de teste `$True` retorna `$False` ou apenas para indicar se o nó está em conformidade.</span><span class="sxs-lookup"><span data-stu-id="52d75-128">The **Test** method returns `$True` or `$False` only to indicate whether the Node is compliant.</span></span>
<span data-ttu-id="52d75-129">Quando você chama [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), o LCM chama o método de **teste** de cada recurso na configuração aplicada no momento.</span><span class="sxs-lookup"><span data-stu-id="52d75-129">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="52d75-130">O LCM usa os valores de chave armazenados no arquivo ". mof" como parâmetros para cada instância de recurso correspondente.</span><span class="sxs-lookup"><span data-stu-id="52d75-130">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="52d75-131">Se o resultado de qualquer **teste** de recurso individual for `$False`, `Test-DSCConfiguration` o `$False` retornará indicando que o nó não está em conformidade.</span><span class="sxs-lookup"><span data-stu-id="52d75-131">If the result of any individual resource's **Test** is `$False`, `Test-DSCConfiguration` returns `$False` indicating that the Node is not compliant.</span></span> <span data-ttu-id="52d75-132">Se os métodos `$True`de **teste** de todos os `Test-DSCConfiguration` recursos `$True` retornarem, o retornará para indicar que o nó está em conformidade.</span><span class="sxs-lookup"><span data-stu-id="52d75-132">If all resource's **Test** methods return `$True`, `Test-DSCConfiguration` returns `$True` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="52d75-133">A partir do PowerShell 5,0, `-Detailed` o parâmetro foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="52d75-133">Beginning in PowerShell 5.0, the `-Detailed` parameter was added.</span></span> <span data-ttu-id="52d75-134">Especificar `-Detailed` as `Test-DSCConfiguration` causas para retornar um objeto que contém coleções de resultados para recursos em conformidade e sem conformidade.</span><span class="sxs-lookup"><span data-stu-id="52d75-134">Specifying `-Detailed` causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="52d75-135">Para obter mais informações, consulte [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span><span class="sxs-lookup"><span data-stu-id="52d75-135">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span></span>

## <a name="set"></a><span data-ttu-id="52d75-136">Definir</span><span class="sxs-lookup"><span data-stu-id="52d75-136">Set</span></span>

<span data-ttu-id="52d75-137">O método **set** de um recurso tenta forçar o nó a ficar em conformidade com o *estado desejado*do recurso.</span><span class="sxs-lookup"><span data-stu-id="52d75-137">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="52d75-138">O método **set** deve ser **idempotente**, o que significa que **set** pode ser executado várias vezes e sempre obter o mesmo resultado sem erros.</span><span class="sxs-lookup"><span data-stu-id="52d75-138">The **Set** method is meant to be **idempotent**, which means that **Set** could be run multiple times and always get the same result without errors.</span></span>  <span data-ttu-id="52d75-139">Quando você executa [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), o LCM percorre cada recurso na configuração aplicada no momento.</span><span class="sxs-lookup"><span data-stu-id="52d75-139">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="52d75-140">O LCM recupera valores de chave para a instância de recurso atual do arquivo ". mof" e as usa como parâmetros para o método de **teste** .</span><span class="sxs-lookup"><span data-stu-id="52d75-140">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="52d75-141">Se o método de teste `$True`retornar, o nó será compatível com o recurso atual e o método **set** será ignorado.</span><span class="sxs-lookup"><span data-stu-id="52d75-141">If the **Test** method returns `$True`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="52d75-142">Se o **teste** retornar `$False`, o nó não será compatível.</span><span class="sxs-lookup"><span data-stu-id="52d75-142">If the **Test** returns `$False`, the Node is non-compliant.</span></span>  <span data-ttu-id="52d75-143">O LCM passa os valores de chave da instância de recurso como parâmetros para o método **set** do recurso, restaurando o nó para conformidade.</span><span class="sxs-lookup"><span data-stu-id="52d75-143">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="52d75-144">Ao especificar os `-Verbose` parâmetros `-Wait` e, você pode `Start-DSCConfiguration` observar o progresso do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="52d75-144">By specifying the `-Verbose` and `-Wait` parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="52d75-145">Neste exemplo, o nó já está em conformidade.</span><span class="sxs-lookup"><span data-stu-id="52d75-145">In this example, the Node is already compliant.</span></span> <span data-ttu-id="52d75-146">A `Verbose` saída indica que o método **set** foi ignorado.</span><span class="sxs-lookup"><span data-stu-id="52d75-146">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="52d75-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52d75-147">See also</span></span>

- [<span data-ttu-id="52d75-148">Visão geral do Azure DSC de Automação</span><span class="sxs-lookup"><span data-stu-id="52d75-148">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="52d75-149">Configurando um servidor de pull SMB</span><span class="sxs-lookup"><span data-stu-id="52d75-149">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="52d75-150">Configurando um cliente de pull</span><span class="sxs-lookup"><span data-stu-id="52d75-150">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
