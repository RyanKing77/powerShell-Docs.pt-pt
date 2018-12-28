---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método StopConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405256"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="094fb-103">Método StopConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="094fb-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="094fb-104">Interrompe a alteração da configuração que está em curso.</span><span class="sxs-lookup"><span data-stu-id="094fb-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="094fb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="094fb-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="094fb-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="094fb-106">Parameters</span></span>

<span data-ttu-id="094fb-107">*Forçar* \[na\] **verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="094fb-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="094fb-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="094fb-108">Return value</span></span>

<span data-ttu-id="094fb-109">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="094fb-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="094fb-110">Observações</span><span class="sxs-lookup"><span data-stu-id="094fb-110">Remarks</span></span>

<span data-ttu-id="094fb-111">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="094fb-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="094fb-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="094fb-112">Requirements</span></span>

<span data-ttu-id="094fb-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="094fb-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="094fb-114">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="094fb-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="094fb-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="094fb-115">See also</span></span>

[<span data-ttu-id="094fb-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="094fb-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)