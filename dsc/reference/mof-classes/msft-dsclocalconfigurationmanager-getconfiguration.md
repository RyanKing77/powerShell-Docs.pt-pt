---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método GetConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ae31ac30c152c96707b764ddaf00c924806afcfc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687210"
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="3d79e-103">Método GetConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="3d79e-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="3d79e-104">Envia o documento de configuração para o nó gerido e utiliza a **obter** método do agente de configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="3d79e-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="3d79e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3d79e-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="3d79e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3d79e-106">Parameters</span></span>

<span data-ttu-id="3d79e-107">*configurationData* \[no\] Especifica os dados de configuração para enviar.</span><span class="sxs-lookup"><span data-stu-id="3d79e-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="3d79e-108">*configurações* \[horizontalmente\] no retorno, contém uma instância incorporada das configurações.</span><span class="sxs-lookup"><span data-stu-id="3d79e-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="3d79e-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3d79e-109">Return value</span></span>

<span data-ttu-id="3d79e-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="3d79e-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3d79e-111">Observações</span><span class="sxs-lookup"><span data-stu-id="3d79e-111">Remarks</span></span>

<span data-ttu-id="3d79e-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="3d79e-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3d79e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3d79e-113">Requirements</span></span>

<span data-ttu-id="3d79e-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3d79e-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3d79e-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3d79e-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3d79e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d79e-116">See also</span></span>

[<span data-ttu-id="3d79e-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3d79e-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)