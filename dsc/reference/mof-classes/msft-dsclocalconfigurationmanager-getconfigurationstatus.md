---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método GetConfigurationStatus
ms.openlocfilehash: 83b30ba2612d962fcf2fa658d07d18fb2d91ccc7
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734504"
---
# <a name="getconfigurationstatus-method"></a><span data-ttu-id="d7c6b-103">Método GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="d7c6b-103">GetConfigurationStatus method</span></span>

<span data-ttu-id="d7c6b-104">Obter o histórico do Estado de configuração.</span><span class="sxs-lookup"><span data-stu-id="d7c6b-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="d7c6b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7c6b-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="d7c6b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d7c6b-106">Parameters</span></span>

<span data-ttu-id="d7c6b-107">*Todos os* \[na\] **verdadeiro** se esse método deve retornar informações sobre todas a configuração é executada na máquina, incluindo o aplicativo de configuração e a verificação de consistência.</span><span class="sxs-lookup"><span data-stu-id="d7c6b-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="d7c6b-108">*configurationStatus* \[horizontalmente\] no retorno, contém uma instância incorporada do **MSFT_DSCConfigurationStatus** classe que define as definições.</span><span class="sxs-lookup"><span data-stu-id="d7c6b-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="d7c6b-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d7c6b-109">Return value</span></span>

<span data-ttu-id="d7c6b-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="d7c6b-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7c6b-111">Observações</span><span class="sxs-lookup"><span data-stu-id="d7c6b-111">Remarks</span></span>

<span data-ttu-id="d7c6b-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="d7c6b-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d7c6b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d7c6b-113">Requirements</span></span>

<span data-ttu-id="d7c6b-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d7c6b-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d7c6b-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d7c6b-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d7c6b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7c6b-116">See also</span></span>

[<span data-ttu-id="d7c6b-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d7c6b-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
