---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405124"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f8582-103">Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="f8582-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f8582-104">Obtém o resultado de agente de configuração associado a uma tarefa específica.</span><span class="sxs-lookup"><span data-stu-id="f8582-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="f8582-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f8582-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="f8582-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8582-106">Parameters</span></span>

<span data-ttu-id="f8582-107">*jobId* \[no\] o ID da tarefa do qual pretende obter dados de saída.</span><span class="sxs-lookup"><span data-stu-id="f8582-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="f8582-108">*resumeOutputBookmark* \[no\] Especifica que o resultado deve ser uma continuação de um marcador anterior.</span><span class="sxs-lookup"><span data-stu-id="f8582-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="f8582-109">*saída* \[horizontalmente\] a saída para o trabalho especificado.</span><span class="sxs-lookup"><span data-stu-id="f8582-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="f8582-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f8582-110">Return value</span></span>

<span data-ttu-id="f8582-111">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="f8582-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8582-112">Observações</span><span class="sxs-lookup"><span data-stu-id="f8582-112">Remarks</span></span>

<span data-ttu-id="f8582-113">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="f8582-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f8582-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f8582-114">Requirements</span></span>

<span data-ttu-id="f8582-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f8582-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f8582-116">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f8582-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f8582-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8582-117">See also</span></span>

[<span data-ttu-id="f8582-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f8582-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)