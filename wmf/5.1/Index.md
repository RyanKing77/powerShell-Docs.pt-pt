---
ms.date: 08/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Notas de Versão do WMF 5.1
ms.openlocfilehash: dd68f101e6f21256f966f7472dabc273a475a25e
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795339"
---
# <a name="windows-management-framework-wmf-51"></a><span data-ttu-id="2c3bb-103">Windows Management Framework (WMF) 5.1</span><span class="sxs-lookup"><span data-stu-id="2c3bb-103">Windows Management Framework (WMF) 5.1</span></span>

<span data-ttu-id="2c3bb-104">O WMF permite que os utilizadores atualizem os sistemas Windows existentes para as versões com os componentes PowerShell, WMI, WinRM e Registo de Inventário de Software (SIL) que foram lançadas com o Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="2c3bb-104">WMF provides users with the ability to update existing Windows systems to the versions of PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>

<span data-ttu-id="2c3bb-105">O WMF 5.1 pode ser instalado no Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 e 2012 R2 e oferece várias melhorias em relação ao WMF 5.0 RTM, incluindo:</span><span class="sxs-lookup"><span data-stu-id="2c3bb-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="2c3bb-106">Novos cmdlets: grupos e utilizadores; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="2c3bb-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="2c3bb-107">Melhorias do PowerShellGet com a imposição de módulos assinados e a instalação de módulos JEA</span><span class="sxs-lookup"><span data-stu-id="2c3bb-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="2c3bb-108">Adicionado suporte ao PackageManagement para Contentores, Configuração CBS, configuração com base em EXE, pacotes CAB</span><span class="sxs-lookup"><span data-stu-id="2c3bb-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="2c3bb-109">Melhorias na depuração para classes DSC e PowerShell</span><span class="sxs-lookup"><span data-stu-id="2c3bb-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="2c3bb-110">Melhorias de segurança, incluindo a imposição de módulos assinados de catálogo provenientes do Servidor de Solicitação e ao utilizar os cmdlets PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="2c3bb-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="2c3bb-111">Respostas a vários pedidos e problemas de utilizadores</span><span class="sxs-lookup"><span data-stu-id="2c3bb-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="2c3bb-112">Para obter mais informações sobre as novidades nesta versão, procure nos tópicos listados em [Novos Cenários e Funcionalidades](https://docs.microsoft.com/powershell/wmf/5.1/scenarios-features).</span><span class="sxs-lookup"><span data-stu-id="2c3bb-112">To learn about what is new in this release, browse the topics listed under [New Scenarios and Features](https://docs.microsoft.com/powershell/wmf/5.1/scenarios-features).</span></span>

<span data-ttu-id="2c3bb-113">O tópico [Instalar e Configurar](https://docs.microsoft.com/powershell/wmf/5.1/install-configure) lista os requisitos e fornece as instruções de instalação do WMF.</span><span class="sxs-lookup"><span data-stu-id="2c3bb-113">The [Install and Configure](https://docs.microsoft.com/powershell/wmf/5.1/install-configure) topic lists the requirements and provides installation instructions for WMF.</span></span>

<span data-ttu-id="2c3bb-114">O tópico [Compatibilidade](https://docs.microsoft.com/powershell/wmf/5.1/compatibility) lista quais são as versões do WMF que podem ser instaladas nas diferentes versões do Windows.</span><span class="sxs-lookup"><span data-stu-id="2c3bb-114">The [Compatibility](https://docs.microsoft.com/powershell/wmf/5.1/compatibility) topic lists which versions of WMF may be installed on which Windows releases.</span></span>

<span data-ttu-id="2c3bb-115">O tópico [Compatibilidade de Produtos](https://docs.microsoft.com/powershell/wmf/5.1/productincompat) lista as aplicações da Microsoft para as quais ainda não foi aprovada a utilização do WMF 5.1 de momento.</span><span class="sxs-lookup"><span data-stu-id="2c3bb-115">[Product Compatibility](https://docs.microsoft.com/powershell/wmf/5.1/productincompat) lists the Microsoft applications that have not approved WMF 5.1 for use at this time.</span></span>

<span data-ttu-id="2c3bb-116">Os detalhes dos componentes do WMF estarão disponíveis na documentação MSDN:</span><span class="sxs-lookup"><span data-stu-id="2c3bb-116">Details for the components of WMF will be found in MSDN documentation:</span></span>

- [<span data-ttu-id="2c3bb-117">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="2c3bb-117">PowerShell 5.1</span></span>](https://docs.microsoft.com/powershell/)
- <span data-ttu-id="2c3bb-118">[WMI](https://msdn.microsoft.com/library/jj152383(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="2c3bb-118">[WMI](https://msdn.microsoft.com/library/jj152383(v=vs.85).aspx)</span></span>
- <span data-ttu-id="2c3bb-119">[WinRM](https://msdn.microsoft.com/library/aa384426(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="2c3bb-119">[WinRM](https://msdn.microsoft.com/library/aa384426(v=vs.85).aspx)</span></span>
- <span data-ttu-id="2c3bb-120">[Registo de Inventário de Software](https://technet.microsoft.com/library/dn383584(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="2c3bb-120">[Software Inventory Logging](https://technet.microsoft.com/library/dn383584(v=ws.11).aspx)</span></span>
