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
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>Adding Non-Terminating Error Reporting to Your Cmdlet (Adicionar Comunicações de Erros de Não Terminação ao seu Cmdlet)

Cmdlets podem comunicar os erros de não terminação, chamando o [System.Management.Automation.Cmdlet.WriteError][] método e continuar a funcionar no objeto de entrada ou de entrada mais objetos do pipeline.
Esta secção explica como criar um cmdlet que relatórios de erros de não terminação de seus métodos de processamento de entrada.

Para erros de não terminação (assim como erros de terminação), o cmdlet tem de passar um [System.Management.Automation.ErrorRecord][] objeto identificação do erro.
Cada registo de erro é identificado por uma cadeia exclusiva de chamada "identificador de erro".
Para além do identificador, a categoria de cada erro especificada pelo constantes definidas por um [System.Management.Automation.ErrorCategory][] enumeração.
O utilizador pode ver os erros com base na sua categoria, definindo o `$ErrorView` variável à "CategoryView".

Para obter mais informações sobre os registos de erro, consulte [registos de erros do Windows PowerShell](./windows-powershell-error-records.md).

## <a name="defining-the-cmdlet"></a>Definir o Cmdlet

A primeira etapa na criação do cmdlet é sempre o cmdlet de nomenclatura e declarar a classe do .NET que implementa o cmdlet.
Este cmdlet obtém informações do processo, portanto, o nome de verbo escolhido aqui é "Get".
(Quase qualquer tipo de cmdlet que é capaz de obtenção de informações pode processar entrada da linha de comandos). Para obter mais informações sobre verbos aprovados cmdlet, consulte [nomes de verbo do Cmdlet](approved-verbs-for-windows-powershell-commands.md).

