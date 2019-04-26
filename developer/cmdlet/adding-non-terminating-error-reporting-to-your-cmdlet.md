---
title: Adicionar relatórios de erros e seu Cmdlet de não terminação | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: 3741982f81efa04d8fe7ab448fba5f2fdf4b0c01
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068869"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="46ec9-102">Adding Non-Terminating Error Reporting to Your Cmdlet (Adicionar Comunicações de Erros de Não Terminação ao seu Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="46ec9-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="46ec9-103">Cmdlets podem comunicar os erros de não terminação, chamando o [System.Management.Automation.Cmdlet.WriteError][] método e continuar a funcionar no objeto de entrada ou de entrada mais objetos do pipeline.</span><span class="sxs-lookup"><span data-stu-id="46ec9-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError][] method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span>
<span data-ttu-id="46ec9-104">Esta secção explica como criar um cmdlet que relatórios de erros de não terminação de seus métodos de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="46ec9-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="46ec9-105">Para erros de não terminação (assim como erros de terminação), o cmdlet tem de passar um [System.Management.Automation.ErrorRecord][] objeto identificação do erro.</span><span class="sxs-lookup"><span data-stu-id="46ec9-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord][] object identifying the error.</span></span>
<span data-ttu-id="46ec9-106">Cada registo de erro é identificado por uma cadeia exclusiva de chamada "identificador de erro".</span><span class="sxs-lookup"><span data-stu-id="46ec9-106">Each error record is identified by a unique string called the "error identifier".</span></span>
<span data-ttu-id="46ec9-107">Para além do identificador, a categoria de cada erro especificada pelo constantes definidas por um [System.Management.Automation.ErrorCategory][] enumeração.</span><span class="sxs-lookup"><span data-stu-id="46ec9-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.ErrorCategory][] enumeration.</span></span>
<span data-ttu-id="46ec9-108">O utilizador pode ver os erros com base na sua categoria, definindo o `$ErrorView` variável à "CategoryView".</span><span class="sxs-lookup"><span data-stu-id="46ec9-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="46ec9-109">Para obter mais informações sobre os registos de erro, consulte [registos de erros do Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="46ec9-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="46ec9-110">Definir o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="46ec9-110">Defining the Cmdlet</span></span>

