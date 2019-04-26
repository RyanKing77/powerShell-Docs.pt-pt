---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método RollBack da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078372"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b3a96-103">Método RollBack da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b3a96-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b3a96-104">Reverte a configuração para uma versão anterior.</span><span class="sxs-lookup"><span data-stu-id="b3a96-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="b3a96-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3a96-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="b3a96-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b3a96-106">Parameters</span></span>

<span data-ttu-id="b3a96-107">*configurationNumber* \[no\] Especifica a configuração pedida.</span><span class="sxs-lookup"><span data-stu-id="b3a96-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="b3a96-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b3a96-108">Return value</span></span>

<span data-ttu-id="b3a96-109">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="b3a96-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b3a96-110">Observações</span><span class="sxs-lookup"><span data-stu-id="b3a96-110">Remarks</span></span>

<span data-ttu-id="b3a96-111">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="b3a96-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b3a96-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b3a96-112">Requirements</span></span>

<span data-ttu-id="b3a96-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b3a96-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b3a96-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b3a96-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b3a96-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3a96-115">See also</span></span>

[<span data-ttu-id="b3a96-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b3a96-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)