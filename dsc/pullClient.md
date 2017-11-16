---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Configurar um cliente de solicitação do DSC"
ms.openlocfilehash: d2d1bab7ba2b482b2a66ce59b5f80ea32c242c47
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="bf3cb-103">Configurar um cliente de solicitação do DSC</span><span class="sxs-lookup"><span data-stu-id="bf3cb-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="bf3cb-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bf3cb-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="bf3cb-105">Cada nó de destino tem de ser disse para utilizar o modo de extração e determinados a localização do ficheiro ou URL em que podem contactar o servidor de solicitação para obter recursos e configurações e, em que deve enviar dados de relatório.</span><span class="sxs-lookup"><span data-stu-id="bf3cb-105">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>


<span data-ttu-id="bf3cb-106">Os tópicos seguintes explicam como configurar clientes de extração:</span><span class="sxs-lookup"><span data-stu-id="bf3cb-106">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="bf3cb-107">Configurar um cliente de solicitação utilizando nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="bf3cb-107">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="bf3cb-108">Configurar um cliente de extração com o ID de configuração</span><span class="sxs-lookup"><span data-stu-id="bf3cb-108">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="bf3cb-109">**Tenha em atenção**: estes tópicos que se aplicam ao PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="bf3cb-109">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="bf3cb-110">Para configurar um cliente de solicitação no PowerShell 4.0, consulte [configurar um cliente de extração com o ID de configuração no PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="bf3cb-110">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>

