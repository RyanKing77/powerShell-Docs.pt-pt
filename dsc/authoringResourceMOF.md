---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Escrever um recurso personalizado de DSC com MOF
ms.openlocfilehash: 50b5f2eddbac4571f5351b32648d45c54ded167e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a><span data-ttu-id="53b72-103">Escrever um recurso personalizado de DSC com MOF</span><span class="sxs-lookup"><span data-stu-id="53b72-103">Writing a custom DSC resource with MOF</span></span>

> <span data-ttu-id="53b72-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="53b72-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="53b72-105">Neste tópico, iremos definir o esquema para um recurso personalizado de configuração de estado pretendido do Windows PowerShell (DSC) num ficheiro MOF e implementar o recurso de um ficheiro de script do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="53b72-105">In this topic, we will define the schema for a Windows PowerShell Desired State Configuration (DSC) custom resource in a MOF file, and implement the resource in a Windows PowerShell script file.</span></span> <span data-ttu-id="53b72-106">Este recurso personalizado destina-se a criação e manutenção de um web site.</span><span class="sxs-lookup"><span data-stu-id="53b72-106">This custom resource is for creating and maintaining a web site.</span></span>

## <a name="creating-the-mof-schema"></a><span data-ttu-id="53b72-107">Criar o esquema MOF</span><span class="sxs-lookup"><span data-stu-id="53b72-107">Creating the MOF schema</span></span>

<span data-ttu-id="53b72-108">O esquema define as propriedades dos seus recursos que podem ser configuradas por um script de configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="53b72-108">The schema defines the properties of your resource that can be configured by a DSC configuration script.</span></span>

### <a name="folder-structure-for-a-mof-resource"></a><span data-ttu-id="53b72-109">Estrutura de pastas para um recurso MOF</span><span class="sxs-lookup"><span data-stu-id="53b72-109">Folder structure for a MOF resource</span></span>

<span data-ttu-id="53b72-110">Para implementar um recurso personalizado de DSC com um esquema MOF, crie a seguinte estrutura de pasta.</span><span class="sxs-lookup"><span data-stu-id="53b72-110">To implement a DSC custom resource with a MOF schema, create the following folder structure.</span></span> <span data-ttu-id="53b72-111">O esquema MOF está definido no ficheiro Demo_IISWebsite.schema.mof e o script de recursos está definido no Demo_IISWebsite.psm1.</span><span class="sxs-lookup"><span data-stu-id="53b72-111">The MOF schema is defined in the file Demo_IISWebsite.schema.mof, and the resource script is defined in Demo_IISWebsite.psm1.</span></span> <span data-ttu-id="53b72-112">Opcionalmente, pode criar um ficheiro de manifesto (. psd1) do módulo.</span><span class="sxs-lookup"><span data-stu-id="53b72-112">Optionally, you can create a module manifest (psd1) file.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

<span data-ttu-id="53b72-113">Tenha em atenção que é necessário criar uma pasta denominada DSCResources sob a pasta de nível superior e que a pasta para cada recurso têm de ter o mesmo nome que o recurso.</span><span class="sxs-lookup"><span data-stu-id="53b72-113">Note that it is necessary to create a folder named DSCResources under the top-level folder, and that the folder for each resource must have the same name as the resource.</span></span>

### <a name="the-contents-of-the-mof-file"></a><span data-ttu-id="53b72-114">O conteúdo do ficheiro MOF</span><span class="sxs-lookup"><span data-stu-id="53b72-114">The contents of the MOF file</span></span>

<span data-ttu-id="53b72-115">Segue-se um ficheiro MOF de exemplo que pode ser utilizado para um recurso de Web site personalizado.</span><span class="sxs-lookup"><span data-stu-id="53b72-115">Following is an example MOF file that can be used for a custom website resource.</span></span> <span data-ttu-id="53b72-116">Para seguir este exemplo, guarde este esquema de um ficheiro e chamar o ficheiro *Demo_IISWebsite.schema.mof*.</span><span class="sxs-lookup"><span data-stu-id="53b72-116">To follow this example, save this schema to a file, and call the file *Demo_IISWebsite.schema.mof*.</span></span>

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

<span data-ttu-id="53b72-117">Tenha em atenção o seguinte sobre o código anterior:</span><span class="sxs-lookup"><span data-stu-id="53b72-117">Note the following about the previous code:</span></span>

