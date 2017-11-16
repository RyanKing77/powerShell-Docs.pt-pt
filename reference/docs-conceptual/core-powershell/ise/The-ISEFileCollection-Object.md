---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: O objeto de ISEFileCollection
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: 60bf4dae33f3a71c31e7fdbed0f4fd6ab27a8bd1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="58418-103">O objeto de ISEFileCollection</span><span class="sxs-lookup"><span data-stu-id="58418-103">The ISEFileCollection Object</span></span>
  <span data-ttu-id="58418-104">O **ISEFileCollection** objeto é uma coleção de **ISEFile** objetos.</span><span class="sxs-lookup"><span data-stu-id="58418-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="58418-105">Um exemplo é uma coleção $psISE.CurrentPowerShellTab.Files.</span><span class="sxs-lookup"><span data-stu-id="58418-105">An example is the $psISE.CurrentPowerShellTab.Files collection.</span></span>

## <a name="methods"></a><span data-ttu-id="58418-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="58418-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="58418-107">Adicionar\( \[fullPath\]\)</span><span class="sxs-lookup"><span data-stu-id="58418-107">Add\( \[fullPath\] \)</span></span>
  <span data-ttu-id="58418-108">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="58418-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="58418-109">Cria e devolve um novo ficheiro untitled e adiciona-o para a coleção.</span><span class="sxs-lookup"><span data-stu-id="58418-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="58418-110">O **IsUntitled** é propriedade do ficheiro recém-criado **$true**.</span><span class="sxs-lookup"><span data-stu-id="58418-110">The **IsUntitled** property of the newly created file is **$true**.</span></span>

 <span data-ttu-id="58418-111">**\[fullPath\]**  - opcional da cadeia de caminho completamente especificado do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="58418-111">**\[fullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="58418-112">Uma exceção é gerada se incluir o **fullPath** parâmetro e um caminho relativo, mas se utilizar um nome de ficheiro em vez do caminho completo.</span><span class="sxs-lookup"><span data-stu-id="58418-112">An exception is generated if you include the **fullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")

```

### <a name="remove-file-force-"></a><span data-ttu-id="58418-113">Remover\( ficheiro, \[Force\]\)</span><span class="sxs-lookup"><span data-stu-id="58418-113">Remove\( File, \[Force\] \)</span></span>
  <span data-ttu-id="58418-114">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="58418-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="58418-115">Remove um ficheiro especificado no separador atual do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58418-115">Removes a specified file from the current PowerShell tab.</span></span>

 <span data-ttu-id="58418-116">**Ficheiro** -ficheiro ISEFile a cadeia que pretende remover da coleção.</span><span class="sxs-lookup"><span data-stu-id="58418-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="58418-117">Se não foi guardado o ficheiro, este método emite uma exceção.</span><span class="sxs-lookup"><span data-stu-id="58418-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="58418-118">Utilize o **forçar** comutador parâmetro para forçar a remoção de um ficheiro não guardada.</span><span class="sxs-lookup"><span data-stu-id="58418-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

 <span data-ttu-id="58418-119">**\[Force\]**  -opcional booleano se definido como **$true**, concede permissão para remover o ficheiro, mesmo que não foi guardado após a última utilização.</span><span class="sxs-lookup"><span data-stu-id="58418-119">**\[Force\]** - optional Boolean If set to **$true**, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="58418-120">A predefinição é **$false**.</span><span class="sxs-lookup"><span data-stu-id="58418-120">The default is **$false**.</span></span>

```
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="58418-121">SetSelectedFile\( selectedFile\)</span><span class="sxs-lookup"><span data-stu-id="58418-121">SetSelectedFile\( selectedFile \)</span></span>
  <span data-ttu-id="58418-122">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="58418-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="58418-123">Seleciona o ficheiro que é especificado pelo **selectedFile** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="58418-123">Selects the file that is specified by the **selectedFile** parameter.</span></span>

 <span data-ttu-id="58418-124">**selectedFile** -Microsoft.PowerShell.Host.ISE.ISEFile ISEFile do ficheiro que pretende selecionar.</span><span class="sxs-lookup"><span data-stu-id="58418-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```

# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)

```

## <a name="see-also"></a><span data-ttu-id="58418-125">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="58418-125">See Also</span></span>
- [<span data-ttu-id="58418-126">O objeto de ISEFile</span><span class="sxs-lookup"><span data-stu-id="58418-126">The ISEFile Object</span></span>](The-ISEFile-Object.md) 
- [<span data-ttu-id="58418-127">O ISE do Windows PowerShell modelo de objeto de Scripting</span><span class="sxs-lookup"><span data-stu-id="58418-127">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="58418-128">Referência de modelo de objeto do Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="58418-128">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="58418-129">A hierarquia de modelo de objeto ISE</span><span class="sxs-lookup"><span data-stu-id="58418-129">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
