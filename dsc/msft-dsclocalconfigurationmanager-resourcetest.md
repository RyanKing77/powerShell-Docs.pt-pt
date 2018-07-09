---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método ResourceTest da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e7645b0c6b93b96cb01f72c1c92d468f7642ea13
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893081"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fbfc8-103">Método ResourceTest da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="fbfc8-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fbfc8-104">Chama diretamente a **teste** método de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="fbfc8-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="fbfc8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbfc8-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="fbfc8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fbfc8-106">Parameters</span></span>

<span data-ttu-id="fbfc8-107">*ResourceType* \[no\] o nome do recurso a chamar.</span><span class="sxs-lookup"><span data-stu-id="fbfc8-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="fbfc8-108">*ModuleName* \[no\] o nome do módulo que contém o recurso para chamar.</span><span class="sxs-lookup"><span data-stu-id="fbfc8-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="fbfc8-109">*resourceProperty* \[no\] Especifica o nome de propriedade de recursos e seu valor numa tabela de hash como chave e valor, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="fbfc8-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="fbfc8-110">Utilize o [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet para detetar as propriedades de recurso e os respetivos tipos.</span><span class="sxs-lookup"><span data-stu-id="fbfc8-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="fbfc8-111">*InDesiredState* \[horizontalmente\] em retorno, esta propriedade é definida como **verdadeiro** se o nó de destino está no estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="fbfc8-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="fbfc8-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fbfc8-112">Return value</span></span>

<span data-ttu-id="fbfc8-113">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="fbfc8-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fbfc8-114">Observações</span><span class="sxs-lookup"><span data-stu-id="fbfc8-114">Remarks</span></span>

<span data-ttu-id="fbfc8-115">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="fbfc8-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fbfc8-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fbfc8-116">Requirements</span></span>

<span data-ttu-id="fbfc8-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fbfc8-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="fbfc8-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fbfc8-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="fbfc8-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbfc8-119">See also</span></span>

[<span data-ttu-id="fbfc8-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fbfc8-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)