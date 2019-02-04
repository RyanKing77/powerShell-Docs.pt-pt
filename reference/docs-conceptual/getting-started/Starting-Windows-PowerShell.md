---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Iniciar o Windows PowerShell
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: 9184e8b0e508610e7f4775f1032f3a69c93bb8c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688323"
---
# <a name="starting-windows-powershell"></a>Iniciar o Windows PowerShell
O PowerShell é uma dll de mecanismo de script que é incorporada em vários anfitriões.  O anfitrião mais comuns que começa são a linha de comandos interativa PowerShell.exe e ambiente PowerShell_ISE.exe interativa de scripts.

Para iniciar Windows PowerShell® no Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 e Windows 8, consulte [tarefas de gestão comuns e navegação](https://technet.microsoft.com/library/hh831491.aspx).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Como iniciar o Windows PowerShell em versões anteriores do Windows

Esta secção explica como iniciar o Windows PowerShell e o Windows PowerShell Integrated Scripting Environment (ISE) no Windows® 7, Windows Server® 2008 R2 e Windows Server® 2008. Também explica como ativar a funcionalidade opcional para o Windows PowerShell ISE do Windows PowerShell 2.0 no Windows Server® 2008 R2 e Windows Server® 2008.

Utilize qualquer um dos seguintes métodos para iniciar a versão instalada do Windows PowerShell 3.0 ou o Windows PowerShell 4.0, quando aplicável.

#### <a name="from-the-start-menu"></a>No Menu Iniciar

- Clique em **começar**, tipo **PowerShell**e, em seguida, clique em **Windows PowerShell**.
- Do **começar** menu, clique em **iniciar**, clique em **todos os programas**, clique em **acessórios**, clique no **Windows PowerShell**  e, em seguida, clique **Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>No Prompt de comando

Na Cmd.exe, o Windows PowerShell ou o ISE do Windows PowerShell, para iniciar o Windows PowerShell, escreva:

```
PowerShell
```

Também pode utilizar os parâmetros do programa PowerShell.exe para personalizar a sessão. Para obter mais informações, consulte [a ajuda de linha de comandos PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>Com a administração de privilégios ("Executar como administrador")

Clique em **começar**, tipo **PowerShell**, clique com botão direito **Windows PowerShell**e, em seguida, clique em **executar como administrador**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Como iniciar o ISE do Windows PowerShell em versões anteriores do Windows

Utilize qualquer um dos seguintes métodos para iniciar o ISE do Windows PowerShell.

#### <a name="from-the-start-menu"></a>No Menu Iniciar

- Clique em **começar**, tipo **ISE**e, em seguida, clique em **ISE do Windows PowerShell**.
- Do **começar** menu, clique em **iniciar**, clique em **todos os programas**, clique em **acessórios**, clique no **Windows PowerShell**  e, em seguida, clique **ISE do Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>No Prompt de comando

Na Cmd.exe, o Windows PowerShell ou o ISE do Windows PowerShell, para iniciar o Windows PowerShell, escreva:

```
PowerShell_ISE
```

ou

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a>Com a administração de privilégios ("Executar como administrador")

Clique em **começar**, tipo **ISE**, clique com botão direito **ISE do Windows PowerShell**e, em seguida, clique em **executar como administrador**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Como ativar o ISE do Windows PowerShell em versões anteriores do Windows

No Windows PowerShell 4.0 e no Windows PowerShell 3.0, o ISE do Windows PowerShell está ativado por predefinição em todas as versões do Windows. Se não estiver já ativada, Windows Management Framework 4.0 ou Windows Management Framework 3.0 permite que ela.

No Windows PowerShell 2.0, o ISE do Windows PowerShell está ativado por predefinição no Windows 7. No entanto, no Windows Server 2008 R2 e Windows Server 2008, é uma funcionalidade opcional.

Para ativar o Windows PowerShell ISE do Windows PowerShell 2.0 no Windows Server 2008 R2 ou Windows Server 2008, utilize o procedimento seguinte.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Para ativar o Windows PowerShell Integrated Scripting Environment (ISE)

1. Inicie o Gestor de Servidores.
2. Clique em **funcionalidades** e, em seguida, clique em **adicionar funcionalidades**.
3. Em Selecionar funcionalidades, clique em Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="starting-the-32-bit-version-of-windows-powershell"></a>Iniciar a versão de 32 bits do Windows PowerShell

Quando instala o Windows PowerShell num computador de 64 bits **Windows PowerShell (x86)**, está instalada uma versão de 32 bits do Windows PowerShell, além da versão de 64 bits. Quando executa o Windows PowerShell, a versão de 64 bits é executada por predefinição.

No entanto, ocasionalmente, poderá ter de ser executado **Windows PowerShell (x86)**, como quando estiver a utilizar um módulo que requer a versão de 32 bits ou quando estiver a ligar remotamente a um computador de 32 bits.

Para iniciar uma versão de 32 bits do Windows PowerShell, utilize qualquer um dos seguintes procedimentos.

#### <a name="in-windows-server-2012-r2"></a>No Windows Server® 2012 R2

- Sobre o **começar** ecrã, escreva **(x86) do Windows PowerShell**. Clique nas **x86 do Windows PowerShell** mosaico.
- Na **Gestor de servidores**, da **ferramentas** menu, selecione **Windows PowerShell (x86)**.
- Na área de trabalho, mover o cursor para o canto superior direito, clique em **pesquisa**, tipo **PowerShell x86** e, em seguida, clique em **Windows PowerShell (x86)**.
- Por meio da linha de comandos, introduza: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>In Windows Server® 2012

- Sobre o **começar** ecrã, escreva **PowerShell** e, em seguida, clique em **(x86) do Windows PowerShell**.
- Na **Gestor de servidores**, da **ferramentas** menu, selecione **Windows PowerShell (x86)**.
- Na área de trabalho, mover o cursor para o canto superior direito, clique em **pesquisa**, tipo **PowerShell** e, em seguida, clique em **Windows PowerShell (x86)**.
- Por meio da linha de comandos, introduza: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>No Windows® 8.1

- Sobre o **começar** ecrã, escreva **(x86) do Windows PowerShell**. Clique nas **x86 do Windows PowerShell** mosaico.
- Se estiver a executar [ferramentas de administração remota do servidor](https://go.microsoft.com/fwlink/?LinkID=304145) para Windows 8.1, também pode abrir o Windows PowerShell x86 a partir do **servidor ManagerTools** menu.
  Selecione **Windows PowerShell (x86)**.
- Na área de trabalho, mover o cursor para o canto superior direito, clique em **pesquisa**, tipo **PowerShell x86** e, em seguida, clique em **Windows PowerShell (x86)**.
- Por meio da linha de comandos, introduza: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>No Windows® 8

- Na **começar** ecrã, mova o cursor para o canto superior direito, clique em **definições**, clique em **mosaicos**e, em seguida, mova o **Mostrar Ferramentas administrativas** controlo de deslize como Yes. Em seguida, escreva **PowerShell** e clique em **(x86) do Windows PowerShell**.
- Se estiver a executar [ferramentas de administração remota do servidor](https://www.microsoft.com/download/details.aspx?id=28972) para Windows 8, também pode abrir o Windows PowerShell x86 a partir do **servidor ManagerTools** menu. Selecione **Windows PowerShell (x86)**.
- Sobre o **começar** ecrã ou ambiente de trabalho, escreva **PowerShell (x86)** e, em seguida, clique em **(x86) do Windows PowerShell**.
- Por meio da linha de comandos, introduza: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`