---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="the-isesnippetcollection-object"></a>Objeto ISESnippetCollection

O **ISESnippetCollection** objeto é uma coleção de **ISESnippet** objetos. A coleção de ficheiros que está associada um **PowerShellTab** objeto é um membro desta classe. Um exemplo é o **$psISE.CurrentPowerShellTab.Files** coleção.

## <a name="methods"></a>Métodos

### <a name="load-filepathname-"></a>Load\( FilePathName \)

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

Carrega um. snippets.ps1xml ficheiro que contém fragmentos definido pelo utilizador. A forma mais fácil criar fragmentos consiste em utilizar o cmdlet New-IseSnippet, que armazena-os automaticamente na sua pasta de perfil que sejam carregados sempre que iniciar o ISE do Windows PowerShell.

**FilePathName** - o caminho de cadeia e ficheiro o nome de um. snippets.ps1xml ficheiro que contém as definições de fragmento.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Consulte Também

- [O ISESnippetObject](The-ISESnippetObject.md)
- [Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)