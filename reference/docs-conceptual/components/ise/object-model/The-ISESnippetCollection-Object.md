---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISESnippetCollection
ms.openlocfilehash: 6c392c08767fba004f63155d5a469777856a0b59
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030511"
---
# <a name="the-isesnippetcollection-object"></a>Objeto ISESnippetCollection

O **ISESnippetCollection** objeto é uma coleção de **ISESnippet** objetos. A coleção de ficheiros que está associada um **PowerShellTab** objeto é um membro dessa classe. Um exemplo é o **$psISE.CurrentPowerShellTab.Files** coleção.

## <a name="methods"></a>Métodos

### <a name="load-filepathname-"></a>Load\( FilePathName \)

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.

Carrega um. snippets.ps1xml ficheiro que contém trechos de código definido pelo utilizador. A maneira mais fácil de criar trechos de código é usar o cmdlet New-IseSnippet, que armazena-os automaticamente na sua pasta de perfil para que eles são carregados sempre que iniciar o ISE do Windows PowerShell.

**FilePathName** - o caminho de cadeias de caracteres e ficheiro o nome para um. snippets.ps1xml ficheiro que contém definições de Trecho de código.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Veja Também

- [ISESnippetObject](The-ISESnippetObject.md)
- [Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)
