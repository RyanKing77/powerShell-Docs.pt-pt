---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Acessibilidade no ISE do Windows PowerShell
ms.assetid: a078f9d1-dd6b-4323-b16d-0622cd993aa8
ms.openlocfilehash: 505ec3aca84b5ad0b9d58a1ec84d80e3aa86db7a
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/29/2017
---
# <a name="accessibility-in-windows-powershell-ise"></a>Acessibilidade no ISE do Windows PowerShell
Este tópico descreve as funcionalidades de acessibilidade do Windows PowerShell Integrated Scripting Environment (ISE) que poderão ser úteis.

* [Como alterar o tamanho e a localização da consola e painéis de Script](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
* [Atalhos de teclado para edição de texto](#keyboard-shortcuts-for-editing-text)
* [Atalhos de teclado para executar scripts](#keyboard-shortcuts-for-running-scripts)
* [Atalhos de teclado para personalizar a vista](#keyboard-shortcuts-for-customizing-the-view)
* [Atalhos de teclado para depuração de scripts](#keyboard-shortcuts-for-debugging-scripts)
* [Atalhos de teclado para separadores do Windows PowerShell](#keyboard-shortcuts-for-windows-powershell-tabs)
* [Atalhos de teclado para iniciar e sair](#keyboard-shortcuts-for-starting-and-exiting)

A Microsoft está empenhada em tornar mais fácil a utilização dos seus produtos e serviços para todos os utilizadores. Os tópicos seguintes fornecem informações sobre as funcionalidades, produtos e serviços que tornam o ISE do Windows PowerShell mais acessível para pessoas com incapacidades.

ISE do Windows PowerShell suporta o modo de alto contraste. Para visualmente debilitada, estão disponíveis através dos cmdlets para gerir pontos de interrupção, tais como informações de ponto de interrupção [Get-PSBreakpoint](https://technet.microsoft.com/en-us/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) e [conjunto PSBreakpoint](https://technet.microsoft.com/en-us/library/6afd5d2c-a285-4796-8607-3cbf49471420). Para mais informações, consulte 'Como gerir pontos de interrupção' no [como depurar Scripts no ISE do Windows PowerShell](../core-powershell/ise/How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md). Além das funcionalidades de acessibilidade e utilitários no Microsoft Windows, as seguintes funcionalidades tornam o ISE do Windows PowerShell mais acessível para pessoas com incapacidades:

- Atalhos de teclado

- Tabela Coloring sintaxe e a capacidade de modificar várias outras definições de cor a utilizar o [$psISE.Options](https://technet.microsoft.com/en-us/library/75e2a76f-f3d1-490b-ad5d-e3829946aabb) objeto de scripting.

- Alteração do tamanho de texto

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>Como alterar o tamanho e a localização da consola e painéis de Script
Pode utilizar os seguintes passos para alterar o tamanho e localização do painel de consola e o painel de Script. Quando abrir novamente o ISE do Windows PowerShell, os tamanho e localização alterações que serão mantidas.

### <a name="to-resize-the-script-pane-and-console-pane"></a>Redimensionar o painel de Script e o painel de consola

1. Colocar em pausa o ponteiro sobre a linha de divisão entre o painel de Script e o painel de consola.

2. Quando o ponteiro do rato muda para uma seta headed de dois, arraste o limite para alterar o tamanho do painel.

### <a name="to-move-the-script-pane-and-console-pane"></a>Para mover o painel de Script e o painel de consola
Efetue uma das seguintes opções:

- Para mover o painel de Script acima do painel de consola, prima **CTRL + 1** ou, na barra de ferramentas, clique em de **Mostrar parte superior do Script painel** ícone, ou no **vista** menu, clique em **Mostrar Parte superior do painel de script**.

- Para mover o painel de Script à direita do painel de consola, prima **CTRL + 2** ou, na barra de ferramentas, clique em de **Mostrar direita do painel de Script** ícone, ou no **vista** menu, clique em **Mostrar o painel de Script direita**.

- Para maximizar o painel de Script, prima **CTRL + 3** ou, na barra de ferramentas, clique em de **Mostrar maximizado do painel de Script** ícone, ou no **vista** menu, clique em **Mostrar Script Painel maximizado**.

- Para maximizar o painel de consola e ocultar o painel de Script, na extremidade extremidade direita da linha de separadores, clique em de **ocultar o painel de Script** ícone, no **vista** menu, clique para desmarcar o **Mostrar painel de Script** opção do menu.

- Para apresentar o painel de Script ao painel de consola é maximizado, na extremidade extremidade direita da linha de separadores, clique em de **Mostrar painel de Script** ícone, ou no **vista** menu, clique para selecionar o **Mostrar Script Painel** opção do menu.

## <a name="keyboard-shortcuts-for-editing-text"></a>Atalhos de teclado para edição de texto
Pode utilizar os seguintes atalhos de teclado ao editar o texto.

|Ação|Atalhos de teclado|Utilize|
|----------|----------------------|----------|
|**Copiar**|CTRL + C|Painel de script, o painel de consola|
|**Cortar**|CTRL + X|Painel de script, o painel de consola|
|**Localizar o script**|CTRL + L|Painel de script|
|**Localizar o seguinte script**|F3|Painel de script|
|**Localizar anterior no Script**|SHIFT + F3|Painel de script|
|**Colar**|CTRL + V|Painel de script, o painel de consola|
|**Ação de Refazer**|CTRL + Y|Painel de script, o painel de consola|
|**Substituir o script**|CTRL + H|Painel de script|
|**Guardar**|CTRL+S|Painel de script|
|**Selecionar tudo**|CTRL + T|Painel de script, o painel de consola|
|**Anular**|CTRL + Z|Painel de script, o painel de consola|

## <a name="keyboard-shortcuts-for-running-scripts"></a>Atalhos de teclado para executar scripts
Pode utilizar os seguintes atalhos de teclado quando executar scripts no painel de Script.

|Ação|Atalho de teclado|
|----------|---------------------|
|**Novo**|CTRL + N|
|**Abrir**|CTRL + O|
|**Executar**|F5|
|**Executar seleção**|F8|
|**Parar a execução**|CTRL + BREAK. CTRL + C podem ser utilizado quando o contexto é inequívoca (quando não existe nenhum texto selecionado).|
|**Separador** (para o script seguinte)|CTRL + TAB **Nota:** separador para o script seguinte funciona apenas quando tiver um separador de PowerShell único abrir, ou quando tem mais do que um separador de PowerShell abrir, mas centra-se no painel de Script.|
|**Separador** (para o script anterior)|CTRL + SHIFT + TAB **Nota:** separador ao script anterior funciona quando tem apenas uma abertura de separador do PowerShell ou se tiver mais do que um separador de PowerShell abrir e centra-se no painel de Script.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Atalhos de teclado para personalizar a vista
Pode utilizar os seguintes atalhos de teclado para personalizar a vista no ISE do Windows PowerShell. Que estejam acessíveis a partir de todos os painéis na aplicação.

|Ação|Atalho de teclado|
|----------|---------------------|
|**Aceda ao painel de consola**|CTRL + D|
|**Aceda ao painel de Script**|CTRL + I|
|**Mostrar o painel de Script**|CTRL + R|
|**Ocultar o painel de Script**|CTRL + R|
||
|**Painel de Script mover para cima**|CTRL + 1|
|**Mover o Script painel à direita**|CTRL + 2|
|**Maximizar o painel de Script**|CTRL + 3|
|**Ampliar**|CTRL + SINAL DE ADIÇÃO|
|**Reduzir**|CTRL + SINAL DE SUBTRAÇÃO|

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Atalhos de teclado para depuração de scripts
Pode utilizar os seguintes atalhos de teclado quando depurar scripts.

|Ação|Atalho de teclado|Utilize|
|----------|---------------------|----------|
|**Executar/continuar**|F5|Painel de script, quando um script de depuração|
|**Avance para**|F11|Painel de script, quando um script de depuração|
|**Passo ao longo do**|F10|Painel de script, quando um script de depuração|
|**Passo**|SHIFT + F11|Painel de script, quando um script de depuração|
|**Pilha de chamadas de apresentação**|CTRL + SHIFT + D|Painel de script, quando um script de depuração|
|**Pontos de interrupção de lista**|CTRL + SHIFT + L|Painel de script, quando um script de depuração|
|**Ativar/desativar ponto de interrupção**|F9|Painel de script, quando um script de depuração|
|**Remover todos os pontos de interrupção**|CTRL + SHIFT + F9|Painel de script, quando um script de depuração|
|**Parar o depurador**|SHIFT + F5|Painel de script, quando um script de depuração|

> ![Tenha em atenção](../core-powershell/web-access/images/Note.jpeg)**nota**
>
> Também pode utilizar os atalhos de teclado concebidos para a consola do Windows PowerShell quando depurar scripts no ISE do Windows PowerShell. Para utilizar estes atalhos, tem de escrever o atalho no painel de consola e prima ENTER.

|Ação|Atalho de teclado|Utilize|
|----------|---------------------|----------|
|**Continuar**|C|Painel de consola, quando um script de depuração|
|**Avance para**|S|Painel de consola, quando um script de depuração|
|**Passo ao longo do**|V|Painel de consola, quando um script de depuração|
|**Passo**|O|Painel de consola, quando um script de depuração|
|**Repita o último comando** (para o passo em ou passo ao longo)|ENTER|Painel de consola, quando um script de depuração|
|**Pilha de chamadas de apresentação**|K|Painel de consola, quando um script de depuração|
|**Pare a depuração**|PERGUNTAS E|Painel de consola, quando um script de depuração|
|**Lista o Script**|L|Painel de consola, quando um script de depuração|
|**Apresentar consola a depuração de comandos**|H ou?|Painel de consola, quando um script de depuração|

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Atalhos de teclado para separadores do Windows PowerShell
Pode utilizar os seguintes atalhos de teclado ao utilizar os separadores de Windows PowerShell.

|Ação|Atalho de teclado|
|----------|---------------------|
|**Fechar o separador de PowerShell**|CTRL + W|
|**Novo separador do PowerShell**|CTRL + T|
|**Separador anterior do PowerShell**|CTRL + SHIFT + TAB. Este atalho funciona apenas quando não existem ficheiros abertos em qualquer separador do PowerShell.|
|**Separador que se segue do Windows PowerShell**|CTRL + TAB. Este atalho funciona apenas quando não existem ficheiros abertos em qualquer separador do PowerShell.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Atalhos de teclado para iniciar e sair
Pode utilizar os seguintes atalhos de teclado para iniciar a consola do Windows PowerShell (PowerShell.exe) ou para sair do ISE do Windows PowerShell.

|Ação|Atalho de teclado|
|----------|---------------------|
|**Saída**|ALT+F4|
|**Iniciar o PowerShell.exe** (consola do Windows PowerShell)|CTRL + SHIFT + P|

## <a name="see-also"></a>Consulte Também
- [Utilizar o ISE do Windows PowerShell](../core-powershell/ise/Using-the-Windows-PowerShell-ISE.md)

