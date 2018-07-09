---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c66ccc4eefaef2d0c3a68fa8a96c5abb9bda6e4c
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893064"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="324f9-103">Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="324f9-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="324f9-104">Obter o histórico do Estado de configuração.</span><span class="sxs-lookup"><span data-stu-id="324f9-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="324f9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="324f9-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="324f9-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="324f9-106">Parameters</span></span>

<span data-ttu-id="324f9-107">*Todos os* \[na\] **verdadeiro** se esse método deve retornar informações sobre todas a configuração é executada na máquina, incluindo o aplicativo de configuração e a verificação de consistência.</span><span class="sxs-lookup"><span data-stu-id="324f9-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="324f9-108">*configurationStatus* \[horizontalmente\] no retorno, contém uma instância incorporada do **MSFT_DSCConfigurationStatus** classe que define as definições.</span><span class="sxs-lookup"><span data-stu-id="324f9-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="324f9-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="324f9-109">Return value</span></span>

<span data-ttu-id="324f9-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="324f9-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="324f9-111">Observações</span><span class="sxs-lookup"><span data-stu-id="324f9-111">Remarks</span></span>

<span data-ttu-id="324f9-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="324f9-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="324f9-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="324f9-113">Requirements</span></span>

<span data-ttu-id="324f9-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="324f9-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="324f9-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="324f9-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="324f9-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="324f9-116">See also</span></span>

[<span data-ttu-id="324f9-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="324f9-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)