---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Método ResourceSet da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 0c9c1d33117067d76d61036d5839f0b676eb4a97
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219621"
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bc36b-103">Método ResourceSet da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="bc36b-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bc36b-104">Chamadas diretamente a **definir** método de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="bc36b-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="bc36b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bc36b-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="bc36b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bc36b-106">Parameters</span></span>
----------

<span data-ttu-id="bc36b-107">*ResourceType* \[no\] o nome do recurso para chamar.</span><span class="sxs-lookup"><span data-stu-id="bc36b-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="bc36b-108">*ModuleName* \[no\] o nome do módulo que contém o recurso a chamada.</span><span class="sxs-lookup"><span data-stu-id="bc36b-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="bc36b-109">*resourceProperty* \[no\] Especifica o nome de propriedade de recursos e o respetivo valor numa tabela hash como chave e valor, respetivamente.</span><span class="sxs-lookup"><span data-stu-id="bc36b-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="bc36b-110">Utilize o [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet para detetar as propriedades de recurso e os respetivos tipos.</span><span class="sxs-lookup"><span data-stu-id="bc36b-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="bc36b-111">*RebootRequired* \[saída\] no retorno, esta propriedade está definida como **verdadeiro** se o nó de destino tem de ser reiniciado.</span><span class="sxs-lookup"><span data-stu-id="bc36b-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="bc36b-112">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="bc36b-112">Return value</span></span>
------------

<span data-ttu-id="bc36b-113">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="bc36b-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bc36b-114">Observações</span><span class="sxs-lookup"><span data-stu-id="bc36b-114">Remarks</span></span>

<span data-ttu-id="bc36b-115">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="bc36b-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bc36b-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bc36b-116">Requirements</span></span>
------------
><span data-ttu-id="bc36b-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bc36b-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="bc36b-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bc36b-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="bc36b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc36b-119">See also</span></span>


[<span data-ttu-id="bc36b-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bc36b-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)