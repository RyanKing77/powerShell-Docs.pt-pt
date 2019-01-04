---
title: Como replicar a experiência ISE no Visual Studio Code
description: Como replicar a experiência ISE no Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012488"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="4b6a3-103">Como replicar a experiência ISE no Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4b6a3-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="4b6a3-104">Enquanto a extensão de PowerShell para VSCode não procura paridade de funcionalidades completo com o ISE do PowerShell, existem recursos no local para fazer com que a experiência de VSCode mais natural para os usuários de ISE.</span><span class="sxs-lookup"><span data-stu-id="4b6a3-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="4b6a3-105">Este documento tenta definições de lista que pode configurar no VSCode para tornar o experiência familiar de um pouco mais em comparação com o ISE do usuário.</span><span class="sxs-lookup"><span data-stu-id="4b6a3-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="4b6a3-106">Enlaces de chave</span><span class="sxs-lookup"><span data-stu-id="4b6a3-106">Key bindings</span></span>

| <span data-ttu-id="4b6a3-107">Função</span><span class="sxs-lookup"><span data-stu-id="4b6a3-107">Function</span></span>                              | <span data-ttu-id="4b6a3-108">Enlace de ISE</span><span class="sxs-lookup"><span data-stu-id="4b6a3-108">ISE Binding</span></span>                  | <span data-ttu-id="4b6a3-109">Enlace de VSCode</span><span class="sxs-lookup"><span data-stu-id="4b6a3-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="4b6a3-110">Depurador de interrupção e break</span><span class="sxs-lookup"><span data-stu-id="4b6a3-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="4b6a3-111"><kbd>CTRL</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="4b6a3-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="4b6a3-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="4b6a3-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="4b6a3-113">Executar o texto realçado/linha atual</span><span class="sxs-lookup"><span data-stu-id="4b6a3-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="4b6a3-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="4b6a3-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="4b6a3-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="4b6a3-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="4b6a3-116">Lista de fragmentos disponíveis</span><span class="sxs-lookup"><span data-stu-id="4b6a3-116">List available snippets</span></span>               | <span data-ttu-id="4b6a3-117"><kbd>CTRL</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="4b6a3-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="4b6a3-118"><kbd>CTRL</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="4b6a3-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="4b6a3-119">Enlaces de tecla personalizados</span><span class="sxs-lookup"><span data-stu-id="4b6a3-119">Custom Key bindings</span></span>

<span data-ttu-id="4b6a3-120">Pode [configurar suas próprias ligações principais](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) no VSCode também.</span><span class="sxs-lookup"><span data-stu-id="4b6a3-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="4b6a3-121">Conclusão de tabulação</span><span class="sxs-lookup"><span data-stu-id="4b6a3-121">Tab completion</span></span>

<span data-ttu-id="4b6a3-122">Para ativar a conclusão de tabulação mais semelhantes a ISE, adicione esta definição:</span><span class="sxs-lookup"><span data-stu-id="4b6a3-122">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> <span data-ttu-id="4b6a3-123">Esta definição foi adicionada diretamente para VSCode (e não na extensão).</span><span class="sxs-lookup"><span data-stu-id="4b6a3-123">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="4b6a3-124">Seu comportamento é determinado pelo VSCode diretamente e não pode ser alterado, a extensão.</span><span class="sxs-lookup"><span data-stu-id="4b6a3-124">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="4b6a3-125">Não existem foco na consola, quando em execução</span><span class="sxs-lookup"><span data-stu-id="4b6a3-125">No focus on console when executing</span></span>

<span data-ttu-id="4b6a3-126">Para manter o foco no editor, quando executa com <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="4b6a3-126">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="4b6a3-127">A predefinição é `true` para fins de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="4b6a3-127">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="4b6a3-128">Não inicie a consola integrada no arranque</span><span class="sxs-lookup"><span data-stu-id="4b6a3-128">Don't start integrated console on startup</span></span>

<span data-ttu-id="4b6a3-129">Para interromper a consola integrada no arranque, defina:</span><span class="sxs-lookup"><span data-stu-id="4b6a3-129">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="4b6a3-130">O plano de fundo, o processo de PowerShell ainda será iniciada uma vez que o que fornece o IntelliSense, análise de script, navegação de símbolos, etc. Mas a consola não será apresentada.</span><span class="sxs-lookup"><span data-stu-id="4b6a3-130">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="4b6a3-131">Partem do princípio de arquivos são PowerShell por predefinição</span><span class="sxs-lookup"><span data-stu-id="4b6a3-131">Assume files are PowerShell by default</span></span>

