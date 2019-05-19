---
title: Adicionar parâmetros que processam a entrada da linha de comandos | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: c9ad84c5bcb6826fcf51db9a1f1a578a65a1f275
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854953"
---
# <a name="adding-parameters-that-process-command-line-input"></a>Adding Parameters That Process Command-Line Input (Adicionar Parâmetros que Processam Entradas da Linha de Comandos)

Uma fonte de entrada para um cmdlet é a linha de comandos. Este tópico descreve como adicionar um parâmetro para o **Get-Proc** cmdlet (descrito na [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)) para que o cmdlet pode processar a entrada a partir do computador local com base em explícita objetos transmitidos ao cmdlet. O **Get-Proc** cmdlet descrito aqui obtém processos com base em seus nomes e, em seguida, apresenta informações sobre os processos num prompt de comando.

## <a name="defining-the-cmdlet-class"></a>Definir a classe Cmdlet

A primeira etapa na criação do cmdlet é a nomeação do cmdlet e a declaração da classe .NET Framework que implementa o cmdlet. Este cmdlet obtém as informações de processo, portanto, o nome de verbo escolhido aqui é "Get". (Quase qualquer tipo de cmdlet que é capaz de obtenção de informações pode processar entrada da linha de comandos). Para obter mais informações sobre verbos aprovados cmdlet, consulte [nomes de verbo do Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Aqui é a declaração de classe para o **Get-Proc** cmdlet. São fornecidos detalhes sobre essa definição nas [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a>Declarando parâmetros

Um parâmetro de cmdlet permite que o usuário fornecer entradas ao cmdlet. No exemplo a seguir **Get-Proc** e `Get-Member` são os nomes em pipeline cmdlets, e `MemberType` é um parâmetro para o `Get-Member` cmdlet. O parâmetro tem o argumento "property".

**PS > get-proc; `get-member` MemberType pedidos - propriedade**

Para declarar parâmetros para um cmdlet, deve primeiro definir as propriedades que representam os parâmetros. Na **Get-Proc** é o único parâmetro de cmdlet, `Name`, que neste caso, representa o nome do objeto de processo do .NET Framework para obter. Por conseguinte, a classe cmdlet define uma propriedade de cadeia de caracteres de tipo para aceitar uma matriz de nomes.

Aqui é a declaração de parâmetro para o `Name` parâmetro do **Get-Proc** cmdlet.

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

Para informar o tempo de execução do Windows PowerShell que esta propriedade é o `Name` parâmetro, um [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributo é adicionado à definição da propriedade. A sintaxe básica para declarar este atributo é `[Parameter()]`.

> [!NOTE]
> Um parâmetro tem de ser marcado explicitamente como público. Parâmetros que não estão marcados como padrão público para interno e não são encontrados pelo runtime do Windows PowerShell.

Este cmdlet utiliza uma matriz de cadeias de caracteres para o `Name` parâmetro. Se possível, seu cmdlet também deve definir um parâmetro como uma matriz, porque isso permite que o cmdlet aceitar mais de um item.

#### <a name="things-to-remember-about-parameter-definitions"></a>Coisas a serem lembrados sobre definições de parâmetros

- Predefinidos Windows PowerShell parâmetro nomes e tipos de dados devem ser reutilizados tanto quanto possível para garantir que seu cmdlet é compatível com os cmdlets do Windows PowerShell. Por exemplo, se todos os cmdlets que utilizam o predefinidos `Id` nome do parâmetro para identificar facilmente um recurso, o utilizador será compreender o significado do parâmetro, independentemente de quais cmdlet estão a utilizar. Basicamente, os nomes de parâmetro seguem as mesmas regras que são utilizados para nomes de variáveis em common language runtime (CLR). Para obter mais informações sobre os nomes de parâmetro, consulte [nomes de parâmetros de Cmdlet](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).

- Windows PowerShell reserva alguns nomes de parâmetros para proporcionar uma experiência de usuário consistente. Não utilize estes nomes de parâmetro: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, e `OutBuffer`. Além disso, os seguintes aliases para esses nomes de parâmetros são reservados: `vb`, `db`, `ea`, `ev`, `ov`, e `ob`.

- `Name` é um nome de parâmetro simples e comum, recomendado para utilização em seus cmdlets. É melhor escolher um nome de parâmetro assim que um nome complexo que seja exclusivo para um cmdlet específico e difíceis de memorizar.

- Parâmetros diferenciam maiúsculas de minúsculas no Windows PowerShell, embora por predefinição, o shell preserva caso. Sensibilidade dos argumentos depende da operação do cmdlet. Argumentos são transmitidos para um parâmetro, conforme especificado na linha de comandos.

- Para obter exemplos de outras declarações de parâmetros, consulte [parâmetros de Cmdlet](./cmdlet-parameters.md).

## <a name="declaring-parameters-as-positional-or-named"></a>Declarando parâmetros como posicional ou nomeado

Um cmdlet deve definir cada parâmetro como um parâmetro posicional ou nomeado. Os dois tipos de parâmetros aceitam argumentos únicos, vários argumentos separados por vírgulas e definições booleanas. Um parâmetro booleano, também designado por um *mudar*, processa apenas as definições booleanas. A opção é usada para determinar a presença do parâmetro. A predefinição recomendada é `false`.

O exemplo **Get-Proc** cmdlet define o `Name` parâmetro como um parâmetro posicional com posição 0. Isso significa que o primeiro argumento, que o utilizador introduz na linha de comando é automaticamente inserido para este parâmetro. Se quiser definir um parâmetro nomeado, para que o utilizador tem de especificar o nome do parâmetro da linha de comando, deixe o `Position` palavra-chave fora da declaração de atributo.

> [!NOTE]
> A menos que os parâmetros devem ser nomeados, recomendamos que faça os parâmetros mais utilizadas posicional, para que os utilizadores não terão de digitar o nome do parâmetro.

## <a name="declaring-parameters-as-mandatory-or-optional"></a>Declarando parâmetros como obrigatório ou opcional

Um cmdlet deve definir cada parâmetro como opcional ou um parâmetro obrigatório. No exemplo **Get-Proc** cmdlet, o `Name` parâmetro é definido como opcional, porque o `Mandatory` palavra-chave não está definida na declaração do atributo.

## <a name="supporting-parameter-validation"></a>Suporte a validação de parâmetro

O exemplo **Get-Proc** cmdlet adiciona um atributo de validação de entrada [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute)para o `Name` parâmetro para ativar a validação de que o a entrada é nenhum `null` nem estiver vazio. Este atributo é um dos vários atributos de validação fornecidos pelo Windows PowerShell. Para obter exemplos de outros atributos de validação, consulte [validação de entrada de parâmetro](./validating-parameter-input.md).

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>Substituir uma método de processamento de entrada

Se for seu cmdlet para lidar com entradas de linha de comandos, tem de substituir a entrada apropriada de métodos de processamento. Os métodos de processamento básico de entrada são introduzidos nas [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).

O **Get-Proc** cmdlet substitui o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para tratar a `Name` entrada de parâmetro fornecida pelo utilizador ou um script. Este método obtém os processos para cada nome do processo de pedido ou todos os processos se não for fornecido nenhum nome. Tenha em atenção que no [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), a chamada para [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) é a saída objetos do mecanismo de envio de saída no pipeline. O segundo parâmetro desta chamada `enumerateCollection`, está definida como `true` para informar o tempo de execução do Windows PowerShell enumere a matriz de saída de objetos de processo e escrever um processo de cada vez à linha de comandos.

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
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>Exemplo de código

Para o completa C# código de exemplo, consulte [exemplo de GetProcessSample02](./getprocesssample02-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir tipos de objeto e formatação

Windows PowerShell passa informações entre cmdlets com objetos do .NET Framework. Consequentemente, um cmdlet poderá ter de definir seu próprio tipo, ou um cmdlet poderá ter de expandir um tipo existente fornecido pelo outro cmdlet. Para obter mais informações sobre definir novos tipos ou estendendo tipos existentes, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Criando o Cmdlet

Depois de implementar um cmdlet, tem de registá-lo com o Windows PowerShell, utilizando um snap-in do Windows PowerShell. Para obter mais informações sobre como registar os cmdlets, consulte [como registrar Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>O Cmdlet de teste

Quando seu cmdlet é registrado com o Windows PowerShell, pode testá-lo executando-a na linha de comandos. Seguem-se duas formas de testar o código para o cmdlet de exemplo. Para obter mais informações sobre como utilizar cmdlets da linha de comando, consulte [introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- No prompt do Windows PowerShell, utilize o seguinte comando para listar o processo do Internet Explorer, o que é denominado "IEXPLORE."

    ```powershell
    PS> get-proc -name iexplore
    ```

O resultado seguinte é apresentada.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- Para listar os processos do Internet Explorer, o Outlook e o bloco de notas com o nome "IEXPLORE", "OUTLOOK" e "Bloco de notas", utilizam o seguinte comando. Se existirem vários processos, todos eles são apresentados.

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

O resultado seguinte é apresentada.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a>Veja Também

[Adicionar parâmetros do que a entrada de Pipeline de processo](./adding-parameters-that-process-pipeline-input.md)

[Criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)

[Estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Como registar os Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Referência do Windows PowerShell](../windows-powershell-reference.md)

[Exemplos de cmdlet](./cmdlet-samples.md)
