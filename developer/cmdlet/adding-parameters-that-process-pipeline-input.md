---
title: Adicionar parâmetros que processam a entrada do Pipeline | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: def0ac2ff98575beb29c3c2a7d91a5a5c53e648e
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854987"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="55eee-102">Adding Parameters that Process Pipeline Input (Adicionar Parâmetros que Processam Entradas de Pipeline)</span><span class="sxs-lookup"><span data-stu-id="55eee-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="55eee-103">Uma fonte de entrada para um cmdlet é um objeto no pipeline que provém de um cmdlet a montante.</span><span class="sxs-lookup"><span data-stu-id="55eee-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="55eee-104">Esta secção descreve como adicionar um parâmetro para o cmdlet Get-Proc (descrito em [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)) para que o cmdlet pode processar objetos do pipeline.</span><span class="sxs-lookup"><span data-stu-id="55eee-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="55eee-105">Este cmdlet de Get-Proc utiliza um `Name` parâmetro que aceite entrada de um objeto de pipeline, obtém informações de processo a partir do computador local com base nos nomes fornecidos e, em seguida, apresenta informações sobre os processos na linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="55eee-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="55eee-106">Definir a classe Cmdlet</span><span class="sxs-lookup"><span data-stu-id="55eee-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="55eee-107">A primeira etapa na criação do cmdlet é sempre o cmdlet de nomenclatura e declarar a classe do .NET que implementa o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="55eee-107">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="55eee-108">Este cmdlet obtém informações do processo, portanto, o nome de verbo escolhido aqui é "Get".</span><span class="sxs-lookup"><span data-stu-id="55eee-108">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="55eee-109">(Quase qualquer tipo de cmdlet que é capaz de obtenção de informações pode processar entrada da linha de comandos). Para obter mais informações sobre verbos aprovados cmdlet, consulte [nomes de verbo do Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="55eee-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="55eee-110">Segue-se a definição para este cmdlet de Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="55eee-110">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="55eee-111">Detalhes desta definição recebem [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="55eee-111">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="55eee-112">Definir a entrada do Pipeline</span><span class="sxs-lookup"><span data-stu-id="55eee-112">Defining Input from the Pipeline</span></span>

<span data-ttu-id="55eee-113">Esta secção descreve como definir a entrada do pipeline para um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="55eee-113">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="55eee-114">Este cmdlet de Get-Proc define uma propriedade que representa a `Name` parâmetro, conforme descrito na [adicionando parâmetros essa entrada de linha de comandos do processo](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="55eee-114">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span> <span data-ttu-id="55eee-115">(Consulte esse tópico para obter informações gerais sobre a declaração de parâmetros.)</span><span class="sxs-lookup"><span data-stu-id="55eee-115">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="55eee-116">No entanto, quando precisa de um cmdlet processar a entrada do pipeline, tem de ter seus parâmetros vinculados a valores de entrada pelo tempo de execução do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="55eee-116">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="55eee-117">Para tal, tem de adicionar o `ValueFromPipeline` palavra-chave ou adicionar a `ValueFromPipelineByProperty` palavra-chave para o [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaração de atributo.</span><span class="sxs-lookup"><span data-stu-id="55eee-117">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="55eee-118">Especifique o `ValueFromPipeline` palavra-chave se o cmdlet acessa o objeto de entrada completado.</span><span class="sxs-lookup"><span data-stu-id="55eee-118">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="55eee-119">Especifique o `ValueFromPipelineByProperty` se o cmdlet acede a apenas uma propriedade do objeto.</span><span class="sxs-lookup"><span data-stu-id="55eee-119">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="55eee-120">Aqui é a declaração de parâmetro para o `Name` parâmetro deste cmdlet de Get-Proc que aceita entrada do pipeline.</span><span class="sxs-lookup"><span data-stu-id="55eee-120">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

<span data-ttu-id="55eee-121">Os conjuntos de declaração anterior a `ValueFromPipeline` palavra-chave para `true` para que o tempo de execução do Windows PowerShell irá vincular o parâmetro para o objeto de entrada, se o objeto é o mesmo tipo com o parâmetro ou se ele pode ser forçado para o mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="55eee-121">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="55eee-122">O `ValueFromPipelineByPropertyName` palavra-chave também está definida como `true` , para que o tempo de execução do Windows PowerShell irá verificar o objeto de entrada para um `Name` propriedade.</span><span class="sxs-lookup"><span data-stu-id="55eee-122">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="55eee-123">Se o objeto de entrada tem uma propriedade desse tipo, o tempo de execução irá vincular a `Name` parâmetro para o `Name` propriedade do objeto de entrada.</span><span class="sxs-lookup"><span data-stu-id="55eee-123">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="55eee-124">A definição do `ValueFromPipeline` palavra-chave de atributo para um parâmetro tem precedência sobre a definição para o `ValueFromPipelineByPropertyName` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="55eee-124">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="55eee-125">Substituir uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="55eee-125">Overriding an Input Processing Method</span></span>

<span data-ttu-id="55eee-126">Se for seu cmdlet para processar a entrada do pipeline, tem de substituir a entrada apropriada de métodos de processamento.</span><span class="sxs-lookup"><span data-stu-id="55eee-126">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="55eee-127">Os métodos de processamento básico de entrada são introduzidos nas [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="55eee-127">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="55eee-128">Este cmdlet de Get-Proc substitui o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para tratar a `Name` entrada de parâmetro fornecida pelo utilizador ou um script.</span><span class="sxs-lookup"><span data-stu-id="55eee-128">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="55eee-129">Este método irá obter os processos para cada nome do processo de pedido ou todos os processos se não for fornecido nenhum nome.</span><span class="sxs-lookup"><span data-stu-id="55eee-129">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="55eee-130">Repare que dentro [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), a chamada para [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) é a saída objetos do mecanismo de envio de saída no pipeline.</span><span class="sxs-lookup"><span data-stu-id="55eee-130">Notice that within [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="55eee-131">O segundo parâmetro desta chamada `enumerateCollection`, está definida como `true` para informar o tempo de execução do Windows PowerShell para enumerar a matriz de objetos de processo e escrever um processo de cada vez à linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="55eee-131">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument of this call tells
      // PowerShell to enumerate the array, and send one process at a
      // time to the pipeline.
      WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="55eee-132">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="55eee-132">Code Sample</span></span>

<span data-ttu-id="55eee-133">Para o completa C# código de exemplo, consulte [exemplo de GetProcessSample03](./getprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="55eee-133">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="55eee-134">Definir tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="55eee-134">Defining Object Types and Formatting</span></span>

<span data-ttu-id="55eee-135">Windows PowerShell passa informações entre cmdlets com objetos .net.</span><span class="sxs-lookup"><span data-stu-id="55eee-135">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="55eee-136">Consequentemente, um cmdlet poderá ter de definir seu próprio tipo, ou o cmdlet poderá ter de expandir um tipo existente fornecido pelo outro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="55eee-136">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="55eee-137">Para obter mais informações sobre definir novos tipos ou estendendo tipos existentes, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="55eee-137">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="55eee-138">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="55eee-138">Building the Cmdlet</span></span>

<span data-ttu-id="55eee-139">Após a implementação de um cmdlet tem de ser registado com o Windows PowerShell através de um snap-in do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="55eee-139">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="55eee-140">Para obter mais informações sobre como registar os cmdlets, consulte [como registrar Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="55eee-140">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="55eee-141">O Cmdlet de teste</span><span class="sxs-lookup"><span data-stu-id="55eee-141">Testing the Cmdlet</span></span>

<span data-ttu-id="55eee-142">Quando seu cmdlet foi registado com o Windows PowerShell, testá-la executando-a na linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="55eee-142">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="55eee-143">Por exemplo, teste o código para o cmdlet de exemplo.</span><span class="sxs-lookup"><span data-stu-id="55eee-143">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="55eee-144">Para obter mais informações sobre como utilizar cmdlets da linha de comando, consulte a [introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="55eee-144">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="55eee-145">No prompt do Windows PowerShell, introduza os seguintes comandos para recuperar os nomes de processo através do pipeline.</span><span class="sxs-lookup"><span data-stu-id="55eee-145">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

    ```powershell
    PS> type ProcessNames | get-proc
    ```

<span data-ttu-id="55eee-146">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="55eee-146">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- <span data-ttu-id="55eee-147">Introduza as seguintes linhas ao obter os objetos de processo que tenham um `Name` propriedade dos processos chamado "IEXPLORE".</span><span class="sxs-lookup"><span data-stu-id="55eee-147">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="55eee-148">Este exemplo utiliza o `Get-Process` cmdlet (fornecido pelo Windows PowerShell) como um comando a montante para obter os processos de "IEXPLORE".</span><span class="sxs-lookup"><span data-stu-id="55eee-148">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

    ```powershell
    PS> get-process iexplore | get-proc
    ```

<span data-ttu-id="55eee-149">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="55eee-149">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a><span data-ttu-id="55eee-150">Veja Também</span><span class="sxs-lookup"><span data-stu-id="55eee-150">See Also</span></span>

[<span data-ttu-id="55eee-151">Adicionar parâmetros que processam a entrada de linha de comandos</span><span class="sxs-lookup"><span data-stu-id="55eee-151">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="55eee-152">Criando seu primeiro Cmdlet</span><span class="sxs-lookup"><span data-stu-id="55eee-152">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="55eee-153">Estendendo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="55eee-153">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="55eee-154">Como registar os Cmdlets, fornecedores e alojar aplicações</span><span class="sxs-lookup"><span data-stu-id="55eee-154">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="55eee-155">Referência do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="55eee-155">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="55eee-156">Exemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="55eee-156">Cmdlet Samples</span></span>](./cmdlet-samples.md)