<span data-ttu-id="46ec9-111">A primeira etapa na criação do cmdlet é sempre o cmdlet de nomenclatura e declarar a classe do .NET que implementa o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="46ec9-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span>
<span data-ttu-id="46ec9-112">Este cmdlet obtém informações do processo, portanto, o nome de verbo escolhido aqui é "Get".</span><span class="sxs-lookup"><span data-stu-id="46ec9-112">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span>
<span data-ttu-id="46ec9-113">(Quase qualquer tipo de cmdlet que é capaz de obtenção de informações pode processar entrada da linha de comandos). Para obter mais informações sobre verbos aprovados cmdlet, consulte [nomes de verbo do Cmdlet](approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="46ec9-113">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="46ec9-114">Segue-se a definição para este cmdlet de Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="46ec9-114">The following is the definition for this Get-Proc cmdlet.</span></span>
<span data-ttu-id="46ec9-115">Detalhes desta definição recebem [criando seu primeiro Cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="46ec9-115">Details of this definition are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="46ec9-116">Definição de parâmetros</span><span class="sxs-lookup"><span data-stu-id="46ec9-116">Defining Parameters</span></span>

<span data-ttu-id="46ec9-117">Se necessário, seu cmdlet tem de definir parâmetros para o processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="46ec9-117">If necessary, your cmdlet must define parameters for processing input.</span></span>
<span data-ttu-id="46ec9-118">Este cmdlet de Get-Proc define um **nome** parâmetro conforme descrito na [adicionando parâmetros essa entrada de linha de comandos do processo](adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="46ec9-118">This Get-Proc cmdlet defines a **Name** parameter as described in [Adding Parameters that Process Command-Line Input](adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="46ec9-119">Aqui é a declaração de parâmetro para o **nome** parâmetro deste cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="46ec9-119">Here is the parameter declaration for the **Name** parameter of this Get-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

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

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="46ec9-120">Substituir os métodos de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="46ec9-120">Overriding Input Processing Methods</span></span>

<span data-ttu-id="46ec9-121">Todos os cmdlets devem substituir, pelo menos, um da entrada métodos fornecidos pela processar a [System.Management.Automation.Cmdlet][] classe.</span><span class="sxs-lookup"><span data-stu-id="46ec9-121">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet][] class.</span></span>
<span data-ttu-id="46ec9-122">Esses métodos são discutidos [criando seu primeiro Cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="46ec9-122">These methods are discussed in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="46ec9-123">O cmdlet deve processar cada registo de forma independente possível.</span><span class="sxs-lookup"><span data-stu-id="46ec9-123">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="46ec9-124">Este cmdlet de Get-Proc substitui o [System.Management.Automation.Cmdlet.ProcessRecord][] método para lidar com o **nome** o parâmetro de entrada fornecida pelo utilizador ou um script.</span><span class="sxs-lookup"><span data-stu-id="46ec9-124">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord][] method to handle the **Name** parameter for input provided by the user or a script.</span></span>
<span data-ttu-id="46ec9-125">Este método irá obter os processos para cada nome do processo de pedido ou todos os processos se não for fornecido nenhum nome.</span><span class="sxs-lookup"><span data-stu-id="46ec9-125">This method will get the processes for each requested process name or all processes if no name is provided.</span></span>
<span data-ttu-id="46ec9-126">Detalhes desta substituição recebem [criando seu primeiro Cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="46ec9-126">Details of this override are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="46ec9-127">Coisas a serem lembradas ao relatório de erros</span><span class="sxs-lookup"><span data-stu-id="46ec9-127">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="46ec9-128">O [System.Management.Automation.ErrorRecord][] de objeto que o cmdlet passa ao escrever um erro requer uma exceção em seu núcleo.</span><span class="sxs-lookup"><span data-stu-id="46ec9-128">The [System.Management.Automation.ErrorRecord][] object that the cmdlet passes when writing an error requires an exception at its core.</span></span>
<span data-ttu-id="46ec9-129">Siga as diretrizes do .NET ao determinar a exceção para utilizar.</span><span class="sxs-lookup"><span data-stu-id="46ec9-129">Follow the .NET guidelines when determining the exception to use.</span></span>
<span data-ttu-id="46ec9-130">Basicamente, se o erro semanticamente é o mesmo que uma exceção existente, o cmdlet deve utilizar ou derivar dessa exceção.</span><span class="sxs-lookup"><span data-stu-id="46ec9-130">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span>
<span data-ttu-id="46ec9-131">Caso contrário, ele deve derivar uma nova exceção ou uma hierarquia de exceção diretamente a partir da [System.Exception][] classe.</span><span class="sxs-lookup"><span data-stu-id="46ec9-131">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception][] class.</span></span>

<span data-ttu-id="46ec9-132">Durante a criação de identificadores de erro (acessados por meio da propriedade da classe ErrorRecord FullyQualifiedErrorId) tenha em atenção o seguinte.</span><span class="sxs-lookup"><span data-stu-id="46ec9-132">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="46ec9-133">Utilize cadeias de caracteres que são direcionadas para fins de diagnóstico para que quando inspecionar o identificador completamente qualificado pode determinar que o erro é e onde o erro veio.</span><span class="sxs-lookup"><span data-stu-id="46ec9-133">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="46ec9-134">Um identificador de formação correta de erro completamente qualificado pode ser da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="46ec9-134">A well formed fully qualified error identifier might be as follows.</span></span>

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

<span data-ttu-id="46ec9-135">Tenha em atenção que, no exemplo anterior, o identificador de erro (o token primeiro) designa o que é o erro e a parte restante indica de onde provém o erro.</span><span class="sxs-lookup"><span data-stu-id="46ec9-135">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="46ec9-136">Para cenários mais complexos, o identificador de erro pode ser um token de ponto separado que pode ser analisado na inspeção.</span><span class="sxs-lookup"><span data-stu-id="46ec9-136">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span>
  <span data-ttu-id="46ec9-137">Isso permite que demasiado ramificar nas partes do identificador de erro, bem como a categoria de identificador e o erro de erro.</span><span class="sxs-lookup"><span data-stu-id="46ec9-137">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="46ec9-138">O cmdlet deve atribuir os identificadores de erro específicas para diferentes caminhos de código.</span><span class="sxs-lookup"><span data-stu-id="46ec9-138">The cmdlet should assign specific error identifiers to different code paths.</span></span>
<span data-ttu-id="46ec9-139">Considere as seguintes informações para a atribuição de identificadores de erro:</span><span class="sxs-lookup"><span data-stu-id="46ec9-139">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="46ec9-140">Um identificador de erro deve permanecer constante ao longo do ciclo de vida do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="46ec9-140">An error identifier should remain constant throughout the cmdlet life cycle.</span></span>
  <span data-ttu-id="46ec9-141">Não altere a semântica de um identificador de erro entre versões de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="46ec9-141">Do not change the semantics of an error identifier between cmdlet versions.</span></span>

- <span data-ttu-id="46ec9-142">Utilize o texto para um identificador de erro que tersely corresponde ao erro está a ser comunicado.</span><span class="sxs-lookup"><span data-stu-id="46ec9-142">Use text for an error identifier that tersely corresponds to the error being reported.</span></span>
  <span data-ttu-id="46ec9-143">Não utilize espaços em branco ou pontuação.</span><span class="sxs-lookup"><span data-stu-id="46ec9-143">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="46ec9-144">Ter seu cmdlet gerar apenas os identificadores de erro que são reproduzíveis.</span><span class="sxs-lookup"><span data-stu-id="46ec9-144">Have your cmdlet generate only error identifiers that are reproducible.</span></span>
  <span data-ttu-id="46ec9-145">Por exemplo, não deve gerar um identificador que inclui um identificador de processo.</span><span class="sxs-lookup"><span data-stu-id="46ec9-145">For example, it should not generate an identifier that includes a process identifier.</span></span>
  <span data-ttu-id="46ec9-146">Identificadores de erro são úteis para um usuário apenas quando eles correspondem aos identificadores são visualizadas por outros utilizadores com o mesmo problema.</span><span class="sxs-lookup"><span data-stu-id="46ec9-146">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="46ec9-147">Exceções sem tratamento não são detetadas pelo PowerShell nas seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="46ec9-147">Unhandled exceptions are not caught by PowerShell in the following conditions:</span></span>

- <span data-ttu-id="46ec9-148">Se um cmdlet cria um novo thread e o código em execução nesse thread lança uma exceção não processada, o PowerShell não capturará o erro e encerrará o processo.</span><span class="sxs-lookup"><span data-stu-id="46ec9-148">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

- <span data-ttu-id="46ec9-149">Se um objeto tiver código em seu destruidor ou métodos Dispose que faz com que uma exceção não processada, o PowerShell não capturará o erro e encerrará o processo.</span><span class="sxs-lookup"><span data-stu-id="46ec9-149">If an object has code in its destructor or Dispose methods that causes an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="46ec9-150">Relatório de erros de não terminação</span><span class="sxs-lookup"><span data-stu-id="46ec9-150">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="46ec9-151">Qualquer um da entrada de métodos de processamento pode relatar um erro de não terminação para o fluxo de saída com o [System.Management.Automation.Cmdlet.WriteError][] método.</span><span class="sxs-lookup"><span data-stu-id="46ec9-151">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError][] method.</span></span>

<span data-ttu-id="46ec9-152">Eis um exemplo de código deste cmdlet de Get-Proc que ilustra a chamada para [System.Management.Automation.Cmdlet.WriteError][] partir em substituição do [System.Management.Automation.Cmdlet.ProcessRecord][] método.</span><span class="sxs-lookup"><span data-stu-id="46ec9-152">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError][] from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord][] method.</span></span>
<span data-ttu-id="46ec9-153">Neste caso, a chamada é executada se o cmdlet não consegue encontrar um processo para um identificador de processo especificado.</span><span class="sxs-lookup"><span data-stu-id="46ec9-153">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="46ec9-154">Coisas a serem lembrados sobre a escrita de erros de não terminação</span><span class="sxs-lookup"><span data-stu-id="46ec9-154">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="46ec9-155">Para um erro de não terminação, o cmdlet tem de gerar um identificador de erro específico para cada objeto de entrada específico.</span><span class="sxs-lookup"><span data-stu-id="46ec9-155">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="46ec9-156">Um cmdlet com frequência tem de modificar a ação de PowerShell produzida por um erro de não terminação.</span><span class="sxs-lookup"><span data-stu-id="46ec9-156">A cmdlet frequently needs to modify the PowerShell action produced by a nonterminating error.</span></span>
<span data-ttu-id="46ec9-157">Ele pode fazer isso definindo a `ErrorAction` e `ErrorVariable` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="46ec9-157">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span>
<span data-ttu-id="46ec9-158">Se definir o `ErrorAction` parâmetro, o cmdlet apresenta as opções de utilizador [System.Management.Automation.ActionPreference][], pode influenciar a ação também diretamente ao definir o `$ErrorActionPreference` variável.</span><span class="sxs-lookup"><span data-stu-id="46ec9-158">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.ActionPreference][], you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="46ec9-159">O cmdlet pode salvar a erros de não terminação numa variável usando o `ErrorVariable` parâmetro, que não é afetado pela definição de `ErrorAction`.</span><span class="sxs-lookup"><span data-stu-id="46ec9-159">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span>
<span data-ttu-id="46ec9-160">Falhas podem ser anexadas a uma variável existente do erro ao adicionar um sinal de adição (+) para a frente do nome da variável.</span><span class="sxs-lookup"><span data-stu-id="46ec9-160">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="46ec9-161">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="46ec9-161">Code Sample</span></span>

