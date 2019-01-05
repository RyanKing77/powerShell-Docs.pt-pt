---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048367"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c574b-103">Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c574b-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c574b-104">Utiliza o agente de configuração para aplicar a configuração que está pendente.</span><span class="sxs-lookup"><span data-stu-id="c574b-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="c574b-105">Se não houver nenhuma configuração pendentes, este método de volta a aplicar a configuração atual.</span><span class="sxs-lookup"><span data-stu-id="c574b-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="c574b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c574b-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="c574b-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c574b-107">Parameters</span></span>

<span data-ttu-id="c574b-108">*Forçar* \[na\] se se tratar de **verdadeiro**, a configuração atual é reaplicada, mesmo que haja uma configuração pendentes.</span><span class="sxs-lookup"><span data-stu-id="c574b-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="c574b-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c574b-109">Return value</span></span>

<span data-ttu-id="c574b-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="c574b-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c574b-111">Observações</span><span class="sxs-lookup"><span data-stu-id="c574b-111">Remarks</span></span>

<span data-ttu-id="c574b-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="c574b-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c574b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c574b-113">Requirements</span></span>

<span data-ttu-id="c574b-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c574b-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c574b-115">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c574b-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c574b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c574b-116">See also</span></span>

[<span data-ttu-id="c574b-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c574b-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)