---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Atalhos de Teclado do ISE do Windows PowerShell
ms.assetid: 8328b946-0f02-4ef4-ac28-2743a1b4043b
ms.openlocfilehash: 1abae849ce599b586357fd2a8db46c608932bd4e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086838"
---
# <a name="keyboard-shortcuts-for-the-windows-powershell-ise"></a>Atalhos de Teclado do ISE do Windows PowerShell

Utilize os seguintes atalhos de teclado para executar ações no Windows PowerShell® Integrated Scripting Environment (ISE). ISE do Windows PowerShell está disponível como parte do Windows Server e cliente Windows operar sistemas, mas podem também ser instalado em alguns sistemas de operativos mais antigos do Windows como parte do [pacote de download do Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881).

## <a name="keyboard-shortcuts-for-editing-text"></a>Atalhos de teclado para a edição de texto

Pode utilizar os seguintes atalhos de teclado, ao editar o texto.

|Ação|Atalhos de teclado|Utilize|
|----------|----------------------|----------|
|**Obter ajuda**|F1|Painel de script **importantes:** Pode especificar que a ajuda F1 vem da biblioteca do TechNet na web ou transferido ajuda (consulte a ajuda de atualização). Para selecionar, clique em **ferramentas**, **opções**, em seguida, no **definições gerais**separador, definir ou limpar **utilizar conteúdo da ajuda local em vez de conteúdo online.**|
|**cópia**|CTRL + C|Painel, o painel de comando, o painel de resultados do script|
|**Cut**|CTRL + X|Painel de script, o painel de comando|
|**Expandir ou fechar que descreva**|CTRL+M|Painel de script|
|**Encontrar no Script**|CTRL + L|Painel de script|
|**Localizar seguinte no Script**|F3|Painel de script|
|**Localizar anterior no Script**|TECLA SHIFT+F3|Painel de script|
|**Localizar a chave de correspondência**|CTRL +]|Painel de script|
|**Paste**|CTRL + V|Painel de script, o painel de comando|
|**Refazer**|CTRL + Y|Painel de script, o painel de comando|
|**Substituir no Script**|CTRL + H|Painel de script|
|**Guardar**|CTRL + S|Painel de script|
|**Selecionar tudo**|CTRL + T|Painel, o painel de comando, o painel de resultados do script|
|**Mostrar trechos de código**|CTRL + J|Painel de script, o painel de comando|
|**Undo**|CTRL + Z|Painel de script, o painel de comando|

## <a name="keyboard-shortcuts-for-running-scripts"></a>Atalhos de teclado para executar scripts

Pode utilizar os seguintes atalhos de teclado ao executar scripts no painel de Script.

|Ação|Atalho de teclado|
|----------|---------------------|
|**Novidade**|CTRL + N|
|**abrir**|CTRL + O|
|**Executar**|F5|
|**Executar seleção**|F8|
|**Parar a execução**|CTRL + BREAK. CTRL + C pode ser utilizado quando o contexto é inequívoca (quando não houver nenhum texto selecionado).|
|**Separador** (para o próximo script)|CTRL + TAB **observação:** Guia para o próximo script funciona apenas quando tem uma guia única do Windows PowerShell, abrir, ou quando tiver mais do que um separador do PowerShell de Windows abrir, mas o foco está no painel de Script.|
|**Separador** (para o script anterior)|CTRL + SHIFT + TAB **observação:** Guia para o script anterior funciona quando tem apenas um separador do PowerShell de Windows abrir, ou se tiver mais do que um separador do PowerShell de Windows abrir e o foco está no painel de Script.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Atalhos de teclado para personalizar a vista

Pode utilizar os seguintes atalhos de teclado para personalizar a vista no ISE do Windows PowerShell. Podem ser acedidos a partir de todos os painéis no aplicativo.

|Ação|Atalho de teclado|
|----------|---------------------|
|**Vá para o comando (v2) ou a consola (v3 e posterior) painel**|CTRL + D|
|**Aceda ao painel de resultados (apenas v2)**|CTRL + SHIFT + O|
|**Vá para Painel de Script**|CTRL + I|
|**Mostrar painel de Script**|CTRL + R|
|**Ocultar painel de Script**|CTRL + R|
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
> Também pode utilizar os atalhos de teclado concebidos para a consola do Windows PowerShell ao depurar scripts no ISE do Windows PowerShell. Para usar esses atalhos, tem de escreva o atalho no painel do comando e prima ENTER.

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
|**Separador do PowerShell anterior**|CTRL + SHIFT + TAB. Este atalho funciona apenas quando não existem ficheiros abertos de qualquer separador do Windows PowerShell.|
|**Separador de Windows PowerShell seguinte**|CTRL + TAB. Este atalho funciona apenas quando não existem ficheiros abertos de qualquer separador do Windows PowerShell.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Atalhos de teclado para iniciar e sair

Pode utilizar os seguintes atalhos de teclado para iniciar a consola do Windows PowerShell (PowerShell.exe) ou para sair do ISE do Windows PowerShell.

|Ação|Atalho de teclado|
|----------|---------------------|
|**Exit**|ALT+F4|
|**Iniciar PowerShell.exe** (consola do Windows PowerShell)|CTRL + SHIFT + P|

## <a name="see-also"></a>Veja Também

- [PowerShell Magazine: A lista completa de atalhos de teclado do ISE do PowerShell de Windows](https://www.powershellmagazine.com/2013/01/29/the-complete-list-of-powershell-ise-3-0-keyboard-shortcuts/)