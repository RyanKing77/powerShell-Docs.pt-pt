---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Escrever um recurso personalizado do DSC com o MOF
ms.openlocfilehash: f243c3e3297711e6f6346a0f813a9c017fe227c3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076740"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a><span data-ttu-id="75f4c-103">Escrever um recurso personalizado do DSC com o MOF</span><span class="sxs-lookup"><span data-stu-id="75f4c-103">Writing a custom DSC resource with MOF</span></span>

> <span data-ttu-id="75f4c-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="75f4c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="75f4c-105">Neste tópico, iremos definir o esquema para um recurso personalizado do Windows PowerShell Desired State Configuration (DSC) num ficheiro MOF e, implementar o recurso num arquivo de script do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75f4c-105">In this topic, we will define the schema for a Windows PowerShell Desired State Configuration (DSC) custom resource in a MOF file, and implement the resource in a Windows PowerShell script file.</span></span> <span data-ttu-id="75f4c-106">Este recurso personalizado destina-se a criação e manutenção de um web site.</span><span class="sxs-lookup"><span data-stu-id="75f4c-106">This custom resource is for creating and maintaining a web site.</span></span>

## <a name="creating-the-mof-schema"></a><span data-ttu-id="75f4c-107">Criar o esquema MOF</span><span class="sxs-lookup"><span data-stu-id="75f4c-107">Creating the MOF schema</span></span>

<span data-ttu-id="75f4c-108">O esquema define as propriedades do seu recurso que podem ser configuradas por um script de configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="75f4c-108">The schema defines the properties of your resource that can be configured by a DSC configuration script.</span></span>

### <a name="folder-structure-for-a-mof-resource"></a><span data-ttu-id="75f4c-109">Estrutura de pastas para um recurso MOF</span><span class="sxs-lookup"><span data-stu-id="75f4c-109">Folder structure for a MOF resource</span></span>

<span data-ttu-id="75f4c-110">Para implementar um recurso personalizado do DSC com um esquema MOF, crie a seguinte estrutura de pasta.</span><span class="sxs-lookup"><span data-stu-id="75f4c-110">To implement a DSC custom resource with a MOF schema, create the following folder structure.</span></span> <span data-ttu-id="75f4c-111">O esquema da MOF é definido no ficheiro Demo_IISWebsite.schema.mof, e o script de recurso é definido no Demo_IISWebsite.psm1.</span><span class="sxs-lookup"><span data-stu-id="75f4c-111">The MOF schema is defined in the file Demo_IISWebsite.schema.mof, and the resource script is defined in Demo_IISWebsite.psm1.</span></span> <span data-ttu-id="75f4c-112">Opcionalmente, pode criar um ficheiro de manifesto (. psd1) do módulo.</span><span class="sxs-lookup"><span data-stu-id="75f4c-112">Optionally, you can create a module manifest (psd1) file.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

<span data-ttu-id="75f4c-113">Tenha em atenção que é necessário criar uma pasta denominada DSCResources sob a pasta de nível superior e que a pasta para cada recurso tem de ter o mesmo nome que o recurso.</span><span class="sxs-lookup"><span data-stu-id="75f4c-113">Note that it is necessary to create a folder named DSCResources under the top-level folder, and that the folder for each resource must have the same name as the resource.</span></span>

### <a name="the-contents-of-the-mof-file"></a><span data-ttu-id="75f4c-114">O conteúdo do ficheiro MOF</span><span class="sxs-lookup"><span data-stu-id="75f4c-114">The contents of the MOF file</span></span>

<span data-ttu-id="75f4c-115">Segue-se um ficheiro MOF de exemplo que pode ser utilizado para um recurso de Web site personalizado.</span><span class="sxs-lookup"><span data-stu-id="75f4c-115">Following is an example MOF file that can be used for a custom website resource.</span></span> <span data-ttu-id="75f4c-116">Para seguir este exemplo, salvar esse esquema num arquivo e chame o arquivo *Demo_IISWebsite.schema.mof*.</span><span class="sxs-lookup"><span data-stu-id="75f4c-116">To follow this example, save this schema to a file, and call the file *Demo_IISWebsite.schema.mof*.</span></span>

