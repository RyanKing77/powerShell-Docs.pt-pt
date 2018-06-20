---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Método StopConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: aaed29cb81e2079c4673b621b81c52e109aa7b48
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218880"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="36c19-103">Método StopConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="36c19-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="36c19-104">Interrompe a alteração da configuração que está em curso.</span><span class="sxs-lookup"><span data-stu-id="36c19-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="36c19-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36c19-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="36c19-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="36c19-106">Parameters</span></span>
----------

<span data-ttu-id="36c19-107">*Forçar* \[no\] **verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="36c19-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="36c19-108">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="36c19-108">Return value</span></span>
------------

<span data-ttu-id="36c19-109">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="36c19-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="36c19-110">Observações</span><span class="sxs-lookup"><span data-stu-id="36c19-110">Remarks</span></span>

<span data-ttu-id="36c19-111">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="36c19-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="36c19-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="36c19-112">Requirements</span></span>
------------
><span data-ttu-id="36c19-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="36c19-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="36c19-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="36c19-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="36c19-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36c19-115">See also</span></span>


[<span data-ttu-id="36c19-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="36c19-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)