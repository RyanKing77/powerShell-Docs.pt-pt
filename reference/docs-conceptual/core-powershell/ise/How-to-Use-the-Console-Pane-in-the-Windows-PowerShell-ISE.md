---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Como Utilizar o Painel de Consola no ISE do Windows PowerShell
ms.assetid: 44d67705-87c7-4a69-a53e-6471fdebb757
ms.openlocfilehash: 5bbbdd3b1f0324ff1a4f2298459f58640c4dc9a6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950792"
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>Como Utilizar o Painel de Consola no ISE do Windows PowerShell

O painel de consola no Windows PowerShell Integrated Scripting Environment (ISE) funciona exatamente como a janela de consola do ISE do Windows PowerShell autónoma.

Para executar um comando no painel de consola, escreva um comando e, em seguida, prima ENTER. Para introduzir vários comandos que pretende executar na sequência, escreva SHIFT + ENTER entre comandos. Consulte [como conclusão de separador de utilização no painel de Script e painel de consola](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) para obter ajuda na digitando comandos.

Para parar um comando, na barra de ferramentas, clique em **operação parar**, ou prima CTRL + BREAK. Também pode utilizar CTRL + C para parar um comando, se o contexto é inequívoca. Por exemplo, se algum texto tiver sido selecionado no painel de atual, em seguida, CTRL + C mapeia para a operação de cópia.

O painel de resultados a partir do Windows PowerShell v3, foi combinado com o painel de consola. Isto apresenta as vantagens de comportam como a consola autónoma do Windows PowerShell e elimina as diferenças nos procedimentos que eram necessários quando se encontravam separados. Pode:

- Selecione e copie o texto do painel de consola para a área de transferência para colar qualquer outra janela. Para selecionar o texto, clique e mantenha premido o rato no painel de resultados ao arrastar o rato sobre o texto que pretende capturar. Também pode utilizar as teclas de seta do cursor ao aprendem facilmente **SHIFT** para selecionar o texto. Em seguida, prima CTRL + C ou clique em de **cópia** ícone na barra de ferramentas.

- Cole o texto seleccionado uma posição atual do cursor. Clique em de **colar** ícone na barra de ferramentas.

- Limpe todo o texto no painel de consola. Para limpar o painel de consola, pode clicar no **limpar o painel de consola** ícone na barra de ferramentas ou execute o comando **limpar anfitrião** ou o alias, **cls**.

## <a name="see-also"></a>Consulte Também

- [Introdução ao ISE do Windows PowerShell](Introducing-the-Windows-PowerShell-ISE.md)