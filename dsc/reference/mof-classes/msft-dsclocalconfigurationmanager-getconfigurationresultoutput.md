---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método GetConfigurationResultOutput
ms.openlocfilehash: 480e710ce1a208253f0e664474c3e9bab296066a
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727127"
---
# <a name="getconfigurationresultoutput-method"></a><span data-ttu-id="0f1db-103">Método GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="0f1db-103">GetConfigurationResultOutput method</span></span>

<span data-ttu-id="0f1db-104">Obtém o resultado de agente de configuração associado a uma tarefa específica.</span><span class="sxs-lookup"><span data-stu-id="0f1db-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f1db-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f1db-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="0f1db-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0f1db-106">Parameters</span></span>

<span data-ttu-id="0f1db-107">*jobId* \[no\] o ID da tarefa do qual pretende obter dados de saída.</span><span class="sxs-lookup"><span data-stu-id="0f1db-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="0f1db-108">*resumeOutputBookmark* \[no\] Especifica que o resultado deve ser uma continuação de um marcador anterior.</span><span class="sxs-lookup"><span data-stu-id="0f1db-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="0f1db-109">*saída* \[horizontalmente\] a saída para o trabalho especificado.</span><span class="sxs-lookup"><span data-stu-id="0f1db-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="0f1db-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0f1db-110">Return value</span></span>

<span data-ttu-id="0f1db-111">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="0f1db-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f1db-112">Observações</span><span class="sxs-lookup"><span data-stu-id="0f1db-112">Remarks</span></span>

<span data-ttu-id="0f1db-113">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="0f1db-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0f1db-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0f1db-114">Requirements</span></span>

<span data-ttu-id="0f1db-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0f1db-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0f1db-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0f1db-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0f1db-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f1db-117">See also</span></span>

[<span data-ttu-id="0f1db-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0f1db-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
