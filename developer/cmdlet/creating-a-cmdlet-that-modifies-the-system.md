---
title: Criar um Cmdlet que modifica o sistema | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.assetid: 59be4120-1700-4d92-a308-ef4a32ccf11a
caps.latest.revision: 8
ms.openlocfilehash: bbe9f0213754d1cc47e0fd9a7a898bde916c0636
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055143"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="df328-102">Creating a Cmdlet that Modifies the System (Criar um Cmdlet que Modifica o Sistema)</span><span class="sxs-lookup"><span data-stu-id="df328-102">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="df328-103">Por vezes, um cmdlet tem de modificar o estado de execução do sistema, não apenas o estado do tempo de execução do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df328-103">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="df328-104">Nestes casos, o cmdlet deve permitir ao utilizador uma oportunidade para confirmar se deve ou não efetue a alteração.</span><span class="sxs-lookup"><span data-stu-id="df328-104">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="df328-105">Para oferecer suporte a confirmação de um cmdlet tem de fazer duas coisas.</span><span class="sxs-lookup"><span data-stu-id="df328-105">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="df328-106">Declarar que o cmdlet oferece suporte a confirmação quando especificar a [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atributo ao definir a palavra-chave SupportsShouldProcess como `true`.</span><span class="sxs-lookup"><span data-stu-id="df328-106">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="df328-107">Chamar [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) durante a execução do cmdlet (conforme mostrado no exemplo a seguir).</span><span class="sxs-lookup"><span data-stu-id="df328-107">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="df328-108">Ao suportar confirmação, expõe um cmdlet do `Confirm` e `WhatIf` parâmetros que são fornecidos pelo Windows PowerShell e também cumpre as diretrizes de desenvolvimento para os cmdlets (para obter mais informações sobre as diretrizes de desenvolvimento do cmdlet, consulte [ Diretrizes de desenvolvimento do cmdlet](./cmdlet-development-guidelines.md).).</span><span class="sxs-lookup"><span data-stu-id="df328-108">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="df328-109">Alterar o sistema</span><span class="sxs-lookup"><span data-stu-id="df328-109">Changing the System</span></span>

<span data-ttu-id="df328-110">O ato de "alterar o sistema" refere-se para qualquer cmdlet que potencialmente altera o estado do sistema fora do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df328-110">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="df328-111">Por exemplo, a parar um processo, ativar ou desativar uma conta de utilizador ou adicionar uma linha a uma tabela de base de dados são todas as alterações ao sistema que deve ser confirmada.</span><span class="sxs-lookup"><span data-stu-id="df328-111">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span> <span data-ttu-id="df328-112">Por outro lado, operações que leu os dados ou estabelecer ligações transitórias não altere o sistema e geralmente não necessitam de confirmação.</span><span class="sxs-lookup"><span data-stu-id="df328-112">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="df328-113">Confirmação também não é necessária para ações cujo efeito é limitado para dentro do runtime do Windows PowerShell, tal como `set-variable`.</span><span class="sxs-lookup"><span data-stu-id="df328-113">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="df328-114">Cmdlets que podem ou não pode fazer uma alteração persistente devem declarar `SupportsShouldProcess` e chamar [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) apenas se estiverem prestes a efetuar uma alteração persistente.</span><span class="sxs-lookup"><span data-stu-id="df328-114">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="df328-115">Confirmação de ShouldProcess aplica-se apenas aos cmdlets.</span><span class="sxs-lookup"><span data-stu-id="df328-115">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="df328-116">Se um comando ou script modifica o estado de execução de um sistema chamando diretamente as propriedades ou métodos do .NET, ou por chamada aplicações fora do Windows PowerShell, essa forma de confirmação não estará disponível.</span><span class="sxs-lookup"><span data-stu-id="df328-116">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="df328-117">O StopProc Cmdlet</span><span class="sxs-lookup"><span data-stu-id="df328-117">The StopProc Cmdlet</span></span>

<span data-ttu-id="df328-118">Este tópico descreve um cmdlet Stop-Proc que tenta parar os processos que são obtidos com o cmdlet Get-Proc (descrito em [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="df328-118">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="df328-119">Os tópicos nesta secção incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="df328-119">Topics in this section include the following:</span></span>

- [<span data-ttu-id="df328-120">Definir o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="df328-120">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="df328-121">Definir parâmetros para modificação do sistema</span><span class="sxs-lookup"><span data-stu-id="df328-121">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="df328-122">Substituir uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="df328-122">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="df328-123">Chamando o método ShouldProcess.</span><span class="sxs-lookup"><span data-stu-id="df328-123">Calling the ShouldProcess Method</span></span>](#Calling-the-ShouldProcess-Method)

- [<span data-ttu-id="df328-124">Chamando o método de ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="df328-124">Calling the ShouldContinue Method</span></span>](#Calling-the-ShouldContinue-Method)

- [<span data-ttu-id="df328-125">A parar processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="df328-125">Stopping Input Processing</span></span>](#Stopping-Input-Processing)

- [<span data-ttu-id="df328-126">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="df328-126">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="df328-127">Definir tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="df328-127">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="df328-128">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="df328-128">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="df328-129">O Cmdlet de teste</span><span class="sxs-lookup"><span data-stu-id="df328-129">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="df328-130">Definir o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="df328-130">Defining the Cmdlet</span></span>

<span data-ttu-id="df328-131">A primeira etapa na criação do cmdlet é sempre o cmdlet de nomenclatura e declarar a classe do .NET que implementa o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="df328-131">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="df328-132">Uma vez que esteja escrevendo um cmdlet para alterar o sistema, deve ser nomeado em conformidade.</span><span class="sxs-lookup"><span data-stu-id="df328-132">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="df328-133">Este cmdlet deixar de processos do sistema, portanto, o nome de verbo escolhido aqui é "Parar", definido pela [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) classe, com o substantivo "Procedimento" para indicar que o cmdlet interrompe processos.</span><span class="sxs-lookup"><span data-stu-id="df328-133">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="df328-134">Para obter mais informações sobre verbos aprovados cmdlet, consulte [nomes de verbo do Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="df328-134">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="df328-135">Segue-se a definição de classe para este cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="df328-135">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="df328-136">Tenha em atenção que, na [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaração, o `SupportsShouldProcess` palavra-chave do atributo está definido como `true` para ativar o cmdlet fazer chamadas para [ System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="df328-136">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="df328-137">Sem este conjunto de palavra-chave, o `Confirm` e `WhatIf` parâmetros não estarão disponíveis ao usuário.</span><span class="sxs-lookup"><span data-stu-id="df328-137">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="df328-138">Ações extremamente destrutivas</span><span class="sxs-lookup"><span data-stu-id="df328-138">Extremely Destructive Actions</span></span>

<span data-ttu-id="df328-139">Algumas operações são extremamente destrutivas, tais como reformatação uma partição de disco de rígido Active Directory.</span><span class="sxs-lookup"><span data-stu-id="df328-139">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="df328-140">Nestes casos, deve definir o cmdlet `ConfirmImpact`  =  `ConfirmImpact.High` ao declarar o [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atributo.</span><span class="sxs-lookup"><span data-stu-id="df328-140">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="df328-141">Esta definição força o cmdlet a confirmação do utilizador pedido, mesmo quando o usuário não especificou o `Confirm` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="df328-141">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="df328-142">No entanto, os desenvolvedores de cmdlet devem evitar o excesso `ConfirmImpact` para operações que são apenas potencialmente destrutivas, como eliminar uma conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="df328-142">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="df328-143">Lembre-se de que, se `ConfirmImpact` está definido como [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).</span><span class="sxs-lookup"><span data-stu-id="df328-143">Remember that if `ConfirmImpact` is set to [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).</span></span>

<span data-ttu-id="df328-144">Da mesma forma, algumas operações são provavelmente não destrutiva, embora eles teoricamente modificar o estado de execução de um sistema fora do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df328-144">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="df328-145">Pode definir esses cmdlets `ConfirmImpact` para [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="df328-145">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span></span> <span data-ttu-id="df328-146">Isto irá ignorar pedidos de confirmação em que o utilizador recebe o pedido para confirmar a operações apenas impacto médio e alto impacto.</span><span class="sxs-lookup"><span data-stu-id="df328-146">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="df328-147">Definir parâmetros para modificação do sistema</span><span class="sxs-lookup"><span data-stu-id="df328-147">Defining Parameters for System Modification</span></span>

<span data-ttu-id="df328-148">Esta secção descreve como definir os parâmetros do cmdlet, incluindo os que são necessários para a modificação do sistema de suporte.</span><span class="sxs-lookup"><span data-stu-id="df328-148">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="df328-149">Ver [adicionando parâmetros essa entrada de linha de comandos do processo](./adding-parameters-that-process-command-line-input.md) se precisar de informações gerais sobre a definição de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="df328-149">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="df328-150">O cmdlet Stop-Proc define três parâmetros: `Name`, `Force`, e `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="df328-150">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="df328-151">O `Name` parâmetro corresponde ao `Name` propriedade do objeto de entrada do processo.</span><span class="sxs-lookup"><span data-stu-id="df328-151">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="df328-152">Tenha em atenção que o `Name` este exemplo é o parâmetro obrigatório, como o cmdlet irá falhar se não tiver um processo com o nome para parar.</span><span class="sxs-lookup"><span data-stu-id="df328-152">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="df328-153">O `Force` parâmetro permite que o usuário substitui as chamadas ao [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="df328-153">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="df328-154">Na verdade, qualquer cmdlet que chama [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) deve ter um `Force` parâmetro, de modo que quando `Force` for especificado, o cmdlet ignora a chamada para [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) e prossegue com a operação.</span><span class="sxs-lookup"><span data-stu-id="df328-154">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="df328-155">Lembre-se de que isso não afeta chamadas para [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span><span class="sxs-lookup"><span data-stu-id="df328-155">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="df328-156">O `PassThru` parâmetro permite que o utilizador indicar se o cmdlet passa um objeto de saída através do pipeline, neste caso, depois de um processo é parado.</span><span class="sxs-lookup"><span data-stu-id="df328-156">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="df328-157">Lembre-se de que este parâmetro está ligado ao cmdlet em si em vez da uma propriedade do objeto de entrada.</span><span class="sxs-lookup"><span data-stu-id="df328-157">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="df328-158">Segue-se a declaração de parâmetro para o cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="df328-158">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="df328-159">Substituir uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="df328-159">Overriding an Input Processing Method</span></span>

<span data-ttu-id="df328-160">O cmdlet tem de substituir uma método de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="df328-160">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="df328-161">O código a seguir ilustra o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) utilizada no cmdlet Stop-Proc exemplo de substituição.</span><span class="sxs-lookup"><span data-stu-id="df328-161">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="df328-162">Para cada pedido o nome do processo, esse método garante que o processo não é um processo especial, tenta parar o processo e, em seguida, envia um objeto de saída, se o `PassThru` parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="df328-162">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  foreach (string name in processNames)
  {
    // For every process name passed to the cmdlet, get the associated
    // process(es). For failures, write a non-terminating error
    Process[] processes;

    try
    {
      processes = Process.GetProcessesByName(name);
    }
    catch (InvalidOperationException ioe)
    {
      WriteError(new ErrorRecord(ioe,"Unable to access the target process by name",
                 ErrorCategory.InvalidOperation, name));
      continue;
    }

    // Try to stop the process(es) that have been retrieved for a name
    foreach (Process process in processes)
    {
      string processName;

      try
      {
        processName = process.ProcessName;
      }

      catch (Win32Exception e)
        {
          WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                     ErrorCategory.ReadError, process));
          continue;
        }

        // Call Should Process to confirm the operation first.
        // This is always false if WhatIf is set.
        if (!ShouldProcess(string.Format("{0} ({1})", processName,
                           process.Id)))
        {
          continue;
        }
        // Call ShouldContinue to make sure the user really does want
        // to stop a critical process that could possibly stop the computer.
        bool criticalProcess =
             criticalProcessNames.Contains(processName.ToLower());

        if (criticalProcess &&!force)
        {
          string message = String.Format
                ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                processName);

          // It is possible that ProcessRecord is called multiple times
          // when the Name parameter receives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across multiple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (criticalProcess...
        // Stop the named process.
        try
        {
          process.Kill();
        }
        catch (Exception e)
        {
          if ((e is Win32Exception) || (e is SystemException) ||
              (e is InvalidOperationException))
          {
            // This process could not be stopped so write
            // a non-terminating error.
            string message = String.Format("{0} {1} {2}",
                             "Could not stop process \"", processName,
                             "\".");
            WriteError(new ErrorRecord(e, message,
                       ErrorCategory.CloseError, process));
                       continue;
          } // if ((e is...
          else throw;
        } // catch

        // If the PassThru parameter argument is
        // True, pass the terminated process on.
        if (passThru)
        {
          WriteObject(process);
        }
    } // foreach (Process...
  } // foreach (string...
} // ProcessRecord
```

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="df328-163">Chamando o método ShouldProcess.</span><span class="sxs-lookup"><span data-stu-id="df328-163">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="df328-164">A entrada a processar o método de seu cmdlet deve chamar o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método para confirmar a execução de uma operação antes de uma alteração (por exemplo, ao eliminar ficheiros) é feita para o estado de execução do sistema.</span><span class="sxs-lookup"><span data-stu-id="df328-164">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="df328-165">Isso permite que o tempo de execução do Windows PowerShell fornecer o comportamento correto de "WhatIf" e "Confirmar" dentro do shell.</span><span class="sxs-lookup"><span data-stu-id="df328-165">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="df328-166">Se um cmdlet afirma que ele oferece suporte deve processar e não conseguir fazer a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamar, o utilizador pode modificar o sistema inesperadamente.</span><span class="sxs-lookup"><span data-stu-id="df328-166">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="df328-167">A chamada para [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) envia o nome do recurso a ser alterados ao usuário, com o tempo de execução do Windows PowerShell tendo em conta as definições da linha de comandos ou variáveis de preferência determinar o que deverá ser apresentado ao utilizador.</span><span class="sxs-lookup"><span data-stu-id="df328-167">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="df328-168">O exemplo seguinte mostra a chamada para [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) de substituição do [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método na amostra Cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="df328-168">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="df328-169">Chamando o método de ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="df328-169">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="df328-170">A chamada para o [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método envia uma mensagem de secundária para o utilizador.</span><span class="sxs-lookup"><span data-stu-id="df328-170">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="df328-171">Esta chamada é feita após a chamada para [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) devolve `true` e, se o `Force` parâmetro não foi definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="df328-171">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="df328-172">O utilizador, em seguida, pode fornecer comentários para dizer se a operação deve ser contínuo.</span><span class="sxs-lookup"><span data-stu-id="df328-172">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="df328-173">As chamadas de cmdlet [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) como uma verificação adicional para as modificações de sistema potencialmente perigosas ou quando quiser fornecer opções de Sim-para-all e não a tudo ao utilizador.</span><span class="sxs-lookup"><span data-stu-id="df328-173">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="df328-174">O exemplo seguinte mostra a chamada para [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) de substituição do [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método na amostra Cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="df328-174">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter receives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across multiple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (criticalProcess...
```

## <a name="stopping-input-processing"></a><span data-ttu-id="df328-175">A parar processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="df328-175">Stopping Input Processing</span></span>

<span data-ttu-id="df328-176">A método de um cmdlet que faz com que as modificações de sistema de processamento de entrada tem de fornecer uma forma de parar o processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="df328-176">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="df328-177">No caso deste cmdlet Stop-Proc, é feita uma chamada a partir da [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para o [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) método.</span><span class="sxs-lookup"><span data-stu-id="df328-177">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="df328-178">Uma vez que o `PassThru` parâmetro estiver definido como `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) também chama [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) para enviar o objeto de processo para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="df328-178">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="df328-179">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="df328-179">Code Sample</span></span>

<span data-ttu-id="df328-180">Para o completa C# código de exemplo, consulte [exemplo de StopProcessSample01](./stopprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="df328-180">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="df328-181">Definir tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="df328-181">Defining Object Types and Formatting</span></span>

<span data-ttu-id="df328-182">Windows PowerShell passa informações entre cmdlets com objetos .net.</span><span class="sxs-lookup"><span data-stu-id="df328-182">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="df328-183">Consequentemente, um cmdlet poderá ter de definir seu próprio tipo, ou o cmdlet poderá ter de expandir um tipo existente fornecido pelo outro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="df328-183">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="df328-184">Para obter mais informações sobre definir novos tipos ou estendendo tipos existentes, consulte [estendendo tipos de objeto e formatação](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="df328-184">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="df328-185">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="df328-185">Building the Cmdlet</span></span>

<span data-ttu-id="df328-186">Depois de implementar um cmdlet, tem de ser registado com o Windows PowerShell através de um snap-in do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df328-186">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="df328-187">Para obter mais informações sobre como registar os cmdlets, consulte [como registrar Cmdlets, fornecedores e alojar aplicações](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="df328-187">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="df328-188">O Cmdlet de teste</span><span class="sxs-lookup"><span data-stu-id="df328-188">Testing the Cmdlet</span></span>

<span data-ttu-id="df328-189">Quando seu cmdlet foi registado com o Windows PowerShell, pode testá-lo executando-a na linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="df328-189">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="df328-190">Seguem-se vários testes que testam o cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="df328-190">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="df328-191">Para obter mais informações sobre como utilizar cmdlets da linha de comando, consulte a [introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="df328-191">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="df328-192">Inicie o Windows PowerShell e utilize o cmdlet Stop-Proc para parar o processamento, conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="df328-192">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="df328-193">Uma vez que o cmdlet Especifica a `Name` parâmetro como obrigatória, as consultas de cmdlet para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="df328-193">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="df328-194">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="df328-194">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="df328-195">Agora vamos utilizar o cmdlet para parar o processo com o nome "Bloco de notas".</span><span class="sxs-lookup"><span data-stu-id="df328-195">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="df328-196">O cmdlet pede-lhe para confirmar a ação.</span><span class="sxs-lookup"><span data-stu-id="df328-196">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

<span data-ttu-id="df328-197">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="df328-197">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="df328-198">Utilize Stop-Proc conforme mostrado para parar o processo crítico com o nome "WINLOGON".</span><span class="sxs-lookup"><span data-stu-id="df328-198">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="df328-199">É solicitado e avisado sobre como efetuar esta ação, porque fará com que o sistema operativo reiniciar o computador.</span><span class="sxs-lookup"><span data-stu-id="df328-199">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

<span data-ttu-id="df328-200">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="df328-200">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="df328-201">Vamos agora tentar parar o processo WINLOGON sem receber um aviso.</span><span class="sxs-lookup"><span data-stu-id="df328-201">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="df328-202">Lembre-se de que esta entrada de comando utiliza o `Force` parâmetro para ignorar o aviso.</span><span class="sxs-lookup"><span data-stu-id="df328-202">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

<span data-ttu-id="df328-203">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="df328-203">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="df328-204">Veja Também</span><span class="sxs-lookup"><span data-stu-id="df328-204">See Also</span></span>

[<span data-ttu-id="df328-205">Adicionar parâmetros que processam a entrada da linha de comandos</span><span class="sxs-lookup"><span data-stu-id="df328-205">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="df328-206">Estendendo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="df328-206">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="df328-207">Como registar os Cmdlets, fornecedores e alojar aplicações</span><span class="sxs-lookup"><span data-stu-id="df328-207">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="df328-208">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="df328-208">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="df328-209">Exemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="df328-209">Cmdlet Samples</span></span>](./cmdlet-samples.md)