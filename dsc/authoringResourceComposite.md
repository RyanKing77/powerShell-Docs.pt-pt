---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Recursos compostos - através de uma configuração de DSC como um recurso"
ms.openlocfilehash: 4a9574081d3579ffa910bf2ee595ba2550f40a15
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="ebf23-103">Recursos compostos: utilizar uma configuração de DSC como um recurso</span><span class="sxs-lookup"><span data-stu-id="ebf23-103">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="ebf23-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ebf23-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="ebf23-105">Em situações de mundo real, configurações podem tornar-se muito complexas, chamar muitos recursos diferentes e a definição de um grande número de propriedades.</span><span class="sxs-lookup"><span data-stu-id="ebf23-105">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="ebf23-106">Para ajudar a resolver este complexidade, pode utilizar uma configuração de configuração de estado pretendido do Windows PowerShell (DSC) como um recurso para outras configurações.</span><span class="sxs-lookup"><span data-stu-id="ebf23-106">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="ebf23-107">Chamamos a isto um recurso composto.</span><span class="sxs-lookup"><span data-stu-id="ebf23-107">We call this a composite resource.</span></span> <span data-ttu-id="ebf23-108">Um recurso composto é uma configuração de DSC que aceita parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ebf23-108">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="ebf23-109">Os parâmetros da configuração atuam como as propriedades do recurso.</span><span class="sxs-lookup"><span data-stu-id="ebf23-109">The parameters of the configuration act as the properties of the resource.</span></span> <span data-ttu-id="ebf23-110">A configuração é guardada como um ficheiro com um **. schema.psm1** extensão e demora o local de esquema MOF e o recurso de script num recurso DSC típico (para obter mais informações sobre os recursos de DSC, consulte [Windows Recursos de configuração do estado pretendido do PowerShell](resources.md).</span><span class="sxs-lookup"><span data-stu-id="ebf23-110">The configuration is saved as a file with a **.schema.psm1** extension, and takes the place of both the MOF schema and the resource script in a typical DSC resource (for more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="ebf23-111">Criar o recurso composto</span><span class="sxs-lookup"><span data-stu-id="ebf23-111">Creating the composite resource</span></span>

<span data-ttu-id="ebf23-112">No nosso exemplo, vamos criar uma configuração que invoca uma série de recursos existentes para configurar as máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="ebf23-112">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="ebf23-113">Em vez de especificar os valores para ser definido em blocos de configuração, a configuração cria um número de parâmetros que, em seguida, são utilizados em blocos de configuração.</span><span class="sxs-lookup"><span data-stu-id="ebf23-113">Instead of specifying the values to be set in configuration blocks, the configuration takes a number of parameters that are then used in the configuration blocks.</span></span>

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

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="ebf23-114">Guardar a configuração como um recurso composto</span><span class="sxs-lookup"><span data-stu-id="ebf23-114">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="ebf23-115">Para utilizar a configuração parametrizada como um recurso de DSC, guarde-o numa estrutura de diretórios como que quaisquer outros recursos baseados em MOF e atribua o nome com um **. schema.psm1** extensão.</span><span class="sxs-lookup"><span data-stu-id="ebf23-115">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a **.schema.psm1** extension.</span></span> <span data-ttu-id="ebf23-116">Neste exemplo, iremos irá nome ao ficheiro **xVirtualMachine.schema.psm1**.</span><span class="sxs-lookup"><span data-stu-id="ebf23-116">For this example, we’ll name the file **xVirtualMachine.schema.psm1**.</span></span> <span data-ttu-id="ebf23-117">Também tem de criar um manifesto com o nome **xVirtualMachine.psd1** que contém a seguinte linha.</span><span class="sxs-lookup"><span data-stu-id="ebf23-117">You also need to create a manifest named **xVirtualMachine.psd1** that contains the following line.</span></span> <span data-ttu-id="ebf23-118">Tenha em atenção que isto é, para além **MyDscResources.psd1**, o manifesto de módulo para todos os recursos sob o **MyDscResources** pasta.</span><span class="sxs-lookup"><span data-stu-id="ebf23-118">Note that this is in addition to **MyDscResources.psd1**, the module manifest for all resources under the **MyDscResources** folder.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

<span data-ttu-id="ebf23-119">Quando tiver terminado, a estrutura da pasta deve ser o seguinte.</span><span class="sxs-lookup"><span data-stu-id="ebf23-119">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="ebf23-120">O recurso está agora detetável utilizando o cmdlet Get-DscResource e as respetivas propriedades são Detetáveis pela esse cmdlet ou utilizando **Ctrl + espaço** a conclusão automática no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ebf23-120">The resource is now discoverable by using the Get-DscResource cmdlet, and its properties are discoverable by either that cmdlet or by using **Ctrl+Space** auto-complete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="ebf23-121">Utilizar o recurso composto</span><span class="sxs-lookup"><span data-stu-id="ebf23-121">Using the composite resource</span></span>

<span data-ttu-id="ebf23-122">Em seguida, iremos criar uma configuração que chama o recurso composto.</span><span class="sxs-lookup"><span data-stu-id="ebf23-122">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="ebf23-123">Esta configuração chama o recurso composto xVirtualMachine para criar uma máquina virtual e, em seguida, chama o **xComputer** recursos para alterá-lo.</span><span class="sxs-lookup"><span data-stu-id="ebf23-123">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="ebf23-124">Suporte PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="ebf23-124">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="ebf23-125">**Nota:** **PsDscRunAsCredential** é suportada no PowerShell 5.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="ebf23-125">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="ebf23-126">O **PsDscRunAsCredential** propriedade pode ser utilizada em [configurações de DSC](configurations.md) blocos de recurso para especificar que o recurso deve ser executado sob um conjunto especificado de credenciais.</span><span class="sxs-lookup"><span data-stu-id="ebf23-126">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="ebf23-127">Para obter mais informações, consulte [DSC em execução com as credenciais de utilizador](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="ebf23-127">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

<span data-ttu-id="ebf23-128">Para aceder ao contexto de utilizador a partir de um recurso personalizado, pode utilizar a variável automática `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="ebf23-128">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="ebf23-129">Por exemplo o seguinte código teria de escrever o contexto de utilizador na qual o recurso está em execução no fluxo de saída verbosa:</span><span class="sxs-lookup"><span data-stu-id="ebf23-129">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="ebf23-130">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="ebf23-130">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="ebf23-131">Conceitos</span><span class="sxs-lookup"><span data-stu-id="ebf23-131">Concepts</span></span>
* [<span data-ttu-id="ebf23-132">Escrever um recurso personalizado de DSC com MOF</span><span class="sxs-lookup"><span data-stu-id="ebf23-132">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="ebf23-133">Introdução à configuração estado pretendido do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ebf23-133">Get Started with Windows PowerShell Desired State Configuration</span></span>](overview.md)

