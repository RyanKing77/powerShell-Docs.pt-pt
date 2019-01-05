---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método RollBack da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048497"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d0752-103">Método RollBack da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d0752-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d0752-104">Reverte a configuração para uma versão anterior.</span><span class="sxs-lookup"><span data-stu-id="d0752-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="d0752-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0752-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="d0752-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d0752-106">Parameters</span></span>

<span data-ttu-id="d0752-107">*configurationNumber* \[no\] Especifica a configuração pedida.</span><span class="sxs-lookup"><span data-stu-id="d0752-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="d0752-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d0752-108">Return value</span></span>

<span data-ttu-id="d0752-109">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="d0752-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0752-110">Observações</span><span class="sxs-lookup"><span data-stu-id="d0752-110">Remarks</span></span>

<span data-ttu-id="d0752-111">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="d0752-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d0752-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d0752-112">Requirements</span></span>

<span data-ttu-id="d0752-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d0752-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d0752-114">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d0752-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d0752-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0752-115">See also</span></span>

[<span data-ttu-id="d0752-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d0752-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)