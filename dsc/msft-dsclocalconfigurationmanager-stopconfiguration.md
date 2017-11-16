---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de StopConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: f0b550615b20f07f99c8ed7009805c45794bfe22
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2f64c-103">Método de StopConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2f64c-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2f64c-104">Interrompe a alteração da configuração que está em curso.</span><span class="sxs-lookup"><span data-stu-id="2f64c-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="2f64c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2f64c-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="2f64c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2f64c-106">Parameters</span></span>
----------

<span data-ttu-id="2f64c-107">*Forçar* \[no\]</span><span class="sxs-lookup"><span data-stu-id="2f64c-107">*force* \[in\]</span></span>  
<span data-ttu-id="2f64c-108">**Verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="2f64c-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="2f64c-109">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="2f64c-109">Return value</span></span>
------------

<span data-ttu-id="2f64c-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="2f64c-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2f64c-111">Observações</span><span class="sxs-lookup"><span data-stu-id="2f64c-111">Remarks</span></span>

<span data-ttu-id="2f64c-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="2f64c-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2f64c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2f64c-113">Requirements</span></span>
------------
><span data-ttu-id="2f64c-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2f64c-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="2f64c-115">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2f64c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="2f64c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f64c-116">See also</span></span>


[<span data-ttu-id="2f64c-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2f64c-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