* <span data-ttu-id="53b72-118">`FriendlyName` Define o nome que pode utilizar para fazer referência a este recurso personalizado em scripts de configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="53b72-118">`FriendlyName` defines the name you can use to refer to this custom resource in DSC configuration scripts.</span></span> <span data-ttu-id="53b72-119">Neste exemplo, `Website` é equivalente ao nome amigável `Archive` para o recurso de arquivo incorporado.</span><span class="sxs-lookup"><span data-stu-id="53b72-119">In this example, `Website` is equivalent to the friendly name `Archive` for the built-in Archive resource.</span></span>
* <span data-ttu-id="53b72-120">A classe definir para o recurso personalizado tem de derivar de `OMI_BaseResource`.</span><span class="sxs-lookup"><span data-stu-id="53b72-120">The class you define for your custom resource must derive from `OMI_BaseResource`.</span></span>
* <span data-ttu-id="53b72-121">O qualificador do tipo, `[Key]`, uma propriedade indica que esta propriedade identifiquem exclusivamente a instância de recurso.</span><span class="sxs-lookup"><span data-stu-id="53b72-121">The type qualifier, `[Key]`, on a property indicates that this property will uniquely identify the resource instance.</span></span> <span data-ttu-id="53b72-122">Pelo menos um `[Key]` propriedade é necessária.</span><span class="sxs-lookup"><span data-stu-id="53b72-122">At least one `[Key]` property is required.</span></span>
* <span data-ttu-id="53b72-123">O `[Required]` qualificador indica que a propriedade é necessária (um valor tem de ser especificado qualquer script de configuração que utiliza este recurso).</span><span class="sxs-lookup"><span data-stu-id="53b72-123">The `[Required]` qualifier indicates that the property is required (a value must be specified in any configuration script that uses this resource).</span></span>
* <span data-ttu-id="53b72-124">O `[write]` qualificador indica que esta propriedade é opcional quando o recurso personalizado num script de configuração.</span><span class="sxs-lookup"><span data-stu-id="53b72-124">The `[write]` qualifier indicates that this property is optional when using the custom resource in a configuration script.</span></span> <span data-ttu-id="53b72-125">O `[read]` qualificador indica que uma propriedade não pode ser definida por uma configuração e, para fins de relatórios.</span><span class="sxs-lookup"><span data-stu-id="53b72-125">The `[read]` qualifier indicates that a property cannot be set by a configuration, and is for reporting purposes only.</span></span>
* <span data-ttu-id="53b72-126">`Values` restringe os valores que podem ser atribuídos a propriedade à lista de valores definidos no `ValueMap`.</span><span class="sxs-lookup"><span data-stu-id="53b72-126">`Values` restricts the values that can be assigned to the property to the list of values defined in `ValueMap`.</span></span> <span data-ttu-id="53b72-127">Para obter mais informações, consulte [ValueMap e qualificadores de valor](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).</span><span class="sxs-lookup"><span data-stu-id="53b72-127">For more information, see [ValueMap and Value Qualifiers](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).</span></span>
* <span data-ttu-id="53b72-128">Incluindo uma propriedade denominada `Ensure` com valores `Present` e `Absent` no seu recurso é recomendado como uma forma para manter um estilo consistente com os recursos de DSC incorporados.</span><span class="sxs-lookup"><span data-stu-id="53b72-128">Including a property called `Ensure` with values `Present` and `Absent` in your resource is recommended as a way to maintain a consistent style with built-in DSC resources.</span></span>
* <span data-ttu-id="53b72-129">Nome do ficheiro de esquema para o seu recurso personalizado da seguinte forma: `classname.schema.mof`, onde `classname` é o identificador que se segue o `class` palavra-chave na definição de esquema.</span><span class="sxs-lookup"><span data-stu-id="53b72-129">Name the schema file for your custom resource as follows: `classname.schema.mof`, where `classname` is the identifier that follows the `class` keyword in your schema definition.</span></span>

### <a name="writing-the-resource-script"></a><span data-ttu-id="53b72-130">Escrever o script de recursos</span><span class="sxs-lookup"><span data-stu-id="53b72-130">Writing the resource script</span></span>

