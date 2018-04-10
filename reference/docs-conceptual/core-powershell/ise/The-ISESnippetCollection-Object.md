---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="17aed-103">Objeto ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="17aed-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="17aed-104">O **ISESnippetCollection** objeto é uma coleção de **ISESnippet** objetos.</span><span class="sxs-lookup"><span data-stu-id="17aed-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="17aed-105">A coleção de ficheiros que está associada um **PowerShellTab** objeto é um membro desta classe.</span><span class="sxs-lookup"><span data-stu-id="17aed-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="17aed-106">Um exemplo é o **$psISE.CurrentPowerShellTab.Files** coleção.</span><span class="sxs-lookup"><span data-stu-id="17aed-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="17aed-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="17aed-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="17aed-108">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="17aed-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="17aed-109">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="17aed-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="17aed-110">Carrega um. snippets.ps1xml ficheiro que contém fragmentos definido pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="17aed-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="17aed-111">A forma mais fácil criar fragmentos consiste em utilizar o cmdlet New-IseSnippet, que armazena-os automaticamente na sua pasta de perfil que sejam carregados sempre que iniciar o ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="17aed-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="17aed-112">**FilePathName** - o caminho de cadeia e ficheiro o nome de um. snippets.ps1xml ficheiro que contém as definições de fragmento.</span><span class="sxs-lookup"><span data-stu-id="17aed-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="17aed-113">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="17aed-113">See Also</span></span>

- [<span data-ttu-id="17aed-114">O ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="17aed-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="17aed-115">Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do</span><span class="sxs-lookup"><span data-stu-id="17aed-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="17aed-116">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="17aed-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)