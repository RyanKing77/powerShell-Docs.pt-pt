---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ef8488246b2c8614452d32009e45535f0ff2e184
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="436a5-103">Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="436a5-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="436a5-104">Utiliza o agente de configuração para aplicar a configuração que está pendente.</span><span class="sxs-lookup"><span data-stu-id="436a5-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="436a5-105">Se não houver nenhuma configuração pendentes, este método volta a configuração atual.</span><span class="sxs-lookup"><span data-stu-id="436a5-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="436a5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="436a5-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="436a5-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="436a5-107">Parameters</span></span>
----------

<span data-ttu-id="436a5-108">*Forçar* \[no\] se este for **verdadeiro**, a configuração atual é reaplicada, mesmo se houver uma configuração pendentes.</span><span class="sxs-lookup"><span data-stu-id="436a5-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="436a5-109">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="436a5-109">Return value</span></span>
------------

<span data-ttu-id="436a5-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="436a5-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="436a5-111">Observações</span><span class="sxs-lookup"><span data-stu-id="436a5-111">Remarks</span></span>

<span data-ttu-id="436a5-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="436a5-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="436a5-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="436a5-113">Requirements</span></span>
------------
><span data-ttu-id="436a5-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="436a5-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="436a5-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="436a5-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="436a5-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="436a5-116">See also</span></span>


[<span data-ttu-id="436a5-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="436a5-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)