<span data-ttu-id="4b6a3-132">Para tornar os arquivos sem novo título, registe-se como o PowerShell por predefinição:</span><span class="sxs-lookup"><span data-stu-id="4b6a3-132">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a><span data-ttu-id="4b6a3-133">Esquema de cores</span><span class="sxs-lookup"><span data-stu-id="4b6a3-133">Color scheme</span></span>

<span data-ttu-id="4b6a3-134">Um número de temas ISE estão disponíveis para VSCode tornar o editor pareça muito mais com o ISE.</span><span class="sxs-lookup"><span data-stu-id="4b6a3-134">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="4b6a3-135">Na [paleta de comandos] tipo `theme` para obter `Preferences: Color Theme` e pressione <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4b6a3-135">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="4b6a3-136">Na lista pendente, selecione `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="4b6a3-136">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="4b6a3-137">Pode definir esse tema nas configurações com:</span><span class="sxs-lookup"><span data-stu-id="4b6a3-137">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="4b6a3-138">Explorador de comando do PowerShell</span><span class="sxs-lookup"><span data-stu-id="4b6a3-138">PowerShell Command Explorer</span></span>

<span data-ttu-id="4b6a3-139">Graças ao trabalho de [ @corbob ](https://github.com/corbob), a extensão de PowerShell tem o início do desenvolvimento do seu próprio explorer de comando.</span><span class="sxs-lookup"><span data-stu-id="4b6a3-139">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="4b6a3-140">Na [paleta de comandos], introduza `PowerShell Command Explorer` e prima <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4b6a3-140">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="4b6a3-141">Abrir no ISE</span><span class="sxs-lookup"><span data-stu-id="4b6a3-141">Open in the ISE</span></span>

<span data-ttu-id="4b6a3-142">Se ficar que queiram abrir um arquivo no ISE, de qualquer forma, pode utilizar <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4b6a3-142">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="4b6a3-143">Outros recursos</span><span class="sxs-lookup"><span data-stu-id="4b6a3-143">Other resources</span></span>

- <span data-ttu-id="4b6a3-144">tem de 4sysops [um ótimo artigo](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) sobre como configurar o VSCode para ser mais parecido com o ISE.</span><span class="sxs-lookup"><span data-stu-id="4b6a3-144">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="4b6a3-145">Tem de Mike F Robbins [uma excelente postagem](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) sobre como configurar o VSCode.</span><span class="sxs-lookup"><span data-stu-id="4b6a3-145">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="4b6a3-146">Saiba PowerShell possui [uma gravação excelente](https://www.learnpwsh.com/setup-vs-code-for-powershell/) na obtenção de VSCode de configuração para o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4b6a3-146">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="4b6a3-147">Mais definições</span><span class="sxs-lookup"><span data-stu-id="4b6a3-147">More settings</span></span>

<span data-ttu-id="4b6a3-148">Se souber de mais maneiras de tornar o VSCode se sentir mais familiar para os utilizadores do ISE, contribua para este documento. Se não existe uma configuração de compatibilidade que procura, mas não é possível localizar qualquer forma de ativá-la, [abra um problema](https://github.com/PowerShell/vscode-powershell/issues/new/choose) e pergunte!</span><span class="sxs-lookup"><span data-stu-id="4b6a3-148">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="4b6a3-149">Temos o prazer sempre aceitar pedidos pull e contribuições também!</span><span class="sxs-lookup"><span data-stu-id="4b6a3-149">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="4b6a3-150">Dicas de VSCode</span><span class="sxs-lookup"><span data-stu-id="4b6a3-150">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="4b6a3-151">Paleta de comandos</span><span class="sxs-lookup"><span data-stu-id="4b6a3-151">Command Palette</span></span>

<span data-ttu-id="4b6a3-152"><kbd>F1</kbd> ou <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> SHIFT</kbd>+<kbd>P</kbd> no macOS)</span><span class="sxs-lookup"><span data-stu-id="4b6a3-152"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="4b6a3-153">Uma forma prática de executar comandos em VSCode.</span><span class="sxs-lookup"><span data-stu-id="4b6a3-153">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="4b6a3-154">Para obter mais informações, consulte [documentos VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="4b6a3-154">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Paleta de comandos]: #command-palette
[Command Palette]: #command-palette
