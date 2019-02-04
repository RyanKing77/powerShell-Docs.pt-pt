---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método TestConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d746832b01310f43a7aae33dd0fa70c0928bb3e0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685670"
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="71210-103">Método TestConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="71210-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="71210-104">Envia o documento de configuração para o nó gerido e verifica a configuração atual contra o documento.</span><span class="sxs-lookup"><span data-stu-id="71210-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="71210-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="71210-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="71210-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="71210-106">Parameters</span></span>

<span data-ttu-id="71210-107">*configurationData* \[no\] dados de ambiente para o confuguration.</span><span class="sxs-lookup"><span data-stu-id="71210-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="71210-108">*InDesiredState* \[horizontalmente\] no retorno, especifica se o nó gerido está num estado especificado pelo documento de configuração.</span><span class="sxs-lookup"><span data-stu-id="71210-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="71210-109">*ResourcesInDesiredState* \[horizontalmente\] no retorno, contém uma instância incorporada do **MSFT_ResourceInDesiredState** classe que especifica os recursos que estão no estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="71210-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="71210-110">*ResourcesNotInDesiredState* \[horizontalmente\] no retorno, contém uma instância incorporada do **MSFT_ResourceNotInDesiredState** classe que especifica os recursos que não estão no estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="71210-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="71210-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="71210-111">Return value</span></span>

<span data-ttu-id="71210-112">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="71210-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="71210-113">Observações</span><span class="sxs-lookup"><span data-stu-id="71210-113">Remarks</span></span>

<span data-ttu-id="71210-114">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="71210-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="71210-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="71210-115">Requirements</span></span>

<span data-ttu-id="71210-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="71210-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="71210-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="71210-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="71210-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71210-118">See also</span></span>

[<span data-ttu-id="71210-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="71210-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)