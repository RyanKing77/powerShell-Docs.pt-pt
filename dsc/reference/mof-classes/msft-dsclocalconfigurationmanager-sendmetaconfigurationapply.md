---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688071"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="78db1-103">Método SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="78db1-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="78db1-104">Define as definições do Gestor de configuração Local que são utilizadas para controlar o agente de configuração.</span><span class="sxs-lookup"><span data-stu-id="78db1-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="78db1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78db1-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="78db1-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="78db1-106">Parameters</span></span>

<span data-ttu-id="78db1-107">*ConfigurationData* \[no\] os dados de ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="78db1-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="78db1-108">*Forçar* \[na\] **verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="78db1-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="78db1-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="78db1-109">Return value</span></span>

<span data-ttu-id="78db1-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="78db1-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="78db1-111">Observações</span><span class="sxs-lookup"><span data-stu-id="78db1-111">Remarks</span></span>

<span data-ttu-id="78db1-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="78db1-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="78db1-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="78db1-113">Requirements</span></span>

<span data-ttu-id="78db1-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="78db1-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="78db1-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="78db1-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="78db1-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78db1-116">See also</span></span>

[<span data-ttu-id="78db1-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="78db1-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)