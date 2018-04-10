---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Método SendConfigurationApply da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 8edf8c55089e767394ba21b42fe74072777a45c9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="58c7c-103">Método SendConfigurationApply da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="58c7c-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="58c7c-104">Envia o documento de configuração para o nó gerido e utiliza o agente de configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="58c7c-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="58c7c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58c7c-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="58c7c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="58c7c-106">Parameters</span></span>
----------

<span data-ttu-id="58c7c-107">*ConfigurationData* \[no\] os dados de ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="58c7c-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="58c7c-108">*Forçar* \[no\] **verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="58c7c-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="58c7c-109">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="58c7c-109">Return value</span></span>
------------

<span data-ttu-id="58c7c-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="58c7c-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="58c7c-111">Observações</span><span class="sxs-lookup"><span data-stu-id="58c7c-111">Remarks</span></span>

<span data-ttu-id="58c7c-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="58c7c-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="58c7c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="58c7c-113">Requirements</span></span>
------------
><span data-ttu-id="58c7c-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="58c7c-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="58c7c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="58c7c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="58c7c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58c7c-116">See also</span></span>


[<span data-ttu-id="58c7c-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="58c7c-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)