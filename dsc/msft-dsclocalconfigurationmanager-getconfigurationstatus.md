---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 725b1a2a62510a4e9b59aabdec8a7e502c737bfc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="12319-103">Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="12319-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="12319-104">Obter o histórico do Estado de configuração.</span><span class="sxs-lookup"><span data-stu-id="12319-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="12319-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12319-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="12319-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="12319-106">Parameters</span></span>
----------

<span data-ttu-id="12319-107">*Todos os* \[no\] **verdadeiro** se este método deverá devolver informações sobre todas a configuração é executada na máquina, incluindo a aplicação de configuração e a verificação de consistência.</span><span class="sxs-lookup"><span data-stu-id="12319-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="12319-108">*configurationStatus* \[saída\] no retorno, contém uma instância do embedded o **MSFT_DSCConfigurationStatus** classe que define as definições.</span><span class="sxs-lookup"><span data-stu-id="12319-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="12319-109">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="12319-109">Return value</span></span>
------------

<span data-ttu-id="12319-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="12319-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="12319-111">Observações</span><span class="sxs-lookup"><span data-stu-id="12319-111">Remarks</span></span>

<span data-ttu-id="12319-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="12319-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="12319-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="12319-113">Requirements</span></span>
------------
><span data-ttu-id="12319-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="12319-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="12319-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="12319-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="12319-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12319-116">See also</span></span>


[<span data-ttu-id="12319-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="12319-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)