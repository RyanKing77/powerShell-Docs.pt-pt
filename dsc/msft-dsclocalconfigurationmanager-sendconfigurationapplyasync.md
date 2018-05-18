---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Método SendConfigurationApplyAsync da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: acd8f380f1c49eb008563398c2c3de3fce5477f9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9ea69-103">Método SendConfigurationApplyAsync da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="9ea69-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9ea69-104">Envia o documento de configuração no modo assíncrono para o nó gerido e utiliza o agente de configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="9ea69-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="9ea69-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ea69-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="9ea69-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9ea69-106">Parameters</span></span>
----------

<span data-ttu-id="9ea69-107">*ConfigurationData* \[no\] os dados de ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="9ea69-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="9ea69-108">*Forçar* \[no\] **verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="9ea69-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="9ea69-109">*jobId* \[no\] o ID da tarefa para o qual pretende enviar a configuração.</span><span class="sxs-lookup"><span data-stu-id="9ea69-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="9ea69-110">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="9ea69-110">Return value</span></span>
------------

<span data-ttu-id="9ea69-111">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="9ea69-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9ea69-112">Observações</span><span class="sxs-lookup"><span data-stu-id="9ea69-112">Remarks</span></span>

<span data-ttu-id="9ea69-113">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="9ea69-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9ea69-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ea69-114">Requirements</span></span>
------------
><span data-ttu-id="9ea69-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9ea69-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9ea69-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9ea69-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9ea69-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ea69-117">See also</span></span>


[<span data-ttu-id="9ea69-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9ea69-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)