---
ms.date: 2017-10-16
author: eslesar;mgreenegit
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Enacting configurações"
ms.openlocfilehash: f9f8889439e43d540b50b68ef13e8e088b8cadd3
ms.sourcegitcommit: 9a5da3f739b1eebb81ede58bd4fc8037bad87224
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2017
---
# <a name="enacting-configurations"></a><span data-ttu-id="d8d57-103">Enacting configurações</span><span class="sxs-lookup"><span data-stu-id="d8d57-103">Enacting configurations</span></span>

><span data-ttu-id="d8d57-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d8d57-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="d8d57-105">Existem duas formas de enact configurações do PowerShell pretendido Estado Configuration (DSC): push modo e o modo de extração.</span><span class="sxs-lookup"><span data-stu-id="d8d57-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="d8d57-106">Modo de push</span><span class="sxs-lookup"><span data-stu-id="d8d57-106">Push mode</span></span>

<span data-ttu-id="d8d57-107">![Modo de push](images/pushModel.png "como push funciona do modo")</span><span class="sxs-lookup"><span data-stu-id="d8d57-107">![Push mode](images/pushModel.png "How push mode works")</span></span>

<span data-ttu-id="d8d57-108">Modo de push refere-se a um utilizador ativamente aplicar uma configuração para um nó de destino ao chamar o [início DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d8d57-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span>

<span data-ttu-id="d8d57-109">Depois de criar e compilar uma configuração, pode enact-lo no modo de push chamando a [início DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, definir o parâmetro - Path do cmdlet para o caminho onde está localizada a configuração MOF.</span><span class="sxs-lookup"><span data-stu-id="d8d57-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span>
<span data-ttu-id="d8d57-110">Por exemplo, se a configuração MOF está localizada em `C:\DSC\Configurations\localhost.mof`, seria aplicá-la para o computador local com o seguinte comando:`Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="d8d57-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="d8d57-111">__Tenha em atenção__: por predefinição, o DSC é executada uma configuração como uma tarefa em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="d8d57-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="d8d57-112">Para executar a configuração de forma interativa, chame o [início DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) com o __-aguarde__ parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d8d57-112">To run the configuration interactively, call the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) with the __-Wait__ parameter.</span></span>

## <a name="pull-mode"></a><span data-ttu-id="d8d57-113">Modo de extração</span><span class="sxs-lookup"><span data-stu-id="d8d57-113">Pull mode</span></span>

<span data-ttu-id="d8d57-114">![Modo de extração](images/pullModel.png "como funciona do modo de extração")</span><span class="sxs-lookup"><span data-stu-id="d8d57-114">![Pull Mode](images/pullModel.png "How pull mode works")</span></span>

<span data-ttu-id="d8d57-115">No modo de extração, os clientes de extração estão configurados para obter as respetivas configurações de estado pretendido de um serviço de solicitação remoto.</span><span class="sxs-lookup"><span data-stu-id="d8d57-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull service.</span></span>
<span data-ttu-id="d8d57-116">Da mesma forma, o serviço de solicitação tiver sido configurado para o serviço anfitrião de DSC e tiver sido aprovisionado com as configurações e os recursos que são necessários para os clientes de extração.</span><span class="sxs-lookup"><span data-stu-id="d8d57-116">Likewise, the pull service has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span>
<span data-ttu-id="d8d57-117">Cada um dos clientes de solicitação tem um evento agendado que efetua uma verificação de compatibilidade periódica na configuração do nó.</span><span class="sxs-lookup"><span data-stu-id="d8d57-117">Each of the pull clients has a scheduled event that performs a periodic compliance check on the configuration of the node.</span></span>
<span data-ttu-id="d8d57-118">Quando o evento é acionado pela primeira vez, o Gestor de configuração Local (MMC) no cliente solicitação faz um pedido para o serviço de extração para obter a configuração especificada no MMC.</span><span class="sxs-lookup"><span data-stu-id="d8d57-118">When the event is triggered the first time, the Local Configuration Manager (LCM) on the pull client makes a request to the pull service to get the configuration specified in the LCM.</span></span>
<span data-ttu-id="d8d57-119">Se essa configuração existe no serviço de solicitação e transmite-as verificações de validação inicial, a configuração é transferida para o cliente de solicitação, onde, em seguida, é executada através do MMC.</span><span class="sxs-lookup"><span data-stu-id="d8d57-119">If that configuration exists on the pull service, and it passes initial validation checks, the configuration is downloaded to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="d8d57-120">O MMC verifica se o cliente está em conformidade com a configuração em intervalos regulares especificado pelo **ConfigurationModeFrequencyMins** propriedade a MMC.</span><span class="sxs-lookup"><span data-stu-id="d8d57-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span>
<span data-ttu-id="d8d57-121">O MMC verifica a existência de configurações atualizadas no serviço de solicitação em intervalos regulares especificados pelo **RefreshModeFrequency** propriedade a MMC.</span><span class="sxs-lookup"><span data-stu-id="d8d57-121">The LCM checks for updated configurations on the pull service at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span>
<span data-ttu-id="d8d57-122">Para obter informações sobre como configurar o MMC, consulte [configurar o Gestor de configuração Local](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="d8d57-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

<span data-ttu-id="d8d57-123">A solução recomendada para alojar um serviço de extração é o serviço de nuvem de DSC [da automatização do Azure](https://azure.microsoft.com/en-us/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="d8d57-123">The recommended solution for hosting a Pull Service, is the DSC cloud service, [Azure Automation](https://azure.microsoft.com/en-us/services/automation/).</span></span>
<span data-ttu-id="d8d57-124">Isto está alojado fornece a solução de gestão gráficas, relatórios e administração centralizada.</span><span class="sxs-lookup"><span data-stu-id="d8d57-124">This is hosted solution provides graphical management, reporting, and centralized administration.</span></span>

<span data-ttu-id="d8d57-125">Para obter mais informações sobre como configurar um serviço de solicitação no Windows Server, consulte [configurar um servidor de solicitação do DSC web](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="d8d57-125">For more information on setting up a Pull Service on Windows Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>
<span data-ttu-id="d8d57-126">No entanto, de compreender que esta implementação limitou as funcionalidades e exigir algumas integração "fazê-lo a próprio".</span><span class="sxs-lookup"><span data-stu-id="d8d57-126">Understand however, that this implementation has limited features and does require some "do it yourself" integration.</span></span>

<span data-ttu-id="d8d57-127">Os tópicos seguintes explicam o serviço de extração e os clientes:</span><span class="sxs-lookup"><span data-stu-id="d8d57-127">The following topics explain pull service and clients:</span></span>

- [<span data-ttu-id="d8d57-128">Descrição geral do DSC da automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="d8d57-128">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="d8d57-129">Configurar um servidor de solicitação do SMB</span><span class="sxs-lookup"><span data-stu-id="d8d57-129">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="d8d57-130">Configurar um cliente de solicitação</span><span class="sxs-lookup"><span data-stu-id="d8d57-130">Configuring a pull client</span></span>](pullClientConfigID.md)
