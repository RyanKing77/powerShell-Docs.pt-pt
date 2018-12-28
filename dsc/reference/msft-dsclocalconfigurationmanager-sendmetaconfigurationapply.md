---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404782"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="6fcb3-103">Método SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="6fcb3-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="6fcb3-104">Define as definições do Gestor de configuração Local que são utilizadas para controlar o agente de configuração.</span><span class="sxs-lookup"><span data-stu-id="6fcb3-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="6fcb3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6fcb3-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="6fcb3-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6fcb3-106">Parameters</span></span>

<span data-ttu-id="6fcb3-107">*ConfigurationData* \[no\] os dados de ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="6fcb3-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="6fcb3-108">*Forçar* \[na\] **verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="6fcb3-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="6fcb3-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6fcb3-109">Return value</span></span>

<span data-ttu-id="6fcb3-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="6fcb3-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6fcb3-111">Observações</span><span class="sxs-lookup"><span data-stu-id="6fcb3-111">Remarks</span></span>

<span data-ttu-id="6fcb3-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="6fcb3-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6fcb3-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6fcb3-113">Requirements</span></span>

<span data-ttu-id="6fcb3-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6fcb3-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="6fcb3-115">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fcb3-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="6fcb3-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fcb3-116">See also</span></span>

[<span data-ttu-id="6fcb3-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="6fcb3-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)