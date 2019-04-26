---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: DSC para Linux nxPackage recursos
ms.openlocfilehash: 64bb89a95bd6cbaea4e74b8a9979de52428fef3f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077879"
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="9a138-103">DSC para Linux nxPackage recursos</span><span class="sxs-lookup"><span data-stu-id="9a138-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="9a138-104">O **nxPackage** recursos no PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir pacotes num nó de Linux.</span><span class="sxs-lookup"><span data-stu-id="9a138-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="9a138-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a138-105">Syntax</span></span>

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="9a138-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="9a138-106">Properties</span></span>

|  <span data-ttu-id="9a138-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="9a138-107">Property</span></span> |  <span data-ttu-id="9a138-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a138-108">Description</span></span> |
|---|---|
| <span data-ttu-id="9a138-109">Nome</span><span class="sxs-lookup"><span data-stu-id="9a138-109">Name</span></span>| <span data-ttu-id="9a138-110">O nome do pacote para o qual pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="9a138-110">The name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="9a138-111">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="9a138-111">Ensure</span></span>| <span data-ttu-id="9a138-112">Determina se deve verificar se o pacote existe.</span><span class="sxs-lookup"><span data-stu-id="9a138-112">Determines whether to check if the package exists.</span></span> <span data-ttu-id="9a138-113">Defina esta propriedade para "Presente" para garantir que o pacote existe.</span><span class="sxs-lookup"><span data-stu-id="9a138-113">Set this property to "Present" to ensure the package exists.</span></span> <span data-ttu-id="9a138-114">Defini-lo como "Ausente", certifique-se de que o pacote não existe.</span><span class="sxs-lookup"><span data-stu-id="9a138-114">Set it to "Absent" to ensure the package does not exist.</span></span> <span data-ttu-id="9a138-115">O valor predefinido é "Presente".</span><span class="sxs-lookup"><span data-stu-id="9a138-115">The default value is "Present".</span></span>|
| <span data-ttu-id="9a138-116">PackageManager</span><span class="sxs-lookup"><span data-stu-id="9a138-116">PackageManager</span></span>| <span data-ttu-id="9a138-117">Os valores suportados são "yum", "apt" e "zypper".</span><span class="sxs-lookup"><span data-stu-id="9a138-117">Supported values are "yum", "apt", and "zypper".</span></span> <span data-ttu-id="9a138-118">Especifica o Gestor de pacotes a utilizar ao instalar pacotes.</span><span class="sxs-lookup"><span data-stu-id="9a138-118">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="9a138-119">Se **FilePath** for especificado, o caminho fornecido vai ser utilizado para instalar o pacote.</span><span class="sxs-lookup"><span data-stu-id="9a138-119">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="9a138-120">Caso contrário, um Gestor de pacotes será utilizado para instalar o pacote a partir de um repositório previamente configurado.</span><span class="sxs-lookup"><span data-stu-id="9a138-120">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="9a138-121">Se nenhum desses **PackageManager** nem **FilePath** são fornecidas, o Gestor de pacotes padrão para o sistema será usado.</span><span class="sxs-lookup"><span data-stu-id="9a138-121">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span>|
| <span data-ttu-id="9a138-122">FilePath</span><span class="sxs-lookup"><span data-stu-id="9a138-122">FilePath</span></span>| <span data-ttu-id="9a138-123">O caminho do ficheiro onde reside o pacote</span><span class="sxs-lookup"><span data-stu-id="9a138-123">The file path where the package resides</span></span>|
| <span data-ttu-id="9a138-124">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="9a138-124">PackageGroup</span></span>| <span data-ttu-id="9a138-125">Se **$true**, o **nome** deve ser o nome de um grupo de pacote para utilização com um **PackageManager**.</span><span class="sxs-lookup"><span data-stu-id="9a138-125">If **$true**, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="9a138-126">**PacakgeGroup** não é válido quando fornecer um **FilePath**.</span><span class="sxs-lookup"><span data-stu-id="9a138-126">**PacakgeGroup** is not valid when providing a **FilePath**.</span></span>|
| <span data-ttu-id="9a138-127">Argumentos</span><span class="sxs-lookup"><span data-stu-id="9a138-127">Arguments</span></span>| <span data-ttu-id="9a138-128">Uma cadeia de argumentos que será passada para o pacote exatamente como fornecida.</span><span class="sxs-lookup"><span data-stu-id="9a138-128">A string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="9a138-129">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="9a138-129">ReturnCode</span></span>| <span data-ttu-id="9a138-130">O código de retorno esperado.</span><span class="sxs-lookup"><span data-stu-id="9a138-130">The expected return code.</span></span> <span data-ttu-id="9a138-131">Se o código de retorno real não corresponde ao que valor esperado fornecido aqui, que a configuração irá devolver um erro.</span><span class="sxs-lookup"><span data-stu-id="9a138-131">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|
| <span data-ttu-id="9a138-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="9a138-132">DependsOn</span></span> | <span data-ttu-id="9a138-133">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="9a138-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="9a138-134">Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e seu tipo é **ResourceType**, a sintaxe para usar isso a propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="9a138-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="9a138-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9a138-135">Example</span></span>

<span data-ttu-id="9a138-136">O exemplo seguinte garante que o pacote com o nome "httpd" está instalado num computador Linux, utilizando o Gestor de pacotes "Yum".</span><span class="sxs-lookup"><span data-stu-id="9a138-136">The following example ensures that the package named "httpd" is installed on a Linux computer, using the “Yum” package manager.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```