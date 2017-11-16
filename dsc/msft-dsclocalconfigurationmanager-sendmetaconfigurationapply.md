---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: d8ddc9d99f0d74ad907a6e39ae0e8ac14159be16
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d6c11-103">Método de SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d6c11-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d6c11-104">Define as definições do Gestor de configuração locais que são utilizadas para controlar o agente de configuração.</span><span class="sxs-lookup"><span data-stu-id="d6c11-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="d6c11-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6c11-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="d6c11-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d6c11-106">Parameters</span></span>
----------

<span data-ttu-id="d6c11-107">*ConfigurationData* \[no\]</span><span class="sxs-lookup"><span data-stu-id="d6c11-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="d6c11-108">Os dados de ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="d6c11-108">The environment data for the configuration.</span></span>

<span data-ttu-id="d6c11-109">*Forçar* \[no\]</span><span class="sxs-lookup"><span data-stu-id="d6c11-109">*force* \[in\]</span></span>  
<span data-ttu-id="d6c11-110">**Verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="d6c11-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="d6c11-111">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="d6c11-111">Return value</span></span>
------------

<span data-ttu-id="d6c11-112">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="d6c11-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d6c11-113">Observações</span><span class="sxs-lookup"><span data-stu-id="d6c11-113">Remarks</span></span>

<span data-ttu-id="d6c11-114">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="d6c11-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d6c11-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6c11-115">Requirements</span></span>
------------
><span data-ttu-id="d6c11-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d6c11-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d6c11-117">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d6c11-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d6c11-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6c11-118">See also</span></span>


[<span data-ttu-id="d6c11-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d6c11-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



