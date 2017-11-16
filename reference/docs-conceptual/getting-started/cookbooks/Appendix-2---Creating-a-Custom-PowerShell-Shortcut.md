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
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a><span data-ttu-id="791d3-103">Apêndice 2 - criar um atalho personalizados do PowerShell</span><span class="sxs-lookup"><span data-stu-id="791d3-103">Appendix 2 - Creating a Custom PowerShell Shortcut</span></span>
<span data-ttu-id="791d3-104">O procedimento seguinte descreve como criar um atalho para o Windows PowerShell que tem várias opções convenientes personalizadas.</span><span class="sxs-lookup"><span data-stu-id="791d3-104">The following procedure describes how to create a shortcut to Windows PowerShell that has several convenient options customized.</span></span>

1. <span data-ttu-id="791d3-105">Crie um atalho que aponta para o Powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="791d3-105">Create a shortcut that points to Powershell.exe.</span></span>

2. <span data-ttu-id="791d3-106">Faça duplo clique no atalho e, em seguida, clique em **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="791d3-106">Right-click the shortcut, and then click **Properties**.</span></span>

3. <span data-ttu-id="791d3-107">Clique na **opções** separador.</span><span class="sxs-lookup"><span data-stu-id="791d3-107">Click the **Options** tab.</span></span>

4. <span data-ttu-id="791d3-108">No **editar opções** secção, selecione o **QuickEdit** caixa de verificação.</span><span class="sxs-lookup"><span data-stu-id="791d3-108">In the **Edit Options** section, select the **QuickEdit** check box.</span></span>

    <span data-ttu-id="791d3-109">Esta definição permite-lhe selecionar o texto na janela da consola do Windows PowerShell, arrastando botão esquerdo do rato e permite-lhe copiar texto para a área de transferência, premindo ENTER, ou clicando com o rato.</span><span class="sxs-lookup"><span data-stu-id="791d3-109">This setting lets you select text in the Windows PowerShell console window by dragging the left mouse button, and it lets you copy text to the clipboard by pressing ENTER or by right-clicking the mouse.</span></span>

5. <span data-ttu-id="791d3-110">No **editar opções** secção, selecione o **inserir modo** caixa de verificação.</span><span class="sxs-lookup"><span data-stu-id="791d3-110">In the **Edit Options** section, select the **Insert Mode** check box.</span></span> <span data-ttu-id="791d3-111">Esta definição permite-lhe o botão direito do rato na janela da consola automaticamente colar o texto da área de transferência.</span><span class="sxs-lookup"><span data-stu-id="791d3-111">This setting lets you right-click in the console window to automatically paste text from the clipboard.</span></span>

6. <span data-ttu-id="791d3-112">No **histórico de comando** secção, escreva ou selecione um número entre 1 e 999 no **tamanho da memória intermédia** caixa.</span><span class="sxs-lookup"><span data-stu-id="791d3-112">In the **Command History** section, type or select a number between 1 and 999 in the **Buffer Size** box.</span></span> <span data-ttu-id="791d3-113">Isto define o número de comandos escritos que serão mantidos na memória intermédia de consola.</span><span class="sxs-lookup"><span data-stu-id="791d3-113">This sets the number of typed commands that will be kept in the console buffer.</span></span>

7. <span data-ttu-id="791d3-114">No **histórico de comando** secção, selecione o **eliminar duplicados antigo** caixa de verificação para eliminar repetidos comandos a partir da memória intermédia de consola.</span><span class="sxs-lookup"><span data-stu-id="791d3-114">In the **Command History** section, select the **Discard Old Duplicates** check box to eliminate repeated commands from the console buffer.</span></span>

8. <span data-ttu-id="791d3-115">Clique na **esquema** separador.</span><span class="sxs-lookup"><span data-stu-id="791d3-115">Click the **Layout** tab.</span></span>

9. <span data-ttu-id="791d3-116">No **memória intermédia de ecrã** secção, escreva um número entre 1 e 9999 no **altura** caixa.</span><span class="sxs-lookup"><span data-stu-id="791d3-116">In the **Screen Buffer** section, type a number between 1 and 9999 in the **Height** box.</span></span> <span data-ttu-id="791d3-117">A altura representa o número de linhas de saída que são colocado na memória intermédia.</span><span class="sxs-lookup"><span data-stu-id="791d3-117">The height represents the number of lines of output that are buffered.</span></span> <span data-ttu-id="791d3-118">Este é o número máximo de linhas retidos para visualização quando percorra a janela de consola.</span><span class="sxs-lookup"><span data-stu-id="791d3-118">This is the maximum number of lines retained for viewing when you scroll through the console window.</span></span> <span data-ttu-id="791d3-119">Se este número é inferior à altura mostrada no **tamanho da janela** secção, a altura do tamanho de janela automaticamente será reduzida para o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="791d3-119">If this number is lower than the height shown in the **Window size** section, the window size height will automatically be reduced to the same value.</span></span>

10. <span data-ttu-id="791d3-120">No **tamanho da janela** secção, escreva um número entre 1 e 9999 para a largura.</span><span class="sxs-lookup"><span data-stu-id="791d3-120">In the **Window Size** section, type a number between 1 and 9999 for the width.</span></span> <span data-ttu-id="791d3-121">Representa o número de carateres que são apresentados na janela da consola.</span><span class="sxs-lookup"><span data-stu-id="791d3-121">This represents the number of characters that are displayed across the console window.</span></span> <span data-ttu-id="791d3-122">A largura predefinida é 80 e saída do Windows PowerShell formatação foi concebida para esta largura.</span><span class="sxs-lookup"><span data-stu-id="791d3-122">The default width is 80, and Windows PowerShell's output formatting is designed for this width.</span></span>

11. <span data-ttu-id="791d3-123">Se pretende colocar a consola num determinado ponto no ambiente de trabalho quando é aberta, desmarque a **permitem a janela de posição de sistema** caixa de verificação a **posição da janela** secção e, em seguida, altere os valores existentes no  **À esquerda** e **superior** caixas **posição da janela** secção.</span><span class="sxs-lookup"><span data-stu-id="791d3-123">If you want to place the console at a particular point on the desktop when it is opened, clear the **Let system position window** check box in the **Window position** section, and then change the values in the **Left** and **Top** boxes in the **Window position** section.</span></span>

12. <span data-ttu-id="791d3-124">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="791d3-124">Click **OK**.</span></span>

