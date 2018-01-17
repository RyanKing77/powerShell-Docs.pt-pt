---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recurso de pacote DSC
ms.openlocfilehash: 68b996e0f51e60bc178c27e3a71f07fb7220f847
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-package-resource"></a><span data-ttu-id="2c516-103">Recurso de pacote DSC</span><span class="sxs-lookup"><span data-stu-id="2c516-103">DSC Package Resource</span></span>

> <span data-ttu-id="2c516-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2c516-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="2c516-105">O **pacote** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para instalar ou desinstalar pacotes, tais como pacotes do Windows Installer e setup.exe, num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="2c516-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="2c516-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2c516-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="2c516-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="2c516-107">Properties</span></span>
|  <span data-ttu-id="2c516-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="2c516-108">Property</span></span>  |  <span data-ttu-id="2c516-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c516-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="2c516-110">Nome</span><span class="sxs-lookup"><span data-stu-id="2c516-110">Name</span></span>| <span data-ttu-id="2c516-111">Indica o nome do pacote para o qual pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="2c516-111">Indicates the name of the package for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="2c516-112">Caminho</span><span class="sxs-lookup"><span data-stu-id="2c516-112">Path</span></span>| <span data-ttu-id="2c516-113">Indica o caminho onde reside o pacote.</span><span class="sxs-lookup"><span data-stu-id="2c516-113">Indicates the path where the package resides.</span></span>| 
| <span data-ttu-id="2c516-114">ProductId</span><span class="sxs-lookup"><span data-stu-id="2c516-114">ProductId</span></span>| <span data-ttu-id="2c516-115">Indica o ID de produto que identifica exclusivamente o pacote.</span><span class="sxs-lookup"><span data-stu-id="2c516-115">Indicates the product ID that uniquely identifies the package.</span></span>| 
| <span data-ttu-id="2c516-116">Argumentos</span><span class="sxs-lookup"><span data-stu-id="2c516-116">Arguments</span></span>| <span data-ttu-id="2c516-117">Apresenta uma lista de uma cadeia de argumentos que serão transmitidas ao pacote exatamente como fornecido.</span><span class="sxs-lookup"><span data-stu-id="2c516-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span>| 
| <span data-ttu-id="2c516-118">credencial</span><span class="sxs-lookup"><span data-stu-id="2c516-118">Credential</span></span>| <span data-ttu-id="2c516-119">Fornece acesso ao pacote de uma origem remota.</span><span class="sxs-lookup"><span data-stu-id="2c516-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="2c516-120">Esta propriedade não é utilizada para instalar o pacote.</span><span class="sxs-lookup"><span data-stu-id="2c516-120">This property is not used to install the package.</span></span> <span data-ttu-id="2c516-121">O pacote é sempre instalado no sistema local.</span><span class="sxs-lookup"><span data-stu-id="2c516-121">The package is always installed on the local system.</span></span>| 
| <span data-ttu-id="2c516-122">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="2c516-122">Ensure</span></span>| <span data-ttu-id="2c516-123">Indica se o pacote está instalado.</span><span class="sxs-lookup"><span data-stu-id="2c516-123">Indicates if the package is installed.</span></span> <span data-ttu-id="2c516-124">Defina esta propriedade para "Ausente", certifique-se de que o pacote não está instalado (ou desinstalar o pacote, caso esteja instalada).</span><span class="sxs-lookup"><span data-stu-id="2c516-124">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="2c516-125">Defina-o para "Apresentar" (o valor predefinido) para garantir que o pacote está instalado.</span><span class="sxs-lookup"><span data-stu-id="2c516-125">Set it to "Present" (the default value) to ensure the package is installed.</span></span>| 
| <span data-ttu-id="2c516-126">LogPath</span><span class="sxs-lookup"><span data-stu-id="2c516-126">LogPath</span></span>| <span data-ttu-id="2c516-127">Indica o caminho completo onde pretende que o fornecedor para guardar um ficheiro de registo para instalar ou desinstalar o pacote.</span><span class="sxs-lookup"><span data-stu-id="2c516-127">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>| 
| <span data-ttu-id="2c516-128">dependsOn</span><span class="sxs-lookup"><span data-stu-id="2c516-128">DependsOn</span></span> | <span data-ttu-id="2c516-129">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="2c516-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2c516-130">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é ' DependsOn = "[ ResourceName ResourceType]"'.</span><span class="sxs-lookup"><span data-stu-id="2c516-130">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>| 
| <span data-ttu-id="2c516-131">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="2c516-131">ReturnCode</span></span>| <span data-ttu-id="2c516-132">Indica o código de retorno esperado.</span><span class="sxs-lookup"><span data-stu-id="2c516-132">Indicates the expected return code.</span></span> <span data-ttu-id="2c516-133">Se o código de retorno de real não coincide com que o valor esperado indicado aqui, que a configuração irá devolver um erro.</span><span class="sxs-lookup"><span data-stu-id="2c516-133">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>| 

## <a name="example"></a><span data-ttu-id="2c516-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2c516-134">Example</span></span>

<span data-ttu-id="2c516-135">Neste exemplo executa o instalador. msi, que está localizado no caminho especificado e tem o ID de produto especificada.</span><span class="sxs-lookup"><span data-stu-id="2c516-135">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

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

