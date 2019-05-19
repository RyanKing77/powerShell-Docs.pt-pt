---
title: Adicionar mensagens de utilizador ao seu Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: 138c6a43937e72fffaa2a09243e500e9822e6111
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854926"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="d6826-102">Adding User Messages to Your Cmdlet (Adicionar Mensagens para o Utilizador ao seu Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="d6826-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="d6826-103">Cmdlets pode gravar vários tipos de mensagens que podem ser apresentados ao utilizador pelo tempo de execução do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d6826-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="d6826-104">Essas mensagens incluem os seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="d6826-104">These messages include the following types:</span></span>

- <span data-ttu-id="d6826-105">Mensagens verbosas que contêm informações de utilizador gerais.</span><span class="sxs-lookup"><span data-stu-id="d6826-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="d6826-106">Depure mensagens que contêm informações de resolução de problemas.</span><span class="sxs-lookup"><span data-stu-id="d6826-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="d6826-107">Mensagens de aviso que contêm uma notificação que o cmdlet está prestes a realizar uma operação que pode ter resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="d6826-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="d6826-108">O cmdlet de trabalho de mensagens que contêm informações sobre a quantidade de relatório de progresso está concluída quando efetuar uma operação que demora muito tempo.</span><span class="sxs-lookup"><span data-stu-id="d6826-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="d6826-109">Não há nenhum limite para o número de mensagens que seu cmdlet pode escrever ou o tipo de mensagens que escreve seu cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d6826-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="d6826-110">Cada mensagem foi escrita por fazer uma chamada específica a partir da entrada a processar o método de seu cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d6826-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="d6826-111">Definir o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d6826-111">Defining the Cmdlet</span></span>

