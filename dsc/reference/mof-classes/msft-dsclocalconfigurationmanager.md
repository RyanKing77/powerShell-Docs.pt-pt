---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 7f6aaf209601e99b0120407eb301d32fcfda9eb8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685397"
---
# <a name="msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c4892-103">Classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c4892-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c4892-104">O Local Configuration Manager (LCM) que controla os Estados dos arquivos de configuração e utiliza o agente de configuração para aplicar as configurações.</span><span class="sxs-lookup"><span data-stu-id="c4892-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="c4892-105">A seguinte sintaxe é simplificada a partir do código de formato MOF (Managed Object) e inclui todas as propriedades herdadas.</span><span class="sxs-lookup"><span data-stu-id="c4892-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="c4892-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4892-106">Syntax</span></span>

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="c4892-107">Membros</span><span class="sxs-lookup"><span data-stu-id="c4892-107">Members</span></span>

<span data-ttu-id="c4892-108">O **MSFT_DSCLocalConfigurationManager** classe tem os seguintes membros:</span><span class="sxs-lookup"><span data-stu-id="c4892-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

- <span data-ttu-id="c4892-109">[Métodos] []</span><span class="sxs-lookup"><span data-stu-id="c4892-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="c4892-110">Métodos</span><span class="sxs-lookup"><span data-stu-id="c4892-110">Methods</span></span>

<span data-ttu-id="c4892-111">O **MSFT_DSCLocalConfigurationManager** classe tem esses métodos.</span><span class="sxs-lookup"><span data-stu-id="c4892-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="c4892-112">Método</span><span class="sxs-lookup"><span data-stu-id="c4892-112">Method</span></span> |<span data-ttu-id="c4892-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4892-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="c4892-114">ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4892-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="c4892-115">Utiliza o agente de configuração para aplicar a configuração que está pendente.</span><span class="sxs-lookup"><span data-stu-id="c4892-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>|
| [<span data-ttu-id="c4892-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4892-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="c4892-117">Desativa a depuração de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="c4892-117">Disables DSC resource debugging.</span></span>|
| [<span data-ttu-id="c4892-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4892-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="c4892-119">Permite a depuração de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="c4892-119">Enables DSC resource debugging.</span></span>|
| [<span data-ttu-id="c4892-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4892-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="c4892-121">Envia o documento de configuração para o nó gerido e utiliza a **obter** método do agente de configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="c4892-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="c4892-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="c4892-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="c4892-123">Obtém o resultado de agente de configuração relacionadas com uma tarefa específica.</span><span class="sxs-lookup"><span data-stu-id="c4892-123">Gets the Configuration Agent output relating to a specific job.</span></span>|
| [<span data-ttu-id="c4892-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="c4892-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="c4892-125">Obter o histórico do Estado de configuração.</span><span class="sxs-lookup"><span data-stu-id="c4892-125">Get the configuration status history.</span></span>|
| [<span data-ttu-id="c4892-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4892-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="c4892-127">Obtém as definições de LCM que são utilizadas para controlar o agente de configuração.</span><span class="sxs-lookup"><span data-stu-id="c4892-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>|
| [<span data-ttu-id="c4892-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="c4892-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="c4892-129">Inicia a verificação de consistência.</span><span class="sxs-lookup"><span data-stu-id="c4892-129">Starts the consistency check.</span></span>|
| [<span data-ttu-id="c4892-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4892-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="c4892-131">Remove os ficheiros de configuração.</span><span class="sxs-lookup"><span data-stu-id="c4892-131">Removes the configuration files.</span></span>|
| [<span data-ttu-id="c4892-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="c4892-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="c4892-133">Chama diretamente a **obter** método de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="c4892-133">Directly calls the **Get** method of a DSC resource.</span></span>|
| [<span data-ttu-id="c4892-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="c4892-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="c4892-135">Chama diretamente a **definir** método de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="c4892-135">Directly calls the **Set** method of a DSC resource.</span></span>|
| [<span data-ttu-id="c4892-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="c4892-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="c4892-137">Chama diretamente a **teste** método de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="c4892-137">Directly calls the **Test** method of a DSC resource.</span></span>|
| [<span data-ttu-id="c4892-138">RollBack</span><span class="sxs-lookup"><span data-stu-id="c4892-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="c4892-139">Rolls novamente para uma configuração anterior.</span><span class="sxs-lookup"><span data-stu-id="c4892-139">Rolls back to a previous configuration.</span></span>|
| [<span data-ttu-id="c4892-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4892-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="c4892-141">Envia o documento de configuração para o nó gerido e o salva como uma alteração pendente.</span><span class="sxs-lookup"><span data-stu-id="c4892-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>|
| [<span data-ttu-id="c4892-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="c4892-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="c4892-143">Envia o documento de configuração para o nó gerido e utiliza o agente de configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="c4892-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="c4892-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="c4892-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="c4892-145">Enviar o documento de configuração para o nó gerido e começar a utilizar o agente de configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="c4892-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="c4892-146">Utilize GetConfigurationResultOutput para obter a saída do resultado.</span><span class="sxs-lookup"><span data-stu-id="c4892-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>|
| [<span data-ttu-id="c4892-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="c4892-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="c4892-148">Define as definições de LCM que são utilizadas para controlar o agente de configuração.</span><span class="sxs-lookup"><span data-stu-id="c4892-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>|
| [<span data-ttu-id="c4892-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4892-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="c4892-150">Interrompe a configuração que está em curso.</span><span class="sxs-lookup"><span data-stu-id="c4892-150">Stops the configuration that is in progress.</span></span>|
| [<span data-ttu-id="c4892-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4892-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="c4892-152">Envia o documento de configuração para o nó gerido e verifica a configuração atual contra o documento.</span><span class="sxs-lookup"><span data-stu-id="c4892-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>|

## <a name="requirements"></a><span data-ttu-id="c4892-153">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c4892-153">Requirements</span></span>

<span data-ttu-id="c4892-154">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c4892-154">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c4892-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4892-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>