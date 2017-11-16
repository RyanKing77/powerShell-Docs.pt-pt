---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: A hierarquia de modelo de objeto ISE
ms.openlocfilehash: 2df6d40f39dbe14bd3f46a6400cde4a6e91052ef
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="the-ise-object-model-hierarchy"></a>A hierarquia de modelo de objeto ISE
Este tópico mostra a hierarquia de objetos que fazem parte do Windows PowerShell Integrated Scripting Environment (ISE). ISE do Windows PowerShell está incluído no Windows PowerShell 3.0 e no Windows PowerShell 4.0. Clique num objeto para leva-o para a documentação de referência para a classe que define o objeto.

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
É uma coleção de todos os atualmente abertos PowerShell separadores que representam o Windows PowerShell disponíveis execute ambientes no computador local ou em computadores remotos ligados. Cada membro da coleção é uma instância do [PowerShellTab](The-PowerShellTab-Object.md) classe.

## <a name="see-also"></a>Consulte Também
- [O ISE do Windows PowerShell modelo de objeto de Scripting](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Referência de modelo de objeto do Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md)
