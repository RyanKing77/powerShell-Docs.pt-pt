---
title: Adicionar parâmetro define como um Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: b02a2e0d4b0a27c261b0bc05febda7826ad5276e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849099"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="891df-102">Adding Parameter Sets to a Cmdlet (Adicionar Conjuntos de Parâmetros a um Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="891df-102">Adding Parameter Sets to a Cmdlet</span></span>

<span data-ttu-id="891df-103">Esta secção descreve como adicionar o parâmetro define como o cmdlet Stop-Proc (descrito em [criar um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="891df-103">This section describes how to add parameter sets to the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span> <span data-ttu-id="891df-104">Assim como os outros cmdlets de Stop-Proc descritos no Guia do programador, esta, este cmdlet tenta parar os processos que são obtidos com o cmdlet Get-Proc (descrito em [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="891df-104">Similar to the other Stop-Proc cmdlets described in this Programmer's Guide, this cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="891df-105">Os tópicos nesta secção incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="891df-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="891df-106">Que precisa saber sobre conjuntos de parâmetros</span><span class="sxs-lookup"><span data-stu-id="891df-106">Things to Know About Parameter Sets</span></span>](#Adding-Parameter-Sets-to-a-Cmdlet)

- [<span data-ttu-id="891df-107">Declarar a classe Cmdlet</span><span class="sxs-lookup"><span data-stu-id="891df-107">Declaring the Cmdlet Class</span></span>](#Declaring-the-Cmdlet-Class)

- [<span data-ttu-id="891df-108">Declarar os parâmetros do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="891df-108">Declaring the Parameters of the Cmdlet</span></span>](#Declaring-the-Parameters-of-the-Cmdlet)

- [<span data-ttu-id="891df-109">Substituir uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="891df-109">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="891df-110">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="891df-110">Code Sample</span></span>](#Declaring-the-Parameters-of-the-Cmdlet)

- [<span data-ttu-id="891df-111">Definir tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="891df-111">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="891df-112">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="891df-112">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="891df-113">O Cmdlet de teste</span><span class="sxs-lookup"><span data-stu-id="891df-113">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="891df-114">Que precisa saber sobre conjuntos de parâmetros</span><span class="sxs-lookup"><span data-stu-id="891df-114">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="891df-115">Windows PowerShell define um parâmetro definido como um grupo de parâmetros que funcionam em conjunto.</span><span class="sxs-lookup"><span data-stu-id="891df-115">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="891df-116">Ao agrupar os parâmetros de um cmdlet, pode criar um único cmdlet que pode alterar a sua funcionalidade com base no que grupo de parâmetros que o utilizador Especifica.</span><span class="sxs-lookup"><span data-stu-id="891df-116">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="891df-117">Um exemplo de um cmdlet que usa dois conjuntos de parâmetros para definir funcionalidades diferentes é o `Get-EventLog` cmdlet fornecido pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="891df-117">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="891df-118">Este cmdlet retorna informações distintas quando o utilizador Especifica os `List` ou `LogName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="891df-118">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="891df-119">Se o `LogName` parâmetro for especificado, o cmdlet retorna informações sobre os eventos em determinado log de eventos.</span><span class="sxs-lookup"><span data-stu-id="891df-119">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="891df-120">Se o `List` parâmetro for especificado, o cmdlet devolve informações sobre o registo de ficheiros propriamente ditos (não as informações de eventos contêm).</span><span class="sxs-lookup"><span data-stu-id="891df-120">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="891df-121">Neste caso, o `List` e `LogName` parâmetros identificam dois conjuntos de parâmetros separados.</span><span class="sxs-lookup"><span data-stu-id="891df-121">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="891df-122">Dois pontos importantes a serem lembrados sobre conjuntos de parâmetros é que o tempo de execução do Windows PowerShell utiliza apenas um parâmetro definido para uma determinada entrada, e que cada conjunto de parâmetros têm de ter, pelo menos, um parâmetro que é exclusiva para esse conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="891df-122">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="891df-123">Para ilustrar esse último ponto, este cmdlet Stop-Proc utiliza três conjuntos de parâmetros: `ProcessName`, `ProcessId`, e `InputObject`.</span><span class="sxs-lookup"><span data-stu-id="891df-123">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="891df-124">Cada um desses conjuntos de parâmetros tem um parâmetro que não esteja em outros conjuntos de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="891df-124">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="891df-125">Os conjuntos de parâmetros podem partilhar os outros parâmetros, mas o cmdlet utiliza os parâmetros exclusivos `ProcessName`, `ProcessId`, e `InputObject` para identificar qual conjunto de parâmetros que o tempo de execução do Windows PowerShell deve utilizar.</span><span class="sxs-lookup"><span data-stu-id="891df-125">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="891df-126">Declarar a classe Cmdlet</span><span class="sxs-lookup"><span data-stu-id="891df-126">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="891df-127">A primeira etapa na criação do cmdlet é sempre o cmdlet de nomenclatura e declarar a classe do .NET que implementa o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="891df-127">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="891df-128">Para este cmdlet, o verbo do ciclo de vida "Stop" é utilizado porque o cmdlet interrompe processos do sistema.</span><span class="sxs-lookup"><span data-stu-id="891df-128">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="891df-129">O nome do substantivo "Proc" é utilizado porque o cmdlet funciona em processos.</span><span class="sxs-lookup"><span data-stu-id="891df-129">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="891df-130">Na declaração abaixo, tenha em atenção que o nome de verbo e substantivo do cmdlet são refletidas no nome da classe de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="891df-130">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="891df-131">Para obter mais informações sobre nomes de verbo do cmdlet aprovados, consulte [nomes de verbo do Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="891df-131">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="891df-132">O código a seguir é a definição de classe para este cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="891df-132">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="891df-133">Declarar os parâmetros do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="891df-133">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="891df-134">Este cmdlet define três parâmetros necessários como entrada para o cmdlet (esses parâmetros também definem os conjuntos de parâmetros), bem como um `Force` parâmetro que gere o que o cmdlet faz e um `PassThru` parâmetro que determina se o cmdlet envia um objeto de saída através do pipeline.</span><span class="sxs-lookup"><span data-stu-id="891df-134">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="891df-135">Por predefinição, este cmdlet não é transmitido um objeto através do pipeline.</span><span class="sxs-lookup"><span data-stu-id="891df-135">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="891df-136">Para obter mais informações sobre estes dois últimos parâmetros, consulte [criar um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="891df-136">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="891df-137">Declarando o parâmetro de nome</span><span class="sxs-lookup"><span data-stu-id="891df-137">Declaring the Name Parameter</span></span>

<span data-ttu-id="891df-138">Este parâmetro de entrada permite ao utilizador especificar os nomes dos processos de ser parado.</span><span class="sxs-lookup"><span data-stu-id="891df-138">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="891df-139">Tenha em atenção que o `ParameterSetName` atributo palavra-chave do [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributo especifica o `ProcessName` parâmetro definido para este parâmetro.</span><span class="sxs-lookup"><span data-stu-id="891df-139">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

<span data-ttu-id="891df-140">Observe também que o alias "ProcessName" é fornecido para este parâmetro.</span><span class="sxs-lookup"><span data-stu-id="891df-140">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="891df-141">Declarando o parâmetro de Id</span><span class="sxs-lookup"><span data-stu-id="891df-141">Declaring the Id Parameter</span></span>

<span data-ttu-id="891df-142">Este parâmetro de entrada permite ao utilizador especificar os identificadores dos processos de ser parado.</span><span class="sxs-lookup"><span data-stu-id="891df-142">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="891df-143">Tenha em atenção que o `ParameterSetName` palavra-chave de atributo a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributo especifica o `ProcessId` conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="891df-143">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

<span data-ttu-id="891df-144">Observe também que o alias "ProcessId" é fornecido para este parâmetro.</span><span class="sxs-lookup"><span data-stu-id="891df-144">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="891df-145">Declarando o parâmetro InputObject</span><span class="sxs-lookup"><span data-stu-id="891df-145">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="891df-146">Este parâmetro de entrada permite ao utilizador especificar um objeto de entrada que contém informações sobre os processos de ser parado.</span><span class="sxs-lookup"><span data-stu-id="891df-146">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="891df-147">Tenha em atenção que o `ParameterSetName` atributo palavra-chave do [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributo especifica o `InputObject` parâmetro definido para este parâmetro.</span><span class="sxs-lookup"><span data-stu-id="891df-147">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

<span data-ttu-id="891df-148">Observe também que este parâmetro não tem nenhum alias.</span><span class="sxs-lookup"><span data-stu-id="891df-148">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="891df-149">Declarando parâmetros em vários conjuntos de parâmetros</span><span class="sxs-lookup"><span data-stu-id="891df-149">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="891df-150">Embora tem de existir um parâmetro exclusivo para cada conjunto de parâmetros, os parâmetros podem pertencer a mais do que um conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="891df-150">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="891df-151">Nestes casos, fornecer o parâmetro partilhado um [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaração de atributo para cada conjunto a que o parâmetro de pertence.</span><span class="sxs-lookup"><span data-stu-id="891df-151">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="891df-152">Se for um parâmetro em todos os conjuntos de parâmetros, só tem de declarar o atributo de parâmetro de uma vez e não é necessário especificar que o parâmetro de nome do conjunto.</span><span class="sxs-lookup"><span data-stu-id="891df-152">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="891df-153">Substituir uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="891df-153">Overriding an Input Processing Method</span></span>

<span data-ttu-id="891df-154">Cada cmdlet tem de substituir uma método de processamento de entrada, mais freqüentemente, isso será o [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.</span><span class="sxs-lookup"><span data-stu-id="891df-154">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="891df-155">Neste cmdlet, o [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método é substituído para que o cmdlet pode processar qualquer número de processos.</span><span class="sxs-lookup"><span data-stu-id="891df-155">In this cmdlet, the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="891df-156">Ela contém uma instrução Select que chama um método diferente com base no conjunto de parâmetros que o utilizador especificado.</span><span class="sxs-lookup"><span data-stu-id="891df-156">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

<span data-ttu-id="891df-157">Métodos auxiliares chamados pela instrução Select não são descritos aqui, mas pode ver a sua implementação no exemplo de código completo, na secção seguinte.</span><span class="sxs-lookup"><span data-stu-id="891df-157">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="891df-158">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="891df-158">Code Sample</span></span>

<span data-ttu-id="891df-159">Para o completa C# código de exemplo, consulte [exemplo de StopProcessSample04](./stopprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="891df-159">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="891df-160">Definir tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="891df-160">Defining Object Types and Formatting</span></span>

<span data-ttu-id="891df-161">Windows PowerShell passa informações entre cmdlets com objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="891df-161">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="891df-162">Consequentemente, um cmdlet poderá ter de definir seu próprio tipo, ou o cmdlet poderá ter de expandir um tipo existente fornecido pelo outro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="891df-162">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="891df-163">Para obter mais informações sobre definir novos tipos ou estendendo tipos existentes, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="891df-163">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="891df-164">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="891df-164">Building the Cmdlet</span></span>

<span data-ttu-id="891df-165">Depois de implementar um cmdlet, tem de registá-lo com o Windows PowerShell através de um snap-in do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="891df-165">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="891df-166">Para obter mais informações sobre como registar os cmdlets, consulte [como registrar Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="891df-166">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="891df-167">O Cmdlet de teste</span><span class="sxs-lookup"><span data-stu-id="891df-167">Testing the Cmdlet</span></span>

<span data-ttu-id="891df-168">Quando seu cmdlet foi registado com o Windows PowerShell, testá-la executando-a na linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="891df-168">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="891df-169">Aqui estão alguns testes que mostram como o `ProcessId` e `InputObject` parâmetros podem ser utilizados para testar seus conjuntos de parâmetros para interromper um processo.</span><span class="sxs-lookup"><span data-stu-id="891df-169">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="891df-170">Com o PowerShell do Windows iniciado, execute o cmdlet Stop-Proc com o `ProcessId` parâmetro definido para parar um processo com base no respetivo identificador.</span><span class="sxs-lookup"><span data-stu-id="891df-170">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="891df-171">Neste caso, o cmdlet está a utilizar o `ProcessId` parâmetro definido para parar o processo.</span><span class="sxs-lookup"><span data-stu-id="891df-171">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="891df-172">Com o PowerShell do Windows iniciado, execute o cmdlet Stop-Proc com o `InputObject` parâmetro definido como para parar os processos no objeto obtido pelo bloco de notas a `Get-Process` comando.</span><span class="sxs-lookup"><span data-stu-id="891df-172">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="891df-173">Veja Também</span><span class="sxs-lookup"><span data-stu-id="891df-173">See Also</span></span>

[<span data-ttu-id="891df-174">Criar um Cmdlet que modifica o sistema</span><span class="sxs-lookup"><span data-stu-id="891df-174">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="891df-175">Como criar um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="891df-175">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="891df-176">Estendendo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="891df-176">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="891df-177">Como registar os Cmdlets, fornecedores e alojar aplicações</span><span class="sxs-lookup"><span data-stu-id="891df-177">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="891df-178">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="891df-178">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
