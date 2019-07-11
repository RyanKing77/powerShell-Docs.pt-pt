---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método EnableDebugConfiguration
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727142"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="63907-103">Método EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="63907-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="63907-104">Permite a depuração de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="63907-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="63907-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="63907-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="63907-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="63907-106">Parameters</span></span>

<span data-ttu-id="63907-107">*BreakAll* \[no\] define um ponto de interrupção em cada linha do script de recursos.</span><span class="sxs-lookup"><span data-stu-id="63907-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="63907-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="63907-108">Return value</span></span>

<span data-ttu-id="63907-109">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="63907-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="63907-110">Observações</span><span class="sxs-lookup"><span data-stu-id="63907-110">Remarks</span></span>

<span data-ttu-id="63907-111">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="63907-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="63907-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="63907-112">Requirements</span></span>

<span data-ttu-id="63907-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="63907-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="63907-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="63907-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="63907-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63907-115">See also</span></span>

[<span data-ttu-id="63907-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="63907-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
