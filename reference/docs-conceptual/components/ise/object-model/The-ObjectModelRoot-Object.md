---
ms.date: 08/25/2017
keywords: PowerShell, o cmdlet
title: Objeto ObjectModelRoot
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684375"
---
# <a name="the-objectmodelroot-object"></a>Objeto ObjectModelRoot

O **$psISE** objeto, o que é o objeto raiz principal no Windows PowerShell® Integrated Scripting Environment (ISE) é uma instância da classe Microsoft.PowerShell.Host.ISE.ObjectModelRoot.
Este tópico descreve as propriedades do **ObjectModelRoot** objeto.

## <a name="properties"></a>Propriedades

### <a name="currentfile"></a>CurrentFile

> Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade só de leitura que obtém o arquivo, que está associado este objeto de host que atualmente possui o foco.

### <a name="currentpowershelltab"></a>CurrentPowerShellTab

> Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade só de leitura que obtém o separador do PowerShell que possui o foco.

### <a name="currentvisiblehorizontaltool"></a>CurrentVisibleHorizontalTool

> Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade só de leitura que obtém a ferramenta de suplemento visível no momento do ISE do Windows PowerShell que está localizada no painel de ferramenta horizontal na parte inferior do editor.

### <a name="currentvisibleverticaltool"></a>CurrentVisibleVerticalTool

> Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade só de leitura que obtém a ferramenta de suplemento visível no momento do ISE do Windows PowerShell que está localizada no painel de ferramenta vertical no lado direito do editor.

### <a name="options"></a>Opções

> Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade só de leitura que obtém as várias opções que pode alterar as definições no ISE do Windows PowerShell.

### <a name="powershelltabs"></a>PowerShellTabs

> Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade só de leitura que obtém a coleção de guias do PowerShell, que estão abertas no ISE do Windows PowerShell. Por predefinição, este objeto contém um separador do PowerShell. No entanto, pode adicionar mais guias do PowerShell para este objeto utilizando scripts ou utilizando os menus no ISE do Windows PowerShell.

## <a name="see-also"></a>Consulte Também

- [Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)