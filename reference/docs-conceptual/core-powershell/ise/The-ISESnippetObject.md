---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f80080f4207cf226fb7466c4842446d08c081347
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954199"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="05f56-103">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="05f56-103">The ISESnippetObject</span></span>

<span data-ttu-id="05f56-104">Um **ISESnippet** objeto é uma instância da classe Microsoft.PowerShell.Host.ISE.ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="05f56-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="05f56-105">Os membros de **$psISE.CurrentPowerShellTab.Snippets** coleção se todos os exemplos de **ISESnippet** objetos.</span><span class="sxs-lookup"><span data-stu-id="05f56-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="05f56-106">A forma mais fácil de criar um fragmento consiste em utilizar o [New-IseSnippet&#91;PSITPro5_ISE&#93; ](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="05f56-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="05f56-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="05f56-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="05f56-108">autor</span><span class="sxs-lookup"><span data-stu-id="05f56-108">Author</span></span>

<span data-ttu-id="05f56-109">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="05f56-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="05f56-110">A propriedade só de leitura que obtém o nome do autor de fragmento.</span><span class="sxs-lookup"><span data-stu-id="05f56-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="05f56-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="05f56-111">CodeFragment</span></span>

<span data-ttu-id="05f56-112">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="05f56-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="05f56-113">A propriedade só de leitura que obtém o fragmento de código a inserir no editor.</span><span class="sxs-lookup"><span data-stu-id="05f56-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="05f56-114">Atalho</span><span class="sxs-lookup"><span data-stu-id="05f56-114">Shortcut</span></span>

<span data-ttu-id="05f56-115">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="05f56-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="05f56-116">A propriedade só de leitura que obtém a Windows teclado atalho para o item de menu.</span><span class="sxs-lookup"><span data-stu-id="05f56-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="05f56-117">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="05f56-117">See Also</span></span>

- [<span data-ttu-id="05f56-118">O objeto de ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="05f56-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="05f56-119">Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do</span><span class="sxs-lookup"><span data-stu-id="05f56-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="05f56-120">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="05f56-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)