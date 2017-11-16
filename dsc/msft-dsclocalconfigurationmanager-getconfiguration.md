---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de GetConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 96676a76a0302543e5e4a214c82ed952d7f52a71
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="24b80-103">Método de GetConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="24b80-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="24b80-104">Envia o documento de configuração para o nó gerido e utiliza o **obter** método do agente de configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="24b80-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="24b80-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="24b80-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="24b80-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="24b80-106">Parameters</span></span>
----------

<span data-ttu-id="24b80-107">*configurationData* \[no\]</span><span class="sxs-lookup"><span data-stu-id="24b80-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="24b80-108">Especifica os dados de configuração para enviar.</span><span class="sxs-lookup"><span data-stu-id="24b80-108">Specifies the configuration data to send.</span></span>

<span data-ttu-id="24b80-109">*configurações* \[enviados\]</span><span class="sxs-lookup"><span data-stu-id="24b80-109">*configurations* \[out\]</span></span>  
<span data-ttu-id="24b80-110">No retorno, contém uma instância incorporada das configurações.</span><span class="sxs-lookup"><span data-stu-id="24b80-110">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="24b80-111">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="24b80-111">Return value</span></span>
------------

<span data-ttu-id="24b80-112">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="24b80-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="24b80-113">Observações</span><span class="sxs-lookup"><span data-stu-id="24b80-113">Remarks</span></span>

<span data-ttu-id="24b80-114">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="24b80-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="24b80-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="24b80-115">Requirements</span></span>
------------
><span data-ttu-id="24b80-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="24b80-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="24b80-117">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="24b80-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="24b80-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24b80-118">See also</span></span>


[<span data-ttu-id="24b80-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="24b80-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



