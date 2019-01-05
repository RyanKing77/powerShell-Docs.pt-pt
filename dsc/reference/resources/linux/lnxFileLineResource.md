---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: DSC para Linux nxFileLine recursos
ms.openlocfilehash: 6a91db25638b09659adfabcec78f91bcb2e69dd9
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048368"
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="29cfd-103">DSC para Linux nxFileLine recursos</span><span class="sxs-lookup"><span data-stu-id="29cfd-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="29cfd-104">O **nxFileLine** recursos no PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir linhas dentro de um ficheiro de configuração num nó de Linux.</span><span class="sxs-lookup"><span data-stu-id="29cfd-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="29cfd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29cfd-105">Syntax</span></span>

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="29cfd-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="29cfd-106">Properties</span></span>

|  <span data-ttu-id="29cfd-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="29cfd-107">Property</span></span> |  <span data-ttu-id="29cfd-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="29cfd-108">Description</span></span> |
|---|---|
| <span data-ttu-id="29cfd-109">Caminho do ficheiro</span><span class="sxs-lookup"><span data-stu-id="29cfd-109">FilePath</span></span>| <span data-ttu-id="29cfd-110">O caminho completo para o ficheiro para gerir as linhas no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="29cfd-110">The full path to the file to manage lines in on the target node.</span></span>|
| <span data-ttu-id="29cfd-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="29cfd-111">ContainsLine</span></span>| <span data-ttu-id="29cfd-112">Uma linha para garantir que existe no ficheiro.</span><span class="sxs-lookup"><span data-stu-id="29cfd-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="29cfd-113">Essa linha será anexada ao ficheiro se não existir no ficheiro.</span><span class="sxs-lookup"><span data-stu-id="29cfd-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="29cfd-114">**ContainsLine** é obrigatório, mas pode ser definido como uma cadeia vazia (`ContainsLine = ""`) se não for necessário.</span><span class="sxs-lookup"><span data-stu-id="29cfd-114">**ContainsLine** is mandatory, but can be set to an empty string (`ContainsLine = ""`) if it is not needed.</span></span>|
| <span data-ttu-id="29cfd-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="29cfd-115">DoesNotContainPattern</span></span>| <span data-ttu-id="29cfd-116">Um padrão de expressão regular para linhas que não deve existir no ficheiro.</span><span class="sxs-lookup"><span data-stu-id="29cfd-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="29cfd-117">Para as linhas existentes no arquivo que correspondem essa expressão regular, a linha será removida do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="29cfd-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span>|
| <span data-ttu-id="29cfd-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="29cfd-118">DependsOn</span></span> | <span data-ttu-id="29cfd-119">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="29cfd-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="29cfd-120">Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e seu tipo é **ResourceType**, a sintaxe para usar isso a propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="29cfd-120">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="29cfd-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="29cfd-121">Example</span></span>

<span data-ttu-id="29cfd-122">Este exemplo demonstra como utilizar o **nxFileLine** recurso para configurar o `/etc/sudoers` arquivo, assegurando que o utilizador: monuser está configurado para não requiretty.</span><span class="sxs-lookup"><span data-stu-id="29cfd-122">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```