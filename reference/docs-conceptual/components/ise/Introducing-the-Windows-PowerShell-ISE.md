---
ms.date: 08/14/2018
keywords: PowerShell, o cmdlet
title: Introdução ao ISE do Windows PowerShell
ms.openlocfilehash: 729c8535dbcfcd2c51070b8beac5d328375f36ae
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685103"
---
# <a name="the-windows-powershell-ise"></a>ISE do Windows PowerShell

O Windows PowerShell Integrated Scripting Environment (ISE) é um aplicativo de host para o Windows PowerShell. No ISE, pode executar comandos e escrita, teste e depurar scripts numa interface de único usuário em gráficos baseados em Windows. O ISE fornece edição com várias linhas, conclusão de tabulação, sintaxe colorida, execução seletiva, ajuda sensível ao contexto e suporte para idiomas da direita para a esquerda. Itens de menu e os atalhos de teclado são mapeados para muitas das mesmas tarefas que faria na consola do Windows PowerShell. Por exemplo, ao depurar um script no ISE, pode clicar numa linha de código no painel de edição para definir um ponto de interrupção.

## <a name="support"></a>Suporte

O ISE foi introduzido pela primeira vez com o Windows PowerShell V2 e foi reformulado com PowerShell V3. O ISE é suportado em todas as versões suportadas do Windows PowerShell até e incluindo V5.1 de PowerShell do Windows. ISE, no entanto, está no modo de manutenção e não existem novas funcionalidades estão provavelmente seja adicionado.
Além disso, não há suporte para o ISE com o PowerShell v6 e muito mais. Os utilizadores que pretendem uma ferramenta gráfica gerir scripts do PowerShell, etc., devem considerar [Visual Studio Code](https://code.visualstudio.com/).

## <a name="key-features"></a>Principais Funcionalidades

Recursos-chave no ISE do Windows PowerShell incluem:

- Edição de várias linhas: Para inserir uma linha em branco abaixo da linha atual no painel de comando, prima SHIFT + ENTER.
- Execução seletiva: Para executar a parte de um script, selecione o texto que pretende executar e, em seguida, clique a **executar Script** botão. Em alternativa, prima F5.
- Ajuda sensível ao contexto: Tipo **Invoke-Item**, e, em seguida, prima F1. O ficheiro de ajuda é aberto o artigo para o **Invoke-Item** cmdlet.

ISE do Windows PowerShell permite-lhe personalizar alguns aspectos de sua aparência. Ele também tem seu próprio script de perfil do Windows PowerShell.

## <a name="to-start-the-windows-powershell-ise"></a>Para iniciar o ISE do Windows PowerShell

Clique em **começar**, selecione **Windows PowerShell**e, em seguida, clique em **ISE do Windows PowerShell**.
Em alternativa, pode escrever `powershell_ise.exe` em qualquer shell de comandos ou na caixa executar.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>Para obter ajuda no ISE do Windows PowerShell

Sobre o **ajudar** menu, clique em **ajuda do Windows PowerShell**. Em alternativa, prima F1. O ficheiro que se abre descreve o ISE do Windows PowerShell e o Windows PowerShell, incluindo todos da ajuda disponíveis a partir do cmdlet Get-Help.
