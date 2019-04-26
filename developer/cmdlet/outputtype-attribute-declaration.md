---
title: Declaração de atributo OutputType | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067608"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="2fb5f-102">OutputType Attribute Declaration (Declaração do Atributo OutputType)</span><span class="sxs-lookup"><span data-stu-id="2fb5f-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="2fb5f-103">O `OutputType` atributo identifica os tipos do .NET Framework devolvidos pelo cmdlet, função ou script.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="2fb5f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2fb5f-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="2fb5f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2fb5f-105">Parameters</span></span>

<span data-ttu-id="2fb5f-106">Tipo (`string[]` ou `Type[]`) necessária.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="2fb5f-107">Especifica os tipos devolvidos pelo cmdlet função ou script.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="2fb5f-108">ParameterSetName (string[]) opcional.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="2fb5f-109">Especifica os conjuntos de parâmetros que retornam tipos especificados no `type` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="2fb5f-110">providerCmdlet opcional.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-110">providerCmdlet Optional.</span></span> <span data-ttu-id="2fb5f-111">Especifica o cmdlet de fornecedor que retorna os tipos especificados no `type` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="2fb5f-112">Veja Também</span><span class="sxs-lookup"><span data-stu-id="2fb5f-112">See Also</span></span>

[<span data-ttu-id="2fb5f-113">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2fb5f-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
