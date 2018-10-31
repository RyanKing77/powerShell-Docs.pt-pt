---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Escrever um recurso personalizado do DSC com classes do PowerShell
ms.openlocfilehash: a8f08323f2cced8a17de4224bea94a54ba5ef0cd
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226088"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a>Escrever um recurso personalizado do DSC com classes do PowerShell

> Aplica-se a: O Windows PowerShell 5.0

Com a introdução de classes do PowerShell no Windows PowerShell 5.0, agora pode definir um recurso de DSC através da criação de uma classe. A classe define o esquema e a implementação do recurso, para que não é necessário para criar um arquivo separado do MOF. A estrutura de pastas para um recurso baseado na classe também é mais simples, uma vez que um **DSCResources** pasta não é necessária.

Num recurso de DSC baseados em classe, o esquema é definido como propriedades da classe que podem ser modificados com atributos para especificar o tipo de propriedade.... O recurso é implementado pela **GET ()**, **Set()**, e **Test()** métodos (equivalente para o **Get-TargetResource**, **Set-TargetResource**, e **teste TargetResource** funções num recurso de script.

Neste tópico, vamos criar um recurso simple designado **FileResource** que gere um ficheiro num caminho especificado.

Para obter mais informações sobre os recursos de DSC, consulte [criar Windows PowerShell Desired State Configuration recursos personalizados](authoringResource.md)

>**Nota:** coleções genéricas não são suportadas em recursos baseados na classe.

## <a name="folder-structure-for-a-class-resource"></a>Estrutura de pastas para um recurso de classe

Para implementar um recurso personalizado do DSC com uma classe de PowerShell, crie a seguinte estrutura de pasta. A classe é definida no **MyDscResource.psm1** e o manifesto de módulo é definido no **MyDscResource.psd1**.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        |- MyDscResource.psm1
           MyDscResource.psd1
```

## <a name="create-the-class"></a>Criar a classe

Utilize a palavra-chave de classe para criar uma classe do PowerShell. Para especificar que uma classe é um recurso de DSC, utilize o **DscResource()** atributo. O nome da classe é o nome do recurso de DSC.

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a>Declarar propriedades

O esquema de recursos de DSC é definido como propriedades da classe. Vamos declarar três propriedades da seguinte forma.

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

Tenha em atenção que as propriedades são modificadas por atributos. O significado dos atributos é o seguinte:

- **DscProperty(Key)**: A propriedade é necessária. A propriedade é uma chave. Os valores de todas as propriedades marcado como chaves devem combinar para identificar exclusivamente uma instância de recursos dentro de uma configuração.
- **DscProperty(Mandatory)**: A propriedade é necessária.
- **DscProperty(NotConfigurable)**: A propriedade é só de leitura. Propriedades marcadas com esse atributo não pode ser definidas por uma configuração, mas são preenchidas pela **GET ()** método quando presente.
- **DscProperty()**: A propriedade pode ser configurada, mas não é necessário.

O **$Path** e **$SourcePath** propriedades são ambas as cadeias de caracteres. O **$CreationTime** é um [DateTime](https://technet.microsoft.com/library/system.datetime.aspx) propriedade. O **$Ensure** propriedade é um tipo de enumeração, definido da seguinte forma.

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a>Implementando os métodos

O **GET ()**, **Set()**, e **Test()** métodos são análogos para o **Get-TargetResource**, **TargetResource de conjunto** , e **teste TargetResource** funções num recurso de script.

Esse código também inclui a função de CopyFile(), uma função auxiliar que copia o ficheiro a partir **$SourcePath** ao **$Path**.

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

### <a name="the-complete-file"></a>O arquivo completo
Segue-se o arquivo de classe completa.

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


## <a name="create-a-manifest"></a>Criar um manifesto

Para disponibilizar um recurso baseado em classes para o motor de DSC, tem de incluir um **DscResourcesToExport** declaração no arquivo de manifesto que instrui o módulo para exportar o recurso. Nosso manifesto tem esta aparência:

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

## <a name="test-the-resource"></a>O recurso de teste

Depois de guardar a classe e os ficheiros de manifesto na estrutura de pastas, conforme descrito anteriormente, pode criar uma configuração que utiliza o novo recurso. Para obter informações sobre como executar uma configuração de DSC, veja [aplicar configurações](enactingConfigurations.md). A seguinte configuração verificará se o ficheiro no `c:\test\test.txt` existe e, se não tiver, copia o ficheiro a partir `c:\test.txt` (deve criar `c:\test.txt` antes de executar a configuração).

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

## <a name="supporting-psdscrunascredential"></a>Suporte PsDscRunAsCredential

>**Nota:** **PsDscRunAsCredential** é suportada no PowerShell 5.0 e posterior.

O **PsDscRunAsCredential** propriedade pode ser utilizada em [configurações de DSC](configurations.md) bloco de recurso para especificar que o recurso deve ser executado num conjunto especificado de credenciais.
Para obter mais informações, consulte [a executar o DSC com as credenciais de utilizador](runAsUser.md).

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a>Exigir ou não PsDscRunAsCredential para o seu recurso

O **DscResource()** atributo utiliza um parâmetro opcional **RunAsCredential**.
Este parâmetro assume um de três valores:

- `Optional` **PsDscRunAsCredential** é opcional para as configurações que chamam este recurso. Este é o valor predefinido.
- `Mandatory` **PsDscRunAsCredential** devem ser utilizados para qualquer configuração que chama este recurso.
- `NotSupported` As configurações que chamam este recurso não é possível utilizar **PsDscRunAsCredential**.
- `Default` Mesmo que `Optional`.

Por exemplo, utilize o seguinte atributo para especificar que o recurso personalizado não suporta a utilização **PsDscRunAsCredential**:

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="access-the-user-context"></a>Acessar o contexto de utilizador

Para acessar o contexto de utilizador a partir de um recurso personalizado, pode utilizar a variável automática `$global:PsDscContext`.

Por exemplo, o código a seguir escreveria o contexto do usuário sob a qual o recurso está em execução no fluxo de saída detalhada:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Consulte Também
### <a name="concepts"></a>Conceitos
[Criar recursos do Windows personalizados do PowerShell Desired State Configuration](authoringResource.md)