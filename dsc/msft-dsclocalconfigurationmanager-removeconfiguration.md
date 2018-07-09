---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892689"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="54eca-103">Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="54eca-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="54eca-104">Remove os ficheiros de configuração.</span><span class="sxs-lookup"><span data-stu-id="54eca-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="54eca-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="54eca-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="54eca-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="54eca-106">Parameters</span></span>

<span data-ttu-id="54eca-107">*Fase* \[no\] Especifica qual documento de configuração para remover.</span><span class="sxs-lookup"><span data-stu-id="54eca-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="54eca-108">Os seguintes valores são válidos:</span><span class="sxs-lookup"><span data-stu-id="54eca-108">The following values are valid:</span></span>

|<span data-ttu-id="54eca-109">Valor</span><span class="sxs-lookup"><span data-stu-id="54eca-109">Value</span></span> |<span data-ttu-id="54eca-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="54eca-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="54eca-111">**1**</span><span class="sxs-lookup"><span data-stu-id="54eca-111">**1**</span></span> | <span data-ttu-id="54eca-112">O **atual** documento de configuração (current.mof).</span><span class="sxs-lookup"><span data-stu-id="54eca-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="54eca-113">**2**</span><span class="sxs-lookup"><span data-stu-id="54eca-113">**2**</span></span> | <span data-ttu-id="54eca-114">O **pendente** documento de configuração (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="54eca-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="54eca-115">**4**</span><span class="sxs-lookup"><span data-stu-id="54eca-115">**4**</span></span> | <span data-ttu-id="54eca-116">O **Previous** documento de configuração (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="54eca-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="54eca-117">*Forçar* \[na\] **verdadeiro** para forçar a remoção da configuração.</span><span class="sxs-lookup"><span data-stu-id="54eca-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="54eca-118">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="54eca-118">Return value</span></span>

<span data-ttu-id="54eca-119">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="54eca-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="54eca-120">Observações</span><span class="sxs-lookup"><span data-stu-id="54eca-120">Remarks</span></span>

<span data-ttu-id="54eca-121">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="54eca-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="54eca-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="54eca-122">Requirements</span></span>

<span data-ttu-id="54eca-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="54eca-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="54eca-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="54eca-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="54eca-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54eca-125">See also</span></span>

[<span data-ttu-id="54eca-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="54eca-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)