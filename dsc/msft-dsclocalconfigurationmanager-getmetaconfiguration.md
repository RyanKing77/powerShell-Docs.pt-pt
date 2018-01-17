---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 695be4ee6490567295fda0cc44635870362d24b8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8d7fb-103">Método de GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="8d7fb-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8d7fb-104">Obtém as definições de Configuration Manager local que são utilizadas para controlar o agente de configuração.</span><span class="sxs-lookup"><span data-stu-id="8d7fb-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="8d7fb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d7fb-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="8d7fb-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8d7fb-106">Parameters</span></span>
----------

<span data-ttu-id="8d7fb-107">*MetaConfiguration* \[out\]</span><span class="sxs-lookup"><span data-stu-id="8d7fb-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="8d7fb-108">No retorno, contém uma instância do embedded o **MSFT_DSCMetaConfiguration** classe que define as definições.</span><span class="sxs-lookup"><span data-stu-id="8d7fb-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="8d7fb-109">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="8d7fb-109">Return value</span></span>
------------

<span data-ttu-id="8d7fb-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="8d7fb-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8d7fb-111">Observações</span><span class="sxs-lookup"><span data-stu-id="8d7fb-111">Remarks</span></span>

<span data-ttu-id="8d7fb-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="8d7fb-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8d7fb-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8d7fb-113">Requirements</span></span>
------------
><span data-ttu-id="8d7fb-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8d7fb-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="8d7fb-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8d7fb-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="8d7fb-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d7fb-116">See also</span></span>


[<span data-ttu-id="8d7fb-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8d7fb-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



