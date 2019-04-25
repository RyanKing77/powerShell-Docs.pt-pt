---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Notas de Versão do WMF 5.1
ms.openlocfilehash: 61ca854cf8f26a9e96c6c5b5c06f6b54d08fb4ea
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055586"
---
# <a name="windows-management-framework-wmf-51-release-notes"></a>Notas de versão do Windows Management Framework (WMF) 5.1

WMF 5.1 inclui os componentes PowerShell, WMI, WinRM e registo de inventário de Software (SIL) que foram lançados com o Windows Server 2016.
O WMF 5.1 pode ser instalado no Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 e 2012 R2 e oferece várias melhorias em relação ao WMF 5.0 RTM, incluindo:

- Novos cmdlets: grupos e utilizadores; Get-ComputerInfo
- Melhorias do PowerShellGet com a imposição de módulos assinados e a instalação de módulos JEA
- Adicionado suporte ao PackageManagement para Contentores, Configuração CBS, configuração com base em EXE, pacotes CAB
- Melhorias na depuração para classes DSC e PowerShell
- Melhorias de segurança, incluindo a imposição de módulos assinados de catálogo provenientes do Servidor de Solicitação e ao utilizar os cmdlets PowerShellGet
- Respostas a vários pedidos e problemas de utilizadores

**Notas importantes:**

- **WMF 5.1 requer o .NET Framework 4.5.2** (ou superior). Instalação será concluída com êxito, mas os principais recursos irão falhar se a .NET 4.5.2 (ou superior) não está instalado. As instruções estão disponíveis no [instalar e configurar o WMF 5.1](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure) tópico.
- Pré-visualização do WMF 5.1 têm de ser desinstalada antes de instalar a versão do WMF 5.1 RTM.
- WMF 5.1 pode ser instalado diretamente ao longo do WMF 5.0 ou WMF 4.0.
- É __não é necessário__ para instalar o WMF 4.0 antes de instalar o WMF 5.1 no Windows 7 e Windows Server 2008 R2. Isso foi um problema para a versão de pré-visualização do WMF 5.1 e foi resolvido.
