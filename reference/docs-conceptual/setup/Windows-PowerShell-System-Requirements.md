---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Requisitos de Sistema do Windows PowerShell
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
ms.openlocfilehash: 74c65a97a30227997c48a23c42b0431189f9ed76
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/25/2018
---
# <a name="windows-powershell-system-requirements"></a>Requisitos de Sistema do Windows PowerShell
Este tópico lista os requisitos de sistema para o Windows PowerShell 3.0, o Windows PowerShell 4.0 e o Windows PowerShell 5.0 e para funcionalidades especiais, como o Windows PowerShell Integrated Scripting Environment (ISE), comandos CIM e fluxos de trabalho.

Windows® 8.1 e Windows Server® 2012 R2 incluem todos os programas necessários. Este tópico foi concebido para utilizadores das versões anteriores do Windows.

## <a name="operating-system-requirements"></a>Requisitos do sistema operativo
Windows PowerShell 5.0 é executado nas seguintes versões do Windows.

- Windows Server 2016, instalados por predefinição

- Instalar o Windows Server 2012 R2, [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para executar o Windows PowerShell 5.0

- Instalar o Windows Server 2012, [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para executar o Windows PowerShell 5.0

- Instalar o Windows Server 2008 R2 com Service Pack 1, [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para executar o Windows PowerShell 5.0

- Windows 8.1

- Instalar o Windows 7 com Service Pack 1, [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para executar o Windows PowerShell 5.0

Windows PowerShell 4.0 é executado nas seguintes versões do Windows.

- Windows 8.1, instalados por predefinição

- Windows Server 2012 R2, instalados por predefinição

- Instalar o Windows® 7 com Service Pack 1, [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) para executar o Windows PowerShell 4.0

- Instalar o Windows Server® 2008 R2 com Service Pack 1, [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) para executar o Windows PowerShell 4.0

Windows PowerShell 3.0 é executado nas seguintes versões do Windows.

- Windows 8, instalados por predefinição

- Windows Server 2012, instalados por predefinição

- Instalar o Windows® 7 com Service Pack 1, [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) para executar o Windows PowerShell 3.0

- Instalar o Windows Server® 2008 R2 com Service Pack 1, [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) para executar o Windows PowerShell 3.0

- Instalar o Windows Server 2008 com Service Pack 2, [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) para executar o Windows PowerShell 3.0

## <a name="microsoft-net-framework-requirements"></a>Requisitos do Microsoft .NET Framework
Windows PowerShell 5.0 requer a instalação completa do Microsoft .NET Framework 4.5. Windows 8.1 e Windows Server 2012 R2 incluem o Microsoft .NET Framework 4.5 por predefinição.

Windows PowerShell 4.0 requer a instalação completa do Microsoft .NET Framework 4.5. Windows 8.1 e Windows Server 2012 R2 incluem o Microsoft .NET Framework 4.5 por predefinição.

Windows PowerShell 3.0 requer a instalação completa do Microsoft .NET Framework 4. Windows 8 e Windows Server 2012 incluem o Microsoft .NET Framework 4.5 por predefinição, o que cumpre este requisito.

Para instalar o Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe), consulte [o Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkID=242919) no Microsoft Download Center.

Para instalar a instalação completa do Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe), consulte [o Microsoft .NET Framework 4 (programa de instalação Web)](http://go.microsoft.com/fwlink/?LinkID=212931) no Microsoft Download Center.

## <a name="windows-management-framework-40"></a>Windows Management Framework 4.0
Windows PowerShell 5.0 requer o Windows Management Framework 4.0 ser pré-instalado na Windows Server 2008 R2 SP1 e Windows 7 SP1.

## <a name="ws-management-30"></a>WS-Management 3.0
Windows PowerShell 3.0 e o Windows PowerShell 4.0 necessitam de WS-Management 3.0, que suporta o serviço WinRM e o protocolo de WSMan. Este programa está incluído no Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 e o Windows Management Framework 3.0.

## <a name="windows-management-instrumentation-30"></a>Windows Management Instrumentation 3.0
Windows PowerShell 3.0 e o Windows PowerShell 4.0 requerem 3.0 de Windows Management Instrumentation (WMI). Este programa está incluído no Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 e o Windows Management Framework 3.0. Se este programa não está instalado no computador, as funcionalidades que requerem o WMI, por exemplo, comandos CIM, não são executados.

## <a name="common-language-runtime-40"></a>Common Language Runtime 4.0
Windows PowerShell 3.0, o Windows PowerShell 4.0 e o Windows PowerShell 5.0 são compilados contra o Common Language Runtime (CLR) 4.0.

## <a name="graphical-user-interface-requirements"></a>Requisitos de Interface de utilizador gráfica
O Windows PowerShell é uma aplicação baseada na consola que não necessita de uma interface gráfica do utilizador. Como tal, é-bem adequada para computadores que não tenham ecrãs ou monitores ou uma interface de utilizador, tais como as opções de instalação Server Core do Windows Server 2012 R2 ou Windows Server 2012.

No entanto, alguns itens, tais como o seguinte, necessitam de uma interface gráfica do utilizador. Para obter detalhes, consulte o tópico de ajuda para cada item.

- Windows PowerShell Integrated Scripting Environment (ISE)

- Cmdlets

    1.  [Out-GridView](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview)

    2.  [Mostrar comando](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Show-Command)

    3.  [Mostrar ControlPanelItem](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Show-ControlPanelItem)

    4.  [Mostrar-registo de eventos](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Show-EventLog)

- Parâmetros

    1.  **ShowWindow** parâmetro o [Get-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.

    2.  **ShowSecurityDescriptorUI** parâmetro o [Register-PSSessionConfiguration](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) e [Set-PSSessionConfiguration](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration) cmdlets.

## <a name="windows-powershell-engine-requirements"></a>Requisitos do Windows PowerShell motor
Windows PowerShell 4.0 está concebido para ser retrocompatíveis com o Windows PowerShell 3.0 e o Windows PowerShell 2.0. Os cmdlets, fornecedores, snap-ins, módulos e scripts escritos para o Windows PowerShell 2.0 e Windows PowerShell 3.0 executam inalterados no Windows PowerShell 4.0.

No entanto, devido a uma alteração na política de ativação de tempo de execução no Microsoft .NET Framework 4, alojar programas do Windows PowerShell que foram escritos para o Windows PowerShell 2.0 e compilados com o Common Language Runtime (CLR) 2.0 não é possível executar sem modificação no Windows PowerShell 3.0, que é compilada com CLR 4.0.

O motor do Windows PowerShell 2.0 requer o Microsoft .NET Framework 2.0.50727 no mínimo. Este requisito é cumprido ao Microsoft .NET Framework 3.5 Service Pack 1. Este requisito é cumprido não pela Microsoft .NET Framework 4 e versões posteriores do Microsoft .NET Framework.

Para obter informações sobre a adição ou instalar o motor do Windows PowerShell 2.0 e adicionar ou instalar as versões necessárias do Microsoft .NET Framework, consulte [instalar o motor do Windows PowerShell 2.0](Installing-the-Windows-PowerShell-2.0-Engine.md). Para obter informações sobre a iniciar o motor do Windows PowerShell 2.0, consulte [iniciar o motor do Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="windows-preinstallation-environment"></a>Ambiente de Pré-instalação do Windows
O Windows PowerShell 2.0, o Windows PowerShell 3.0 e o Windows PowerShell 4.0 executam no ambiente de pré-instalação do Windows (Windows PE). No entanto, os seguintes cmdlets não são suportados.

- [Cmdlets de serviço (BITS) de transferência inteligente em segundo plano](http://go.microsoft.com/fwlink/?LinkId=257514)

- [Get-EventLog](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Get-EventLog)

- [Get-WinEvent](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)

- [Save-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Save-Help)

- [Update-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Update-Help)

Além disso, o **WinRM** serviço não está presente no Windows PE.

## <a name="see-also"></a>Consulte Também
- [Introdução ao Windows PowerShell](../getting-started/Getting-Started-with-Windows-PowerShell.md)
- [Instalar o Windows PowerShell](Installing-Windows-PowerShell.md)
- [A partir do Windows PowerShell](Starting-Windows-PowerShell.md)