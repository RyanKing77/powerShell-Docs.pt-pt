---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Método TestConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2df04d317bd5e7a5c2a713d92be57c5c9a9f5e8c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="11080-103">Método TestConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="11080-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="11080-104">Envia o documento de configuração para o nó gerido e verifica a configuração atual contra o documento.</span><span class="sxs-lookup"><span data-stu-id="11080-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="11080-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11080-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="11080-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="11080-106">Parameters</span></span>
----------

<span data-ttu-id="11080-107">*configurationData* \[no\] dados de ambiente para o confuguration.</span><span class="sxs-lookup"><span data-stu-id="11080-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="11080-108">*InDesiredState* \[saída\] no retorno, especifica se o nó gerido está num estado especificado pelo documento de configuração.</span><span class="sxs-lookup"><span data-stu-id="11080-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="11080-109">*ResourcesInDesiredState* \[saída\] no retorno, contém uma instância do embedded o **MSFT_ResourceInDesiredState** classe que especifica os recursos que estão no estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="11080-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="11080-110">*ResourcesNotInDesiredState* \[saída\] no retorno, contém uma instância do embedded o **MSFT_ResourceNotInDesiredState** classe que especifica os recursos que não estão no estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="11080-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="11080-111">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="11080-111">Return value</span></span>
------------

<span data-ttu-id="11080-112">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="11080-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="11080-113">Observações</span><span class="sxs-lookup"><span data-stu-id="11080-113">Remarks</span></span>

<span data-ttu-id="11080-114">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="11080-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="11080-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11080-115">Requirements</span></span>
------------
><span data-ttu-id="11080-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="11080-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="11080-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="11080-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="11080-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11080-118">See also</span></span>


[<span data-ttu-id="11080-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="11080-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)