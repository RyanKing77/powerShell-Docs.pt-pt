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
---
# <a name="the-isefilecollection-object"></a>Objeto ISEFileCollection

O **ISEFileCollection** objeto é uma coleção de **ISEFile** objetos. Um exemplo é uma coleção $psISE.CurrentPowerShellTab.Files.

## <a name="methods"></a>Métodos

### <a name="add-fullpath-"></a>Adicionar\( \[fullPath\] \)

Suportado no Windows PowerShell ISE 2.0 e posterior.

Cria e devolve um novo ficheiro untitled e adiciona-o para a coleção. O **IsUntitled** é propriedade do ficheiro recém-criado **$true**.

**\[fullPath\]**  - opcional da cadeia de caminho completamente especificado do ficheiro. Uma exceção é gerada se incluir o **fullPath** parâmetro e um caminho relativo, mas se utilizar um nome de ficheiro em vez do caminho completo.

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a>Remover\( ficheiro, \[Force\] \)

Suportado no Windows PowerShell ISE 2.0 e posterior.

Remove um ficheiro especificado no separador atual do PowerShell.

**Ficheiro** -ficheiro ISEFile a cadeia que pretende remover da coleção. Se não foi guardado o ficheiro, este método emite uma exceção. Utilize o **forçar** comutador parâmetro para forçar a remoção de um ficheiro não guardada.

**\[Force\]**  -opcional booleano se definido como **$true**, concede permissão para remover o ficheiro, mesmo que não foi guardado após a última utilização. A predefinição é **$false**.

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

Suportado no Windows PowerShell ISE 2.0 e posterior.

Seleciona o ficheiro que é especificado pelo **selectedFile** parâmetro.

**selectedFile** -Microsoft.PowerShell.Host.ISE.ISEFile ISEFile do ficheiro que pretende selecionar.

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a>Consulte Também

- [O objeto de ISEFile](The-ISEFile-Object.md)
- [Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)