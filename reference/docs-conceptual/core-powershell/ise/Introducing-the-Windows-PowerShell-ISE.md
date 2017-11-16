---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "Introdução ao ISE do Windows PowerShell"
ms.openlocfilehash: 75242c20548e2e83397867214417a48806c897ec
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="introducing-the-windows-powershell-ise"></a><span data-ttu-id="4f44a-103">Introdução ao ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4f44a-103">Introducing the Windows PowerShell ISE</span></span>
<span data-ttu-id="4f44a-104">O Windows PowerShell Integrated Scripting Environment (ISE) é uma aplicação de anfitrião para o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f44a-104">The Windows PowerShell Integrated Scripting Environment (ISE) is a host application for Windows PowerShell.</span></span> <span data-ttu-id="4f44a-105">No ISE do Windows PowerShell, pode executar comandos e escrita, teste e depuração de scripts numa interface baseados em Windows gráfico utilizador único com a edição de múltiplas linhas, conclusão de separador, cores da sintaxe, execução seletiva, ajuda sensível ao contexto e suporte para idiomas de direita para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="4f44a-105">In Windows PowerShell ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphic user interface with multiline editing, tab completion, syntax coloring, selective execution, context-sensitive help, and support for right-to-left languages.</span></span>
<span data-ttu-id="4f44a-106">Pode utilizar itens de menu e atalhos de teclado para efetuar muitas das mesmas tarefas que executará a consola do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f44a-106">You can use menu items and keyboard shortcuts to perform many of the same tasks that you would perform in the Windows PowerShell console.</span></span>  <span data-ttu-id="4f44a-107">Por exemplo, quando depurar um script no ISE do Windows PowerShell, para definir um ponto de interrupção de linha num script, clique com o botão direito a linha de código e, em seguida, clique em **Ativar/desativar ponto de interrupção**.</span><span class="sxs-lookup"><span data-stu-id="4f44a-107">For example, when you debug a script in the Windows PowerShell ISE, to set a line breakpoint in a script, right-click the line of code, and then click **Toggle Breakpoint**.</span></span>

<span data-ttu-id="4f44a-108">Experimente estas funcionalidades no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f44a-108">Try these features in Windows PowerShell ISE.</span></span>

- <span data-ttu-id="4f44a-109">Edição de múltiplas linhas: para inserir uma linha em branco sob a linha atual no painel de comando, prima SHIFT + ENTER.</span><span class="sxs-lookup"><span data-stu-id="4f44a-109">Multiline editing: To insert a blank line under the current line in the Command pane, press SHIFT+ENTER.</span></span>

- <span data-ttu-id="4f44a-110">Execução seletiva: para executar a parte de um script, selecione o texto que pretende executar e, em seguida, clique em de **executar Script** botão.</span><span class="sxs-lookup"><span data-stu-id="4f44a-110">Selective execution: To run part of a script, select the text you want to run, and then click the **Run Script** button.</span></span> <span data-ttu-id="4f44a-111">Em alternativa, prima F5.</span><span class="sxs-lookup"><span data-stu-id="4f44a-111">Or, press F5.</span></span>

- <span data-ttu-id="4f44a-112">Ajuda sensível ao contexto: tipo **Invoke-Item**, e, em seguida, prima F1.</span><span class="sxs-lookup"><span data-stu-id="4f44a-112">Context-sensitive help: Type **Invoke-Item**, and then press F1.</span></span> <span data-ttu-id="4f44a-113">Para abrir o ficheiro de ajuda para o tópico de ajuda para o **Invoke-Item** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f44a-113">The Help file opens to the Help topic for the **Invoke-Item** cmdlet.</span></span>

<span data-ttu-id="4f44a-114">O ISE do Windows PowerShell permite-lhe personalizar alguns aspetos das respetivo aspeto.</span><span class="sxs-lookup"><span data-stu-id="4f44a-114">The Windows PowerShell ISE lets you customize some aspects of its appearance.</span></span> <span data-ttu-id="4f44a-115">Também tem o seus próprios perfil do Windows PowerShell, onde pode armazenar funções, aliases, variáveis e os comandos que utiliza no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f44a-115">It also has its own Windows PowerShell profile, where you can store functions, aliases, variables, and commands you use in the Windows PowerShell ISE.</span></span>

### <a name="to-start-the-windows-powershell-ise"></a><span data-ttu-id="4f44a-116">Para iniciar o ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4f44a-116">To start the Windows PowerShell ISE</span></span>

1. <span data-ttu-id="4f44a-117">Efetue uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="4f44a-117">Do one of the following:</span></span>

    -   <span data-ttu-id="4f44a-118">Clique em **iniciar**, aponte para **todos os programas**, aponte para **Windows PowerShell V2**e, em seguida, clique em **ISE do Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="4f44a-118">Click **Start**, point to **All Programs**, point to **Windows PowerShell V2**, and then click **Windows PowerShell ISE**.</span></span>

    -   <span data-ttu-id="4f44a-119">Na consola do Windows PowerShell Cmd.exe ou na caixa de executar, tipo, **powershell_ise.exe**.</span><span class="sxs-lookup"><span data-stu-id="4f44a-119">In the Windows PowerShell console Cmd.exe, or in the Run box, type, **powershell_ise.exe**.</span></span>

### <a name="to-get-help-in-the-windows-powershell-ise"></a><span data-ttu-id="4f44a-120">Para obter ajuda no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4f44a-120">To get Help in the Windows PowerShell ISE</span></span>

- <span data-ttu-id="4f44a-121">No **ajudar** menu, clique em **ajuda do Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="4f44a-121">On the **Help** menu, click **Windows PowerShell Help**.</span></span> <span data-ttu-id="4f44a-122">Em alternativa, prima F1.</span><span class="sxs-lookup"><span data-stu-id="4f44a-122">Or, press F1.</span></span> <span data-ttu-id="4f44a-123">O ficheiro que abre descreve o ISE do Windows PowerShell e o Windows PowerShell, incluindo todos os ajuda disponível a partir do cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="4f44a-123">The file that opens describes Windows PowerShell ISE and Windows PowerShell, including all of the help available from the Get-Help cmdlet.</span></span>

