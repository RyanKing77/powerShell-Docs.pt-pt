---
title: Como declarar parâmetros do Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067921"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="ac135-102">How to Declare Cmdlet Parameters (Como Declarar Parâmetros de Cmdlets)</span><span class="sxs-lookup"><span data-stu-id="ac135-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="ac135-103">Estes exemplos mostram como declarar nomeado, posicional, obrigatória, opcional e parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ac135-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="ac135-104">Estes exemplos também mostram como definir um alias de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ac135-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="ac135-105">Como declarar um parâmetro com nome</span><span class="sxs-lookup"><span data-stu-id="ac135-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="ac135-106">Defina uma propriedade pública, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ac135-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="ac135-107">Ao adicionar o atributo de parâmetro, omita o `Position` palavra-chave do atributo.</span><span class="sxs-lookup"><span data-stu-id="ac135-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="ac135-108">Para obter mais informações sobre o atributo de parâmetro, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ac135-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="ac135-109">Como declarar um parâmetro posicional</span><span class="sxs-lookup"><span data-stu-id="ac135-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="ac135-110">Defina uma propriedade pública, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ac135-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="ac135-111">Ao adicionar o atributo de parâmetro, defina o `Position` palavra-chave para a posição de argumento.</span><span class="sxs-lookup"><span data-stu-id="ac135-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="ac135-112">Um valor de 0 indica a primeira posição.</span><span class="sxs-lookup"><span data-stu-id="ac135-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="ac135-113">Para obter mais informações sobre o atributo de parâmetro, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ac135-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="ac135-114">Como declarar um parâmetro obrigatório</span><span class="sxs-lookup"><span data-stu-id="ac135-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="ac135-115">Defina uma propriedade pública, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ac135-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="ac135-116">Ao adicionar o atributo de parâmetro, defina o `Mandatory` palavra-chave para `true`.</span><span class="sxs-lookup"><span data-stu-id="ac135-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="ac135-117">Para obter mais informações sobre o atributo de parâmetro, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ac135-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="ac135-118">Como declarar um parâmetro opcional</span><span class="sxs-lookup"><span data-stu-id="ac135-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="ac135-119">Defina uma propriedade pública, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ac135-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="ac135-120">Ao adicionar o atributo de parâmetro, omita o `Mandatory` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="ac135-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="ac135-121">Como declarar um parâmetro de mudança</span><span class="sxs-lookup"><span data-stu-id="ac135-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="ac135-122">Definir uma propriedade pública como tipo [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)e, em seguida, declarar o atributo de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ac135-122">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="ac135-123">Para obter mais informações sobre o atributo de parâmetro, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ac135-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="ac135-124">Como declarar um parâmetro com Aliases</span><span class="sxs-lookup"><span data-stu-id="ac135-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="ac135-125">Defina uma propriedade pública, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ac135-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="ac135-126">Adicione um atributo de Alias que lista os aliases para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ac135-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="ac135-127">Neste exemplo, três aliases são definidas para o mesmo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ac135-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="ac135-128">O alias primeiro fornece um atalho.</span><span class="sxs-lookup"><span data-stu-id="ac135-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="ac135-129">Os aliases da segundo e terceiro fornecem nomes, que pode usar para diferentes cenários.</span><span class="sxs-lookup"><span data-stu-id="ac135-129">The second and third aliases provide names you can use for different scenarios.</span></span>

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

<span data-ttu-id="ac135-130">Para obter mais informações sobre o atributo de Alias, consulte [declaração de atributo de Alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ac135-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ac135-131">Veja Também</span><span class="sxs-lookup"><span data-stu-id="ac135-131">See Also</span></span>

[<span data-ttu-id="ac135-132">System.Management.Automation.SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="ac135-132">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="ac135-133">Declaração de atributo de parâmetro</span><span class="sxs-lookup"><span data-stu-id="ac135-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="ac135-134">Declaração de atributo de alias</span><span class="sxs-lookup"><span data-stu-id="ac135-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="ac135-135">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ac135-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
