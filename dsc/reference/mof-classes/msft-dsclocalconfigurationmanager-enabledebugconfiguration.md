---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048403"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4fab0-103">Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4fab0-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4fab0-104">Permite a depuração de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="4fab0-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="4fab0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4fab0-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="4fab0-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4fab0-106">Parameters</span></span>

<span data-ttu-id="4fab0-107">*BreakAll* \[no\] define um ponto de interrupção em cada linha do script de recursos.</span><span class="sxs-lookup"><span data-stu-id="4fab0-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="4fab0-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4fab0-108">Return value</span></span>

<span data-ttu-id="4fab0-109">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="4fab0-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4fab0-110">Observações</span><span class="sxs-lookup"><span data-stu-id="4fab0-110">Remarks</span></span>

<span data-ttu-id="4fab0-111">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="4fab0-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4fab0-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4fab0-112">Requirements</span></span>

<span data-ttu-id="4fab0-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4fab0-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="4fab0-114">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4fab0-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="4fab0-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4fab0-115">See also</span></span>

[<span data-ttu-id="4fab0-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4fab0-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)