<span data-ttu-id="46ec9-162">Para o completa C# código de exemplo, consulte [exemplo de GetProcessSample04](./getprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="46ec9-162">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="46ec9-163">Definir tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="46ec9-163">Define Object Types and Formatting</span></span>

<span data-ttu-id="46ec9-164">PowerShell passa informações entre cmdlets com objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="46ec9-164">PowerShell passes information between cmdlets using .NET objects.</span></span>
<span data-ttu-id="46ec9-165">Consequentemente, um cmdlet poderá ter de definir seu próprio tipo, ou o cmdlet poderá ter de expandir um tipo existente fornecido pelo outro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="46ec9-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span>
<span data-ttu-id="46ec9-166">Para obter mais informações sobre definir novos tipos ou estendendo tipos existentes, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="46ec9-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="46ec9-167">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="46ec9-167">Building the Cmdlet</span></span>

<span data-ttu-id="46ec9-168">Depois de implementar um cmdlet, tem de registá-lo com o Windows PowerShell através de um snap-in do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46ec9-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span>
<span data-ttu-id="46ec9-169">Para obter mais informações sobre como registar os cmdlets, consulte [como registrar Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="46ec9-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="46ec9-170">O Cmdlet de teste</span><span class="sxs-lookup"><span data-stu-id="46ec9-170">Testing the Cmdlet</span></span>

<span data-ttu-id="46ec9-171">Quando seu cmdlet foi registado com o PowerShell, pode testá-lo executando-a na linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="46ec9-171">When your cmdlet has been registered with PowerShell, you can test it by running it on the command line.</span></span>
<span data-ttu-id="46ec9-172">Vamos testar o cmdlet Get-procedimento de exemplo para ver se ele relata um erro:</span><span class="sxs-lookup"><span data-stu-id="46ec9-172">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="46ec9-173">Inicie o PowerShell e utilize o cmdlet Get-Proc para obter os processos com o nome "TEST".</span><span class="sxs-lookup"><span data-stu-id="46ec9-173">Start PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

    ```powershell
    PS> get-proc -name test
    ```

<span data-ttu-id="46ec9-174">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="46ec9-174">The following output appears.</span></span>

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a><span data-ttu-id="46ec9-175">Veja Também</span><span class="sxs-lookup"><span data-stu-id="46ec9-175">See Also</span></span>

[<span data-ttu-id="46ec9-176">Adicionar parâmetros do que a entrada de Pipeline de processo</span><span class="sxs-lookup"><span data-stu-id="46ec9-176">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="46ec9-177">Adicionar parâmetros que processam a entrada da linha de comandos</span><span class="sxs-lookup"><span data-stu-id="46ec9-177">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="46ec9-178">Criando seu primeiro Cmdlet</span><span class="sxs-lookup"><span data-stu-id="46ec9-178">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="46ec9-179">Estendendo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="46ec9-179">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="46ec9-180">Como registar os Cmdlets, fornecedores e alojar aplicações</span><span class="sxs-lookup"><span data-stu-id="46ec9-180">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="46ec9-181">Referência do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="46ec9-181">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="46ec9-182">Exemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="46ec9-182">Cmdlet Samples</span></span>](./cmdlet-samples.md)

[System.Exception]: /dotnet/api/System.Exception
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
