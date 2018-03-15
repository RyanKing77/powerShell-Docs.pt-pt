---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de ResourceGet da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 2c055b3fab468f85c9e2f91cf1eaf1a4353b4660
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b37ad-103">Método de ResourceGet da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b37ad-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b37ad-104">Chamadas diretamente a **obter** método de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="b37ad-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="b37ad-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b37ad-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="b37ad-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b37ad-106">Parameters</span></span>
----------

<span data-ttu-id="b37ad-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b37ad-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="b37ad-108">O nome do recurso para chamar.</span><span class="sxs-lookup"><span data-stu-id="b37ad-108">The name of the resource to call.</span></span>

<span data-ttu-id="b37ad-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b37ad-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="b37ad-110">O nome do módulo que contém o recurso a chamada.</span><span class="sxs-lookup"><span data-stu-id="b37ad-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="b37ad-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b37ad-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="b37ad-112">Especifica o nome de propriedade de recursos e o respetivo valor numa tabela hash como chave e valor, respetivamente.</span><span class="sxs-lookup"><span data-stu-id="b37ad-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="b37ad-113">Utilize o [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet para detetar as propriedades de recurso e os respetivos tipos.</span><span class="sxs-lookup"><span data-stu-id="b37ad-113">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="b37ad-114">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="b37ad-114">*configurations* \[out\]</span></span>  
<span data-ttu-id="b37ad-115">No retorno, contém uma instância incorporada das configurações.</span><span class="sxs-lookup"><span data-stu-id="b37ad-115">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="b37ad-116">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="b37ad-116">Return value</span></span>
------------

<span data-ttu-id="b37ad-117">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="b37ad-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b37ad-118">Observações</span><span class="sxs-lookup"><span data-stu-id="b37ad-118">Remarks</span></span>

<span data-ttu-id="b37ad-119">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="b37ad-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b37ad-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b37ad-120">Requirements</span></span>
------------
><span data-ttu-id="b37ad-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b37ad-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b37ad-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b37ad-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b37ad-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b37ad-123">See also</span></span>


[<span data-ttu-id="b37ad-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b37ad-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



