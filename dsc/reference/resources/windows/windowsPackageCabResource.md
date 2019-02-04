---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso WindowsPackageCab de DSC
ms.openlocfilehash: 035944e7ca5c7469250c48a19b79f2f2d5d38e9a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687217"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="2d0c6-103">Recurso WindowsPackageCab de DSC</span><span class="sxs-lookup"><span data-stu-id="2d0c6-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="2d0c6-104">Aplica-se a: Windows PowerShell 5.1 e versões posterior</span><span class="sxs-lookup"><span data-stu-id="2d0c6-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="2d0c6-105">O **WindowsPackageCab** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para instalar ou desinstalar pacotes de Gabinete (. cab) do Windows num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="2d0c6-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="2d0c6-106">O nó de destino tem de ter o módulo DISM PowerShell instalado.</span><span class="sxs-lookup"><span data-stu-id="2d0c6-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="2d0c6-107">Para obter informações, consulte [utilize DISM no Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="2d0c6-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>


## <a name="syntax"></a><span data-ttu-id="2d0c6-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d0c6-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="2d0c6-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="2d0c6-109">Properties</span></span>

|  <span data-ttu-id="2d0c6-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="2d0c6-110">Property</span></span>  |  <span data-ttu-id="2d0c6-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d0c6-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="2d0c6-112">Nome</span><span class="sxs-lookup"><span data-stu-id="2d0c6-112">Name</span></span>| <span data-ttu-id="2d0c6-113">Indica o nome do pacote para quando pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="2d0c6-113">Indicates the name of the package for you want to ensure a specific state.</span></span>|
| <span data-ttu-id="2d0c6-114">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="2d0c6-114">Ensure</span></span>| <span data-ttu-id="2d0c6-115">Indica se o pacote está instalado.</span><span class="sxs-lookup"><span data-stu-id="2d0c6-115">Indicates if the package is installed.</span></span> <span data-ttu-id="2d0c6-116">Defina esta propriedade como "Ausente", certifique-se de que o pacote não está instalado (ou desinstalar o pacote se estiver instalado).</span><span class="sxs-lookup"><span data-stu-id="2d0c6-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="2d0c6-117">Defina-o para "Apresentar" (o valor predefinido) para garantir que o pacote está instalado.</span><span class="sxs-lookup"><span data-stu-id="2d0c6-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="2d0c6-118">Caminho</span><span class="sxs-lookup"><span data-stu-id="2d0c6-118">Path</span></span>| <span data-ttu-id="2d0c6-119">Indica o caminho onde reside o pacote.</span><span class="sxs-lookup"><span data-stu-id="2d0c6-119">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="2d0c6-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="2d0c6-120">LogPath</span></span>| <span data-ttu-id="2d0c6-121">Indica o caminho completo onde pretende que o fornecedor para guardar um ficheiro de registo para instalar ou desinstalar o pacote.</span><span class="sxs-lookup"><span data-stu-id="2d0c6-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="2d0c6-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="2d0c6-122">DependsOn</span></span> | <span data-ttu-id="2d0c6-123">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="2d0c6-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2d0c6-124">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será **ResourceName** e seu tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é "DependsOn ="[ ResourceName ResourceType]"'.</span><span class="sxs-lookup"><span data-stu-id="2d0c6-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example"></a><span data-ttu-id="2d0c6-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2d0c6-125">Example</span></span>

<span data-ttu-id="2d0c6-126">A seguinte configuração de exemplo usa parâmetros de entrada e garante que o arquivo. cab especificado pelo `$Name` parâmetro está instalado.</span><span class="sxs-lookup"><span data-stu-id="2d0c6-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

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