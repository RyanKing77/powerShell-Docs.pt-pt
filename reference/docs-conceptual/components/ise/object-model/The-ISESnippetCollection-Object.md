---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405561"
---
# <a name="the-isesnippetcollection-object"></a>Objeto ISESnippetCollection

O **ISESnippetCollection** objeto é uma coleção de **ISESnippet** objetos. A coleção de ficheiros que está associada um **PowerShellTab** objeto é um membro dessa classe. Um exemplo é o **$psISE.CurrentPowerShellTab.Files** coleção.

## <a name="methods"></a>Métodos

### <a name="load-filepathname-"></a>Carga\( FilePathName \)

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.

Carrega um. snippets.ps1xml ficheiro que contém trechos de código definido pelo utilizador. A maneira mais fácil de criar trechos de código é usar o cmdlet New-IseSnippet, que armazena-os automaticamente na sua pasta de perfil para que eles são carregados sempre que iniciar o ISE do Windows PowerShell.

**FilePathName** - o caminho de cadeias de caracteres e ficheiro o nome para um. snippets.ps1xml ficheiro que contém definições de Trecho de código.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Consulte Também

- [ISESnippetObject](The-ISESnippetObject.md)
- [Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)