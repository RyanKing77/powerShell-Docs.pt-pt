---
title: Como importar cmdlets usando módulos | Microsoft Docs
ms.custom: ''
ms.date: 08/28/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: 2f145795a57c988da0cb4ed294142aa141c53cae
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215271"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="05296-102">How to Import Cmdlets Using Modules (Como Importar Cmdlets Através de Módulos)</span><span class="sxs-lookup"><span data-stu-id="05296-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="05296-103">Este artigo descreve como importar cmdlets para uma sessão do PowerShell usando um módulo binário.</span><span class="sxs-lookup"><span data-stu-id="05296-103">This article describes how to import cmdlets to a PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="05296-104">Os membros de módulos podem incluir cmdlets, provedores, funções, variáveis, aliases e muito mais.</span><span class="sxs-lookup"><span data-stu-id="05296-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="05296-105">Os snap-ins podem conter apenas cmdlets e provedores.</span><span class="sxs-lookup"><span data-stu-id="05296-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="05296-106">Como carregar cmdlets usando um módulo</span><span class="sxs-lookup"><span data-stu-id="05296-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="05296-107">Crie uma pasta de módulo que tenha o mesmo nome que o arquivo de assembly no qual os cmdlets são implementados.</span><span class="sxs-lookup"><span data-stu-id="05296-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="05296-108">Neste procedimento, a pasta do módulo é criada na pasta do `system32` Windows.</span><span class="sxs-lookup"><span data-stu-id="05296-108">In this procedure, the module folder is created in the Windows `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. <span data-ttu-id="05296-109">Verifique se a variável `PSModulePath` de ambiente inclui o caminho para a nova pasta do módulo.</span><span class="sxs-lookup"><span data-stu-id="05296-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="05296-110">Por padrão, a pasta do sistema já foi adicionada à `PSModulePath` variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="05296-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span> <span data-ttu-id="05296-111">Para exibir o `PSModulePath`, digite: `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="05296-111">To view the `PSModulePath`, type: `$env:PSModulePath`.</span></span>

1. <span data-ttu-id="05296-112">Copie o assembly do cmdlet para a pasta do módulo.</span><span class="sxs-lookup"><span data-stu-id="05296-112">Copy the cmdlet assembly into the module folder.</span></span>

1. <span data-ttu-id="05296-113">Adicione um arquivo de manifesto de`.psd1`módulo () na pasta raiz do módulo.</span><span class="sxs-lookup"><span data-stu-id="05296-113">Add a module manifest file (`.psd1`) in the module's root folder.</span></span> <span data-ttu-id="05296-114">O PowerShell usa o manifesto do módulo para importar o módulo.</span><span class="sxs-lookup"><span data-stu-id="05296-114">PowerShell uses the module manifest to import your module.</span></span> <span data-ttu-id="05296-115">Para obter mais informações, consulte [como escrever um manifesto de módulo do PowerShell](../module/how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="05296-115">For more information, see [How to Write a PowerShell Module Manifest](../module/how-to-write-a-powershell-module-manifest.md).</span></span>

1. <span data-ttu-id="05296-116">Execute o seguinte comando para adicionar os cmdlets à sessão:</span><span class="sxs-lookup"><span data-stu-id="05296-116">Run the following command to add the cmdlets to the session:</span></span>

   `Import-Module [Module_Name]`

   <span data-ttu-id="05296-117">Esse procedimento pode ser usado para testar seus cmdlets.</span><span class="sxs-lookup"><span data-stu-id="05296-117">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="05296-118">Ele adiciona todos os cmdlets no assembly à sessão.</span><span class="sxs-lookup"><span data-stu-id="05296-118">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="05296-119">Para obter mais informações sobre módulos, consulte [escrevendo um módulo do Windows PowerShell](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="05296-119">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="05296-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05296-120">See also</span></span>

[<span data-ttu-id="05296-121">Como escrever um manifesto de módulo do PowerShell</span><span class="sxs-lookup"><span data-stu-id="05296-121">How to Write a PowerShell Module Manifest</span></span>](../module/how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="05296-122">Importando um módulo do PowerShell</span><span class="sxs-lookup"><span data-stu-id="05296-122">Importing a PowerShell Module</span></span>](../module/importing-a-powershell-module.md)

[<span data-ttu-id="05296-123">Importar-módulo</span><span class="sxs-lookup"><span data-stu-id="05296-123">Import-Module</span></span>](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[<span data-ttu-id="05296-124">Instalando módulos</span><span class="sxs-lookup"><span data-stu-id="05296-124">Installing Modules</span></span>](../module/installing-a-powershell-module.md)

[<span data-ttu-id="05296-125">Modificando o caminho de instalação do PSModulePath</span><span class="sxs-lookup"><span data-stu-id="05296-125">Modifying the PSModulePath Installation Path</span></span>](../module/modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="05296-126">Escrevendo um cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="05296-126">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