```
[ClassVersion("1.0.0"), FriendlyName("Website")]
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

<span data-ttu-id="75f4c-117">Tenha em atenção o seguinte sobre o código anterior:</span><span class="sxs-lookup"><span data-stu-id="75f4c-117">Note the following about the previous code:</span></span>

* <span data-ttu-id="75f4c-118">`FriendlyName` Define o nome que pode usar para fazer referência a este recurso personalizado em scripts de configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="75f4c-118">`FriendlyName` defines the name you can use to refer to this custom resource in DSC configuration scripts.</span></span> <span data-ttu-id="75f4c-119">Neste exemplo, `Website` é equivalente ao nome amigável `Archive` para o recurso de arquivo interno.</span><span class="sxs-lookup"><span data-stu-id="75f4c-119">In this example, `Website` is equivalent to the friendly name `Archive` for the built-in Archive resource.</span></span>
* <span data-ttu-id="75f4c-120">A classe definir para o recurso personalizado deve ser derivados dos `OMI_BaseResource`.</span><span class="sxs-lookup"><span data-stu-id="75f4c-120">The class you define for your custom resource must derive from `OMI_BaseResource`.</span></span>
* <span data-ttu-id="75f4c-121">O qualificador de tipo, `[Key]`, numa propriedade indica que esta propriedade irá identificar exclusivamente a instância de recurso.</span><span class="sxs-lookup"><span data-stu-id="75f4c-121">The type qualifier, `[Key]`, on a property indicates that this property will uniquely identify the resource instance.</span></span> <span data-ttu-id="75f4c-122">Pelo menos um `[Key]` propriedade é necessária.</span><span class="sxs-lookup"><span data-stu-id="75f4c-122">At least one `[Key]` property is required.</span></span>
* <span data-ttu-id="75f4c-123">O `[Required]` qualificador indica que a propriedade é necessária (tem de ser especificado um valor em qualquer script de configuração que utiliza este recurso).</span><span class="sxs-lookup"><span data-stu-id="75f4c-123">The `[Required]` qualifier indicates that the property is required (a value must be specified in any configuration script that uses this resource).</span></span>
* <span data-ttu-id="75f4c-124">O `[write]` qualificador indica que esta propriedade é opcional ao usar o recurso personalizado num script de configuração.</span><span class="sxs-lookup"><span data-stu-id="75f4c-124">The `[write]` qualifier indicates that this property is optional when using the custom resource in a configuration script.</span></span> <span data-ttu-id="75f4c-125">O `[read]` qualificador indica que uma propriedade não pode ser definida por uma configuração e destina-se apenas a fins de relatórios.</span><span class="sxs-lookup"><span data-stu-id="75f4c-125">The `[read]` qualifier indicates that a property cannot be set by a configuration, and is for reporting purposes only.</span></span>
* <span data-ttu-id="75f4c-126">`Values` restringe os valores que podem ser atribuídos à propriedade à lista de valores definidos no `ValueMap`.</span><span class="sxs-lookup"><span data-stu-id="75f4c-126">`Values` restricts the values that can be assigned to the property to the list of values defined in `ValueMap`.</span></span> <span data-ttu-id="75f4c-127">Para obter mais informações, consulte [ValueMap e qualificadores de valor](/windows/desktop/WmiSdk/value-map).</span><span class="sxs-lookup"><span data-stu-id="75f4c-127">For more information, see [ValueMap and Value Qualifiers](/windows/desktop/WmiSdk/value-map).</span></span>
* <span data-ttu-id="75f4c-128">Incluindo uma propriedade chamada `Ensure` com os valores `Present` e `Absent` no seu recurso, é recomendado como uma forma de manter um estilo consistente com os recursos de DSC incorporados.</span><span class="sxs-lookup"><span data-stu-id="75f4c-128">Including a property called `Ensure` with values `Present` and `Absent` in your resource is recommended as a way to maintain a consistent style with built-in DSC resources.</span></span>
* <span data-ttu-id="75f4c-129">Nomeie o arquivo de esquema para o seu recurso personalizado da seguinte forma: `classname.schema.mof`, onde `classname` é o identificador após o `class` palavra-chave em sua definição de esquema.</span><span class="sxs-lookup"><span data-stu-id="75f4c-129">Name the schema file for your custom resource as follows: `classname.schema.mof`, where `classname` is the identifier that follows the `class` keyword in your schema definition.</span></span>

### <a name="writing-the-resource-script"></a><span data-ttu-id="75f4c-130">Escrever o script de recursos</span><span class="sxs-lookup"><span data-stu-id="75f4c-130">Writing the resource script</span></span>

<span data-ttu-id="75f4c-131">O script de recurso implementa a lógica do recurso.</span><span class="sxs-lookup"><span data-stu-id="75f4c-131">The resource script implements the logic of the resource.</span></span> <span data-ttu-id="75f4c-132">Neste módulo, tem de incluir três funções chamadas **Get-TargetResource**, **conjunto TargetResource**, e **teste TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="75f4c-132">In this module, you must include three functions called **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource**.</span></span> <span data-ttu-id="75f4c-133">Todas as três funções tem de executar um conjunto de parâmetros é idêntico ao conjunto de propriedades definidas no esquema do MOF que criou para o seu recurso.</span><span class="sxs-lookup"><span data-stu-id="75f4c-133">All three functions must take a parameter set that is identical to the set of properties defined in the MOF schema that you created for your resource.</span></span> <span data-ttu-id="75f4c-134">Neste documento, este conjunto de propriedades é referido como "Propriedades de recurso."</span><span class="sxs-lookup"><span data-stu-id="75f4c-134">In this document, this set of properties is referred to as the “resource properties.”</span></span> <span data-ttu-id="75f4c-135">Store essas três funções num arquivo chamadas <ResourceName>. psm1.</span><span class="sxs-lookup"><span data-stu-id="75f4c-135">Store these three functions in a file called <ResourceName>.psm1.</span></span> <span data-ttu-id="75f4c-136">No exemplo seguinte, as funções são armazenadas num arquivo chamado Demo_IISWebsite.psm1.</span><span class="sxs-lookup"><span data-stu-id="75f4c-136">In the following example, the functions are stored in a file called Demo_IISWebsite.psm1.</span></span>

> [!NOTE]
> <span data-ttu-id="75f4c-137">Ao executar o mesmo script de configuração no recurso mais de uma vez, deverá receber sem erros e o recurso deve permanecer no mesmo Estado de execução do script de uma vez.</span><span class="sxs-lookup"><span data-stu-id="75f4c-137">When you run the same configuration script on your resource more than once, you should receive no errors and the resource should remain in the same state as running the script once.</span></span> <span data-ttu-id="75f4c-138">Para tal, certifique-se de que sua **Get-TargetResource** e **teste TargetResource** deixe de funções, o recurso inalterado e esse invocando o **conjunto-TargetResource**funcionar mais do que uma vez numa sequência com o mesmo parâmetro de valores equivale sempre ao invocá-lo uma vez.</span><span class="sxs-lookup"><span data-stu-id="75f4c-138">To accomplish this, ensure that your **Get-TargetResource** and **Test-TargetResource** functions leave the resource unchanged, and that invoking the **Set-TargetResource** function more than once in a sequence with the same parameter values is always equivalent to invoking it once.</span></span>

<span data-ttu-id="75f4c-139">Na **Get-TargetResource** implementação de função, utilize os valores de propriedade de recursos principais que são fornecidos como parâmetros para verificar o estado da instância do recurso especificado.</span><span class="sxs-lookup"><span data-stu-id="75f4c-139">In the **Get-TargetResource** function implementation, use the key resource property values that are provided as parameters to check the status of the specified resource instance.</span></span> <span data-ttu-id="75f4c-140">Esta função tem de devolver uma tabela de hash que lista todas as propriedades de recurso como chaves e valores reais dessas propriedades como os valores correspondentes.</span><span class="sxs-lookup"><span data-stu-id="75f4c-140">This function must return a hash table that lists all the resource properties as keys and the actual values of these properties as the corresponding values.</span></span> <span data-ttu-id="75f4c-141">O código a seguir fornece um exemplo.</span><span class="sxs-lookup"><span data-stu-id="75f4c-141">The following code provides an example.</span></span>

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance specified in the parameters for the target machine
function Get-TargetResource
{
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <# Insert logic that uses the mandatory parameter values to get the website and assign it to a variable called $Website #>
        <# Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
                                      Name = $Website.Name;
                                        Ensure = $ensureResult;
                                        PhysicalPath = $Website.physicalPath;
                                        State = $Website.state;
                                        ID = $Website.id;
                                        ApplicationPool = $Website.applicationPool;
                                        Protocol = $Website.bindings.Collection.protocol;
                                        Binding = $Website.bindings.Collection.bindingInformation;
                                    }

        $getTargetResourceResult;
}
```

