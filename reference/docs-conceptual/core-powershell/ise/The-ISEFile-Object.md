---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: O objeto de ISEFile
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: a1fbd48e872684cc578adb03f52430eabdc54c2c
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefile-object"></a><span data-ttu-id="f7dff-103">O objeto de ISEFile</span><span class="sxs-lookup"><span data-stu-id="f7dff-103">The ISEFile Object</span></span>
  <span data-ttu-id="f7dff-104">Um **ISEFile** objeto representa um ficheiro no Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="f7dff-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="f7dff-105">É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="f7dff-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="f7dff-106">Este tópico lista os métodos de membro e propriedades de membro.</span><span class="sxs-lookup"><span data-stu-id="f7dff-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="f7dff-107">O **$psISE.CurrentFile** e os ficheiros na coleção de ficheiros num separador PowerShell estão todas as instâncias da classe Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="f7dff-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="f7dff-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="f7dff-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="f7dff-109">Guardar\( \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="f7dff-109">Save\( \[saveEncoding\] \)</span></span>
  <span data-ttu-id="f7dff-110">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="f7dff-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f7dff-111">Guarda o ficheiro de disco.</span><span class="sxs-lookup"><span data-stu-id="f7dff-111">Saves the file to disk.</span></span>

 <span data-ttu-id="f7dff-112">**\[saveEncoding\]**  - opcional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) um caráter opcional codificação parâmetro a ser utilizada para o ficheiro guardado.</span><span class="sxs-lookup"><span data-stu-id="f7dff-112">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="f7dff-113">O valor predefinido é **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="f7dff-113">The default value is **UTF8**.</span></span>

 <span data-ttu-id="f7dff-114">**Exceções**</span><span class="sxs-lookup"><span data-stu-id="f7dff-114">**Exceptions**</span></span>
 -   <span data-ttu-id="f7dff-115">**System.IO.IOException**: não foi possível guardar o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="f7dff-115">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="f7dff-116">SaveAs\(filename, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="f7dff-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>
  <span data-ttu-id="f7dff-117">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="f7dff-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f7dff-118">Codificação e guarda o ficheiro com o nome de ficheiro especificado.</span><span class="sxs-lookup"><span data-stu-id="f7dff-118">Saves the file with the specified file name and encoding.</span></span>

 <span data-ttu-id="f7dff-119">**nome de ficheiro** -o nome a ser utilizada para guardar o ficheiro de cadeia.</span><span class="sxs-lookup"><span data-stu-id="f7dff-119">**filename** - String The name to be used to save the file.</span></span>

 <span data-ttu-id="f7dff-120">**\[saveEncoding\]**  - opcional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) um caráter opcional codificação parâmetro a ser utilizada para o ficheiro guardado.</span><span class="sxs-lookup"><span data-stu-id="f7dff-120">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="f7dff-121">O valor predefinido é **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="f7dff-121">The default value is **UTF8**.</span></span>

 <span data-ttu-id="f7dff-122">**Exceções**</span><span class="sxs-lookup"><span data-stu-id="f7dff-122">**Exceptions**</span></span>
 -   <span data-ttu-id="f7dff-123">**Argumentnullexception**: O **filename** parâmetro é nulo.</span><span class="sxs-lookup"><span data-stu-id="f7dff-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>

- <span data-ttu-id="f7dff-124">**System.ArgumentException**: O **filename** parâmetro está vazio.</span><span class="sxs-lookup"><span data-stu-id="f7dff-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>

- <span data-ttu-id="f7dff-125">**System.IO.IOException**: não foi possível guardar o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="f7dff-125">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a><span data-ttu-id="f7dff-126">Propriedades</span><span class="sxs-lookup"><span data-stu-id="f7dff-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="f7dff-127">NomeaApresentar</span><span class="sxs-lookup"><span data-stu-id="f7dff-127">DisplayName</span></span>
  <span data-ttu-id="f7dff-128">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="f7dff-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="f7dff-129">A propriedade só de leitura que obtém a cadeia que contém o nome a apresentar deste ficheiro.</span><span class="sxs-lookup"><span data-stu-id="f7dff-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="f7dff-130">O nome é apresentado no **ficheiro** separador no topo do editor.</span><span class="sxs-lookup"><span data-stu-id="f7dff-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="f7dff-131">A presença de um asterisco \( \* \) no fim do nome indica que o ficheiro tem alterações que não foram guardadas.</span><span class="sxs-lookup"><span data-stu-id="f7dff-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

### <a name="editor"></a><span data-ttu-id="f7dff-132">Editor</span><span class="sxs-lookup"><span data-stu-id="f7dff-132">Editor</span></span>
  <span data-ttu-id="f7dff-133">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="f7dff-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f7dff-134">A propriedade só de leitura que obtém a [editor objeto](The-ISEEditor-Object.md) que é utilizado para o ficheiro especificado.</span><span class="sxs-lookup"><span data-stu-id="f7dff-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

### <a name="encoding"></a><span data-ttu-id="f7dff-135">Codificação</span><span class="sxs-lookup"><span data-stu-id="f7dff-135">Encoding</span></span>
  <span data-ttu-id="f7dff-136">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="f7dff-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f7dff-137">A propriedade só de leitura que obtém a codificação de ficheiro original.</span><span class="sxs-lookup"><span data-stu-id="f7dff-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="f7dff-138">Este é um **System.Text.Encoding** objeto.</span><span class="sxs-lookup"><span data-stu-id="f7dff-138">This is a **System.Text.Encoding** object.</span></span>

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

### <a name="fullpath"></a><span data-ttu-id="f7dff-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="f7dff-139">FullPath</span></span>
  <span data-ttu-id="f7dff-140">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="f7dff-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f7dff-141">A propriedade só de leitura que obtém a cadeia que especifica o caminho completo do ficheiro está aberto.</span><span class="sxs-lookup"><span data-stu-id="f7dff-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

### <a name="issaved"></a><span data-ttu-id="f7dff-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="f7dff-142">IsSaved</span></span>
  <span data-ttu-id="f7dff-143">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="f7dff-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f7dff-144">A propriedade booleana só de leitura que devolve **$true** se o ficheiro foi guardado após foi modificado pela última vez.</span><span class="sxs-lookup"><span data-stu-id="f7dff-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

### <a name="isuntitled"></a><span data-ttu-id="f7dff-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="f7dff-145">IsUntitled</span></span>
  <span data-ttu-id="f7dff-146">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="f7dff-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f7dff-147">A propriedade só de leitura que devolve **$true** se o ficheiro nunca foi indicado um título.</span><span class="sxs-lookup"><span data-stu-id="f7dff-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a><span data-ttu-id="f7dff-148">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="f7dff-148">See Also</span></span>
- [<span data-ttu-id="f7dff-149">O ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="f7dff-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md) 
- [<span data-ttu-id="f7dff-150">O ISE do Windows PowerShell modelo de objeto de Scripting</span><span class="sxs-lookup"><span data-stu-id="f7dff-150">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="f7dff-151">Referência de modelo de objeto do Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f7dff-151">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="f7dff-152">A hierarquia de modelo de objeto ISE</span><span class="sxs-lookup"><span data-stu-id="f7dff-152">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
