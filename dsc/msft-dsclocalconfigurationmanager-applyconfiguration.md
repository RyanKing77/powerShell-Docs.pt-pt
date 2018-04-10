---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2844e354e0d054b13b92267ce314536d88a1c33e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4c1eb-103">Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4c1eb-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4c1eb-104">Utiliza o agente de configuração para aplicar a configuração que está pendente.</span><span class="sxs-lookup"><span data-stu-id="4c1eb-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="4c1eb-105">Se não houver nenhuma configuração pendentes, este método volta a configuração atual.</span><span class="sxs-lookup"><span data-stu-id="4c1eb-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="4c1eb-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c1eb-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="4c1eb-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4c1eb-107">Parameters</span></span>
----------

<span data-ttu-id="4c1eb-108">*Forçar* \[no\] se este for **verdadeiro**, a configuração atual é reaplicada, mesmo se houver uma configuração pendentes.</span><span class="sxs-lookup"><span data-stu-id="4c1eb-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="4c1eb-109">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="4c1eb-109">Return value</span></span>
------------

<span data-ttu-id="4c1eb-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="4c1eb-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4c1eb-111">Observações</span><span class="sxs-lookup"><span data-stu-id="4c1eb-111">Remarks</span></span>

<span data-ttu-id="4c1eb-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="4c1eb-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4c1eb-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4c1eb-113">Requirements</span></span>
------------
><span data-ttu-id="4c1eb-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4c1eb-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4c1eb-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4c1eb-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4c1eb-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c1eb-116">See also</span></span>


[<span data-ttu-id="4c1eb-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4c1eb-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)