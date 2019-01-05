---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método SendConfigurationApply da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: da3a08307122ab38ee4a6fd5d4a9b97579a988f7
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048364"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="01c50-103">Método SendConfigurationApply da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="01c50-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="01c50-104">Envia o documento de configuração para o nó gerido e utiliza o agente de configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="01c50-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="01c50-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="01c50-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="01c50-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="01c50-106">Parameters</span></span>

<span data-ttu-id="01c50-107">*ConfigurationData* \[no\] os dados de ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="01c50-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="01c50-108">*Forçar* \[na\] **verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="01c50-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="01c50-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="01c50-109">Return value</span></span>

<span data-ttu-id="01c50-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="01c50-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="01c50-111">Observações</span><span class="sxs-lookup"><span data-stu-id="01c50-111">Remarks</span></span>

<span data-ttu-id="01c50-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="01c50-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="01c50-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="01c50-113">Requirements</span></span>

<span data-ttu-id="01c50-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="01c50-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="01c50-115">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="01c50-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="01c50-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01c50-116">See also</span></span>

[<span data-ttu-id="01c50-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="01c50-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)