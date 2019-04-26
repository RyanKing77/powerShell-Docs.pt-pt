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
ms.openlocfilehash: 5b3a5f5d5d02c7d5a3c1d622ec1a3740739c694f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068781"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>Adding User Messages to Your Cmdlet (Adicionar Mensagens para o Utilizador ao seu Cmdlet)

Cmdlets pode gravar vários tipos de mensagens que podem ser apresentados ao utilizador pelo tempo de execução do Windows PowerShell. Essas mensagens incluem os seguintes tipos:

- Mensagens verbosas que contêm informações de utilizador gerais.

- Depure mensagens que contêm informações de resolução de problemas.

- Mensagens de aviso que contêm uma notificação que o cmdlet está prestes a realizar uma operação que pode ter resultados inesperados.

- O cmdlet de trabalho de mensagens que contêm informações sobre a quantidade de relatório de progresso está concluída quando efetuar uma operação que demora muito tempo.

Não há nenhum limite para o número de mensagens que seu cmdlet pode escrever ou o tipo de mensagens que escreve seu cmdlet. Cada mensagem foi escrita por fazer uma chamada específica a partir da entrada a processar o método de seu cmdlet.

## <a name="the-stopproc-cmdlet"></a>O StopProc Cmdlet

Os tópicos nesta secção incluem o seguinte:

- [Definir o Cmdlet](#Defining-the-Cmdlet)

- [Definir parâmetros para modificação do sistema](#Defining-Parameters-for-System-Modification)

- [Substituir uma método de processamento de entrada](#Overriding-an-Input-Processing-Method)

- [Gravar uma mensagem detalhada](#Writing-a-Verbose-Message)

- [Escrever uma mensagem de depuração](#Writing-a-Debug-Message)

- [Escrever uma mensagem de aviso](#Writing-a-Warning-Message)

- [Escrever uma mensagem de progresso](#Writing-a-Progress-Message)

- [Exemplo de código](#Code-Sample)

- [Definir tipos de objeto e formatação](#Define-Object-Types-and-Formatting)

- [Criando o Cmdlet](#Building-the-Cmdlet)

- [O Cmdlet de teste](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Definir o Cmdlet

A primeira etapa na criação do cmdlet é sempre o cmdlet de nomenclatura e declarar a classe do .NET que implementa o cmdlet. Qualquer tipo de cmdlet pode escrever notificações do utilizador da sua entrada processamento métodos; então, em geral, pode nomear este cmdlet com qualquer verbo que indica quais modificações de sistema que executa o cmdlet. Para obter mais informações sobre verbos aprovados cmdlet, consulte [nomes de verbo do Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

O cmdlet Stop-Proc foi concebido para modificar o sistema; Por conseguinte, o [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaração para a classe do .NET tem de incluir o `SupportsShouldProcess` palavra-chave de atributo e ser definido como `true`.

O código a seguir é a definição para esta classe de cmdlet Stop-Proc. Para obter mais informações sobre esta definição, consulte [criar um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definir parâmetros para modificação do sistema

O cmdlet Stop-Proc define três parâmetros: `Name`, `Force`, e `PassThru`. Para obter mais informações sobre como definir estes parâmetros, consulte [criar um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).

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

Seu cmdlet tem de substituir uma método de processamento de entrada, com mais frequência ficará [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Este cmdlet Stop-Proc substitui o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método de processamento de entrada. Nessa implementação do cmdlet Stop-Proc, as chamadas são feitas para escrever as mensagens verbosas, mensagens de depuração e mensagens de aviso.

> [!NOTE]
> Para obter mais informações sobre como esse método chama o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos, consulte [Criação de um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="writing-a-verbose-message"></a>Gravar uma mensagem detalhada

O [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método é usado para escrever informações gerais do nível de usuário que não está relacionada com as condições de erro específico. O administrador de sistema, em seguida, pode utilizar essas informações para continuar a processar outros comandos. Além disso, qualquer informação escrita usando esse método deve ser localizada conforme necessário.

O código seguinte deste cmdlet Stop-Proc mostra duas chamadas para o [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método de substituição do [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>Escrever uma mensagem de depuração

O [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método é usado para escrever mensagens de depuração que podem ser utilizadas para resolver problemas relacionados com a operação do cmdlet. A chamada é feita a partir de uma método de processamento de entrada.

> [!NOTE]
> Windows PowerShell também define um `Debug` parâmetro que apresenta ambos verboso e informações de depuração. Se seu cmdlet oferece suporte esse parâmetro, não é necessário chamar [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) no mesmo código que chama [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .

As duas secções seguintes de código do cmdlet Stop-Proc exemplo mostram chamadas para o [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método de substituição do [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.

Esta mensagem de depuração é gravada imediatamente antes [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) é chamado.

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

Esta mensagem de depuração é gravada imediatamente antes [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) é chamado.

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell encaminha automaticamente qualquer [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) chamadas para os cmdlets e infra-estrutura de rastreamento. Isso permite que as chamadas de método para ser rastreados no aplicativo de hospedagem, um arquivo ou um depurador sem ter de fazer qualquer trabalho de desenvolvimento extra dentro do cmdlet. A seguinte entrada de linha de comando implementa uma operação de rastreamento.

**PS > expressão de rastreio stop-proc-proc.log de ficheiro-bloco de notas do comando stop-proc**

## <a name="writing-a-warning-message"></a>Escrever uma mensagem de aviso

O [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método é usado para escrever um aviso quando o cmdlet está prestes a realizar uma operação que poderá ter um resultado inesperado, por exemplo, substituindo um arquivo só de leitura.

O código a seguir do cmdlet Stop-Proc exemplo mostra a chamada para o [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método de substituição do [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a>Escrever uma mensagem de progresso

O [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) é utilizada para escrever mensagens de progresso quando operações de cmdlet demorar mais tempo a concluir. Uma chamada para [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passa um [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) objeto que é enviado para o aplicativo de hospedagem para a composição para o usuário.

> [!NOTE]
> Este cmdlet Stop-Proc não inclui uma chamada para o [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) método.

O código a seguir é um exemplo de uma mensagem de progresso, escrito por um cmdlet que está a tentar copiar um item.

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a>Exemplo de código

Para o completa C# código de exemplo, consulte [exemplo de StopProcessSample02](./stopprocesssample02-sample.md).

## <a name="define-object-types-and-formatting"></a>Definir tipos de objeto e formatação

Windows PowerShell passa informações entre cmdlets com objetos .NET. Consequentemente, um cmdlet poderá ter de definir seu próprio tipo, ou o cmdlet poderá ter de expandir um tipo existente fornecido pelo outro cmdlet. Para obter mais informações sobre definir novos tipos ou estendendo tipos existentes, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Criando o Cmdlet

Depois de implementar um cmdlet, tem de ser registado com o Windows PowerShell através de um snap-in do Windows PowerShell. Para obter mais informações sobre como registar os cmdlets, consulte [como registrar Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>O Cmdlet de teste

Quando seu cmdlet foi registado com o Windows PowerShell, pode testá-lo executando-a na linha de comandos. Vamos testar o cmdlet Stop-Proc de exemplo. Para obter mais informações sobre como utilizar cmdlets da linha de comando, consulte a [introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- A seguinte entrada de linha de comandos utiliza Stop-Proc para parar o processo com o nome "Bloco de notas", fornecer notificações verbosas e imprimir informações de depuração.

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

O resultado seguinte é apresentada.

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

## <a name="see-also"></a>Veja Também

[Criar um Cmdlet que modifique o sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Como criar um Cmdlet do Windows PowerShell](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Como registar os Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
