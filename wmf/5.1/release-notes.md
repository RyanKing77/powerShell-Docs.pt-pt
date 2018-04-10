---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Notas de Versão do WMF 5.1
ms.openlocfilehash: eb22267c1af28a9fcdd049c76d363fff687f6167
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="windows-management-framework-wmf-51-release-notes"></a>Notas de versão do Windows Management Framework (WMF) 5.1 #

WMF 5.1 inclui os componentes do PowerShell, WMI, WinRM e registo de inventário de Software (SIL) que foram lançados com o Windows Server 2016.
O WMF 5.1 pode ser instalado no Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 e 2012 R2 e oferece várias melhorias em relação ao WMF 5.0 RTM, incluindo:

- Novos cmdlets: grupos e utilizadores; Get-ComputerInfo
- Melhorias do PowerShellGet com a imposição de módulos assinados e a instalação de módulos JEA
- Adicionado suporte ao PackageManagement para Contentores, Configuração CBS, configuração com base em EXE, pacotes CAB
- Melhorias na depuração para classes DSC e PowerShell
- Melhorias de segurança, incluindo a imposição de módulos assinados de catálogo provenientes do Servidor de Solicitação e ao utilizar os cmdlets PowerShellGet
- Respostas a vários pedidos e problemas de utilizadores

**Notas importantes:**

- **WMF 5.1 exige o .NET Framework 4.5.2** (ou superior). Instalação será bem-sucedida, mas as principais funcionalidades irão falhar se a .NET 4.5.2 (ou superior) não está instalado. Estão disponíveis nas instruções de [instalar e configurar o WMF 5.1 ](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure) tópico.
- Pré-visualização do WMF 5.1 tem de ser desinstalado antes de instalar o WMF 5.1 RTM.
- WMF 5.1 pode ser instalado diretamente ao longo do WMF 5.0 ou WMF 4.0.
- É __não necessário__ para instalar o WMF 4.0 antes de instalar o WMF 5.1 no Windows 7 e Windows Server 2008 R2. Se um problema para a versão de pré-visualização do WMF 5.1 e foi resolvido.