Segue-se a definição para este cmdlet de Get-Proc.
Detalhes desta definição recebem [criando seu primeiro Cmdlet](creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a>Definição de parâmetros

Se necessário, seu cmdlet tem de definir parâmetros para o processamento de entrada.
Este cmdlet de Get-Proc define um **nome** parâmetro conforme descrito na [adicionando parâmetros essa entrada de linha de comandos do processo](adding-parameters-that-process-command-line-input.md).

Aqui é a declaração de parâmetro para o **nome** parâmetro deste cmdlet Get-Proc.

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

## <a name="overriding-input-processing-methods"></a>Substituir os métodos de processamento de entrada

Todos os cmdlets devem substituir, pelo menos, um da entrada métodos fornecidos pela processar a [System.Management.Automation.Cmdlet][] classe.
Esses métodos são discutidos [criando seu primeiro Cmdlet](creating-a-cmdlet-without-parameters.md).

> [!NOTE]
> O cmdlet deve processar cada registo de forma independente possível.

Este cmdlet de Get-Proc substitui o [System.Management.Automation.Cmdlet.ProcessRecord][] método para lidar com o **nome** o parâmetro de entrada fornecida pelo utilizador ou um script.
Este método irá obter os processos para cada nome do processo de pedido ou todos os processos se não for fornecido nenhum nome.
Detalhes desta substituição recebem [criando seu primeiro Cmdlet](creating-a-cmdlet-without-parameters.md).

### <a name="things-to-remember-when-reporting-errors"></a>Coisas a serem lembradas ao relatório de erros

O [System.Management.Automation.ErrorRecord][] de objeto que o cmdlet passa ao escrever um erro requer uma exceção em seu núcleo.
Siga as diretrizes do .NET ao determinar a exceção para utilizar.
Basicamente, se o erro semanticamente é o mesmo que uma exceção existente, o cmdlet deve utilizar ou derivar dessa exceção.
Caso contrário, ele deve derivar uma nova exceção ou uma hierarquia de exceção diretamente a partir da [System.Exception][] classe.

Durante a criação de identificadores de erro (acessados por meio da propriedade da classe ErrorRecord FullyQualifiedErrorId) tenha em atenção o seguinte.

- Utilize cadeias de caracteres que são direcionadas para fins de diagnóstico para que quando inspecionar o identificador completamente qualificado pode determinar que o erro é e onde o erro veio.

- Um identificador de formação correta de erro completamente qualificado pode ser da seguinte forma.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

Tenha em atenção que, no exemplo anterior, o identificador de erro (o token primeiro) designa o que é o erro e a parte restante indica de onde provém o erro.

- Para cenários mais complexos, o identificador de erro pode ser um token de ponto separado que pode ser analisado na inspeção.
  Isso permite que demasiado ramificar nas partes do identificador de erro, bem como a categoria de identificador e o erro de erro.

O cmdlet deve atribuir os identificadores de erro específicas para diferentes caminhos de código.
Considere as seguintes informações para a atribuição de identificadores de erro:

- Um identificador de erro deve permanecer constante ao longo do ciclo de vida do cmdlet.
  Não altere a semântica de um identificador de erro entre versões de cmdlet.

- Utilize o texto para um identificador de erro que tersely corresponde ao erro está a ser comunicado.
  Não utilize espaços em branco ou pontuação.

- Ter seu cmdlet gerar apenas os identificadores de erro que são reproduzíveis.
  Por exemplo, não deve gerar um identificador que inclui um identificador de processo.
  Identificadores de erro são úteis para um usuário apenas quando eles correspondem aos identificadores são visualizadas por outros utilizadores com o mesmo problema.

Exceções sem tratamento não são detetadas pelo PowerShell nas seguintes condições:

- Se um cmdlet cria um novo thread e o código em execução nesse thread lança uma exceção não processada, o PowerShell não capturará o erro e encerrará o processo.

- Se um objeto tiver código em seu destruidor ou métodos Dispose que faz com que uma exceção não processada, o PowerShell não capturará o erro e encerrará o processo.

## <a name="reporting-nonterminating-errors"></a>Relatório de erros de não terminação

Qualquer um da entrada de métodos de processamento pode relatar um erro de não terminação para o fluxo de saída com o [System.Management.Automation.Cmdlet.WriteError][] método.

Eis um exemplo de código deste cmdlet de Get-Proc que ilustra a chamada para [System.Management.Automation.Cmdlet.WriteError][] partir em substituição do [System.Management.Automation.Cmdlet.ProcessRecord][] método.
Neste caso, a chamada é executada se o cmdlet não consegue encontrar um processo para um identificador de processo especificado.

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

### <a name="things-to-remember-about-writing-nonterminating-errors"></a>Coisas a serem lembrados sobre a escrita de erros de não terminação

Para um erro de não terminação, o cmdlet tem de gerar um identificador de erro específico para cada objeto de entrada específico.

Um cmdlet com frequência tem de modificar a ação de PowerShell produzida por um erro de não terminação.
Ele pode fazer isso definindo a `ErrorAction` e `ErrorVariable` parâmetros.
Se definir o `ErrorAction` parâmetro, o cmdlet apresenta as opções de utilizador [System.Management.Automation.ActionPreference][], pode influenciar a ação também diretamente ao definir o `$ErrorActionPreference` variável.

O cmdlet pode salvar a erros de não terminação numa variável usando o `ErrorVariable` parâmetro, que não é afetado pela definição de `ErrorAction`.
Falhas podem ser anexadas a uma variável existente do erro ao adicionar um sinal de adição (+) para a frente do nome da variável.

## <a name="code-sample"></a>Exemplo de código

Para o completa C# código de exemplo, consulte [exemplo de GetProcessSample04](./getprocesssample04-sample.md).

## <a name="define-object-types-and-formatting"></a>Definir tipos de objeto e formatação

PowerShell passa informações entre cmdlets com objetos .NET.
Consequentemente, um cmdlet poderá ter de definir seu próprio tipo, ou o cmdlet poderá ter de expandir um tipo existente fornecido pelo outro cmdlet.
Para obter mais informações sobre definir novos tipos ou estendendo tipos existentes, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Criando o Cmdlet

Depois de implementar um cmdlet, tem de registá-lo com o Windows PowerShell através de um snap-in do Windows PowerShell.
Para obter mais informações sobre como registar os cmdlets, consulte [como registrar Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>O Cmdlet de teste

Quando seu cmdlet foi registado com o PowerShell, pode testá-lo executando-a na linha de comandos.
Vamos testar o cmdlet Get-procedimento de exemplo para ver se ele relata um erro:

- Inicie o PowerShell e utilize o cmdlet Get-Proc para obter os processos com o nome "TEST".

    ```powershell
    PS> get-proc -name test
    ```

O resultado seguinte é apresentada.

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a>Veja Também

[Adicionar parâmetros do que a entrada de Pipeline de processo](./adding-parameters-that-process-pipeline-input.md)

[Adicionar parâmetros que processam a entrada da linha de comandos](./adding-parameters-that-process-command-line-input.md)

[Criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)

[Estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Como registar os Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Referência do Windows PowerShell](../windows-powershell-reference.md)

[Exemplos de cmdlet](./cmdlet-samples.md)

[System.Exception]: /dotnet/api/System.Exception
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
