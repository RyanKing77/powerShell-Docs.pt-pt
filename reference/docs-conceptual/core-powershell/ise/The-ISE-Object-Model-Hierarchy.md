---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Hierarquia do Modelo de Objeto ISE
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950697"
---
# <a name="the-ise-object-model-hierarchy"></a>Hierarquia do Modelo de Objeto ISE

Este tópico mostra a hierarquia de objetos que fazem parte do Windows PowerShell Integrated Scripting Environment (ISE).
ISE do Windows PowerShell está incluído no Windows PowerShell 3.0 e no Windows PowerShell 4.0.
Clique num objeto para leva-o para a documentação de referência para a classe que define o objeto.

## <a name="psise-object"></a>objeto de $psISE

O **$psISE** objeto é o [objecto raiz](The-ObjectModelRoot-Object.md) da hierarquia de objeto de ISE do Windows PowerShell.
Localizada no nível superior, disponibiliza os seguintes objetos para processamento de scripts:

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE.CurrentFile](The-ISEFile-Object.md)

O **$psISE.CurrentFile** objeto é uma instância do [ISEFile](The-ISEFile-Object.md) classe.

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)

O **$psISE.CurrentPowerShellTab** objeto é uma instância do [PowerShellTab](The-PowerShellTab-Object.md) classe.

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE.CurrentVisibleHorizontalTool

O **$psISE.CurrentVisibleHorizontalTool** objeto é uma instância do [ISEAddOnTool](The-ISEAddOnTool-Object.md) classe.
Representa a ferramenta de suplemento instalado atualmente estiver ancorada para o limite superior da janela ISE do Windows PowerShell.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE.CurrentVisibleVerticalTool

O **$psISE.CurrentVisibleHorizontalTool** objeto é uma instância do [ISEAddOnTool](The-ISEAddOnTool-Object.md) classe.
Representa a ferramenta de suplemento instalado atualmente estiver ancorada para o limite direito da janela ISE do Windows PowerShell.

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE.Options](The-ISEOptions-Object.md)

O **$psISE.Options** objeto é uma instância do [ISEOptions](The-ISEOptions-Object.md) classe.
O objeto de ISEOptions representa várias definições de ISE do Windows PowerShell.
É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEOptions.

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)

O **$psISE.PowerShellTabs** objeto é uma instância do [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) classe.
É uma coleção de todos os atualmente abertos PowerShell separadores que representam o Windows PowerShell disponíveis execute ambientes no computador local ou em computadores remotos ligados.
Cada membro da coleção é uma instância do [PowerShellTab](The-PowerShellTab-Object.md) classe.

## <a name="see-also"></a>Consulte Também

- [Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)