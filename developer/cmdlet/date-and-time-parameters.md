---
title: Data e hora parâmetros | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 49f6c667b0fd9678586559af39a33f982de0a68c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846712"
---
# <a name="date-and-time-parameters"></a><span data-ttu-id="f19b3-102">Date and Time Parameters (Parâmetros de Data e Hora)</span><span class="sxs-lookup"><span data-stu-id="f19b3-102">Date and Time Parameters</span></span>

<span data-ttu-id="f19b3-103">A tabela seguinte apresenta uma lista de nomes recomendados e funcionalidades para os parâmetros que lidam com informações de data e hora.</span><span class="sxs-lookup"><span data-stu-id="f19b3-103">The following table lists recommended names and functionality for parameters that handle date and time information.</span></span> <span data-ttu-id="f19b3-104">Parâmetros de data e hora são normalmente utilizados para registrar quando algo é criado ou acessado.</span><span class="sxs-lookup"><span data-stu-id="f19b3-104">Date and time parameters are typically used to record when something is created or accessed.</span></span>

<span data-ttu-id="f19b3-105">Tipo de dados acedidos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="f19b3-105">Accessed Data type: SwitchParameter</span></span>

<span data-ttu-id="f19b3-106">Implementar este parâmetro, de modo que quando é especificado o cmdlet irá operar nos recursos que foram acessados com base na data e hora especificada pelos `Before` e `After` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f19b3-106">Implement this parameter so that when it is specified the cmdlet will operate on the resources that have been accessed based on the date and time specified by the `Before` and `After` parameters.</span></span>

<span data-ttu-id="f19b3-107">Se este parâmetro for especificado, o `Created` e `Modified` parâmetros têm de não ser especificado.</span><span class="sxs-lookup"><span data-stu-id="f19b3-107">If this parameter is specified, the `Created` and `Modified` parameters must be not be specified.</span></span>

<span data-ttu-id="f19b3-108">Depois de tipo de dados: DateTime</span><span class="sxs-lookup"><span data-stu-id="f19b3-108">After Data type: DateTime</span></span>

<span data-ttu-id="f19b3-109">Implemente este parâmetro para especificar a data e hora após o qual foi utilizado o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f19b3-109">Implement this parameter to specify the date and time after which the cmdlet was used.</span></span> <span data-ttu-id="f19b3-110">Para o `After` parâmetro para trabalhar, o cmdlet também tem de ter uma `Accessed`, `Created`, ou `Modified` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f19b3-110">For the `After` parameter to work, the cmdlet must also have an `Accessed`, `Created`, or `Modified` parameter.</span></span> <span data-ttu-id="f19b3-111">E, esse parâmetro deve ser definido como `true` quando o cmdlet é chamado.</span><span class="sxs-lookup"><span data-stu-id="f19b3-111">And, that parameter must be set to `true` when the cmdlet is called.</span></span>

<span data-ttu-id="f19b3-112">Antes de tipo de dados: DateTime</span><span class="sxs-lookup"><span data-stu-id="f19b3-112">Before Data type: DateTime</span></span>

<span data-ttu-id="f19b3-113">Implemente este parâmetro para especificar a data e hora antes do qual foi utilizado o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f19b3-113">Implement this parameter to specify the date and time before which the cmdlet was used.</span></span> <span data-ttu-id="f19b3-114">Para o `Before` parâmetro para trabalhar, o cmdlet também tem de ter uma `Accessed`, `Created`, ou `Modified` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f19b3-114">For the `Before` parameter to work, the cmdlet must also have an `Accessed`, `Created`, or `Modified` parameter.</span></span> <span data-ttu-id="f19b3-115">E, esse parâmetro deve ser definido como `true` quando o cmdlet é chamado.</span><span class="sxs-lookup"><span data-stu-id="f19b3-115">And, that parameter must be set to `true` when the cmdlet is called.</span></span>

<span data-ttu-id="f19b3-116">Criou o tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="f19b3-116">Created Data type: SwitchParameter</span></span>

<span data-ttu-id="f19b3-117">Implementar este parâmetro, de modo que quando é especificado o cmdlet irá operar nos recursos que foram criados com base na data e hora especificada pelos `Before` e `After` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f19b3-117">Implement this parameter so that when it is specified the cmdlet will operate on the resources that have been created based on the date and time specified by the `Before` and `After` parameters.</span></span>

<span data-ttu-id="f19b3-118">Se este parâmetro for especificado, o `Accessed` e `Modified` parâmetros não pode ser especificados.</span><span class="sxs-lookup"><span data-stu-id="f19b3-118">If this parameter is specified, the `Accessed` and `Modified` parameters must not be specified.</span></span>

<span data-ttu-id="f19b3-119">Tipo de dados exatos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="f19b3-119">Exact Data type: SwitchParameter</span></span>

<span data-ttu-id="f19b3-120">Implemente este parâmetro, de modo que quando é especificado o termo de recursos tem de corresponder ao nome do recurso exatamente.</span><span class="sxs-lookup"><span data-stu-id="f19b3-120">Implement this parameter so that when it is specified the resource term must match the resource name exactly.</span></span> <span data-ttu-id="f19b3-121">Quando o parâmetro não for especificado o termo de recursos e o nome não têm de corresponder exatamente.</span><span class="sxs-lookup"><span data-stu-id="f19b3-121">When the parameter is not specified the resource term and name do not need to match exactly.</span></span>

<span data-ttu-id="f19b3-122">Tipo de dados modificados: DateTime</span><span class="sxs-lookup"><span data-stu-id="f19b3-122">Modified Data type: DateTime</span></span>

<span data-ttu-id="f19b3-123">Implementar este parâmetro, de modo que quando é especificado o cmdlet irá operar em recursos que foram alterados com base na data e hora especificada pelos `Before` e `After` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f19b3-123">Implement this parameter so that when it is specified the cmdlet will operate on resources that have been changed based on the date and time specified by the `Before` and `After` parameters.</span></span>

<span data-ttu-id="f19b3-124">Se este parâmetro for especificado, o `Accessed` e `Created` parâmetros não pode ser especificados.</span><span class="sxs-lookup"><span data-stu-id="f19b3-124">If this parameter is specified, the `Accessed` and `Created` parameters must not be specified.</span></span>

## <a name="see-also"></a><span data-ttu-id="f19b3-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="f19b3-125">See Also</span></span>

[<span data-ttu-id="f19b3-126">Parâmetros do cmdlet</span><span class="sxs-lookup"><span data-stu-id="f19b3-126">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="f19b3-127">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f19b3-127">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="f19b3-128">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f19b3-128">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
