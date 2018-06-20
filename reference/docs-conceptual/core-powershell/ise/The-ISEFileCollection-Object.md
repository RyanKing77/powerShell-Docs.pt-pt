---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISEFileCollection
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: eb4b2784820cbe51f662fd2fd945d8760ef9dbff
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953094"
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="17352-103">Objeto ISEFileCollection</span><span class="sxs-lookup"><span data-stu-id="17352-103">The ISEFileCollection Object</span></span>

<span data-ttu-id="17352-104">O **ISEFileCollection** objeto é uma coleção de **ISEFile** objetos.</span><span class="sxs-lookup"><span data-stu-id="17352-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="17352-105">Um exemplo é uma coleção $psISE.CurrentPowerShellTab.Files.</span><span class="sxs-lookup"><span data-stu-id="17352-105">An example is the $psISE.CurrentPowerShellTab.Files collection.</span></span>

## <a name="methods"></a><span data-ttu-id="17352-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="17352-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="17352-107">Adicionar\( \[fullPath\] \)</span><span class="sxs-lookup"><span data-stu-id="17352-107">Add\( \[fullPath\] \)</span></span>

<span data-ttu-id="17352-108">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="17352-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="17352-109">Cria e devolve um novo ficheiro untitled e adiciona-o para a coleção.</span><span class="sxs-lookup"><span data-stu-id="17352-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="17352-110">O **IsUntitled** é propriedade do ficheiro recém-criado **$true**.</span><span class="sxs-lookup"><span data-stu-id="17352-110">The **IsUntitled** property of the newly created file is **$true**.</span></span>

<span data-ttu-id="17352-111">**\[fullPath\]**  - opcional da cadeia de caminho completamente especificado do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="17352-111">**\[fullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="17352-112">Uma exceção é gerada se incluir o **fullPath** parâmetro e um caminho relativo, mas se utilizar um nome de ficheiro em vez do caminho completo.</span><span class="sxs-lookup"><span data-stu-id="17352-112">An exception is generated if you include the **fullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a><span data-ttu-id="17352-113">Remover\( ficheiro, \[Force\] \)</span><span class="sxs-lookup"><span data-stu-id="17352-113">Remove\( File, \[Force\] \)</span></span>

<span data-ttu-id="17352-114">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="17352-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="17352-115">Remove um ficheiro especificado no separador atual do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="17352-115">Removes a specified file from the current PowerShell tab.</span></span>

<span data-ttu-id="17352-116">**Ficheiro** -ficheiro ISEFile a cadeia que pretende remover da coleção.</span><span class="sxs-lookup"><span data-stu-id="17352-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="17352-117">Se não foi guardado o ficheiro, este método emite uma exceção.</span><span class="sxs-lookup"><span data-stu-id="17352-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="17352-118">Utilize o **forçar** comutador parâmetro para forçar a remoção de um ficheiro não guardada.</span><span class="sxs-lookup"><span data-stu-id="17352-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

<span data-ttu-id="17352-119">**\[Force\]**  -opcional booleano se definido como **$true**, concede permissão para remover o ficheiro, mesmo que não foi guardado após a última utilização.</span><span class="sxs-lookup"><span data-stu-id="17352-119">**\[Force\]** - optional Boolean If set to **$true**, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="17352-120">A predefinição é **$false**.</span><span class="sxs-lookup"><span data-stu-id="17352-120">The default is **$false**.</span></span>

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="17352-121">SetSelectedFile\( selectedFile \)</span><span class="sxs-lookup"><span data-stu-id="17352-121">SetSelectedFile\( selectedFile \)</span></span>

<span data-ttu-id="17352-122">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="17352-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="17352-123">Seleciona o ficheiro que é especificado pelo **selectedFile** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="17352-123">Selects the file that is specified by the **selectedFile** parameter.</span></span>

<span data-ttu-id="17352-124">**selectedFile** -Microsoft.PowerShell.Host.ISE.ISEFile ISEFile do ficheiro que pretende selecionar.</span><span class="sxs-lookup"><span data-stu-id="17352-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a><span data-ttu-id="17352-125">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="17352-125">See Also</span></span>

- [<span data-ttu-id="17352-126">O objeto de ISEFile</span><span class="sxs-lookup"><span data-stu-id="17352-126">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="17352-127">Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do</span><span class="sxs-lookup"><span data-stu-id="17352-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="17352-128">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="17352-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)