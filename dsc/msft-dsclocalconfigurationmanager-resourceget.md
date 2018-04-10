---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Método ResourceGet da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3fd7ae54eb3ae782156dc4619ee0b6905dfb1212
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b79f8-103">Método ResourceGet da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b79f8-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b79f8-104">Chamadas diretamente a **obter** método de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="b79f8-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="b79f8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b79f8-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="b79f8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b79f8-106">Parameters</span></span>
----------

<span data-ttu-id="b79f8-107">*ResourceType* \[no\] o nome do recurso para chamar.</span><span class="sxs-lookup"><span data-stu-id="b79f8-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="b79f8-108">*ModuleName* \[no\] o nome do módulo que contém o recurso a chamada.</span><span class="sxs-lookup"><span data-stu-id="b79f8-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="b79f8-109">*resourceProperty* \[no\] Especifica o nome de propriedade de recursos e o respetivo valor numa tabela hash como chave e valor, respetivamente.</span><span class="sxs-lookup"><span data-stu-id="b79f8-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="b79f8-110">Utilize o [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet para detetar as propriedades de recurso e os respetivos tipos.</span><span class="sxs-lookup"><span data-stu-id="b79f8-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="b79f8-111">*configurações* \[saída\] no retorno, contém uma instância incorporada das configurações.</span><span class="sxs-lookup"><span data-stu-id="b79f8-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="b79f8-112">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="b79f8-112">Return value</span></span>
------------

<span data-ttu-id="b79f8-113">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="b79f8-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b79f8-114">Observações</span><span class="sxs-lookup"><span data-stu-id="b79f8-114">Remarks</span></span>

<span data-ttu-id="b79f8-115">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="b79f8-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b79f8-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b79f8-116">Requirements</span></span>
------------
><span data-ttu-id="b79f8-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b79f8-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b79f8-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b79f8-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b79f8-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b79f8-119">See also</span></span>


[<span data-ttu-id="b79f8-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b79f8-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)