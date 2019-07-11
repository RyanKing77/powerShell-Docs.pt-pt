---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método SendConfiguration
ms.openlocfilehash: 4feba090bc58844659c2329a304dd9805255564f
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734321"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="1e8b4-103">Método SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="1e8b4-103">SendConfiguration method</span></span>

<span data-ttu-id="1e8b4-104">Envia o documento de configuração para o nó gerido e o salva como uma alteração pendente.</span><span class="sxs-lookup"><span data-stu-id="1e8b4-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="1e8b4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1e8b4-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="1e8b4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1e8b4-106">Parameters</span></span>

<span data-ttu-id="1e8b4-107">*ConfigurationData* \[no\] os dados de ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="1e8b4-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="1e8b4-108">*Forçar* \[na\] **verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="1e8b4-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="1e8b4-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1e8b4-109">Return value</span></span>

<span data-ttu-id="1e8b4-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="1e8b4-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1e8b4-111">Observações</span><span class="sxs-lookup"><span data-stu-id="1e8b4-111">Remarks</span></span>

<span data-ttu-id="1e8b4-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="1e8b4-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1e8b4-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1e8b4-113">Requirements</span></span>

<span data-ttu-id="1e8b4-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1e8b4-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="1e8b4-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1e8b4-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="1e8b4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e8b4-116">See also</span></span>

[<span data-ttu-id="1e8b4-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1e8b4-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
