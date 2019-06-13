---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISEFile
ms.openlocfilehash: ebb5a35f6ea9d93eab633b9f4e6c84e4fddd6ae8
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028952"
---
# <a name="the-isefile-object"></a><span data-ttu-id="d604d-103">Objeto ISEFile</span><span class="sxs-lookup"><span data-stu-id="d604d-103">The ISEFile Object</span></span>

<span data-ttu-id="d604d-104">Uma **ISEFile** objeto representa um arquivo no Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="d604d-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="d604d-105">É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="d604d-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="d604d-106">Este tópico apresenta uma lista de seus métodos de membro e propriedades de membro.</span><span class="sxs-lookup"><span data-stu-id="d604d-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="d604d-107">O **$psISE.CurrentFile** e os ficheiros da coleção de ficheiros num separador do PowerShell são todas as instâncias da classe Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="d604d-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="d604d-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="d604d-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="d604d-109">Save\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="d604d-109">Save\( \[saveEncoding\] \)</span></span>

<span data-ttu-id="d604d-110">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="d604d-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d604d-111">Guarda o ficheiro de disco.</span><span class="sxs-lookup"><span data-stu-id="d604d-111">Saves the file to disk.</span></span>

<span data-ttu-id="d604d-112">**\[saveEncoding\]**  - opcional [Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) um parâmetro a ser utilizado para o ficheiro guardado de codificação de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="d604d-112">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="d604d-113">O valor predefinido é **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="d604d-113">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="d604d-114">Exceções</span><span class="sxs-lookup"><span data-stu-id="d604d-114">Exceptions</span></span>

- <span data-ttu-id="d604d-115">**System.IO.IOException**: Não foi possível guardar o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="d604d-115">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="d604d-116">SaveAs\(filename, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="d604d-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>

<span data-ttu-id="d604d-117">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="d604d-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d604d-118">Guarda o ficheiro com o nome de ficheiro especificado e a codificação.</span><span class="sxs-lookup"><span data-stu-id="d604d-118">Saves the file with the specified file name and encoding.</span></span>

<span data-ttu-id="d604d-119">**nome de ficheiro** -o nome a ser utilizada para guardar o ficheiro de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d604d-119">**filename** - String The name to be used to save the file.</span></span>

<span data-ttu-id="d604d-120">**\[saveEncoding\]**  - opcional [Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) um parâmetro a ser utilizado para o ficheiro guardado de codificação de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="d604d-120">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="d604d-121">O valor predefinido é **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="d604d-121">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="d604d-122">Exceções</span><span class="sxs-lookup"><span data-stu-id="d604d-122">Exceptions</span></span>

- <span data-ttu-id="d604d-123">**System.ArgumentNullException**: O **filename** parâmetro é nulo.</span><span class="sxs-lookup"><span data-stu-id="d604d-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>
- <span data-ttu-id="d604d-124">**System.ArgumentException**: O **filename** parâmetro está vazio.</span><span class="sxs-lookup"><span data-stu-id="d604d-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>
- <span data-ttu-id="d604d-125">**System.IO.IOException**: Não foi possível guardar o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="d604d-125">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a><span data-ttu-id="d604d-126">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d604d-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="d604d-127">DisplayName</span><span class="sxs-lookup"><span data-stu-id="d604d-127">DisplayName</span></span>

<span data-ttu-id="d604d-128">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="d604d-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d604d-129">A propriedade só de leitura que obtém a cadeia que contém o nome a apresentar deste ficheiro.</span><span class="sxs-lookup"><span data-stu-id="d604d-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="d604d-130">O nome é mostrado no **ficheiro** separador na parte superior do editor.</span><span class="sxs-lookup"><span data-stu-id="d604d-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="d604d-131">A presença de um asterisco \( \* \) no final do nome indica que o ficheiro tem alterações que não foram guardadas.</span><span class="sxs-lookup"><span data-stu-id="d604d-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a><span data-ttu-id="d604d-132">Editor</span><span class="sxs-lookup"><span data-stu-id="d604d-132">Editor</span></span>

<span data-ttu-id="d604d-133">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="d604d-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d604d-134">A propriedade só de leitura que obtém a [editor de objeto](The-ISEEditor-Object.md) que é utilizado para o ficheiro especificado.</span><span class="sxs-lookup"><span data-stu-id="d604d-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a><span data-ttu-id="d604d-135">Encoding</span><span class="sxs-lookup"><span data-stu-id="d604d-135">Encoding</span></span>

<span data-ttu-id="d604d-136">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="d604d-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d604d-137">A propriedade só de leitura que obtém a codificação de ficheiro original.</span><span class="sxs-lookup"><span data-stu-id="d604d-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="d604d-138">Este é um **Encoding** objeto.</span><span class="sxs-lookup"><span data-stu-id="d604d-138">This is a **System.Text.Encoding** object.</span></span>

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a><span data-ttu-id="d604d-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="d604d-139">FullPath</span></span>

<span data-ttu-id="d604d-140">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="d604d-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d604d-141">A propriedade só de leitura que obtém a cadeia de caracteres que especifica o caminho completo do ficheiro aberto.</span><span class="sxs-lookup"><span data-stu-id="d604d-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a><span data-ttu-id="d604d-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="d604d-142">IsSaved</span></span>

<span data-ttu-id="d604d-143">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="d604d-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d604d-144">A propriedade booleana só de leitura que retorna **$true** se foi guardado o ficheiro depois foi modificado pela última vez.</span><span class="sxs-lookup"><span data-stu-id="d604d-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a><span data-ttu-id="d604d-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="d604d-145">IsUntitled</span></span>

<span data-ttu-id="d604d-146">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="d604d-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d604d-147">A propriedade só de leitura que retorna **$true** se o ficheiro nunca recebeu um título.</span><span class="sxs-lookup"><span data-stu-id="d604d-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a><span data-ttu-id="d604d-148">Veja Também</span><span class="sxs-lookup"><span data-stu-id="d604d-148">See Also</span></span>

- [<span data-ttu-id="d604d-149">O ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="d604d-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md)
- [<span data-ttu-id="d604d-150">Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="d604d-150">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="d604d-151">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="d604d-151">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
