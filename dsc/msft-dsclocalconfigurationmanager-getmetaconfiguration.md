---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ddc016402239bcdea060a717fbac9ab7ea42698c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7f6a4-103">Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="7f6a4-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7f6a4-104">Obtém as definições de Configuration Manager local que são utilizadas para controlar o agente de configuração.</span><span class="sxs-lookup"><span data-stu-id="7f6a4-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="7f6a4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f6a4-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="7f6a4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7f6a4-106">Parameters</span></span>
----------

<span data-ttu-id="7f6a4-107">*Configuração meta do* \[saída\] no retorno, contém uma instância do embedded o **MSFT_DSCMetaConfiguration** classe que define as definições.</span><span class="sxs-lookup"><span data-stu-id="7f6a4-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="7f6a4-108">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="7f6a4-108">Return value</span></span>
------------

<span data-ttu-id="7f6a4-109">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="7f6a4-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7f6a4-110">Observações</span><span class="sxs-lookup"><span data-stu-id="7f6a4-110">Remarks</span></span>

<span data-ttu-id="7f6a4-111">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="7f6a4-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7f6a4-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7f6a4-112">Requirements</span></span>
------------
><span data-ttu-id="7f6a4-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7f6a4-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7f6a4-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7f6a4-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7f6a4-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f6a4-115">See also</span></span>


[<span data-ttu-id="7f6a4-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7f6a4-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)