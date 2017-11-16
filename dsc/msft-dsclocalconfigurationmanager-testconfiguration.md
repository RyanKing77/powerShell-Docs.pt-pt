---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de TestConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 8e9986837aaf41b1396a2399c58675bc51b0b708
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7a0b6-103">Método de TestConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="7a0b6-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7a0b6-104">Envia o documento de configuração para o nó gerido e verifica a configuração atual contra o documento.</span><span class="sxs-lookup"><span data-stu-id="7a0b6-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="7a0b6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7a0b6-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="7a0b6-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7a0b6-106">Parameters</span></span>
----------

<span data-ttu-id="7a0b6-107">*configurationData* \[no\]</span><span class="sxs-lookup"><span data-stu-id="7a0b6-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="7a0b6-108">Dados de ambiente para o confuguration.</span><span class="sxs-lookup"><span data-stu-id="7a0b6-108">Environment data for the confuguration.</span></span>

<span data-ttu-id="7a0b6-109">*InDesiredState* \[enviados\]</span><span class="sxs-lookup"><span data-stu-id="7a0b6-109">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="7a0b6-110">No retorno, especifica se o nó gerido está num estado especificado pelo documento de configuração.</span><span class="sxs-lookup"><span data-stu-id="7a0b6-110">On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="7a0b6-111">*ResourcesInDesiredState* \[enviados\]</span><span class="sxs-lookup"><span data-stu-id="7a0b6-111">*ResourcesInDesiredState* \[out\]</span></span>  
<span data-ttu-id="7a0b6-112">No retorno, contém uma instância do embedded o **MSFT_ResourceInDesiredState** classe que especifica os recursos que estão no estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="7a0b6-112">On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="7a0b6-113">*ResourcesNotInDesiredState* \[enviados\]</span><span class="sxs-lookup"><span data-stu-id="7a0b6-113">*ResourcesNotInDesiredState* \[out\]</span></span>  
<span data-ttu-id="7a0b6-114">No retorno, contém uma instância do embedded o **MSFT_ResourceNotInDesiredState** classe que especifica os recursos que não estão no estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="7a0b6-114">On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="7a0b6-115">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="7a0b6-115">Return value</span></span>
------------

<span data-ttu-id="7a0b6-116">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="7a0b6-116">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7a0b6-117">Observações</span><span class="sxs-lookup"><span data-stu-id="7a0b6-117">Remarks</span></span>

<span data-ttu-id="7a0b6-118">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="7a0b6-118">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7a0b6-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7a0b6-119">Requirements</span></span>
------------
><span data-ttu-id="7a0b6-120">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7a0b6-120">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7a0b6-121">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7a0b6-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7a0b6-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a0b6-122">See also</span></span>


[<span data-ttu-id="7a0b6-123">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7a0b6-123">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



