---
title: Aliases de parâmetro | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844934"
---
# <a name="parameter-aliases"></a><span data-ttu-id="5ec92-102">Parameter Aliases (Aliases de Parâmetros)</span><span class="sxs-lookup"><span data-stu-id="5ec92-102">Parameter Aliases</span></span>

<span data-ttu-id="5ec92-103">Os parâmetros de cmdlet também podem ter aliases.</span><span class="sxs-lookup"><span data-stu-id="5ec92-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="5ec92-104">Pode utilizar os aliases em vez dos nomes de parâmetros, quando escreve ou especificar o parâmetro num comando.</span><span class="sxs-lookup"><span data-stu-id="5ec92-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="5ec92-105">Vantagens da utilização de Aliases</span><span class="sxs-lookup"><span data-stu-id="5ec92-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="5ec92-106">Adicionar aliases para parâmetros fornece as seguintes vantagens.</span><span class="sxs-lookup"><span data-stu-id="5ec92-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="5ec92-107">Pode fornecer um atalho para que o utilizador não tem de utilizar o nome do parâmetro completo quando o cmdlet é chamado.</span><span class="sxs-lookup"><span data-stu-id="5ec92-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="5ec92-108">Por exemplo, poderia usar o alias "CN" em vez do nome de parâmetro "ComputerName".</span><span class="sxs-lookup"><span data-stu-id="5ec92-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="5ec92-109">Se quiser fornecer nomes diferentes para o mesmo parâmetro, pode definir vários aliases.</span><span class="sxs-lookup"><span data-stu-id="5ec92-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="5ec92-110">Pode querer definir vários aliases, se tem que trabalhar com vários grupos de utilizadores que se referem aos mesmos dados de formas diferentes.</span><span class="sxs-lookup"><span data-stu-id="5ec92-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="5ec92-111">Pode proporcionar compatibilidade para os scripts existentes se mudar o nome de um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5ec92-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="5ec92-112">Ao utilizar o atributo de Alias, juntamente com o atributo ValueFromPipelineByName, pode definir um parâmetro que permite seu cmdlet vincular a diferentes tipos de objeto.</span><span class="sxs-lookup"><span data-stu-id="5ec92-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="5ec92-113">Por exemplo, digamos que tinha dois objetos de diferentes tipos e o primeiro objeto tinha uma propriedade de escritor e o segundo objeto tinha uma propriedade de editor.</span><span class="sxs-lookup"><span data-stu-id="5ec92-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="5ec92-114">Se seu cmdlet tinha um parâmetro que tiveram aliases de escritor e editor e o cmdlet aceitaram entrada do pipeline com base em nomes de propriedade, seu cmdlet poderia vincular-se os dois objetos usando os dois aliases de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5ec92-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="5ec92-115">Para obter mais informações sobre os aliases que pode ser utilizado com parâmetros específicos, consulte [nomes de parâmetros comuns](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="5ec92-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="5ec92-116">Definir Aliases de parâmetro</span><span class="sxs-lookup"><span data-stu-id="5ec92-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="5ec92-117">Para definir um alias para um parâmetro, declare o atributo de Alias, como mostra a seguinte declaração de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5ec92-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="5ec92-118">Neste exemplo, vários aliases são definidas para o mesmo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5ec92-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="5ec92-119">(Para obter mais informações, consulte[como declarar parâmetros de Cmdlet](./how-to-declare-cmdlet-parameters.md).)</span><span class="sxs-lookup"><span data-stu-id="5ec92-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a><span data-ttu-id="5ec92-120">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="5ec92-120">See Also</span></span>

[<span data-ttu-id="5ec92-121">Nomes de parâmetros comuns</span><span class="sxs-lookup"><span data-stu-id="5ec92-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="5ec92-122">Como declarar parâmetros do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5ec92-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

[<span data-ttu-id="5ec92-123">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5ec92-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
