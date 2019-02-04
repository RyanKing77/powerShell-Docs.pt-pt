---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISEFile
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 24549720b8bc35435882533b0eb138de432ede65
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685138"
---
# <a name="the-isefile-object"></a>Objeto ISEFile

Uma **ISEFile** objeto representa um arquivo no Windows PowerShell® Integrated Scripting Environment (ISE). É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEFile. Este tópico apresenta uma lista de seus métodos de membro e propriedades de membro. O **$psISE.CurrentFile** e os ficheiros da coleção de ficheiros num separador do PowerShell são todas as instâncias da classe Microsoft.PowerShell.Host.ISE.ISEFile.

## <a name="methods"></a>Métodos

### <a name="save-saveencoding-"></a>Save\( \[saveEncoding\] \)

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

Guarda o ficheiro de disco.

**\[saveEncoding\]**  - opcional [Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) um parâmetro a ser utilizado para o ficheiro guardado de codificação de caracteres opcional. O valor predefinido é **UTF8**.

### <a name="exceptions"></a>Exceções

- **System.IO.IOException**: Não foi possível guardar o ficheiro.

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

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

Guarda o ficheiro com o nome de ficheiro especificado e a codificação.

**nome de ficheiro** -o nome a ser utilizada para guardar o ficheiro de cadeias de caracteres.

**\[saveEncoding\]**  - opcional [Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) um parâmetro a ser utilizado para o ficheiro guardado de codificação de caracteres opcional. O valor predefinido é **UTF8**.

### <a name="exceptions"></a>Exceções

- **System.ArgumentNullException**: O **filename** parâmetro é nulo.
- **System.ArgumentException**: O **filename** parâmetro está vazio.
- **System.IO.IOException**: Não foi possível guardar o ficheiro.

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a>Propriedades

### <a name="displayname"></a>NomeaApresentar

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade só de leitura que obtém a cadeia que contém o nome a apresentar deste ficheiro. O nome é mostrado no **ficheiro** separador na parte superior do editor. A presença de um asterisco \( \* \) no final do nome indica que o ficheiro tem alterações que não foram guardadas.

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a>Editor

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade só de leitura que obtém a [editor de objeto](The-ISEEditor-Object.md) que é utilizado para o ficheiro especificado.

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a>Encoding

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade só de leitura que obtém a codificação de ficheiro original. Este é um **Encoding** objeto.

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a>FullPath

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade só de leitura que obtém a cadeia de caracteres que especifica o caminho completo do ficheiro aberto.

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a>IsSaved

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade booleana só de leitura que retorna **$true** se foi guardado o ficheiro depois foi modificado pela última vez.

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a>IsUntitled

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade só de leitura que retorna **$true** se o ficheiro nunca recebeu um título.

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a>Veja Também

- [O ISEFileCollectionObject](The-ISEFileCollection-Object.md)
- [Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)