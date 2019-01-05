---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método ResourceGet da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1b74adf2327af2e0f9416f1d00eac4e3b75e9013
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048388"
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="dfc0e-103">Método ResourceGet da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="dfc0e-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="dfc0e-104">Chama diretamente a **obter** método de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="dfc0e-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="dfc0e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dfc0e-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="dfc0e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dfc0e-106">Parameters</span></span>

<span data-ttu-id="dfc0e-107">*ResourceType* \[no\] o nome do recurso a chamar.</span><span class="sxs-lookup"><span data-stu-id="dfc0e-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="dfc0e-108">*ModuleName* \[no\] o nome do módulo que contém o recurso para chamar.</span><span class="sxs-lookup"><span data-stu-id="dfc0e-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="dfc0e-109">*resourceProperty* \[no\] Especifica o nome de propriedade de recursos e seu valor numa tabela de hash como chave e valor, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="dfc0e-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="dfc0e-110">Utilize o [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet para detetar as propriedades de recurso e os respetivos tipos.</span><span class="sxs-lookup"><span data-stu-id="dfc0e-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="dfc0e-111">*configurações* \[horizontalmente\] no retorno, contém uma instância incorporada das configurações.</span><span class="sxs-lookup"><span data-stu-id="dfc0e-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="dfc0e-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="dfc0e-112">Return value</span></span>

<span data-ttu-id="dfc0e-113">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="dfc0e-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="dfc0e-114">Observações</span><span class="sxs-lookup"><span data-stu-id="dfc0e-114">Remarks</span></span>

<span data-ttu-id="dfc0e-115">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="dfc0e-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="dfc0e-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dfc0e-116">Requirements</span></span>

<span data-ttu-id="dfc0e-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="dfc0e-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="dfc0e-118">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="dfc0e-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="dfc0e-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfc0e-119">See also</span></span>

[<span data-ttu-id="dfc0e-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="dfc0e-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)