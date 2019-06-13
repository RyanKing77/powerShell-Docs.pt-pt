---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Como Utilizar o Painel de Consola no ISE do Windows PowerShell
ms.openlocfilehash: 114be19b86d98d829620a3718649bc3a3256cb07
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030573"
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>Como Utilizar o Painel de Consola no ISE do Windows PowerShell

O painel de consola no Windows PowerShell Integrated Scripting Environment (ISE) funciona exatamente como a janela da consola autónoma do ISE do Windows PowerShell.

Para executar um comando no painel da consola, escreva um comando e, em seguida, prima ENTER. Para introduzir vários comandos que deseja que sejam executadas em seqüência, escreva SHIFT + ENTER entre comandos. Ver [como uso de conclusão de tabulação no painel de Script e o painel de consola](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) para obter ajuda em escrever comandos.

Para parar um comando, na barra de ferramentas, clique em **operação parar**, ou prima CTRL + BREAK. Também pode utilizar CTRL + C para parar um comando, se o contexto é inequívoca. Por exemplo, se algum texto foi selecionado no painel de atual, em seguida, CTRL + C é mapeado para a operação de cópia.

O painel de resultados a partir da v3 do Windows PowerShell, foi combinado com o painel de consola. Isso tem a vantagem de se comportando como a consola autónoma do Windows PowerShell e elimina as diferenças nos procedimentos que foram necessárias quando eles foram separados. Pode:

- Selecione e copie o texto do painel de consola para a área de transferência para colar em qualquer outra janela. Para selecionar o texto, clique e mantenha premido o mouse no painel de saída ao arrastar o mouse sobre o texto que pretende capturar. Também pode utilizar as teclas de seta de cursor enquanto espera **SHIFT** para selecionar o texto. Em seguida, prima CTRL + C ou clique nas **cópia** ícone na barra de ferramentas.

- Cole o texto selecionado numa posição atual do cursor. Clique nas **colar** ícone na barra de ferramentas.

- Limpe todo o texto no painel da consola. Para limpar o painel de consola, pode clicar a **limpar o painel de consola** ícone na barra de ferramentas ou execute o comando **Clear-Host** ou o respetivo alias **cls**.

## <a name="see-also"></a>Veja Também

- [Introdução ao ISE do Windows PowerShell](Introducing-the-Windows-PowerShell-ISE.md)
