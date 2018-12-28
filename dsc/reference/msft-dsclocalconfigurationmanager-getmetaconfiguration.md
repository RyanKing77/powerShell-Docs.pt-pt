---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e14237ef68b95d68e2f14071aa1fa6ba0717f39f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405274"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="44a8f-103">Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="44a8f-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="44a8f-104">Obtém as definições locais do Configuration Manager que são utilizadas para controlar o agente de configuração.</span><span class="sxs-lookup"><span data-stu-id="44a8f-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="44a8f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44a8f-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="44a8f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="44a8f-106">Parameters</span></span>

<span data-ttu-id="44a8f-107">*MetaConfiguration* \[horizontalmente\] no retorno, contém uma instância incorporada do **MSFT_DSCMetaConfiguration** classe que define as definições.</span><span class="sxs-lookup"><span data-stu-id="44a8f-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="44a8f-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="44a8f-108">Return value</span></span>

<span data-ttu-id="44a8f-109">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="44a8f-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="44a8f-110">Observações</span><span class="sxs-lookup"><span data-stu-id="44a8f-110">Remarks</span></span>

<span data-ttu-id="44a8f-111">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="44a8f-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="44a8f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="44a8f-112">Requirements</span></span>

<span data-ttu-id="44a8f-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="44a8f-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="44a8f-114">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="44a8f-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="44a8f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44a8f-115">See also</span></span>

[<span data-ttu-id="44a8f-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="44a8f-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)