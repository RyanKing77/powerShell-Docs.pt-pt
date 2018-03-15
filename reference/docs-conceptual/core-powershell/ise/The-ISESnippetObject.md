---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f1b023291826d5568eb8bdf5a898a00228825276
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="the-isesnippetobject"></a>ISESnippetObject
  Um **ISESnippet** objeto é uma instância da classe Microsoft.PowerShell.Host.ISE.ISESnippet. Os membros de **$psISE.CurrentPowerShellTab.Snippets** coleção se todos os exemplos de **ISESnippet** objetos. A forma mais fácil de criar um fragmento consiste em utilizar o [New-IseSnippet&#91;PSITPro5_ISE&#93; ](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.

## <a name="properties"></a>Propriedades

### <a name="author"></a>autor
  Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

 A propriedade só de leitura que obtém o nome do autor de fragmento.

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

### <a name="codefragment"></a>CodeFragment
  Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

 A propriedade só de leitura que obtém o fragmento de código a inserir no editor.

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

### <a name="shortcut"></a>Atalho
  Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

 A propriedade só de leitura que obtém a Windows teclado atalho para o item de menu.

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Consulte Também
- [O objeto de ISESnippetCollection](The-ISESnippetCollection-Object.md)
- [Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)
