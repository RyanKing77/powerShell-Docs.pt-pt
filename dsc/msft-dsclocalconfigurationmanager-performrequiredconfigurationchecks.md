---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de PerformRequiredConfigurationChecks da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 26110b3920104da7343b8d55cf63440c12accbbc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d9220-103">Método de PerformRequiredConfigurationChecks da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d9220-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d9220-104">Inicia uma verificação de consistência utilizando o Programador de tarefas.</span><span class="sxs-lookup"><span data-stu-id="d9220-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="d9220-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9220-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="d9220-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d9220-106">Parameters</span></span>
----------

<span data-ttu-id="d9220-107">*Sinalizadores* \[no\]</span><span class="sxs-lookup"><span data-stu-id="d9220-107">*Flags* \[in\]</span></span>  
<span data-ttu-id="d9220-108">Uma máscara de bits que especifica o tipo de verificação de consistência para ser executada.</span><span class="sxs-lookup"><span data-stu-id="d9220-108">A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="d9220-109">Os seguintes valores são válidos e podem ser combinados utilizando um bit a bit **ou** operação:</span><span class="sxs-lookup"><span data-stu-id="d9220-109">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="d9220-110">Valor</span><span class="sxs-lookup"><span data-stu-id="d9220-110">Value</span></span> |<span data-ttu-id="d9220-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9220-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="d9220-112">**1**</span><span class="sxs-lookup"><span data-stu-id="d9220-112">**1**</span></span> | <span data-ttu-id="d9220-113">Uma verificação de consistência normal.</span><span class="sxs-lookup"><span data-stu-id="d9220-113">A normal consistency check.</span></span> |
|<span data-ttu-id="d9220-114">**2**</span><span class="sxs-lookup"><span data-stu-id="d9220-114">**2**</span></span> | <span data-ttu-id="d9220-115">Uma continuação de uma verificação de consistência após um reinício.</span><span class="sxs-lookup"><span data-stu-id="d9220-115">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="d9220-116">Este valor não deve ser combinado com outros valores.</span><span class="sxs-lookup"><span data-stu-id="d9220-116">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="d9220-117">**4**</span><span class="sxs-lookup"><span data-stu-id="d9220-117">**4**</span></span> | <span data-ttu-id="d9220-118">A configuração deve ser solicitada a partir do servidor de solicitação especificado na configuração meta da para o nó.</span><span class="sxs-lookup"><span data-stu-id="d9220-118">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="d9220-119">Este valor deve sempre ser combinado com **1**, para um valor de **5**.</span><span class="sxs-lookup"><span data-stu-id="d9220-119">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="d9220-120">**8**</span><span class="sxs-lookup"><span data-stu-id="d9220-120">**8**</span></span> | <span data-ttu-id="d9220-121">Envie estado para o servidor de relatórios.</span><span class="sxs-lookup"><span data-stu-id="d9220-121">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="d9220-122">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="d9220-122">Return value</span></span>
------------

<span data-ttu-id="d9220-123">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="d9220-123">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d9220-124">Observações</span><span class="sxs-lookup"><span data-stu-id="d9220-124">Remarks</span></span>

<span data-ttu-id="d9220-125">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="d9220-125">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d9220-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d9220-126">Requirements</span></span>
------------
><span data-ttu-id="d9220-127">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d9220-127">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d9220-128">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d9220-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d9220-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9220-129">See also</span></span>


[<span data-ttu-id="d9220-130">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d9220-130">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



