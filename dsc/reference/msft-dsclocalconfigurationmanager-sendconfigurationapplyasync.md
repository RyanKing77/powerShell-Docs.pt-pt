---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método SendConfigurationApplyAsync da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404659"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="07d77-103">Método SendConfigurationApplyAsync da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="07d77-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="07d77-104">Envia o documento de configuração de forma assíncrona para o nó gerido e utiliza o agente de configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="07d77-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="07d77-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="07d77-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="07d77-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="07d77-106">Parameters</span></span>

<span data-ttu-id="07d77-107">*ConfigurationData* \[no\] os dados de ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="07d77-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="07d77-108">*Forçar* \[na\] **verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="07d77-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="07d77-109">*jobId* \[no\] o ID da tarefa para a qual enviar a configuração.</span><span class="sxs-lookup"><span data-stu-id="07d77-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="07d77-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="07d77-110">Return value</span></span>

<span data-ttu-id="07d77-111">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="07d77-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="07d77-112">Observações</span><span class="sxs-lookup"><span data-stu-id="07d77-112">Remarks</span></span>

<span data-ttu-id="07d77-113">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="07d77-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="07d77-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="07d77-114">Requirements</span></span>

<span data-ttu-id="07d77-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="07d77-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="07d77-116">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="07d77-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="07d77-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07d77-117">See also</span></span>

[<span data-ttu-id="07d77-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="07d77-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)