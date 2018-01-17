---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de StopConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 66d00cb40750e91e4b369a2e8cebb449697406d9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4dacb-103">Método de StopConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4dacb-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4dacb-104">Interrompe a alteração da configuração que está em curso.</span><span class="sxs-lookup"><span data-stu-id="4dacb-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="4dacb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4dacb-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="4dacb-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4dacb-106">Parameters</span></span>
----------

<span data-ttu-id="4dacb-107">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="4dacb-107">*force* \[in\]</span></span>  
<span data-ttu-id="4dacb-108">**Verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="4dacb-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="4dacb-109">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="4dacb-109">Return value</span></span>
------------

<span data-ttu-id="4dacb-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="4dacb-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4dacb-111">Observações</span><span class="sxs-lookup"><span data-stu-id="4dacb-111">Remarks</span></span>

<span data-ttu-id="4dacb-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="4dacb-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4dacb-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4dacb-113">Requirements</span></span>
------------
><span data-ttu-id="4dacb-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4dacb-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4dacb-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4dacb-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4dacb-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4dacb-116">See also</span></span>


[<span data-ttu-id="4dacb-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4dacb-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



