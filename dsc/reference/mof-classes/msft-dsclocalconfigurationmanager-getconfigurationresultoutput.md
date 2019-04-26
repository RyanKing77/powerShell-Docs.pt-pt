---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078650"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7a3e2-103">Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="7a3e2-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7a3e2-104">Obtém o resultado de agente de configuração associado a uma tarefa específica.</span><span class="sxs-lookup"><span data-stu-id="7a3e2-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="7a3e2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7a3e2-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="7a3e2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7a3e2-106">Parameters</span></span>

<span data-ttu-id="7a3e2-107">*jobId* \[no\] o ID da tarefa do qual pretende obter dados de saída.</span><span class="sxs-lookup"><span data-stu-id="7a3e2-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="7a3e2-108">*resumeOutputBookmark* \[no\] Especifica que o resultado deve ser uma continuação de um marcador anterior.</span><span class="sxs-lookup"><span data-stu-id="7a3e2-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="7a3e2-109">*saída* \[horizontalmente\] a saída para o trabalho especificado.</span><span class="sxs-lookup"><span data-stu-id="7a3e2-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="7a3e2-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7a3e2-110">Return value</span></span>

<span data-ttu-id="7a3e2-111">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="7a3e2-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7a3e2-112">Observações</span><span class="sxs-lookup"><span data-stu-id="7a3e2-112">Remarks</span></span>

<span data-ttu-id="7a3e2-113">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="7a3e2-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7a3e2-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7a3e2-114">Requirements</span></span>

<span data-ttu-id="7a3e2-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7a3e2-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="7a3e2-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7a3e2-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="7a3e2-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a3e2-117">See also</span></span>

[<span data-ttu-id="7a3e2-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7a3e2-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)