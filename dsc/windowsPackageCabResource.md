---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos do DSC WindowsPackageCab
ms.openlocfilehash: 9b1bf3cb95abcbe46976ae0fd328280a3a8d7f28
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="79c68-103">Recursos do DSC WindowsPackageCab</span><span class="sxs-lookup"><span data-stu-id="79c68-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="79c68-104">Aplica-se a: Windows PowerShell 5.1 e posterior</span><span class="sxs-lookup"><span data-stu-id="79c68-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="79c68-105">O **WindowsPackageCab** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para instalar ou desinstalar pacotes CAB (. cab) do Windows num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="79c68-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="79c68-106">O nó de destino tem de ter o módulo do DISM PowerShell instalado.</span><span class="sxs-lookup"><span data-stu-id="79c68-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="79c68-107">Para informações, consulte [DISM de utilização no Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="79c68-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span> 


## <a name="syntax"></a><span data-ttu-id="79c68-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79c68-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="79c68-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="79c68-109">Properties</span></span>

|  <span data-ttu-id="79c68-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="79c68-110">Property</span></span>  |  <span data-ttu-id="79c68-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="79c68-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="79c68-112">Nome</span><span class="sxs-lookup"><span data-stu-id="79c68-112">Name</span></span>| <span data-ttu-id="79c68-113">Indica o nome do pacote para quando pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="79c68-113">Indicates the name of the package for you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="79c68-114">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="79c68-114">Ensure</span></span>| <span data-ttu-id="79c68-115">Indica se o pacote está instalado.</span><span class="sxs-lookup"><span data-stu-id="79c68-115">Indicates if the package is installed.</span></span> <span data-ttu-id="79c68-116">Defina esta propriedade para "Ausente", certifique-se de que o pacote não está instalado (ou desinstalar o pacote, caso esteja instalada).</span><span class="sxs-lookup"><span data-stu-id="79c68-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="79c68-117">Defina-o para "Apresentar" (o valor predefinido) para garantir que o pacote está instalado.</span><span class="sxs-lookup"><span data-stu-id="79c68-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="79c68-118">Caminho</span><span class="sxs-lookup"><span data-stu-id="79c68-118">Path</span></span>| <span data-ttu-id="79c68-119">Indica o caminho onde reside o pacote.</span><span class="sxs-lookup"><span data-stu-id="79c68-119">Indicates the path where the package resides.</span></span>| 
| <span data-ttu-id="79c68-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="79c68-120">LogPath</span></span>| <span data-ttu-id="79c68-121">Indica o caminho completo onde pretende que o fornecedor para guardar um ficheiro de registo para instalar ou desinstalar o pacote.</span><span class="sxs-lookup"><span data-stu-id="79c68-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>| 
| <span data-ttu-id="79c68-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="79c68-122">DependsOn</span></span> | <span data-ttu-id="79c68-123">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="79c68-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="79c68-124">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é ' DependsOn = "[ ResourceName ResourceType]"'.</span><span class="sxs-lookup"><span data-stu-id="79c68-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\`.</span></span>| 

## <a name="example"></a><span data-ttu-id="79c68-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="79c68-125">Example</span></span>

<span data-ttu-id="79c68-126">A seguinte configuração de exemplo utiliza os parâmetros de entrada e assegura que o ficheiro. cab especificado pelo `$Name` parâmetro está instalado.</span><span class="sxs-lookup"><span data-stu-id="79c68-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```

