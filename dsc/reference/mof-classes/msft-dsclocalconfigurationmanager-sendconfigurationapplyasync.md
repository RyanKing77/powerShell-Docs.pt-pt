---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método SendConfigurationApplyAsync
ms.openlocfilehash: c0e6dc9418757ee719e848fa8e7006dd73d91ad8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734298"
---
# <a name="sendconfigurationapplyasync-method"></a><span data-ttu-id="d5f3e-103">Método SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="d5f3e-103">SendConfigurationApplyAsync method</span></span>

<span data-ttu-id="d5f3e-104">Envia o documento de configuração de forma assíncrona para o nó gerido e utiliza o agente de configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="d5f3e-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="d5f3e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5f3e-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="d5f3e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d5f3e-106">Parameters</span></span>

<span data-ttu-id="d5f3e-107">*ConfigurationData* \[no\] os dados de ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="d5f3e-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="d5f3e-108">*Forçar* \[na\] **verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="d5f3e-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="d5f3e-109">*jobId* \[no\] o ID da tarefa para a qual enviar a configuração.</span><span class="sxs-lookup"><span data-stu-id="d5f3e-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="d5f3e-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d5f3e-110">Return value</span></span>

<span data-ttu-id="d5f3e-111">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="d5f3e-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d5f3e-112">Observações</span><span class="sxs-lookup"><span data-stu-id="d5f3e-112">Remarks</span></span>

<span data-ttu-id="d5f3e-113">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="d5f3e-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d5f3e-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d5f3e-114">Requirements</span></span>

<span data-ttu-id="d5f3e-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d5f3e-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d5f3e-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d5f3e-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d5f3e-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5f3e-117">See also</span></span>

[<span data-ttu-id="d5f3e-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d5f3e-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
