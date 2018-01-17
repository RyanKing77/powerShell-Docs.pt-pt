---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de TestConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 04f0f3146473dc71f492086449d9dce5467c55db
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="1da17-103">Método de TestConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="1da17-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="1da17-104">Envia o documento de configuração para o nó gerido e verifica a configuração atual contra o documento.</span><span class="sxs-lookup"><span data-stu-id="1da17-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="1da17-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1da17-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="1da17-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1da17-106">Parameters</span></span>
----------

<span data-ttu-id="1da17-107">*configurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="1da17-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="1da17-108">Dados de ambiente para o confuguration.</span><span class="sxs-lookup"><span data-stu-id="1da17-108">Environment data for the confuguration.</span></span>

<span data-ttu-id="1da17-109">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="1da17-109">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="1da17-110">No retorno, especifica se o nó gerido está num estado especificado pelo documento de configuração.</span><span class="sxs-lookup"><span data-stu-id="1da17-110">On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="1da17-111">*ResourcesInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="1da17-111">*ResourcesInDesiredState* \[out\]</span></span>  
<span data-ttu-id="1da17-112">No retorno, contém uma instância do embedded o **MSFT_ResourceInDesiredState** classe que especifica os recursos que estão no estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="1da17-112">On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="1da17-113">*ResourcesNotInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="1da17-113">*ResourcesNotInDesiredState* \[out\]</span></span>  
<span data-ttu-id="1da17-114">No retorno, contém uma instância do embedded o **MSFT_ResourceNotInDesiredState** classe que especifica os recursos que não estão no estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="1da17-114">On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="1da17-115">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="1da17-115">Return value</span></span>
------------

<span data-ttu-id="1da17-116">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="1da17-116">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1da17-117">Observações</span><span class="sxs-lookup"><span data-stu-id="1da17-117">Remarks</span></span>

<span data-ttu-id="1da17-118">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="1da17-118">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1da17-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1da17-119">Requirements</span></span>
------------
><span data-ttu-id="1da17-120">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1da17-120">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="1da17-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1da17-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="1da17-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1da17-122">See also</span></span>


[<span data-ttu-id="1da17-123">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1da17-123">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



