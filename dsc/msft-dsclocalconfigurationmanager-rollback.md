---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de reversão da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: a219703389405c0dd457d0b2e0b1c54b9c28f559
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8c9ee-103">Método de reversão da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="8c9ee-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8c9ee-104">Reverte a configuração para uma versão anterior.</span><span class="sxs-lookup"><span data-stu-id="8c9ee-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="8c9ee-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c9ee-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="8c9ee-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8c9ee-106">Parameters</span></span>
----------

<span data-ttu-id="8c9ee-107">*configurationNumber* \[in\]</span><span class="sxs-lookup"><span data-stu-id="8c9ee-107">*configurationNumber* \[in\]</span></span>  
<span data-ttu-id="8c9ee-108">Especifica a configuração solicitada.</span><span class="sxs-lookup"><span data-stu-id="8c9ee-108">Specifies the requested configuration.</span></span> 

## <a name="return-value"></a><span data-ttu-id="8c9ee-109">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="8c9ee-109">Return value</span></span>
------------

<span data-ttu-id="8c9ee-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="8c9ee-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8c9ee-111">Observações</span><span class="sxs-lookup"><span data-stu-id="8c9ee-111">Remarks</span></span>

<span data-ttu-id="8c9ee-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="8c9ee-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8c9ee-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8c9ee-113">Requirements</span></span>
------------
><span data-ttu-id="8c9ee-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8c9ee-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="8c9ee-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8c9ee-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="8c9ee-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c9ee-116">See also</span></span>


[<span data-ttu-id="8c9ee-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8c9ee-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