<span data-ttu-id="75f4c-142">Dependendo dos valores que são especificados para as propriedades de recurso no script de configuração, o **Set-TargetResource** tem de efetuar um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="75f4c-142">Depending on the values that are specified for the resource properties in the configuration script, the **Set-TargetResource** must do one of the following:</span></span>

* <span data-ttu-id="75f4c-143">Criar um novo Web site</span><span class="sxs-lookup"><span data-stu-id="75f4c-143">Create a new website</span></span>
* <span data-ttu-id="75f4c-144">Atualizar um site existente</span><span class="sxs-lookup"><span data-stu-id="75f4c-144">Update an existing website</span></span>
* <span data-ttu-id="75f4c-145">Eliminar um site existente</span><span class="sxs-lookup"><span data-stu-id="75f4c-145">Delete an existing website</span></span>

<span data-ttu-id="75f4c-146">O exemplo a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="75f4c-146">The following example illustrates this.</span></span>

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine.
function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

    <# If Ensure is set to "Present" and the website specified in the mandatory input parameters does not exist, then create it using the specified parameter values #>
    <# Else, if Ensure is set to "Present" and the website does exist, then update its properties to match the values provided in the non-mandatory parameter values #>
    <# Else, if Ensure is set to "Absent" and the website does not exist, then do nothing #>
    <# Else, if Ensure is set to "Absent" and the website does exist, then delete the website #>
}
```

<span data-ttu-id="75f4c-147">Por fim, o **teste TargetResource** função tem de ter o mesmo parâmetro definido como **Get-TargetResource** e **conjunto TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="75f4c-147">Finally, the **Test-TargetResource** function must take the same parameter set as **Get-TargetResource** and **Set-TargetResource**.</span></span> <span data-ttu-id="75f4c-148">Na sua implementação do **teste TargetResource**, verificar o estado da instância do recurso que está especificado nos parâmetros de chave.</span><span class="sxs-lookup"><span data-stu-id="75f4c-148">In your implementation of **Test-TargetResource**, check the status of the resource instance that is specified in the key parameters.</span></span> <span data-ttu-id="75f4c-149">Se o estado real da instância do recurso não coincide com os valores especificados no conjunto de parâmetros, devolver **$false**.</span><span class="sxs-lookup"><span data-stu-id="75f4c-149">If the actual status of the resource instance does not match the values specified in the parameter set, return **$false**.</span></span> <span data-ttu-id="75f4c-150">Caso contrário, devolver **$true**.</span><span class="sxs-lookup"><span data-stu-id="75f4c-150">Otherwise, return **$true**.</span></span>

<span data-ttu-id="75f4c-151">O seguinte código implementa a **teste TargetResource** função.</span><span class="sxs-lookup"><span data-stu-id="75f4c-151">The following code implements the **Test-TargetResource** function.</span></span>

```powershell
function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[parameter(Mandatory = $true)]
[System.String]
$Name,

