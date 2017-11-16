---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: febaf972a2a452eb9aaf3ec7fbc5e41f3f463a58
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e0a0b-103">Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e0a0b-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e0a0b-104">Utiliza o agente de configuração para aplicar a configuração que está pendente.</span><span class="sxs-lookup"><span data-stu-id="e0a0b-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span> 

<span data-ttu-id="e0a0b-105">Se não houver nenhuma configuração pendentes, este método volta a configuração atual.</span><span class="sxs-lookup"><span data-stu-id="e0a0b-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="e0a0b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0a0b-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="e0a0b-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e0a0b-107">Parameters</span></span>
----------

<span data-ttu-id="e0a0b-108">*Forçar* \[no\]</span><span class="sxs-lookup"><span data-stu-id="e0a0b-108">*force* \[in\]</span></span>  
<span data-ttu-id="e0a0b-109">Se este for **verdadeiro**, a configuração atual é reaplicada, mesmo se houver uma configuração pendentes.</span><span class="sxs-lookup"><span data-stu-id="e0a0b-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="e0a0b-110">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="e0a0b-110">Return value</span></span>
------------

<span data-ttu-id="e0a0b-111">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="e0a0b-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e0a0b-112">Observações</span><span class="sxs-lookup"><span data-stu-id="e0a0b-112">Remarks</span></span>

<span data-ttu-id="e0a0b-113">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="e0a0b-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e0a0b-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e0a0b-114">Requirements</span></span>
------------
><span data-ttu-id="e0a0b-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e0a0b-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e0a0b-116">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e0a0b-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e0a0b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0a0b-117">See also</span></span>


[<span data-ttu-id="e0a0b-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e0a0b-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



