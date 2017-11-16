---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Recursos compostos - através de uma configuração de DSC como um recurso"
ms.openlocfilehash: 6c9a878c45a3e999e20dec5766ee8bda409905d3
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a>Recursos compostos: utilizar uma configuração de DSC como um recurso

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

Em situações de mundo real, configurações podem tornar-se muito complexas, chamar muitos recursos diferentes e a definição de um grande número de propriedades. Para ajudar a resolver este complexidade, pode utilizar uma configuração de configuração de estado pretendido do Windows PowerShell (DSC) como um recurso para outras configurações. Chamamos a isto um recurso composto. Um recurso composto é uma configuração de DSC que aceita parâmetros. Os parâmetros da configuração atuam como as propriedades do recurso. A configuração é guardada como um ficheiro com um **. schema.psm1** extensão e demora o local de esquema MOF e o recurso de script num recurso DSC típico (para obter mais informações sobre os recursos de DSC, consulte [Windows Recursos de configuração do estado pretendido do PowerShell](resources.md).

## <a name="creating-the-composite-resource"></a>Criar o recurso composto

No nosso exemplo, vamos criar uma configuração que invoca uma série de recursos existentes para configurar as máquinas virtuais. Em vez de especificar os valores para ser definido em blocos de configuração, a configuração cria um número de parâmetros que, em seguida, são utilizados em blocos de configuração.

```powershell
Configuration xVirtualMachine
{
    param
    (
        # Name of VMs
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String[]] $VMName,

        # Name of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchName,

        # Type of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchType,

        # Source Path for VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDParentPath,

        # Destination path for diff VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDPath,

        # Startup Memory for VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMStartupMemory,

        # State of the VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMState
    )

    # Import the module that defines custom resources
    Import-DscResource -Module xComputerManagement,xHyper-V

    # Install the Hyper-V role
    WindowsFeature HyperV
    {
        Ensure = "Present"
        Name = "Hyper-V"
    }

    # Create the virtual switch
    xVMSwitch $SwitchName
    {
        Ensure = "Present"
        Name = $SwitchName
        Type = $SwitchType
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check for Parent VHD file
    File ParentVHDFile
    {
        Ensure = "Present"
        DestinationPath = $VHDParentPath
        Type = "File"
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check the destination VHD folder
    File VHDFolder
    {
        Ensure = "Present"
        DestinationPath = $VHDPath
        Type = "Directory"
        DependsOn = "[File]ParentVHDFile"
    }

    # Creae VM specific diff VHD
    foreach ($Name in $VMName)
    {
        xVHD "VHD$Name"
        {
            Ensure = "Present"
            Name = $Name
            Path = $VHDPath
            ParentPath = $VHDParentPath
            DependsOn = @("[WindowsFeature]HyperV",
                          "[File]VHDFolder")
        }
    }

    # Create VM using the above VHD
    foreach($Name in $VMName)
    {
        xVMHyperV "VMachine$Name"
        {
            Ensure = "Present"
            Name = $Name
            VhDPath = (Join-Path -Path $VHDPath -ChildPath $Name)
            SwitchName = $SwitchName
            StartupMemory = $VMStartupMemory
            State = $VMState
            MACAddress = $MACAddress
            WaitForIP = $true
            DependsOn = @("[WindowsFeature]HyperV",
                          "[xVHD]VHD$Name")
        }
    }
}
```

### <a name="saving-the-configuration-as-a-composite-resource"></a>Guardar a configuração como um recurso composto

Para utilizar a configuração parametrizada como um recurso de DSC, guarde-o numa estrutura de diretórios como que quaisquer outros recursos baseados em MOF e atribua o nome com um **. schema.psm1** extensão. Neste exemplo, iremos irá nome ao ficheiro **xVirtualMachine.schema.psm1**. Também tem de criar um manifesto com o nome **xVirtualMachine.psd1** que contém a seguinte linha. Tenha em atenção que isto é, para além **MyDscResources.psd1**, o manifesto de módulo para todos os recursos sob o **MyDscResources** pasta.

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

Quando tiver terminado, a estrutura da pasta deve ser o seguinte.

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

O recurso está agora detetável utilizando o cmdlet Get-DscResource e as respetivas propriedades são Detetáveis pela esse cmdlet ou utilizando **Ctrl + espaço** a conclusão automática no ISE do Windows PowerShell.

## <a name="using-the-composite-resource"></a>Utilizar o recurso composto

Em seguida, iremos criar uma configuração que chama o recurso composto. Esta configuração chama o recurso composto xVirtualMachine para criar uma máquina virtual e, em seguida, chama o **xComputer** recursos para alterá-lo.

```powershell

configuration RenameVM
{

    Import-DscResource -Module TestCompositeResource
    Node localhost
    {
        xVirtualMachine VM
        {
            VMName = "Test"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }

    Node "192.168.10.1"
    {
        xComputer Name
        {
            Name = "SQL01"
            DomainName = "fourthcoffee.com"
        }
    }
}
```

## <a name="supporting-psdscrunascredential"></a>Suporte PsDscRunAsCredential

>**Nota:** **PsDscRunAsCredential** é suportada no PowerShell 5.0 e posterior.

O **PsDscRunAsCredential** propriedade pode ser utilizada em [configurações de DSC](configurations.md) blocos de recurso para especificar que o recurso deve ser executado sob um conjunto especificado de credenciais.
Para obter mais informações, consulte [DSC em execução com as credenciais de utilizador](runAsUser.md).

Para aceder ao contexto de utilizador a partir de um recurso personalizado, pode utilizar a variável automática `$PsDscContext`.

Por exemplo o seguinte código teria de escrever o contexto de utilizador na qual o recurso está em execução no fluxo de saída verbosa:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Consulte Também
### <a name="concepts"></a>Conceitos
* [Escrever um recurso personalizado de DSC com MOF](authoringResourceMOF.md)
* [Introdução à configuração estado pretendido do Windows PowerShell](overview.md)

