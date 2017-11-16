---
ms.date: 2017-08-25
keywords: PowerShell, o cmdlet
title: O objeto de ObjectModelRoot
ms.openlocfilehash: eb3424ff147c35364fa08543d59ebd30f6d2d857
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="the-objectmodelroot-object"></a>O objeto de ObjectModelRoot

O **$psISE** objeto, que é o objeto principal raiz no Windows PowerShell® Integrated Scripting Environment (ISE) é uma instância da classe Microsoft.PowerShell.Host.ISE.ObjectModelRoot.
Este tópico descreve as propriedades do **ObjectModelRoot** objeto.

## <a name="properties"></a>Propriedades

### <a name="currentfile"></a>CurrentFile

> Suportado no Windows PowerShell ISE 2.0 e posterior. 

A propriedade só de leitura que obtém o ficheiro, que está associado este objeto de anfitrião que tem actualmente o foco.

### <a name="currentpowershelltab"></a>CurrentPowerShellTab

> Suportado no Windows PowerShell ISE 2.0 e posterior.

A propriedade só de leitura que obtém o separador do PowerShell que tem o foco.

### <a name="currentvisiblehorizontaltool"></a>CurrentVisibleHorizontalTool

> Suportado no Windows PowerShell ISE 2.0 e posterior.

A propriedade só de leitura que obtém a ferramenta de suplemento atualmente visível do ISE do Windows PowerShell que está localizada no painel de ferramenta horizontal na parte inferior do editor.

### <a name="currentvisibleverticaltool"></a>CurrentVisibleVerticalTool

> Suportado no Windows PowerShell ISE 2.0 e posterior. 

A propriedade só de leitura que obtém a ferramenta de suplemento atualmente visível do ISE do Windows PowerShell que está localizada no painel de ferramenta vertical no lado direito do editor.

### <a name="options"></a>Opções

> Suportado no Windows PowerShell ISE 2.0 e posterior. 

A propriedade só de leitura que obtém as várias opções que pode alterar as definições no ISE do Windows PowerShell.

### <a name="powershelltabs"></a>PowerShellTabs

> Suportado no Windows PowerShell ISE 2.0 e posterior. 

A propriedade só de leitura que obtém a coleção dos separadores do PowerShell, que estão abertos no ISE do Windows PowerShell. Por predefinição, este objeto contém um separador de PowerShell. No entanto, pode adicionar mais separadores de PowerShell para este objeto utilizando scripts ou utilizando os menus no ISE do Windows PowerShell.

## <a name="see-also"></a>Consulte Também

- [O ISE do Windows PowerShell modelo de objeto de Scripting](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Referência de modelo de objeto do Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [A hierarquia de modelo de objeto ISE](The-ISE-Object-Model-Hierarchy.md)
