---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 615f2998b11a0a927d3868d852e0d408f500c86d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188840"
---
# <a name="msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a7cf6-103">Classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="a7cf6-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a7cf6-104">O Local Configuration Manager (MMC) que controla os Estados dos ficheiros de configuração e utiliza o agente de configuração para aplicar as configurações.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="a7cf6-105">A seguinte sintaxe é simplificada a partir do código de objeto formato MOF (Managed) e inclui todas as propriedades herdadas.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="a7cf6-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7cf6-106">Syntax</span></span>
------

``` syntax
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="a7cf6-107">Membros</span><span class="sxs-lookup"><span data-stu-id="a7cf6-107">Members</span></span>
-------

<span data-ttu-id="a7cf6-108">O **MSFT_DSCLocalConfigurationManager** classe tem os seguintes membros:</span><span class="sxs-lookup"><span data-stu-id="a7cf6-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

-   <span data-ttu-id="a7cf6-109">[Métodos] []</span><span class="sxs-lookup"><span data-stu-id="a7cf6-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="a7cf6-110">Métodos</span><span class="sxs-lookup"><span data-stu-id="a7cf6-110">Methods</span></span>

<span data-ttu-id="a7cf6-111">O **MSFT_DSCLocalConfigurationManager** classe tem estes métodos.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="a7cf6-112">Método</span><span class="sxs-lookup"><span data-stu-id="a7cf6-112">Method</span></span> |<span data-ttu-id="a7cf6-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7cf6-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="a7cf6-114">ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7cf6-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="a7cf6-115">Utiliza o agente de configuração para aplicar a configuração que está pendente.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>|
| [<span data-ttu-id="a7cf6-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7cf6-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="a7cf6-117">Desativa a depuração de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-117">Disables DSC resource debugging.</span></span>|
| [<span data-ttu-id="a7cf6-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7cf6-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="a7cf6-119">Ativa a depuração de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-119">Enables DSC resource debugging.</span></span>|
| [<span data-ttu-id="a7cf6-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7cf6-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="a7cf6-121">Envia o documento de configuração para o nó gerido e utiliza o **obter** método do agente de configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="a7cf6-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="a7cf6-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="a7cf6-123">Obtém o resultado de agente de configuração relacionados com uma tarefa específica.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-123">Gets the Configuration Agent output relating to a specific job.</span></span>|
| [<span data-ttu-id="a7cf6-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="a7cf6-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="a7cf6-125">Obter o histórico do Estado de configuração.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-125">Get the configuration status history.</span></span>|
| [<span data-ttu-id="a7cf6-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7cf6-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="a7cf6-127">Obtém as definições de MMC que são utilizadas para controlar o agente de configuração.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>|
| [<span data-ttu-id="a7cf6-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="a7cf6-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="a7cf6-129">Inicia a verificação de consistência.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-129">Starts the consistency check.</span></span>|
| [<span data-ttu-id="a7cf6-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7cf6-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="a7cf6-131">Remove os ficheiros de configuração.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-131">Removes the configuration files.</span></span>|
| [<span data-ttu-id="a7cf6-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="a7cf6-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="a7cf6-133">Chamadas diretamente a **obter** método de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-133">Directly calls the **Get** method of a DSC resource.</span></span>|
| [<span data-ttu-id="a7cf6-134">resourceSet</span><span class="sxs-lookup"><span data-stu-id="a7cf6-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="a7cf6-135">Chamadas diretamente a **definir** método de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-135">Directly calls the **Set** method of a DSC resource.</span></span>|
| [<span data-ttu-id="a7cf6-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="a7cf6-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="a7cf6-137">Chamadas diretamente a **teste** método de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-137">Directly calls the **Test** method of a DSC resource.</span></span>|
| [<span data-ttu-id="a7cf6-138">Reversão</span><span class="sxs-lookup"><span data-stu-id="a7cf6-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="a7cf6-139">Rolls novamente para uma configuração anterior.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-139">Rolls back to a previous configuration.</span></span>|
| [<span data-ttu-id="a7cf6-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7cf6-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="a7cf6-141">Envia o documento de configuração para o nó gerido e guarda-o como uma alteração pendente.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>|
| [<span data-ttu-id="a7cf6-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="a7cf6-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="a7cf6-143">Envia o documento de configuração para o nó gerido e utiliza o agente de configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="a7cf6-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="a7cf6-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="a7cf6-145">Enviar o documento de configuração para o nó gerido e começar a utilizar o agente de configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="a7cf6-146">Utilize GetConfigurationResultOutput para obter a saída de resultado.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>|
| [<span data-ttu-id="a7cf6-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="a7cf6-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="a7cf6-148">Define as definições de MMC que são utilizadas para controlar o agente de configuração.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>|
| [<span data-ttu-id="a7cf6-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7cf6-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="a7cf6-150">Interrompe a configuração que está em curso.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-150">Stops the configuration that is in progress.</span></span>|
| [<span data-ttu-id="a7cf6-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7cf6-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="a7cf6-152">Envia o documento de configuração para o nó gerido e verifica a configuração atual contra o documento.</span><span class="sxs-lookup"><span data-stu-id="a7cf6-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>|





## <a name="requirements"></a><span data-ttu-id="a7cf6-153">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a7cf6-153">Requirements</span></span>
------------
><span data-ttu-id="a7cf6-154">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a7cf6-154">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a7cf6-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7cf6-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>