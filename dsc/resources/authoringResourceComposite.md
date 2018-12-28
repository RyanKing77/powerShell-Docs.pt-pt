---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recursos compostos – usando uma configuração de DSC como um recurso
ms.openlocfilehash: 2823d05e0c8feb2933ca691f9ab5149ace2f7ee3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404734"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a>Recursos compostos: Utilizar uma configuração de DSC como um recurso

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Em situações do mundo real, as configurações podem se tornar longos e complexos, chamando a muitos recursos diferentes e definir um grande número de propriedades. Para ajudar a resolver essa complexidade, pode utilizar uma configuração do Windows PowerShell Desired State Configuration (DSC) como um recurso para outras configurações. Chamamos isso de um recurso composto. Um recurso composto é uma configuração de DSC que usa parâmetros. Os parâmetros da configuração atuam como as propriedades do recurso. A configuração é guardada como um ficheiro com um **. schema.psm1** extensão e assume o lugar do esquema do MOF e o recurso de script num recurso de DSC típico (para obter mais informações sobre os recursos de DSC, consulte [Windows PowerShell Desired State Configuration recursos](resources.md).

## <a name="creating-the-composite-resource"></a>Criar o recurso composto

No nosso exemplo, vamos criar uma configuração que invoca uma série de recursos existentes para configurar máquinas virtuais. Em vez de especificar os valores a ser definido em blocos de configuração, a configuração demora um número de parâmetros que, em seguida, são utilizados em blocos de configuração.

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

    # Create VM specific diff VHD
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

### <a name="saving-the-configuration-as-a-composite-resource"></a>A guardar a configuração como um recurso composto

Para utilizar a configuração parametrizada como um recurso de DSC, guarde-o numa estrutura de diretório, como que qualquer outro recurso baseado em MOF e designe-com um **. schema.psm1** extensão. Neste exemplo, nomear o arquivo **xVirtualMachine.schema.psm1**. Terá também de criar um manifesto com o nome **xVirtualMachine.psd1** que contém a seguinte linha. Tenha em atenção que esta é uma adição ao **MyDscResources.psd1**, o manifesto de módulo para todos os recursos sob o **MyDscResources** pasta.

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

Quando tiver terminado, a estrutura de pastas deve ser o seguinte.

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

O recurso está agora detetável utilizando o cmdlet Get-DscResource e as respetivas propriedades são descobertas por qualquer um desse cmdlet ou através da utilização **Ctrl + espaço** conclusão automática no ISE do Windows PowerShell.

## <a name="using-the-composite-resource"></a>Usando o recurso composto

Em seguida, criamos uma configuração que chama o recurso composto. Esta configuração chama o recurso de compostos xVirtualMachine para criar uma máquina virtual e, em seguida, chama o **xComputer** recurso para renomeá-lo.

```powershell

configuration RenameVM
{

    Import-DscResource -Module xVirtualMachine
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

O **PsDscRunAsCredential** propriedade pode ser utilizada em [configurações de DSC](../configurations/configurations.md) bloco de recurso para especificar que o recurso deve ser executado num conjunto especificado de credenciais.
Para obter mais informações, consulte [a executar o DSC com as credenciais de utilizador](../configurations/runAsUser.md).

Para acessar o contexto de utilizador a partir de um recurso personalizado, pode utilizar a variável automática `$PsDscContext`.

Por exemplo, o código a seguir escreveria o contexto do usuário sob a qual o recurso está em execução no fluxo de saída detalhada:

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Consulte Também
### <a name="concepts"></a>Conceitos
* [Escrever um recurso personalizado do DSC com o MOF](authoringResourceMOF.md)
* [Introdução ao Windows PowerShell Desired State Configuration](../overview/overview.md)