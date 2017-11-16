---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 09862fd3c19e1e517c9bf5df878113ba3f10d8a6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="643f9-103">Método de GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="643f9-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="643f9-104">Obtém o resultado de agente de configuração associado uma tarefa específica.</span><span class="sxs-lookup"><span data-stu-id="643f9-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="643f9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="643f9-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="643f9-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="643f9-106">Parameters</span></span>
----------

<span data-ttu-id="643f9-107">*jobId* \[no\]</span><span class="sxs-lookup"><span data-stu-id="643f9-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="643f9-108">O ID da tarefa para o qual pretende obter dados de saída.</span><span class="sxs-lookup"><span data-stu-id="643f9-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="643f9-109">*resumeOutputBookmark* \[no\]</span><span class="sxs-lookup"><span data-stu-id="643f9-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="643f9-110">Especifica que o resultado deve ser uma continuação de um marcador anterior.</span><span class="sxs-lookup"><span data-stu-id="643f9-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="643f9-111">*saída* \[enviados\]</span><span class="sxs-lookup"><span data-stu-id="643f9-111">*output* \[out\]</span></span>  
<span data-ttu-id="643f9-112">A saída para a tarefa especificada.</span><span class="sxs-lookup"><span data-stu-id="643f9-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="643f9-113">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="643f9-113">Return value</span></span>
------------

<span data-ttu-id="643f9-114">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="643f9-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="643f9-115">Observações</span><span class="sxs-lookup"><span data-stu-id="643f9-115">Remarks</span></span>

<span data-ttu-id="643f9-116">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="643f9-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="643f9-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="643f9-117">Requirements</span></span>
------------
><span data-ttu-id="643f9-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="643f9-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="643f9-119">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="643f9-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="643f9-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="643f9-120">See also</span></span>


[<span data-ttu-id="643f9-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="643f9-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



