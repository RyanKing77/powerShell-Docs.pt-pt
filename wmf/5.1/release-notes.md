---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
title: "Notas de versão do WMF 5.1"
ms.openlocfilehash: ce9bc7791facfcc2cce9468689e88a26154bda7d
ms.sourcegitcommit: 3f49bd2e0b786e69c71393c00ad85d05a8466753
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/04/2017
---
# <a name="windows-management-framework-wmf-51-release-notes"></a>Notas de versão do Windows Management Framework (WMF) 5.1 #

WMF 5.1 inclui os componentes do PowerShell, WMI, WinRM e registo de inventário de Software (SIL) que foram lançados com o Windows Server 2016.
WMF 5.1 pode ser instalado no Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 e 2012 R2 e fornece um número de melhorias ao longo do WMF 5.0 RTM, incluindo:

- Novos cmdlets: utilizadores e grupos; locais Get-ComputerInfo
- PowerShellGet melhoramentos incluem impor módulos assinados e instalar módulos JEA
- PackageManagement foi adicionado suporte para a configuração contentores, configuração CBS, com base em EXE, pacotes CAB
- Melhoramentos de depuração para classes de DSC e PowerShell
- Melhoramentos de segurança, incluindo a imposição de módulos assinada de catálogo proveniência do servidor de solicitação e ao utilizar os cmdlets de PowerShellGet
- Respostas para um número de pedidos de utilizador e problemas

**Notas importantes:**

- **WMF 5.1 exige o .NET Framework 4.5.2** (ou superior). Instalação será bem-sucedida, mas as principais funcionalidades irão falhar se a .NET 4.5.2 (ou superior) não está instalado. Estão disponíveis nas instruções de [instalar e configurar o WMF 5.1 ](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure) tópico.
- Pré-visualização do WMF 5.1 tem de ser desinstalado antes de instalar o WMF 5.1 RTM.
- WMF 5.1 pode ser instalado diretamente ao longo do WMF 5.0 ou WMF 4.0.
- É __não necessário__ para instalar o WMF 4.0 antes de instalar o WMF 5.1 no Windows 7 e Windows Server 2008 R2. Se um problema para a versão de pré-visualização do WMF 5.1 e foi resolvido.  


