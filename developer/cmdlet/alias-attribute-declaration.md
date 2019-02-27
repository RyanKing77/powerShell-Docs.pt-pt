---
title: Declaração de atributo de alias | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846145"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="26fec-102">Alias Attribute Declaration (Declaração do Atributo Alias)</span><span class="sxs-lookup"><span data-stu-id="26fec-102">Alias Attribute Declaration</span></span>

<span data-ttu-id="26fec-103">O atributo de Alias permite que o usuário Especifique nomes diferentes para um parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="26fec-103">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="26fec-104">Aliases que podem ser utilizados para fornecer os atalhos para um nome de parâmetro ou podem fornecer nomes diferentes que são adequados para diferentes cenários.</span><span class="sxs-lookup"><span data-stu-id="26fec-104">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="26fec-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26fec-105">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="26fec-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="26fec-106">Parameters</span></span>

<span data-ttu-id="26fec-107">`aliasName` (String[]) É necessário.</span><span class="sxs-lookup"><span data-stu-id="26fec-107">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="26fec-108">Especifica um conjunto de nomes de alias separados por vírgulas para o parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="26fec-108">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="26fec-109">Observações</span><span class="sxs-lookup"><span data-stu-id="26fec-109">Remarks</span></span>

- <span data-ttu-id="26fec-110">O atributo de Alias é utilizado com o atributo de parâmetro ao especificar um parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="26fec-110">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="26fec-111">Para obter mais informações sobre como declarar esses atributos, consulte [como declarar parâmetros de Cmdlet](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="26fec-111">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="26fec-112">Cada nome de alias têm de ser exclusivo dentro de um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="26fec-112">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="26fec-113">Windows PowerShell não verifica se os nomes de alias duplicado.</span><span class="sxs-lookup"><span data-stu-id="26fec-113">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="26fec-114">O atributo de Alias é utilizado uma vez para cada parâmetro num cmdlet.</span><span class="sxs-lookup"><span data-stu-id="26fec-114">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="26fec-115">O atributo de Alias é definido pela [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="26fec-115">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="26fec-116">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="26fec-116">See Also</span></span>

[<span data-ttu-id="26fec-117">Aliases de parâmetro</span><span class="sxs-lookup"><span data-stu-id="26fec-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="26fec-118">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="26fec-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
