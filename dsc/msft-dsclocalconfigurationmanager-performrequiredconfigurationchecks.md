---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Método PerformRequiredConfigurationChecks da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c3fdaa23875815b1cf5cbf0b6e21c633e00664aa
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186699"
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b5424-103">Método PerformRequiredConfigurationChecks da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b5424-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b5424-104">Inicia uma verificação de consistência utilizando o Programador de tarefas.</span><span class="sxs-lookup"><span data-stu-id="b5424-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="b5424-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5424-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="b5424-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b5424-106">Parameters</span></span>
----------

<span data-ttu-id="b5424-107">*Sinalizadores* \[no\] uma máscara de bits que especifica o tipo de verificação de consistência para ser executada.</span><span class="sxs-lookup"><span data-stu-id="b5424-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="b5424-108">Os seguintes valores são válidos e podem ser combinados utilizando um bit a bit **ou** operação:</span><span class="sxs-lookup"><span data-stu-id="b5424-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="b5424-109">Valor</span><span class="sxs-lookup"><span data-stu-id="b5424-109">Value</span></span> |<span data-ttu-id="b5424-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5424-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="b5424-111">**1**</span><span class="sxs-lookup"><span data-stu-id="b5424-111">**1**</span></span> | <span data-ttu-id="b5424-112">Uma verificação de consistência normal.</span><span class="sxs-lookup"><span data-stu-id="b5424-112">A normal consistency check.</span></span> |
|<span data-ttu-id="b5424-113">**2**</span><span class="sxs-lookup"><span data-stu-id="b5424-113">**2**</span></span> | <span data-ttu-id="b5424-114">Uma continuação de uma verificação de consistência após um reinício.</span><span class="sxs-lookup"><span data-stu-id="b5424-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="b5424-115">Este valor não deve ser combinado com outros valores.</span><span class="sxs-lookup"><span data-stu-id="b5424-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="b5424-116">**4**</span><span class="sxs-lookup"><span data-stu-id="b5424-116">**4**</span></span> | <span data-ttu-id="b5424-117">A configuração deve ser solicitada a partir do servidor de solicitação especificado na configuração meta da para o nó.</span><span class="sxs-lookup"><span data-stu-id="b5424-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="b5424-118">Este valor deve sempre ser combinado com **1**, para um valor de **5**.</span><span class="sxs-lookup"><span data-stu-id="b5424-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="b5424-119">**8**</span><span class="sxs-lookup"><span data-stu-id="b5424-119">**8**</span></span> | <span data-ttu-id="b5424-120">Envie estado para o servidor de relatórios.</span><span class="sxs-lookup"><span data-stu-id="b5424-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="b5424-121">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="b5424-121">Return value</span></span>
------------

<span data-ttu-id="b5424-122">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="b5424-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5424-123">Observações</span><span class="sxs-lookup"><span data-stu-id="b5424-123">Remarks</span></span>

<span data-ttu-id="b5424-124">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="b5424-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b5424-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b5424-125">Requirements</span></span>
------------
><span data-ttu-id="b5424-126">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b5424-126">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b5424-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b5424-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b5424-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5424-128">See also</span></span>


[<span data-ttu-id="b5424-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b5424-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)