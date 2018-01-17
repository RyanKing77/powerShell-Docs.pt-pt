---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de SendConfigurationApply da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 20f732d35860cccde4e507dc6916e27d0cf8c5f6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8a2c0-103">Método de SendConfigurationApply da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="8a2c0-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8a2c0-104">Envia o documento de configuração para o nó gerido e utiliza o agente de configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="8a2c0-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="8a2c0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a2c0-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="8a2c0-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8a2c0-106">Parameters</span></span>
----------

<span data-ttu-id="8a2c0-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="8a2c0-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="8a2c0-108">Os dados de ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="8a2c0-108">The environment data for the configuration.</span></span>

<span data-ttu-id="8a2c0-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="8a2c0-109">*force* \[in\]</span></span>  
<span data-ttu-id="8a2c0-110">**Verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="8a2c0-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="8a2c0-111">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="8a2c0-111">Return value</span></span>
------------

<span data-ttu-id="8a2c0-112">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="8a2c0-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8a2c0-113">Observações</span><span class="sxs-lookup"><span data-stu-id="8a2c0-113">Remarks</span></span>

<span data-ttu-id="8a2c0-114">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="8a2c0-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8a2c0-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8a2c0-115">Requirements</span></span>
------------
><span data-ttu-id="8a2c0-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8a2c0-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="8a2c0-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8a2c0-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="8a2c0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a2c0-118">See also</span></span>


[<span data-ttu-id="8a2c0-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8a2c0-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



