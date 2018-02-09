---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Iniciar o Windows PowerShell
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: 90f6992f47e62c1775cae216b4012f630e07558f
ms.sourcegitcommit: 755d7bc0740573d73613cedcf79981ca3dc81c5e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/09/2018
---
# <a name="starting-windows-powershell"></a>Iniciar o Windows PowerShell
PowerShell é uma dll de motor de script que está incorporada em vários anfitriões.  O anfitrião mais comuns que iniciará são a linha de comandos interativa PowerShell.exe e ambiente PowerShell_ISE.exe interativa Scripting.

Para iniciar Windows PowerShell® no Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 e Windows 8, consulte [tarefas de gestão comuns e navegação](http://technet.microsoft.com/library/hh831491.aspx).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Como iniciar o Windows PowerShell em versões anteriores do Windows

Esta secção explica como iniciar o Windows PowerShell e Windows PowerShell Integrated Scripting Environment (ISE) no Windows® 7, Windows Server® 2008 R2 e Windows Server® 2008. Também explica como ativar a funcionalidade opcional para o ISE do Windows PowerShell no Windows PowerShell 2.0 no Windows Server® 2008 R2 e no Windows Server® 2008.

Utilize qualquer um dos seguintes métodos para iniciar a versão instalada do Windows PowerShell 3.0 ou Windows PowerShell 4.0, onde for aplicável.

#### <a name="from-the-start-menu"></a>No Menu Iniciar

- Clique em **iniciar**, tipo **PowerShell**e, em seguida, clique em **do Windows PowerShell**.
- Do **iniciar** menu, clique em **iniciar**, clique em **todos os programas**, clique em **acessórios**, clique em de **do Windows PowerShell**  pasta e, em seguida, clique em **do Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>Na linha de comandos

No Cmd.exe, o Windows PowerShell ou o ISE do Windows PowerShell, para iniciar o Windows PowerShell, escreva:

```
PowerShell
```

Também pode utilizar os parâmetros do programa PowerShell.exe para personalizar a sessão. Para obter mais informações, consulte [ajudar a linha de comandos PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>Com administração privilégios ("Executar como administrador")

Clique em **iniciar**, tipo **PowerShell**, faça duplo clique **do Windows PowerShell**e, em seguida, clique em **executar como administrador**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Como iniciar o ISE do Windows PowerShell em versões anteriores do Windows

Utilize qualquer um dos seguintes métodos para iniciar o ISE do Windows PowerShell.

#### <a name="from-the-start-menu"></a>No Menu Iniciar

- Clique em **iniciar**, tipo **ISE**e, em seguida, clique em **ISE do Windows PowerShell**.
- Do **iniciar** menu, clique em **iniciar**, clique em **todos os programas**, clique em **acessórios**, clique em de **do Windows PowerShell**  pasta e, em seguida, clique em **ISE do Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>Na linha de comandos

No Cmd.exe, o Windows PowerShell ou o ISE do Windows PowerShell, para iniciar o Windows PowerShell, escreva:

```
PowerShell_ISE
```

ou

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a>Com administração privilégios ("Executar como administrador")

Clique em **iniciar**, tipo **ISE**, faça duplo clique **ISE do Windows PowerShell**e, em seguida, clique em **executar como administrador**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Como ativar o ISE do Windows PowerShell em versões anteriores do Windows

No Windows PowerShell 4.0 e o Windows PowerShell 3.0, o ISE do Windows PowerShell está ativada por predefinição em todas as versões do Windows. Caso não ainda esteja ativado, Windows Management Framework 4.0 ou o Windows Management Framework 3.0 ativa o mesmo.

No Windows PowerShell 2.0, o ISE do Windows PowerShell está ativada por predefinição no Windows 7. No entanto, no Windows Server 2008 R2 e Windows Server 2008, é uma funcionalidade opcional.

Para ativar o ISE do Windows PowerShell no Windows PowerShell 2.0 no Windows Server 2008 R2 ou Windows Server 2008, utilize o procedimento seguinte.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Para ativar o Windows PowerShell Integrated Scripting Environment (ISE)

1. Inicie o Gestor de Servidor.
2. Clique em **funcionalidades** e, em seguida, clique em **adicionar funcionalidades**.
3. Em Selecionar funcionalidades, clique em Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="starting-the-32-bit-version-of-windows-powershell"></a>A iniciar a versão de 32 bits do Windows PowerShell

Quando instalar o Windows PowerShell no computador de 64 bits, **Windows PowerShell (x86)**, está instalada uma versão de 32 bits do Windows PowerShell para além da versão de 64 bits. Quando executar o Windows PowerShell, executa a versão de 64 bits por predefinição.

No entanto, ocasionalmente, poderá ter de executar **Windows PowerShell (x86)**, tal como quando estiver a utilizar um módulo que requer a versão de 32 bits ou quando estiverem a ligar remotamente a um computador de 32 bits.

Para iniciar uma versão de 32 bits do Windows PowerShell, utilize qualquer um dos seguintes procedimentos.

#### <a name="in-windows-server-2012-r2"></a>In Windows Server® 2012 R2

- No **iniciar** ecrã, escreva **Windows PowerShell (x86)**. Clique em de **Windows PowerShell x86** mosaico.
- No **Gestor de servidor**, do **ferramentas** menu, selecione **Windows PowerShell (x86)**.
- No ambiente de trabalho, mova o cursor para o canto superior direito, clique em **pesquisa**, tipo **PowerShell x86** e, em seguida, clique em **Windows PowerShell (x86)**.
- Linha de comandos, introduza:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>In Windows Server® 2012

- No **iniciar** ecrã, escreva **PowerShell** e, em seguida, clique em **Windows PowerShell (x86)**.
- No **Gestor de servidor**, do **ferramentas** menu, selecione **Windows PowerShell (x86)**.
- No ambiente de trabalho, mova o cursor para o canto superior direito, clique em **pesquisa**, tipo **PowerShell** e, em seguida, clique em **Windows PowerShell (x86)**.
- Linha de comandos, introduza:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>No Windows® 8.1

- No **iniciar** ecrã, escreva **Windows PowerShell (x86)**. Clique em de **Windows PowerShell x86** mosaico.
- Se estiver a executar [ferramentas de administração remota do servidor](http://go.microsoft.com/fwlink/?LinkID=304145) para Windows 8.1, pode também abrir o Windows PowerShell x86 a partir de **ManagerTools servidor** menu.
  Selecione **Windows PowerShell (x86)**.
- No ambiente de trabalho, mova o cursor para o canto superior direito, clique em **pesquisa**, tipo **PowerShell x86** e, em seguida, clique em **Windows PowerShell (x86)**.
- Linha de comandos, introduza:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>No Windows® 8

- No **iniciar** ecrã, mova o cursor para o canto superior direito, clique em **definições**, clique em **mosaicos**e, em seguida, mova o **Mostrar Ferramentas administrativas** controlo de deslize para Sim. Em seguida, escreva **PowerShell** e clique em **Windows PowerShell (x86)**.
- Se estiver a executar [ferramentas de administração remota do servidor](http://www.microsoft.com/download/details.aspx?id=28972) para o Windows 8, pode também abrir o Windows PowerShell x86 do **servidor ManagerTools** menu. Selecione **Windows PowerShell (x86)**.
- No **iniciar** ecrã ou ambiente de trabalho, escreva **PowerShell (x86)** e, em seguida, clique em **Windows PowerShell (x86)**.
- Linha de comandos, introduza:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`
