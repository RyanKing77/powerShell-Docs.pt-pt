---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e0ae8a50212b70841d210d7b2d666a2855218d1a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5ffcc-103">Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5ffcc-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5ffcc-104">Remove os ficheiros de configuração.</span><span class="sxs-lookup"><span data-stu-id="5ffcc-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="5ffcc-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ffcc-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="5ffcc-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ffcc-106">Parameters</span></span>
----------

<span data-ttu-id="5ffcc-107">*Fase* \[no\] Especifica o documento de configuração para remover.</span><span class="sxs-lookup"><span data-stu-id="5ffcc-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="5ffcc-108">Os seguintes valores são válidos:</span><span class="sxs-lookup"><span data-stu-id="5ffcc-108">The following values are valid:</span></span>

|<span data-ttu-id="5ffcc-109">Valor</span><span class="sxs-lookup"><span data-stu-id="5ffcc-109">Value</span></span> |<span data-ttu-id="5ffcc-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ffcc-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="5ffcc-111">**1**</span><span class="sxs-lookup"><span data-stu-id="5ffcc-111">**1**</span></span> | <span data-ttu-id="5ffcc-112">O **atual** documento de configuração (current.mof).</span><span class="sxs-lookup"><span data-stu-id="5ffcc-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="5ffcc-113">**2**</span><span class="sxs-lookup"><span data-stu-id="5ffcc-113">**2**</span></span> | <span data-ttu-id="5ffcc-114">O **pendente** documento de configuração (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="5ffcc-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="5ffcc-115">**4**</span><span class="sxs-lookup"><span data-stu-id="5ffcc-115">**4**</span></span> | <span data-ttu-id="5ffcc-116">O **anterior** documento de configuração (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="5ffcc-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="5ffcc-117">*Forçar* \[no\] **verdadeiro** para forçar a remoção da configuração.</span><span class="sxs-lookup"><span data-stu-id="5ffcc-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="5ffcc-118">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="5ffcc-118">Return value</span></span>
------------

<span data-ttu-id="5ffcc-119">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="5ffcc-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ffcc-120">Observações</span><span class="sxs-lookup"><span data-stu-id="5ffcc-120">Remarks</span></span>

<span data-ttu-id="5ffcc-121">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="5ffcc-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ffcc-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5ffcc-122">Requirements</span></span>
------------
><span data-ttu-id="5ffcc-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5ffcc-123">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5ffcc-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5ffcc-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="5ffcc-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ffcc-125">See also</span></span>


[<span data-ttu-id="5ffcc-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5ffcc-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)