---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9fe41fa806a6abff1d36dadd0c041a5cf0e78caf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e9953-103">Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e9953-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e9953-104">Ativa a depuração de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="e9953-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="e9953-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9953-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="e9953-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e9953-106">Parameters</span></span>
----------

<span data-ttu-id="e9953-107">*BreakAll* \[no\] define um ponto de interrupção em cada linha no script de recursos.</span><span class="sxs-lookup"><span data-stu-id="e9953-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="e9953-108">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="e9953-108">Return value</span></span>
------------

<span data-ttu-id="e9953-109">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="e9953-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e9953-110">Observações</span><span class="sxs-lookup"><span data-stu-id="e9953-110">Remarks</span></span>

<span data-ttu-id="e9953-111">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="e9953-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e9953-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e9953-112">Requirements</span></span>
------------
><span data-ttu-id="e9953-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e9953-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e9953-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e9953-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e9953-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9953-115">See also</span></span>


[<span data-ttu-id="e9953-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e9953-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)