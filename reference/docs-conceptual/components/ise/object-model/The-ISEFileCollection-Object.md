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
# <a name="the-isefilecollection-object"></a>Objeto ISEFileCollection

O **ISEFileCollection** objeto é uma coleção de **ISEFile** objetos. Um exemplo é uma coleção $psISE.CurrentPowerShellTab.Files.

## <a name="methods"></a>Métodos

### <a name="add-fullpath-"></a>Add\( \[fullPath\] \)

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

Cria e retorna um novo ficheiro sem título e o adiciona à coleção. O **IsUntitled** é de propriedade do ficheiro recentemente criado **$true**.

**\[fullPath\]**  - opcional o caminho totalmente especificado do arquivo de cadeias de caracteres. Uma exceção é gerada se incluir o **fullPath** parâmetro e um caminho relativo, ou se utilizar um nome de ficheiro em vez do caminho completo.

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a>Remova\( arquivo, \[Force\] \)

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

Remove um ficheiro especificado do separador atual do PowerShell.

**Ficheiro** -cadeia de caracteres de ISEFile o ficheiro que pretende remover da coleção. Se o ficheiro não foi salvo, esse método lança uma exceção. Utilize o **forçar** mudar o parâmetro para forçar a remoção de um arquivo não guardada.

**\[Força\]**  -opcional booleano se definido como **$true**, concede permissão para remover o ficheiro, mesmo que não foi guardado após a última utilização. A predefinição é **$false**.

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a>SetSelectedFile\( selectedFile \)

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

Seleciona o ficheiro especificado pelos **selectedFile** parâmetro.

**selectedFile** -Microsoft.PowerShell.Host.ISE.ISEFile ISEFile do ficheiro que pretende selecionar.

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a>Veja Também

- [Objeto ISEFile](The-ISEFile-Object.md)
- [Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)