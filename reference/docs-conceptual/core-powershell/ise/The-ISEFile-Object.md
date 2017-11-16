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
# <a name="the-isefile-object"></a>O objeto de ISEFile
  Um **ISEFile** objeto representa um ficheiro no Windows PowerShell® Integrated Scripting Environment (ISE). É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEFile. Este tópico lista os métodos de membro e propriedades de membro. O **$psISE.CurrentFile** e os ficheiros na coleção de ficheiros num separador PowerShell estão todas as instâncias da classe Microsoft.PowerShell.Host.ISE.ISEFile.

## <a name="methods"></a>Métodos

### <a name="save-saveencoding-"></a>Guardar\( \[saveEncoding\]\)
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 Guarda o ficheiro de disco.

 **\[saveEncoding\]**  - opcional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) um caráter opcional codificação parâmetro a ser utilizada para o ficheiro guardado. O valor predefinido é **UTF8**.

 **Exceções**
 -   **System.IO.IOException**: não foi possível guardar o ficheiro.

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

### <a name="saveasfilename-saveencoding"></a>SaveAs\(filename, \[saveEncoding\]\)
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 Codificação e guarda o ficheiro com o nome de ficheiro especificado.

 **nome de ficheiro** -o nome a ser utilizada para guardar o ficheiro de cadeia.

 **\[saveEncoding\]**  - opcional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) um caráter opcional codificação parâmetro a ser utilizada para o ficheiro guardado. O valor predefinido é **UTF8**.

 **Exceções**
 -   **Argumentnullexception**: O **filename** parâmetro é nulo.

- **System.ArgumentException**: O **filename** parâmetro está vazio.

- **System.IO.IOException**: não foi possível guardar o ficheiro.

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a>Propriedades

### <a name="displayname"></a>NomeaApresentar
  Suportado no Windows PowerShell ISE 2.0 e posterior.

 A propriedade só de leitura que obtém a cadeia que contém o nome a apresentar deste ficheiro. O nome é apresentado no **ficheiro** separador no topo do editor. A presença de um asterisco \( \* \) no fim do nome indica que o ficheiro tem alterações que não foram guardadas.

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

### <a name="editor"></a>Editor
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade só de leitura que obtém a [editor objeto](The-ISEEditor-Object.md) que é utilizado para o ficheiro especificado.

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

### <a name="encoding"></a>Codificação
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade só de leitura que obtém a codificação de ficheiro original. Este é um **System.Text.Encoding** objeto.

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

### <a name="fullpath"></a>FullPath
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade só de leitura que obtém a cadeia que especifica o caminho completo do ficheiro está aberto.

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

### <a name="issaved"></a>IsSaved
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade booleana só de leitura que devolve **$true** se o ficheiro foi guardado após foi modificado pela última vez.

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

### <a name="isuntitled"></a>IsUntitled
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade só de leitura que devolve **$true** se o ficheiro nunca foi indicado um título.

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a>Consulte Também
- [O ISEFileCollectionObject](The-ISEFileCollection-Object.md) 
- [O ISE do Windows PowerShell modelo de objeto de Scripting](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referência de modelo de objeto do Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [A hierarquia de modelo de objeto ISE](The-ISE-Object-Model-Hierarchy.md)
