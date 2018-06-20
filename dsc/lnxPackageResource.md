---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: DSC de Linux nxPackage recursos
ms.openlocfilehash: 64bb89a95bd6cbaea4e74b8a9979de52428fef3f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218710"
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="52a85-103">DSC de Linux nxPackage recursos</span><span class="sxs-lookup"><span data-stu-id="52a85-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="52a85-104">O **nxPackage** recursos no PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir pacotes num nó de Linux.</span><span class="sxs-lookup"><span data-stu-id="52a85-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="52a85-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52a85-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="52a85-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="52a85-106">Properties</span></span>

|  <span data-ttu-id="52a85-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="52a85-107">Property</span></span> |  <span data-ttu-id="52a85-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="52a85-108">Description</span></span> |
|---|---|
| <span data-ttu-id="52a85-109">Nome</span><span class="sxs-lookup"><span data-stu-id="52a85-109">Name</span></span>| <span data-ttu-id="52a85-110">O nome do pacote para o qual pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="52a85-110">The name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="52a85-111">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="52a85-111">Ensure</span></span>| <span data-ttu-id="52a85-112">Determina se deve verificar se o pacote existir.</span><span class="sxs-lookup"><span data-stu-id="52a85-112">Determines whether to check if the package exists.</span></span> <span data-ttu-id="52a85-113">Defina esta propriedade para "Presente" para garantir que o pacote existir.</span><span class="sxs-lookup"><span data-stu-id="52a85-113">Set this property to "Present" to ensure the package exists.</span></span> <span data-ttu-id="52a85-114">Defina-o para "Ausente", certifique-se de que o pacote não existe.</span><span class="sxs-lookup"><span data-stu-id="52a85-114">Set it to "Absent" to ensure the package does not exist.</span></span> <span data-ttu-id="52a85-115">O valor predefinido é "Presente".</span><span class="sxs-lookup"><span data-stu-id="52a85-115">The default value is "Present".</span></span>|
| <span data-ttu-id="52a85-116">PackageManager</span><span class="sxs-lookup"><span data-stu-id="52a85-116">PackageManager</span></span>| <span data-ttu-id="52a85-117">Os valores suportados são "yum", "apt" e "zypper".</span><span class="sxs-lookup"><span data-stu-id="52a85-117">Supported values are "yum", "apt", and "zypper".</span></span> <span data-ttu-id="52a85-118">Especifica o Gestor de pacotes a utilizar ao instalar pacotes.</span><span class="sxs-lookup"><span data-stu-id="52a85-118">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="52a85-119">Se **FilePath** for especificado, o caminho fornecido será utilizado para instalar o pacote.</span><span class="sxs-lookup"><span data-stu-id="52a85-119">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="52a85-120">Caso contrário, um Gestor de pacote será utilizado para instalar o pacote a partir de um repositório de pré-configurado.</span><span class="sxs-lookup"><span data-stu-id="52a85-120">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="52a85-121">Se nenhum dos **PackageManager** nem **FilePath** são fornecidos, o Gestor de pacote predefinido para o sistema irá ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="52a85-121">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span>|
| <span data-ttu-id="52a85-122">filePath</span><span class="sxs-lookup"><span data-stu-id="52a85-122">FilePath</span></span>| <span data-ttu-id="52a85-123">O caminho do ficheiro onde reside o pacote</span><span class="sxs-lookup"><span data-stu-id="52a85-123">The file path where the package resides</span></span>|
| <span data-ttu-id="52a85-124">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="52a85-124">PackageGroup</span></span>| <span data-ttu-id="52a85-125">Se **$true**, a **nome** deve ser o nome de um grupo do pacote para utilização com um **PackageManager**.</span><span class="sxs-lookup"><span data-stu-id="52a85-125">If **$true**, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="52a85-126">**PacakgeGroup** não é válido quando fornecer um **FilePath**.</span><span class="sxs-lookup"><span data-stu-id="52a85-126">**PacakgeGroup** is not valid when providing a **FilePath**.</span></span>|
| <span data-ttu-id="52a85-127">Argumentos</span><span class="sxs-lookup"><span data-stu-id="52a85-127">Arguments</span></span>| <span data-ttu-id="52a85-128">Uma cadeia de argumentos que serão transmitidas ao pacote exatamente como fornecido.</span><span class="sxs-lookup"><span data-stu-id="52a85-128">A string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="52a85-129">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="52a85-129">ReturnCode</span></span>| <span data-ttu-id="52a85-130">O código de retorno esperado.</span><span class="sxs-lookup"><span data-stu-id="52a85-130">The expected return code.</span></span> <span data-ttu-id="52a85-131">Se o código de retorno de real não coincide com que o valor esperado indicado aqui, que a configuração irá devolver um erro.</span><span class="sxs-lookup"><span data-stu-id="52a85-131">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|
| <span data-ttu-id="52a85-132">dependsOn</span><span class="sxs-lookup"><span data-stu-id="52a85-132">DependsOn</span></span> | <span data-ttu-id="52a85-133">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="52a85-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="52a85-134">Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta a propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="52a85-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="52a85-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="52a85-135">Example</span></span>

<span data-ttu-id="52a85-136">O exemplo seguinte assegura que o pacote designado "httpd" é instalado num computador Linux, utilizando o Gestor de pacote "Yum".</span><span class="sxs-lookup"><span data-stu-id="52a85-136">The following example ensures that the package named "httpd" is installed on a Linux computer, using the “Yum” package manager.</span></span>

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