<span data-ttu-id="53b72-131">O script de recurso implementa a lógica do recurso.</span><span class="sxs-lookup"><span data-stu-id="53b72-131">The resource script implements the logic of the resource.</span></span> <span data-ttu-id="53b72-132">Este módulo, tem de incluir três funções chamadas **Get-TargetResource**, **conjunto TargetResource**, e **teste TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="53b72-132">In this module, you must include three functions called **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource**.</span></span> <span data-ttu-id="53b72-133">Todos os três funções tem de colocar um conjunto de parâmetros é idêntico ao conjunto de propriedades definida no esquema MOF que criou para o seu recurso.</span><span class="sxs-lookup"><span data-stu-id="53b72-133">All three functions must take a parameter set that is identical to the set of properties defined in the MOF schema that you created for your resource.</span></span> <span data-ttu-id="53b72-134">Neste documento, este conjunto de propriedades é referido como "Propriedades de recurso."</span><span class="sxs-lookup"><span data-stu-id="53b72-134">In this document, this set of properties is referred to as the “resource properties.”</span></span> <span data-ttu-id="53b72-135">Arquivo estas três funções num ficheiro denominadas <ResourceName>. psm1.</span><span class="sxs-lookup"><span data-stu-id="53b72-135">Store these three functions in a file called <ResourceName>.psm1.</span></span> <span data-ttu-id="53b72-136">No exemplo seguinte, as funções são armazenadas num ficheiro denominado Demo_IISWebsite.psm1.</span><span class="sxs-lookup"><span data-stu-id="53b72-136">In the following example, the functions are stored in a file called Demo_IISWebsite.psm1.</span></span>

> <span data-ttu-id="53b72-137">**Tenha em atenção**: quando executar o mesmo script de configuração no seu recurso mais do que uma vez, deverá receber sem erros e de recursos devem permanecer no mesmo estado como executar o script de uma vez.</span><span class="sxs-lookup"><span data-stu-id="53b72-137">**Note**: When you run the same configuration script on your resource more than once, you should receive no errors and the resource should remain in the same state as running the script once.</span></span> <span data-ttu-id="53b72-138">Para tal, certifique-se de que o **Get-TargetResource** e **teste TargetResource** deixe de funções inalterado do recurso e que invocar o **Set-TargetResource**funcionar mais do que uma vez numa sequência com o mesmo parâmetro de valores é sempre equivalente ao invocar, uma vez.</span><span class="sxs-lookup"><span data-stu-id="53b72-138">To accomplish this, ensure that your **Get-TargetResource** and **Test-TargetResource** functions leave the resource unchanged, and that invoking the **Set-TargetResource** function more than once in a sequence with the same parameter values is always equivalent to invoking it once.</span></span>

<span data-ttu-id="53b72-139">No **Get-TargetResource** implementação de função, utilize os valores de propriedade de chave de recurso que são fornecidos como parâmetros para verificar o estado da instância do recurso especificado.</span><span class="sxs-lookup"><span data-stu-id="53b72-139">In the **Get-TargetResource** function implementation, use the key resource property values that are provided as parameters to check the status of the specified resource instance.</span></span> <span data-ttu-id="53b72-140">Esta função tem de devolver uma tabela hash que apresenta uma lista de todas as propriedades de recurso como chaves e os valores reais destas propriedades como os valores correspondentes.</span><span class="sxs-lookup"><span data-stu-id="53b72-140">This function must return a hash table that lists all the resource properties as keys and the actual values of these properties as the corresponding values.</span></span> <span data-ttu-id="53b72-141">O código seguinte fornece um exemplo.</span><span class="sxs-lookup"><span data-stu-id="53b72-141">The following code provides an example.</span></span>

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

<span data-ttu-id="53b72-142">Consoante os valores que são especificados para as propriedades de recurso no script de configuração, o **conjunto TargetResource** tem de efetuar um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="53b72-142">Depending on the values that are specified for the resource properties in the configuration script, the **Set-TargetResource** must do one of the following:</span></span>

* <span data-ttu-id="53b72-143">Criar um novo Web site</span><span class="sxs-lookup"><span data-stu-id="53b72-143">Create a new website</span></span>
* <span data-ttu-id="53b72-144">Atualizar um site existente</span><span class="sxs-lookup"><span data-stu-id="53b72-144">Update an existing website</span></span>
* <span data-ttu-id="53b72-145">Eliminar um Web site existente</span><span class="sxs-lookup"><span data-stu-id="53b72-145">Delete an existing website</span></span>

<span data-ttu-id="53b72-146">O exemplo a seguir ilustra este.</span><span class="sxs-lookup"><span data-stu-id="53b72-146">The following example illustrates this.</span></span>

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

