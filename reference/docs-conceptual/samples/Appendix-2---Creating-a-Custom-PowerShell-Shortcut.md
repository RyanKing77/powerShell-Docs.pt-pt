---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Apêndice 2 – Criar um Atalho Personalizado para o PowerShell
ms.assetid: 5d4fd421-5d43-4ec7-86fd-acfe887b066e
ms.openlocfilehash: e8081b7a64d313c8ef4bbccf95f250445dd68ad9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405537"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a>Apêndice 2 – criar um atalho para o PowerShell personalizado

O procedimento seguinte descreve como criar um atalho para o Windows PowerShell que tem várias opções convenientes personalizadas.

1. Crie um atalho que aponta para Powershell.exe.

2. Com o botão direito no atalho e, em seguida, clique em **propriedades**.

3. Clique na **opções** separador.

4. Na **editar opções** secção, selecione a **QuickEdit** caixa de verificação.

    Esta definição permite-lhe selecionar o texto na janela de consola do Windows PowerShell ao arrastar o botão esquerdo do mouse e permite-lhe copiar texto para a área de transferência, premindo ENTER ou clicando com o mouse.

5. Na **editar opções** secção, selecione a **inserir modo** caixa de verificação. Esta definição permite-lhe com o botão direito na janela da consola automaticamente colar texto da área de transferência.

6. Na **histórico de comandos** secção, escreva ou selecione um número entre 1 e 999 no **tamanho da memória intermédia** caixa. Isso define o número de comandos escritos que serão mantidos na memória intermédia de consola.

7. Na **histórico de comandos** secção, selecione a **descartar duplica antigo** caixa de verificação para eliminar repetidos de comandos do buffer de consola.

8. Clique na **esquema** separador.

9. Na **memória intermédia ecrã** secção, escreva um número entre 1 e 9999 no **altura** caixa. A altura representa o número de linhas de saída que são colocados em memória intermédia. Este é o número máximo de linhas mantido para ver quando rola a janela da consola. Se este número é menor do que a altura mostrada a **tamanho da janela** secção, automaticamente diminui a altura do tamanho de janela para o mesmo valor.

10. Na **tamanho da janela** secção, escreva um número entre 1 e 9999 para a largura. Isso representa o número de carateres que são apresentados na janela da consola. A largura predefinida é 80 e a formatação de saída do Windows PowerShell foi concebida para esta largura.

11. Se pretende colocar o console num momento específico no ambiente de trabalho quando for aberta, desmarque a **permitir que a janela de posição de sistema** caixa de verificação a **posição da janela** secção e, em seguida, altere os valores no  **À esquerda** e **superior** caixas no **posição da janela** secção.

12. Clique em **OK**.