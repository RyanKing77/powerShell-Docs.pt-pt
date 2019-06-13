---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Instalar o Motor do Windows PowerShell 2.0
ms.openlocfilehash: a2b78755e7e44e2523baee5477fadc94eab485b1
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030956"
---
# <a name="installing-the-windows-powershell-20-engine"></a>Instalar o Motor do Windows PowerShell 2.0
Este tópico explica como instalar o motor do Windows PowerShell 2.0.

Windows PowerShell 3.0 foi concebido para compatibilidade com o Windows PowerShell 2.0. Cmdlets, fornecedores, snap-ins, módulos e scripts escritos para o Windows PowerShell 2.0 continuar em execução no Windows PowerShell 3.0 e no Windows PowerShell 4.0. No entanto, devido a uma alteração na política de ativação de tempo de execução no Microsoft .NET Framework 4, programas de anfitrião do Windows PowerShell que foram escritos para o Windows PowerShell 2.0 e compilados com o tempo de execução do CLR (Common Language) 2.0 não é possível executar sem modificações no mais tarde versões do Windows PowerShell, que é compilado com o CLR 4.0.

Para manter a compatibilidade com versões anteriores com comandos e programas de anfitrião que são afetados por essas alterações, os motores do Windows PowerShell 2.0, o Windows PowerShell 3.0 e o Windows PowerShell 4.0 destinam-se para ser executado lado a lado. Além disso, o motor do Windows PowerShell 2.0 está incluído no Windows Server 2012 R2, Windows 8.1, Windows 8, Windows Server 2012 e Windows Management Framework 3.0. O motor do Windows PowerShell 2.0 se destina a ser utilizado apenas quando um script existente ou programa de anfitrião não pode ser executado porque ele não é compatível com o Windows PowerShell 3.0, Windows PowerShell 4.0 ou Microsoft .NET Framework 4. Nesses casos devem ser raros.

O motor do Windows PowerShell 2.0 é uma funcionalidade opcional do Windows Server 2012 R2, Windows 8.1, Windows® 8 e Windows Server® 2012. Em versões anteriores do Windows, ao instalar o Windows Management Framework 3.0, a instalação do Windows PowerShell 3.0 completamente substitui a instalação do Windows PowerShell 2.0 no diretório de instalação do Windows PowerShell. No entanto, o motor do Windows PowerShell 2.0 é mantido.

Para obter informações sobre como iniciar o motor do Windows PowerShell 2.0, consulte [iniciar o motor do Windows PowerShell 2.0](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-windows-81-and-windows-8"></a>No Windows 8.1 e Windows 8
No Windows 8.1 e Windows 8, a funcionalidade do motor do Windows PowerShell 2.0 está ativada por predefinição. No entanto, para usá-lo, terá de ativar a opção para Microsoft .NET Framework 3.5, que requer. Esta secção também explica como ativar a funcionalidade do motor do Windows PowerShell 2.0 e desativar.

#### <a name="to-turn-on-net-framework-35"></a>Para ativar o .NET Framework 3.5

1. Sobre o **começar** ecrã, escreva **funcionalidades do Windows**.

2. Sobre o **aplicações** barra, clique em **definições**e, em seguida, clique em **ou desativar as funcionalidades de ativar o Windows**.

3. Na **funcionalidades do Windows** , clique em **.NET Framework 3.5 (inclui .NET 2.0 e 3.0** para selecioná-lo.

    Quando seleciona **.NET Framework 3.5 (inclui .NET 2.0 e 3.0**, a caixa preenche para indicar que apenas uma parte da funcionalidade está selecionada. No entanto, isso é suficiente para o mecanismo do Windows PowerShell 2.0.

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a>Para ativar o motor do Windows PowerShell 2.0 e desativar

1. Sobre o **começar** ecrã, escreva **funcionalidades do Windows**.

2. Sobre o **aplicações** barra, clique em **definições**e, em seguida, clique em **ou desativar as funcionalidades de ativar o Windows**.

3. Na **funcionalidades do Windows** caixa, expanda o **Windows PowerShell 2.0** nó e clique no **motor do Windows PowerShell 2.0** caixa para selecionar ou desmarcá-lo.

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a>No Windows Server 2012 R2 e Windows Server 2012
Utilize os procedimentos seguintes para adicionar o motor do Windows PowerShell 2.0 e funcionalidades do Microsoft .NET Framework 3.5. O motor do Windows PowerShell 2.0 requer o Microsoft .NET Framework 2.0.50727 no mínimo. Este requisito foi cumprido pelo Microsoft .NET Framework 3.5.

#### <a name="to-add-the-net-framework-35-feature"></a>Para adicionar a funcionalidade do .NET Framework 3.5

1. Na **Gestor de servidores**, da **gerir** menu, selecione **adicionar funções e funcionalidades**.

    Ou no **Gestor de servidores**, clique em **todos os servidores**, um nome de servidor com o botão direito e, em seguida, selecione **adicionar funções e funcionalidades**.

2. Sobre o **tipo de instalação** página, selecione **instalação baseada em funções ou baseada em recursos**.

3. Sobre o **funcionalidades** página, expanda o **funcionalidades do .NET 3.5 Framework** nó e selecione **.NET Framework 3.5 (inclui .NET 2.0 e 3.0)** .

    As outras opções desse nó não são necessárias para o motor do Windows PowerShell 2.0.

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a>Para adicionar a funcionalidade do motor do Windows PowerShell 2.0

- Na **Gestor de servidores**, da **gerir** menu, selecione **adicionar funções e funcionalidades**.

    Ou **Gestor de servidores**, clique em **todos os servidores**, um nome de servidor com o botão direito e, em seguida, selecione **adicionar funções e funcionalidades**.

- Sobre o **tipo de instalação** página, selecione **instalação baseada em funções ou baseada em recursos**.

- Sobre o **funcionalidades** página, expanda o **(instalado) do Windows PowerShell** nó e selecione **motor do Windows PowerShell 2.0**.

Para obter informações sobre como iniciar o motor do Windows PowerShell 2.0, consulte [iniciar o motor do Windows PowerShell 2.0](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-earlier-systems"></a>Em sistemas anteriores
O [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) pacote que instala o Windows PowerShell 4.0 no Windows 7, Windows Server 2008 R2 e Windows Server 2012, inclui o mecanismo do Windows PowerShell 2.0. O motor do Windows PowerShell 2.0 está ativado e pronto a utilizar, se necessário, sem instalação adicionais, instalação ou configuração.

O pacote do Windows Management Framework 3.0 que instala o Windows PowerShell 3.0 no Windows 7, Windows Server 2008 R2 e Windows Server 2008, inclui o mecanismo do Windows PowerShell 2.0. O motor do Windows PowerShell 2.0 está ativado e pronto a utilizar, se necessário, sem instalação adicionais, instalação ou configuração.

## <a name="see-also"></a>Veja Também
- [Requisitos de sistema do PowerShell do Windows](Windows-PowerShell-System-Requirements.md)
- [Instalar o Windows PowerShell](Installing-Windows-PowerShell.md)
- [Iniciar o Windows PowerShell](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
- [Iniciar o Motor do Windows PowerShell 2.0](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md)
