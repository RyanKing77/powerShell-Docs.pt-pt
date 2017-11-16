---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de SendConfigurationApplyAsync da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: e680bfd1c5b39d364c90cf5ef6b43d0a568af23a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="28898-103">Método de SendConfigurationApplyAsync da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="28898-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="28898-104">Envia o documento de configuração no modo assíncrono para o nó gerido e utiliza o agente de configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="28898-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="28898-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28898-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="28898-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="28898-106">Parameters</span></span>
----------

<span data-ttu-id="28898-107">*ConfigurationData* \[no\]</span><span class="sxs-lookup"><span data-stu-id="28898-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="28898-108">Os dados de ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="28898-108">The environment data for the configuration.</span></span>

<span data-ttu-id="28898-109">*Forçar* \[no\]</span><span class="sxs-lookup"><span data-stu-id="28898-109">*force* \[in\]</span></span>  
<span data-ttu-id="28898-110">**Verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="28898-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="28898-111">*jobId* \[no\]</span><span class="sxs-lookup"><span data-stu-id="28898-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="28898-112">O ID da tarefa para o qual pretende enviar a configuração.</span><span class="sxs-lookup"><span data-stu-id="28898-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="28898-113">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="28898-113">Return value</span></span>
------------

<span data-ttu-id="28898-114">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="28898-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="28898-115">Observações</span><span class="sxs-lookup"><span data-stu-id="28898-115">Remarks</span></span>

<span data-ttu-id="28898-116">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="28898-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="28898-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="28898-117">Requirements</span></span>
------------
><span data-ttu-id="28898-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="28898-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="28898-119">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="28898-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="28898-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28898-120">See also</span></span>


[<span data-ttu-id="28898-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="28898-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



