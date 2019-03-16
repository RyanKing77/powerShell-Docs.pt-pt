---
title: Criação de um Cmdlet sem parâmetros | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: c380b28570c955de6f41152fd617f5c1b0f9e4bd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054701"
---
# <a name="creating-a-cmdlet-without-parameters"></a>Creating a Cmdlet without Parameters (Criar um Cmdlet sem Parâmetros)

Esta secção descreve como criar um cmdlet que obtém informações do computador local sem o uso de parâmetros e, em seguida, escreve as informações para o pipeline. O cmdlet descrito aqui é um cmdlet de Get-Proc que obtém informações sobre os processos do computador local e, em seguida, exibe essas informações na linha de comandos.

Os tópicos nesta secção incluem o seguinte:

- [O Cmdlet de nomenclatura](#Naming-the-Cmdlet)

- [Definir a classe Cmdlet](#Defining-the-Cmdlet-Class)

- [Substituir uma método de processamento de entrada](#Overriding-an-Input-Processing-Method)

- [Exemplo de código](#Code-Sample)

- [Definir tipos de objeto e formatação](#Defining-Object-Types-and-Formatting)

- [Criando o Cmdlet](#Building-the-Cmdlet)

- [O Cmdlet de teste](#Testing-the-Cmdlet)

> [!NOTE]
> Lembre-se de que ao escrever cmdlets, os assemblies de referência Windows PowerShell® são transferidos para o disco (por predefinição em C:\Program arquivos Assemblies\Microsoft\WindowsPowerShell\v1.0). Não estiverem instalados no Cache de Assembly Global (GAC).

## <a name="naming-the-cmdlet"></a>O Cmdlet de nomenclatura

Um nome de cmdlet é constituído por um verbo que indica que a ação, o cmdlet aceita e um substantivo que indica os itens que o cmdlet age sobre. Uma vez que este cmdlet de Get-Proc de exemplo obtém objetos de processo, ele usa o verbo "Get", definido pela [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeração e o substantivo "Procedimento" para indicar que o cmdlet funciona nos itens de processo.

Quando atribuir nomes cmdlets, não use nenhum dos seguintes carateres: #, () {} [] & - / \ $;: "" <> &#124; ? @ ` .

### <a name="choosing-a-noun"></a>Escolher um substantivo

Deve escolher um substantivo específicos. É melhor usar um substantivo singular prefixado com uma versão abreviada do nome do produto. Um nome de cmdlet de exemplo deste tipo é "`Get-SQLServer`".

### <a name="choosing-a-verb"></a>Escolher um verbo

Deve usar um verbo do conjunto de nomes de verbo do cmdlet aprovados. Para obter mais informações sobre os verbos aprovados cmdlet, consulte [nomes de verbo do Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

## <a name="defining-the-cmdlet-class"></a>Definir a classe Cmdlet

Depois de escolher um nome de cmdlet, defina uma classe do .NET para implementar o cmdlet. Segue-se a definição de classe para este cmdlet de Get-procedimento de exemplo:

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

Tenha em atenção que anteriormente a definição de classe, o [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atributo, com a sintaxe `[Cmdlet(verb, noun, ...)]`, é utilizado para identificar esta classe como um cmdlet. Este é o único atributo obrigatório para todos os cmdlets e permite que o tempo de execução do Windows PowerShell para chamá-los corretamente. Pode definir palavras-chave de atributo ainda mais declarar a classe, se necessário. Lembre-se de que a declaração de atributo para nossa classe de GetProcCommand exemplo declara apenas os nome próprio e o verbo nomes para o cmdlet Get-Proc.

> [!NOTE]
> Para todas as classes de atributo do Windows PowerShell, as palavras-chave que pode definir correspondem às propriedades da classe de atributo.

Quando atribuir nomes a classe do cmdlet, é uma boa prática para refletir o nome do cmdlet do nome da classe. Para fazer isso, use o formulário "VerbNounCommand" e substitua "Verbo" e "Substantivo" com o verbo e substantivo usado no nome do cmdlet. Como é mostrado na definição de classe anterior, o cmdlet Get-procedimento de exemplo define uma classe chamada GetProcCommand, que deriva de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe base.

> [!IMPORTANT]
> Se quiser definir um cmdlet que acede diretamente ao tempo de execução do Windows PowerShell, sua classe do .NET deve derivar a partir da [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe base. Para obter mais informações sobre essa classe, consulte [criar um Cmdlet que conjuntos de parâmetros define](./adding-parameter-sets-to-a-cmdlet.md).

> [!NOTE]
> A classe para um cmdlet deve ser marcada explicitamente como pública. As classes que não estão marcadas como pública serão predefinido para interno e não serão encontradas pelo tempo de execução do Windows PowerShell.

Windows PowerShell utiliza a [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) espaço de nomes para suas classes de cmdlet. É recomendado colocar suas classes de cmdlet num espaço de nomes de comandos do seu espaço de nomes de API, por exemplo, xxx.PS.Commands.

## <a name="overriding-an-input-processing-method"></a>Substituir uma método de processamento de entrada

O [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe fornece três métodos de processamento de entrada principal, pelo menos um dos quais deve substituir seu cmdlet. Para obter mais informações sobre como o Windows PowerShell processa os registos, consulte [como o Windows PowerShell funciona](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

Para todos os tipos de entrada, o tempo de execução do Windows PowerShell chama [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) para ativar o processamento. Se seu cmdlet tem de efetuar alguns pré-processamento ou a configuração, pode fazer isso substituindo esse método.

> [!NOTE]
> Windows PowerShell utiliza o termo "Registro" para descrever o conjunto de valores de parâmetro fornecido quando é chamado um cmdlet.

Se seu cmdlet aceita entrada do pipeline, deve substituir a [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método e, opcionalmente, o [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)método. Por exemplo, um cmdlet pode substituir os dois métodos se ele reúne todas as entradas usando [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) e, em seguida, funciona sobre a entrada como um todo, em vez de um elemento por vez, como o `Sort-Object` cmdlet faz.

Se seu cmdlet não der entrada do pipeline, deve substituir a [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método. Lembre-se de que este método é frequentemente utilizado em vez de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) quando o cmdlet não é possível operar num elemento por vez, como no caso de um cmdlet de classificação.

Uma vez que este cmdlet de Get-procedimento de exemplo tem de receber entrada do pipeline, substitui o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método e utiliza as implementações predefinidas para [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) e [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing). O [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) substituição obtém processos e escreve-as para a linha de comandos utilizando o [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método.

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a>Coisas a serem lembrados sobre o processamento de entrada

- A origem de padrão para entrada é um objeto explícito (por exemplo, uma cadeia de caracteres) fornecido pelo usuário na linha de comandos. Para obter mais informações, consulte [criação de um Cmdlet para entrada de linha de comandos do processo](./adding-parameters-that-process-command-line-input.md).

- Uma método de processamento de entrada também pode receber a entrada do objeto de saída de um cmdlet a montante no pipeline. Para obter mais informações, consulte [criação de um Cmdlet para entrada de Pipeline de processo](./adding-parameters-that-process-pipeline-input.md). Tenha em atenção que seu cmdlet pode recebam entrada de uma combinação de linha de comandos e um pipeline de origens.

- O cmdlet downstream pode não devolver durante muito tempo ou nada. Por esse motivo, a entrada a processar o método no seu cmdlet não deve manter bloqueios em durante chamadas para [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especialmente os bloqueios para o qual o escopo ultrapassa a instância de cmdlet.

> [!IMPORTANT]
> Cmdlets nunca deve chamar [System.Console.Writeline*](/dotnet/api/System.Console.WriteLine) ou seu equivalente.

- Seu cmdlet pode ter variáveis de objeto a ser limpo quando terminar de processamento (por exemplo, se abrir um identificador de arquivo no [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método e mantém o identificador aberto para utilização por [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)). É importante lembrar-se de que o tempo de execução do Windows PowerShell não sempre chamar o [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método, que deve efetuar a limpeza do objeto.

Por exemplo, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) não podem ser chamados se o cmdlet foi cancelado midway ou se acabar o erro ocorre em qualquer parte do cmdlet. Por conseguinte, um cmdlet que necessita de limpeza do objeto deve implementar o concluída [System.IDisposable](/dotnet/api/System.IDisposable) padrão, incluindo o finalizador, para que o tempo de execução possa chamar ambos [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) e [System.IDisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) no final do processamento.

## <a name="code-sample"></a>Exemplo de código

Para o completa C# código de exemplo, consulte [exemplo de GetProcessSample01](./getprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir tipos de objeto e formatação

Windows PowerShell passa informações entre cmdlets com objetos .NET. Consequentemente, um cmdlet poderá ter de definir seu próprio tipo, ou o cmdlet poderá ter de expandir um tipo existente fornecido pelo outro cmdlet. Para obter mais informações sobre definir novos tipos ou estendendo tipos existentes, consulte [estendendo tipos de objeto e formatação](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Criando o Cmdlet

Depois de implementar um cmdlet, tem de registá-lo com o Windows PowerShell através de um snap-in do Windows PowerShell. Para obter mais informações sobre como registar os cmdlets, consulte [como registrar Cmdlets, fornecedores e alojar aplicações](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>O Cmdlet de teste

Quando seu cmdlet foi registado com o Windows PowerShell, pode testá-lo executando-a na linha de comandos. O código para o cmdlet de Get-Proc nosso exemplo é pequeno, mas ele ainda usa o tempo de execução do Windows PowerShell e um objeto .NET existente, que é o suficiente para torná-lo útil. Vamos testá-lo para compreender melhor o Get-Proc pode fazer e como sua saída pode ser utilizada. Para obter mais informações sobre como utilizar cmdlets da linha de comando, consulte a [introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

1. Inicie o Windows PowerShell e obtenha os processos atuais em execução no computador.

    ```powershell
    get-proc
    ```

    O resultado seguinte é apresentada.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. Atribua uma variável para os resultados do cmdlet para facilitar a manipulação.

    ```powershell
    $p=get-proc
    ```

3. Obter o número de processos.

    ```powershell
    $p.length
    ```

    O resultado seguinte é apresentada.

    ```output
    63
    ```

4. Obter um processo específico.

    ```powershell
    $p[6]
    ```

    O resultado seguinte é apresentada.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. Obter a hora de início deste processo.

    ```powershell
    $p[6].starttime
    ```

    O resultado seguinte é apresentada.

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. Obtenha os processos para o qual a contagem de identificador é superior a 500 e ordenar o resultado.

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    O resultado seguinte é apresentada.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. Utilize o `Get-Member` cmdlet para listar as propriedades disponíveis para cada processo.

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    O resultado seguinte é apresentada.

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a>Veja Também

[Criação de um Cmdlet para processar a entrada de linha de comandos](./adding-parameters-that-process-command-line-input.md)

[Criação de um Cmdlet para processar a entrada do Pipeline](./adding-parameters-that-process-pipeline-input.md)

[Como criar um Cmdlet do Windows PowerShell](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Estendendo tipos de objeto e formatação](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Como funciona o Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Como registar os Cmdlets, fornecedores e alojar aplicações](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Referência do Windows PowerShell](../windows-powershell-reference.md)

[Exemplos de cmdlet](./cmdlet-samples.md)