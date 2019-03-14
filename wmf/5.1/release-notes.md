---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Notas de Versão do WMF 5.1
ms.openlocfilehash: 61ca854cf8f26a9e96c6c5b5c06f6b54d08fb4ea
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795016"
---
# <a name="windows-management-framework-wmf-51-release-notes"></a><span data-ttu-id="4a3d6-103">Notas de versão do Windows Management Framework (WMF) 5.1</span><span class="sxs-lookup"><span data-stu-id="4a3d6-103">Windows Management Framework (WMF) 5.1 Release Notes</span></span>

<span data-ttu-id="4a3d6-104">WMF 5.1 inclui os componentes PowerShell, WMI, WinRM e registo de inventário de Software (SIL) que foram lançados com o Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="4a3d6-104">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>
<span data-ttu-id="4a3d6-105">O WMF 5.1 pode ser instalado no Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 e 2012 R2 e oferece várias melhorias em relação ao WMF 5.0 RTM, incluindo:</span><span class="sxs-lookup"><span data-stu-id="4a3d6-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="4a3d6-106">Novos cmdlets: grupos e utilizadores; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="4a3d6-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="4a3d6-107">Melhorias do PowerShellGet com a imposição de módulos assinados e a instalação de módulos JEA</span><span class="sxs-lookup"><span data-stu-id="4a3d6-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="4a3d6-108">Adicionado suporte ao PackageManagement para Contentores, Configuração CBS, configuração com base em EXE, pacotes CAB</span><span class="sxs-lookup"><span data-stu-id="4a3d6-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="4a3d6-109">Melhorias na depuração para classes DSC e PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a3d6-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="4a3d6-110">Melhorias de segurança, incluindo a imposição de módulos assinados de catálogo provenientes do Servidor de Solicitação e ao utilizar os cmdlets PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="4a3d6-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="4a3d6-111">Respostas a vários pedidos e problemas de utilizadores</span><span class="sxs-lookup"><span data-stu-id="4a3d6-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="4a3d6-112">**Notas importantes:**</span><span class="sxs-lookup"><span data-stu-id="4a3d6-112">**Important notes:**</span></span>

- <span data-ttu-id="4a3d6-113">**WMF 5.1 requer o .NET Framework 4.5.2** (ou superior).</span><span class="sxs-lookup"><span data-stu-id="4a3d6-113">**WMF 5.1 requires the .NET Framework 4.5.2** (or above).</span></span> <span data-ttu-id="4a3d6-114">Instalação será concluída com êxito, mas os principais recursos irão falhar se a .NET 4.5.2 (ou superior) não está instalado.</span><span class="sxs-lookup"><span data-stu-id="4a3d6-114">Installation will succeed, but key features will fail if .NET 4.5.2 (or above) is not installed.</span></span> <span data-ttu-id="4a3d6-115">As instruções estão disponíveis no [instalar e configurar o WMF 5.1](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure) tópico.</span><span class="sxs-lookup"><span data-stu-id="4a3d6-115">Instructions are available in the [Install and Configure WMF 5.1](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure) topic.</span></span>
- <span data-ttu-id="4a3d6-116">Pré-visualização do WMF 5.1 têm de ser desinstalada antes de instalar a versão do WMF 5.1 RTM.</span><span class="sxs-lookup"><span data-stu-id="4a3d6-116">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="4a3d6-117">WMF 5.1 pode ser instalado diretamente ao longo do WMF 5.0 ou WMF 4.0.</span><span class="sxs-lookup"><span data-stu-id="4a3d6-117">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="4a3d6-118">É __não é necessário__ para instalar o WMF 4.0 antes de instalar o WMF 5.1 no Windows 7 e Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="4a3d6-118">It is __not required__ to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="4a3d6-119">Isso foi um problema para a versão de pré-visualização do WMF 5.1 e foi resolvido.</span><span class="sxs-lookup"><span data-stu-id="4a3d6-119">That was an issue for the WMF 5.1 Preview release, and has been resolved.</span></span>
