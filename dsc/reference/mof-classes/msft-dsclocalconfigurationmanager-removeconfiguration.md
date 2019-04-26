---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078695"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0174e-103">Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0174e-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0174e-104">Remove os ficheiros de configuração.</span><span class="sxs-lookup"><span data-stu-id="0174e-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="0174e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0174e-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="0174e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0174e-106">Parameters</span></span>

<span data-ttu-id="0174e-107">*Fase* \[no\] Especifica qual documento de configuração para remover.</span><span class="sxs-lookup"><span data-stu-id="0174e-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="0174e-108">Os seguintes valores são válidos:</span><span class="sxs-lookup"><span data-stu-id="0174e-108">The following values are valid:</span></span>

|<span data-ttu-id="0174e-109">Valor</span><span class="sxs-lookup"><span data-stu-id="0174e-109">Value</span></span> |<span data-ttu-id="0174e-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="0174e-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="0174e-111">**1**</span><span class="sxs-lookup"><span data-stu-id="0174e-111">**1**</span></span> | <span data-ttu-id="0174e-112">O **atual** documento de configuração (current.mof).</span><span class="sxs-lookup"><span data-stu-id="0174e-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="0174e-113">**2**</span><span class="sxs-lookup"><span data-stu-id="0174e-113">**2**</span></span> | <span data-ttu-id="0174e-114">O **pendente** documento de configuração (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="0174e-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="0174e-115">**4**</span><span class="sxs-lookup"><span data-stu-id="0174e-115">**4**</span></span> | <span data-ttu-id="0174e-116">O **Previous** documento de configuração (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="0174e-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="0174e-117">*Forçar* \[na\] **verdadeiro** para forçar a remoção da configuração.</span><span class="sxs-lookup"><span data-stu-id="0174e-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="0174e-118">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0174e-118">Return value</span></span>

<span data-ttu-id="0174e-119">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="0174e-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0174e-120">Observações</span><span class="sxs-lookup"><span data-stu-id="0174e-120">Remarks</span></span>

<span data-ttu-id="0174e-121">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="0174e-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0174e-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0174e-122">Requirements</span></span>

<span data-ttu-id="0174e-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0174e-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0174e-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0174e-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0174e-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0174e-125">See also</span></span>

[<span data-ttu-id="0174e-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0174e-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)