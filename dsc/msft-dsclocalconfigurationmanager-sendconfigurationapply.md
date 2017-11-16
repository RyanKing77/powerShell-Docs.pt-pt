---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de SendConfigurationApply da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 9552fd5b5feb862fbe8ef95a7746776e7fe2f5c8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="52374-103">Método de SendConfigurationApply da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="52374-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="52374-104">Envia o documento de configuração para o nó gerido e utiliza o agente de configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="52374-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="52374-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52374-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="52374-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="52374-106">Parameters</span></span>
----------

<span data-ttu-id="52374-107">*ConfigurationData* \[no\]</span><span class="sxs-lookup"><span data-stu-id="52374-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="52374-108">Os dados de ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="52374-108">The environment data for the configuration.</span></span>

<span data-ttu-id="52374-109">*Forçar* \[no\]</span><span class="sxs-lookup"><span data-stu-id="52374-109">*force* \[in\]</span></span>  
<span data-ttu-id="52374-110">**Verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="52374-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="52374-111">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="52374-111">Return value</span></span>
------------

<span data-ttu-id="52374-112">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="52374-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="52374-113">Observações</span><span class="sxs-lookup"><span data-stu-id="52374-113">Remarks</span></span>

<span data-ttu-id="52374-114">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="52374-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="52374-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="52374-115">Requirements</span></span>
------------
><span data-ttu-id="52374-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="52374-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="52374-117">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="52374-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="52374-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52374-118">See also</span></span>


[<span data-ttu-id="52374-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="52374-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



