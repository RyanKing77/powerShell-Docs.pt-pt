---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Acessibilidade no ISE do Windows PowerShell
ms.assetid: a078f9d1-dd6b-4323-b16d-0622cd993aa8
ms.openlocfilehash: 78a001dbe43a0b005d10a817e05e4cc7a72f5bd0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058459"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Acessibilidade no ISE do Windows PowerShell

Este tópico descreve as funcionalidades de acessibilidade do Windows PowerShell Integrated Scripting Environment (ISE) que poderão ser úteis.

* [Como alterar o tamanho e a localização da consola do e painéis de Script](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
* [Atalhos de teclado para a edição de texto](#keyboard-shortcuts-for-editing-text)
* [Atalhos de teclado para executar scripts](#keyboard-shortcuts-for-running-scripts)
* [Atalhos de teclado para personalizar a vista](#keyboard-shortcuts-for-customizing-the-view)
* [Atalhos de teclado para depuração de scripts](#keyboard-shortcuts-for-debugging-scripts)
* [Atalhos de teclado do Windows PowerShell separadores](#keyboard-shortcuts-for-windows-powershell-tabs)
* [Atalhos de teclado para iniciar e sair](#keyboard-shortcuts-for-starting-and-exiting)

A Microsoft está empenhada em tornar mais fácil a utilização dos seus produtos e serviços para todos os utilizadores. Os tópicos seguintes fornecem informações sobre as funcionalidades, produtos e serviços que tornam o Windows PowerShell ISE mais acessível para pessoas portadoras de deficiência.

ISE do Windows PowerShell oferece suporte ao modo de alto contraste. Para o deficiente, estão disponíveis através dos cmdlets para gerir pontos de interrupção, tais como informações de ponto de interrupção [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) e [conjunto PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420). Para mais informações, consulte "Como gerir pontos de interrupção" na [como depurar Scripts no ISE do Windows PowerShell](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md). Além das funcionalidades de acessibilidade e utilitários no Microsoft Windows, as seguintes funcionalidades tornam o ISE do Windows PowerShell mais acessível para pessoas com incapacidades:

- Atalhos de teclado

- Tabela de cores da sintaxe e a capacidade de modificar a várias outras definições de cor a utilizar o [$psISE.Options](https://technet.microsoft.com/library/75e2a76f-f3d1-490b-ad5d-e3829946aabb) objeto de scripting.

- Alterações de tamanho do texto

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>Como alterar o tamanho e a localização da consola do e painéis de Script

Pode utilizar os seguintes passos para alterar o tamanho e localização do painel de consola e o painel de scripts. Quando abrir novamente o ISE do Windows PowerShell, as alterações de tamanho e localização que efetuou serão mantidas.

### <a name="to-resize-the-script-pane-and-console-pane"></a>Para redimensionar o painel de Script e o painel de consola

1. Colocar em pausa o ponteiro sobre a linha de divisão entre o painel de Script e o painel de consola.

2. Quando o ponteiro do mouse é alterado para uma seta de duas-chegar, arraste o limite para alterar o tamanho do painel.

### <a name="to-move-the-script-pane-and-console-pane"></a>Para mover o painel de Script e o painel de consola

Efetue uma das seguintes opções:

- Para mover o painel de Script acima do painel de consola, prima **CTRL + 1** ou, na barra de ferramentas, clique nas **Mostrar parte superior do Script painel** ícone, ou no **vista** menu, clique em **Mostrar Parte superior do painel de script**.

- Para mover o painel de scripts para a direita do painel de consola, prima **CTRL + 2** ou, na barra de ferramentas, clique nas **Mostrar direita do painel de Script** ícone, ou no **vista** menu, clique em **Mostrar painel de Script certo**.

- Para maximizar o painel de scripts, prima **CTRL + 3** ou, na barra de ferramentas, clique nas **Mostrar maximizada do painel de Script** ícone, ou no **vista** menu, clique em **Mostrar o Script Painel maximizado**.

- Para maximizar o painel de consola e ocultar o painel de Script, na extremidade direita da linha de guias, clique nas **ocultar painel de Script** ícone, na **vista** menu, clique para desmarcar o **Mostrar painel de Script** opção de menu.

- Para mostrar o painel de Script, quando o painel de consola é maximizado, na extremidade direita da linha de guias, clique nas **Mostrar painel de Script** ícone, ou no **vista** menu, clique para selecionar o **Mostrar o Script Painel** opção de menu.

## <a name="keyboard-shortcuts-for-editing-text"></a>Atalhos de teclado para a edição de texto

Pode utilizar os seguintes atalhos de teclado, ao editar o texto.

|Ação|Atalhos de teclado|Utilize|
|----------|----------------------|----------|
|**cópia**|CTRL + C|Painel de script, o painel de consola|
|**Cut**|CTRL + X|Painel de script, o painel de consola|
|**Encontrar no Script**|CTRL + L|Painel de script|
|**Localizar seguinte no Script**|F3|Painel de script|
|**Localizar anterior no Script**|TECLA SHIFT+F3|Painel de script|
|**Paste**|CTRL + V|Painel de script, o painel de consola|
|**Refazer**|CTRL + Y|Painel de script, o painel de consola|
|**Substituir no Script**|CTRL + H|Painel de script|
|**Guardar**|CTRL + S|Painel de script|
|**Selecionar tudo**|CTRL + T|Painel de script, o painel de consola|
|**Undo**|CTRL + Z|Painel de script, o painel de consola|

## <a name="keyboard-shortcuts-for-running-scripts"></a>Atalhos de teclado para executar scripts

Pode utilizar os seguintes atalhos de teclado ao executar scripts no painel de Script.

|Ação|Atalho de teclado|
|----------|---------------------|
|**Novidade**|CTRL + N|
|**abrir**|CTRL + O|
|**Executar**|F5|
|**Executar seleção**|F8|
|**Parar a execução**|CTRL + BREAK. CTRL + C pode ser utilizado quando o contexto é inequívoca (quando não houver nenhum texto selecionado).|
|**Separador** (para o próximo script)|CTRL + TAB **observação:** Guia para o próximo script funciona apenas quando tiver uma única marca de PowerShell abrir, ou quando tiver mais do que um separador do PowerShell abrir, mas o foco está no painel de Script.|
|**Separador** (para o script anterior)|CTRL + SHIFT + TAB **observação:** Guia para o script anterior funciona quando tem apenas um separador do PowerShell abrir, ou se tiver mais do que um separador do PowerShell abrir e o foco está no painel de Script.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Atalhos de teclado para personalizar a vista

Pode utilizar os seguintes atalhos de teclado para personalizar a vista no ISE do Windows PowerShell. Podem ser acedidos a partir de todos os painéis no aplicativo.

|Ação|Atalho de teclado|
|----------|---------------------|
|**Vá para Painel de consola**|CTRL + D|
|**Vá para Painel de Script**|CTRL + I|
|**Mostrar painel de Script**|CTRL + R|
|**Ocultar painel de Script**|CTRL + R|
||
|**Suba o painel de Script**|CTRL + 1|
|**Mover o painel de Script para a direita**|CTRL + 2|
|**Maximizar painel de Script**|CTRL + 3|
|**Ampliar**|CTRL + SINAL DE ADIÇÃO|
|**Reduzir**|CTRL + SINAL DE SUBTRAÇÃO|

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Atalhos de teclado para depuração de scripts

Pode utilizar os seguintes atalhos de teclado ao depurar scripts.

|Ação|Atalho de teclado|Utilize|
|----------|---------------------|----------|
|**Execução/continuar**|F5|Painel de script, quando um script de depuração|
|**Avance para**|F11|Painel de script, quando um script de depuração|
|**Step Over**|F10|Painel de script, quando um script de depuração|
|**Krokovat s Vystoupením**|SHIFT + F11|Painel de script, quando um script de depuração|
|**Pilha de chamadas de apresentação**|CTRL + SHIFT + D|Painel de script, quando um script de depuração|
|**Pontos de interrupção de lista**|CTRL + SHIFT + L|Painel de script, quando um script de depuração|
|**Ativar/desativar ponto de interrupção**|F9|Painel de script, quando um script de depuração|
|**Remover todos os pontos de interrupção**|CTRL + SHIFT + F9|Painel de script, quando um script de depuração|
|**Parar o depurador**|SHIFT + F5|Painel de script, quando um script de depuração|

> [!NOTE]
>
> Também pode utilizar os atalhos de teclado concebidos para a consola do Windows PowerShell ao depurar scripts no ISE do Windows PowerShell. Para usar esses atalhos, tem de escrever o atalho no painel da consola e prima ENTER.

|Ação|Atalho de teclado|Utilize|
|----------|---------------------|----------|
|**Continuar**|C|Painel de consola, quando um script de depuração|
|**Avance para**|S|Painel de consola, quando um script de depuração|
|**Step Over**|V|Painel de consola, quando um script de depuração|
|**Krokovat s Vystoupením**|O|Painel de consola, quando um script de depuração|
|**Repetir último comando** (para o passo em ou Step Over)|INTRODUZA|Painel de consola, quando um script de depuração|
|**Pilha de chamadas de apresentação**|K|Painel de consola, quando um script de depuração|
|**Parar a depuração**|PERGUNTAS E|Painel de consola, quando um script de depuração|
|**Lista o Script**|L|Painel de consola, quando um script de depuração|
|**Apresentar consola comandos de depuração**|H ou?|Painel de consola, quando um script de depuração|

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Atalhos de teclado do Windows PowerShell separadores

Pode utilizar os seguintes atalhos de teclado ao utilizar os separadores de Windows PowerShell.

|Ação|Atalho de teclado|
|----------|---------------------|
|**Feche o separador do PowerShell**|CTRL + W|
|**Novo separador do PowerShell**|CTRL + T|
|**Separador do PowerShell anterior**|CTRL + SHIFT + TAB. Este atalho funciona apenas quando não existem ficheiros abertos em qualquer separador do PowerShell.|
|**Separador de Windows PowerShell seguinte**|CTRL + TAB. Este atalho funciona apenas quando não existem ficheiros abertos em qualquer separador do PowerShell.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Atalhos de teclado para iniciar e sair

Pode utilizar os seguintes atalhos de teclado para iniciar a consola do Windows PowerShell (PowerShell.exe) ou para sair do ISE do Windows PowerShell.

|Ação|Atalho de teclado|
|----------|---------------------|
|**Exit**|ALT+F4|
|**Iniciar PowerShell.exe** (consola do Windows PowerShell)|CTRL + SHIFT + P|

## <a name="see-also"></a>Veja Também

[Introdução ao ISE do Windows PowerShell](Introducing-the-Windows-PowerShell-ISE.md)