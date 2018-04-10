---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: DSC de Linux nxFileLine recursos
ms.openlocfilehash: 798bfa4150996622c33c77d6a5aa3be4af342f1b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="53411-103">DSC de Linux nxFileLine recursos</span><span class="sxs-lookup"><span data-stu-id="53411-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="53411-104">O **nxFileLine** recursos no PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir linhas dentro de um ficheiro de configuração num nó de Linux.</span><span class="sxs-lookup"><span data-stu-id="53411-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="53411-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53411-105">Syntax</span></span>

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="53411-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="53411-106">Properties</span></span>

|  <span data-ttu-id="53411-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="53411-107">Property</span></span> |  <span data-ttu-id="53411-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="53411-108">Description</span></span> |
|---|---|
| <span data-ttu-id="53411-109">FilePath</span><span class="sxs-lookup"><span data-stu-id="53411-109">FilePath</span></span>| <span data-ttu-id="53411-110">O caminho completo para o ficheiro para gerir linhas no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="53411-110">The full path to the file to manage lines in on the target node.</span></span>|
| <span data-ttu-id="53411-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="53411-111">ContainsLine</span></span>| <span data-ttu-id="53411-112">Uma linha para garantir que existe no ficheiro.</span><span class="sxs-lookup"><span data-stu-id="53411-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="53411-113">Esta linha será anexada ao ficheiro se não existir no ficheiro.</span><span class="sxs-lookup"><span data-stu-id="53411-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="53411-114">**ContainsLine** é obrigatório, mas pode ser definido como uma cadeia vazia ("ContainsLine = ' ') se não for necessário.</span><span class="sxs-lookup"><span data-stu-id="53411-114">**ContainsLine** is mandatory, but can be set to an empty string (\`ContainsLine = ‘’\`\`) if it is not needed.</span></span>|
| <span data-ttu-id="53411-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="53411-115">DoesNotContainPattern</span></span>| <span data-ttu-id="53411-116">Um padrão de expressão regular para as linhas que não deve existir no ficheiro.</span><span class="sxs-lookup"><span data-stu-id="53411-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="53411-117">Para as linhas de que existe no ficheiro que correspondem a esta expressão regular, a linha será removida do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="53411-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span>|
| <span data-ttu-id="53411-118">dependsOn</span><span class="sxs-lookup"><span data-stu-id="53411-118">DependsOn</span></span> | <span data-ttu-id="53411-119">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="53411-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="53411-120">Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta a propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="53411-120">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="53411-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="53411-121">Example</span></span>

<span data-ttu-id="53411-122">Este exemplo mostra como utilizar o **nxFileLine** recursos para configurar o `/etc/sudoers` ficheiro, garantindo que o utilizador: monuser está configurado para não requiretty.</span><span class="sxs-lookup"><span data-stu-id="53411-122">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```
Import-DSCResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```