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
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a><span data-ttu-id="770a9-103">Como utilizar a conclusão de separador no painel de Script e painel de consola</span><span class="sxs-lookup"><span data-stu-id="770a9-103">How to Use Tab Completion in the Script Pane and Console Pane</span></span>
<span data-ttu-id="770a9-104">Conclusão de separador fornece ajuda automática quando ao escrever no painel de Script ou no painel de comandos.</span><span class="sxs-lookup"><span data-stu-id="770a9-104">Tab completion provides automatic help when you are typing in the Script Pane or in the Command Pane.</span></span> <span data-ttu-id="770a9-105">Utilize os seguintes passos para tirar partido desta funcionalidade:</span><span class="sxs-lookup"><span data-stu-id="770a9-105">Use the following steps to take advantage of this feature:</span></span>

## <a name="to-automatically-complete-a-command-entry"></a><span data-ttu-id="770a9-106">Para concluir automaticamente uma entrada de comando</span><span class="sxs-lookup"><span data-stu-id="770a9-106">To automatically complete a command entry</span></span>
<span data-ttu-id="770a9-107">No painel de comandos ou painel de Script, escreva alguns carateres de um comando e, em seguida, prima SEPARADOR para selecionar o texto de conclusão pretendido.</span><span class="sxs-lookup"><span data-stu-id="770a9-107">In the Command Pane or Script Pane, type a few characters of a command and then press TAB to select the desired completion text.</span></span> <span data-ttu-id="770a9-108">Se iniciar vários itens com o texto que introduziu inicialmente, continue premir separador até que o item que pretende que aparece.</span><span class="sxs-lookup"><span data-stu-id="770a9-108">If multiple items begin with the text that you initially typed, then continue pressing Tab until the item you want appears.</span></span> <span data-ttu-id="770a9-109">Conclusão de separador pode ajudar a escrever um nome do cmdlet, nome do parâmetro, nome da variável, o nome de propriedade do objeto ou um caminho de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="770a9-109">Tab completion can help with typing a cmdlet name, parameter name, variable name, object property name, or a file path.</span></span>

> [!NOTE]
> <span data-ttu-id="770a9-110">No painel de Script, premir SEPARADOR automaticamente concluirá um comando apenas quando estiver a editar ps1,. psd1 ou ficheiros. psm1.</span><span class="sxs-lookup"><span data-stu-id="770a9-110">In the Script Pane, pressing TAB will automatically complete a command only when you are editing .ps1, .psd1, or .psm1 files.</span></span> <span data-ttu-id="770a9-111">Conclusão de separador funciona a qualquer altura ao escrever no painel de comandos.</span><span class="sxs-lookup"><span data-stu-id="770a9-111">Tab completion works any time when you are typing in the Command Pane.</span></span>

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a><span data-ttu-id="770a9-112">Para concluir automaticamente uma entrada de parâmetro de cmdlet</span><span class="sxs-lookup"><span data-stu-id="770a9-112">To automatically complete a cmdlet parameter entry</span></span>
<span data-ttu-id="770a9-113">No painel de painel de comando ou Script, escreva um cmdlet seguido por um traço e, em seguida, prima SEPARADOR.</span><span class="sxs-lookup"><span data-stu-id="770a9-113">In the Command Pane or Script pane, type a cmdlet followed by a dash, and then press TAB.</span></span>

<span data-ttu-id="770a9-114">Por exemplo, digite `Get-Process -` e, em seguida, prima a tecla SEPARADOR várias vezes para apresentar cada um dos parâmetros do cmdlet por sua vez.</span><span class="sxs-lookup"><span data-stu-id="770a9-114">For example, type `Get-Process -` and then press TAB multiple times to display each of the parameters for the cmdlet in turn.</span></span>

## <a name="see-also"></a><span data-ttu-id="770a9-115">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="770a9-115">See Also</span></span>
- [<span data-ttu-id="770a9-116">Utilizar o ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="770a9-116">Using Windows PowerShell ISE</span></span>](using-the-windows-powershell-ise.md)
- [<span data-ttu-id="770a9-117">Como criar um separador de PowerShell</span><span class="sxs-lookup"><span data-stu-id="770a9-117">How to Create a PowerShell Tab</span></span>](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)

