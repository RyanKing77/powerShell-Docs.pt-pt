---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recursos compostos – usando uma configuração de DSC como um recurso
ms.openlocfilehash: 2823d05e0c8feb2933ca691f9ab5149ace2f7ee3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684046"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="4f211-103">Recursos compostos: Utilizar uma configuração de DSC como um recurso</span><span class="sxs-lookup"><span data-stu-id="4f211-103">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="4f211-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4f211-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="4f211-105">Em situações do mundo real, as configurações podem se tornar longos e complexos, chamando a muitos recursos diferentes e definir um grande número de propriedades.</span><span class="sxs-lookup"><span data-stu-id="4f211-105">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="4f211-106">Para ajudar a resolver essa complexidade, pode utilizar uma configuração do Windows PowerShell Desired State Configuration (DSC) como um recurso para outras configurações.</span><span class="sxs-lookup"><span data-stu-id="4f211-106">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="4f211-107">Chamamos isso de um recurso composto.</span><span class="sxs-lookup"><span data-stu-id="4f211-107">We call this a composite resource.</span></span> <span data-ttu-id="4f211-108">Um recurso composto é uma configuração de DSC que usa parâmetros.</span><span class="sxs-lookup"><span data-stu-id="4f211-108">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="4f211-109">Os parâmetros da configuração atuam como as propriedades do recurso.</span><span class="sxs-lookup"><span data-stu-id="4f211-109">The parameters of the configuration act as the properties of the resource.</span></span> <span data-ttu-id="4f211-110">A configuração é guardada como um ficheiro com um **. schema.psm1** extensão e assume o lugar do esquema do MOF e o recurso de script num recurso de DSC típico (para obter mais informações sobre os recursos de DSC, consulte [Windows PowerShell Desired State Configuration recursos](resources.md).</span><span class="sxs-lookup"><span data-stu-id="4f211-110">The configuration is saved as a file with a **.schema.psm1** extension, and takes the place of both the MOF schema and the resource script in a typical DSC resource (for more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="4f211-111">Criar o recurso composto</span><span class="sxs-lookup"><span data-stu-id="4f211-111">Creating the composite resource</span></span>

<span data-ttu-id="4f211-112">No nosso exemplo, vamos criar uma configuração que invoca uma série de recursos existentes para configurar máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="4f211-112">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="4f211-113">Em vez de especificar os valores a ser definido em blocos de configuração, a configuração demora um número de parâmetros que, em seguida, são utilizados em blocos de configuração.</span><span class="sxs-lookup"><span data-stu-id="4f211-113">Instead of specifying the values to be set in configuration blocks, the configuration takes a number of parameters that are then used in the configuration blocks.</span></span>

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

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="4f211-114">A guardar a configuração como um recurso composto</span><span class="sxs-lookup"><span data-stu-id="4f211-114">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="4f211-115">Para utilizar a configuração parametrizada como um recurso de DSC, guarde-o numa estrutura de diretório, como que qualquer outro recurso baseado em MOF e designe-com um **. schema.psm1** extensão.</span><span class="sxs-lookup"><span data-stu-id="4f211-115">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a **.schema.psm1** extension.</span></span> <span data-ttu-id="4f211-116">Neste exemplo, nomear o arquivo **xVirtualMachine.schema.psm1**.</span><span class="sxs-lookup"><span data-stu-id="4f211-116">For this example, we’ll name the file **xVirtualMachine.schema.psm1**.</span></span> <span data-ttu-id="4f211-117">Terá também de criar um manifesto com o nome **xVirtualMachine.psd1** que contém a seguinte linha.</span><span class="sxs-lookup"><span data-stu-id="4f211-117">You also need to create a manifest named **xVirtualMachine.psd1** that contains the following line.</span></span> <span data-ttu-id="4f211-118">Tenha em atenção que esta é uma adição ao **MyDscResources.psd1**, o manifesto de módulo para todos os recursos sob o **MyDscResources** pasta.</span><span class="sxs-lookup"><span data-stu-id="4f211-118">Note that this is in addition to **MyDscResources.psd1**, the module manifest for all resources under the **MyDscResources** folder.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

<span data-ttu-id="4f211-119">Quando tiver terminado, a estrutura de pastas deve ser o seguinte.</span><span class="sxs-lookup"><span data-stu-id="4f211-119">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="4f211-120">O recurso está agora detetável utilizando o cmdlet Get-DscResource e as respetivas propriedades são descobertas por qualquer um desse cmdlet ou através da utilização **Ctrl + espaço** conclusão automática no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f211-120">The resource is now discoverable by using the Get-DscResource cmdlet, and its properties are discoverable by either that cmdlet or by using **Ctrl+Space** auto-complete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="4f211-121">Usando o recurso composto</span><span class="sxs-lookup"><span data-stu-id="4f211-121">Using the composite resource</span></span>

<span data-ttu-id="4f211-122">Em seguida, criamos uma configuração que chama o recurso composto.</span><span class="sxs-lookup"><span data-stu-id="4f211-122">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="4f211-123">Esta configuração chama o recurso de compostos xVirtualMachine para criar uma máquina virtual e, em seguida, chama o **xComputer** recurso para renomeá-lo.</span><span class="sxs-lookup"><span data-stu-id="4f211-123">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="4f211-124">Suporte PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="4f211-124">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="4f211-125">**Nota:** **PsDscRunAsCredential** é suportada no PowerShell 5.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="4f211-125">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="4f211-126">O **PsDscRunAsCredential** propriedade pode ser utilizada em [configurações de DSC](../configurations/configurations.md) bloco de recurso para especificar que o recurso deve ser executado num conjunto especificado de credenciais.</span><span class="sxs-lookup"><span data-stu-id="4f211-126">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="4f211-127">Para obter mais informações, consulte [a executar o DSC com as credenciais de utilizador](../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="4f211-127">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="4f211-128">Para acessar o contexto de utilizador a partir de um recurso personalizado, pode utilizar a variável automática `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="4f211-128">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="4f211-129">Por exemplo, o código a seguir escreveria o contexto do usuário sob a qual o recurso está em execução no fluxo de saída detalhada:</span><span class="sxs-lookup"><span data-stu-id="4f211-129">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="4f211-130">Veja Também</span><span class="sxs-lookup"><span data-stu-id="4f211-130">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="4f211-131">Conceitos</span><span class="sxs-lookup"><span data-stu-id="4f211-131">Concepts</span></span>
* [<span data-ttu-id="4f211-132">Escrever um recurso personalizado do DSC com o MOF</span><span class="sxs-lookup"><span data-stu-id="4f211-132">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="4f211-133">Introdução ao Windows PowerShell Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="4f211-133">Get Started with Windows PowerShell Desired State Configuration</span></span>](../overview/overview.md)