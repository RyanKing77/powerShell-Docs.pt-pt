---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método TestConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d746832b01310f43a7aae33dd0fa70c0928bb3e0
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048396"
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="90b85-103">Método TestConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="90b85-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="90b85-104">Envia o documento de configuração para o nó gerido e verifica a configuração atual contra o documento.</span><span class="sxs-lookup"><span data-stu-id="90b85-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="90b85-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90b85-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="90b85-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="90b85-106">Parameters</span></span>

<span data-ttu-id="90b85-107">*configurationData* \[no\] dados de ambiente para o confuguration.</span><span class="sxs-lookup"><span data-stu-id="90b85-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="90b85-108">*InDesiredState* \[horizontalmente\] no retorno, especifica se o nó gerido está num estado especificado pelo documento de configuração.</span><span class="sxs-lookup"><span data-stu-id="90b85-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="90b85-109">*ResourcesInDesiredState* \[horizontalmente\] no retorno, contém uma instância incorporada do **MSFT_ResourceInDesiredState** classe que especifica os recursos que estão no estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="90b85-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="90b85-110">*ResourcesNotInDesiredState* \[horizontalmente\] no retorno, contém uma instância incorporada do **MSFT_ResourceNotInDesiredState** classe que especifica os recursos que não estão no estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="90b85-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="90b85-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="90b85-111">Return value</span></span>

<span data-ttu-id="90b85-112">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="90b85-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="90b85-113">Observações</span><span class="sxs-lookup"><span data-stu-id="90b85-113">Remarks</span></span>

<span data-ttu-id="90b85-114">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="90b85-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="90b85-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="90b85-115">Requirements</span></span>

<span data-ttu-id="90b85-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="90b85-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="90b85-117">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="90b85-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="90b85-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90b85-118">See also</span></span>

[<span data-ttu-id="90b85-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="90b85-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)