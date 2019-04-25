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
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="740ee-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters (Adicionar Aliases, Expansão de Carateres Universais e Ajuda a Parâmetros de Cmdlets)</span><span class="sxs-lookup"><span data-stu-id="740ee-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="740ee-103">Esta secção descreve como adicionar aliases, expansão de caráter universal, e mensagens de ajuda para os parâmetros do cmdlet Stop-Proc (descrito em [criar um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="740ee-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="740ee-104">Este cmdlet Stop-Proc tenta parar os processos que são obtidos com o cmdlet Get-Proc (descrito em [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="740ee-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="740ee-105">Os tópicos nesta secção incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="740ee-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="740ee-106">Definir o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="740ee-106">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="740ee-107">Definir parâmetros para modificação do sistema</span><span class="sxs-lookup"><span data-stu-id="740ee-107">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="740ee-108">Definir um Alias de parâmetro</span><span class="sxs-lookup"><span data-stu-id="740ee-108">Defining a Parameter Alias</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="740ee-109">Criação de ajuda para parâmetros</span><span class="sxs-lookup"><span data-stu-id="740ee-109">Creating Help for Parameters</span></span>](#Creating-Help-for-Parameters)

- [<span data-ttu-id="740ee-110">Substituir uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="740ee-110">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="740ee-111">Suporte a expansão de caráter universal</span><span class="sxs-lookup"><span data-stu-id="740ee-111">Supporting Wildcard Expansion</span></span>](#Supporting-Wildcard-Expansion)

- [<span data-ttu-id="740ee-112">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="740ee-112">Code Sample</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="740ee-113">Definir tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="740ee-113">Defining Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="740ee-114">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="740ee-114">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="740ee-115">O Cmdlet de teste</span><span class="sxs-lookup"><span data-stu-id="740ee-115">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="740ee-116">Definir o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="740ee-116">Defining the Cmdlet</span></span>

<span data-ttu-id="740ee-117">A primeira etapa na criação do cmdlet é sempre o cmdlet de nomenclatura e declarar a classe do .NET que implementa o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="740ee-117">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="740ee-118">Uma vez que esteja escrevendo um cmdlet para alterar o sistema, deve ser nomeado em conformidade.</span><span class="sxs-lookup"><span data-stu-id="740ee-118">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="740ee-119">Uma vez que este cmdlet interrompe processos do sistema, ele usa o verbo "Stop", definido pela [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) classe, com o substantivo "Procedimento" para indicar o processo.</span><span class="sxs-lookup"><span data-stu-id="740ee-119">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="740ee-120">Para obter mais informações sobre verbos aprovados cmdlet, consulte [nomes de verbo do Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="740ee-120">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="740ee-121">O código a seguir é a definição de classe para este cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="740ee-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="740ee-122">Definir parâmetros para modificação do sistema</span><span class="sxs-lookup"><span data-stu-id="740ee-122">Defining Parameters for System Modification</span></span>

<span data-ttu-id="740ee-123">Seu cmdlet tem de definir os parâmetros que modificações de sistema de suporte e comentários dos utilizadores.</span><span class="sxs-lookup"><span data-stu-id="740ee-123">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="740ee-124">O cmdlet deve definir um `Name` parâmetro ou equivalente, para que o cmdlet irá ser capaz de modificar o sistema por algum tipo de identificador.</span><span class="sxs-lookup"><span data-stu-id="740ee-124">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="740ee-125">Além disso, o cmdlet deve definir os `Force` e `PassThru` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="740ee-125">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="740ee-126">Para obter mais informações sobre estes parâmetros, consulte [criar um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="740ee-126">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="740ee-127">Definir um Alias de parâmetro</span><span class="sxs-lookup"><span data-stu-id="740ee-127">Defining a Parameter Alias</span></span>

<span data-ttu-id="740ee-128">Um alias de parâmetro pode ser um nome alternativo ou um bem definido nome de curto letras 1 ou 2 letras para um parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="740ee-128">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="740ee-129">Em ambos os casos, o objetivo de usar aliases é simplificar a entrada de utilizador a partir da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="740ee-129">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="740ee-130">Windows PowerShell oferece suporte a aliases de parâmetro através da [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) atributo, que usa a sintaxe de declaração [Alias()].</span><span class="sxs-lookup"><span data-stu-id="740ee-130">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="740ee-131">O código seguinte mostra como é adicionado um alias para o `Name` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="740ee-131">The following code shows how an alias is added to the `Name` parameter.</span></span>

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

<span data-ttu-id="740ee-132">Além de utilizar o [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) atributo, o tempo de execução do Windows PowerShell efetua correspondência de nome parcial, mesmo que não existem aliases são especificados.</span><span class="sxs-lookup"><span data-stu-id="740ee-132">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="740ee-133">Por exemplo, se seu cmdlet tem um `FileName` parâmetro e isto é o único parâmetro que começa por `F`, o usuário poderia digitar `Filename`, `Filenam`, `File`, `Fi`, ou `F` e ainda reconhecer a entrada, como o `FileName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="740ee-133">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="740ee-134">Criação de ajuda para parâmetros</span><span class="sxs-lookup"><span data-stu-id="740ee-134">Creating Help for Parameters</span></span>

<span data-ttu-id="740ee-135">Windows PowerShell permite-lhe criar ajuda para parâmetros de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="740ee-135">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="740ee-136">Fazer isso para qualquer parâmetro utilizado para comentários de utilizador e a modificação do sistema.</span><span class="sxs-lookup"><span data-stu-id="740ee-136">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="740ee-137">Para cada parâmetro dar suporte a ajuda, pode definir o `HelpMessage` palavra-chave de atributo a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaração de atributo.</span><span class="sxs-lookup"><span data-stu-id="740ee-137">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="740ee-138">Esta palavra-chave define o texto a apresentar ao utilizador para obter ajuda na utilizando o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="740ee-138">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="740ee-139">Também pode definir o `HelpMessageBaseName` palavra-chave para identificar o nome da base de um recurso a utilizar para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="740ee-139">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="740ee-140">Se definir esta palavra-chave, também tem de definir o `HelpMessageResourceId` palavra-chave para especificar o identificador de recurso.</span><span class="sxs-lookup"><span data-stu-id="740ee-140">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="740ee-141">O código a seguir deste cmdlet Stop-Proc define a `HelpMessage` palavra-chave para o atributo a `Name` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="740ee-141">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="740ee-142">Substituir uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="740ee-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="740ee-143">Seu cmdlet tem de substituir uma método de processamento de entrada, mais freqüentemente, isso será [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="740ee-143">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="740ee-144">Ao modificar o sistema, o cmdlet deve chamar o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos para permitir ao utilizador para fornecer comentários antes de que é efetuada uma alteração.</span><span class="sxs-lookup"><span data-stu-id="740ee-144">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="740ee-145">Para obter mais informações sobre estes métodos, consulte [criar um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="740ee-145">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="740ee-146">Suporte a expansão de caráter universal</span><span class="sxs-lookup"><span data-stu-id="740ee-146">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="740ee-147">Para permitir a seleção de vários objetos, pode utilizar o cmdlet do [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) e [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes para fornecer suporte de expansão de caráter universal para o parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="740ee-147">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="740ee-148">Exemplos de padrões de carateres universais são lsa \* \*. txt e [a-c]\*.</span><span class="sxs-lookup"><span data-stu-id="740ee-148">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="740ee-149">Utilize o caráter de back-plica (') como um caráter de escape quando o padrão contém um caráter que deve ser utilizado literalmente.</span><span class="sxs-lookup"><span data-stu-id="740ee-149">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="740ee-150">Expansões de caráter universal de nomes de ficheiro e caminho são exemplos de cenários comuns em que o cmdlet poderá querer permitir o suporte para entradas de caminho quando é necessária a seleção de vários objetos.</span><span class="sxs-lookup"><span data-stu-id="740ee-150">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="740ee-151">É um caso comum no sistema de arquivos, onde um usuário deseja ver todos os ficheiros que residem na pasta atual.</span><span class="sxs-lookup"><span data-stu-id="740ee-151">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="740ee-152">Deverá precisar de uma implementação de correspondência de padrão universal personalizado apenas raramente.</span><span class="sxs-lookup"><span data-stu-id="740ee-152">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="740ee-153">Neste caso, seu cmdlet deve dar suporte a 1003.2 POSIX completo, especificação 3.13 para expansão de carateres universais ou o subconjunto de simplificada seguinte:</span><span class="sxs-lookup"><span data-stu-id="740ee-153">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="740ee-154">**Ponto de interrogação (?).**</span><span class="sxs-lookup"><span data-stu-id="740ee-154">**Question mark (?).**</span></span> <span data-ttu-id="740ee-155">Corresponde a qualquer caractere na localização especificada.</span><span class="sxs-lookup"><span data-stu-id="740ee-155">Matches any character at the specified location.</span></span>

- <span data-ttu-id="740ee-156">**Asterisco (\*).**</span><span class="sxs-lookup"><span data-stu-id="740ee-156">**Asterisk (\*).**</span></span> <span data-ttu-id="740ee-157">Corresponde a zero ou mais caracteres começando a localização especificada.</span><span class="sxs-lookup"><span data-stu-id="740ee-157">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="740ee-158">**Parêntesis de abertura ([]).**</span><span class="sxs-lookup"><span data-stu-id="740ee-158">**Open bracket ([).**</span></span> <span data-ttu-id="740ee-159">Apresenta uma expressão de colchete padrão que pode conter caracteres ou um intervalo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="740ee-159">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="740ee-160">Se um intervalo for necessário, um hífen (-) é utilizado para indicar o intervalo.</span><span class="sxs-lookup"><span data-stu-id="740ee-160">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="740ee-161">**Reto de fecho fechar (]).**</span><span class="sxs-lookup"><span data-stu-id="740ee-161">**Close bracket (]).**</span></span> <span data-ttu-id="740ee-162">Termina uma expressão de colchete padrão.</span><span class="sxs-lookup"><span data-stu-id="740ee-162">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="740ee-163">**Back entre aspas simples caráter de escape (').**</span><span class="sxs-lookup"><span data-stu-id="740ee-163">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="740ee-164">Indica que o seguinte caráter deve ser executado literalmente.</span><span class="sxs-lookup"><span data-stu-id="740ee-164">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="740ee-165">Lembre-se de que ao especificar o caráter de plica de back da linha de comando (em vez de especificá-la por meio de programação), o caráter de escape aspas back tem de ser especificado duas vezes.</span><span class="sxs-lookup"><span data-stu-id="740ee-165">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="740ee-166">Para obter mais informações sobre padrões de carateres universais, consulte [dar suporte a curingas nos parâmetros de Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="740ee-166">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="740ee-167">O código a seguir mostra como definir opções de caráter universal e definir o padrão de caráter universal usado para resolver o `Name` parâmetro para este cmdlet.</span><span class="sxs-lookup"><span data-stu-id="740ee-167">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="740ee-168">O código seguinte mostra como testar se o nome do processo coincide com o padrão de caráter universal definidos.</span><span class="sxs-lookup"><span data-stu-id="740ee-168">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="740ee-169">Tenha em atenção que, neste caso, se o nome do processo não coincide com o padrão, o cmdlet continua na obter o nome de processo seguinte.</span><span class="sxs-lookup"><span data-stu-id="740ee-169">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="740ee-170">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="740ee-170">Code Sample</span></span>

<span data-ttu-id="740ee-171">Para o completa C# código de exemplo, consulte [exemplo de StopProcessSample03](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="740ee-171">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="740ee-172">Definir tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="740ee-172">Define Object Types and Formatting</span></span>

<span data-ttu-id="740ee-173">Windows PowerShell passa informações entre cmdlets com objetos .net.</span><span class="sxs-lookup"><span data-stu-id="740ee-173">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="740ee-174">Consequentemente, um cmdlet poderá ter de definir seu próprio tipo, ou o cmdlet poderá ter de expandir um tipo existente fornecido pelo outro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="740ee-174">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="740ee-175">Para obter mais informações sobre definir novos tipos ou estendendo tipos existentes, consulte [estendendo tipos de objeto e formatação](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="740ee-175">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="740ee-176">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="740ee-176">Building the Cmdlet</span></span>

<span data-ttu-id="740ee-177">Depois de implementar um cmdlet, tem de ser registado com o Windows PowerShell através de um snap-in do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="740ee-177">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="740ee-178">Para obter mais informações sobre como registar os cmdlets, consulte [como registrar Cmdlets, fornecedores e alojar aplicações](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="740ee-178">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="740ee-179">O Cmdlet de teste</span><span class="sxs-lookup"><span data-stu-id="740ee-179">Testing the Cmdlet</span></span>

<span data-ttu-id="740ee-180">Quando seu cmdlet foi registado com o Windows PowerShell, pode testá-lo executando-a na linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="740ee-180">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="740ee-181">Vamos testar o cmdlet Stop-Proc de exemplo.</span><span class="sxs-lookup"><span data-stu-id="740ee-181">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="740ee-182">Para obter mais informações sobre como utilizar cmdlets da linha de comando, consulte a [introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="740ee-182">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="740ee-183">Inicie o Windows PowerShell e utilize Stop-Proc para parar um processo usando o alias de ProcessName para o `Name` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="740ee-183">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="740ee-184">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="740ee-184">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="740ee-185">Verifique a entrada seguinte na linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="740ee-185">Make the following entry on the command line.</span></span> <span data-ttu-id="740ee-186">Uma vez que o parâmetro de nome é obrigatório, lhe for pedido para o mesmo.</span><span class="sxs-lookup"><span data-stu-id="740ee-186">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="740ee-187">Introduzir "!?"</span><span class="sxs-lookup"><span data-stu-id="740ee-187">Entering "!?"</span></span> <span data-ttu-id="740ee-188">Apresenta o texto da ajuda associado com o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="740ee-188">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="740ee-189">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="740ee-189">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="740ee-190">Agora que a entrada seguinte para parar todos os processos que correspondam ao padrão de caráter universal "\* nota\*".</span><span class="sxs-lookup"><span data-stu-id="740ee-190">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="740ee-191">É pedido antes de parar a cada processo que corresponde ao padrão.</span><span class="sxs-lookup"><span data-stu-id="740ee-191">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="740ee-192">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="740ee-192">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="740ee-193">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="740ee-193">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="740ee-194">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="740ee-194">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="740ee-195">Veja Também</span><span class="sxs-lookup"><span data-stu-id="740ee-195">See Also</span></span>

[<span data-ttu-id="740ee-196">Criar um Cmdlet que modifique o sistema</span><span class="sxs-lookup"><span data-stu-id="740ee-196">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="740ee-197">Como criar um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="740ee-197">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="740ee-198">Estendendo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="740ee-198">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="740ee-199">Como registar os Cmdlets, fornecedores e alojar aplicações</span><span class="sxs-lookup"><span data-stu-id="740ee-199">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="740ee-200">Suporte a curingas nos parâmetros do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="740ee-200">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="740ee-201">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="740ee-201">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
