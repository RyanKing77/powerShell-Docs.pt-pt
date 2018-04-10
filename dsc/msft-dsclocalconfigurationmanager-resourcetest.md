---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Método ResourceTest da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: f03a034329a9cde5cd44dbaf42ba1789c2b8f4f9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="cf2d3-103">Método ResourceTest da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="cf2d3-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="cf2d3-104">Chamadas diretamente a **teste** método de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="cf2d3-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="cf2d3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf2d3-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="cf2d3-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cf2d3-106">Parameters</span></span>
----------

<span data-ttu-id="cf2d3-107">*ResourceType* \[no\] o nome do recurso para chamar.</span><span class="sxs-lookup"><span data-stu-id="cf2d3-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="cf2d3-108">*ModuleName* \[no\] o nome do módulo que contém o recurso a chamada.</span><span class="sxs-lookup"><span data-stu-id="cf2d3-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="cf2d3-109">*resourceProperty* \[no\] Especifica o nome de propriedade de recursos e o respetivo valor numa tabela hash como chave e valor, respetivamente.</span><span class="sxs-lookup"><span data-stu-id="cf2d3-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="cf2d3-110">Utilize o [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet para detetar as propriedades de recurso e os respetivos tipos.</span><span class="sxs-lookup"><span data-stu-id="cf2d3-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="cf2d3-111">*InDesiredState* \[saída\] no retorno, esta propriedade está definida como **verdadeiro** se o nó de destino estiver no estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="cf2d3-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="cf2d3-112">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="cf2d3-112">Return value</span></span>
------------

<span data-ttu-id="cf2d3-113">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="cf2d3-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cf2d3-114">Observações</span><span class="sxs-lookup"><span data-stu-id="cf2d3-114">Remarks</span></span>

<span data-ttu-id="cf2d3-115">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="cf2d3-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cf2d3-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cf2d3-116">Requirements</span></span>
------------
><span data-ttu-id="cf2d3-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cf2d3-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="cf2d3-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cf2d3-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="cf2d3-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf2d3-119">See also</span></span>


[<span data-ttu-id="cf2d3-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="cf2d3-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)