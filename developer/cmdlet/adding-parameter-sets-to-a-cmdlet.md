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
ms.openlocfilehash: 6a3b592c5f85c1f065ad4b5b0290cf44dcef484e
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854886"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>Adding Parameter Sets to a Cmdlet (Adicionar Conjuntos de Parâmetros a um Cmdlet)

## <a name="things-to-know-about-parameter-sets"></a>Que precisa saber sobre conjuntos de parâmetros

Windows PowerShell define um parâmetro definido como um grupo de parâmetros que funcionam em conjunto. Ao agrupar os parâmetros de um cmdlet, pode criar um único cmdlet que pode alterar a sua funcionalidade com base no que grupo de parâmetros que o utilizador Especifica.

Um exemplo de um cmdlet que usa dois conjuntos de parâmetros para definir funcionalidades diferentes é o `Get-EventLog` cmdlet fornecido pelo Windows PowerShell. Este cmdlet retorna informações distintas quando o utilizador Especifica os `List` ou `LogName` parâmetro. Se o `LogName` parâmetro for especificado, o cmdlet retorna informações sobre os eventos em determinado log de eventos. Se o `List` parâmetro for especificado, o cmdlet devolve informações sobre o registo de ficheiros propriamente ditos (não as informações de eventos contêm). Neste caso, o `List` e `LogName` parâmetros identificam dois conjuntos de parâmetros separados.

Dois pontos importantes a serem lembrados sobre conjuntos de parâmetros é que o tempo de execução do Windows PowerShell utiliza apenas um parâmetro definido para uma determinada entrada, e que cada conjunto de parâmetros têm de ter, pelo menos, um parâmetro que é exclusiva para esse conjunto de parâmetros.

Para ilustrar esse último ponto, este cmdlet Stop-Proc utiliza três conjuntos de parâmetros: `ProcessName`, `ProcessId`, e `InputObject`. Cada um desses conjuntos de parâmetros tem um parâmetro que não esteja em outros conjuntos de parâmetros. Os conjuntos de parâmetros podem partilhar os outros parâmetros, mas o cmdlet utiliza os parâmetros exclusivos `ProcessName`, `ProcessId`, e `InputObject` para identificar qual conjunto de parâmetros que o tempo de execução do Windows PowerShell deve utilizar.

## <a name="declaring-the-cmdlet-class"></a>Declarar a classe Cmdlet

A primeira etapa na criação do cmdlet é sempre o cmdlet de nomenclatura e declarar a classe do .NET que implementa o cmdlet. Para este cmdlet, o verbo do ciclo de vida "Stop" é utilizado porque o cmdlet interrompe processos do sistema. O nome do substantivo "Proc" é utilizado porque o cmdlet funciona em processos. Na declaração abaixo, tenha em atenção que o nome de verbo e substantivo do cmdlet são refletidas no nome da classe de cmdlet.

> [!NOTE]
> Para obter mais informações sobre nomes de verbo do cmdlet aprovados, consulte [nomes de verbo do Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

O código a seguir é a definição de classe para este cmdlet Stop-Proc.

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a>Declarar os parâmetros do Cmdlet

Este cmdlet define três parâmetros necessários como entrada para o cmdlet (esses parâmetros também definem os conjuntos de parâmetros), bem como um `Force` parâmetro que gere o que o cmdlet faz e um `PassThru` parâmetro que determina se o cmdlet envia um objeto de saída através do pipeline. Por predefinição, este cmdlet não é transmitido um objeto através do pipeline. Para obter mais informações sobre estes dois últimos parâmetros, consulte [criar um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).

### <a name="declaring-the-name-parameter"></a>Declarando o parâmetro de nome

Este parâmetro de entrada permite ao utilizador especificar os nomes dos processos de ser parado. Tenha em atenção que o `ParameterSetName` atributo palavra-chave do [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributo especifica o `ProcessName` parâmetro definido para este parâmetro.

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

Observe também que o alias "ProcessName" é fornecido para este parâmetro.

### <a name="declaring-the-id-parameter"></a>Declarando o parâmetro de Id

Este parâmetro de entrada permite ao utilizador especificar os identificadores dos processos de ser parado. Tenha em atenção que o `ParameterSetName` palavra-chave de atributo a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributo especifica o `ProcessId` conjunto de parâmetros.

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

Observe também que o alias "ProcessId" é fornecido para este parâmetro.

### <a name="declaring-the-inputobject-parameter"></a>Declarando o parâmetro InputObject

Este parâmetro de entrada permite ao utilizador especificar um objeto de entrada que contém informações sobre os processos de ser parado. Tenha em atenção que o `ParameterSetName` atributo palavra-chave do [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributo especifica o `InputObject` parâmetro definido para este parâmetro.

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

Observe também que este parâmetro não tem nenhum alias.

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>Declarando parâmetros em vários conjuntos de parâmetros

Embora tem de existir um parâmetro exclusivo para cada conjunto de parâmetros, os parâmetros podem pertencer a mais do que um conjunto de parâmetros. Nestes casos, fornecer o parâmetro partilhado um [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaração de atributo para cada conjunto a que o parâmetro de pertence. Se for um parâmetro em todos os conjuntos de parâmetros, só tem de declarar o atributo de parâmetro de uma vez e não é necessário especificar que o parâmetro de nome do conjunto.

## <a name="overriding-an-input-processing-method"></a>Substituir uma método de processamento de entrada

Cada cmdlet tem de substituir uma método de processamento de entrada, mais freqüentemente, isso será o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método. Neste cmdlet, o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método é substituído para que o cmdlet pode processar qualquer número de processos. Ela contém uma instrução Select que chama um método diferente com base no conjunto de parâmetros que o utilizador especificado.

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

Métodos auxiliares chamados pela instrução Select não são descritos aqui, mas pode ver a sua implementação no exemplo de código completo, na secção seguinte.

## <a name="code-sample"></a>Exemplo de código

Para o completa C# código de exemplo, consulte [exemplo de StopProcessSample04](./stopprocesssample04-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir tipos de objeto e formatação

Windows PowerShell passa informações entre cmdlets com objetos .NET. Consequentemente, um cmdlet poderá ter de definir seu próprio tipo, ou o cmdlet poderá ter de expandir um tipo existente fornecido pelo outro cmdlet. Para obter mais informações sobre definir novos tipos ou estendendo tipos existentes, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Criando o Cmdlet

Depois de implementar um cmdlet, tem de registá-lo com o Windows PowerShell através de um snap-in do Windows PowerShell. Para obter mais informações sobre como registar os cmdlets, consulte [como registrar Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>O Cmdlet de teste

Quando seu cmdlet foi registado com o Windows PowerShell, testá-la executando-a na linha de comandos. Aqui estão alguns testes que mostram como o `ProcessId` e `InputObject` parâmetros podem ser utilizados para testar seus conjuntos de parâmetros para interromper um processo.

- Com o PowerShell do Windows iniciado, execute o cmdlet Stop-Proc com o `ProcessId` parâmetro definido para parar um processo com base no respetivo identificador. Neste caso, o cmdlet está a utilizar o `ProcessId` parâmetro definido para parar o processo.

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Com o PowerShell do Windows iniciado, execute o cmdlet Stop-Proc com o `InputObject` parâmetro definido como para parar os processos no objeto obtido pelo bloco de notas a `Get-Process` comando.

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Veja Também

[Criar um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Como criar um Cmdlet do Windows PowerShell](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Como registar os Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
