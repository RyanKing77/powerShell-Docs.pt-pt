---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Método RollBack da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c0a801c4037921e700e447d1434e246df0a63a4f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="01e30-103">Método RollBack da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="01e30-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="01e30-104">Reverte a configuração para uma versão anterior.</span><span class="sxs-lookup"><span data-stu-id="01e30-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="01e30-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="01e30-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="01e30-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="01e30-106">Parameters</span></span>
----------

<span data-ttu-id="01e30-107">*configurationNumber* \[no\] Especifica a configuração solicitada.</span><span class="sxs-lookup"><span data-stu-id="01e30-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="01e30-108">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="01e30-108">Return value</span></span>
------------

<span data-ttu-id="01e30-109">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="01e30-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="01e30-110">Observações</span><span class="sxs-lookup"><span data-stu-id="01e30-110">Remarks</span></span>

<span data-ttu-id="01e30-111">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="01e30-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="01e30-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="01e30-112">Requirements</span></span>
------------
><span data-ttu-id="01e30-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="01e30-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="01e30-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="01e30-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="01e30-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01e30-115">See also</span></span>


[<span data-ttu-id="01e30-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="01e30-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)