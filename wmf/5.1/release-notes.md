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
# <a name="windows-management-framework-wmf-51-release-notes"></a><span data-ttu-id="a04cc-103">Notas de versão do Windows Management Framework (WMF) 5.1</span><span class="sxs-lookup"><span data-stu-id="a04cc-103">Windows Management Framework (WMF) 5.1 Release Notes</span></span> #

<span data-ttu-id="a04cc-104">WMF 5.1 inclui os componentes do PowerShell, WMI, WinRM e registo de inventário de Software (SIL) que foram lançados com o Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="a04cc-104">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>
<span data-ttu-id="a04cc-105">WMF 5.1 pode ser instalado no Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 e 2012 R2 e fornece um número de melhorias ao longo do WMF 5.0 RTM, incluindo:</span><span class="sxs-lookup"><span data-stu-id="a04cc-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="a04cc-106">Novos cmdlets: utilizadores e grupos; locais Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="a04cc-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="a04cc-107">PowerShellGet melhoramentos incluem impor módulos assinados e instalar módulos JEA</span><span class="sxs-lookup"><span data-stu-id="a04cc-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="a04cc-108">PackageManagement foi adicionado suporte para a configuração contentores, configuração CBS, com base em EXE, pacotes CAB</span><span class="sxs-lookup"><span data-stu-id="a04cc-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="a04cc-109">Melhoramentos de depuração para classes de DSC e PowerShell</span><span class="sxs-lookup"><span data-stu-id="a04cc-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="a04cc-110">Melhoramentos de segurança, incluindo a imposição de módulos assinada de catálogo proveniência do servidor de solicitação e ao utilizar os cmdlets de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a04cc-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="a04cc-111">Respostas para um número de pedidos de utilizador e problemas</span><span class="sxs-lookup"><span data-stu-id="a04cc-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="a04cc-112">**Notas importantes:**</span><span class="sxs-lookup"><span data-stu-id="a04cc-112">**Important notes:**</span></span>

- <span data-ttu-id="a04cc-113">**WMF 5.1 exige o .NET Framework 4.5.2** (ou superior).</span><span class="sxs-lookup"><span data-stu-id="a04cc-113">**WMF 5.1 requires the .NET Framework 4.5.2** (or above).</span></span> <span data-ttu-id="a04cc-114">Instalação será bem-sucedida, mas as principais funcionalidades irão falhar se a .NET 4.5.2 (ou superior) não está instalado.</span><span class="sxs-lookup"><span data-stu-id="a04cc-114">Installation will succeed, but key features will fail if .NET 4.5.2 (or above) is not installed.</span></span> <span data-ttu-id="a04cc-115">Estão disponíveis nas instruções de [instalar e configurar o WMF 5.1 ](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure) tópico.</span><span class="sxs-lookup"><span data-stu-id="a04cc-115">Instructions are available in the [Install and Configure WMF 5.1 ](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure) topic.</span></span>
- <span data-ttu-id="a04cc-116">Pré-visualização do WMF 5.1 tem de ser desinstalado antes de instalar o WMF 5.1 RTM.</span><span class="sxs-lookup"><span data-stu-id="a04cc-116">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="a04cc-117">WMF 5.1 pode ser instalado diretamente ao longo do WMF 5.0 ou WMF 4.0.</span><span class="sxs-lookup"><span data-stu-id="a04cc-117">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="a04cc-118">É __não necessário__ para instalar o WMF 4.0 antes de instalar o WMF 5.1 no Windows 7 e Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="a04cc-118">It is __not required__ to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="a04cc-119">Se um problema para a versão de pré-visualização do WMF 5.1 e foi resolvido.</span><span class="sxs-lookup"><span data-stu-id="a04cc-119">That was an issue for the WMF 5.1 Preview release, and has been resolved.</span></span>  


