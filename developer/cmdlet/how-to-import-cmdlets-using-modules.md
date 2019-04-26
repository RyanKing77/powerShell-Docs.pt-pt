---
title: Como importar os Cmdlets que utilizam módulos | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067982"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="48546-102">How to Import Cmdlets Using Modules (Como Importar Cmdlets Através de Módulos)</span><span class="sxs-lookup"><span data-stu-id="48546-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="48546-103">Este tópico descreve como importar os cmdlets para uma sessão do Windows PowerShell através de um módulo de binário.</span><span class="sxs-lookup"><span data-stu-id="48546-103">This topic describes how to import cmdlets to a Windows PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="48546-104">Os membros dos módulos podem incluir cmdlets, provedores, funções, variáveis, aliases e muito mais.</span><span class="sxs-lookup"><span data-stu-id="48546-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="48546-105">Snap-ins pode conter apenas os cmdlets e provedores.</span><span class="sxs-lookup"><span data-stu-id="48546-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="48546-106">Como carregar cmdlets a utilizar um módulo</span><span class="sxs-lookup"><span data-stu-id="48546-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="48546-107">Crie uma pasta de módulo que tem o mesmo nome que o ficheiro de assemblagem em que os cmdlets são implementados.</span><span class="sxs-lookup"><span data-stu-id="48546-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="48546-108">Neste procedimento, a pasta de módulo é criada no `system32` pasta.</span><span class="sxs-lookup"><span data-stu-id="48546-108">In this procedure, the module folder is created in the `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. <span data-ttu-id="48546-109">Certifique-se de que o `PSModulePath` variável de ambiente inclui o caminho para a nova pasta de módulo.</span><span class="sxs-lookup"><span data-stu-id="48546-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="48546-110">Por predefinição, a pasta de sistema já foi adicionada ao `PSModulePath` variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="48546-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span>

3. <span data-ttu-id="48546-111">Copie o assembly de cmdlet para a pasta de módulo.</span><span class="sxs-lookup"><span data-stu-id="48546-111">Copy the cmdlet assembly into the module folder.</span></span>

4. <span data-ttu-id="48546-112">Execute o seguinte comando para adicionar os cmdlets para a sessão:</span><span class="sxs-lookup"><span data-stu-id="48546-112">Run the following command to add the cmdlets to the session:</span></span>

   `import-module [Module_Name]`

   <span data-ttu-id="48546-113">Este procedimento pode ser utilizado para testar seus cmdlets.</span><span class="sxs-lookup"><span data-stu-id="48546-113">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="48546-114">Ele adiciona todos os cmdlets no assembly para a sessão.</span><span class="sxs-lookup"><span data-stu-id="48546-114">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="48546-115">Para obter mais informações sobre os módulos, os diferentes tipos de módulos, as diferentes formas de carregar módulos e como restringir os elementos de um módulo que são exportados, consulte [escrever um módulo do Windows PowerShell](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="48546-115">For more information about modules, the different types of modules, the different ways to load modules, and how to restrict the elements of a module that are exported, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="48546-116">Veja Também</span><span class="sxs-lookup"><span data-stu-id="48546-116">See Also</span></span>

[<span data-ttu-id="48546-117">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="48546-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="48546-118">Instalar módulos</span><span class="sxs-lookup"><span data-stu-id="48546-118">Installing Modules</span></span>](../module/installing-a-powershell-module.md)