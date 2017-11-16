---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Escrever um recurso personalizado de DSC com classes de PowerShell
ms.openlocfilehash: 6e482f45c7d09898d46de20f43dcf16ecf3da7da
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a><span data-ttu-id="61407-103">Escrever um recurso personalizado de DSC com classes de PowerShell</span><span class="sxs-lookup"><span data-stu-id="61407-103">Writing a custom DSC resource with PowerShell classes</span></span>

> <span data-ttu-id="61407-104">Aplica-se a: Windows do Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="61407-104">Applies To: Windows Windows PowerShell 5.0</span></span>

<span data-ttu-id="61407-105">Com a introdução de classes do PowerShell no Windows PowerShell 5.0, agora pode definir um recurso de DSC através da criação de uma classe.</span><span class="sxs-lookup"><span data-stu-id="61407-105">With the introduction of PowerShell classes in Windows PowerShell 5.0, you can now define a DSC resource by creating a class.</span></span> <span data-ttu-id="61407-106">A classe define o esquema e a implementação de recursos, pelo que não é necessário para criar um ficheiro MOF separado.</span><span class="sxs-lookup"><span data-stu-id="61407-106">The class defines both the schema and the implementation of the resource, so there is no need to create a separate MOF file.</span></span> <span data-ttu-id="61407-107">A estrutura da pasta para um recurso com base na classe também é mais simples, porque um **DSCResources** pasta não é necessária.</span><span class="sxs-lookup"><span data-stu-id="61407-107">The folder structure for a class-based resource is also simpler, because a **DSCResources** folder is not necessary.</span></span>

