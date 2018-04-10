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
# <a name="the-isefile-object"></a>Objeto ISEFile

Um **ISEFile** objeto representa um ficheiro no Windows PowerShell® Integrated Scripting Environment (ISE). É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEFile. Este tópico lista os métodos de membro e propriedades de membro. O **$psISE.CurrentFile** e os ficheiros na coleção de ficheiros num separador PowerShell estão todas as instâncias da classe Microsoft.PowerShell.Host.ISE.ISEFile.

## <a name="methods"></a>Métodos

### <a name="save-saveencoding-"></a>Save\( \[saveEncoding\] \)

Suportado no Windows PowerShell ISE 2.0 e posterior.

Guarda o ficheiro de disco.

**\[saveEncoding\]**  - opcional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) um caráter opcional codificação parâmetro a ser utilizada para o ficheiro guardado. O valor predefinido é **UTF8**.

### <a name="exceptions"></a>Exceções

- **System.IO.IOException**: não foi possível guardar o ficheiro.

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a>SaveAs\(filename, \[saveEncoding\]\)

Suportado no Windows PowerShell ISE 2.0 e posterior.

Codificação e guarda o ficheiro com o nome de ficheiro especificado.

**nome de ficheiro** -o nome a ser utilizada para guardar o ficheiro de cadeia.

**\[saveEncoding\]**  - opcional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) um caráter opcional codificação parâmetro a ser utilizada para o ficheiro guardado. O valor predefinido é **UTF8**.

### <a name="exceptions"></a>Exceções

- **Argumentnullexception**: O **filename** parâmetro é nulo.
- **System.ArgumentException**: O **filename** parâmetro está vazio.
- **System.IO.IOException**: não foi possível guardar o ficheiro.

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a>Propriedades

### <a name="displayname"></a>NomeaApresentar

Suportado no Windows PowerShell ISE 2.0 e posterior.

A propriedade só de leitura que obtém a cadeia que contém o nome a apresentar deste ficheiro. O nome é apresentado no **ficheiro** separador no topo do editor. A presença de um asterisco \( \* \) no fim do nome indica que o ficheiro tem alterações que não foram guardadas.

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a>Editor

Suportado no Windows PowerShell ISE 2.0 e posterior.

A propriedade só de leitura que obtém a [editor objeto](The-ISEEditor-Object.md) que é utilizado para o ficheiro especificado.

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a>Codificação

Suportado no Windows PowerShell ISE 2.0 e posterior.

A propriedade só de leitura que obtém a codificação de ficheiro original. Este é um **System.Text.Encoding** objeto.

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a>FullPath

Suportado no Windows PowerShell ISE 2.0 e posterior.

A propriedade só de leitura que obtém a cadeia que especifica o caminho completo do ficheiro está aberto.

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a>IsSaved

Suportado no Windows PowerShell ISE 2.0 e posterior.

A propriedade booleana só de leitura que devolve **$true** se o ficheiro foi guardado após foi modificado pela última vez.

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a>IsUntitled

Suportado no Windows PowerShell ISE 2.0 e posterior.

A propriedade só de leitura que devolve **$true** se o ficheiro nunca foi indicado um título.

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a>Consulte Também

- [O ISEFileCollectionObject](The-ISEFileCollection-Object.md)
- [Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)