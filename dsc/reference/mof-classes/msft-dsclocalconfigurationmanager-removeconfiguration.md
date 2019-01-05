---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048460"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d6c43-103">Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d6c43-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d6c43-104">Remove os ficheiros de configuração.</span><span class="sxs-lookup"><span data-stu-id="d6c43-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="d6c43-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6c43-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="d6c43-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d6c43-106">Parameters</span></span>

<span data-ttu-id="d6c43-107">*Fase* \[no\] Especifica qual documento de configuração para remover.</span><span class="sxs-lookup"><span data-stu-id="d6c43-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="d6c43-108">Os seguintes valores são válidos:</span><span class="sxs-lookup"><span data-stu-id="d6c43-108">The following values are valid:</span></span>

|<span data-ttu-id="d6c43-109">Valor</span><span class="sxs-lookup"><span data-stu-id="d6c43-109">Value</span></span> |<span data-ttu-id="d6c43-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6c43-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="d6c43-111">**1**</span><span class="sxs-lookup"><span data-stu-id="d6c43-111">**1**</span></span> | <span data-ttu-id="d6c43-112">O **atual** documento de configuração (current.mof).</span><span class="sxs-lookup"><span data-stu-id="d6c43-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="d6c43-113">**2**</span><span class="sxs-lookup"><span data-stu-id="d6c43-113">**2**</span></span> | <span data-ttu-id="d6c43-114">O **pendente** documento de configuração (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="d6c43-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="d6c43-115">**4**</span><span class="sxs-lookup"><span data-stu-id="d6c43-115">**4**</span></span> | <span data-ttu-id="d6c43-116">O **Previous** documento de configuração (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="d6c43-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="d6c43-117">*Forçar* \[na\] **verdadeiro** para forçar a remoção da configuração.</span><span class="sxs-lookup"><span data-stu-id="d6c43-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="d6c43-118">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d6c43-118">Return value</span></span>

<span data-ttu-id="d6c43-119">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="d6c43-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d6c43-120">Observações</span><span class="sxs-lookup"><span data-stu-id="d6c43-120">Remarks</span></span>

<span data-ttu-id="d6c43-121">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="d6c43-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d6c43-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6c43-122">Requirements</span></span>

<span data-ttu-id="d6c43-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d6c43-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d6c43-124">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d6c43-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d6c43-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6c43-125">See also</span></span>

[<span data-ttu-id="d6c43-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d6c43-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)