<span data-ttu-id="d6826-112">A primeira etapa na criação do cmdlet é sempre o cmdlet de nomenclatura e declarar a classe do .NET que implementa o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d6826-112">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="d6826-113">Qualquer tipo de cmdlet pode escrever notificações do utilizador da sua entrada processamento métodos; então, em geral, pode nomear este cmdlet com qualquer verbo que indica quais modificações de sistema que executa o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d6826-113">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="d6826-114">Para obter mais informações sobre verbos aprovados cmdlet, consulte [nomes de verbo do Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="d6826-114">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="d6826-115">O cmdlet Stop-Proc foi concebido para modificar o sistema; Por conseguinte, o [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaração para a classe do .NET tem de incluir o `SupportsShouldProcess` palavra-chave de atributo e ser definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="d6826-115">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="d6826-116">O código a seguir é a definição para esta classe de cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="d6826-116">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="d6826-117">Para obter mais informações sobre esta definição, consulte [criar um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="d6826-117">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="d6826-118">Definir parâmetros para modificação do sistema</span><span class="sxs-lookup"><span data-stu-id="d6826-118">Defining Parameters for System Modification</span></span>

<span data-ttu-id="d6826-119">O cmdlet Stop-Proc define três parâmetros: `Name`, `Force`, e `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="d6826-119">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="d6826-120">Para obter mais informações sobre como definir estes parâmetros, consulte [criar um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="d6826-120">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="d6826-121">Segue-se a declaração de parâmetro para o cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="d6826-121">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="d6826-122">Substituir uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="d6826-122">Overriding an Input Processing Method</span></span>

<span data-ttu-id="d6826-123">Seu cmdlet tem de substituir uma método de processamento de entrada, com mais frequência ficará [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="d6826-123">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="d6826-124">Este cmdlet Stop-Proc substitui o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="d6826-124">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="d6826-125">Nessa implementação do cmdlet Stop-Proc, as chamadas são feitas para escrever as mensagens verbosas, mensagens de depuração e mensagens de aviso.</span><span class="sxs-lookup"><span data-stu-id="d6826-125">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="d6826-126">Para obter mais informações sobre como esse método chama o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos, consulte [Criação de um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="d6826-126">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="d6826-127">Gravar uma mensagem detalhada</span><span class="sxs-lookup"><span data-stu-id="d6826-127">Writing a Verbose Message</span></span>

<span data-ttu-id="d6826-128">O [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método é usado para escrever informações gerais do nível de usuário que não está relacionada com as condições de erro específico.</span><span class="sxs-lookup"><span data-stu-id="d6826-128">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="d6826-129">O administrador de sistema, em seguida, pode utilizar essas informações para continuar a processar outros comandos.</span><span class="sxs-lookup"><span data-stu-id="d6826-129">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="d6826-130">Além disso, qualquer informação escrita usando esse método deve ser localizada conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="d6826-130">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="d6826-131">O código seguinte deste cmdlet Stop-Proc mostra duas chamadas para o [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método de substituição do [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.</span><span class="sxs-lookup"><span data-stu-id="d6826-131">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="d6826-132">Escrever uma mensagem de depuração</span><span class="sxs-lookup"><span data-stu-id="d6826-132">Writing a Debug Message</span></span>

<span data-ttu-id="d6826-133">O [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método é usado para escrever mensagens de depuração que podem ser utilizadas para resolver problemas relacionados com a operação do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d6826-133">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="d6826-134">A chamada é feita a partir de uma método de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="d6826-134">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="d6826-135">Windows PowerShell também define um `Debug` parâmetro que apresenta ambos verboso e informações de depuração.</span><span class="sxs-lookup"><span data-stu-id="d6826-135">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="d6826-136">Se seu cmdlet oferece suporte esse parâmetro, não é necessário chamar [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) no mesmo código que chama [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .</span><span class="sxs-lookup"><span data-stu-id="d6826-136">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="d6826-137">As duas secções seguintes de código do cmdlet Stop-Proc exemplo mostram chamadas para o [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método de substituição do [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.</span><span class="sxs-lookup"><span data-stu-id="d6826-137">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="d6826-138">Esta mensagem de depuração é gravada imediatamente antes [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) é chamado.</span><span class="sxs-lookup"><span data-stu-id="d6826-138">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="d6826-139">Esta mensagem de depuração é gravada imediatamente antes [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) é chamado.</span><span class="sxs-lookup"><span data-stu-id="d6826-139">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="d6826-140">Windows PowerShell encaminha automaticamente qualquer [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) chamadas para os cmdlets e infra-estrutura de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="d6826-140">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="d6826-141">Isso permite que as chamadas de método para ser rastreados no aplicativo de hospedagem, um arquivo ou um depurador sem ter de fazer qualquer trabalho de desenvolvimento extra dentro do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d6826-141">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="d6826-142">A seguinte entrada de linha de comando implementa uma operação de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="d6826-142">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="d6826-143">**PS > expressão de rastreio stop-proc-proc.log de ficheiro-bloco de notas do comando stop-proc**</span><span class="sxs-lookup"><span data-stu-id="d6826-143">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="d6826-144">Escrever uma mensagem de aviso</span><span class="sxs-lookup"><span data-stu-id="d6826-144">Writing a Warning Message</span></span>

<span data-ttu-id="d6826-145">O [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método é usado para escrever um aviso quando o cmdlet está prestes a realizar uma operação que poderá ter um resultado inesperado, por exemplo, substituindo um arquivo só de leitura.</span><span class="sxs-lookup"><span data-stu-id="d6826-145">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="d6826-146">O código a seguir do cmdlet Stop-Proc exemplo mostra a chamada para o [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método de substituição do [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.</span><span class="sxs-lookup"><span data-stu-id="d6826-146">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="d6826-147">Escrever uma mensagem de progresso</span><span class="sxs-lookup"><span data-stu-id="d6826-147">Writing a Progress Message</span></span>

<span data-ttu-id="d6826-148">O [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) é utilizada para escrever mensagens de progresso quando operações de cmdlet demorar mais tempo a concluir.</span><span class="sxs-lookup"><span data-stu-id="d6826-148">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="d6826-149">Uma chamada para [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passa um [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) objeto que é enviado para o aplicativo de hospedagem para a composição para o usuário.</span><span class="sxs-lookup"><span data-stu-id="d6826-149">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="d6826-150">Este cmdlet Stop-Proc não inclui uma chamada para o [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) método.</span><span class="sxs-lookup"><span data-stu-id="d6826-150">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="d6826-151">O código a seguir é um exemplo de uma mensagem de progresso, escrito por um cmdlet que está a tentar copiar um item.</span><span class="sxs-lookup"><span data-stu-id="d6826-151">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="d6826-152">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="d6826-152">Code Sample</span></span>

<span data-ttu-id="d6826-153">Para o completa C# código de exemplo, consulte [exemplo de StopProcessSample02](./stopprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d6826-153">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="d6826-154">Definir tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="d6826-154">Define Object Types and Formatting</span></span>

<span data-ttu-id="d6826-155">Windows PowerShell passa informações entre cmdlets com objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="d6826-155">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="d6826-156">Consequentemente, um cmdlet poderá ter de definir seu próprio tipo, ou o cmdlet poderá ter de expandir um tipo existente fornecido pelo outro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d6826-156">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="d6826-157">Para obter mais informações sobre definir novos tipos ou estendendo tipos existentes, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="d6826-157">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="d6826-158">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d6826-158">Building the Cmdlet</span></span>

<span data-ttu-id="d6826-159">Depois de implementar um cmdlet, tem de ser registado com o Windows PowerShell através de um snap-in do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d6826-159">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="d6826-160">Para obter mais informações sobre como registar os cmdlets, consulte [como registrar Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="d6826-160">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="d6826-161">O Cmdlet de teste</span><span class="sxs-lookup"><span data-stu-id="d6826-161">Testing the Cmdlet</span></span>

<span data-ttu-id="d6826-162">Quando seu cmdlet foi registado com o Windows PowerShell, pode testá-lo executando-a na linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="d6826-162">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="d6826-163">Vamos testar o cmdlet Stop-Proc de exemplo.</span><span class="sxs-lookup"><span data-stu-id="d6826-163">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="d6826-164">Para obter mais informações sobre como utilizar cmdlets da linha de comando, consulte a [introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="d6826-164">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="d6826-165">A seguinte entrada de linha de comandos utiliza Stop-Proc para parar o processo com o nome "Bloco de notas", fornecer notificações verbosas e imprimir informações de depuração.</span><span class="sxs-lookup"><span data-stu-id="d6826-165">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="d6826-166">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="d6826-166">The following output appears.</span></span>

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a><span data-ttu-id="d6826-167">Veja Também</span><span class="sxs-lookup"><span data-stu-id="d6826-167">See Also</span></span>

[<span data-ttu-id="d6826-168">Criar um Cmdlet que modifique o sistema</span><span class="sxs-lookup"><span data-stu-id="d6826-168">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="d6826-169">Como criar um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6826-169">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="d6826-170">Estendendo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="d6826-170">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="d6826-171">Como registar os Cmdlets, fornecedores e alojar aplicações</span><span class="sxs-lookup"><span data-stu-id="d6826-171">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="d6826-172">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6826-172">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
