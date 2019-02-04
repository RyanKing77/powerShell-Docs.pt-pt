---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método RollBack da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688582"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4a75a-103">Método RollBack da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4a75a-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4a75a-104">Reverte a configuração para uma versão anterior.</span><span class="sxs-lookup"><span data-stu-id="4a75a-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="4a75a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a75a-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="4a75a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4a75a-106">Parameters</span></span>

<span data-ttu-id="4a75a-107">*configurationNumber* \[no\] Especifica a configuração pedida.</span><span class="sxs-lookup"><span data-stu-id="4a75a-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="4a75a-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4a75a-108">Return value</span></span>

<span data-ttu-id="4a75a-109">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="4a75a-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4a75a-110">Observações</span><span class="sxs-lookup"><span data-stu-id="4a75a-110">Remarks</span></span>

<span data-ttu-id="4a75a-111">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="4a75a-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4a75a-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a75a-112">Requirements</span></span>

<span data-ttu-id="4a75a-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4a75a-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="4a75a-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4a75a-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="4a75a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a75a-115">See also</span></span>

[<span data-ttu-id="4a75a-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4a75a-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)