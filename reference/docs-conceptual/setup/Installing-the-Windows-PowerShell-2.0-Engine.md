---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Instalar o motor do Windows PowerShell 2.0
ms.assetid: 82928f2b-f96a-4ae6-a0d0-6e7b181da308
ms.openlocfilehash: ff6c2b52b8948472ace3ee35cd4c6aa2dbf46c25
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="installing-the-windows-powershell-20-engine"></a>Instalar o motor do Windows PowerShell 2.0
Este tópico explica como instalar o motor do Windows PowerShell 2.0.

Windows PowerShell 3.0 está concebido para ser retrocompatíveis com o Windows PowerShell 2.0. Os cmdlets, fornecedores, snap-ins, módulos e scripts escritos para o Windows PowerShell 2.0 executam inalterados no Windows PowerShell 3.0 e o Windows PowerShell 4.0. No entanto, devido a uma alteração na política de ativação de tempo de execução no Microsoft .NET Framework 4, alojar programas do Windows PowerShell que foram escritos para o Windows PowerShell 2.0 e compilados com o Common Language Runtime (CLR) 2.0 não é possível executar sem modificação no mais tarde versões do Windows PowerShell, que é compilada com CLR 4.0.

Para manter a compatibilidade com versões anteriores com comandos e programas de anfitrião que são afetados por estas alterações, os motores do Windows PowerShell 2.0, Windows PowerShell 3.0 e 4.0 do Windows PowerShell foram concebidos para executar lado a lado. Além disso, o motor do Windows PowerShell 2.0 está incluído no Windows Server 2012 R2, Windows 8.1, Windows 8, Windows Server 2012 e Windows Management Framework 3.0. O motor do Windows PowerShell 2.0 se destina a ser utilizado apenas quando um script existente ou não é possível executar o programa de anfitrião porque é incompatível com o Windows PowerShell 3.0, o Windows PowerShell 4.0 ou o Microsoft .NET Framework 4. Nestes casos deverão estar raro.

O motor do Windows PowerShell 2.0 é uma funcionalidade opcional do Windows Server 2012 R2, Windows 8.1, Windows® 8 e Windows Server® 2012. Em versões anteriores do Windows, ao instalar o Windows Management Framework 3.0, a instalação do Windows PowerShell 3.0 completamente substitui o a instalação do Windows PowerShell 2.0 no diretório de instalação do Windows PowerShell. No entanto, o motor do Windows PowerShell 2.0 é mantido.

Para obter informações sobre a iniciar o motor do Windows PowerShell 2.0, consulte [iniciar o motor do Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-windows-81-and-windows-8"></a>No Windows 8.1 e Windows 8
No Windows 8.1 e Windows 8, a funcionalidade de motor do Windows PowerShell 2.0 está ativada por predefinição. No entanto, para utilizá-la, terá de ativar a opção para o Microsoft .NET Framework 3.5, que requer. Esta secção também explica como ativar a funcionalidade de motor do Windows PowerShell 2.0 e desativar.

#### <a name="to-turn-on-net-framework-35"></a>Para ativar o .NET Framework 3.5

1. No **iniciar** ecrã, escreva **funcionalidades do Windows**.

2. No **aplicações** barra, clique em **definições**e, em seguida, clique em **ativar funcionalidades do Windows ou desativar**.

3. No **funcionalidades do Windows** , clique em **.NET Framework 3.5 (inclui .NET 2.0 e 3.0** para selecioná-lo.

    Quando seleciona **.NET Framework 3.5 (inclui .NET 2.0 e 3.0**, a caixa se preenche para indicar que apenas uma parte da funcionalidade está selecionada. No entanto, isto é suficiente para o motor do Windows PowerShell 2.0.

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a>Para ativar o motor do Windows PowerShell 2.0 e desativar

1. No **iniciar** ecrã, escreva **funcionalidades do Windows**.

2. No **aplicações** barra, clique em **definições**e, em seguida, clique em **ativar funcionalidades do Windows ou desativar**.

3. No **funcionalidades do Windows** caixa, expanda o **Windows PowerShell 2.0** nó e clique no **motor do Windows PowerShell 2.0** caixa para selecionar ou desmarcá-lo.

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a>No Windows Server 2012 R2 e Windows Server 2012
Utilize os procedimentos seguintes para adicionar o motor do Windows PowerShell 2.0 e funcionalidades do Microsoft .NET Framework 3.5. O motor do Windows PowerShell 2.0 requer o Microsoft .NET Framework 2.0.50727 no mínimo. Este requisito é cumprido pelo Microsoft .NET Framework 3.5.

#### <a name="to-add-the-net-framework-35-feature"></a>Para adicionar a funcionalidade .NET Framework 3.5

1. No **Gestor de servidor**, do **gerir** menu, selecione **para adicionar funções e funcionalidades**.

    Ou no **Gestor de servidor**, clique em **todos os servidores**, um nome de servidor com o botão direito e, em seguida, selecione **para adicionar funções e funcionalidades**.

2. No **tipo de instalação** página, selecione **instalação baseada em funções ou baseada em funcionalidade**.

3. No **funcionalidades** página, expanda o **funcionalidades do .NET 3.5 Framework** nó e selecione **.NET Framework 3.5 (inclui .NET 2.0 e 3.0)**.

    As outras opções desse nó não são necessárias para o motor do Windows PowerShell 2.0.

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a>Para adicionar a funcionalidade de motor do Windows PowerShell 2.0

- No **Gestor de servidor**, do **gerir** menu, selecione **para adicionar funções e funcionalidades**.

    Ou **Gestor de servidor**, clique em **todos os servidores**, um nome de servidor com o botão direito e, em seguida, selecione **para adicionar funções e funcionalidades**.

- No **tipo de instalação** página, selecione **instalação baseada em funções ou baseada em funcionalidade**.

- No **funcionalidades** página, expanda o **(instalada) do Windows PowerShell** nó e selecione **motor do Windows PowerShell 2.0**.

Para obter informações sobre a iniciar o motor do Windows PowerShell 2.0, consulte [iniciar o motor do Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-earlier-systems"></a>Em sistemas anteriores
O [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) pacote instala o Windows PowerShell 4.0 no Windows 7, Windows Server 2008 R2 e Windows Server 2012, inclui o motor do Windows PowerShell 2.0. O motor do Windows PowerShell 2.0 está ativado e pronto a utilizar, se necessário, sem configuração, a configuração ou instalação adicionais.

O pacote do Windows Management Framework 3.0 que instala no Windows 7, Windows Server 2008 R2 e Windows Server 2008, o Windows PowerShell 3.0 inclui o motor do Windows PowerShell 2.0. O motor do Windows PowerShell 2.0 está ativado e pronto a utilizar, se necessário, sem configuração, a configuração ou instalação adicionais.

## <a name="see-also"></a>Consulte Também
- [Requisitos de sistema do PowerShell do Windows](Windows-PowerShell-System-Requirements.md)
- [Instalar o Windows PowerShell](Installing-Windows-PowerShell.md)
- [A partir do Windows PowerShell](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
- [A iniciar o motor do Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md)

