---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de ResourceSet da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 7291641098578226449f8cbd360da0a3f9842598
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="3b043-103">Método de ResourceSet da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="3b043-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="3b043-104">Chamadas diretamente a **definir** método de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="3b043-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="3b043-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b043-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="3b043-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3b043-106">Parameters</span></span>
----------

<span data-ttu-id="3b043-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="3b043-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="3b043-108">O nome do recurso para chamar.</span><span class="sxs-lookup"><span data-stu-id="3b043-108">The name of the resource to call.</span></span>

<span data-ttu-id="3b043-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="3b043-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="3b043-110">O nome do módulo que contém o recurso a chamada.</span><span class="sxs-lookup"><span data-stu-id="3b043-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="3b043-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="3b043-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="3b043-112">Especifica o nome de propriedade de recursos e o respetivo valor numa tabela hash como chave e valor, respetivamente.</span><span class="sxs-lookup"><span data-stu-id="3b043-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="3b043-113">Utilize o [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet para detetar as propriedades de recurso e os respetivos tipos.</span><span class="sxs-lookup"><span data-stu-id="3b043-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="3b043-114">*RebootRequired* \[out\]</span><span class="sxs-lookup"><span data-stu-id="3b043-114">*RebootRequired* \[out\]</span></span>  
<span data-ttu-id="3b043-115">No retorno, esta propriedade está definida como **verdadeiro** se o nó de destino tem de ser reiniciado.</span><span class="sxs-lookup"><span data-stu-id="3b043-115">On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="3b043-116">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="3b043-116">Return value</span></span>
------------

<span data-ttu-id="3b043-117">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="3b043-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3b043-118">Observações</span><span class="sxs-lookup"><span data-stu-id="3b043-118">Remarks</span></span>

<span data-ttu-id="3b043-119">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="3b043-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3b043-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3b043-120">Requirements</span></span>
------------
><span data-ttu-id="3b043-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3b043-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="3b043-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3b043-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="3b043-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b043-123">See also</span></span>


[<span data-ttu-id="3b043-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3b043-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



