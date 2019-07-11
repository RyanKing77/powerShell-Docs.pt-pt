---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método SendConfigurationApply
ms.openlocfilehash: 11b9d435bbaac1600d25ff074b6c55b236a8378b
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727011"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="1de4d-103">Método SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="1de4d-103">SendConfigurationApply method</span></span>

<span data-ttu-id="1de4d-104">Envia o documento de configuração para o nó gerido e utiliza o agente de configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="1de4d-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="1de4d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1de4d-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="1de4d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1de4d-106">Parameters</span></span>

<span data-ttu-id="1de4d-107">*ConfigurationData* \[no\] os dados de ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="1de4d-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="1de4d-108">*Forçar* \[na\] **verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="1de4d-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="1de4d-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1de4d-109">Return value</span></span>

<span data-ttu-id="1de4d-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="1de4d-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1de4d-111">Observações</span><span class="sxs-lookup"><span data-stu-id="1de4d-111">Remarks</span></span>

<span data-ttu-id="1de4d-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="1de4d-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1de4d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1de4d-113">Requirements</span></span>

<span data-ttu-id="1de4d-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1de4d-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="1de4d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1de4d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="1de4d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1de4d-116">See also</span></span>

[<span data-ttu-id="1de4d-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1de4d-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
