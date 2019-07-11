---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método StopConfiguration
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726998"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="4f93e-103">Método StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="4f93e-103">StopConfiguration method</span></span>

<span data-ttu-id="4f93e-104">Interrompe a alteração da configuração que está em curso.</span><span class="sxs-lookup"><span data-stu-id="4f93e-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="4f93e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f93e-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="4f93e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4f93e-106">Parameters</span></span>

<span data-ttu-id="4f93e-107">*Forçar* \[na\] **verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="4f93e-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="4f93e-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4f93e-108">Return value</span></span>

<span data-ttu-id="4f93e-109">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="4f93e-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4f93e-110">Observações</span><span class="sxs-lookup"><span data-stu-id="4f93e-110">Remarks</span></span>

<span data-ttu-id="4f93e-111">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="4f93e-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4f93e-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4f93e-112">Requirements</span></span>

<span data-ttu-id="4f93e-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4f93e-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="4f93e-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4f93e-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="4f93e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f93e-115">See also</span></span>

[<span data-ttu-id="4f93e-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4f93e-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
