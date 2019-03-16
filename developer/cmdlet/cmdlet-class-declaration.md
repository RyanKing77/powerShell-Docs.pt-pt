---
title: Declaração de classe cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 3168275423dc65fcb2e41dedd9bea275ede58397
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055092"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="d92fd-102">Cmdlet Class Declaration (Declaração da Classe de Cmdlets)</span><span class="sxs-lookup"><span data-stu-id="d92fd-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="d92fd-103">Uma classe de Microsoft .NET Framework está declarada como um cmdlet, especificando o **Cmdlet** atributo como metadados para a classe.</span><span class="sxs-lookup"><span data-stu-id="d92fd-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="d92fd-104">(A **Cmdlet** atributo é o único atributo obrigatório para todos os cmdlets).</span><span class="sxs-lookup"><span data-stu-id="d92fd-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span> <span data-ttu-id="d92fd-105">Quando especificar a **Cmdlet** atributo, tem de especificar o par de verbo e substantivo que identifica o cmdlet para o utilizador.</span><span class="sxs-lookup"><span data-stu-id="d92fd-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="d92fd-106">Além disso, tem de descrever a funcionalidade do Windows PowerShell que suporta o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d92fd-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="d92fd-107">Para obter mais informações sobre a sintaxe de declaração é utilizada para especificar a **Cmdlet** de atributos, consulte [declaração de atributo do Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="d92fd-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d92fd-108">O **Cmdlet** atributo é definido pela [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="d92fd-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="d92fd-109">As propriedades dessa classe correspondem aos parâmetros de declaração que são utilizados quando declara o atributo.</span><span class="sxs-lookup"><span data-stu-id="d92fd-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="d92fd-110">Substantivos</span><span class="sxs-lookup"><span data-stu-id="d92fd-110">Nouns</span></span>

<span data-ttu-id="d92fd-111">O substantivo do cmdlet Especifica os recursos no qual o cmdlet atua.</span><span class="sxs-lookup"><span data-stu-id="d92fd-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="d92fd-112">O substantivo diferencia os seus cmdlets de outros cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d92fd-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="d92fd-113">Substantivos em nomes de cmdlet tem de ser específico e, no caso de substantivos genéricos, tal como *servidor*, é melhor adicionar um prefixo curto que diferencia o recurso a partir de outros recursos semelhantes.</span><span class="sxs-lookup"><span data-stu-id="d92fd-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="d92fd-114">Por exemplo, é um nome de cmdlet que inclui um substantivo com um prefixo `Get-SQLServer`.</span><span class="sxs-lookup"><span data-stu-id="d92fd-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="d92fd-115">A combinação de um substantivo específico com um verbo mais geral permite ao utilizador localizar rapidamente o cmdlet por sua ação e, em seguida, identifique o cmdlet ao seu recurso, evitando duplicação de nome do cmdlet desnecessários.</span><span class="sxs-lookup"><span data-stu-id="d92fd-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="d92fd-116">Para obter uma lista de carateres especiais que não pode ser utilizado em nomes de cmdlet, consulte [diretrizes de desenvolvimento necessário](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="d92fd-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="d92fd-117">Verbos</span><span class="sxs-lookup"><span data-stu-id="d92fd-117">Verbs</span></span>

<span data-ttu-id="d92fd-118">Quando especificar um verbo, as diretrizes de desenvolvimento exigem que utilize um dos verbos predefinidos fornecidos pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d92fd-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="d92fd-119">Ao utilizar um desses verbos predefinidos, irá garantir a consistência entre os cmdlets que escreve e os cmdlets que são escritos pela Microsoft e por outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="d92fd-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="d92fd-120">Por exemplo, o verbo "Get" é utilizado para cmdlets que obtêm dados.</span><span class="sxs-lookup"><span data-stu-id="d92fd-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="d92fd-121">Para obter mais informações sobre as diretrizes para verbos, consulte [nomes de verbo do Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="d92fd-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="d92fd-122">Para obter uma lista de carateres especiais que não pode ser utilizado em nomes de cmdlet, consulte [diretrizes de desenvolvimento necessário](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="d92fd-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="d92fd-123">Suporte a funcionalidade do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d92fd-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="d92fd-124">O **Cmdlet** atributo também permite que especifique de que seu cmdlet oferece suporte a algumas das funcionalidades comuns que é fornecida pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d92fd-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="d92fd-125">Isto inclui suporte para funcionalidades comuns, tais como a confirmação de comentários do utilizador (referida como suporte para a funcionalidade de ShouldProcess) e suporte para transações.</span><span class="sxs-lookup"><span data-stu-id="d92fd-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="d92fd-126">(Suporte para transações foi introduzido no Windows PowerShell 2.0).</span><span class="sxs-lookup"><span data-stu-id="d92fd-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="d92fd-127">Para obter mais informações sobre a sintaxe de declaração é utilizada para especificar a **Cmdlet** de atributos, consulte [declaração de atributo do Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="d92fd-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="d92fd-128">Definição de classe do cmdlet</span><span class="sxs-lookup"><span data-stu-id="d92fd-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="d92fd-129">O código a seguir é a definição de uma classe de cmdlet GetProc.</span><span class="sxs-lookup"><span data-stu-id="d92fd-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="d92fd-130">Observe que esse Pascal casing é utilizado e que o nome da classe inclui o verbo e substantivo do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d92fd-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a><span data-ttu-id="d92fd-131">Letras maiúsculas e minúsculas de Pascal</span><span class="sxs-lookup"><span data-stu-id="d92fd-131">Pascal Casing</span></span>

<span data-ttu-id="d92fd-132">Ao atribuir um nome de cmdlets, utilize Pascal casing.</span><span class="sxs-lookup"><span data-stu-id="d92fd-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="d92fd-133">Por exemplo, o `Get-Item` e `Get-ItemProperty` cmdlets Mostrar a forma correta para utilizar a capitalização quando atribuir nomes a cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d92fd-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="d92fd-134">Veja Também</span><span class="sxs-lookup"><span data-stu-id="d92fd-134">See Also</span></span>

[<span data-ttu-id="d92fd-135">System.Management.Automation.CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="d92fd-135">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="d92fd-136">Declaração CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="d92fd-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="d92fd-137">Nomes de verbo do cmdlet</span><span class="sxs-lookup"><span data-stu-id="d92fd-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="d92fd-138">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d92fd-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="d92fd-139">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d92fd-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