<span data-ttu-id="53b72-147">Por fim, o **teste TargetResource** função tem de ter o mesmo parâmetro definido como **Get-TargetResource** e **conjunto TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="53b72-147">Finally, the **Test-TargetResource** function must take the same parameter set as **Get-TargetResource** and **Set-TargetResource**.</span></span> <span data-ttu-id="53b72-148">Na sua implementação do **teste TargetResource**, verifique o estado da instância de recurso que foi especificado nos parâmetros de chaves.</span><span class="sxs-lookup"><span data-stu-id="53b72-148">In your implementation of **Test-TargetResource**, check the status of the resource instance that is specified in the key parameters.</span></span> <span data-ttu-id="53b72-149">Se o estado real da instância do recurso não correspondem aos valores especificados no conjunto de parâmetros, devolver **$false**.</span><span class="sxs-lookup"><span data-stu-id="53b72-149">If the actual status of the resource instance does not match the values specified in the parameter set, return **$false**.</span></span> <span data-ttu-id="53b72-150">Caso contrário, devolve **$true**.</span><span class="sxs-lookup"><span data-stu-id="53b72-150">Otherwise, return **$true**.</span></span>

<span data-ttu-id="53b72-151">O seguinte código implementa o **teste TargetResource** função.</span><span class="sxs-lookup"><span data-stu-id="53b72-151">The following code implements the **Test-TargetResource** function.</span></span>

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

<span data-ttu-id="53b72-152">**Tenha em atenção**: para depuração mais fácil, utilize o **Write-Verbose** cmdlet na sua implementação das três funções anteriores.</span><span class="sxs-lookup"><span data-stu-id="53b72-152">**Note**: For easier debugging, use the **Write-Verbose** cmdlet in your implementation of the previous three functions.</span></span>
><span data-ttu-id="53b72-153">Este cmdlet escreve o texto no fluxo de mensagens verbosas.</span><span class="sxs-lookup"><span data-stu-id="53b72-153">This cmdlet writes text to the verbose message stream.</span></span>
><span data-ttu-id="53b72-154">Por predefinição, o fluxo de mensagens verbosas não for apresentado, mas pode apresentá-lo alterando o valor da **$VerbosePreference** variável ou utilizando o **verboso** parâmetro os cmdlets do DSC = novos.</span><span class="sxs-lookup"><span data-stu-id="53b72-154">By default, the verbose message stream is not displayed, but you can display it by changing the value of the **$VerbosePreference** variable or by using the **Verbose** parameter in the DSC cmdlets = new.</span></span>

### <a name="creating-the-module-manifest"></a><span data-ttu-id="53b72-155">Criar o manifesto de módulo</span><span class="sxs-lookup"><span data-stu-id="53b72-155">Creating the module manifest</span></span>

<span data-ttu-id="53b72-156">Por último, utilize o **New-ModuleManifest** cmdlet para definir um <ResourceName>. psd1 ficheiro para o módulo de recurso personalizado.</span><span class="sxs-lookup"><span data-stu-id="53b72-156">Finally, use the **New-ModuleManifest** cmdlet to define a <ResourceName>.psd1 file for your custom resource module.</span></span> <span data-ttu-id="53b72-157">Quando invocar este cmdlet, referencia o ficheiro de script do módulo (. psm1) descrito na secção anterior.</span><span class="sxs-lookup"><span data-stu-id="53b72-157">When you invoke this cmdlet, reference the script module (.psm1) file described in the previous section.</span></span> <span data-ttu-id="53b72-158">Incluir **Get-TargetResource**, **conjunto TargetResource**, e **teste TargetResource** na lista de funções para exportar.</span><span class="sxs-lookup"><span data-stu-id="53b72-158">Include **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** in the list of functions to export.</span></span> <span data-ttu-id="53b72-159">Segue-se um ficheiro de manifesto de exemplo.</span><span class="sxs-lookup"><span data-stu-id="53b72-159">Following is an example manifest file.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="53b72-160">Suporte PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="53b72-160">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="53b72-161">**Nota:** **PsDscRunAsCredential** é suportada no PowerShell 5.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="53b72-161">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="53b72-162">O **PsDscRunAsCredential** propriedade pode ser utilizada em [configurações de DSC](configurations.md) blocos de recurso para especificar que o recurso deve ser executado sob um conjunto especificado de credenciais.</span><span class="sxs-lookup"><span data-stu-id="53b72-162">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="53b72-163">Para obter mais informações, consulte [DSC em execução com as credenciais de utilizador](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="53b72-163">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

<span data-ttu-id="53b72-164">Para aceder ao contexto de utilizador a partir de um recurso personalizado, pode utilizar a variável automática `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="53b72-164">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="53b72-165">Por exemplo o seguinte código teria de escrever o contexto de utilizador na qual o recurso está em execução no fluxo de saída verbosa:</span><span class="sxs-lookup"><span data-stu-id="53b72-165">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```