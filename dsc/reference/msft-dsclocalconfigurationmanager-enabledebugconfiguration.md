---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404656"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0cb8a-103">Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0cb8a-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0cb8a-104">Permite a depuração de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="0cb8a-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="0cb8a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0cb8a-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="0cb8a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0cb8a-106">Parameters</span></span>

<span data-ttu-id="0cb8a-107">*BreakAll* \[no\] define um ponto de interrupção em cada linha do script de recursos.</span><span class="sxs-lookup"><span data-stu-id="0cb8a-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="0cb8a-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0cb8a-108">Return value</span></span>

<span data-ttu-id="0cb8a-109">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="0cb8a-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0cb8a-110">Observações</span><span class="sxs-lookup"><span data-stu-id="0cb8a-110">Remarks</span></span>

<span data-ttu-id="0cb8a-111">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="0cb8a-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0cb8a-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0cb8a-112">Requirements</span></span>

<span data-ttu-id="0cb8a-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0cb8a-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0cb8a-114">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0cb8a-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0cb8a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0cb8a-115">See also</span></span>

[<span data-ttu-id="0cb8a-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0cb8a-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)