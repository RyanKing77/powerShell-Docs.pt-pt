---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Windows PowerShell Desired State Configuration descrição-geral
ms.openlocfilehash: 3e4f0afa17ab60bfa98f1b86b9830462a7c8e1cf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079976"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a><span data-ttu-id="0ece2-103">Windows PowerShell Desired State Configuration descrição-geral</span><span class="sxs-lookup"><span data-stu-id="0ece2-103">Windows PowerShell Desired State Configuration Overview</span></span>

> <span data-ttu-id="0ece2-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0ece2-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="0ece2-105">DSC é uma plataforma de gestão do PowerShell que permite-lhe gerir o departamento de TI e a infraestrutura de desenvolvimento com a configuração como código.</span><span class="sxs-lookup"><span data-stu-id="0ece2-105">DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code.</span></span>

- <span data-ttu-id="0ece2-106">Para obter uma descrição geral dos benefícios comerciais do uso de DSC, veja [Desired State Configuration descrição geral para os tomadores de decisão](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="0ece2-106">For an overview of the business benefits of using DSC, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>
- <span data-ttu-id="0ece2-107">Para uma descrição geral dos benefícios da utilização do DSC engenharia, consulte [Desired State Configuration descrição geral para engenheiros de](DscForEngineers.md).</span><span class="sxs-lookup"><span data-stu-id="0ece2-107">For an overview of the engineering benefits of using DSC, see [Desired State Configuration Overview for Engineers](DscForEngineers.md).</span></span>
- <span data-ttu-id="0ece2-108">Para começar a utilizar rapidamente o DSC, veja [guia de introdução do DSC](../quickstarts/website-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="0ece2-108">To start using DSC quickly, see [DSC quick start](../quickstarts/website-quickstart.md).</span></span>

## <a name="key-concepts"></a><span data-ttu-id="0ece2-109">Conceitos-chave</span><span class="sxs-lookup"><span data-stu-id="0ece2-109">Key Concepts</span></span>

<span data-ttu-id="0ece2-110">DSC é uma plataforma declarativa usada para configuração, implantação e gerenciamento de sistemas.</span><span class="sxs-lookup"><span data-stu-id="0ece2-110">DSC is a declarative platform used for configuration, deployment, and management of systems.</span></span> <span data-ttu-id="0ece2-111">Esta é composta por três componentes principais:</span><span class="sxs-lookup"><span data-stu-id="0ece2-111">It consists of three primary components:</span></span>

- <span data-ttu-id="0ece2-112">[Configurações](../configurations/configurations.md) são scripts do PowerShell declarativas que definem e configure as instâncias de recursos.</span><span class="sxs-lookup"><span data-stu-id="0ece2-112">[Configurations](../configurations/configurations.md) are declarative PowerShell scripts which define and configure instances of resources.</span></span>
    <span data-ttu-id="0ece2-113">Após executar a configuração, DSC (e os recursos a ser chamados pela configuração) será simplesmente "que isso", garantindo que o sistema existe no Estado disposto pela configuração.</span><span class="sxs-lookup"><span data-stu-id="0ece2-113">Upon running the configuration, DSC (and the resources being called by the configuration) will simply “make it so”, ensuring that the system exists in the state laid out by the configuration.</span></span>
    <span data-ttu-id="0ece2-114">As configurações de DSC também são idempotentes: o Gestor de configuração Local (LCM) irá continuar a garantir que as máquinas estão configuradas em tudo o que a configuração de estado declara.</span><span class="sxs-lookup"><span data-stu-id="0ece2-114">DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.</span></span>
- <span data-ttu-id="0ece2-115">[Recursos](../resources/resources.md) são a parte "tornam isso" do DSC.</span><span class="sxs-lookup"><span data-stu-id="0ece2-115">[Resources](../resources/resources.md) are the "make it so" part of DSC.</span></span> <span data-ttu-id="0ece2-116">Eles contêm o código que coloca e manter o destino de uma configuração no estado especificado.</span><span class="sxs-lookup"><span data-stu-id="0ece2-116">They contain the code that put and keep the target of a configuration in the specified state.</span></span>
    <span data-ttu-id="0ece2-117">Recursos residem em módulos do PowerShell e podem ser escritos para modelar algo tão genérico, um arquivo ou um processo do Windows ou o mais específico que um servidor IIS ou uma VM em execução no Azure.</span><span class="sxs-lookup"><span data-stu-id="0ece2-117">Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.</span></span>
- <span data-ttu-id="0ece2-118">O [Gestor de configuração Local (LCM)](../managing-nodes/metaConfig.md) é o mecanismo pelo qual o DSC facilita a interação entre os recursos e configurações.</span><span class="sxs-lookup"><span data-stu-id="0ece2-118">The [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md) is the engine by which DSC facilitates the interaction between resources and configurations.</span></span>
    <span data-ttu-id="0ece2-119">O LCM consulta regularmente o sistema usando o fluxo de controlo implementado pelos recursos para garantir que o estado definido por uma configuração é mantido.</span><span class="sxs-lookup"><span data-stu-id="0ece2-119">The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained.</span></span>
    <span data-ttu-id="0ece2-120">Se o sistema está sem estado, o LCM faz chamadas para o código em recursos para "tornam isso", de acordo com a configuração.</span><span class="sxs-lookup"><span data-stu-id="0ece2-120">If the system is out of state, the LCM makes calls to the code in resources to “make it so” according to the configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ece2-121">Veja Também</span><span class="sxs-lookup"><span data-stu-id="0ece2-121">See Also</span></span>

- [<span data-ttu-id="0ece2-122">Configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="0ece2-122">DSC Configurations</span></span>](../configurations/configurations.md)
- [<span data-ttu-id="0ece2-123">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="0ece2-123">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="0ece2-124">Configurar o Gestor de configuração Local</span><span class="sxs-lookup"><span data-stu-id="0ece2-124">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
