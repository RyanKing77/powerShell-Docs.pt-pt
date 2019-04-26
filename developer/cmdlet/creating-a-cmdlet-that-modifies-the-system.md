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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068444"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>Creating a Cmdlet that Modifies the System (Criar um Cmdlet que Modifica o Sistema)

Por vezes, um cmdlet tem de modificar o estado de execução do sistema, não apenas o estado do tempo de execução do Windows PowerShell. Nestes casos, o cmdlet deve permitir ao utilizador uma oportunidade para confirmar se deve ou não efetue a alteração.

Para oferecer suporte a confirmação de um cmdlet tem de fazer duas coisas.

- Declarar que o cmdlet oferece suporte a confirmação quando especificar a [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atributo ao definir a palavra-chave SupportsShouldProcess como `true`.

- Chamar [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) durante a execução do cmdlet (conforme mostrado no exemplo a seguir).

Ao suportar confirmação, expõe um cmdlet do `Confirm` e `WhatIf` parâmetros que são fornecidos pelo Windows PowerShell e também cumpre as diretrizes de desenvolvimento para os cmdlets (para obter mais informações sobre as diretrizes de desenvolvimento do cmdlet, consulte [ Diretrizes de desenvolvimento do cmdlet](./cmdlet-development-guidelines.md).).

## <a name="changing-the-system"></a>Alterar o sistema

O ato de "alterar o sistema" refere-se para qualquer cmdlet que potencialmente altera o estado do sistema fora do Windows PowerShell. Por exemplo, a parar um processo, ativar ou desativar uma conta de utilizador ou adicionar uma linha a uma tabela de base de dados são todas as alterações ao sistema que deve ser confirmada. Por outro lado, operações que leu os dados ou estabelecer ligações transitórias não altere o sistema e geralmente não necessitam de confirmação. Confirmação também não é necessária para ações cujo efeito é limitado para dentro do runtime do Windows PowerShell, tal como `set-variable`. Cmdlets que podem ou não pode fazer uma alteração persistente devem declarar `SupportsShouldProcess` e chamar [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) apenas se estiverem prestes a efetuar uma alteração persistente.

> [!NOTE]
> Confirmação de ShouldProcess aplica-se apenas aos cmdlets. Se um comando ou script modifica o estado de execução de um sistema chamando diretamente as propriedades ou métodos do .NET, ou por chamada aplicações fora do Windows PowerShell, essa forma de confirmação não estará disponível.

## <a name="the-stopproc-cmdlet"></a>O StopProc Cmdlet

Este tópico descreve um cmdlet Stop-Proc que tenta parar os processos que são obtidos com o cmdlet Get-Proc (descrito em [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)).

Os tópicos nesta secção incluem o seguinte:

- [Definir o Cmdlet](#Defining-the-Cmdlet)

- [Definir parâmetros para modificação do sistema](#Defining-Parameters-for-System-Modification)

- [Substituir uma método de processamento de entrada](#Overriding-an-Input-Processing-Method)

- [Chamando o método ShouldProcess.](#Calling-the-ShouldProcess-Method)

- [Chamando o método de ShouldContinue](#Calling-the-ShouldContinue-Method)

- [A parar processamento de entrada](#Stopping-Input-Processing)

- [Exemplo de código](#Code-Sample)

- [Definir tipos de objeto e formatação](#Defining-Object-Types-and-Formatting)

- [Criando o Cmdlet](#Building-the-Cmdlet)

- [O Cmdlet de teste](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Definir o Cmdlet

A primeira etapa na criação do cmdlet é sempre o cmdlet de nomenclatura e declarar a classe do .NET que implementa o cmdlet. Uma vez que esteja escrevendo um cmdlet para alterar o sistema, deve ser nomeado em conformidade. Este cmdlet deixar de processos do sistema, portanto, o nome de verbo escolhido aqui é "Parar", definido pela [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) classe, com o substantivo "Procedimento" para indicar que o cmdlet interrompe processos. Para obter mais informações sobre verbos aprovados cmdlet, consulte [nomes de verbo do Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Segue-se a definição de classe para este cmdlet Stop-Proc.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

Tenha em atenção que, na [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaração, o `SupportsShouldProcess` palavra-chave do atributo está definido como `true` para ativar o cmdlet fazer chamadas para [ System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). Sem este conjunto de palavra-chave, o `Confirm` e `WhatIf` parâmetros não estarão disponíveis ao usuário.

### <a name="extremely-destructive-actions"></a>Ações extremamente destrutivas

Algumas operações são extremamente destrutivas, tais como reformatação uma partição de disco de rígido Active Directory. Nestes casos, deve definir o cmdlet `ConfirmImpact`  =  `ConfirmImpact.High` ao declarar o [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atributo. Esta definição força o cmdlet a confirmação do utilizador pedido, mesmo quando o usuário não especificou o `Confirm` parâmetro. No entanto, os desenvolvedores de cmdlet devem evitar o excesso `ConfirmImpact` para operações que são apenas potencialmente destrutivas, como eliminar uma conta de utilizador. Lembre-se de que, se `ConfirmImpact` está definido como [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).

Da mesma forma, algumas operações são provavelmente não destrutiva, embora eles teoricamente modificar o estado de execução de um sistema fora do Windows PowerShell. Pode definir esses cmdlets `ConfirmImpact` para [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0). Isto irá ignorar pedidos de confirmação em que o utilizador recebe o pedido para confirmar a operações apenas impacto médio e alto impacto.

## <a name="defining-parameters-for-system-modification"></a>Definir parâmetros para modificação do sistema

Esta secção descreve como definir os parâmetros do cmdlet, incluindo os que são necessários para a modificação do sistema de suporte. Ver [adicionando parâmetros essa entrada de linha de comandos do processo](./adding-parameters-that-process-command-line-input.md) se precisar de informações gerais sobre a definição de parâmetros.

O cmdlet Stop-Proc define três parâmetros: `Name`, `Force`, e `PassThru`.

O `Name` parâmetro corresponde ao `Name` propriedade do objeto de entrada do processo. Tenha em atenção que o `Name` este exemplo é o parâmetro obrigatório, como o cmdlet irá falhar se não tiver um processo com o nome para parar.

O `Force` parâmetro permite que o usuário substitui as chamadas ao [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). Na verdade, qualquer cmdlet que chama [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) deve ter um `Force` parâmetro, de modo que quando `Force` for especificado, o cmdlet ignora a chamada para [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) e prossegue com a operação. Lembre-se de que isso não afeta chamadas para [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).

O `PassThru` parâmetro permite que o utilizador indicar se o cmdlet passa um objeto de saída através do pipeline, neste caso, depois de um processo é parado. Lembre-se de que este parâmetro está ligado ao cmdlet em si em vez da uma propriedade do objeto de entrada.

Segue-se a declaração de parâmetro para o cmdlet Stop-Proc.

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

## <a name="overriding-an-input-processing-method"></a>Substituir uma método de processamento de entrada

O cmdlet tem de substituir uma método de processamento de entrada. O código a seguir ilustra o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) utilizada no cmdlet Stop-Proc exemplo de substituição. Para cada pedido o nome do processo, esse método garante que o processo não é um processo especial, tenta parar o processo e, em seguida, envia um objeto de saída, se o `PassThru` parâmetro for especificado.

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

## <a name="calling-the-shouldprocess-method"></a>Chamando o método ShouldProcess.

A entrada a processar o método de seu cmdlet deve chamar o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método para confirmar a execução de uma operação antes de uma alteração (por exemplo, ao eliminar ficheiros) é feita para o estado de execução do sistema. Isso permite que o tempo de execução do Windows PowerShell fornecer o comportamento correto de "WhatIf" e "Confirmar" dentro do shell.

> [!NOTE]
> Se um cmdlet afirma que ele oferece suporte deve processar e não conseguir fazer a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamar, o utilizador pode modificar o sistema inesperadamente.

A chamada para [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) envia o nome do recurso a ser alterados ao usuário, com o tempo de execução do Windows PowerShell tendo em conta as definições da linha de comandos ou variáveis de preferência determinar o que deverá ser apresentado ao utilizador.

O exemplo seguinte mostra a chamada para [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) de substituição do [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método na amostra Cmdlet Stop-Proc.

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>Chamando o método de ShouldContinue

A chamada para o [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método envia uma mensagem de secundária para o utilizador. Esta chamada é feita após a chamada para [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) devolve `true` e, se o `Force` parâmetro não foi definido como `true`. O utilizador, em seguida, pode fornecer comentários para dizer se a operação deve ser contínuo. As chamadas de cmdlet [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) como uma verificação adicional para as modificações de sistema potencialmente perigosas ou quando quiser fornecer opções de Sim-para-all e não a tudo ao utilizador.

O exemplo seguinte mostra a chamada para [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) de substituição do [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método na amostra Cmdlet Stop-Proc.

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

## <a name="stopping-input-processing"></a>A parar processamento de entrada

A método de um cmdlet que faz com que as modificações de sistema de processamento de entrada tem de fornecer uma forma de parar o processamento de entrada. No caso deste cmdlet Stop-Proc, é feita uma chamada a partir da [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para o [System.Diagnostics.Process.Kill*](/dotnet/api/System.Diagnostics.Process.Kill) método. Uma vez que o `PassThru` parâmetro estiver definido como `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) também chama [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) para enviar o objeto de processo para o pipeline.

## <a name="code-sample"></a>Exemplo de código

Para o completa C# código de exemplo, consulte [exemplo de StopProcessSample01](./stopprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir tipos de objeto e formatação

Windows PowerShell passa informações entre cmdlets com objetos .net. Consequentemente, um cmdlet poderá ter de definir seu próprio tipo, ou o cmdlet poderá ter de expandir um tipo existente fornecido pelo outro cmdlet. Para obter mais informações sobre definir novos tipos ou estendendo tipos existentes, consulte [estendendo tipos de objeto e formatação](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Criando o Cmdlet

Depois de implementar um cmdlet, tem de ser registado com o Windows PowerShell através de um snap-in do Windows PowerShell. Para obter mais informações sobre como registar os cmdlets, consulte [como registrar Cmdlets, fornecedores e alojar aplicações](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>O Cmdlet de teste

Quando seu cmdlet foi registado com o Windows PowerShell, pode testá-lo executando-a na linha de comandos. Seguem-se vários testes que testam o cmdlet Stop-Proc. Para obter mais informações sobre como utilizar cmdlets da linha de comando, consulte a [introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Inicie o Windows PowerShell e utilize o cmdlet Stop-Proc para parar o processamento, conforme mostrado abaixo. Uma vez que o cmdlet Especifica a `Name` parâmetro como obrigatória, as consultas de cmdlet para o parâmetro.

    ```powershell
    PS> stop-proc
    ```

O resultado seguinte é apresentada.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- Agora vamos utilizar o cmdlet para parar o processo com o nome "Bloco de notas". O cmdlet pede-lhe para confirmar a ação.

    ```powershell
    PS> stop-proc -Name notepad
    ```

O resultado seguinte é apresentada.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Utilize Stop-Proc conforme mostrado para parar o processo crítico com o nome "WINLOGON". É solicitado e avisado sobre como efetuar esta ação, porque fará com que o sistema operativo reiniciar o computador.

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

O resultado seguinte é apresentada.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- Vamos agora tentar parar o processo WINLOGON sem receber um aviso. Lembre-se de que esta entrada de comando utiliza o `Force` parâmetro para ignorar o aviso.

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

O resultado seguinte é apresentada.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Veja Também

[Adicionar parâmetros que processam a entrada da linha de comandos](./adding-parameters-that-process-command-line-input.md)

[Estendendo tipos de objeto e formatação](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Como registar os Cmdlets, fornecedores e alojar aplicações](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[SDK do Windows PowerShell](../windows-powershell-reference.md)

[Exemplos de cmdlet](./cmdlet-samples.md)