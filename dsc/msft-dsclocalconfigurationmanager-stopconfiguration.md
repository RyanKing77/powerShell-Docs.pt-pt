---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Método StopConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: dadb6912af2e4450381958ed465799056da49946
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="30e71-103">Método StopConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="30e71-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="30e71-104">Interrompe a alteração da configuração que está em curso.</span><span class="sxs-lookup"><span data-stu-id="30e71-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="30e71-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30e71-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="30e71-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="30e71-106">Parameters</span></span>
----------

<span data-ttu-id="30e71-107">*Forçar* \[no\] **verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="30e71-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="30e71-108">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="30e71-108">Return value</span></span>
------------

<span data-ttu-id="30e71-109">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="30e71-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="30e71-110">Observações</span><span class="sxs-lookup"><span data-stu-id="30e71-110">Remarks</span></span>

<span data-ttu-id="30e71-111">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="30e71-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="30e71-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30e71-112">Requirements</span></span>
------------
><span data-ttu-id="30e71-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="30e71-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="30e71-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="30e71-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="30e71-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30e71-115">See also</span></span>


[<span data-ttu-id="30e71-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="30e71-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)