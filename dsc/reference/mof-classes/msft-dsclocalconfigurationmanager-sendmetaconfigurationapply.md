---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método SendMetaConfigurationApply
ms.openlocfilehash: b2e420bafb8ea22aea43800f6e429d3ed785d1e8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727040"
---
# <a name="sendmetaconfigurationapply-method"></a><span data-ttu-id="26851-103">Método SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="26851-103">SendMetaConfigurationApply method</span></span>

<span data-ttu-id="26851-104">Define as definições do Gestor de configuração Local que são utilizadas para controlar o agente de configuração.</span><span class="sxs-lookup"><span data-stu-id="26851-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="26851-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26851-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="26851-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="26851-106">Parameters</span></span>

<span data-ttu-id="26851-107">*ConfigurationData* \[no\] os dados de ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="26851-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="26851-108">*Forçar* \[na\] **verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="26851-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="26851-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="26851-109">Return value</span></span>

<span data-ttu-id="26851-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="26851-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="26851-111">Observações</span><span class="sxs-lookup"><span data-stu-id="26851-111">Remarks</span></span>

<span data-ttu-id="26851-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="26851-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="26851-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26851-113">Requirements</span></span>

<span data-ttu-id="26851-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="26851-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="26851-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="26851-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="26851-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26851-116">See also</span></span>

[<span data-ttu-id="26851-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="26851-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
