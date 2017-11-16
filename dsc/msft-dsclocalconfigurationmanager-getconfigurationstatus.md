---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: e02ed81a7b8436323bc68aaa2587a445e6a5adf9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="615a7-103">Método de GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="615a7-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="615a7-104">Obter o histórico do Estado de configuração.</span><span class="sxs-lookup"><span data-stu-id="615a7-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="615a7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="615a7-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="615a7-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="615a7-106">Parameters</span></span>
----------

<span data-ttu-id="615a7-107">*Todos os* \[no\]</span><span class="sxs-lookup"><span data-stu-id="615a7-107">*All* \[in\]</span></span>  
<span data-ttu-id="615a7-108">**Verdadeiro** se este método deverá devolver informações sobre todas a configuração é executada na máquina, incluindo a aplicação de configuração e a verificação de consistência.</span><span class="sxs-lookup"><span data-stu-id="615a7-108">**true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="615a7-109">*configurationStatus* \[enviados\]</span><span class="sxs-lookup"><span data-stu-id="615a7-109">*configurationStatus* \[out\]</span></span>  
<span data-ttu-id="615a7-110">No retorno, contém uma instância do embedded o **MSFT_DSCConfigurationStatus** classe que define as definições.</span><span class="sxs-lookup"><span data-stu-id="615a7-110">On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="615a7-111">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="615a7-111">Return value</span></span>
------------

<span data-ttu-id="615a7-112">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="615a7-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="615a7-113">Observações</span><span class="sxs-lookup"><span data-stu-id="615a7-113">Remarks</span></span>

<span data-ttu-id="615a7-114">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="615a7-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="615a7-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="615a7-115">Requirements</span></span>
------------
><span data-ttu-id="615a7-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="615a7-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="615a7-117">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="615a7-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="615a7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="615a7-118">See also</span></span>


[<span data-ttu-id="615a7-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="615a7-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



