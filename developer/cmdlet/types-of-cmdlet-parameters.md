---
title: Tipos de parâmetros de Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067200"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="903d7-102">Types of Cmdlet Parameters (Tipos de Parâmetros de Cmdlets)</span><span class="sxs-lookup"><span data-stu-id="903d7-102">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="903d7-103">Este tópico descreve os diferentes tipos de parâmetros que pode declarar nos cmdlets.</span><span class="sxs-lookup"><span data-stu-id="903d7-103">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="903d7-104">Parâmetros do cmdlet podem ser posicional, com nome, obrigatória, opcional ou parâmetros.</span><span class="sxs-lookup"><span data-stu-id="903d7-104">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="903d7-105">Parâmetros posicionais e com nome</span><span class="sxs-lookup"><span data-stu-id="903d7-105">Positional and Named Parameters</span></span>

<span data-ttu-id="903d7-106">Todos os parâmetros de cmdlet são parâmetros nomeados ou posicionais.</span><span class="sxs-lookup"><span data-stu-id="903d7-106">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="903d7-107">Um parâmetro nomeado exige que digite o nome do parâmetro e o argumento ao chamar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="903d7-107">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="903d7-108">Um parâmetro posicional requer apenas que digite os argumentos por ordem relativa.</span><span class="sxs-lookup"><span data-stu-id="903d7-108">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="903d7-109">O sistema mapeia, em seguida, o primeiro argumento sem nome para o primeiro parâmetro posicional.</span><span class="sxs-lookup"><span data-stu-id="903d7-109">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="903d7-110">O sistema mapeia o segundo argumento sem nome para o segundo parâmetro sem nome e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="903d7-110">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="903d7-111">Por predefinição, todos os parâmetros de cmdlet são nomeados parâmetros.</span><span class="sxs-lookup"><span data-stu-id="903d7-111">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="903d7-112">Para definir um parâmetro nomeado, omita o `Position` palavra-chave no **parâmetro** atributo declaração, conforme mostrado na seguinte declaração de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="903d7-112">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="903d7-113">Para definir um parâmetro posicional, adicione o `Position` palavra-chave no parâmetro declaração de atributo e, em seguida, especifique uma posição.</span><span class="sxs-lookup"><span data-stu-id="903d7-113">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="903d7-114">No exemplo a seguir, o `UserName` parâmetro está declarado como um parâmetro posicional com posição 0.</span><span class="sxs-lookup"><span data-stu-id="903d7-114">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="903d7-115">Isso significa que o primeiro argumento da chamada será vinculado automaticamente para este parâmetro.</span><span class="sxs-lookup"><span data-stu-id="903d7-115">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> <span data-ttu-id="903d7-116">Design de cmdlet boas recomenda que os parâmetros utilizados por mais ser declarada como parâmetros posicionais, para que o utilizador não tem de introduzir o nome do parâmetro, quando o cmdlet é executado.</span><span class="sxs-lookup"><span data-stu-id="903d7-116">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="903d7-117">Parâmetros nomeados e posicionais aceitam argumentos únicos ou vários argumentos separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="903d7-117">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="903d7-118">São permitidos vários argumentos apenas se o parâmetro aceita uma coleção, como uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="903d7-118">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="903d7-119">Pode misturar os parâmetros posicionais e com nome no mesmo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="903d7-119">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="903d7-120">Neste caso, o sistema recupera os argumentos nomeados primeiro e, em seguida, tenta mapear o restante sem nome argumentos para os parâmetros posicionais.</span><span class="sxs-lookup"><span data-stu-id="903d7-120">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="903d7-121">Os comandos seguintes mostram as diferentes formas em que pode especificar único e vários argumentos para os parâmetros do `Get-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="903d7-121">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="903d7-122">Tenha em atenção que nos dois últimos exemplos **-name** não precisa de ser especificado porque o `Name` parâmetro é definido como um parâmetro posicional.</span><span class="sxs-lookup"><span data-stu-id="903d7-122">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="903d7-123">Parâmetros obrigatórios e opcionais</span><span class="sxs-lookup"><span data-stu-id="903d7-123">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="903d7-124">Também pode definir parâmetros do cmdlet como parâmetros obrigatórios ou opcionais.</span><span class="sxs-lookup"><span data-stu-id="903d7-124">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="903d7-125">(Deve ser especificado um parâmetro obrigatório antes do tempo de execução do Windows PowerShell invoca o cmdlet.)  Por predefinição, os parâmetros são definidos como opcionais.</span><span class="sxs-lookup"><span data-stu-id="903d7-125">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="903d7-126">Para definir um parâmetro obrigatório, adicione a `Mandatory` palavra-chave no parâmetro declaração de atributo e defini-lo como `true`, conforme mostrado na seguinte declaração de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="903d7-126">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="903d7-127">Para definir um parâmetro opcional, omita o `Mandatory` palavra-chave no **parâmetro** atributo declaração, conforme mostrado na seguinte declaração de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="903d7-127">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="903d7-128">Parâmetros de comutador</span><span class="sxs-lookup"><span data-stu-id="903d7-128">Switch Parameters</span></span>

<span data-ttu-id="903d7-129">Windows PowerShell fornece uma [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) tipo que permite-lhe definir um parâmetro cujo valor é automaticamente definido como `false` se o parâmetro não for especificado, quando o cmdlet é chamado.</span><span class="sxs-lookup"><span data-stu-id="903d7-129">Windows PowerShell provides a [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="903d7-130">Sempre que possível, use parâmetros em vez dos parâmetros booleanos.</span><span class="sxs-lookup"><span data-stu-id="903d7-130">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="903d7-131">Considere o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="903d7-131">Consider the following sample.</span></span> <span data-ttu-id="903d7-132">Por predefinição, vários cmdlets do Windows PowerShell não passar um objeto de saída pelo pipeline.</span><span class="sxs-lookup"><span data-stu-id="903d7-132">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="903d7-133">No entanto, estes cmdlets têm um `PassThru` mudar o parâmetro que substitui o comportamento predefinido.</span><span class="sxs-lookup"><span data-stu-id="903d7-133">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="903d7-134">Se o `PassThru` parâmetro for especificado, quando estes cmdlets são chamados, o cmdlet retorna um objeto de saída no pipeline.</span><span class="sxs-lookup"><span data-stu-id="903d7-134">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="903d7-135">Se é necessário o parâmetro tenha um valor padrão de `true` quando o parâmetro não for especificado na chamada, considere revertendo o sentido do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="903d7-135">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="903d7-136">Para obter exemplo, em vez de definir o atributo de parâmetro para um valor booleano `true`, declare a propriedade como o [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) escreva e, em seguida, defina o valor predefinido do parâmetro como `false`.</span><span class="sxs-lookup"><span data-stu-id="903d7-136">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="903d7-137">Para definir um parâmetro de mudança, declarar a propriedade como o [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) escreve, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="903d7-137">To define a switch parameter, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="903d7-138">Para tornar o cmdlet agir sobre o parâmetro quando é especificado, utilize a seguinte estrutura dentro da entrada de métodos de processamento.</span><span class="sxs-lookup"><span data-stu-id="903d7-138">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a><span data-ttu-id="903d7-139">Veja Também</span><span class="sxs-lookup"><span data-stu-id="903d7-139">See Also</span></span>

[<span data-ttu-id="903d7-140">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="903d7-140">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
