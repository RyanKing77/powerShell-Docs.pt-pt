---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: f4c2ddaa37cdafeff1a442f3f1fa656788a1c6c8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="6426c-103">Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="6426c-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="6426c-104">Obtém o resultado de agente de configuração associado uma tarefa específica.</span><span class="sxs-lookup"><span data-stu-id="6426c-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="6426c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6426c-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="6426c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6426c-106">Parameters</span></span>
----------

<span data-ttu-id="6426c-107">*jobId* \[no\] o ID da tarefa para o qual pretende obter dados de saída.</span><span class="sxs-lookup"><span data-stu-id="6426c-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="6426c-108">*resumeOutputBookmark* \[no\] Especifica que o resultado deve ser uma continuação de um marcador anterior.</span><span class="sxs-lookup"><span data-stu-id="6426c-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="6426c-109">*saída* \[saída\] a saída para a tarefa especificada.</span><span class="sxs-lookup"><span data-stu-id="6426c-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="6426c-110">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="6426c-110">Return value</span></span>
------------

<span data-ttu-id="6426c-111">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="6426c-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6426c-112">Observações</span><span class="sxs-lookup"><span data-stu-id="6426c-112">Remarks</span></span>

<span data-ttu-id="6426c-113">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="6426c-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6426c-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6426c-114">Requirements</span></span>
------------
><span data-ttu-id="6426c-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6426c-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="6426c-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6426c-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="6426c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6426c-117">See also</span></span>


[<span data-ttu-id="6426c-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="6426c-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)