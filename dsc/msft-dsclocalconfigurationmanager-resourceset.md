---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de ResourceSet da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 3486ef559102929f8d05994a4bf6e45d49a0c140
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ff668-103">Método de ResourceSet da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ff668-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ff668-104">Chamadas diretamente a **definir** método de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="ff668-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="ff668-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ff668-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="ff668-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ff668-106">Parameters</span></span>
----------

<span data-ttu-id="ff668-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="ff668-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="ff668-108">O nome do recurso para chamar.</span><span class="sxs-lookup"><span data-stu-id="ff668-108">The name of the resource to call.</span></span>

<span data-ttu-id="ff668-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="ff668-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="ff668-110">O nome do módulo que contém o recurso a chamada.</span><span class="sxs-lookup"><span data-stu-id="ff668-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="ff668-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="ff668-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="ff668-112">Especifica o nome de propriedade de recursos e o respetivo valor numa tabela hash como chave e valor, respetivamente.</span><span class="sxs-lookup"><span data-stu-id="ff668-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="ff668-113">Utilize o [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet para detetar as propriedades de recurso e os respetivos tipos.</span><span class="sxs-lookup"><span data-stu-id="ff668-113">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="ff668-114">*RebootRequired* \[out\]</span><span class="sxs-lookup"><span data-stu-id="ff668-114">*RebootRequired* \[out\]</span></span>  
<span data-ttu-id="ff668-115">No retorno, esta propriedade está definida como **verdadeiro** se o nó de destino tem de ser reiniciado.</span><span class="sxs-lookup"><span data-stu-id="ff668-115">On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="ff668-116">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="ff668-116">Return value</span></span>
------------

<span data-ttu-id="ff668-117">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="ff668-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ff668-118">Observações</span><span class="sxs-lookup"><span data-stu-id="ff668-118">Remarks</span></span>

<span data-ttu-id="ff668-119">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="ff668-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ff668-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ff668-120">Requirements</span></span>
------------
><span data-ttu-id="ff668-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ff668-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ff668-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ff668-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ff668-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff668-123">See also</span></span>


[<span data-ttu-id="ff668-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ff668-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



