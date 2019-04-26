---
title: Utilizar o Visual Studio Code para a edição e depuração remotas
description: Utilizar o Visual Studio Code para a edição e depuração remotas
ms.date: 08/06/2018
ms.openlocfilehash: fbc1ee3556e822b4afb2b37111d0688dc89fdab3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086681"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Utilizar o Visual Studio Code para a edição e depuração remotas

Para aqueles que estão familiarizados com o ISE, deve se lembrar que pode executar `psedit file.ps1` a partir da consola integrada para abrir ficheiros - locais ou remotos - botão direito do rato no ISE.

Na verdade, esse recurso também está disponível na extensão do PowerShell para VSCode. Este guia irá mostrar como fazer isso.

## <a name="prerequisites"></a>Pré-requisitos

Este guia assume que tem:

- um recurso remoto (ex: uma VM, um contentor) que têm acesso a
- PowerShell em execução no mesmo e a máquina de anfitrião
- VSCode e a extensão de PowerShell para VSCode

Esta funcionalidade funciona no Windows PowerShell e no PowerShell Core.

Esta funcionalidade também funciona ao ligar a uma máquina remota através de WinRM, PowerShell Direct ou SSH. Se quiser utilizar o SSH, mas estiver a utilizar o Windows, consulte a [versão de Win32 do SSH](https://github.com/PowerShell/Win32-OpenSSH)!

## <a name="lets-go"></a>Vamos

Nesta seção, vou percorrer remoto de edição e depuração de meu MacBook Pro, para uma VM do Ubuntu em execução no Azure. Eu poderá não estar a utilizar o Windows, mas **o processo é idêntico**.

### <a name="local-file-editing-with-open-editorfile"></a>Ficheiro local com Open EditorFile de edição

Com a extensão de PowerShell para utilizar o VSCode e abrir a consola integrada do PowerShell, também podemos digitar `Open-EditorFile foo.ps1` ou `psedit foo.ps1` para abrir o ficheiro de local foo.ps1 diretamente no editor.

![Aberto EditorFile foo.ps1 funciona localmente](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> foo.ps1 já devem existir.

A partir daí, podemos:

adicionar pontos de interrupção para o medianiz ![adicionar o ponto de interrupção para medianiz](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)

e pressionar F5 para depurar o script do PowerShell.
![depurar o script do PowerShell local](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)

Durante a depuração, pode interagir com a consola de depuração, confira as variáveis no âmbito à esquerda, e todos os outro padrão ferramentas de depuração.

### <a name="remote-file-editing-with-open-editorfile"></a>Ficheiro remoto edição com EditorFile aberto

Agora vamos entrar em ficheiro remoto, edição e depuração. Os passos são praticamente os mesmos, existe apenas uma coisa que precisamos fazer primeiro - introduzir nossa sessão de PowerShell para o servidor remoto.

Existe um cmdlet para fazer isso. Ele é chamado `Enter-PSSession`.

A explicação menos potente para baixo do cmdlet é:

- `Enter-PSSession -ComputerName foo` inicia uma sessão através do WinRM
- `Enter-PSSession -ContainerId foo` e `Enter-PSSession -VmId foo` iniciar uma sessão através do PowerShell Direct
- `Enter-PSSession -HostName foo` inicia uma sessão através de SSH

Para obter mais informações sobre `Enter-PSSession`, verifique os docs [aqui](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).

Posso utilizar SSH para a gestão remota, uma vez que vou partir de macOS para uma VM do Ubuntu no Azure.

Em primeiro lugar, na consola do integrada, vamos executar nosso Enter-PSSession. Saberá que está na sessão porque `[something]` aparecerá para a esquerda da sua linha de comandos.

![A chamada para Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

A partir daí, podemos fazer os passos exatos como se podemos estava editando um script local.

1. Execute `Open-EditorFile test.ps1` ou `psedit test.ps1` para abrir a ligação remota `test.ps1` ficheiro ![EditorFile de abrir o ficheiro de test.ps1](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)
2. Editar os pontos de interrupção do ficheiro/conjunto ![editar e configurar pontos de interrupção](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. Iniciar a depuração (F5) o ficheiro remoto

![depuração do ficheiro remoto](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

É tudo o que é preciso! Esperamos que este guia ajudou a limpar a quaisquer perguntas sobre a depuração remota e o PowerShell no VSCode de edição.

Se tiver quaisquer problemas, pode abrir problemas [no repositório GitHub](http://github.com/powershell/vscode-powershell).