<span data-ttu-id="61407-108">Num recurso DSC baseado em classes, o esquema está definido como propriedades da classe que podem ser modificadas com os atributos para especificar o tipo de propriedade...</span><span class="sxs-lookup"><span data-stu-id="61407-108">In a class-based DSC resource, the schema is defined as properties of the class which can be modified with attributes to specify the property type..</span></span> <span data-ttu-id="61407-109">O recurso é implementado por **Get()**, **set ()**, e **Test()** métodos (equivalente para o **Get-TargetResource**, **Conjunto TargetResource**, e **teste TargetResource** as funções de um recurso de script.</span><span class="sxs-lookup"><span data-stu-id="61407-109">The resource is implemented by **Get()**, **Set()**, and **Test()** methods (equivalent to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="61407-110">Este tópico, vamos criar um recurso simple designado **FileResource** que gere um ficheiro num caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="61407-110">In this topic, we will create a simple resource named **FileResource** that manages a file in a specified path.</span></span>

<span data-ttu-id="61407-111">Para obter mais informações sobre os recursos de DSC, consulte [criar Windows PowerShell pretendido estado configuração recursos personalizados](authoringResource.md)</span><span class="sxs-lookup"><span data-stu-id="61407-111">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md)</span></span>

><span data-ttu-id="61407-112">**Nota:** coleções genéricas não são suportadas em recursos baseados na classe.</span><span class="sxs-lookup"><span data-stu-id="61407-112">**Note:** Generic collections are not supported in class-based resources.</span></span>

## <a name="folder-structure-for-a-class-resource"></a><span data-ttu-id="61407-113">Estrutura de pastas para um recurso de classe</span><span class="sxs-lookup"><span data-stu-id="61407-113">Folder structure for a class resource</span></span>

<span data-ttu-id="61407-114">Para implementar um recurso personalizado de DSC com uma classe de PowerShell, crie a seguinte estrutura de pasta.</span><span class="sxs-lookup"><span data-stu-id="61407-114">To implement a DSC custom resource with a PowerShell class, create the following folder structure.</span></span> <span data-ttu-id="61407-115">A classe está definida no **MyDscResource.psm1** e o manifesto de módulo está definido no **MyDscResource.psd1**.</span><span class="sxs-lookup"><span data-stu-id="61407-115">The class is defined in **MyDscResource.psm1** and the module manifest is defined in **MyDscResource.psd1**.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        |- MyDscResource.psm1 
           MyDscResource.psd1 
```

## <a name="create-the-class"></a><span data-ttu-id="61407-116">Criar a classe</span><span class="sxs-lookup"><span data-stu-id="61407-116">Create the class</span></span>

<span data-ttu-id="61407-117">Utilize a palavra-chave da classe para criar uma classe do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="61407-117">You use the class keyword to create a PowerShell class.</span></span> <span data-ttu-id="61407-118">Para especificar que uma classe é um recurso de DSC, utilize o **DscResource()** atributo.</span><span class="sxs-lookup"><span data-stu-id="61407-118">To specify that a class is a DSC resource, use the **DscResource()** attribute.</span></span> <span data-ttu-id="61407-119">O nome da classe é o nome do recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="61407-119">The name of the class is the name of the DSC resource.</span></span>

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a><span data-ttu-id="61407-120">Declarar as propriedades</span><span class="sxs-lookup"><span data-stu-id="61407-120">Declare properties</span></span>

<span data-ttu-id="61407-121">O esquema de recursos de DSC está definido como propriedades da classe.</span><span class="sxs-lookup"><span data-stu-id="61407-121">The DSC resource schema is defined as properties of the class.</span></span> <span data-ttu-id="61407-122">Iremos declarar três propriedades da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="61407-122">We declare three properties as follows.</span></span>

```powershell
[DscProperty(Key)]
[string]$Path

[DscProperty(Mandatory)]
[Ensure] $Ensure

[DscProperty(Mandatory)]
[string] $SourcePath

[DscProperty(NotConfigurable)]
[Nullable[datetime]] $CreationTime
```

<span data-ttu-id="61407-123">Tenha em atenção que as propriedades são modificadas por atributos.</span><span class="sxs-lookup"><span data-stu-id="61407-123">Notice that the properties are modified by attributes.</span></span> <span data-ttu-id="61407-124">O significado dos atributos é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="61407-124">The meaning of the attributes is as follows:</span></span>

- <span data-ttu-id="61407-125">**DscProperty(Key)**: A propriedade é necessária.</span><span class="sxs-lookup"><span data-stu-id="61407-125">**DscProperty(Key)**: The property is required.</span></span> <span data-ttu-id="61407-126">A propriedade é uma chave.</span><span class="sxs-lookup"><span data-stu-id="61407-126">The property is a key.</span></span> <span data-ttu-id="61407-127">Os valores de todas as propriedades marcado como chaves têm de combinar para identificar exclusivamente uma instância de recurso dentro de uma configuração.</span><span class="sxs-lookup"><span data-stu-id="61407-127">The values of all properties marked as keys must combine to uniquely identify a resource instance within a configuration.</span></span>
- <span data-ttu-id="61407-128">**DscProperty(Mandatory)**: A propriedade é necessária.</span><span class="sxs-lookup"><span data-stu-id="61407-128">**DscProperty(Mandatory)**: The property is required.</span></span>
- <span data-ttu-id="61407-129">**DscProperty(NotConfigurable)**: A propriedade é só de leitura.</span><span class="sxs-lookup"><span data-stu-id="61407-129">**DscProperty(NotConfigurable)**: The property is read-only.</span></span> <span data-ttu-id="61407-130">Propriedades marcadas com este atributo não pode ser definidas por uma configuração, mas são preenchidas pelo **Get()** método quando presente.</span><span class="sxs-lookup"><span data-stu-id="61407-130">Properties marked with this attribute cannot be set by a configuration, but are populated by the **Get()** method when present.</span></span>
- <span data-ttu-id="61407-131">**DscProperty()**: A propriedade é configurável, mas não é necessária.</span><span class="sxs-lookup"><span data-stu-id="61407-131">**DscProperty()**: The property is configurable, but it is not required.</span></span>

<span data-ttu-id="61407-132">O **$Path** e **$SourcePath** propriedades são ambas as cadeias.</span><span class="sxs-lookup"><span data-stu-id="61407-132">The **$Path** and **$SourcePath** properties are both strings.</span></span> <span data-ttu-id="61407-133">O **$CreationTime** é um [DateTime](https://technet.microsoft.com/en-us/library/system.datetime.aspx) propriedade.</span><span class="sxs-lookup"><span data-stu-id="61407-133">The **$CreationTime** is a [DateTime](https://technet.microsoft.com/en-us/library/system.datetime.aspx) property.</span></span> <span data-ttu-id="61407-134">O **$Ensure** propriedade é um tipo de enumeração definido do seguinte modo.</span><span class="sxs-lookup"><span data-stu-id="61407-134">The **$Ensure** property is an enumeration type, defined as follows.</span></span>

```powershell
enum Ensure 
{ 
    Absent 
    Present 
}
```

### <a name="implementing-the-methods"></a><span data-ttu-id="61407-135">Implementar os métodos</span><span class="sxs-lookup"><span data-stu-id="61407-135">Implementing the methods</span></span>

<span data-ttu-id="61407-136">O **Get()**, **set ()**, e **Test()** métodos são análogos ao **Get-TargetResource**, **TargetResource conjunto** , e **teste TargetResource** as funções de um recurso de script.</span><span class="sxs-lookup"><span data-stu-id="61407-136">The **Get()**, **Set()**, and **Test()** methods are analogous to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="61407-137">Este código também inclui a função de CopyFile(), uma função de programa auxiliar que copia o ficheiro de **$SourcePath** para **$Path**.</span><span class="sxs-lookup"><span data-stu-id="61407-137">This code also includes the CopyFile() function, a helper function that copies the file from **$SourcePath** to **$Path**.</span></span> 

```powershell

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)

        if ($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ErrorAction Ignore

        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = New-Object -TypeName System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
```

### <a name="the-complete-file"></a><span data-ttu-id="61407-138">O ficheiro completo</span><span class="sxs-lookup"><span data-stu-id="61407-138">The complete file</span></span>
<span data-ttu-id="61407-139">O ficheiro de classes completa segue.</span><span class="sxs-lookup"><span data-stu-id="61407-139">The complete class file follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}

<#
   This resource manages the file in a specific path.
   [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
       This property is the fully qualified path to the file that is
       expected to be present or absent.

       The [DscProperty(Key)] attribute indicates the property is a
       key and its value uniquely identifies a resource instance.
       Defining this attribute also means the property is required
       and DSC will ensure a value is set before calling the resource.

       A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
       This property defines the fully qualified path to a file that will
       be placed on the system if $Ensure = Present and $Path does not
        exist.

       NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
       This property reports the file's create timestamp.

       [DscProperty(NotConfigurable)] attribute indicates the property is
       not configurable in DSC configuration.  Properties marked this way
       are populated by the Get() method to report additional details
       about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                 to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
} # This module defines a class for a DSC "FileResource" provider.
```


## <a name="create-a-manifest"></a><span data-ttu-id="61407-140">Crie um manifesto</span><span class="sxs-lookup"><span data-stu-id="61407-140">Create a manifest</span></span>

<span data-ttu-id="61407-141">Para disponibilizar um recurso com base na classe para o motor de DSC, tem de incluir um **DscResourcesToExport** instrução no ficheiro de manifesto que dá instruções ao módulo a exportar recurso.</span><span class="sxs-lookup"><span data-stu-id="61407-141">To make a class-based resource available to the DSC engine, you must include a **DscResourcesToExport** statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="61407-142">A nossa manifesto tem o seguinte aspeto:</span><span class="sxs-lookup"><span data-stu-id="61407-142">Our manifest looks like this:</span></span>

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''
} 
```

## <a name="test-the-resource"></a><span data-ttu-id="61407-143">O recurso de teste</span><span class="sxs-lookup"><span data-stu-id="61407-143">Test the resource</span></span>

<span data-ttu-id="61407-144">Depois de guardar a classe e ficheiros de manifesto na estrutura da pasta, conforme descrito anteriormente, pode criar uma configuração que utiliza o novo recurso.</span><span class="sxs-lookup"><span data-stu-id="61407-144">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="61407-145">Para obter informações sobre como executar uma configuração de DSC, consulte [Enacting configurações](enactingConfigurations.md).</span><span class="sxs-lookup"><span data-stu-id="61407-145">For information about how to run a DSC configuration, see [Enacting configurations](enactingConfigurations.md).</span></span> <span data-ttu-id="61407-146">A seguinte configuração irá verificar se o ficheiro em `c:\test\test.txt` existe e se não, copia o ficheiro de `c:\test.txt` (deve criar `c:\test.txt` antes de executar a configuração).</span><span class="sxs-lookup"><span data-stu-id="61407-146">The following configuration will check to see whether the file at `c:\test\test.txt` exists, and, if not, copies the file from `c:\test.txt` (you should create `c:\test.txt` before you run the configuration).</span></span>

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    } 
}
Test
Start-DscConfiguration -Wait -Force Test
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="61407-147">Suporte PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="61407-147">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="61407-148">**Nota:** **PsDscRunAsCredential** é suportada no PowerShell 5.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="61407-148">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="61407-149">O **PsDscRunAsCredential** propriedade pode ser utilizada em [configurações de DSC](configurations.md) blocos de recurso para especificar que o recurso deve ser executado sob um conjunto especificado de credenciais.</span><span class="sxs-lookup"><span data-stu-id="61407-149">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="61407-150">Para obter mais informações, consulte [DSC em execução com as credenciais de utilizador](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="61407-150">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a><span data-ttu-id="61407-151">Exigir ou não permitir PsDscRunAsCredential para o seu recurso</span><span class="sxs-lookup"><span data-stu-id="61407-151">Require or disallow PsDscRunAsCredential for your resource</span></span>

<span data-ttu-id="61407-152">O **DscResource()** atributo assume um parâmetro opcional **RunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="61407-152">The **DscResource()** attribute takes an optional parameter **RunAsCredential**.</span></span>
<span data-ttu-id="61407-153">Este parâmetro assume um de três valores:</span><span class="sxs-lookup"><span data-stu-id="61407-153">This parameter takes one of three values:</span></span>

- <span data-ttu-id="61407-154">`Optional`**PsDscRunAsCredential** é opcional para as configurações que chamar este recurso.</span><span class="sxs-lookup"><span data-stu-id="61407-154">`Optional` **PsDscRunAsCredential** is optional for configurations that call this resource.</span></span> <span data-ttu-id="61407-155">Este é o valor predefinido.</span><span class="sxs-lookup"><span data-stu-id="61407-155">This is the default value.</span></span>
- <span data-ttu-id="61407-156">`Mandatory`**PsDscRunAsCredential** devem ser utilizadas para qualquer configuração que chama este recurso.</span><span class="sxs-lookup"><span data-stu-id="61407-156">`Mandatory` **PsDscRunAsCredential** must be used for any configuration that calls this resource.</span></span>
- <span data-ttu-id="61407-157">`NotSupported`Não é possível utilizar as configurações que chamar este recurso **PsDscRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="61407-157">`NotSupported` Configurations that call this resource cannot use **PsDscRunAsCredential**.</span></span>
- <span data-ttu-id="61407-158">`Default`Igual ao `Optional`.</span><span class="sxs-lookup"><span data-stu-id="61407-158">`Default` Same as `Optional`.</span></span>

<span data-ttu-id="61407-159">Por exemplo, utilize o seguinte atributo para especificar que o recurso personalizado não suporta a utilização **PsDscRunAsCredential**:</span><span class="sxs-lookup"><span data-stu-id="61407-159">For example, use the following attribute to specify that your custom resource does not support using **PsDscRunAsCredential**:</span></span>

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="access-the-user-context"></a><span data-ttu-id="61407-160">O contexto de utilizador de acesso</span><span class="sxs-lookup"><span data-stu-id="61407-160">Access the user context</span></span>

<span data-ttu-id="61407-161">Para aceder ao contexto de utilizador a partir de um recurso personalizado, pode utilizar a variável automática `$global:PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="61407-161">To access the user context from within a custom resource, you can use the automatic variable `$global:PsDscContext`.</span></span>

<span data-ttu-id="61407-162">Por exemplo o seguinte código teria de escrever o contexto de utilizador na qual o recurso está em execução no fluxo de saída verbosa:</span><span class="sxs-lookup"><span data-stu-id="61407-162">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="61407-163">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="61407-163">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="61407-164">Conceitos</span><span class="sxs-lookup"><span data-stu-id="61407-164">Concepts</span></span>
[<span data-ttu-id="61407-165">Criar recursos de configuração do estado pretendido do PowerShell de personalizada do Windows</span><span class="sxs-lookup"><span data-stu-id="61407-165">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

