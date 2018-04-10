---
ms.date: 08/25/2017
keywords: PowerShell, o cmdlet
title: Objeto ObjectModelRoot
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="the-objectmodelroot-object"></a>Objeto ObjectModelRoot

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

- [Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)