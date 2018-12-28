---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f80080f4207cf226fb7466c4842446d08c081347
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405546"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="cb52f-103">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="cb52f-103">The ISESnippetObject</span></span>

<span data-ttu-id="cb52f-104">Uma **ISESnippet** objeto é uma instância da classe Microsoft.PowerShell.Host.ISE.ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="cb52f-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="cb52f-105">Os membros do **$psISE.CurrentPowerShellTab.Snippets** coleção são todos exemplos de **ISESnippet** objetos.</span><span class="sxs-lookup"><span data-stu-id="cb52f-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="cb52f-106">A maneira mais fácil para criar um trecho de código é usar o [New-IseSnippet&#91;PSITPro5_ISE&#93; ](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cb52f-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="cb52f-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="cb52f-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="cb52f-108">Autor</span><span class="sxs-lookup"><span data-stu-id="cb52f-108">Author</span></span>

<span data-ttu-id="cb52f-109">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="cb52f-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="cb52f-110">A propriedade só de leitura que obtém o nome do autor do trecho.</span><span class="sxs-lookup"><span data-stu-id="cb52f-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="cb52f-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="cb52f-111">CodeFragment</span></span>

<span data-ttu-id="cb52f-112">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="cb52f-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="cb52f-113">A propriedade só de leitura que obtém o fragmento de código a ser inserido no editor.</span><span class="sxs-lookup"><span data-stu-id="cb52f-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="cb52f-114">Atalho</span><span class="sxs-lookup"><span data-stu-id="cb52f-114">Shortcut</span></span>

<span data-ttu-id="cb52f-115">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="cb52f-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="cb52f-116">A propriedade só de leitura que obtém o Windows teclado atalho para o item de menu.</span><span class="sxs-lookup"><span data-stu-id="cb52f-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="cb52f-117">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="cb52f-117">See Also</span></span>

- [<span data-ttu-id="cb52f-118">Objeto ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="cb52f-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="cb52f-119">Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="cb52f-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="cb52f-120">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="cb52f-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)