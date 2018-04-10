---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: dde4ac003b346018561481e05ca7374475f9ff1d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="19ce1-103">Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="19ce1-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="19ce1-104">Obter o histórico do Estado de configuração.</span><span class="sxs-lookup"><span data-stu-id="19ce1-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="19ce1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="19ce1-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="19ce1-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="19ce1-106">Parameters</span></span>
----------

<span data-ttu-id="19ce1-107">*Todos os* \[no\] **verdadeiro** se este método deverá devolver informações sobre todas a configuração é executada na máquina, incluindo a aplicação de configuração e a verificação de consistência.</span><span class="sxs-lookup"><span data-stu-id="19ce1-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="19ce1-108">*configurationStatus* \[saída\] no retorno, contém uma instância do embedded o **MSFT_DSCConfigurationStatus** classe que define as definições.</span><span class="sxs-lookup"><span data-stu-id="19ce1-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="19ce1-109">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="19ce1-109">Return value</span></span>
------------

<span data-ttu-id="19ce1-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="19ce1-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="19ce1-111">Observações</span><span class="sxs-lookup"><span data-stu-id="19ce1-111">Remarks</span></span>

<span data-ttu-id="19ce1-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="19ce1-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="19ce1-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="19ce1-113">Requirements</span></span>
------------
><span data-ttu-id="19ce1-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="19ce1-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="19ce1-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="19ce1-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="19ce1-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19ce1-116">See also</span></span>


[<span data-ttu-id="19ce1-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="19ce1-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)