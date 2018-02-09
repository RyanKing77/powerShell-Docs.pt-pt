---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "Iniciar o Windows PowerShell em Versões Anteriores do Windows"
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: 52e3acc1fd3009ecad3b7134008e38d4edfb5ca7
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/08/2018
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a>Iniciar o Windows PowerShell em Versões Anteriores do Windows
Esta secção explica como iniciar o Windows PowerShell e Windows PowerShell Integrated Scripting Environment (ISE) no Windows® 7, Windows Server® 2008 R2 e Windows Server® 2008. Também explica como ativar a funcionalidade opcional para o ISE do Windows PowerShell no Windows PowerShell 2.0 no Windows Server® 2008 R2 e no Windows Server® 2008.

Para instalar o Windows PowerShell 4.0 em sistemas suportados, transfira e instale [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881). Para obter mais informações, consulte [instalar o Windows PowerShell](Installing-Windows-PowerShell.md).

Para instalar o Windows PowerShell 3.0 em sistemas suportados, transfira e instale [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290). Para obter mais informações, consulte [instalar o Windows PowerShell](Installing-Windows-PowerShell.md).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Como iniciar o Windows PowerShell em versões anteriores do Windows
Utilize qualquer um dos seguintes métodos para iniciar a versão instalada do Windows PowerShell 3.0 ou Windows PowerShell 4.0, onde for aplicável.

#### <a name="from-the-start-menu"></a>No Menu Iniciar

- Clique em **iniciar**, tipo **PowerShell**e, em seguida, clique em **do Windows PowerShell**.

- Do **iniciar** menu, clique em **iniciar**, clique em **todos os programas**, clique em **acessórios**, clique em de **do Windows PowerShell**  pasta e, em seguida, clique em **do Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>Na linha de comandos

- No Cmd.exe, o Windows PowerShell ou o ISE do Windows PowerShell, para iniciar o Windows PowerShell, escreva:

    ```
    PowerShell
    ```

    Também pode utilizar os parâmetros do programa PowerShell.exe para personalizar a sessão. Para obter mais informações, consulte [ajudar a linha de comandos PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>Com administração privilégios ("Executar como administrador")

1. Clique em **iniciar**, tipo **PowerShell**, faça duplo clique **do Windows PowerShell**e, em seguida, clique em **executar como administrador**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Como iniciar o ISE do Windows PowerShell em versões anteriores do Windows
Utilize qualquer um dos seguintes métodos para iniciar o ISE do Windows PowerShell.

#### <a name="from-the-start-menu"></a>No Menu Iniciar

- Clique em **iniciar**, tipo **ISE**e, em seguida, clique em **ISE do Windows PowerShell**.

- Do **iniciar** menu, clique em **iniciar**, clique em **todos os programas**, clique em **acessórios**, clique em de **do Windows PowerShell**  pasta e, em seguida, clique em **ISE do Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>Na linha de comandos

- No Cmd.exe, o Windows PowerShell ou o ISE do Windows PowerShell, para iniciar o Windows PowerShell, escreva:

    ```
    PowerShell_ISE
    ```

    ou

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a>Com administração privilégios ("Executar como administrador")

1. Clique em **iniciar**, tipo **ISE**, faça duplo clique **ISE do Windows PowerShell**e, em seguida, clique em **executar como administrador**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Como ativar o ISE do Windows PowerShell em versões anteriores do Windows
No Windows PowerShell 4.0 e o Windows PowerShell 3.0, o ISE do Windows PowerShell está ativada por predefinição em todas as versões do Windows. Caso não ainda esteja ativado, Windows Management Framework 4.0 ou o Windows Management Framework 3.0 ativa o mesmo.

No Windows PowerShell 2.0, o ISE do Windows PowerShell está ativada por predefinição no Windows 7. No entanto, no Windows Server 2008 R2 e Windows Server 2008, é uma funcionalidade opcional.

Para ativar o ISE do Windows PowerShell no Windows PowerShell 2.0 no Windows Server 2008 R2 ou Windows Server 2008, utilize o procedimento seguinte.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Para ativar o Windows PowerShell Integrated Scripting Environment (ISE)

1. Inicie o Gestor de Servidor.

2. Clique em **funcionalidades** e, em seguida, clique em **adicionar funcionalidades**.

3. Em Selecionar funcionalidades, clique em Windows PowerShell Integrated Scripting Environment (ISE).

