---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de reversão da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: b8597e3eb7872d9894863fb02d927c9f475da44c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="78704-103">Método de reversão da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="78704-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="78704-104">Reverte a configuração para uma versão anterior.</span><span class="sxs-lookup"><span data-stu-id="78704-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="78704-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78704-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="78704-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="78704-106">Parameters</span></span>
----------

<span data-ttu-id="78704-107">*configurationNumber* \[no\]</span><span class="sxs-lookup"><span data-stu-id="78704-107">*configurationNumber* \[in\]</span></span>  
<span data-ttu-id="78704-108">Especifica a configuração solicitada.</span><span class="sxs-lookup"><span data-stu-id="78704-108">Specifies the requested configuration.</span></span> 

## <a name="return-value"></a><span data-ttu-id="78704-109">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="78704-109">Return value</span></span>
------------

<span data-ttu-id="78704-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="78704-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="78704-111">Observações</span><span class="sxs-lookup"><span data-stu-id="78704-111">Remarks</span></span>

<span data-ttu-id="78704-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="78704-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="78704-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="78704-113">Requirements</span></span>
------------
><span data-ttu-id="78704-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="78704-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="78704-115">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="78704-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="78704-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78704-116">See also</span></span>


[<span data-ttu-id="78704-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="78704-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



