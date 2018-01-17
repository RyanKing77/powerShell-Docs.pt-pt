---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: a41e7a15fc935c2cd5fd4cb66d0ab13509d5d4e0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ec0d3-103">Método de GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ec0d3-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ec0d3-104">Obter o histórico do Estado de configuração.</span><span class="sxs-lookup"><span data-stu-id="ec0d3-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="ec0d3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec0d3-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="ec0d3-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ec0d3-106">Parameters</span></span>
----------

<span data-ttu-id="ec0d3-107">*All* \[in\]</span><span class="sxs-lookup"><span data-stu-id="ec0d3-107">*All* \[in\]</span></span>  
<span data-ttu-id="ec0d3-108">**Verdadeiro** se este método deverá devolver informações sobre todas a configuração é executada na máquina, incluindo a aplicação de configuração e a verificação de consistência.</span><span class="sxs-lookup"><span data-stu-id="ec0d3-108">**true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="ec0d3-109">*configurationStatus* \[out\]</span><span class="sxs-lookup"><span data-stu-id="ec0d3-109">*configurationStatus* \[out\]</span></span>  
<span data-ttu-id="ec0d3-110">No retorno, contém uma instância do embedded o **MSFT_DSCConfigurationStatus** classe que define as definições.</span><span class="sxs-lookup"><span data-stu-id="ec0d3-110">On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="ec0d3-111">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="ec0d3-111">Return value</span></span>
------------

<span data-ttu-id="ec0d3-112">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="ec0d3-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ec0d3-113">Observações</span><span class="sxs-lookup"><span data-stu-id="ec0d3-113">Remarks</span></span>

<span data-ttu-id="ec0d3-114">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="ec0d3-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ec0d3-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ec0d3-115">Requirements</span></span>
------------
><span data-ttu-id="ec0d3-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ec0d3-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ec0d3-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ec0d3-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ec0d3-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec0d3-118">See also</span></span>


[<span data-ttu-id="ec0d3-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ec0d3-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



