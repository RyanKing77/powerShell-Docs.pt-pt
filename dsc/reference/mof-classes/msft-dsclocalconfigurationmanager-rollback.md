---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método rollBack
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727018"
---
# <a name="rollback-method"></a><span data-ttu-id="d0afa-103">Método rollBack</span><span class="sxs-lookup"><span data-stu-id="d0afa-103">RollBack method</span></span>

<span data-ttu-id="d0afa-104">Reverte a configuração para uma versão anterior.</span><span class="sxs-lookup"><span data-stu-id="d0afa-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="d0afa-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0afa-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="d0afa-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d0afa-106">Parameters</span></span>

<span data-ttu-id="d0afa-107">*configurationNumber* \[no\] Especifica a configuração pedida.</span><span class="sxs-lookup"><span data-stu-id="d0afa-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="d0afa-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d0afa-108">Return value</span></span>

<span data-ttu-id="d0afa-109">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="d0afa-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0afa-110">Observações</span><span class="sxs-lookup"><span data-stu-id="d0afa-110">Remarks</span></span>

<span data-ttu-id="d0afa-111">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="d0afa-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d0afa-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d0afa-112">Requirements</span></span>

<span data-ttu-id="d0afa-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d0afa-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d0afa-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d0afa-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d0afa-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0afa-115">See also</span></span>

[<span data-ttu-id="d0afa-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d0afa-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
