---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 7220c972b3f43b4697cf71df54d2d43881938367
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4b0bd-103">Método de EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4b0bd-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4b0bd-104">Ativa a depuração de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="4b0bd-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="4b0bd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b0bd-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="4b0bd-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4b0bd-106">Parameters</span></span>
----------

<span data-ttu-id="4b0bd-107">*BreakAll* \[no\]</span><span class="sxs-lookup"><span data-stu-id="4b0bd-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="4b0bd-108">Define um ponto de interrupção em cada linha no script de recursos.</span><span class="sxs-lookup"><span data-stu-id="4b0bd-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="4b0bd-109">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="4b0bd-109">Return value</span></span>
------------

<span data-ttu-id="4b0bd-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="4b0bd-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4b0bd-111">Observações</span><span class="sxs-lookup"><span data-stu-id="4b0bd-111">Remarks</span></span>

<span data-ttu-id="4b0bd-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="4b0bd-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4b0bd-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b0bd-113">Requirements</span></span>
------------
><span data-ttu-id="4b0bd-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4b0bd-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4b0bd-115">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4b0bd-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4b0bd-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b0bd-116">See also</span></span>


[<span data-ttu-id="4b0bd-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4b0bd-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



