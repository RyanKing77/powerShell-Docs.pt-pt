---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso de pacote de DSC
ms.openlocfilehash: 9285df71a303c9a53dd50d450272575a64e962e7
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268675"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="2b932-103">Recurso de pacote de DSC</span><span class="sxs-lookup"><span data-stu-id="2b932-103">DSC Package Resource</span></span>

<span data-ttu-id="2b932-104">_Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="2b932-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="2b932-105">O **pacote** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para instalar ou desinstalar pacotes, como pacotes de instalador do Windows e setup.exe, num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="2b932-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="2b932-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b932-106">Syntax</span></span>

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="2b932-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="2b932-107">Properties</span></span>

| <span data-ttu-id="2b932-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="2b932-108">Property</span></span> | <span data-ttu-id="2b932-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b932-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="2b932-110">Nome</span><span class="sxs-lookup"><span data-stu-id="2b932-110">Name</span></span>| <span data-ttu-id="2b932-111">Indica o nome do pacote para o qual pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="2b932-111">Indicates the name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="2b932-112">Caminho</span><span class="sxs-lookup"><span data-stu-id="2b932-112">Path</span></span>| <span data-ttu-id="2b932-113">Indica o caminho onde reside o pacote.</span><span class="sxs-lookup"><span data-stu-id="2b932-113">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="2b932-114">productId</span><span class="sxs-lookup"><span data-stu-id="2b932-114">ProductId</span></span>| <span data-ttu-id="2b932-115">Indica o ID de produto que identifica exclusivamente o pacote.</span><span class="sxs-lookup"><span data-stu-id="2b932-115">Indicates the product ID that uniquely identifies the package.</span></span>|
| <span data-ttu-id="2b932-116">Argumentos</span><span class="sxs-lookup"><span data-stu-id="2b932-116">Arguments</span></span>| <span data-ttu-id="2b932-117">Lista de argumentos que será passada para o pacote exatamente como fornecida uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2b932-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="2b932-118">Credencial</span><span class="sxs-lookup"><span data-stu-id="2b932-118">Credential</span></span>| <span data-ttu-id="2b932-119">Fornece acesso ao pacote de sobre uma origem remota.</span><span class="sxs-lookup"><span data-stu-id="2b932-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="2b932-120">Esta propriedade não é utilizada para instalar o pacote.</span><span class="sxs-lookup"><span data-stu-id="2b932-120">This property is not used to install the package.</span></span> <span data-ttu-id="2b932-121">O pacote é sempre instalado no sistema local.</span><span class="sxs-lookup"><span data-stu-id="2b932-121">The package is always installed on the local system.</span></span>|
| <span data-ttu-id="2b932-122">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="2b932-122">Ensure</span></span>| <span data-ttu-id="2b932-123">Indica se o pacote está instalado.</span><span class="sxs-lookup"><span data-stu-id="2b932-123">Indicates if the package is installed.</span></span> <span data-ttu-id="2b932-124">Defina esta propriedade como "Ausente", certifique-se de que o pacote não está instalado (ou desinstalar o pacote se estiver instalado).</span><span class="sxs-lookup"><span data-stu-id="2b932-124">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="2b932-125">Defina-o para "Apresentar" (o valor predefinido) para garantir que o pacote está instalado.</span><span class="sxs-lookup"><span data-stu-id="2b932-125">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="2b932-126">LogPath</span><span class="sxs-lookup"><span data-stu-id="2b932-126">LogPath</span></span>| <span data-ttu-id="2b932-127">Indica o caminho completo onde pretende que o fornecedor para guardar um ficheiro de registo para instalar ou desinstalar o pacote.</span><span class="sxs-lookup"><span data-stu-id="2b932-127">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="2b932-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="2b932-128">DependsOn</span></span> | <span data-ttu-id="2b932-129">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="2b932-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2b932-130">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será **ResourceName** e seu tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="2b932-130">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="2b932-131">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="2b932-131">ReturnCode</span></span>| <span data-ttu-id="2b932-132">Indica o código de retorno esperado.</span><span class="sxs-lookup"><span data-stu-id="2b932-132">Indicates the expected return code.</span></span> <span data-ttu-id="2b932-133">Se o código de retorno real não corresponde ao que valor esperado fornecido aqui, que a configuração irá devolver um erro.</span><span class="sxs-lookup"><span data-stu-id="2b932-133">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|

## <a name="example"></a><span data-ttu-id="2b932-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b932-134">Example</span></span>

<span data-ttu-id="2b932-135">Este exemplo é executado o instalador. msi, que está localizado no caminho especificado e tem o ID de produto especificada.</span><span class="sxs-lookup"><span data-stu-id="2b932-135">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```