---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f80080f4207cf226fb7466c4842446d08c081347
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="the-isesnippetobject"></a>ISESnippetObject

Um **ISESnippet** objeto é uma instância da classe Microsoft.PowerShell.Host.ISE.ISESnippet. Os membros de **$psISE.CurrentPowerShellTab.Snippets** coleção se todos os exemplos de **ISESnippet** objetos. A forma mais fácil de criar um fragmento consiste em utilizar o [New-IseSnippet&#91;PSITPro5_ISE&#93; ](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.

## <a name="properties"></a>Propriedades

### <a name="author"></a>autor

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

A propriedade só de leitura que obtém o nome do autor de fragmento.

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a>CodeFragment

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

A propriedade só de leitura que obtém o fragmento de código a inserir no editor.

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a>Atalho

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

A propriedade só de leitura que obtém a Windows teclado atalho para o item de menu.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Consulte Também

- [O objeto de ISESnippetCollection](The-ISESnippetCollection-Object.md)
- [Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)