---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 350555220757b1939b1de34ab423e963635eb53c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ffab7-103">Método de SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ffab7-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ffab7-104">Define as definições do Gestor de configuração locais que são utilizadas para controlar o agente de configuração.</span><span class="sxs-lookup"><span data-stu-id="ffab7-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="ffab7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ffab7-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="ffab7-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ffab7-106">Parameters</span></span>
----------

<span data-ttu-id="ffab7-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="ffab7-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="ffab7-108">Os dados de ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="ffab7-108">The environment data for the configuration.</span></span>

<span data-ttu-id="ffab7-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="ffab7-109">*force* \[in\]</span></span>  
<span data-ttu-id="ffab7-110">**Verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="ffab7-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="ffab7-111">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="ffab7-111">Return value</span></span>
------------

<span data-ttu-id="ffab7-112">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="ffab7-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ffab7-113">Observações</span><span class="sxs-lookup"><span data-stu-id="ffab7-113">Remarks</span></span>

<span data-ttu-id="ffab7-114">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="ffab7-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ffab7-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ffab7-115">Requirements</span></span>
------------
><span data-ttu-id="ffab7-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ffab7-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ffab7-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ffab7-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ffab7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ffab7-118">See also</span></span>


[<span data-ttu-id="ffab7-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ffab7-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



