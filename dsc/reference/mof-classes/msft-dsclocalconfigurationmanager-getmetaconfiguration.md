---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método Getconfigurationstatus
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734442"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="d6c5a-103">Método Getconfigurationstatus</span><span class="sxs-lookup"><span data-stu-id="d6c5a-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="d6c5a-104">Obtém as definições locais do Configuration Manager que são utilizadas para controlar o agente de configuração.</span><span class="sxs-lookup"><span data-stu-id="d6c5a-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="d6c5a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6c5a-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="d6c5a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d6c5a-106">Parameters</span></span>

<span data-ttu-id="d6c5a-107">*MetaConfiguration* \[horizontalmente\] no retorno, contém uma instância incorporada do **MSFT_DSCMetaConfiguration** classe que define as definições.</span><span class="sxs-lookup"><span data-stu-id="d6c5a-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="d6c5a-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d6c5a-108">Return value</span></span>

<span data-ttu-id="d6c5a-109">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="d6c5a-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d6c5a-110">Observações</span><span class="sxs-lookup"><span data-stu-id="d6c5a-110">Remarks</span></span>

<span data-ttu-id="d6c5a-111">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="d6c5a-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d6c5a-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6c5a-112">Requirements</span></span>

<span data-ttu-id="d6c5a-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d6c5a-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d6c5a-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d6c5a-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d6c5a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6c5a-115">See also</span></span>

[<span data-ttu-id="d6c5a-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d6c5a-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
