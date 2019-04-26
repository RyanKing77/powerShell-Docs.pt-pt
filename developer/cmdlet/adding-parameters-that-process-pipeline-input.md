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
ms.openlocfilehash: bd52dc8aee7975d0899083a5c2f595b17690dc33
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068764"
---
# <a name="adding-parameters-that-process-pipeline-input"></a>Adding Parameters that Process Pipeline Input (Adicionar Parâmetros que Processam Entradas de Pipeline)

Uma fonte de entrada para um cmdlet é um objeto no pipeline que provém de um cmdlet a montante. Esta secção descreve como adicionar um parâmetro para o cmdlet Get-Proc (descrito em [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)) para que o cmdlet pode processar objetos do pipeline.

Este cmdlet de Get-Proc utiliza um `Name` parâmetro que aceite entrada de um objeto de pipeline, obtém informações de processo a partir do computador local com base nos nomes fornecidos e, em seguida, apresenta informações sobre os processos na linha de comandos.

Os tópicos nesta secção incluem o seguinte:

- [Definir a classe Cmdlet](#Defining-the-Cmdlet-Class)

- [Definir a entrada do Pipeline](#Defining-Input-from-the-Pipeline)

- [Substituir uma método de processamento de entrada](#Overriding-an-Input-Processing-Method)

- [Exemplo de código](#Code-Sample)

- [Definir tipos de objeto e formatação](#Defining-Object-Types-and-Formatting)

- [Criando o Cmdlet](#Building-the-Cmdlet)

- [O Cmdlet de teste](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a>Definir a classe Cmdlet

A primeira etapa na criação do cmdlet é sempre o cmdlet de nomenclatura e declarar a classe do .NET que implementa o cmdlet. Este cmdlet obtém informações do processo, portanto, o nome de verbo escolhido aqui é "Get". (Quase qualquer tipo de cmdlet que é capaz de obtenção de informações pode processar entrada da linha de comandos). Para obter mais informações sobre verbos aprovados cmdlet, consulte [nomes de verbo do Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Segue-se a definição para este cmdlet de Get-Proc. Detalhes desta definição recebem [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a>Definir a entrada do Pipeline

Esta secção descreve como definir a entrada do pipeline para um cmdlet. Este cmdlet de Get-Proc define uma propriedade que representa a `Name` parâmetro, conforme descrito na [adicionando parâmetros essa entrada de linha de comandos do processo](./adding-parameters-that-process-command-line-input.md). (Consulte esse tópico para obter informações gerais sobre a declaração de parâmetros.)

No entanto, quando precisa de um cmdlet processar a entrada do pipeline, tem de ter seus parâmetros vinculados a valores de entrada pelo tempo de execução do Windows PowerShell. Para tal, tem de adicionar o `ValueFromPipeline` palavra-chave ou adicionar a `ValueFromPipelineByProperty` palavra-chave para o [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaração de atributo. Especifique o `ValueFromPipeline` palavra-chave se o cmdlet acessa o objeto de entrada completado. Especifique o `ValueFromPipelineByProperty` se o cmdlet acede a apenas uma propriedade do objeto.

Aqui é a declaração de parâmetro para o `Name` parâmetro deste cmdlet de Get-Proc que aceita entrada do pipeline.

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

Os conjuntos de declaração anterior a `ValueFromPipeline` palavra-chave para `true` para que o tempo de execução do Windows PowerShell irá vincular o parâmetro para o objeto de entrada, se o objeto é o mesmo tipo com o parâmetro ou se ele pode ser forçado para o mesmo tipo. O `ValueFromPipelineByPropertyName` palavra-chave também está definida como `true` , para que o tempo de execução do Windows PowerShell irá verificar o objeto de entrada para um `Name` propriedade. Se o objeto de entrada tem uma propriedade desse tipo, o tempo de execução irá vincular a `Name` parâmetro para o `Name` propriedade do objeto de entrada.

> [!NOTE]
> A definição do `ValueFromPipeline` palavra-chave de atributo para um parâmetro tem precedência sobre a definição para o `ValueFromPipelineByPropertyName` palavra-chave.

## <a name="overriding-an-input-processing-method"></a>Substituir uma método de processamento de entrada

Se for seu cmdlet para processar a entrada do pipeline, tem de substituir a entrada apropriada de métodos de processamento. Os métodos de processamento básico de entrada são introduzidos nas [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).

Este cmdlet de Get-Proc substitui o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para tratar a `Name` entrada de parâmetro fornecida pelo utilizador ou um script. Este método irá obter os processos para cada nome do processo de pedido ou todos os processos se não for fornecido nenhum nome. Repare que dentro [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), a chamada para [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) é a saída objetos do mecanismo de envio de saída no pipeline. O segundo parâmetro desta chamada `enumerateCollection`, está definida como `true` para informar o tempo de execução do Windows PowerShell para enumerar a matriz de objetos de processo e escrever um processo de cada vez à linha de comandos.

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

## <a name="code-sample"></a>Exemplo de código

Para o completa C# código de exemplo, consulte [exemplo de GetProcessSample03](./getprocesssample03-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir tipos de objeto e formatação

Windows PowerShell passa informações entre cmdlets com objetos .net. Consequentemente, um cmdlet poderá ter de definir seu próprio tipo, ou o cmdlet poderá ter de expandir um tipo existente fornecido pelo outro cmdlet. Para obter mais informações sobre definir novos tipos ou estendendo tipos existentes, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Criando o Cmdlet

Após a implementação de um cmdlet tem de ser registado com o Windows PowerShell através de um snap-in do Windows PowerShell. Para obter mais informações sobre como registar os cmdlets, consulte [como registrar Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>O Cmdlet de teste

Quando seu cmdlet foi registado com o Windows PowerShell, testá-la executando-a na linha de comandos. Por exemplo, teste o código para o cmdlet de exemplo. Para obter mais informações sobre como utilizar cmdlets da linha de comando, consulte a [introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- No prompt do Windows PowerShell, introduza os seguintes comandos para recuperar os nomes de processo através do pipeline.

    ```powershell
    PS> type ProcessNames | get-proc
    ```

O resultado seguinte é apresentada.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- Introduza as seguintes linhas ao obter os objetos de processo que tenham um `Name` propriedade dos processos chamado "IEXPLORE". Este exemplo utiliza o `Get-Process` cmdlet (fornecido pelo Windows PowerShell) como um comando a montante para obter os processos de "IEXPLORE".

    ```powershell
    PS> get-process iexplore | get-proc
    ```

O resultado seguinte é apresentada.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a>Veja Também

[Adicionar parâmetros que processam a entrada de linha de comandos](./adding-parameters-that-process-command-line-input.md)

[Criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)

[Estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Como registar os Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Referência do Windows PowerShell](../windows-powershell-reference.md)

[Exemplos de cmdlet](./cmdlet-samples.md)
