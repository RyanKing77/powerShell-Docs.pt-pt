---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Utilizar a palavra-chave Import-DSCResource
ms.openlocfilehash: 6bc3c1aa1d34a05e3188666da825322235c0672e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686615"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="c1fa8-103">Utilizar a palavra-chave Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="c1fa8-103">Using Import-DSCResource</span></span>

<span data-ttu-id="c1fa8-104">`Import-DScResource` é uma palavra-chave dynamic, o que só pode ser utilizada dentro de um bloco de script de configuração.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="c1fa8-105">O `Import-DSCResource` palavra-chave para importar todos os recursos necessários na sua configuração.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="c1fa8-106">Recursos sob `$phsome` são importados automaticamente, mas ainda é considerada uma prática recomendada para importar explicitamente todos os recursos utilizados na sua [configuração](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="c1fa8-106">Resources under `$phsome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="c1fa8-107">A sintaxe para `Import-DSCResource` é mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-107">The syntax for `Import-DSCResource` is shown below.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>]
```

|<span data-ttu-id="c1fa8-108">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="c1fa8-108">Parameter</span></span>  |<span data-ttu-id="c1fa8-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1fa8-109">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="c1fa8-110">Os nomes de recursos de DSC que tem de importar.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-110">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="c1fa8-111">Se não for especificado o nome do módulo, o comando procura estes recursos de DSC dentro deste módulo; caso contrário, o comando procura os recursos de DSC em todos os caminhos de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-111">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="c1fa8-112">São suportados carateres universais.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-112">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="c1fa8-113">O nome de módulo de contentor (s), ou as especificações de módulo.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-113">The container module name(s), or module specification(s).</span></span>  <span data-ttu-id="c1fa8-114">Se especificar recursos para importar a partir de um módulo, irá tentar o comando importar apenas os recursos.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-114">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="c1fa8-115">Se especificar apenas o módulo, o comando importa todos os recursos de DSC no módulo.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-115">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|

<span data-ttu-id="c1fa8-116">Pode utilizar carateres universais com o `-Name` parâmetro ao usar `Import-DSCResource`.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-116">You can use wildcards with the `-Name` parameter when using `Import-DSCResource`.</span></span>

```powershell
Import-DscResource -Name * -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="c1fa8-117">Exemplo: Utilizar Import-DSCResource dentro de uma configuração</span><span class="sxs-lookup"><span data-stu-id="c1fa8-117">Example: Use Import-DSCResource within a configuration</span></span>

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName MS_DSC1 -name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    Import-DSCResource -Name File, TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
...
```

> [!NOTE]
> <span data-ttu-id="c1fa8-118">Especificar vários valores para os nomes de recursos e nomes de módulos no mesmo comando não são suportadas.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-118">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="c1fa8-119">Ele pode ter um comportamento determinística sobre o recurso a carregar a partir do qual módulo no caso o mesmo recurso existe em vários módulos.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-119">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="c1fa8-120">Comando abaixo resultará no erro durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-120">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="c1fa8-121">Aspetos a considerar ao utilizar apenas o parâmetro de nome:</span><span class="sxs-lookup"><span data-stu-id="c1fa8-121">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="c1fa8-122">É uma operação com muitos recursos, dependendo do número de módulos instalados no computador.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-122">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="c1fa8-123">Ele carregará o primeiro recurso encontrado com o nome fornecido.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-123">It will load the first resource found with the given name.</span></span> <span data-ttu-id="c1fa8-124">No caso em que existe mais do que um recurso com o mesmo nome instalado, ele foi possível carregar o recurso de errado.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-124">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="c1fa8-125">A utilização recomendada consiste em especificar `–ModuleName` com o `-Name` parâmetro, conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-125">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="c1fa8-126">Esta utilização tem as seguintes vantagens:</span><span class="sxs-lookup"><span data-stu-id="c1fa8-126">This usage has the following benefits:</span></span>

- <span data-ttu-id="c1fa8-127">Reduz o impacto no desempenho ao limitar o âmbito de pesquisa para o recurso especificado.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-127">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="c1fa8-128">Ele define explicitamente o módulo de definição do recurso, garantir que o recurso correto é carregado.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-128">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="c1fa8-129">No PowerShell 5.0, recursos de DSC podem ter várias versões e versões podem ser instaladas numa computador lado a lado.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-129">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="c1fa8-130">Isso é implementado fazendo com que várias versões de um módulo de recursos que estão contidas na mesma pasta do módulo.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-130">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="c1fa8-131">Para obter mais informações, consulte [utilizar recursos com várias versões](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="c1fa8-131">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="c1fa8-132">IntelliSense com Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="c1fa8-132">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="c1fa8-133">Ao criar a configuração de DSC no ISE, o PowerShell fornece IntelliSence para recursos e propriedades de recurso.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-133">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="c1fa8-134">Definições de recursos sob o `$pshome` caminho do módulo são carregados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-134">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="c1fa8-135">Ao importar recursos com o `Import-DSCResource` palavra-chave, as definições de recurso especificado são adicionadas e Intellisense é expandido para incluir o esquema do recurso importados.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-135">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![Recurso Intellisense](/media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="c1fa8-137">A partir do PowerShell 5.0, conclusão de tabulação foi adicionado ao ISE para recursos de DSC e as respetivas propriedades.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-137">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="c1fa8-138">Para obter mais informações, consulte [recursos](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="c1fa8-138">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="c1fa8-139">Ao compilar a configuração, o PowerShell utiliza definições de recursos importada para validar todos os blocos de recursos na configuração.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-139">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="c1fa8-140">Cada bloco de recursos é validado, com a definição de esquema do recurso, para as seguintes regras.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-140">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="c1fa8-141">Apenas as propriedades definidas no esquema são utilizadas.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-141">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="c1fa8-142">Os tipos de dados para cada propriedade estão corretos.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-142">The data types for each property are correct.</span></span>
- <span data-ttu-id="c1fa8-143">As propriedades de chaves são especificadas.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-143">Keys properties are specified.</span></span>
- <span data-ttu-id="c1fa8-144">Nenhuma propriedade só de leitura é utilizada.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-144">No read-only property is used.</span></span>
- <span data-ttu-id="c1fa8-145">Validação no valor mapeia tipos.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-145">Validation on value maps types.</span></span>

<span data-ttu-id="c1fa8-146">Considere a seguinte configuração:</span><span class="sxs-lookup"><span data-stu-id="c1fa8-146">Consider the following configuration:</span></span>

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

<span data-ttu-id="c1fa8-147">Compilar esta resultados de configuração num erro.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-147">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="c1fa8-148">Validação de esquema e IntelliSense permitem-lhe capturar mais erros durante o tempo de análise e compilação, evitando complicações em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-148">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="c1fa8-149">Cada recurso de DSC pode ter um nome e um **FriendlyName** definida pelo esquema do recurso.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-149">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="c1fa8-150">Seguem-se as duas primeiras linhas de "MSFT_ServiceResource.shema.mof".</span><span class="sxs-lookup"><span data-stu-id="c1fa8-150">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="c1fa8-151">Ao usar este recurso numa configuração, pode especificar **MSFT_ServiceResource** ou **serviço**.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-151">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="c1fa8-152">Diferenças de PowerShell v4 e v5</span><span class="sxs-lookup"><span data-stu-id="c1fa8-152">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="c1fa8-153">Existem várias diferenças que verá quando a criação de configurações no PowerShell 4.0 vs. PowerShell 5.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-153">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="c1fa8-154">Esta secção irá realçar as diferenças que vê relevantes para este artigo.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-154">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="c1fa8-155">Várias versões de recursos</span><span class="sxs-lookup"><span data-stu-id="c1fa8-155">Multiple Resource Versions</span></span>

<span data-ttu-id="c1fa8-156">Instalar e utilizar várias versões de recursos lado a lado não era suportada no PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-156">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="c1fa8-157">Caso se depare com problemas importar recursos para a sua configuração, certifique-se de que tem apenas uma versão do recurso instalada.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-157">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="c1fa8-158">Na imagem abaixo, duas versões dos **xPSDesiredStateConfiguration** módulo são instalados.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-158">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Várias versões de recursos foi corrigidas](/media/multiple-resource-versions-broken.md)

<span data-ttu-id="c1fa8-160">Copie o conteúdo da sua versão do módulo pretendido para o nível superior do diretório de módulo.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-160">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Várias versões de recursos foi corrigidas](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a><span data-ttu-id="c1fa8-162">Localização do recurso</span><span class="sxs-lookup"><span data-stu-id="c1fa8-162">Resource location</span></span>

<span data-ttu-id="c1fa8-163">Ao criar e compilar configurações, os seus recursos podem ser armazenados em qualquer diretório especificado pelo seu [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="c1fa8-163">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="c1fa8-164">No PowerShell 4.0, o LCM requer que todos os módulos de recursos de DSC sejam armazenados em "Programa Files\WindowsPowerShell\Modules" ou `$pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-164">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="c1fa8-165">A partir do PowerShell 5.0, este requisito foi removido e módulos de recursos podem ser armazenados em qualquer diretório especificado por `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="c1fa8-165">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1fa8-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1fa8-166">See also</span></span>

- [<span data-ttu-id="c1fa8-167">Recursos</span><span class="sxs-lookup"><span data-stu-id="c1fa8-167">Resources</span></span>](../resources/resources.md)
