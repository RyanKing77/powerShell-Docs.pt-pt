---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Hierarquia do Modelo de Objeto ISE
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057728"
---
# <a name="the-ise-object-model-hierarchy"></a>Hierarquia do Modelo de Objeto ISE

Este tópico mostra a hierarquia de objetos que fazem parte do Windows PowerShell Integrated Scripting Environment (ISE).
ISE do Windows PowerShell é incluído no Windows PowerShell 3.0 e no Windows PowerShell 4.0.
Clique num objeto para levá-lo para a documentação de referência para a classe que define o objeto.

## <a name="psise-object"></a>objeto de $psISE

O **$psISE** objeto é a [objeto raiz](The-ObjectModelRoot-Object.md) da hierarquia de objeto ISE do Windows PowerShell.
Localizado no nível superior, disponibiliza os seguintes objetos para processamento de scripts:

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE.CurrentFile](The-ISEFile-Object.md)

O **$psISE.CurrentFile** objeto é uma instância da [ISEFile](The-ISEFile-Object.md) classe.

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)

O **$psISE.CurrentPowerShellTab** objeto é uma instância da [PowerShellTab](The-PowerShellTab-Object.md) classe.

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE.CurrentVisibleHorizontalTool

O **$psISE.CurrentVisibleHorizontalTool** objeto é uma instância da [ISEAddOnTool](The-ISEAddOnTool-Object.md) classe.
Ele representa a ferramenta do suplemento instalado que atualmente é encaixada na borda superior da janela de ISE do Windows PowerShell.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE.CurrentVisibleVerticalTool

O **$psISE.CurrentVisibleHorizontalTool** objeto é uma instância da [ISEAddOnTool](The-ISEAddOnTool-Object.md) classe.
Ele representa a ferramenta do suplemento instalado que atualmente é encaixada na borda direita da janela de ISE do Windows PowerShell.

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE.Options](The-ISEOptions-Object.md)

O **$psISE.Options** objeto é uma instância da [ISEOptions](The-ISEOptions-Object.md) classe.
Objeto ISEOptions representa várias definições para o Windows PowerShell ISE.
É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEOptions.

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)

O **$psISE.PowerShellTabs** objeto é uma instância da [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) classe.
É uma coleção de todos os atualmente abertas PowerShell guias que representam a ambientes de execução no computador local ou em computadores remotos ligados do Windows PowerShell disponíveis.
Cada membro da coleção é uma instância do [PowerShellTab](The-PowerShellTab-Object.md) classe.

## <a name="see-also"></a>Veja Também

- [Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)