---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Descrição geral da configuração do estado pretendido do Windows PowerShell
ms.openlocfilehash: 3f357ea11a388a05b73539a63e52e639ee906f68
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="windows-powershell-desired-state-configuration-overview"></a><span data-ttu-id="2bd2f-103">Descrição geral da configuração do estado pretendido do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2bd2f-103">Windows PowerShell Desired State Configuration Overview</span></span>

> <span data-ttu-id="2bd2f-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2bd2f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="2bd2f-105">DSC é uma plataforma de gestão do PowerShell que permite-lhe gerir o seu departamento de TI e a infraestrutura de desenvolvimento com a configuração como código.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-105">DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code.</span></span>

- <span data-ttu-id="2bd2f-106">Para obter uma descrição geral das vantagens empresariais do DSC a utilizar, consulte [Desired Configuration descrição geral do Estado para os decisores](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="2bd2f-106">For an overview of the business benefits of using DSC, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>
- <span data-ttu-id="2bd2f-107">Para obter uma descrição geral das vantagens de utilizar o DSC engenharia, consulte [Desired Configuration descrição geral do Estado para engenheiros](DscForEngineers.md).</span><span class="sxs-lookup"><span data-stu-id="2bd2f-107">For an overview of the engineering benefits of using DSC, see [Desired State Configuration Overview for Engineers](DscForEngineers.md).</span></span>
- <span data-ttu-id="2bd2f-108">Para começar a utilizar o DSC rapidamente, consulte o artigo [início rápido do DSC](quickStart.md).</span><span class="sxs-lookup"><span data-stu-id="2bd2f-108">To start using DSC quickly, see [DSC quick start](quickStart.md).</span></span>

## <a name="key-concepts"></a><span data-ttu-id="2bd2f-109">Conceitos chave</span><span class="sxs-lookup"><span data-stu-id="2bd2f-109">Key Concepts</span></span>

<span data-ttu-id="2bd2f-110">DSC é uma plataforma declarativa utilizada para gestão de sistemas, implementação e configuração.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-110">DSC is a declarative platform used for configuration, deployment, and management of systems.</span></span> <span data-ttu-id="2bd2f-111">É composto por três componentes principais:</span><span class="sxs-lookup"><span data-stu-id="2bd2f-111">It consists of three primary components:</span></span>

- <span data-ttu-id="2bd2f-112">[Configurações](configurations.md) são scripts do PowerShell declarativas que definirem e configurar as instâncias de recursos.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-112">[Configurations](configurations.md) are declarative PowerShell scripts which define and configure instances of resources.</span></span>
    <span data-ttu-id="2bd2f-113">Após executar a configuração, DSC (e os recursos a ser chamados na configuração da) irá simplesmente "torná-lo,", garantindo que o sistema existe no Estado disposto na configuração.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-113">Upon running the configuration, DSC (and the resources being called by the configuration) will simply “make it so”, ensuring that the system exists in the state laid out by the configuration.</span></span>
    <span data-ttu-id="2bd2f-114">Configurações de DSC são também idempotent: o Gestor de configuração Local (MMC) irá continuar a garantir que as máquinas estão configuradas em que a configuração de estado declara.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-114">DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.</span></span>
- <span data-ttu-id="2bd2f-115">[Recursos](resources.md) fazem parte "torná-la para" do DSC.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-115">[Resources](resources.md) are the "make it so" part of DSC.</span></span> <span data-ttu-id="2bd2f-116">Contêm o código que colocar e manter o destino de uma configuração no estado especificado.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-116">They contain the code that put and keep the target of a configuration in the specified state.</span></span>
    <span data-ttu-id="2bd2f-117">Recursos residem em módulos do PowerShell e podem ser escritos para modelar algo como genérica como um ficheiro ou de um processo do Windows ou tão específico como um servidor IIS ou uma VM em execução no Azure.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-117">Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.</span></span>
- <span data-ttu-id="2bd2f-118">O [Gestor de configuração Local (MMC)](metaConfig.md) é o motor através do qual o DSC facilita a interação entre os recursos e configurações.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-118">The [Local Configuration Manager (LCM)](metaConfig.md) is the engine by which DSC facilitates the interaction between resources and configurations.</span></span>
    <span data-ttu-id="2bd2f-119">O MMC consulta regularmente o sistema utilizando o fluxo de controlo implementado por recursos para se certificar de que o estado definido por uma configuração é mantido.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-119">The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained.</span></span>
    <span data-ttu-id="2bd2f-120">Se o sistema está fora do Estado, o MMC faz com que chamadas para o código de recursos para "torná-lo,", de acordo com a configuração.</span><span class="sxs-lookup"><span data-stu-id="2bd2f-120">If the system is out of state, the LCM makes calls to the code in resources to “make it so” according to the configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="2bd2f-121">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="2bd2f-121">See Also</span></span>

- [<span data-ttu-id="2bd2f-122">Configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="2bd2f-122">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="2bd2f-123">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="2bd2f-123">DSC Resources</span></span>](resources.md)
- [<span data-ttu-id="2bd2f-124">Configurar o Gestor de configuração Local</span><span class="sxs-lookup"><span data-stu-id="2bd2f-124">Configuring The Local Configuration Manager</span></span>](metaConfig.md)