---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: fa34a583af7c3fd46d99307d582973410e4c0e31
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="63aab-103">Método de EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="63aab-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="63aab-104">Ativa a depuração de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="63aab-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="63aab-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="63aab-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="63aab-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="63aab-106">Parameters</span></span>
----------

<span data-ttu-id="63aab-107">*BreakAll* \[in\]</span><span class="sxs-lookup"><span data-stu-id="63aab-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="63aab-108">Define um ponto de interrupção em cada linha no script de recursos.</span><span class="sxs-lookup"><span data-stu-id="63aab-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="63aab-109">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="63aab-109">Return value</span></span>
------------

<span data-ttu-id="63aab-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="63aab-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="63aab-111">Observações</span><span class="sxs-lookup"><span data-stu-id="63aab-111">Remarks</span></span>

<span data-ttu-id="63aab-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="63aab-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="63aab-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="63aab-113">Requirements</span></span>
------------
><span data-ttu-id="63aab-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="63aab-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="63aab-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="63aab-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="63aab-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63aab-116">See also</span></span>


[<span data-ttu-id="63aab-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="63aab-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