[parameter(Mandatory = $true)]
[System.String]
$PhysicalPath,

[ValidateSet("Started","Stopped")]
[System.String]
$State,

[System.String[]]
$Protocol,

[System.String[]]
$BindingData,

[System.String]
$ApplicationPool
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


#Include logic to
$result = [System.Boolean]
#Add logic to test whether the website is present and its status mathes the supplied parameter values. If it does, return true. If it does not, return false.
$result
}
```

<span data-ttu-id="75f4c-152">**Tenha em atenção**: Para depuração mais fácil, utilize o **Write-Verbose** cmdlet em sua implementação das três funções anteriores.</span><span class="sxs-lookup"><span data-stu-id="75f4c-152">**Note**: For easier debugging, use the **Write-Verbose** cmdlet in your implementation of the previous three functions.</span></span>
><span data-ttu-id="75f4c-153">Este cmdlet escreve texto no fluxo de mensagens verbosas.</span><span class="sxs-lookup"><span data-stu-id="75f4c-153">This cmdlet writes text to the verbose message stream.</span></span>
><span data-ttu-id="75f4c-154">Por predefinição, o fluxo de mensagens verbosas não for apresentado, mas pode exibi-lo ao alterar o valor do **$VerbosePreference** variável ou utilizando o **verboso** parâmetro nos cmdlets de DSC = novo.</span><span class="sxs-lookup"><span data-stu-id="75f4c-154">By default, the verbose message stream is not displayed, but you can display it by changing the value of the **$VerbosePreference** variable or by using the **Verbose** parameter in the DSC cmdlets = new.</span></span>

### <a name="creating-the-module-manifest"></a><span data-ttu-id="75f4c-155">Criando o manifesto de módulo</span><span class="sxs-lookup"><span data-stu-id="75f4c-155">Creating the module manifest</span></span>

<span data-ttu-id="75f4c-156">Por último, utilize o **New-ModuleManifest** cmdlet para definir um <ResourceName>ficheiro. psd1 para seu módulo de recurso personalizado.</span><span class="sxs-lookup"><span data-stu-id="75f4c-156">Finally, use the **New-ModuleManifest** cmdlet to define a <ResourceName>.psd1 file for your custom resource module.</span></span> <span data-ttu-id="75f4c-157">Quando invoca este cmdlet, referencia o ficheiro do módulo (. psm1) de script descrito na secção anterior.</span><span class="sxs-lookup"><span data-stu-id="75f4c-157">When you invoke this cmdlet, reference the script module (.psm1) file described in the previous section.</span></span> <span data-ttu-id="75f4c-158">Incluem **Get-TargetResource**, **conjunto TargetResource**, e **teste TargetResource** na lista de funções para exportar.</span><span class="sxs-lookup"><span data-stu-id="75f4c-158">Include **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** in the list of functions to export.</span></span> <span data-ttu-id="75f4c-159">Segue-se um ficheiro de manifesto de exemplo.</span><span class="sxs-lookup"><span data-stu-id="75f4c-159">Following is an example manifest file.</span></span>

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="75f4c-160">Suporte PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="75f4c-160">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="75f4c-161">**Nota:** **PsDscRunAsCredential** é suportada no PowerShell 5.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="75f4c-161">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="75f4c-162">O **PsDscRunAsCredential** propriedade pode ser utilizada em [configurações de DSC](../configurations/configurations.md) bloco de recurso para especificar que o recurso deve ser executado num conjunto especificado de credenciais.</span><span class="sxs-lookup"><span data-stu-id="75f4c-162">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="75f4c-163">Para obter mais informações, consulte [a executar o DSC com as credenciais de utilizador](../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="75f4c-163">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="75f4c-164">Para acessar o contexto de utilizador a partir de um recurso personalizado, pode utilizar a variável automática `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="75f4c-164">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="75f4c-165">Por exemplo, o código a seguir escreveria o contexto do usuário sob a qual o recurso está em execução no fluxo de saída detalhada:</span><span class="sxs-lookup"><span data-stu-id="75f4c-165">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="rebooting-the-node"></a><span data-ttu-id="75f4c-166">Reiniciar o nó</span><span class="sxs-lookup"><span data-stu-id="75f4c-166">Rebooting the Node</span></span>

