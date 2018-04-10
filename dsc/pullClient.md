---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Configurar um cliente de solicitação do DSC
ms.openlocfilehash: e6d73187566db2756ae24dabe0a825fffb5ecce0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="2595e-103">Configurar um cliente de solicitação do DSC</span><span class="sxs-lookup"><span data-stu-id="2595e-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="2595e-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2595e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="2595e-105">Cada nó de destino tem de ser disse para utilizar o modo de extração e determinados a localização do ficheiro ou URL em que podem contactar o servidor de solicitação para obter recursos e configurações e, em que deve enviar dados de relatório.</span><span class="sxs-lookup"><span data-stu-id="2595e-105">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>


<span data-ttu-id="2595e-106">Os tópicos seguintes explicam como configurar clientes de extração:</span><span class="sxs-lookup"><span data-stu-id="2595e-106">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="2595e-107">Configurar um cliente de solicitação através de nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="2595e-107">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="2595e-108">Configurar um cliente de solicitação através de IDs de configuração</span><span class="sxs-lookup"><span data-stu-id="2595e-108">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="2595e-109">**Tenha em atenção**: estes tópicos que se aplicam ao PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="2595e-109">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="2595e-110">Para configurar um cliente de solicitação no PowerShell 4.0, consulte [configurar um cliente de extração com o ID de configuração no PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="2595e-110">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>