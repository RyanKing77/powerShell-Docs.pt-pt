---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISEFileCollection
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: eb4b2784820cbe51f662fd2fd945d8760ef9dbff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684599"
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="2b976-103">Objeto ISEFileCollection</span><span class="sxs-lookup"><span data-stu-id="2b976-103">The ISEFileCollection Object</span></span>

<span data-ttu-id="2b976-104">O **ISEFileCollection** objeto é uma coleção de **ISEFile** objetos.</span><span class="sxs-lookup"><span data-stu-id="2b976-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="2b976-105">Um exemplo é uma coleção $psISE.CurrentPowerShellTab.Files.</span><span class="sxs-lookup"><span data-stu-id="2b976-105">An example is the $psISE.CurrentPowerShellTab.Files collection.</span></span>

## <a name="methods"></a><span data-ttu-id="2b976-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="2b976-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="2b976-107">Add\( \[fullPath\] \)</span><span class="sxs-lookup"><span data-stu-id="2b976-107">Add\( \[fullPath\] \)</span></span>

<span data-ttu-id="2b976-108">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="2b976-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2b976-109">Cria e retorna um novo ficheiro sem título e o adiciona à coleção.</span><span class="sxs-lookup"><span data-stu-id="2b976-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="2b976-110">O **IsUntitled** é de propriedade do ficheiro recentemente criado **$true**.</span><span class="sxs-lookup"><span data-stu-id="2b976-110">The **IsUntitled** property of the newly created file is **$true**.</span></span>

<span data-ttu-id="2b976-111">**\[fullPath\]**  - opcional o caminho totalmente especificado do arquivo de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2b976-111">**\[fullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="2b976-112">Uma exceção é gerada se incluir o **fullPath** parâmetro e um caminho relativo, ou se utilizar um nome de ficheiro em vez do caminho completo.</span><span class="sxs-lookup"><span data-stu-id="2b976-112">An exception is generated if you include the **fullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a><span data-ttu-id="2b976-113">Remova\( arquivo, \[Force\] \)</span><span class="sxs-lookup"><span data-stu-id="2b976-113">Remove\( File, \[Force\] \)</span></span>

<span data-ttu-id="2b976-114">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="2b976-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2b976-115">Remove um ficheiro especificado do separador atual do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b976-115">Removes a specified file from the current PowerShell tab.</span></span>

<span data-ttu-id="2b976-116">**Ficheiro** -cadeia de caracteres de ISEFile o ficheiro que pretende remover da coleção.</span><span class="sxs-lookup"><span data-stu-id="2b976-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="2b976-117">Se o ficheiro não foi salvo, esse método lança uma exceção.</span><span class="sxs-lookup"><span data-stu-id="2b976-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="2b976-118">Utilize o **forçar** mudar o parâmetro para forçar a remoção de um arquivo não guardada.</span><span class="sxs-lookup"><span data-stu-id="2b976-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

<span data-ttu-id="2b976-119">**\[Força\]**  -opcional booleano se definido como **$true**, concede permissão para remover o ficheiro, mesmo que não foi guardado após a última utilização.</span><span class="sxs-lookup"><span data-stu-id="2b976-119">**\[Force\]** - optional Boolean If set to **$true**, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="2b976-120">A predefinição é **$false**.</span><span class="sxs-lookup"><span data-stu-id="2b976-120">The default is **$false**.</span></span>

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="2b976-121">SetSelectedFile\( selectedFile \)</span><span class="sxs-lookup"><span data-stu-id="2b976-121">SetSelectedFile\( selectedFile \)</span></span>

<span data-ttu-id="2b976-122">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="2b976-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2b976-123">Seleciona o ficheiro especificado pelos **selectedFile** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2b976-123">Selects the file that is specified by the **selectedFile** parameter.</span></span>

<span data-ttu-id="2b976-124">**selectedFile** -Microsoft.PowerShell.Host.ISE.ISEFile ISEFile do ficheiro que pretende selecionar.</span><span class="sxs-lookup"><span data-stu-id="2b976-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a><span data-ttu-id="2b976-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="2b976-125">See Also</span></span>

- [<span data-ttu-id="2b976-126">Objeto ISEFile</span><span class="sxs-lookup"><span data-stu-id="2b976-126">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="2b976-127">Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="2b976-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="2b976-128">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="2b976-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)