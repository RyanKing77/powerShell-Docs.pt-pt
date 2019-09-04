---
ms.date: 12/12/2018
keywords: DSC, PowerShell, configuração, instalação
title: Utilizar a palavra-chave Import-DSCResource
ms.openlocfilehash: e1c2c06d756a70c2de516f330e3123235ce740ba
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215402"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="22974-103">Utilizar a palavra-chave Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="22974-103">Using Import-DSCResource</span></span>

<span data-ttu-id="22974-104">`Import-DScResource`é uma palavra-chave Dynamic, que só pode ser usada dentro de um bloco de script de configuração.</span><span class="sxs-lookup"><span data-stu-id="22974-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="22974-105">A `Import-DSCResource` palavra-chave para importar todos os recursos necessários em sua configuração.</span><span class="sxs-lookup"><span data-stu-id="22974-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="22974-106">Os recursos `$pshome` em são importados automaticamente, mas ainda é considerado uma prática recomendada importar explicitamente todos os recursos usados em sua [configuração](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="22974-106">Resources under `$pshome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="22974-107">A sintaxe do `Import-DSCResource` é mostrada abaixo.</span><span class="sxs-lookup"><span data-stu-id="22974-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="22974-108">Ao especificar módulos por nome, é um requisito para listar cada um em uma nova linha.</span><span class="sxs-lookup"><span data-stu-id="22974-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|<span data-ttu-id="22974-109">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="22974-109">Parameter</span></span>  |<span data-ttu-id="22974-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="22974-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="22974-111">Os nomes de recursos de DSC que você deve importar.</span><span class="sxs-lookup"><span data-stu-id="22974-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="22974-112">Se o nome do módulo for especificado, o comando pesquisará esses recursos de DSC dentro desse módulo; caso contrário, o comando pesquisará os recursos de DSC em todos os caminhos de recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="22974-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="22974-113">Há suporte para curingas.</span><span class="sxs-lookup"><span data-stu-id="22974-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="22974-114">O nome do módulo ou a especificação do módulo.</span><span class="sxs-lookup"><span data-stu-id="22974-114">The module name, or module specification.</span></span>  <span data-ttu-id="22974-115">Se você especificar os recursos a serem importados de um módulo, o comando tentará importar somente esses recursos.</span><span class="sxs-lookup"><span data-stu-id="22974-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="22974-116">Se você especificar apenas o módulo, o comando importará todos os recursos de DSC no módulo.</span><span class="sxs-lookup"><span data-stu-id="22974-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="22974-117">Exemplo: Usar Import-DSCResource em uma configuração</span><span class="sxs-lookup"><span data-stu-id="22974-117">Example: Use Import-DSCResource within a configuration</span></span>

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry
    
    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> <span data-ttu-id="22974-118">Não há suporte para a especificação de vários valores para nomes de recursos e nomes de módulos no mesmo comando.</span><span class="sxs-lookup"><span data-stu-id="22974-118">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="22974-119">Ele pode ter um comportamento não determinístico sobre qual recurso carregar a partir de qual módulo no caso do mesmo recurso existe em vários módulos.</span><span class="sxs-lookup"><span data-stu-id="22974-119">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="22974-120">O comando abaixo resultará em erro durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="22974-120">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="22974-121">Coisas a considerar ao usar apenas o parâmetro Name:</span><span class="sxs-lookup"><span data-stu-id="22974-121">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="22974-122">É uma operação com uso intensivo de recursos, dependendo do número de módulos instalados no computador.</span><span class="sxs-lookup"><span data-stu-id="22974-122">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="22974-123">Ele carregará o primeiro recurso encontrado com o nome fornecido.</span><span class="sxs-lookup"><span data-stu-id="22974-123">It will load the first resource found with the given name.</span></span> <span data-ttu-id="22974-124">No caso em que há mais de um recurso com o mesmo nome instalado, ele pode carregar o recurso errado.</span><span class="sxs-lookup"><span data-stu-id="22974-124">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="22974-125">O uso recomendado é especificar `–ModuleName` com o `-Name` parâmetro, conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="22974-125">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="22974-126">Esse uso tem os seguintes benefícios:</span><span class="sxs-lookup"><span data-stu-id="22974-126">This usage has the following benefits:</span></span>

- <span data-ttu-id="22974-127">Ele reduz o impacto no desempenho limitando o escopo de pesquisa para o recurso especificado.</span><span class="sxs-lookup"><span data-stu-id="22974-127">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="22974-128">Ele define explicitamente o módulo que define o recurso, garantindo que o recurso correto seja carregado.</span><span class="sxs-lookup"><span data-stu-id="22974-128">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="22974-129">No PowerShell 5,0, os recursos de DSC podem ter várias versões, e as versões podem ser instaladas em um computador lado a lado.</span><span class="sxs-lookup"><span data-stu-id="22974-129">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="22974-130">Isso é implementado com a existência de várias versões de um módulo de recurso que estão contidas na mesma pasta de módulo.</span><span class="sxs-lookup"><span data-stu-id="22974-130">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="22974-131">Para obter mais informações, consulte [usando recursos com várias versões](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="22974-131">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="22974-132">IntelliSense com Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="22974-132">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="22974-133">Ao criar a configuração de DSC no ISE, o PowerShell fornece IntelliSence para recursos e propriedades de recurso.</span><span class="sxs-lookup"><span data-stu-id="22974-133">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="22974-134">As definições de recurso `$pshome` no caminho do módulo são carregadas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="22974-134">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="22974-135">Quando você importa recursos usando a `Import-DSCResource` palavra-chave, as definições de recurso especificadas são adicionadas e o IntelliSense é expandido para incluir o esquema do recurso importado.</span><span class="sxs-lookup"><span data-stu-id="22974-135">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![IntelliSense de recurso](../media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="22974-137">A partir do PowerShell 5,0, o preenchimento com Tab foi adicionado ao ISE para recursos de DSC e suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="22974-137">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="22974-138">Para obter mais informações, consulte [recursos](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="22974-138">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="22974-139">Ao compilar a configuração, o PowerShell usa as definições de recursos importados para validar todos os blocos de recursos na configuração.</span><span class="sxs-lookup"><span data-stu-id="22974-139">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="22974-140">Cada bloco de recursos é validado, usando a definição de esquema do recurso, para as regras a seguir.</span><span class="sxs-lookup"><span data-stu-id="22974-140">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="22974-141">Somente as propriedades definidas no esquema são usadas.</span><span class="sxs-lookup"><span data-stu-id="22974-141">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="22974-142">Os tipos de dados para cada propriedade estão corretos.</span><span class="sxs-lookup"><span data-stu-id="22974-142">The data types for each property are correct.</span></span>
- <span data-ttu-id="22974-143">As propriedades das chaves são especificadas.</span><span class="sxs-lookup"><span data-stu-id="22974-143">Keys properties are specified.</span></span>
- <span data-ttu-id="22974-144">Nenhuma propriedade somente leitura é usada.</span><span class="sxs-lookup"><span data-stu-id="22974-144">No read-only property is used.</span></span>
- <span data-ttu-id="22974-145">Validação em tipos de mapas de valor.</span><span class="sxs-lookup"><span data-stu-id="22974-145">Validation on value maps types.</span></span>

<span data-ttu-id="22974-146">Considere a seguinte configuração:</span><span class="sxs-lookup"><span data-stu-id="22974-146">Consider the following configuration:</span></span>

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

<span data-ttu-id="22974-147">A compilação dessa configuração resulta em um erro.</span><span class="sxs-lookup"><span data-stu-id="22974-147">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="22974-148">O IntelliSense e a validação de esquema permitem que você pegue mais erros durante a análise e o tempo de compilação, evitando complicações no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="22974-148">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="22974-149">Cada recurso de DSC pode ter um nome e um **FriendlyName** definido pelo esquema do recurso.</span><span class="sxs-lookup"><span data-stu-id="22974-149">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="22974-150">Abaixo estão as duas primeiras linhas de "MSFT_ServiceResource. Shema. mof".</span><span class="sxs-lookup"><span data-stu-id="22974-150">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="22974-151">Ao usar esse recurso em uma configuração, você pode especificar **MSFT_ServiceResource** ou **Service**.</span><span class="sxs-lookup"><span data-stu-id="22974-151">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="22974-152">Diferenças do PowerShell v4 e V5</span><span class="sxs-lookup"><span data-stu-id="22974-152">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="22974-153">Há várias diferenças que você vê ao criar configurações no PowerShell 4,0 versus PowerShell 5,0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="22974-153">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="22974-154">Esta seção irá destacar as diferenças que você vê relevantes para este artigo.</span><span class="sxs-lookup"><span data-stu-id="22974-154">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="22974-155">Várias versões de recurso</span><span class="sxs-lookup"><span data-stu-id="22974-155">Multiple Resource Versions</span></span>

<span data-ttu-id="22974-156">Não há suporte para a instalação e o uso de várias versões de recursos lado a lado no PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="22974-156">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="22974-157">Se você notar problemas ao importar recursos para sua configuração, certifique-se de ter apenas uma versão do recurso instalada.</span><span class="sxs-lookup"><span data-stu-id="22974-157">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="22974-158">Na imagem abaixo, são instaladas duas versões do módulo **xPSDesiredStateConfiguration** .</span><span class="sxs-lookup"><span data-stu-id="22974-158">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Várias versões de recurso corrigidas](../media/multiple-resource-versions-broken.png)

<span data-ttu-id="22974-160">Copie o conteúdo da versão do módulo desejada para o nível superior do diretório do módulo.</span><span class="sxs-lookup"><span data-stu-id="22974-160">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Várias versões de recurso corrigidas](../media/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a><span data-ttu-id="22974-162">Local do recurso</span><span class="sxs-lookup"><span data-stu-id="22974-162">Resource location</span></span>

<span data-ttu-id="22974-163">Ao criar e compilar configurações, seus recursos podem ser armazenados em qualquer diretório especificado por seu [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="22974-163">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="22974-164">No PowerShell 4,0, o LCM requer que todos os módulos de recursos de DSC sejam armazenados em "Program `$pshome\Modules`Files\WindowsPowerShell\Modules" ou.</span><span class="sxs-lookup"><span data-stu-id="22974-164">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="22974-165">A partir do PowerShell 5,0, esse requisito foi removido e os módulos de recursos podem ser armazenados em qualquer diretório `PSModulePath`especificado por.</span><span class="sxs-lookup"><span data-stu-id="22974-165">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

## <a name="see-also"></a><span data-ttu-id="22974-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22974-166">See also</span></span>

- [<span data-ttu-id="22974-167">Recursos</span><span class="sxs-lookup"><span data-stu-id="22974-167">Resources</span></span>](../resources/resources.md)
