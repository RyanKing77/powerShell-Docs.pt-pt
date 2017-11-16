---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "Como utilizar a conclusão de separador no painel de Script e painel de consola"
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: ba8d0af7e7fc0f1df9f65116be899097b0a97a3c
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a>Como utilizar a conclusão de separador no painel de Script e painel de consola
Conclusão de separador fornece ajuda automática quando ao escrever no painel de Script ou no painel de comandos. Utilize os seguintes passos para tirar partido desta funcionalidade:

## <a name="to-automatically-complete-a-command-entry"></a>Para concluir automaticamente uma entrada de comando
No painel de comandos ou painel de Script, escreva alguns carateres de um comando e, em seguida, prima SEPARADOR para selecionar o texto de conclusão pretendido. Se iniciar vários itens com o texto que introduziu inicialmente, continue premir separador até que o item que pretende que aparece. Conclusão de separador pode ajudar a escrever um nome do cmdlet, nome do parâmetro, nome da variável, o nome de propriedade do objeto ou um caminho de ficheiro.

> [!NOTE]
> No painel de Script, premir SEPARADOR automaticamente concluirá um comando apenas quando estiver a editar ps1,. psd1 ou ficheiros. psm1. Conclusão de separador funciona a qualquer altura ao escrever no painel de comandos.

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a>Para concluir automaticamente uma entrada de parâmetro de cmdlet
No painel de painel de comando ou Script, escreva um cmdlet seguido por um traço e, em seguida, prima SEPARADOR.

Por exemplo, digite `Get-Process -` e, em seguida, prima a tecla SEPARADOR várias vezes para apresentar cada um dos parâmetros do cmdlet por sua vez.

## <a name="see-also"></a>Consulte Também
- [Utilizar o ISE do Windows PowerShell](using-the-windows-powershell-ise.md)
- [Como criar um separador de PowerShell](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)

