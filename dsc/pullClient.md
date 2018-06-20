---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Configurar um cliente de solicitação do DSC
ms.openlocfilehash: 7f8758bd7145518e30e9c28b74d0db5d74dfaab3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186665"
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="936fc-103">Configurar um cliente de solicitação do DSC</span><span class="sxs-lookup"><span data-stu-id="936fc-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="936fc-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="936fc-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="936fc-105">O servidor de solicitação (funcionalidade do Windows *DSC serviço*) é um componente suportado do Windows Server no entanto, são não planos para oferecer novas funcionalidades ou capacidades.</span><span class="sxs-lookup"><span data-stu-id="936fc-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="936fc-106">É recomendado para começar a transição geridos os clientes [Automation DSC do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação no Windows Server) ou uma das soluções de Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="936fc-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="936fc-107">Cada nó de destino tem de ser disse para utilizar o modo de extração e determinados a localização do ficheiro ou URL em que podem contactar o servidor de solicitação para obter recursos e configurações e, em que deve enviar dados de relatório.</span><span class="sxs-lookup"><span data-stu-id="936fc-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="936fc-108">Os tópicos seguintes explicam como configurar clientes de extração:</span><span class="sxs-lookup"><span data-stu-id="936fc-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="936fc-109">Configurar um cliente de solicitação através de nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="936fc-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="936fc-110">Configurar um cliente de solicitação através de IDs de configuração</span><span class="sxs-lookup"><span data-stu-id="936fc-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="936fc-111">**Tenha em atenção**: estes tópicos que se aplicam ao PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="936fc-111">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="936fc-112">Para configurar um cliente de solicitação no PowerShell 4.0, consulte [configurar um cliente de extração com o ID de configuração no PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="936fc-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>