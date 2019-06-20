---
title: Utilizar o Visual Studio Code para a edição e depuração remotas
description: Utilizar o Visual Studio Code para a edição e depuração remotas
ms.date: 06/13/2019
ms.openlocfilehash: ae3b7a3709498fcd547a48d0849b0dc880217225
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263991"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Utilizar o Visual Studio Code para a edição e depuração remotas

Para aqueles que estão familiarizados com o ISE, deve se lembrar que pode executar `psedit file.ps1` a partir da consola integrada para abrir ficheiros - locais ou remotos - botão direito do rato no ISE.

Esse recurso também está disponível na extensão do PowerShell para VSCode. Este guia mostra-lhe como fazê-lo.

## <a name="prerequisites"></a>Pré-requisitos

Este guia assume que tem:

- um recurso remoto (ex: uma VM, um contentor) que têm acesso a
- PowerShell em execução no mesmo e a máquina de anfitrião
- VSCode e a extensão de PowerShell para VSCode

Esta funcionalidade funciona no Windows PowerShell e no PowerShell Core.

Esta funcionalidade também funciona ao ligar a uma máquina remota através de WinRM, PowerShell Direct ou SSH. Se quiser utilizar o SSH, mas estiver a utilizar o Windows, consulte a [versão de Win32 do SSH](https://github.com/PowerShell/Win32-OpenSSH)!

> [!IMPORTANT]
> O `Open-EditorFile` e `psedit` comandos só funcionam **consola integrada de PowerShell** criado pela extensão do PowerShell para VSCode.

## <a name="usage-examples"></a>Exemplos de utilização

Estes exemplos mostram remotos, edição e depuração de um MacBook Pro para uma VM do Ubuntu em execução no Azure. O processo é idêntico no Windows.

### <a name="local-file-editing-with-open-editorfile"></a>Ficheiro local com Open EditorFile de edição

Com a extensão de PowerShell para utilizar o VSCode e abrir a consola integrada do PowerShell, também podemos digitar `Open-EditorFile foo.ps1` ou `psedit foo.ps1` para abrir o ficheiro de local foo.ps1 diretamente no editor.

![Aberto EditorFile foo.ps1 funciona localmente](images/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> O ficheiro `foo.ps1` já devem existir.

A partir daí, podemos:

- Adicionar pontos de interrupção para o medianiz

  ![adicionar o ponto de interrupção para medianiz](images/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- Pressione F5 para depurar o script do PowerShell.

  ![depurar o script do PowerShell local](images/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

Durante a depuração, pode interagir com a consola de depuração, confira as variáveis no âmbito à esquerda, e todos os outro padrão ferramentas de depuração.

### <a name="remote-file-editing-with-open-editorfile"></a>Ficheiro remoto edição com EditorFile aberto

Agora vamos entrar em ficheiro remoto, edição e depuração. Os passos são praticamente os mesmos, existe apenas uma coisa que precisamos fazer primeiro - introduzir nossa sessão de PowerShell para o servidor remoto.

Existe um cmdlet para fazer isso. Ele é chamado `Enter-PSSession`.

A explicação menos potente para baixo do cmdlet é:

- `Enter-PSSession -ComputerName foo` inicia uma sessão através do WinRM
- `Enter-PSSession -ContainerId foo` e `Enter-PSSession -VmId foo` iniciar uma sessão através do PowerShell Direct
- `Enter-PSSession -HostName foo` inicia uma sessão através de SSH

Para obter mais informações, consulte a documentação para [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).

Uma vez que vamos partir de macOS para uma VM do Ubuntu no Azure, estamos a utilizar SSH para a gestão remota.

Em primeiro lugar, na consola do integrada, execute `Enter-PSSession`. Está conectado à sessão remota quando `[<hostname>]` mostra até à esquerda da sua linha de comandos.

![A chamada para Enter-PSSession](images/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

Agora, podemos fazer as mesmas etapas que estejamos editando um script local.

1. Execute `Open-EditorFile test.ps1` ou `psedit test.ps1` para abrir a ligação remota `test.ps1` ficheiro

  ![O ficheiro de test.ps1 de EditorFile aberto](images/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. Editar os pontos de interrupção do ficheiro/conjunto

   ![editar e configurar pontos de interrupção](images/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. Iniciar a depuração (F5) o ficheiro remoto

   ![depuração do ficheiro remoto](images/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

Se tiver quaisquer problemas, pode abrir problemas a [repositório do GitHub](https://github.com/powershell/vscode-powershell).
