---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método ResourceSet
ms.openlocfilehash: 18364027b249e502e1f0b8802d9f3e031c7b07ce
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727102"
---
# <a name="resourceset-method"></a><span data-ttu-id="b64be-103">Método ResourceSet</span><span class="sxs-lookup"><span data-stu-id="b64be-103">ResourceSet method</span></span>

<span data-ttu-id="b64be-104">Chama diretamente a **definir** método de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="b64be-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="b64be-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b64be-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="b64be-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b64be-106">Parameters</span></span>

<span data-ttu-id="b64be-107">*ResourceType* \[no\] o nome do recurso a chamar.</span><span class="sxs-lookup"><span data-stu-id="b64be-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="b64be-108">*ModuleName* \[no\] o nome do módulo que contém o recurso para chamar.</span><span class="sxs-lookup"><span data-stu-id="b64be-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="b64be-109">*resourceProperty* \[no\] Especifica o nome de propriedade de recursos e seu valor numa tabela de hash como chave e valor, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="b64be-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="b64be-110">Utilize o [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet para detetar as propriedades de recurso e os respetivos tipos.</span><span class="sxs-lookup"><span data-stu-id="b64be-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="b64be-111">*RebootRequired* \[horizontalmente\] em retorno, esta propriedade é definida como **verdadeiro** se o nó de destino tem de ser reiniciado.</span><span class="sxs-lookup"><span data-stu-id="b64be-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="b64be-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b64be-112">Return value</span></span>

<span data-ttu-id="b64be-113">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="b64be-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b64be-114">Observações</span><span class="sxs-lookup"><span data-stu-id="b64be-114">Remarks</span></span>

<span data-ttu-id="b64be-115">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="b64be-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b64be-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b64be-116">Requirements</span></span>

<span data-ttu-id="b64be-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b64be-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b64be-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b64be-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b64be-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b64be-119">See also</span></span>

[<span data-ttu-id="b64be-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b64be-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
