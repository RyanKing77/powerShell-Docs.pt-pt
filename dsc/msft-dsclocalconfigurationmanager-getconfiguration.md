---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Método GetConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 46eec896df643996bea5f2c371a9294034caae6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f5c1d-103">Método GetConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="f5c1d-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f5c1d-104">Envia o documento de configuração para o nó gerido e utiliza o **obter** método do agente de configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="f5c1d-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="f5c1d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5c1d-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="f5c1d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f5c1d-106">Parameters</span></span>
----------

<span data-ttu-id="f5c1d-107">*configurationData* \[no\] Especifica os dados de configuração para enviar.</span><span class="sxs-lookup"><span data-stu-id="f5c1d-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="f5c1d-108">*configurações* \[saída\] no retorno, contém uma instância incorporada das configurações.</span><span class="sxs-lookup"><span data-stu-id="f5c1d-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="f5c1d-109">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="f5c1d-109">Return value</span></span>
------------

<span data-ttu-id="f5c1d-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="f5c1d-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5c1d-111">Observações</span><span class="sxs-lookup"><span data-stu-id="f5c1d-111">Remarks</span></span>

<span data-ttu-id="f5c1d-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="f5c1d-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f5c1d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f5c1d-113">Requirements</span></span>
------------
><span data-ttu-id="f5c1d-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f5c1d-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="f5c1d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f5c1d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="f5c1d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5c1d-116">See also</span></span>


[<span data-ttu-id="f5c1d-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f5c1d-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)