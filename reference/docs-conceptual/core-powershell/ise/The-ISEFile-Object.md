---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISEFile
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 276e8f04a827e18999b5b3ecb08f47de4f4b23b1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="the-isefile-object"></a><span data-ttu-id="380e0-103">Objeto ISEFile</span><span class="sxs-lookup"><span data-stu-id="380e0-103">The ISEFile Object</span></span>

<span data-ttu-id="380e0-104">Um **ISEFile** objeto representa um ficheiro no Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="380e0-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="380e0-105">É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="380e0-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="380e0-106">Este tópico lista os métodos de membro e propriedades de membro.</span><span class="sxs-lookup"><span data-stu-id="380e0-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="380e0-107">O **$psISE.CurrentFile** e os ficheiros na coleção de ficheiros num separador PowerShell estão todas as instâncias da classe Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="380e0-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="380e0-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="380e0-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="380e0-109">Save\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="380e0-109">Save\( \[saveEncoding\] \)</span></span>

<span data-ttu-id="380e0-110">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="380e0-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="380e0-111">Guarda o ficheiro de disco.</span><span class="sxs-lookup"><span data-stu-id="380e0-111">Saves the file to disk.</span></span>

<span data-ttu-id="380e0-112">**\[saveEncoding\]**  - opcional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) um caráter opcional codificação parâmetro a ser utilizada para o ficheiro guardado.</span><span class="sxs-lookup"><span data-stu-id="380e0-112">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="380e0-113">O valor predefinido é **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="380e0-113">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="380e0-114">Exceções</span><span class="sxs-lookup"><span data-stu-id="380e0-114">Exceptions</span></span>

- <span data-ttu-id="380e0-115">**System.IO.IOException**: não foi possível guardar o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="380e0-115">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="380e0-116">SaveAs\(filename, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="380e0-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>

<span data-ttu-id="380e0-117">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="380e0-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="380e0-118">Codificação e guarda o ficheiro com o nome de ficheiro especificado.</span><span class="sxs-lookup"><span data-stu-id="380e0-118">Saves the file with the specified file name and encoding.</span></span>

<span data-ttu-id="380e0-119">**nome de ficheiro** -o nome a ser utilizada para guardar o ficheiro de cadeia.</span><span class="sxs-lookup"><span data-stu-id="380e0-119">**filename** - String The name to be used to save the file.</span></span>

<span data-ttu-id="380e0-120">**\[saveEncoding\]**  - opcional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) um caráter opcional codificação parâmetro a ser utilizada para o ficheiro guardado.</span><span class="sxs-lookup"><span data-stu-id="380e0-120">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="380e0-121">O valor predefinido é **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="380e0-121">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="380e0-122">Exceções</span><span class="sxs-lookup"><span data-stu-id="380e0-122">Exceptions</span></span>

- <span data-ttu-id="380e0-123">**Argumentnullexception**: O **filename** parâmetro é nulo.</span><span class="sxs-lookup"><span data-stu-id="380e0-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>
- <span data-ttu-id="380e0-124">**System.ArgumentException**: O **filename** parâmetro está vazio.</span><span class="sxs-lookup"><span data-stu-id="380e0-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>
- <span data-ttu-id="380e0-125">**System.IO.IOException**: não foi possível guardar o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="380e0-125">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a><span data-ttu-id="380e0-126">Propriedades</span><span class="sxs-lookup"><span data-stu-id="380e0-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="380e0-127">NomeaApresentar</span><span class="sxs-lookup"><span data-stu-id="380e0-127">DisplayName</span></span>

<span data-ttu-id="380e0-128">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="380e0-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="380e0-129">A propriedade só de leitura que obtém a cadeia que contém o nome a apresentar deste ficheiro.</span><span class="sxs-lookup"><span data-stu-id="380e0-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="380e0-130">O nome é apresentado no **ficheiro** separador no topo do editor.</span><span class="sxs-lookup"><span data-stu-id="380e0-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="380e0-131">A presença de um asterisco \( \* \) no fim do nome indica que o ficheiro tem alterações que não foram guardadas.</span><span class="sxs-lookup"><span data-stu-id="380e0-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a><span data-ttu-id="380e0-132">Editor</span><span class="sxs-lookup"><span data-stu-id="380e0-132">Editor</span></span>

<span data-ttu-id="380e0-133">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="380e0-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="380e0-134">A propriedade só de leitura que obtém a [editor objeto](The-ISEEditor-Object.md) que é utilizado para o ficheiro especificado.</span><span class="sxs-lookup"><span data-stu-id="380e0-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a><span data-ttu-id="380e0-135">Codificação</span><span class="sxs-lookup"><span data-stu-id="380e0-135">Encoding</span></span>

<span data-ttu-id="380e0-136">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="380e0-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="380e0-137">A propriedade só de leitura que obtém a codificação de ficheiro original.</span><span class="sxs-lookup"><span data-stu-id="380e0-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="380e0-138">Este é um **System.Text.Encoding** objeto.</span><span class="sxs-lookup"><span data-stu-id="380e0-138">This is a **System.Text.Encoding** object.</span></span>

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a><span data-ttu-id="380e0-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="380e0-139">FullPath</span></span>

<span data-ttu-id="380e0-140">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="380e0-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="380e0-141">A propriedade só de leitura que obtém a cadeia que especifica o caminho completo do ficheiro está aberto.</span><span class="sxs-lookup"><span data-stu-id="380e0-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a><span data-ttu-id="380e0-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="380e0-142">IsSaved</span></span>

<span data-ttu-id="380e0-143">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="380e0-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="380e0-144">A propriedade booleana só de leitura que devolve **$true** se o ficheiro foi guardado após foi modificado pela última vez.</span><span class="sxs-lookup"><span data-stu-id="380e0-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a><span data-ttu-id="380e0-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="380e0-145">IsUntitled</span></span>

<span data-ttu-id="380e0-146">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="380e0-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="380e0-147">A propriedade só de leitura que devolve **$true** se o ficheiro nunca foi indicado um título.</span><span class="sxs-lookup"><span data-stu-id="380e0-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a><span data-ttu-id="380e0-148">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="380e0-148">See Also</span></span>

- [<span data-ttu-id="380e0-149">O ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="380e0-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md)
- [<span data-ttu-id="380e0-150">Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do</span><span class="sxs-lookup"><span data-stu-id="380e0-150">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="380e0-151">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="380e0-151">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)