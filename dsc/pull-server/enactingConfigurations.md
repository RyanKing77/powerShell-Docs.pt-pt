---
ms.date: 10/16/2017
keywords: DSC, powershell, configuração, a configuração
title: Aplicar configurações
ms.openlocfilehash: 4a6e7e511446ab27307683ad3d5676391e7c791c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405424"
---
# <a name="enacting-configurations"></a><span data-ttu-id="bde4c-103">Aplicar configurações</span><span class="sxs-lookup"><span data-stu-id="bde4c-103">Enacting configurations</span></span>

><span data-ttu-id="bde4c-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bde4c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="bde4c-105">Existem duas formas adotar configurações de PowerShell Desired State Configuration (DSC): o modo de solicitação e de push.</span><span class="sxs-lookup"><span data-stu-id="bde4c-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="bde4c-106">Modo de push</span><span class="sxs-lookup"><span data-stu-id="bde4c-106">Push mode</span></span>

<span data-ttu-id="bde4c-107">![Modo push](../images/pushModel.png "como push funciona de modo")</span><span class="sxs-lookup"><span data-stu-id="bde4c-107">![Push mode](../images/pushModel.png "How push mode works")</span></span>

<span data-ttu-id="bde4c-108">Modo push refere-se a um utilizador ativamente aplicar uma configuração para um nó de destino ao chamar o [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bde4c-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="bde4c-109">Depois de criar e compilar uma configuração, pode aplicá-lo no modo push ao chamar o [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet, definindo o parâmetro - Path do cmdlet para o caminho onde está localizada a MOF de configuração.</span><span class="sxs-lookup"><span data-stu-id="bde4c-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span>
<span data-ttu-id="bde4c-110">Por exemplo, se a MOF de configuração está localizada em `C:\DSC\Configurations\localhost.mof`, poderia aplicá-lo na máquina local com o seguinte comando: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="bde4c-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="bde4c-111">__Tenha em atenção__: Por predefinição, o DSC é executada uma configuração como uma tarefa em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="bde4c-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="bde4c-112">Para executar a configuração de forma interativa, chame o [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) com o __-aguardar__ parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bde4c-112">To run the configuration interactively, call the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) with the __-Wait__ parameter.</span></span>

## <a name="pull-mode"></a><span data-ttu-id="bde4c-113">Modo de solicitação</span><span class="sxs-lookup"><span data-stu-id="bde4c-113">Pull mode</span></span>

<span data-ttu-id="bde4c-114">![Modo de solicitação](../images/pullModel.png "funciona de modo por solicitação")</span><span class="sxs-lookup"><span data-stu-id="bde4c-114">![Pull Mode](../images/pullModel.png "How pull mode works")</span></span>

<span data-ttu-id="bde4c-115">No modo de solicitação, os clientes de pull são configurados para obter as respetivas configurações de estado pretendido de um serviço pull de remoto.</span><span class="sxs-lookup"><span data-stu-id="bde4c-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull service.</span></span>
<span data-ttu-id="bde4c-116">Da mesma forma, o serviço de pull foi configurado para o serviço de anfitrião do DSC e tiver sido aprovisionado com as configurações e os recursos que são necessários para os clientes de pull.</span><span class="sxs-lookup"><span data-stu-id="bde4c-116">Likewise, the pull service has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span>
<span data-ttu-id="bde4c-117">Cada um dos clientes pull tem um evento agendado que realiza uma verificação de conformidade periódica na configuração do nó.</span><span class="sxs-lookup"><span data-stu-id="bde4c-117">Each of the pull clients has a scheduled event that performs a periodic compliance check on the configuration of the node.</span></span>
<span data-ttu-id="bde4c-118">Quando o evento é acionado pela primeira vez, o Gestor de configuração Local (LCM) no cliente de solicitação faz um pedido para o serviço de extração para obter a configuração especificada no LCM.</span><span class="sxs-lookup"><span data-stu-id="bde4c-118">When the event is triggered the first time, the Local Configuration Manager (LCM) on the pull client makes a request to the pull service to get the configuration specified in the LCM.</span></span>
<span data-ttu-id="bde4c-119">Se essa configuração existe no serviço de solicitação e passa as verificações de validação inicial, a configuração é transferida para o cliente de solicitação, onde, em seguida, é executada pelo LCM.</span><span class="sxs-lookup"><span data-stu-id="bde4c-119">If that configuration exists on the pull service, and it passes initial validation checks, the configuration is downloaded to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="bde4c-120">O LCM verifica que o cliente está em conformidade com a configuração em intervalos regulares, especificado pelos **ConfigurationModeFrequencyMins** propriedade do LCM.</span><span class="sxs-lookup"><span data-stu-id="bde4c-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span>
<span data-ttu-id="bde4c-121">O LCM verifica a existência de configurações atualizadas no serviço pull em intervalos regulares, especificados pelos **RefreshModeFrequency** propriedade do LCM.</span><span class="sxs-lookup"><span data-stu-id="bde4c-121">The LCM checks for updated configurations on the pull service at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span>
<span data-ttu-id="bde4c-122">Para obter informações sobre como configurar o LCM, consulte [configurar o Gestor de configuração Local](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="bde4c-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="bde4c-123">A solução recomendada para hospedar um serviço de solicitação, é o serviço de nuvem de DSC [automatização do Azure](https://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="bde4c-123">The recommended solution for hosting a Pull Service, is the DSC cloud service, [Azure Automation](https://azure.microsoft.com/services/automation/).</span></span>
<span data-ttu-id="bde4c-124">Isso está alojado a solução fornece gestão gráficas, relatórios e administração centralizada.</span><span class="sxs-lookup"><span data-stu-id="bde4c-124">This is hosted solution provides graphical management, reporting, and centralized administration.</span></span>

<span data-ttu-id="bde4c-125">Para obter mais informações sobre como configurar um serviço Pull no Windows Server, consulte [como configurar um servidor de solicitação do DSC web](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="bde4c-125">For more information on setting up a Pull Service on Windows Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>
<span data-ttu-id="bde4c-126">No entanto, a compreender que essa implementação tiver recursos limitados e exige alguns integração "faça mesmo".</span><span class="sxs-lookup"><span data-stu-id="bde4c-126">Understand however, that this implementation has limited features and does require some "do it yourself" integration.</span></span>

<span data-ttu-id="bde4c-127">Os tópicos seguintes explicam o serviço de solicitação e clientes:</span><span class="sxs-lookup"><span data-stu-id="bde4c-127">The following topics explain pull service and clients:</span></span>

- [<span data-ttu-id="bde4c-128">Descrição geral de DSC de automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="bde4c-128">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="bde4c-129">Como configurar um servidor de solicitação SMB</span><span class="sxs-lookup"><span data-stu-id="bde4c-129">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="bde4c-130">Configurar um cliente de solicitação</span><span class="sxs-lookup"><span data-stu-id="bde4c-130">Configuring a pull client</span></span>](pullClientConfigID.md)
