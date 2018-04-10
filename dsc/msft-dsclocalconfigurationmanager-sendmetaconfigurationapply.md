---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Método SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ab82b239ddfdb4075d9440cd66343266b3c08eda
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b76f8-103">Método SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b76f8-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b76f8-104">Define as definições do Gestor de configuração locais que são utilizadas para controlar o agente de configuração.</span><span class="sxs-lookup"><span data-stu-id="b76f8-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="b76f8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b76f8-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="b76f8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b76f8-106">Parameters</span></span>
----------

<span data-ttu-id="b76f8-107">*ConfigurationData* \[no\] os dados de ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="b76f8-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="b76f8-108">*Forçar* \[no\] **verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="b76f8-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="b76f8-109">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="b76f8-109">Return value</span></span>
------------

<span data-ttu-id="b76f8-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="b76f8-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b76f8-111">Observações</span><span class="sxs-lookup"><span data-stu-id="b76f8-111">Remarks</span></span>

<span data-ttu-id="b76f8-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="b76f8-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b76f8-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b76f8-113">Requirements</span></span>
------------
><span data-ttu-id="b76f8-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b76f8-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b76f8-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b76f8-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b76f8-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b76f8-116">See also</span></span>


[<span data-ttu-id="b76f8-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b76f8-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)