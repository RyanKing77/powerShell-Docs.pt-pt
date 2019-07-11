---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método TestConfiguration
ms.openlocfilehash: 384134212e3b29b63dc045aee4b708c87c970302
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726955"
---
# <a name="testconfiguration-method"></a><span data-ttu-id="43efe-103">Método TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="43efe-103">TestConfiguration method</span></span>

<span data-ttu-id="43efe-104">Envia o documento de configuração para o nó gerido e verifica a configuração atual contra o documento.</span><span class="sxs-lookup"><span data-stu-id="43efe-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="43efe-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43efe-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="43efe-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="43efe-106">Parameters</span></span>

<span data-ttu-id="43efe-107">*configurationData* \[no\] dados de ambiente para o confuguration.</span><span class="sxs-lookup"><span data-stu-id="43efe-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="43efe-108">*InDesiredState* \[horizontalmente\] no retorno, especifica se o nó gerido está num estado especificado pelo documento de configuração.</span><span class="sxs-lookup"><span data-stu-id="43efe-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="43efe-109">*ResourcesInDesiredState* \[horizontalmente\] no retorno, contém uma instância incorporada do **MSFT_ResourceInDesiredState** classe que especifica os recursos que estão no estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="43efe-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="43efe-110">*ResourcesNotInDesiredState* \[horizontalmente\] no retorno, contém uma instância incorporada do **MSFT_ResourceNotInDesiredState** classe que especifica os recursos que não estão no estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="43efe-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="43efe-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="43efe-111">Return value</span></span>

<span data-ttu-id="43efe-112">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="43efe-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="43efe-113">Observações</span><span class="sxs-lookup"><span data-stu-id="43efe-113">Remarks</span></span>

<span data-ttu-id="43efe-114">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="43efe-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="43efe-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="43efe-115">Requirements</span></span>

<span data-ttu-id="43efe-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="43efe-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="43efe-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="43efe-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="43efe-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43efe-118">See also</span></span>

[<span data-ttu-id="43efe-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="43efe-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
