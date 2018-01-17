---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: f6106bb28dc20004b5bbb6df2d8e719cf0c453f0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b222e-103">Método de GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b222e-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b222e-104">Obtém o resultado de agente de configuração associado uma tarefa específica.</span><span class="sxs-lookup"><span data-stu-id="b222e-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="b222e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b222e-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="b222e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b222e-106">Parameters</span></span>
----------

<span data-ttu-id="b222e-107">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b222e-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="b222e-108">O ID da tarefa para o qual pretende obter dados de saída.</span><span class="sxs-lookup"><span data-stu-id="b222e-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="b222e-109">*resumeOutputBookmark* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b222e-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="b222e-110">Especifica que o resultado deve ser uma continuação de um marcador anterior.</span><span class="sxs-lookup"><span data-stu-id="b222e-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="b222e-111">*output* \[out\]</span><span class="sxs-lookup"><span data-stu-id="b222e-111">*output* \[out\]</span></span>  
<span data-ttu-id="b222e-112">A saída para a tarefa especificada.</span><span class="sxs-lookup"><span data-stu-id="b222e-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="b222e-113">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="b222e-113">Return value</span></span>
------------

<span data-ttu-id="b222e-114">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="b222e-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b222e-115">Observações</span><span class="sxs-lookup"><span data-stu-id="b222e-115">Remarks</span></span>

<span data-ttu-id="b222e-116">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="b222e-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b222e-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b222e-117">Requirements</span></span>
------------
><span data-ttu-id="b222e-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b222e-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b222e-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b222e-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b222e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b222e-120">See also</span></span>


[<span data-ttu-id="b222e-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b222e-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



