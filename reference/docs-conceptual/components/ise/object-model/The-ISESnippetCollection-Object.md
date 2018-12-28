---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405561"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="ffc54-103">Objeto ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="ffc54-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="ffc54-104">O **ISESnippetCollection** objeto é uma coleção de **ISESnippet** objetos.</span><span class="sxs-lookup"><span data-stu-id="ffc54-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="ffc54-105">A coleção de ficheiros que está associada um **PowerShellTab** objeto é um membro dessa classe.</span><span class="sxs-lookup"><span data-stu-id="ffc54-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="ffc54-106">Um exemplo é o **$psISE.CurrentPowerShellTab.Files** coleção.</span><span class="sxs-lookup"><span data-stu-id="ffc54-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="ffc54-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="ffc54-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="ffc54-108">Carga\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="ffc54-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="ffc54-109">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="ffc54-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="ffc54-110">Carrega um. snippets.ps1xml ficheiro que contém trechos de código definido pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="ffc54-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="ffc54-111">A maneira mais fácil de criar trechos de código é usar o cmdlet New-IseSnippet, que armazena-os automaticamente na sua pasta de perfil para que eles são carregados sempre que iniciar o ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ffc54-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="ffc54-112">**FilePathName** - o caminho de cadeias de caracteres e ficheiro o nome para um. snippets.ps1xml ficheiro que contém definições de Trecho de código.</span><span class="sxs-lookup"><span data-stu-id="ffc54-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="ffc54-113">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="ffc54-113">See Also</span></span>

- [<span data-ttu-id="ffc54-114">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="ffc54-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="ffc54-115">Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="ffc54-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="ffc54-116">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="ffc54-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)