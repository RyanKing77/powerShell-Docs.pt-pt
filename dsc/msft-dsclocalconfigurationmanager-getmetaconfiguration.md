---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 4f209014e9fde5841a9bce743f5364e6677d1e41
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e9eff-103">Método de GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e9eff-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e9eff-104">Obtém as definições de Configuration Manager local que são utilizadas para controlar o agente de configuração.</span><span class="sxs-lookup"><span data-stu-id="e9eff-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="e9eff-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9eff-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="e9eff-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e9eff-106">Parameters</span></span>
----------

<span data-ttu-id="e9eff-107">*Configuração meta* \[enviados\]</span><span class="sxs-lookup"><span data-stu-id="e9eff-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="e9eff-108">No retorno, contém uma instância do embedded o **MSFT_DSCMetaConfiguration** classe que define as definições.</span><span class="sxs-lookup"><span data-stu-id="e9eff-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="e9eff-109">Valor devolvido</span><span class="sxs-lookup"><span data-stu-id="e9eff-109">Return value</span></span>
------------

<span data-ttu-id="e9eff-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="e9eff-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e9eff-111">Observações</span><span class="sxs-lookup"><span data-stu-id="e9eff-111">Remarks</span></span>

<span data-ttu-id="e9eff-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="e9eff-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e9eff-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e9eff-113">Requirements</span></span>
------------
><span data-ttu-id="e9eff-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e9eff-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e9eff-115">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e9eff-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e9eff-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9eff-116">See also</span></span>


[<span data-ttu-id="e9eff-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e9eff-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



