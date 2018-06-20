---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Como Utilizar o Preenchimento com a Tecla Tab no Painel de Scripts e no Painel de Consola
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: e1f8146b6113a82fd3d857c98550ec2e459715a4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954930"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a>Como Utilizar o Preenchimento com a Tecla Tab no Painel de Scripts e no Painel de Consola

Conclusão de separador fornece ajuda automática quando ao escrever no painel de Script ou no painel de comandos. Utilize os seguintes passos para tirar partido desta funcionalidade:

## <a name="to-automatically-complete-a-command-entry"></a>Para concluir automaticamente uma entrada de comando

No painel de comandos ou painel de Script, escreva alguns carateres de um comando e, em seguida, prima SEPARADOR para selecionar o texto de conclusão pretendido. Se iniciar vários itens com o texto que introduziu inicialmente, continue premir separador até que o item que pretende que aparece. Conclusão de separador pode ajudar a escrever um nome do cmdlet, nome do parâmetro, nome da variável, o nome de propriedade do objeto ou um caminho de ficheiro.

> [!NOTE]
> No painel de Script, premir SEPARADOR automaticamente concluirá um comando apenas quando estiver a editar ps1,. psd1 ou ficheiros. psm1. Conclusão de separador funciona a qualquer altura ao escrever no painel de comandos.

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a>Para concluir automaticamente uma entrada de parâmetro de cmdlet

No painel de painel de comando ou Script, escreva um cmdlet seguido por um traço e, em seguida, prima SEPARADOR.

Por exemplo, digite `Get-Process -` e, em seguida, prima a tecla SEPARADOR várias vezes para apresentar cada um dos parâmetros do cmdlet por sua vez.

## <a name="see-also"></a>Consulte Também

- [Introdução ao ISE do Windows PowerShell](Introducing-the-Windows-PowerShell-ISE.md)
- [Como criar um separador de PowerShell](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)