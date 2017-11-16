---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: O ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: 6112f5252d2d1e868092da4a6cd04feb1875b597
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/31/2017
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="8023f-103">O ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="8023f-103">The ISESnippetObject</span></span>
  <span data-ttu-id="8023f-104">Um **ISESnippet** objeto é uma instância da classe Microsoft.PowerShell.Host.ISE.ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="8023f-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="8023f-105">Os membros de **$psISE.CurrentPowerShellTab.Snippets** coleção se todos os exemplos de **ISESnippet** objetos.</span><span class="sxs-lookup"><span data-stu-id="8023f-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="8023f-106">A forma mais fácil de criar um fragmento consiste em utilizar o [New-IseSnippet &#91; PSITPro5_ISE &#93; ](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8023f-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="8023f-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8023f-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="8023f-108">autor</span><span class="sxs-lookup"><span data-stu-id="8023f-108">Author</span></span>
  <span data-ttu-id="8023f-109">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8023f-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="8023f-110">A propriedade só de leitura que obtém o nome do autor de fragmento.</span><span class="sxs-lookup"><span data-stu-id="8023f-110">The read-only property that gets the name of the author of the snippet.</span></span>

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

### <a name="codefragment"></a><span data-ttu-id="8023f-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="8023f-111">CodeFragment</span></span>
  <span data-ttu-id="8023f-112">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8023f-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="8023f-113">A propriedade só de leitura que obtém o fragmento de código a inserir no editor.</span><span class="sxs-lookup"><span data-stu-id="8023f-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

### <a name="shortcut"></a><span data-ttu-id="8023f-114">Atalho</span><span class="sxs-lookup"><span data-stu-id="8023f-114">Shortcut</span></span>
  <span data-ttu-id="8023f-115">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8023f-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="8023f-116">A propriedade só de leitura que obtém a Windows teclado atalho para o item de menu.</span><span class="sxs-lookup"><span data-stu-id="8023f-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="8023f-117">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="8023f-117">See Also</span></span>
- [<span data-ttu-id="8023f-118">O objeto de ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="8023f-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md) 
- [<span data-ttu-id="8023f-119">O ISE do Windows PowerShell modelo de objeto de Scripting</span><span class="sxs-lookup"><span data-stu-id="8023f-119">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="8023f-120">Referência de modelo de objeto do Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="8023f-120">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="8023f-121">A hierarquia de modelo de objeto ISE</span><span class="sxs-lookup"><span data-stu-id="8023f-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
