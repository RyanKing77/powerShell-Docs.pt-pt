---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "Apêndice 2 a criar um atalho personalizados do PowerShell"
ms.assetid: 5d4fd421-5d43-4ec7-86fd-acfe887b066e
ms.openlocfilehash: d5e554f6f062fc5bf1beddd2aca1acf0b93d2133
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a>Apêndice 2 - criar um atalho personalizados do PowerShell
O procedimento seguinte descreve como criar um atalho para o Windows PowerShell que tem várias opções convenientes personalizadas.

1. Crie um atalho que aponta para o Powershell.exe.

2. Faça duplo clique no atalho e, em seguida, clique em **propriedades**.

3. Clique na **opções** separador.

4. No **editar opções** secção, selecione o **QuickEdit** caixa de verificação.

    Esta definição permite-lhe selecionar o texto na janela da consola do Windows PowerShell, arrastando botão esquerdo do rato e permite-lhe copiar texto para a área de transferência, premindo ENTER, ou clicando com o rato.

5. No **editar opções** secção, selecione o **inserir modo** caixa de verificação. Esta definição permite-lhe o botão direito do rato na janela da consola automaticamente colar o texto da área de transferência.

6. No **histórico de comando** secção, escreva ou selecione um número entre 1 e 999 no **tamanho da memória intermédia** caixa. Isto define o número de comandos escritos que serão mantidos na memória intermédia de consola.

7. No **histórico de comando** secção, selecione o **eliminar duplicados antigo** caixa de verificação para eliminar repetidos comandos a partir da memória intermédia de consola.

8. Clique na **esquema** separador.

9. No **memória intermédia de ecrã** secção, escreva um número entre 1 e 9999 no **altura** caixa. A altura representa o número de linhas de saída que são colocado na memória intermédia. Este é o número máximo de linhas retidos para visualização quando percorra a janela de consola. Se este número é inferior à altura mostrada no **tamanho da janela** secção, a altura do tamanho de janela automaticamente será reduzida para o mesmo valor.

10. No **tamanho da janela** secção, escreva um número entre 1 e 9999 para a largura. Representa o número de carateres que são apresentados na janela da consola. A largura predefinida é 80 e saída do Windows PowerShell formatação foi concebida para esta largura.

11. Se pretende colocar a consola num determinado ponto no ambiente de trabalho quando é aberta, desmarque a **permitem a janela de posição de sistema** caixa de verificação a **posição da janela** secção e, em seguida, altere os valores existentes no  **À esquerda** e **superior** caixas **posição da janela** secção.

12. Clique em **OK**.

