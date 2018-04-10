---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Método SendConfigurationApplyAsync da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 7ff821a277a548869862741551ee9897e417ea45
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c44b9-103">Método SendConfigurationApplyAsync da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c44b9-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c44b9-104">Envia o documento de configuração no modo assíncrono para o nó gerido e utiliza o agente de configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="c44b9-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="c44b9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c44b9-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="c44b9-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c44b9-106">Parameters</span></span>
----------

<span data-ttu-id="c44b9-107">*ConfigurationData* \[no\] os dados de ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="c44b9-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="c44b9-108">*Forçar* \[no\] **verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="c44b9-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="c44b9-109">*jobId* \[no\] o ID da tarefa para o qual pretende enviar a configuração.</span><span class="sxs-lookup"><span data-stu-id="c44b9-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="c44b9-110">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="c44b9-110">Return value</span></span>
------------

<span data-ttu-id="c44b9-111">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="c44b9-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c44b9-112">Observações</span><span class="sxs-lookup"><span data-stu-id="c44b9-112">Remarks</span></span>

<span data-ttu-id="c44b9-113">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="c44b9-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c44b9-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c44b9-114">Requirements</span></span>
------------
><span data-ttu-id="c44b9-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c44b9-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="c44b9-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c44b9-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="c44b9-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c44b9-117">See also</span></span>


[<span data-ttu-id="c44b9-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c44b9-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)