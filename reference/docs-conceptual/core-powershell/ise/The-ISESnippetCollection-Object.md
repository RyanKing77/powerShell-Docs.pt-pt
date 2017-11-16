---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: O objeto de ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: b19c5b5c88f7c8bd0d0c466c7861fa9288bdc7a2
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="4fe47-103">O objeto de ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="4fe47-103">The ISESnippetCollection Object</span></span>
  <span data-ttu-id="4fe47-104">O **ISESnippetCollection** objeto é uma coleção de **ISESnippet** objetos.</span><span class="sxs-lookup"><span data-stu-id="4fe47-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="4fe47-105">A coleção de ficheiros que está associada um **PowerShellTab** objeto é um membro desta classe.</span><span class="sxs-lookup"><span data-stu-id="4fe47-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="4fe47-106">Um exemplo é o **$psISE.CurrentPowerShellTab.Files** coleção.</span><span class="sxs-lookup"><span data-stu-id="4fe47-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="4fe47-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="4fe47-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="4fe47-108">Carga\( FilePathName\)</span><span class="sxs-lookup"><span data-stu-id="4fe47-108">Load\( FilePathName \)</span></span>
  <span data-ttu-id="4fe47-109">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="4fe47-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="4fe47-110">Carrega um. snippets.ps1xml ficheiro que contém fragmentos definido pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="4fe47-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="4fe47-111">A forma mais fácil criar fragmentos consiste em utilizar o cmdlet New-IseSnippet, que armazena-os automaticamente na sua pasta de perfil que sejam carregados sempre que iniciar o ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4fe47-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

 <span data-ttu-id="4fe47-112">**FilePathName** - o caminho de cadeia e ficheiro o nome de um. snippets.ps1xml ficheiro que contém as definições de fragmento.</span><span class="sxs-lookup"><span data-stu-id="4fe47-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## <a name="see-also"></a><span data-ttu-id="4fe47-113">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="4fe47-113">See Also</span></span>
- [<span data-ttu-id="4fe47-114">O ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="4fe47-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md) 
- [<span data-ttu-id="4fe47-115">O ISE do Windows PowerShell modelo de objeto de Scripting</span><span class="sxs-lookup"><span data-stu-id="4fe47-115">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="4fe47-116">Referência de modelo de objeto do Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="4fe47-116">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="4fe47-117">A hierarquia de modelo de objeto ISE</span><span class="sxs-lookup"><span data-stu-id="4fe47-117">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
