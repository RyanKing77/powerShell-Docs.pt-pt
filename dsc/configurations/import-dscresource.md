---
ms.date: 12/12/2018
keywords: DSC, do powershell, a configuração, a configuração
title: Utilizar a palavra-chave Import-DSCResource
ms.openlocfilehash: f22c741969b1429074e7307a00a5c014cf563089
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265506"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="43440-103">Utilizar a palavra-chave Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="43440-103">Using Import-DSCResource</span></span>

<span data-ttu-id="43440-104">`Import-DScResource` é uma palavra-chave dinâmica, o que só pode ser utilizada dentro de um bloco de script de configuração.</span><span class="sxs-lookup"><span data-stu-id="43440-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="43440-105">O `Import-DSCResource` palavra-chave para importar todos os recursos necessários na sua configuração.</span><span class="sxs-lookup"><span data-stu-id="43440-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="43440-106">Recursos sob `$phsome` são importados automaticamente, mas ainda é considerada como melhor prática explicitamente importar todos os recursos utilizados no seu [configuração](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="43440-106">Resources under `$phsome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="43440-107">A sintaxe para `Import-DSCResource` é mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="43440-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="43440-108">Ao especificar módulos por nome, é um requisito para listar cada numa nova linha.</span><span class="sxs-lookup"><span data-stu-id="43440-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|<span data-ttu-id="43440-109">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="43440-109">Parameter</span></span>  |<span data-ttu-id="43440-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="43440-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="43440-111">Os nomes de recursos de DSC tem de importar.</span><span class="sxs-lookup"><span data-stu-id="43440-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="43440-112">Se não for especificado o nome do módulo, o comando de procura para estes recursos de DSC dentro deste módulo; caso contrário, o comando procura os recursos de DSC em todos os caminhos de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="43440-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="43440-113">São suportados carateres universais.</span><span class="sxs-lookup"><span data-stu-id="43440-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="43440-114">O nome do módulo, ou a especificação de módulo.</span><span class="sxs-lookup"><span data-stu-id="43440-114">The module name, or module specification.</span></span>  <span data-ttu-id="43440-115">Se especificar recursos para importar a partir de um módulo, irá tentar o comando importar apenas os recursos.</span><span class="sxs-lookup"><span data-stu-id="43440-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="43440-116">Se especificar apenas o módulo, o comando importa todos os recursos de DSC no módulo.</span><span class="sxs-lookup"><span data-stu-id="43440-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="43440-117">Exemplo: Utilizar DSCResource importação dentro de uma configuração</span><span class="sxs-lookup"><span data-stu-id="43440-117">Example: Use Import-DSCResource within a configuration</span></span>

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
> <span data-ttu-id="43440-118">Especificar vários valores para os nomes de recursos e nomes de módulos no mesmo comando não são suportadas.</span><span class="sxs-lookup"><span data-stu-id="43440-118">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="43440-119">Pode ter um comportamento não determinística sobre qual o recurso para carregar a partir da qual módulo no caso de mesmo recurso existe em vários módulos.</span><span class="sxs-lookup"><span data-stu-id="43440-119">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="43440-120">Comando abaixo resultará num erro durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="43440-120">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="43440-121">Aspetos a considerar ao utilizar apenas o parâmetro de nome:</span><span class="sxs-lookup"><span data-stu-id="43440-121">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="43440-122">É uma operação intensiva de recursos, dependendo do número de módulos instalados no computador.</span><span class="sxs-lookup"><span data-stu-id="43440-122">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="43440-123">Este será carregado no primeiro recurso encontrado com o nome fornecido.</span><span class="sxs-lookup"><span data-stu-id="43440-123">It will load the first resource found with the given name.</span></span> <span data-ttu-id="43440-124">No caso onde existe mais do que um recurso com o mesmo nome instalado, foi possível carregar o recurso errado.</span><span class="sxs-lookup"><span data-stu-id="43440-124">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="43440-125">A utilização recomendada é especificar `–ModuleName` com o `-Name` parâmetro, conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="43440-125">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="43440-126">Esta utilização tem as seguintes vantagens:</span><span class="sxs-lookup"><span data-stu-id="43440-126">This usage has the following benefits:</span></span>

- <span data-ttu-id="43440-127">Reduz o impacto do desempenho ao limitar o âmbito de pesquisa para o recurso especificado.</span><span class="sxs-lookup"><span data-stu-id="43440-127">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="43440-128">Define explicitamente o módulo de definição de recurso, garantindo que o recurso correto está carregado.</span><span class="sxs-lookup"><span data-stu-id="43440-128">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="43440-129">No PowerShell 5.0, recursos de DSC podem ter várias versões e versões podem ser instaladas num computador do lado do lado a lado.</span><span class="sxs-lookup"><span data-stu-id="43440-129">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="43440-130">Isto é implementado por ter várias versões de um módulo de recursos que estão contidas na mesma pasta do módulo.</span><span class="sxs-lookup"><span data-stu-id="43440-130">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="43440-131">Para obter mais informações, consulte [através de recursos com várias versões](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="43440-131">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="43440-132">IntelliSense com DSCResource importação</span><span class="sxs-lookup"><span data-stu-id="43440-132">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="43440-133">Quando criar a configuração de DSC no ISE, o PowerShell fornece IntelliSence para recursos e propriedades de recurso.</span><span class="sxs-lookup"><span data-stu-id="43440-133">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="43440-134">Definições de recursos sob o `$pshome` do módulo caminho são carregados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="43440-134">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="43440-135">Ao importar recursos utilizando o `Import-DSCResource` palavra-chave, definições de recursos especificados são adicionadas e Intellisense é expandido para incluir o esquema do recurso importado.</span><span class="sxs-lookup"><span data-stu-id="43440-135">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![Intellisense de recursos](/media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="43440-137">Conclusão de separador a partir do PowerShell 5.0, foi adicionada ao ISE para recursos de DSC e as respetivas propriedades.</span><span class="sxs-lookup"><span data-stu-id="43440-137">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="43440-138">Para obter mais informações, consulte [recursos](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="43440-138">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="43440-139">Ao compilar a configuração, o PowerShell utiliza as definições de recursos importada para validar todos os blocos de recurso na configuração.</span><span class="sxs-lookup"><span data-stu-id="43440-139">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="43440-140">Cada bloco de recurso é validado, utilizando a definição do recurso de esquema, para as seguintes regras.</span><span class="sxs-lookup"><span data-stu-id="43440-140">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="43440-141">São utilizadas apenas propriedades definidas no esquema.</span><span class="sxs-lookup"><span data-stu-id="43440-141">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="43440-142">Os tipos de dados para cada propriedade estão corretos.</span><span class="sxs-lookup"><span data-stu-id="43440-142">The data types for each property are correct.</span></span>
- <span data-ttu-id="43440-143">Propriedades de chaves são especificadas.</span><span class="sxs-lookup"><span data-stu-id="43440-143">Keys properties are specified.</span></span>
- <span data-ttu-id="43440-144">Nenhuma propriedade só de leitura é utilizada.</span><span class="sxs-lookup"><span data-stu-id="43440-144">No read-only property is used.</span></span>
- <span data-ttu-id="43440-145">Tipos de mapas de validação no valor.</span><span class="sxs-lookup"><span data-stu-id="43440-145">Validation on value maps types.</span></span>

<span data-ttu-id="43440-146">Considere a seguinte configuração:</span><span class="sxs-lookup"><span data-stu-id="43440-146">Consider the following configuration:</span></span>

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

<span data-ttu-id="43440-147">Compilar esta resultados de configuração num erro.</span><span class="sxs-lookup"><span data-stu-id="43440-147">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="43440-148">O IntelliSense e esquema de validação permitem-lhe detetar mais erros durante a análise e compilação tempo, evitando complicações em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="43440-148">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="43440-149">Cada recurso de DSC pode ter um nome e uma **FriendlyName** definido pelo esquema do recurso.</span><span class="sxs-lookup"><span data-stu-id="43440-149">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="43440-150">Seguem-se as primeiras duas linhas de "MSFT_ServiceResource.shema.mof".</span><span class="sxs-lookup"><span data-stu-id="43440-150">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="43440-151">Quando utilizar este recurso numa configuração, pode especificar **MSFT_ServiceResource** ou **serviço**.</span><span class="sxs-lookup"><span data-stu-id="43440-151">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="43440-152">Diferenças de v4 e v5 do PowerShell</span><span class="sxs-lookup"><span data-stu-id="43440-152">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="43440-153">Existem várias diferenças que vir durante a criação de configurações no vs PowerShell 4.0. PowerShell 5.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="43440-153">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="43440-154">Esta secção irá realce as diferenças que vê relevantes para este artigo.</span><span class="sxs-lookup"><span data-stu-id="43440-154">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="43440-155">Várias versões do recurso</span><span class="sxs-lookup"><span data-stu-id="43440-155">Multiple Resource Versions</span></span>

<span data-ttu-id="43440-156">Instalar e utilizar várias versões dos recursos lado a lado não era suportada no PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="43440-156">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="43440-157">Se reparar problemas importar recursos para a configuração, certifique-se de que tem apenas uma versão do recurso instalada.</span><span class="sxs-lookup"><span data-stu-id="43440-157">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="43440-158">Na imagem abaixo, duas versões do **xPSDesiredStateConfiguration** módulo estão instalados.</span><span class="sxs-lookup"><span data-stu-id="43440-158">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Várias versões do recurso fixo](/media/multiple-resource-versions-broken.md)

<span data-ttu-id="43440-160">Copie o conteúdo da sua versão do módulo pretendido para o nível superior do diretório de módulo.</span><span class="sxs-lookup"><span data-stu-id="43440-160">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Várias versões do recurso fixo](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a><span data-ttu-id="43440-162">Localização do recurso</span><span class="sxs-lookup"><span data-stu-id="43440-162">Resource location</span></span>

<span data-ttu-id="43440-163">Quando a criação e compilar configurações, os recursos podem ser armazenados em qualquer diretório especificado pelo seu [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="43440-163">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="43440-164">No PowerShell 4.0, o MMC requer que todos os módulos de recursos de DSC sejam armazenados em "Programa Files\WindowsPowerShell\Modules" ou `$pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="43440-164">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="43440-165">A partir do PowerShell 5.0, este requisito foi removido e módulos de recursos podem ser armazenados em qualquer diretório especificado pelo `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="43440-165">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

## <a name="see-also"></a><span data-ttu-id="43440-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43440-166">See also</span></span>

- [<span data-ttu-id="43440-167">Recursos</span><span class="sxs-lookup"><span data-stu-id="43440-167">Resources</span></span>](../resources/resources.md)
