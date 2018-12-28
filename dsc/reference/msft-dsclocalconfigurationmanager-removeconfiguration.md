---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404899"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5304b-103">Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5304b-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5304b-104">Remove os ficheiros de configuração.</span><span class="sxs-lookup"><span data-stu-id="5304b-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="5304b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5304b-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="5304b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5304b-106">Parameters</span></span>

<span data-ttu-id="5304b-107">*Fase* \[no\] Especifica qual documento de configuração para remover.</span><span class="sxs-lookup"><span data-stu-id="5304b-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="5304b-108">Os seguintes valores são válidos:</span><span class="sxs-lookup"><span data-stu-id="5304b-108">The following values are valid:</span></span>

|<span data-ttu-id="5304b-109">Valor</span><span class="sxs-lookup"><span data-stu-id="5304b-109">Value</span></span> |<span data-ttu-id="5304b-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="5304b-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="5304b-111">**1**</span><span class="sxs-lookup"><span data-stu-id="5304b-111">**1**</span></span> | <span data-ttu-id="5304b-112">O **atual** documento de configuração (current.mof).</span><span class="sxs-lookup"><span data-stu-id="5304b-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="5304b-113">**2**</span><span class="sxs-lookup"><span data-stu-id="5304b-113">**2**</span></span> | <span data-ttu-id="5304b-114">O **pendente** documento de configuração (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="5304b-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="5304b-115">**4**</span><span class="sxs-lookup"><span data-stu-id="5304b-115">**4**</span></span> | <span data-ttu-id="5304b-116">O **Previous** documento de configuração (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="5304b-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="5304b-117">*Forçar* \[na\] **verdadeiro** para forçar a remoção da configuração.</span><span class="sxs-lookup"><span data-stu-id="5304b-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="5304b-118">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5304b-118">Return value</span></span>

<span data-ttu-id="5304b-119">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="5304b-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5304b-120">Observações</span><span class="sxs-lookup"><span data-stu-id="5304b-120">Remarks</span></span>

<span data-ttu-id="5304b-121">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="5304b-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5304b-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5304b-122">Requirements</span></span>

<span data-ttu-id="5304b-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5304b-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="5304b-124">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5304b-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="5304b-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5304b-125">See also</span></span>

[<span data-ttu-id="5304b-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5304b-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)