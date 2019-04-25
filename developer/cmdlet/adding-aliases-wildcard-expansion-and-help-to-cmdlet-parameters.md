---
title: Adicionar Aliases, expansão de caráter universal e ajudar a parâmetros de Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: db664e589f625855b5a33a02c522d6b238ad2810
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075261"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters (Adicionar Aliases, Expansão de Carateres Universais e Ajuda a Parâmetros de Cmdlets)

Esta secção descreve como adicionar aliases, expansão de caráter universal, e mensagens de ajuda para os parâmetros do cmdlet Stop-Proc (descrito em [criar um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md)).

Este cmdlet Stop-Proc tenta parar os processos que são obtidos com o cmdlet Get-Proc (descrito em [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)).

Os tópicos nesta secção incluem o seguinte:

- [Definir o Cmdlet](#Defining-the-Cmdlet)

- [Definir parâmetros para modificação do sistema](#Defining-Parameters-for-System-Modification)

- [Definir um Alias de parâmetro](#Defining-a-Parameter-Alias)

- [Criação de ajuda para parâmetros](#Creating-Help-for-Parameters)

- [Substituir uma método de processamento de entrada](#Overriding-an-Input-Processing-Method)

- [Suporte a expansão de caráter universal](#Supporting-Wildcard-Expansion)

- [Exemplo de código](#Defining-a-Parameter-Alias)

- [Definir tipos de objeto e formatação](#Define-Object-Types-and-Formatting)

- [Criando o Cmdlet](#Building-the-Cmdlet)

- [O Cmdlet de teste](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Definir o Cmdlet

A primeira etapa na criação do cmdlet é sempre o cmdlet de nomenclatura e declarar a classe do .NET que implementa o cmdlet. Uma vez que esteja escrevendo um cmdlet para alterar o sistema, deve ser nomeado em conformidade. Uma vez que este cmdlet interrompe processos do sistema, ele usa o verbo "Stop", definido pela [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) classe, com o substantivo "Procedimento" para indicar o processo. Para obter mais informações sobre verbos aprovados cmdlet, consulte [nomes de verbo do Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

O código a seguir é a definição de classe para este cmdlet Stop-Proc.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definir parâmetros para modificação do sistema

Seu cmdlet tem de definir os parâmetros que modificações de sistema de suporte e comentários dos utilizadores. O cmdlet deve definir um `Name` parâmetro ou equivalente, para que o cmdlet irá ser capaz de modificar o sistema por algum tipo de identificador. Além disso, o cmdlet deve definir os `Force` e `PassThru` parâmetros. Para obter mais informações sobre estes parâmetros, consulte [criar um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="defining-a-parameter-alias"></a>Definir um Alias de parâmetro

Um alias de parâmetro pode ser um nome alternativo ou um bem definido nome de curto letras 1 ou 2 letras para um parâmetro de cmdlet. Em ambos os casos, o objetivo de usar aliases é simplificar a entrada de utilizador a partir da linha de comando. Windows PowerShell oferece suporte a aliases de parâmetro através da [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) atributo, que usa a sintaxe de declaração [Alias()].

O código seguinte mostra como é adicionado um alias para o `Name` parâmetro.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

Além de utilizar o [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) atributo, o tempo de execução do Windows PowerShell efetua correspondência de nome parcial, mesmo que não existem aliases são especificados. Por exemplo, se seu cmdlet tem um `FileName` parâmetro e isto é o único parâmetro que começa por `F`, o usuário poderia digitar `Filename`, `Filenam`, `File`, `Fi`, ou `F` e ainda reconhecer a entrada, como o `FileName` parâmetro.

## <a name="creating-help-for-parameters"></a>Criação de ajuda para parâmetros

Windows PowerShell permite-lhe criar ajuda para parâmetros de cmdlet. Fazer isso para qualquer parâmetro utilizado para comentários de utilizador e a modificação do sistema. Para cada parâmetro dar suporte a ajuda, pode definir o `HelpMessage` palavra-chave de atributo a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaração de atributo. Esta palavra-chave define o texto a apresentar ao utilizador para obter ajuda na utilizando o parâmetro. Também pode definir o `HelpMessageBaseName` palavra-chave para identificar o nome da base de um recurso a utilizar para a mensagem. Se definir esta palavra-chave, também tem de definir o `HelpMessageResourceId` palavra-chave para especificar o identificador de recurso.

O código a seguir deste cmdlet Stop-Proc define a `HelpMessage` palavra-chave para o atributo a `Name` parâmetro.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a>Substituir uma método de processamento de entrada

Seu cmdlet tem de substituir uma método de processamento de entrada, mais freqüentemente, isso será [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Ao modificar o sistema, o cmdlet deve chamar o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos para permitir ao utilizador para fornecer comentários antes de que é efetuada uma alteração. Para obter mais informações sobre estes métodos, consulte [criar um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="supporting-wildcard-expansion"></a>Suporte a expansão de caráter universal

Para permitir a seleção de vários objetos, pode utilizar o cmdlet do [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) e [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes para fornecer suporte de expansão de caráter universal para o parâmetro de entrada. Exemplos de padrões de carateres universais são lsa * \*. txt e [a-c]\*. Utilize o caráter de back-plica (') como um caráter de escape quando o padrão contém um caráter que deve ser utilizado literalmente.

Expansões de caráter universal de nomes de ficheiro e caminho são exemplos de cenários comuns em que o cmdlet poderá querer permitir o suporte para entradas de caminho quando é necessária a seleção de vários objetos. É um caso comum no sistema de arquivos, onde um usuário deseja ver todos os ficheiros que residem na pasta atual.

Deverá precisar de uma implementação de correspondência de padrão universal personalizado apenas raramente. Neste caso, seu cmdlet deve dar suporte a 1003.2 POSIX completo, especificação 3.13 para expansão de carateres universais ou o subconjunto de simplificada seguinte:

- **Ponto de interrogação (?).** Corresponde a qualquer caractere na localização especificada.

- **Asterisco (\*).** Corresponde a zero ou mais caracteres começando a localização especificada.

- **Parêntesis de abertura ([]).** Apresenta uma expressão de colchete padrão que pode conter caracteres ou um intervalo de caracteres. Se um intervalo for necessário, um hífen (-) é utilizado para indicar o intervalo.

- **Reto de fecho fechar (]).** Termina uma expressão de colchete padrão.

- **Back entre aspas simples caráter de escape (').** Indica que o seguinte caráter deve ser executado literalmente. Lembre-se de que ao especificar o caráter de plica de back da linha de comando (em vez de especificá-la por meio de programação), o caráter de escape aspas back tem de ser especificado duas vezes.

> [!NOTE]
> Para obter mais informações sobre padrões de carateres universais, consulte [dar suporte a curingas nos parâmetros de Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).

O código a seguir mostra como definir opções de caráter universal e definir o padrão de caráter universal usado para resolver o `Name` parâmetro para este cmdlet.

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

O código seguinte mostra como testar se o nome do processo coincide com o padrão de caráter universal definidos. Tenha em atenção que, neste caso, se o nome do processo não coincide com o padrão, o cmdlet continua na obter o nome de processo seguinte.

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>Exemplo de código

Para o completa C# código de exemplo, consulte [exemplo de StopProcessSample03](./stopprocesssample03-sample.md).

## <a name="define-object-types-and-formatting"></a>Definir tipos de objeto e formatação

Windows PowerShell passa informações entre cmdlets com objetos .net. Consequentemente, um cmdlet poderá ter de definir seu próprio tipo, ou o cmdlet poderá ter de expandir um tipo existente fornecido pelo outro cmdlet. Para obter mais informações sobre definir novos tipos ou estendendo tipos existentes, consulte [estendendo tipos de objeto e formatação](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Criando o Cmdlet

Depois de implementar um cmdlet, tem de ser registado com o Windows PowerShell através de um snap-in do Windows PowerShell. Para obter mais informações sobre como registar os cmdlets, consulte [como registrar Cmdlets, fornecedores e alojar aplicações](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>O Cmdlet de teste

Quando seu cmdlet foi registado com o Windows PowerShell, pode testá-lo executando-a na linha de comandos. Vamos testar o cmdlet Stop-Proc de exemplo. Para obter mais informações sobre como utilizar cmdlets da linha de comando, consulte a [introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Inicie o Windows PowerShell e utilize Stop-Proc para parar um processo usando o alias de ProcessName para o `Name` parâmetro.

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

O resultado seguinte é apresentada.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Verifique a entrada seguinte na linha de comandos. Uma vez que o parâmetro de nome é obrigatório, lhe for pedido para o mesmo. Introduzir "!?" Apresenta o texto da ajuda associado com o parâmetro.

    ```powershell
    PS> stop-proc
    ```

O resultado seguinte é apresentada.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- Agora que a entrada seguinte para parar todos os processos que correspondam ao padrão de caráter universal "* nota\*". É pedido antes de parar a cada processo que corresponde ao padrão.

    ```powershell
    PS> stop-proc -Name *note*
    ```

O resultado seguinte é apresentada.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

O resultado seguinte é apresentada.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

O resultado seguinte é apresentada.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Veja Também

[Criar um Cmdlet que modifique o sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Como criar um Cmdlet do Windows PowerShell](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Estendendo tipos de objeto e formatação](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Como registar os Cmdlets, fornecedores e alojar aplicações](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Suporte a curingas nos parâmetros do Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
