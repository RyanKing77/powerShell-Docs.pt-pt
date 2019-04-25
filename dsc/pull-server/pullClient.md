---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Configurar um cliente de pull DSC
ms.openlocfilehash: 54c68ac26e5388260e252ce01418170e26ddecde
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079647"
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="df64b-103">Configurar um cliente de pull DSC</span><span class="sxs-lookup"><span data-stu-id="df64b-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="df64b-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="df64b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="df64b-105">O servidor de solicitação (recurso do Windows *DSC-serviço*) é um componente suportado do Windows Server no entanto, não existem planos para oferecer novas funcionalidades ou capacidades.</span><span class="sxs-lookup"><span data-stu-id="df64b-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="df64b-106">É recomendado para começar a fazer a transição geridos os clientes [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação de mensagens em fila no Windows Server) ou uma das soluções da Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="df64b-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="df64b-107">Cada nó de destino deve ser informado para utilizar o modo de solicitação e tendo em conta a localização do ficheiro ou URL onde ele pode contactar o servidor de solicitação para obter recursos e configurações, e onde ele deve enviar dados de relatório.</span><span class="sxs-lookup"><span data-stu-id="df64b-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="df64b-108">Os tópicos seguintes explicam como configurar clientes de extração:</span><span class="sxs-lookup"><span data-stu-id="df64b-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="df64b-109">Configurar um cliente de solicitação através de nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="df64b-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="df64b-110">Configurar um cliente de solicitação através de IDs de configuração</span><span class="sxs-lookup"><span data-stu-id="df64b-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> [!NOTE]
> <span data-ttu-id="df64b-111">Estes tópicos que se aplicam ao PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="df64b-111">These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="df64b-112">Para configurar um cliente de solicitação no PowerShell 4.0, consulte [como configurar um cliente de solicitação com o ID de configuração no PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="df64b-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>