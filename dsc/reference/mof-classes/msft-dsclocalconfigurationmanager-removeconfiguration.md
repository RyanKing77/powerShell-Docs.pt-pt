---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método RemoveConfiguration
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734395"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="c441d-103">Método RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="c441d-103">RemoveConfiguration method</span></span>

<span data-ttu-id="c441d-104">Remove os ficheiros de configuração.</span><span class="sxs-lookup"><span data-stu-id="c441d-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="c441d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c441d-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="c441d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c441d-106">Parameters</span></span>

<span data-ttu-id="c441d-107">*Fase* \[no\] Especifica qual documento de configuração para remover.</span><span class="sxs-lookup"><span data-stu-id="c441d-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="c441d-108">Os seguintes valores são válidos:</span><span class="sxs-lookup"><span data-stu-id="c441d-108">The following values are valid:</span></span>

|<span data-ttu-id="c441d-109">Value</span><span class="sxs-lookup"><span data-stu-id="c441d-109">Value</span></span> |<span data-ttu-id="c441d-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="c441d-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="c441d-111">**1**</span><span class="sxs-lookup"><span data-stu-id="c441d-111">**1**</span></span> | <span data-ttu-id="c441d-112">O **atual** documento de configuração (current.mof).</span><span class="sxs-lookup"><span data-stu-id="c441d-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="c441d-113">**2**</span><span class="sxs-lookup"><span data-stu-id="c441d-113">**2**</span></span> | <span data-ttu-id="c441d-114">O **pendente** documento de configuração (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="c441d-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="c441d-115">**4**</span><span class="sxs-lookup"><span data-stu-id="c441d-115">**4**</span></span> | <span data-ttu-id="c441d-116">O **Previous** documento de configuração (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="c441d-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="c441d-117">*Forçar* \[na\] **verdadeiro** para forçar a remoção da configuração.</span><span class="sxs-lookup"><span data-stu-id="c441d-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="c441d-118">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c441d-118">Return value</span></span>

<span data-ttu-id="c441d-119">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="c441d-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c441d-120">Observações</span><span class="sxs-lookup"><span data-stu-id="c441d-120">Remarks</span></span>

<span data-ttu-id="c441d-121">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="c441d-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c441d-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c441d-122">Requirements</span></span>

<span data-ttu-id="c441d-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c441d-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c441d-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c441d-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c441d-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c441d-125">See also</span></span>

[<span data-ttu-id="c441d-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c441d-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
