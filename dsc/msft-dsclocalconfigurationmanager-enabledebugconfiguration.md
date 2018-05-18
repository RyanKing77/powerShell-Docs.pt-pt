---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9e2a978f9d16abaed959be022229db4da5fd65bd
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bd72d-103">Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="bd72d-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bd72d-104">Ativa a depuração de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="bd72d-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="bd72d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd72d-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="bd72d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bd72d-106">Parameters</span></span>
----------

<span data-ttu-id="bd72d-107">*BreakAll* \[no\] define um ponto de interrupção em cada linha no script de recursos.</span><span class="sxs-lookup"><span data-stu-id="bd72d-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="bd72d-108">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="bd72d-108">Return value</span></span>
------------

<span data-ttu-id="bd72d-109">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="bd72d-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd72d-110">Observações</span><span class="sxs-lookup"><span data-stu-id="bd72d-110">Remarks</span></span>

<span data-ttu-id="bd72d-111">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="bd72d-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bd72d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bd72d-112">Requirements</span></span>
------------
><span data-ttu-id="bd72d-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bd72d-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="bd72d-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bd72d-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="bd72d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd72d-115">See also</span></span>


[<span data-ttu-id="bd72d-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bd72d-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)