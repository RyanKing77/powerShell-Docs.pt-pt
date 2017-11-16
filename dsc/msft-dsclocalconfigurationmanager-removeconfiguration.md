---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: faa113c442b80eea3ac474220b098b7d80ec50a8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="effcb-103">Método de RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="effcb-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="effcb-104">Remove os ficheiros de configuração.</span><span class="sxs-lookup"><span data-stu-id="effcb-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="effcb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="effcb-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="effcb-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="effcb-106">Parameters</span></span>
----------

<span data-ttu-id="effcb-107">*Fase* \[no\]</span><span class="sxs-lookup"><span data-stu-id="effcb-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="effcb-108">Especifica o documento de configuração para remover.</span><span class="sxs-lookup"><span data-stu-id="effcb-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="effcb-109">Os seguintes valores são válidos:</span><span class="sxs-lookup"><span data-stu-id="effcb-109">The following values are valid:</span></span>

|<span data-ttu-id="effcb-110">Valor</span><span class="sxs-lookup"><span data-stu-id="effcb-110">Value</span></span> |<span data-ttu-id="effcb-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="effcb-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="effcb-112">**1**</span><span class="sxs-lookup"><span data-stu-id="effcb-112">**1**</span></span> | <span data-ttu-id="effcb-113">O **atual** documento de configuração (current.mof).</span><span class="sxs-lookup"><span data-stu-id="effcb-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="effcb-114">**2**</span><span class="sxs-lookup"><span data-stu-id="effcb-114">**2**</span></span> | <span data-ttu-id="effcb-115">O **pendente** documento de configuração (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="effcb-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="effcb-116">**4**</span><span class="sxs-lookup"><span data-stu-id="effcb-116">**4**</span></span> | <span data-ttu-id="effcb-117">O **anterior** documento de configuração (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="effcb-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="effcb-118">*Force* \[no\]</span><span class="sxs-lookup"><span data-stu-id="effcb-118">*Force* \[in\]</span></span>  
<span data-ttu-id="effcb-119">**Verdadeiro** para forçar a remoção da configuração.</span><span class="sxs-lookup"><span data-stu-id="effcb-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="effcb-120">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="effcb-120">Return value</span></span>
------------

<span data-ttu-id="effcb-121">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="effcb-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="effcb-122">Observações</span><span class="sxs-lookup"><span data-stu-id="effcb-122">Remarks</span></span>

<span data-ttu-id="effcb-123">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="effcb-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="effcb-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="effcb-124">Requirements</span></span>
------------
><span data-ttu-id="effcb-125">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="effcb-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="effcb-126">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="effcb-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="effcb-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="effcb-127">See also</span></span>


[<span data-ttu-id="effcb-128">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="effcb-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



