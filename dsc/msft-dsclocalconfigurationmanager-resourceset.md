---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de ResourceSet da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 9cd9c1b3f58a5862db6c4eea0488423b8dfe7310
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="af625-103">Método de ResourceSet da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="af625-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="af625-104">Chamadas diretamente a **definir** método de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="af625-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="af625-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af625-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="af625-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="af625-106">Parameters</span></span>
----------

<span data-ttu-id="af625-107">*ResourceType* \[no\]</span><span class="sxs-lookup"><span data-stu-id="af625-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="af625-108">O nome do recurso para chamar.</span><span class="sxs-lookup"><span data-stu-id="af625-108">The name of the resource to call.</span></span>

<span data-ttu-id="af625-109">*ModuleName* \[no\]</span><span class="sxs-lookup"><span data-stu-id="af625-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="af625-110">O nome do módulo que contém o recurso a chamada.</span><span class="sxs-lookup"><span data-stu-id="af625-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="af625-111">*resourceProperty* \[no\]</span><span class="sxs-lookup"><span data-stu-id="af625-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="af625-112">Especifica o nome de propriedade de recursos e o respetivo valor numa tabela hash como chave e valor, respetivamente.</span><span class="sxs-lookup"><span data-stu-id="af625-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="af625-113">Utilize o [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet para detetar as propriedades de recurso e os respetivos tipos.</span><span class="sxs-lookup"><span data-stu-id="af625-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="af625-114">*RebootRequired* \[enviados\]</span><span class="sxs-lookup"><span data-stu-id="af625-114">*RebootRequired* \[out\]</span></span>  
<span data-ttu-id="af625-115">No retorno, esta propriedade está definida como **verdadeiro** se o nó de destino tem de ser reiniciado.</span><span class="sxs-lookup"><span data-stu-id="af625-115">On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="af625-116">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="af625-116">Return value</span></span>
------------

<span data-ttu-id="af625-117">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="af625-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="af625-118">Observações</span><span class="sxs-lookup"><span data-stu-id="af625-118">Remarks</span></span>

<span data-ttu-id="af625-119">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="af625-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="af625-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="af625-120">Requirements</span></span>
------------
><span data-ttu-id="af625-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="af625-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="af625-122">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="af625-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="af625-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af625-123">See also</span></span>


[<span data-ttu-id="af625-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="af625-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



