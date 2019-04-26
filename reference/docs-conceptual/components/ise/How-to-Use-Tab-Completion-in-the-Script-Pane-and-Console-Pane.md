---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Como Utilizar o Preenchimento com a Tecla Tab no Painel de Scripts e no Painel de Consola
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: 24a3f00987ff5ca4bf82d1a3206857ec3c4b3f09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086889"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a>Como Utilizar o Preenchimento com a Tecla Tab no Painel de Scripts e no Painel de Consola

Conclusão de tabulação fornece ajuda automática ao escrever no painel de Script ou no painel de comando. Utilize os seguintes passos para tirar partido desta funcionalidade:

## <a name="to-automatically-complete-a-command-entry"></a>Para concluir automaticamente uma entrada de comando

No painel de comando ou painel de Script, escreva alguns caracteres de um comando e, em seguida, pressione TAB para selecionar o texto de conclusão pretendido. Se começam com o texto digitado inicialmente a vários itens, continue pressionada a tecla Tab até que o item que pretende que seja apresentado. Conclusão de tabulação pode ajudar com a escrever um nome de cmdlet, nome do parâmetro, nome da variável, o nome de propriedade do objeto ou um caminho de ficheiro.

> [!NOTE]
> No painel de Script, pressionada a tecla TAB será automaticamente concluído de um comando apenas quando estiver a editar. ps1,. psd1 ou ficheiros. psm1. Conclusão de tabulação funciona sempre quando ao escrever no painel de comando.

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a>Para concluir automaticamente uma entrada de parâmetro de cmdlet

No painel de painel de comando ou Script, digite um cmdlet seguido por um traço e, em seguida, pressione TAB.

Por exemplo, digite `Get-Process -` e, em seguida, pressione TAB várias vezes para exibir cada um dos parâmetros do cmdlet por sua vez.

## <a name="see-also"></a>Veja Também

- [Introdução ao ISE do Windows PowerShell](Introducing-the-Windows-PowerShell-ISE.md)
- [Como criar um separador do PowerShell](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)
