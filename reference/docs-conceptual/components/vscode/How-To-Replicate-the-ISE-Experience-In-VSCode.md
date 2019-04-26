---
title: Como replicar a experiência do ISE no Visual Studio Code
description: Como replicar a experiência do ISE no Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058527"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Como replicar a experiência do ISE no Visual Studio Code

Enquanto a extensão de PowerShell para VSCode não procura paridade de funcionalidades completo com o ISE do PowerShell, existem recursos no local para fazer com que a experiência de VSCode mais natural para os usuários de ISE.

Este documento tenta definições de lista que pode configurar no VSCode para tornar o experiência familiar de um pouco mais em comparação com o ISE do usuário.

## <a name="key-bindings"></a>Enlaces de chave

| Função                              | Enlace de ISE                  | Enlace de VSCode                              |
| ----------------                      | -----------                  | --------------                              |
| Depurador de interrupção e break          | <kbd>Ctrl</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| Executar o texto realçado/linha atual | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| Lista de fragmentos disponíveis               | <kbd>Ctrl</kbd>+<kbd>J</kbd> | <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>Enlaces de tecla personalizados

Pode [configurar suas próprias ligações principais](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) no VSCode também.

## <a name="tab-completion"></a>Conclusão de tabulação

Para ativar a conclusão de tabulação mais semelhantes a ISE, adicione esta definição:

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> Esta definição foi adicionada diretamente para VSCode (e não na extensão). Seu comportamento é determinado pelo VSCode diretamente e não pode ser alterado, a extensão.

## <a name="no-focus-on-console-when-executing"></a>Não existem foco na consola, quando em execução

Para manter o foco no editor, quando executa com <kbd>F8</kbd>:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

A predefinição é `true` para fins de acessibilidade.

## <a name="dont-start-integrated-console-on-startup"></a>Não inicie a consola integrada no arranque

Para interromper a consola integrada no arranque, defina:

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> O plano de fundo, o processo de PowerShell ainda será iniciada uma vez que o que fornece o IntelliSense, análise de script, navegação de símbolos, etc. Mas a consola não será apresentada.

## <a name="assume-files-are-powershell-by-default"></a>Partem do princípio de arquivos são PowerShell por predefinição

Para tornar os arquivos sem novo título, registe-se como o PowerShell por predefinição:

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a>Esquema de cores

Um número de temas ISE estão disponíveis para VSCode tornar o editor pareça muito mais com o ISE.

Na [paleta de comandos] tipo `theme` para obter `Preferences: Color Theme` e pressione <kbd>Enter</kbd>.
Na lista pendente, selecione `PowerShell ISE`.

Pode definir esse tema nas configurações com:

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a>Explorador de comando do PowerShell

Graças ao trabalho de [ @corbob ](https://github.com/corbob), a extensão de PowerShell tem o início do desenvolvimento do seu próprio explorer de comando.

Na [paleta de comandos], introduza `PowerShell Command Explorer` e prima <kbd>Enter</kbd>.

## <a name="open-in-the-ise"></a>Abrir no ISE

Se ficar que queiram abrir um arquivo no ISE, de qualquer forma, pode utilizar <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.

## <a name="other-resources"></a>Outros recursos

- tem de 4sysops [um ótimo artigo](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) sobre como configurar o VSCode para ser mais parecido com o ISE.
- Tem de Mike F Robbins [uma excelente postagem](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) sobre como configurar o VSCode.
- Saiba PowerShell possui [uma gravação excelente](https://www.learnpwsh.com/setup-vs-code-for-powershell/) na obtenção de VSCode de configuração para o PowerShell.

## <a name="more-settings"></a>Mais definições

Se souber de mais maneiras de tornar o VSCode se sentir mais familiar para os utilizadores do ISE, contribua para este documento. Se não existe uma configuração de compatibilidade que procura, mas não é possível localizar qualquer forma de ativá-la, [abra um problema](https://github.com/PowerShell/vscode-powershell/issues/new/choose) e pergunte!

Temos o prazer sempre aceitar pedidos pull e contribuições também!

## <a name="vscode-tips"></a>Dicas de VSCode

### <a name="command-palette"></a>Paleta de comandos

<kbd>F1</kbd> ou <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> SHIFT</kbd>+<kbd>P</kbd> no macOS)

Uma forma prática de executar comandos em VSCode.
Para obter mais informações, consulte [documentos VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).

[Paleta de comandos]: #command-palette
