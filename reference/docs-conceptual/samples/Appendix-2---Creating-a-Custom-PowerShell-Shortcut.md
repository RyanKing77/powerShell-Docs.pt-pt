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
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a><span data-ttu-id="1a26b-103">Apêndice 2 – criar um atalho para o PowerShell personalizado</span><span class="sxs-lookup"><span data-stu-id="1a26b-103">Appendix 2 - Creating a Custom PowerShell Shortcut</span></span>

<span data-ttu-id="1a26b-104">O procedimento seguinte descreve como criar um atalho para o Windows PowerShell que tem várias opções convenientes personalizadas.</span><span class="sxs-lookup"><span data-stu-id="1a26b-104">The following procedure describes how to create a shortcut to Windows PowerShell that has several convenient options customized.</span></span>

1. <span data-ttu-id="1a26b-105">Crie um atalho que aponta para Powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="1a26b-105">Create a shortcut that points to Powershell.exe.</span></span>

2. <span data-ttu-id="1a26b-106">Com o botão direito no atalho e, em seguida, clique em **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="1a26b-106">Right-click the shortcut, and then click **Properties**.</span></span>

3. <span data-ttu-id="1a26b-107">Clique na **opções** separador.</span><span class="sxs-lookup"><span data-stu-id="1a26b-107">Click the **Options** tab.</span></span>

4. <span data-ttu-id="1a26b-108">Na **editar opções** secção, selecione a **QuickEdit** caixa de verificação.</span><span class="sxs-lookup"><span data-stu-id="1a26b-108">In the **Edit Options** section, select the **QuickEdit** check box.</span></span>

    <span data-ttu-id="1a26b-109">Esta definição permite-lhe selecionar o texto na janela de consola do Windows PowerShell ao arrastar o botão esquerdo do mouse e permite-lhe copiar texto para a área de transferência, premindo ENTER ou clicando com o mouse.</span><span class="sxs-lookup"><span data-stu-id="1a26b-109">This setting lets you select text in the Windows PowerShell console window by dragging the left mouse button, and it lets you copy text to the clipboard by pressing ENTER or by right-clicking the mouse.</span></span>

5. <span data-ttu-id="1a26b-110">Na **editar opções** secção, selecione a **inserir modo** caixa de verificação.</span><span class="sxs-lookup"><span data-stu-id="1a26b-110">In the **Edit Options** section, select the **Insert Mode** check box.</span></span> <span data-ttu-id="1a26b-111">Esta definição permite-lhe com o botão direito na janela da consola automaticamente colar texto da área de transferência.</span><span class="sxs-lookup"><span data-stu-id="1a26b-111">This setting lets you right-click in the console window to automatically paste text from the clipboard.</span></span>

6. <span data-ttu-id="1a26b-112">Na **histórico de comandos** secção, escreva ou selecione um número entre 1 e 999 no **tamanho da memória intermédia** caixa.</span><span class="sxs-lookup"><span data-stu-id="1a26b-112">In the **Command History** section, type or select a number between 1 and 999 in the **Buffer Size** box.</span></span> <span data-ttu-id="1a26b-113">Isso define o número de comandos escritos que serão mantidos na memória intermédia de consola.</span><span class="sxs-lookup"><span data-stu-id="1a26b-113">This sets the number of typed commands that will be kept in the console buffer.</span></span>

7. <span data-ttu-id="1a26b-114">Na **histórico de comandos** secção, selecione a **descartar duplica antigo** caixa de verificação para eliminar repetidos de comandos do buffer de consola.</span><span class="sxs-lookup"><span data-stu-id="1a26b-114">In the **Command History** section, select the **Discard Old Duplicates** check box to eliminate repeated commands from the console buffer.</span></span>

8. <span data-ttu-id="1a26b-115">Clique na **esquema** separador.</span><span class="sxs-lookup"><span data-stu-id="1a26b-115">Click the **Layout** tab.</span></span>

9. <span data-ttu-id="1a26b-116">Na **memória intermédia ecrã** secção, escreva um número entre 1 e 9999 no **altura** caixa.</span><span class="sxs-lookup"><span data-stu-id="1a26b-116">In the **Screen Buffer** section, type a number between 1 and 9999 in the **Height** box.</span></span> <span data-ttu-id="1a26b-117">A altura representa o número de linhas de saída que são colocados em memória intermédia.</span><span class="sxs-lookup"><span data-stu-id="1a26b-117">The height represents the number of lines of output that are buffered.</span></span> <span data-ttu-id="1a26b-118">Este é o número máximo de linhas mantido para ver quando rola a janela da consola.</span><span class="sxs-lookup"><span data-stu-id="1a26b-118">This is the maximum number of lines retained for viewing when you scroll through the console window.</span></span> <span data-ttu-id="1a26b-119">Se este número é menor do que a altura mostrada a **tamanho da janela** secção, automaticamente diminui a altura do tamanho de janela para o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="1a26b-119">If this number is lower than the height shown in the **Window size** section, the window size height will automatically be reduced to the same value.</span></span>

10. <span data-ttu-id="1a26b-120">Na **tamanho da janela** secção, escreva um número entre 1 e 9999 para a largura.</span><span class="sxs-lookup"><span data-stu-id="1a26b-120">In the **Window Size** section, type a number between 1 and 9999 for the width.</span></span> <span data-ttu-id="1a26b-121">Isso representa o número de carateres que são apresentados na janela da consola.</span><span class="sxs-lookup"><span data-stu-id="1a26b-121">This represents the number of characters that are displayed across the console window.</span></span> <span data-ttu-id="1a26b-122">A largura predefinida é 80 e a formatação de saída do Windows PowerShell foi concebida para esta largura.</span><span class="sxs-lookup"><span data-stu-id="1a26b-122">The default width is 80, and Windows PowerShell's output formatting is designed for this width.</span></span>

11. <span data-ttu-id="1a26b-123">Se pretende colocar o console num momento específico no ambiente de trabalho quando for aberta, desmarque a **permitir que a janela de posição de sistema** caixa de verificação a **posição da janela** secção e, em seguida, altere os valores no  **À esquerda** e **superior** caixas no **posição da janela** secção.</span><span class="sxs-lookup"><span data-stu-id="1a26b-123">If you want to place the console at a particular point on the desktop when it is opened, clear the **Let system position window** check box in the **Window position** section, and then change the values in the **Left** and **Top** boxes in the **Window position** section.</span></span>

12. <span data-ttu-id="1a26b-124">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="1a26b-124">Click **OK**.</span></span>