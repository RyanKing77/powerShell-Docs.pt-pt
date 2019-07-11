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
ms.openlocfilehash: bc921537062e35aa203fa3ee95d3b7211c89cb28
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733842"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="7a723-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters (Adicionar Aliases, Expansão de Carateres Universais e Ajuda a Parâmetros de Cmdlets)</span><span class="sxs-lookup"><span data-stu-id="7a723-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="7a723-103">Esta secção descreve como adicionar aliases, expansão de caráter universal, e mensagens de ajuda para os parâmetros do cmdlet Stop-Proc (descrito em [criar um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="7a723-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="7a723-104">Este cmdlet Stop-Proc tenta parar os processos que são obtidos com o cmdlet Get-Proc (descrito em [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="7a723-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="7a723-105">Definir o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7a723-105">Defining the Cmdlet</span></span>

<span data-ttu-id="7a723-106">A primeira etapa na criação do cmdlet é sempre o cmdlet de nomenclatura e declarar a classe do .NET que implementa o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7a723-106">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="7a723-107">Uma vez que esteja escrevendo um cmdlet para alterar o sistema, deve ser nomeado em conformidade.</span><span class="sxs-lookup"><span data-stu-id="7a723-107">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="7a723-108">Uma vez que este cmdlet interrompe processos do sistema, ele usa o verbo "Stop", definido pela [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) classe, com o substantivo "Procedimento" para indicar o processo.</span><span class="sxs-lookup"><span data-stu-id="7a723-108">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="7a723-109">Para obter mais informações sobre verbos aprovados cmdlet, consulte [nomes de verbo do Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="7a723-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="7a723-110">O código a seguir é a definição de classe para este cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="7a723-110">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="7a723-111">Definir parâmetros para modificação do sistema</span><span class="sxs-lookup"><span data-stu-id="7a723-111">Defining Parameters for System Modification</span></span>

<span data-ttu-id="7a723-112">Seu cmdlet tem de definir os parâmetros que modificações de sistema de suporte e comentários dos utilizadores.</span><span class="sxs-lookup"><span data-stu-id="7a723-112">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="7a723-113">O cmdlet deve definir um `Name` parâmetro ou equivalente, para que o cmdlet irá ser capaz de modificar o sistema por algum tipo de identificador.</span><span class="sxs-lookup"><span data-stu-id="7a723-113">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="7a723-114">Além disso, o cmdlet deve definir os `Force` e `PassThru` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7a723-114">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="7a723-115">Para obter mais informações sobre estes parâmetros, consulte [criar um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="7a723-115">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="7a723-116">Definir um Alias de parâmetro</span><span class="sxs-lookup"><span data-stu-id="7a723-116">Defining a Parameter Alias</span></span>

<span data-ttu-id="7a723-117">Um alias de parâmetro pode ser um nome alternativo ou um bem definido nome de curto letras 1 ou 2 letras para um parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7a723-117">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="7a723-118">Em ambos os casos, o objetivo de usar aliases é simplificar a entrada de utilizador a partir da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="7a723-118">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="7a723-119">Windows PowerShell oferece suporte a aliases de parâmetro através da [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) atributo, que usa a sintaxe de declaração [Alias()].</span><span class="sxs-lookup"><span data-stu-id="7a723-119">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="7a723-120">O código seguinte mostra como é adicionado um alias para o `Name` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7a723-120">The following code shows how an alias is added to the `Name` parameter.</span></span>

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

<span data-ttu-id="7a723-121">Além de utilizar o [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) atributo, o tempo de execução do Windows PowerShell efetua correspondência de nome parcial, mesmo que não existem aliases são especificados.</span><span class="sxs-lookup"><span data-stu-id="7a723-121">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="7a723-122">Por exemplo, se seu cmdlet tem um `FileName` parâmetro e isto é o único parâmetro que começa por `F`, o usuário poderia digitar `Filename`, `Filenam`, `File`, `Fi`, ou `F` e ainda reconhecer a entrada, como o `FileName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7a723-122">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="7a723-123">Criação de ajuda para parâmetros</span><span class="sxs-lookup"><span data-stu-id="7a723-123">Creating Help for Parameters</span></span>

<span data-ttu-id="7a723-124">Windows PowerShell permite-lhe criar ajuda para parâmetros de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7a723-124">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="7a723-125">Fazer isso para qualquer parâmetro utilizado para comentários de utilizador e a modificação do sistema.</span><span class="sxs-lookup"><span data-stu-id="7a723-125">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="7a723-126">Para cada parâmetro dar suporte a ajuda, pode definir o `HelpMessage` palavra-chave de atributo a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaração de atributo.</span><span class="sxs-lookup"><span data-stu-id="7a723-126">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="7a723-127">Esta palavra-chave define o texto a apresentar ao utilizador para obter ajuda na utilizando o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7a723-127">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="7a723-128">Também pode definir o `HelpMessageBaseName` palavra-chave para identificar o nome da base de um recurso a utilizar para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="7a723-128">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="7a723-129">Se definir esta palavra-chave, também tem de definir o `HelpMessageResourceId` palavra-chave para especificar o identificador de recurso.</span><span class="sxs-lookup"><span data-stu-id="7a723-129">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="7a723-130">O código a seguir deste cmdlet Stop-Proc define a `HelpMessage` palavra-chave para o atributo a `Name` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7a723-130">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="7a723-131">Substituir uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="7a723-131">Overriding an Input Processing Method</span></span>

<span data-ttu-id="7a723-132">Seu cmdlet tem de substituir uma método de processamento de entrada, mais freqüentemente, isso será [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="7a723-132">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="7a723-133">Ao modificar o sistema, o cmdlet deve chamar o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos para permitir ao utilizador para fornecer comentários antes de que é efetuada uma alteração.</span><span class="sxs-lookup"><span data-stu-id="7a723-133">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="7a723-134">Para obter mais informações sobre estes métodos, consulte [criar um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="7a723-134">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="7a723-135">Suporte a expansão de caráter universal</span><span class="sxs-lookup"><span data-stu-id="7a723-135">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="7a723-136">Para permitir a seleção de vários objetos, pode utilizar o cmdlet do [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) e [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes para fornecer suporte de expansão de caráter universal para o parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="7a723-136">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="7a723-137">Exemplos de padrões de carateres universais são lsa \* \*. txt e [a-c]\*.</span><span class="sxs-lookup"><span data-stu-id="7a723-137">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="7a723-138">Utilize o caráter de back-plica (') como um caráter de escape quando o padrão contém um caráter que deve ser utilizado literalmente.</span><span class="sxs-lookup"><span data-stu-id="7a723-138">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="7a723-139">Expansões de caráter universal de nomes de ficheiro e caminho são exemplos de cenários comuns em que o cmdlet poderá querer permitir o suporte para entradas de caminho quando é necessária a seleção de vários objetos.</span><span class="sxs-lookup"><span data-stu-id="7a723-139">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="7a723-140">É um caso comum no sistema de arquivos, onde um usuário deseja ver todos os ficheiros que residem na pasta atual.</span><span class="sxs-lookup"><span data-stu-id="7a723-140">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="7a723-141">Deverá precisar de uma implementação de correspondência de padrão universal personalizado apenas raramente.</span><span class="sxs-lookup"><span data-stu-id="7a723-141">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="7a723-142">Neste caso, seu cmdlet deve dar suporte a 1003.2 POSIX completo, especificação 3.13 para expansão de carateres universais ou o subconjunto de simplificada seguinte:</span><span class="sxs-lookup"><span data-stu-id="7a723-142">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="7a723-143">**Ponto de interrogação (?).**</span><span class="sxs-lookup"><span data-stu-id="7a723-143">**Question mark (?).**</span></span> <span data-ttu-id="7a723-144">Corresponde a qualquer caractere na localização especificada.</span><span class="sxs-lookup"><span data-stu-id="7a723-144">Matches any character at the specified location.</span></span>

- <span data-ttu-id="7a723-145">**Asterisco (\*).**</span><span class="sxs-lookup"><span data-stu-id="7a723-145">**Asterisk (\*).**</span></span> <span data-ttu-id="7a723-146">Corresponde a zero ou mais caracteres começando a localização especificada.</span><span class="sxs-lookup"><span data-stu-id="7a723-146">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="7a723-147">**Parêntesis de abertura ([]).**</span><span class="sxs-lookup"><span data-stu-id="7a723-147">**Open bracket ([).**</span></span> <span data-ttu-id="7a723-148">Apresenta uma expressão de colchete padrão que pode conter caracteres ou um intervalo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7a723-148">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="7a723-149">Se um intervalo for necessário, um hífen (-) é utilizado para indicar o intervalo.</span><span class="sxs-lookup"><span data-stu-id="7a723-149">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="7a723-150">**Reto de fecho fechar (]).**</span><span class="sxs-lookup"><span data-stu-id="7a723-150">**Close bracket (]).**</span></span> <span data-ttu-id="7a723-151">Termina uma expressão de colchete padrão.</span><span class="sxs-lookup"><span data-stu-id="7a723-151">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="7a723-152">**Back entre aspas simples caráter de escape (').**</span><span class="sxs-lookup"><span data-stu-id="7a723-152">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="7a723-153">Indica que o seguinte caráter deve ser executado literalmente.</span><span class="sxs-lookup"><span data-stu-id="7a723-153">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="7a723-154">Lembre-se de que ao especificar o caráter de plica de back da linha de comando (em vez de especificá-la por meio de programação), o caráter de escape aspas back tem de ser especificado duas vezes.</span><span class="sxs-lookup"><span data-stu-id="7a723-154">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="7a723-155">Para obter mais informações sobre padrões de carateres universais, consulte [dar suporte a curingas nos parâmetros de Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="7a723-155">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="7a723-156">O código a seguir mostra como definir opções de caráter universal e definir o padrão de caráter universal usado para resolver o `Name` parâmetro para este cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7a723-156">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="7a723-157">O código seguinte mostra como testar se o nome do processo coincide com o padrão de caráter universal definidos.</span><span class="sxs-lookup"><span data-stu-id="7a723-157">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="7a723-158">Tenha em atenção que, neste caso, se o nome do processo não coincide com o padrão, o cmdlet continua na obter o nome de processo seguinte.</span><span class="sxs-lookup"><span data-stu-id="7a723-158">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="7a723-159">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="7a723-159">Code Sample</span></span>

<span data-ttu-id="7a723-160">Para o completa C# código de exemplo, consulte [exemplo de StopProcessSample03](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="7a723-160">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="7a723-161">Definir tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="7a723-161">Define Object Types and Formatting</span></span>

<span data-ttu-id="7a723-162">Windows PowerShell passa informações entre cmdlets com objetos .net.</span><span class="sxs-lookup"><span data-stu-id="7a723-162">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="7a723-163">Consequentemente, um cmdlet poderá ter de definir seu próprio tipo, ou o cmdlet poderá ter de expandir um tipo existente fornecido pelo outro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7a723-163">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="7a723-164">Para obter mais informações sobre definir novos tipos ou estendendo tipos existentes, consulte [estendendo tipos de objeto e formatação](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="7a723-164">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="7a723-165">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7a723-165">Building the Cmdlet</span></span>

<span data-ttu-id="7a723-166">Depois de implementar um cmdlet, tem de ser registado com o Windows PowerShell através de um snap-in do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a723-166">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="7a723-167">Para obter mais informações sobre como registar os cmdlets, consulte [como registrar Cmdlets, fornecedores e alojar aplicações](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="7a723-167">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="7a723-168">O Cmdlet de teste</span><span class="sxs-lookup"><span data-stu-id="7a723-168">Testing the Cmdlet</span></span>

<span data-ttu-id="7a723-169">Quando seu cmdlet foi registado com o Windows PowerShell, pode testá-lo executando-a na linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="7a723-169">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="7a723-170">Vamos testar o cmdlet Stop-Proc de exemplo.</span><span class="sxs-lookup"><span data-stu-id="7a723-170">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="7a723-171">Para obter mais informações sobre como utilizar cmdlets da linha de comando, consulte a [introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="7a723-171">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="7a723-172">Inicie o Windows PowerShell e utilize Stop-Proc para parar um processo usando o alias de ProcessName para o `Name` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7a723-172">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="7a723-173">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="7a723-173">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="7a723-174">Verifique a entrada seguinte na linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="7a723-174">Make the following entry on the command line.</span></span> <span data-ttu-id="7a723-175">Uma vez que o parâmetro de nome é obrigatório, lhe for pedido para o mesmo.</span><span class="sxs-lookup"><span data-stu-id="7a723-175">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="7a723-176">Introduzir "!?"</span><span class="sxs-lookup"><span data-stu-id="7a723-176">Entering "!?"</span></span> <span data-ttu-id="7a723-177">Apresenta o texto da ajuda associado com o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7a723-177">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="7a723-178">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="7a723-178">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="7a723-179">Agora que a entrada seguinte para parar todos os processos que correspondam ao padrão de caráter universal "\* nota\*".</span><span class="sxs-lookup"><span data-stu-id="7a723-179">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="7a723-180">É pedido antes de parar a cada processo que corresponde ao padrão.</span><span class="sxs-lookup"><span data-stu-id="7a723-180">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="7a723-181">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="7a723-181">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="7a723-182">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="7a723-182">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="7a723-183">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="7a723-183">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="7a723-184">Veja Também</span><span class="sxs-lookup"><span data-stu-id="7a723-184">See Also</span></span>

[<span data-ttu-id="7a723-185">Criar um Cmdlet que modifique o sistema</span><span class="sxs-lookup"><span data-stu-id="7a723-185">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="7a723-186">Como criar um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a723-186">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="7a723-187">[Estendendo tipos de objeto e formatação](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="7a723-187">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="7a723-188">[Como registar os Cmdlets, fornecedores e alojar aplicações](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="7a723-188">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="7a723-189">Suporte a curingas nos parâmetros do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7a723-189">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="7a723-190">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a723-190">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
