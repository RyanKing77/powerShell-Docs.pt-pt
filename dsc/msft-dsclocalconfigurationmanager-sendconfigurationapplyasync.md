---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de SendConfigurationApplyAsync da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: e680d510aaac097f4f0de80660274230e028ed45
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a060f-103">Método de SendConfigurationApplyAsync da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="a060f-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a060f-104">Envia o documento de configuração no modo assíncrono para o nó gerido e utiliza o agente de configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="a060f-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="a060f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a060f-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="a060f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a060f-106">Parameters</span></span>
----------

<span data-ttu-id="a060f-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="a060f-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="a060f-108">Os dados de ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="a060f-108">The environment data for the configuration.</span></span>

<span data-ttu-id="a060f-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="a060f-109">*force* \[in\]</span></span>  
<span data-ttu-id="a060f-110">**Verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="a060f-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="a060f-111">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="a060f-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="a060f-112">O ID da tarefa para o qual pretende enviar a configuração.</span><span class="sxs-lookup"><span data-stu-id="a060f-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="a060f-113">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="a060f-113">Return value</span></span>
------------

<span data-ttu-id="a060f-114">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="a060f-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a060f-115">Observações</span><span class="sxs-lookup"><span data-stu-id="a060f-115">Remarks</span></span>

<span data-ttu-id="a060f-116">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="a060f-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a060f-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a060f-117">Requirements</span></span>
------------
><span data-ttu-id="a060f-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a060f-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a060f-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a060f-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a060f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a060f-120">See also</span></span>


[<span data-ttu-id="a060f-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a060f-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