<span data-ttu-id="75f4c-167">Se as ações executadas em seu `Set-TargetResource` função requerem um reinício, pode usar um sinalizador global para informar o LCM para reiniciar o nó.</span><span class="sxs-lookup"><span data-stu-id="75f4c-167">If the actions taken in your `Set-TargetResource` function require a reboot, you can use a global flag to tell the LCM to reboot the Node.</span></span> <span data-ttu-id="75f4c-168">Este reinício ocorre imediatamente após o `Set-TargetResource` função for concluída.</span><span class="sxs-lookup"><span data-stu-id="75f4c-168">This reboot occurs directly after the `Set-TargetResource` function completes.</span></span>

<span data-ttu-id="75f4c-169">Dentro de seu `Set-TargetResource` de função, adicione a seguinte linha de código.</span><span class="sxs-lookup"><span data-stu-id="75f4c-169">Inside your `Set-TargetResource` function, add the following line of code.</span></span>

```powershell
# Include this line if the resource requires a system reboot.
$global:DSCMachineStatus = 1
```

<span data-ttu-id="75f4c-170">Para que o MMC para reiniciar o nó, o **RebootNodeIfNeeded** sinalizador precisa ser definida `$true`.</span><span class="sxs-lookup"><span data-stu-id="75f4c-170">In order for the LCM to reboot the Node, the **RebootNodeIfNeeded** flag needs to be set to `$true`.</span></span> <span data-ttu-id="75f4c-171">O **ActionAfterReboot** definição também deve ser definida como **ContinueConfiguration**, que é a predefinição.</span><span class="sxs-lookup"><span data-stu-id="75f4c-171">The **ActionAfterReboot** setting should also be set to **ContinueConfiguration**, which is the default.</span></span> <span data-ttu-id="75f4c-172">Para obter mais informações sobre como configurar o LCM, consulte [configurar o Gestor de configuração Local](../managing-nodes/metaConfig.md), ou [configurar o Gestor de configuração Local (v4)](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="75f4c-172">For more information on configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configuring the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>
