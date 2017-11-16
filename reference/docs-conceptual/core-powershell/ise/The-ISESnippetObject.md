---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: O ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: 6112f5252d2d1e868092da4a6cd04feb1875b597
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/31/2017
---
# <a name="the-isesnippetobject"></a>O ISESnippetObject
  Um **ISESnippet** objeto é uma instância da classe Microsoft.PowerShell.Host.ISE.ISESnippet. Os membros de **$psISE.CurrentPowerShellTab.Snippets** coleção se todos os exemplos de **ISESnippet** objetos. A forma mais fácil de criar um fragmento consiste em utilizar o [New-IseSnippet &#91; PSITPro5_ISE &#93; ](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.

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
- [O ISE do Windows PowerShell modelo de objeto de Scripting](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referência de modelo de objeto do Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [A hierarquia de modelo de objeto ISE](The-ISE-Object-Model-Hierarchy.md)

  
