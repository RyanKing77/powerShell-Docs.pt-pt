---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f80080f4207cf226fb7466c4842446d08c081347
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405546"
---
# <a name="the-isesnippetobject"></a>ISESnippetObject

Uma **ISESnippet** objeto é uma instância da classe Microsoft.PowerShell.Host.ISE.ISESnippet. Os membros do **$psISE.CurrentPowerShellTab.Snippets** coleção são todos exemplos de **ISESnippet** objetos. A maneira mais fácil para criar um trecho de código é usar o [New-IseSnippet&#91;PSITPro5_ISE&#93; ](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.

## <a name="properties"></a>Propriedades

### <a name="author"></a>Autor

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.

A propriedade só de leitura que obtém o nome do autor do trecho.

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a>CodeFragment

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.

A propriedade só de leitura que obtém o fragmento de código a ser inserido no editor.

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a>Atalho

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.

A propriedade só de leitura que obtém o Windows teclado atalho para o item de menu.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Consulte Também

- [Objeto ISESnippetCollection](The-ISESnippetCollection-Object.md)
- [Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)