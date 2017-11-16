---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: O objeto de ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: b19c5b5c88f7c8bd0d0c466c7861fa9288bdc7a2
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="the-isesnippetcollection-object"></a>O objeto de ISESnippetCollection
  O **ISESnippetCollection** objeto é uma coleção de **ISESnippet** objetos. A coleção de ficheiros que está associada um **PowerShellTab** objeto é um membro desta classe. Um exemplo é o **$psISE.CurrentPowerShellTab.Files** coleção.

## <a name="methods"></a>Métodos

### <a name="load-filepathname-"></a>Carga\( FilePathName\)
  Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores. 

 Carrega um. snippets.ps1xml ficheiro que contém fragmentos definido pelo utilizador. A forma mais fácil criar fragmentos consiste em utilizar o cmdlet New-IseSnippet, que armazena-os automaticamente na sua pasta de perfil que sejam carregados sempre que iniciar o ISE do Windows PowerShell.

 **FilePathName** - o caminho de cadeia e ficheiro o nome de um. snippets.ps1xml ficheiro que contém as definições de fragmento.

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## <a name="see-also"></a>Consulte Também
- [O ISESnippetObject](The-ISESnippetObject.md) 
- [O ISE do Windows PowerShell modelo de objeto de Scripting](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referência de modelo de objeto do Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [A hierarquia de modelo de objeto ISE](The-ISE-Object-Model-Hierarchy.md)

  
