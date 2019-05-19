---
title: Criação de um Cmdlet para aceder a um Store de dados | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea15e00e-20dc-4209-9e97-9ffd763e5d97
caps.latest.revision: 8
ms.openlocfilehash: 8d7ba9d122e90b80f6009b6dc8e8e3bb07331e4a
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854841"
---
# <a name="creating-a-cmdlet-to-access-a-data-store"></a><span data-ttu-id="ca281-102">Creating a Cmdlet to Access a Data Store (Criar um Cmdlet para Aceder a um Arquivo de Dados)</span><span class="sxs-lookup"><span data-stu-id="ca281-102">Creating a Cmdlet to Access a Data Store</span></span>

<span data-ttu-id="ca281-103">Esta secção descreve como criar um cmdlet que acede aos dados armazenados por meio de um fornecedor de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca281-103">This section describes how to create a cmdlet that accesses stored data by way of a Windows PowerShell provider.</span></span> <span data-ttu-id="ca281-104">Este tipo de cmdlet utiliza a infraestrutura de fornecedor de Windows PowerShell de tempo de execução do Windows PowerShell e, portanto, a classe cmdlet deve ser derivados da [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe base.</span><span class="sxs-lookup"><span data-stu-id="ca281-104">This type of cmdlet uses the Windows PowerShell provider infrastructure of the Windows PowerShell runtime and, therefore, the cmdlet class must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span>

<span data-ttu-id="ca281-105">O cmdlet Select-Str descrito aqui pode localizar e selecionar cadeias de caracteres num arquivo ou o objeto.</span><span class="sxs-lookup"><span data-stu-id="ca281-105">The Select-Str cmdlet described here can locate and select strings in a file or object.</span></span> <span data-ttu-id="ca281-106">Os padrões usados para identificar a cadeia de caracteres podem ser especificados explicitamente através da `Path` parâmetro do cmdlet ou implicitamente através da `Script` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ca281-106">The patterns used to identify the string can be specified explicitly through the `Path` parameter of the cmdlet or implicitly through the `Script` parameter.</span></span>

<span data-ttu-id="ca281-107">O cmdlet foi projetado para usar um fornecedor de Windows PowerShell que deriva [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider).</span><span class="sxs-lookup"><span data-stu-id="ca281-107">The cmdlet is designed to use any Windows PowerShell provider that derives from [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider).</span></span> <span data-ttu-id="ca281-108">Por exemplo, o cmdlet pode especificar o fornecedor do sistema de ficheiros ou o fornecedor de variável que é fornecido pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca281-108">For example, the cmdlet can specify the FileSystem provider or the Variable provider that is provided by Windows PowerShell.</span></span> <span data-ttu-id="ca281-109">Para obter mais informações aboutWindows provedores PowerShell, consulte [fornecedor do PowerShell para estruturar Your Windows](../prog-guide/designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="ca281-109">For more information aboutWindows PowerShell providers, see [Designing Your Windows PowerShell provider](../prog-guide/designing-your-windows-powershell-provider.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="ca281-110">Definir a classe Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ca281-110">Defining the Cmdlet Class</span></span>

<span data-ttu-id="ca281-111">A primeira etapa na criação do cmdlet é sempre o cmdlet de nomenclatura e declarar a classe do .NET que implementa o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ca281-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="ca281-112">Este cmdlet Deteta determinadas cadeias de caracteres, portanto, o nome de verbo escolhido aqui é "Select", definido pela [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) classe.</span><span class="sxs-lookup"><span data-stu-id="ca281-112">This cmdlet detects certain strings, so the verb name chosen here is "Select", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) class.</span></span> <span data-ttu-id="ca281-113">O nome do substantivo "Str" é utilizado porque o cmdlet age sobre cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ca281-113">The noun name "Str" is used because the cmdlet acts upon strings.</span></span> <span data-ttu-id="ca281-114">Na declaração abaixo, tenha em atenção que o nome de verbo e substantivo do cmdlet são refletidas no nome da classe de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ca281-114">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span> <span data-ttu-id="ca281-115">Para obter mais informações sobre verbos aprovados cmdlet, consulte [nomes de verbo do Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="ca281-115">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="ca281-116">A classe do .NET para este cmdlet deve ser derivados da [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe, de base, porque fornece o suporte necessário para o tempo de execução do Windows PowerShell para expor o fornecedor de Windows PowerShell infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="ca281-116">The .NET class for this cmdlet must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class, because it provides the support needed by the Windows PowerShell runtime to expose the Windows PowerShell provider infrastructure.</span></span> <span data-ttu-id="ca281-117">Tenha em atenção que este cmdlet também é usar as classes de expressões regulares do .NET Framework, como [System.Text.Regularexpressions.Regex](/dotnet/api/System.Text.RegularExpressions.Regex).</span><span class="sxs-lookup"><span data-stu-id="ca281-117">Note that this cmdlet also makes use of the .NET Framework regular expressions classes, such as [System.Text.Regularexpressions.Regex](/dotnet/api/System.Text.RegularExpressions.Regex).</span></span>

<span data-ttu-id="ca281-118">O código a seguir é a definição de classe para este cmdlet Select-Str.</span><span class="sxs-lookup"><span data-stu-id="ca281-118">The following code is the class definition for this Select-Str cmdlet.</span></span>

```csharp
[Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
public class SelectStringCommand : PSCmdlet
```

<span data-ttu-id="ca281-119">Este cmdlet define um parâmetro predefinido definido adicionando o `DefaultParameterSetName` palavra-chave de atributo para a declaração da classe.</span><span class="sxs-lookup"><span data-stu-id="ca281-119">This cmdlet defines a default parameter set by adding the `DefaultParameterSetName` attribute keyword to the class declaration.</span></span> <span data-ttu-id="ca281-120">O conjunto de parâmetros predefinidos `PatternParameterSet` é utilizado quando o `Script` parâmetro não for especificado.</span><span class="sxs-lookup"><span data-stu-id="ca281-120">The default parameter set `PatternParameterSet` is used when the `Script` parameter is not specified.</span></span> <span data-ttu-id="ca281-121">Para obter mais informações sobre este conjunto de parâmetros, consulte a `Pattern` e `Script` discussão de parâmetro na secção seguinte.</span><span class="sxs-lookup"><span data-stu-id="ca281-121">For more information about this parameter set, see the `Pattern` and `Script` parameter discussion in the following section.</span></span>

## <a name="defining-parameters-for-data-access"></a><span data-ttu-id="ca281-122">Definir parâmetros para acesso a dados</span><span class="sxs-lookup"><span data-stu-id="ca281-122">Defining Parameters for Data Access</span></span>

<span data-ttu-id="ca281-123">Este cmdlet define vários parâmetros que permitem ao usuário acessar e examinar os dados armazenados.</span><span class="sxs-lookup"><span data-stu-id="ca281-123">This cmdlet defines several parameters that allow the user to access and examine stored data.</span></span> <span data-ttu-id="ca281-124">Esses parâmetros incluem uma `Path` parâmetro que indica a localização do arquivo de dados, um `Pattern` parâmetro que especifica o padrão a ser utilizado na pesquisa e outros parâmetros que suportam a forma como a pesquisa é executada.</span><span class="sxs-lookup"><span data-stu-id="ca281-124">These parameters include a `Path` parameter that indicates the location of the data store, a `Pattern` parameter that specifies the pattern to be used in the search, and several other parameters that support how the search is performed.</span></span>

> [!NOTE]
> <span data-ttu-id="ca281-125">Para obter mais informações sobre os conceitos básicos da definição de parâmetros, consulte [adicionando parâmetros essa entrada de linha de comandos do processo](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="ca281-125">For more information about the basics of defining parameters, see [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

### <a name="declaring-the-path-parameter"></a><span data-ttu-id="ca281-126">Declarando o parâmetro de caminho</span><span class="sxs-lookup"><span data-stu-id="ca281-126">Declaring the Path Parameter</span></span>

<span data-ttu-id="ca281-127">Para localizar o arquivo de dados, este cmdlet tem de utilizar um caminho do Windows PowerShell para identificar o fornecedor de Windows PowerShell foi projetado para acessar o armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="ca281-127">To locate the data store, this cmdlet must use a Windows PowerShell path to identify the Windows PowerShell provider that is designed to access the data store.</span></span> <span data-ttu-id="ca281-128">Portanto, ele define um `Path` parâmetro do tipo matriz de cadeia de caracteres para indicar a localização do fornecedor.</span><span class="sxs-lookup"><span data-stu-id="ca281-128">Therefore, it defines a `Path` parameter of type string array to indicate the location of the provider.</span></span>

```csharp
[Parameter(
           Position = 0,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
[Parameter(
           Position = 0,
           ParameterSetName = "PatternParameterSet",
           ValueFromPipeline = true,
           Mandatory = true)]
           [Alias("PSPath")]
public string[] Path
{
  get { return paths; }
  set { paths = value; }
}
private string[] paths;
```

<span data-ttu-id="ca281-129">Tenha em atenção que este parâmetro se pertence a dois conjuntos de parâmetros diferentes e que tem um alias.</span><span class="sxs-lookup"><span data-stu-id="ca281-129">Note that this parameter belongs to two different parameter sets and that it has an alias.</span></span>

<span data-ttu-id="ca281-130">Dois [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributos declará-lo a `Path` parâmetro pertence a `ScriptParameterSet` e o `PatternParameterSet`.</span><span class="sxs-lookup"><span data-stu-id="ca281-130">Two [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributes declare that the `Path` parameter belongs to the `ScriptParameterSet` and the `PatternParameterSet`.</span></span> <span data-ttu-id="ca281-131">Para obter mais informações sobre conjuntos de parâmetros, consulte [Adicionar parâmetro define como um Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="ca281-131">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

<span data-ttu-id="ca281-132">O [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) atributo declara um `PSPath` alias para o `Path` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ca281-132">The [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute declares a `PSPath` alias for the `Path` parameter.</span></span> <span data-ttu-id="ca281-133">Declarar este alias é vivamente recomendado para consistência com outros cmdlets que acedem a fornecedores de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca281-133">Declaring this alias is strongly recommended for consistency with other cmdlets that access Windows PowerShell providers.</span></span> <span data-ttu-id="ca281-134">Para obter mais informações aboutWindows caminhos de PowerShell, consulte "Conceitos de caminho do PowerShell" no [como o Windows PowerShell funciona](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span><span class="sxs-lookup"><span data-stu-id="ca281-134">For more information aboutWindows PowerShell paths, see "PowerShell Path Concepts" in [How Windows PowerShell Works](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span></span>

### <a name="declaring-the-pattern-parameter"></a><span data-ttu-id="ca281-135">Declarando o parâmetro do padrão</span><span class="sxs-lookup"><span data-stu-id="ca281-135">Declaring the Pattern Parameter</span></span>

<span data-ttu-id="ca281-136">Para especificar os padrões para procurar, este cmdlet declara um `Pattern` parâmetro que é uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ca281-136">To specify the patterns to search for, this cmdlet declares a `Pattern` parameter that is an array of strings.</span></span> <span data-ttu-id="ca281-137">Um resultado positivo é retornado quando qualquer um dos padrões são encontrados no arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="ca281-137">A positive result is returned when any of the patterns are found in the data store.</span></span> <span data-ttu-id="ca281-138">Tenha em atenção de que esses padrões podem ser compilados numa matriz de expressões regulares compiladas ou uma matriz de padrões de carateres universais utilizado para as pesquisas de literais.</span><span class="sxs-lookup"><span data-stu-id="ca281-138">Note that these patterns can be compiled into an array of compiled regular expressions or an array of wildcard patterns used for literal searches.</span></span>

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "PatternParameterSet",
           Mandatory = true)]
public string[] Pattern
{
  get { return patterns; }
  set { patterns = value; }
}
private string[] patterns;
private Regex[] regexPattern;
private WildcardPattern[] wildcardPattern;
```

<span data-ttu-id="ca281-139">Quando este parâmetro for especificado, o cmdlet utiliza o conjunto de parâmetros padrão `PatternParameterSet`.</span><span class="sxs-lookup"><span data-stu-id="ca281-139">When this parameter is specified, the cmdlet uses the default parameter set `PatternParameterSet`.</span></span> <span data-ttu-id="ca281-140">Neste caso, o cmdlet utiliza os padrões que especificar aqui para selecionar as cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ca281-140">In this case, the cmdlet uses the patterns specified here to select strings.</span></span> <span data-ttu-id="ca281-141">Por outro lado, o `Script` parâmetro também poderia ser usado para fornecer um script que contém os padrões.</span><span class="sxs-lookup"><span data-stu-id="ca281-141">In contrast, the `Script` parameter could also be used to provide a script that contains the patterns.</span></span> <span data-ttu-id="ca281-142">O `Script` e `Pattern` parâmetros definem dois conjuntos de parâmetro separado, para que eles são mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="ca281-142">The `Script` and `Pattern` parameters define two separate parameter sets, so they are mutually exclusive.</span></span>

### <a name="declaring-search-support-parameters"></a><span data-ttu-id="ca281-143">Declarando parâmetros de suporte de pesquisa</span><span class="sxs-lookup"><span data-stu-id="ca281-143">Declaring Search Support Parameters</span></span>

<span data-ttu-id="ca281-144">Este cmdlet define os seguintes parâmetros de suporte que podem ser utilizados para modificar os recursos de pesquisa do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ca281-144">This cmdlet defines the following support parameters that can be used to modify the search capabilities of the cmdlet.</span></span>

<span data-ttu-id="ca281-145">O `Script` parâmetro especifica um bloco de scripts que pode ser utilizado para fornecer um mecanismo de pesquisa alternativo para o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ca281-145">The `Script` parameter specifies a script block that can be used to provide an alternate search mechanism for the cmdlet.</span></span> <span data-ttu-id="ca281-146">O script tem de conter os padrões usados para efetuar a correspondência e retornar uma [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objeto.</span><span class="sxs-lookup"><span data-stu-id="ca281-146">The script must contain the patterns used for matching and return a [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) object.</span></span> <span data-ttu-id="ca281-147">Tenha em atenção que este parâmetro é também o parâmetro exclusivo que identifica o `ScriptParameterSet` conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ca281-147">Note that this parameter is also the unique parameter that identifies the `ScriptParameterSet` parameter set.</span></span> <span data-ttu-id="ca281-148">Quando o tempo de execução do Windows PowerShell vê este parâmetro, ele usa apenas os parâmetros que pertencem ao `ScriptParameterSet` conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ca281-148">When the Windows PowerShell runtime sees this parameter, it uses only parameters that belong to the `ScriptParameterSet` parameter set.</span></span>

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
public ScriptBlock Script
{
  set { script = value; }
  get { return script; }
}
ScriptBlock script;
```

<span data-ttu-id="ca281-149">O `SimpleMatch` parâmetro é um parâmetro que indica se o cmdlet deve ser explicitamente correspondam aos padrões como eles são fornecidos.</span><span class="sxs-lookup"><span data-stu-id="ca281-149">The `SimpleMatch` parameter is a switch parameter that indicates whether the cmdlet is to explicitly match the patterns as they are supplied.</span></span> <span data-ttu-id="ca281-150">Quando o usuário Especifica o parâmetro na linha de comandos (`true`), o cmdlet usa os padrões, como eles são fornecidos.</span><span class="sxs-lookup"><span data-stu-id="ca281-150">When the user specifies the parameter at the command line (`true`), the cmdlet uses the patterns as they are supplied.</span></span> <span data-ttu-id="ca281-151">Se o parâmetro não for especificado (`false`), o cmdlet usa expressões regulares.</span><span class="sxs-lookup"><span data-stu-id="ca281-151">If the parameter is not specified (`false`), the cmdlet uses regular expressions.</span></span> <span data-ttu-id="ca281-152">A predefinição para este parâmetro é `false`.</span><span class="sxs-lookup"><span data-stu-id="ca281-152">The default for this parameter is `false`.</span></span>

```csharp
[Parameter]
public SwitchParameter SimpleMatch
{
  get { return simpleMatch; }
  set { simpleMatch = value; }
}
private bool simpleMatch;
```

<span data-ttu-id="ca281-153">O `CaseSensitive` parâmetro é um parâmetro que indica se é efetuada uma pesquisa de maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="ca281-153">The `CaseSensitive` parameter is a switch parameter that indicates whether a case-sensitive search is performed.</span></span> <span data-ttu-id="ca281-154">Quando o usuário Especifica o parâmetro na linha de comandos (`true`), o cmdlet verifica as maiúsculas e minúsculas de caracteres ao comparar padrões.</span><span class="sxs-lookup"><span data-stu-id="ca281-154">When the user specifies the parameter at the command line (`true`), the cmdlet checks for the uppercase and lowercase of characters when comparing patterns.</span></span> <span data-ttu-id="ca281-155">Se o parâmetro não for especificado (`false`), o cmdlet não faz distinção entre maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="ca281-155">If the parameter is not specified (`false`), the cmdlet does not distinguish between uppercase and lowercase.</span></span> <span data-ttu-id="ca281-156">Por exemplo "MyFile" e "myfile" seriam ambos ser devolvidos como resultados positivos.</span><span class="sxs-lookup"><span data-stu-id="ca281-156">For example "MyFile" and "myfile" would both be returned as positive hits.</span></span> <span data-ttu-id="ca281-157">A predefinição para este parâmetro é `false`.</span><span class="sxs-lookup"><span data-stu-id="ca281-157">The default for this parameter is `false`.</span></span>

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

<span data-ttu-id="ca281-158">O `Exclude` e `Include` parâmetros identificam os itens que são excluídos ou incluídos na pesquisa explicitamente.</span><span class="sxs-lookup"><span data-stu-id="ca281-158">The `Exclude` and `Include` parameters identify items that are explicitly excluded from or included in the search.</span></span> <span data-ttu-id="ca281-159">Por predefinição, o cmdlet irá procurar todos os itens no arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="ca281-159">By default, the cmdlet will search all items in the data store.</span></span> <span data-ttu-id="ca281-160">No entanto, para limitar a pesquisa realizada pelo cmdlet, esses parâmetros podem ser usados para indicar explicitamente os itens a serem incluídos na pesquisa ou for omitidos.</span><span class="sxs-lookup"><span data-stu-id="ca281-160">However, to limit the search performed by the cmdlet, these parameters can be used to explicitly indicate items to be included in the search or omitted.</span></span>

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

```csharp
[Parameter]
[ValidateNotNullOrEmpty]
public string[] Include
{
  get
  {
    return includeStrings;
  }
  set
  {
    includeStrings = value;

    this.include = new WildcardPattern[includeStrings.Length];
    for (int i = 0; i < includeStrings.Length; i++)
    {
      this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
    }
  }
}

internal string[] includeStrings = null;
internal WildcardPattern[] include = null;
```

### <a name="declaring-parameter-sets"></a><span data-ttu-id="ca281-161">Declaração de conjuntos de parâmetros</span><span class="sxs-lookup"><span data-stu-id="ca281-161">Declaring Parameter Sets</span></span>

<span data-ttu-id="ca281-162">Este cmdlet utiliza dois conjuntos de parâmetros (`ScriptParameterSet` e `PatternParameterSet`, que é o padrão) como os nomes dos dois conjuntos de parâmetros utilizados no acesso a dados.</span><span class="sxs-lookup"><span data-stu-id="ca281-162">This cmdlet uses two parameter sets (`ScriptParameterSet` and `PatternParameterSet`, which is the default) as the names of two parameter sets used in data access.</span></span> <span data-ttu-id="ca281-163">`PatternParameterSet` é o conjunto de parâmetros padrão e é utilizado quando o `Pattern` parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="ca281-163">`PatternParameterSet` is the default parameter set and is used when the `Pattern` parameter is specified.</span></span> <span data-ttu-id="ca281-164">`ScriptParameterSet` é usado quando o utilizador Especifica um mecanismo de pesquisa alternativo por meio do `Script` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ca281-164">`ScriptParameterSet` is used when the user specifies an alternate search mechanism through the `Script` parameter.</span></span> <span data-ttu-id="ca281-165">Para obter mais informações sobre conjuntos de parâmetros, consulte [Adicionar parâmetro define como um Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="ca281-165">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="ca281-166">Substituir os métodos de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="ca281-166">Overriding Input Processing Methods</span></span>

<span data-ttu-id="ca281-167">Cmdlets tem de substituir um ou mais da entrada de processamento de métodos para o [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe.</span><span class="sxs-lookup"><span data-stu-id="ca281-167">Cmdlets must override one or more of the input processing methods for the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span> <span data-ttu-id="ca281-168">Para obter mais informações sobre os métodos de processamento de entrada, consulte [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="ca281-168">For more information about the input processing methods, see [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="ca281-169">Este cmdlet substitui o [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) compilados de método para criar uma matriz de expressões regulares na inicialização.</span><span class="sxs-lookup"><span data-stu-id="ca281-169">This cmdlet overrides the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to build an array of compiled regular expressions at startup.</span></span> <span data-ttu-id="ca281-170">Isso aumenta o desempenho durante as buscas que não utilizam a correspondência simples.</span><span class="sxs-lookup"><span data-stu-id="ca281-170">This increases performance during searches that do not use simple matching.</span></span>

```csharp
protected override void BeginProcessing()
{
  WriteDebug("Validating patterns.");
  if (patterns != null)
  {
    foreach(string pattern in patterns)
    {
      if (pattern == null)
      ThrowTerminatingError(new ErrorRecord(
                            new ArgumentNullException(
                            "Search pattern cannot be null."),
                            "NullSearchPattern",
                            ErrorCategory.InvalidArgument,
                            pattern)
                            );
    }

    WriteVerbose("Search pattern(s) are valid.");

    // If a simple match is not specified, then
    // compile the regular expressions once.
    if (!simpleMatch)
    {
      WriteDebug("Compiling search regular expressions.");

      RegexOptions regexOptions = RegexOptions.Compiled;
      if (!caseSensitive)
         regexOptions |= RegexOptions.Compiled;
      regexPattern = new Regex[patterns.Length];

      for (int i = 0; i < patterns.Length; i++)
      {
        try
        {
          regexPattern[i] = new Regex(patterns[i], regexOptions);
        }
        catch (ArgumentException ex)
        {
          ThrowTerminatingError(new ErrorRecord(
                        ex,
                        "InvalidRegularExpression",
                        ErrorCategory.InvalidArgument,
                        patterns[i]
                     ));
        }
      } //Loop through patterns to create RegEx objects.

      WriteVerbose("Pattern(s) compiled into regular expressions.");
    }// If not a simple match.

    // If a simple match is specified, then compile the
    // wildcard patterns once.
    else
    {
      WriteDebug("Compiling search wildcards.");

      WildcardOptions wildcardOptions = WildcardOptions.Compiled;

      if (!caseSensitive)
      {
        wildcardOptions |= WildcardOptions.IgnoreCase;
      }

      wildcardPattern = new WildcardPattern[patterns.Length];
      for (int i = 0; i < patterns.Length; i++)
      {
        wildcardPattern[i] =
                     new WildcardPattern(patterns[i], wildcardOptions);
      }

      WriteVerbose("Pattern(s) compiled into wildcard expressions.");
    }// If match is a simple match.
  }// If valid patterns are available.
}// End of function BeginProcessing().
```

<span data-ttu-id="ca281-171">Este cmdlet também substitui o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para processar as seleções de cadeia de caracteres que o usuário fizer na linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="ca281-171">This cmdlet also overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the string selections that the user makes on the command line.</span></span> <span data-ttu-id="ca281-172">Escreve os resultados da seleção de cadeia de caracteres na forma de um objeto personalizado, chamando uma privada **MatchString** método.</span><span class="sxs-lookup"><span data-stu-id="ca281-172">It writes the results of string selection in the form of a custom object by calling a private **MatchString** method.</span></span>

```csharp
protected override void ProcessRecord()
{
  UInt64 lineNumber = 0;
  MatchInfo result;
  ArrayList nonMatches = new ArrayList();

  // Walk the list of paths and search the contents for
  // any of the specified patterns.
  foreach (string psPath in paths)
  {
    // Once the filepaths are expanded, we may have more than one
    // path, so process all referenced paths.
    foreach(PathInfo path in
            SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
           )
    {
      WriteVerbose("Processing path " + path.Path);

      // Check if the path represents one of the items to be
      // excluded. If so, continue to next path.
      if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
         continue;

      // Get the content reader for the item(s) at the
      // specified path.
      Collection<IContentReader> readerCollection = null;
      try
      {
        readerCollection =
                    this.InvokeProvider.Content.GetReader(path.Path);
      }
      catch (PSNotSupportedException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "ContentAccessNotSupported",
                    ErrorCategory.NotImplemented,
                    path.Path)
                   );
        return;
      }

      foreach(IContentReader reader in readerCollection)
      {
        // Reset the line number for this path.
        lineNumber = 0;

        // Read in a single block (line in case of a file)
        // from the object.
        IList items = reader.Read(1);

        // Read and process one block(line) at a time until
        // no more blocks(lines) exist.
        while (items != null && items.Count == 1)
        {
          // Increment the line number each time a line is
          // processed.
          lineNumber++;

          String message = String.Format("Testing line {0} : {1}",
                                        lineNumber, items[0]);

          WriteDebug(message);

          result = SelectString(items[0]);

          if (result != null)
          {
            result.Path = path.Path;
            result.LineNumber = lineNumber;

            WriteObject(result);
          }
          else
          {
            // Add the block(line) that did not match to the
            // collection of non matches , which will be stored
            // in the SessionState variable $NonMatches
            nonMatches.Add(items[0]);
          }

          // Get the next line from the object.
          items = reader.Read(1);

        }// While loop for reading one line at a time.
      }// Foreach loop for reader collection.
    }// Foreach loop for processing referenced paths.
  }// Foreach loop for walking of path list.

  // Store the list of non-matches in the
  // session state variable $NonMatches.
  try
  {
    this.SessionState.PSVariable.Set("NonMatches", nonMatches);
  }
  catch (SessionStateUnauthorizedAccessException ex)
  {
    WriteError(new ErrorRecord(ex,
               "CannotWriteVariableNonMatches",
               ErrorCategory.InvalidOperation,
               nonMatches)
              );
  }

}// End of protected override void ProcessRecord().
```

## <a name="accessing-content"></a><span data-ttu-id="ca281-173">Aceder ao conteúdo</span><span class="sxs-lookup"><span data-stu-id="ca281-173">Accessing Content</span></span>

<span data-ttu-id="ca281-174">Seu cmdlet tem de abrir o fornecedor indicado pelo caminho do Windows PowerShell, para que possa aceder os dados.</span><span class="sxs-lookup"><span data-stu-id="ca281-174">Your cmdlet must open the provider indicated by the Windows PowerShell path so that it can access the data.</span></span> <span data-ttu-id="ca281-175">O [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) objeto para o espaço de execução é utilizado para acesso ao fornecedor, enquanto o [System.Management.Automation.PSCmdlet.Invokeprovider\*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) propriedade das cmdlet é utilizado para abrir o fornecedor.</span><span class="sxs-lookup"><span data-stu-id="ca281-175">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) object for the runspace is used for access to the provider, while the [System.Management.Automation.PSCmdlet.Invokeprovider\*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) property of the cmdlet is used to open the provider.</span></span> <span data-ttu-id="ca281-176">Acesso ao conteúdo é fornecido pela obtenção do [System.Management.Automation.Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) aberta de objeto para o fornecedor.</span><span class="sxs-lookup"><span data-stu-id="ca281-176">Access to content is provided by retrieval of the [System.Management.Automation.Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) object for the provider opened.</span></span>

<span data-ttu-id="ca281-177">Este cmdlet Select-Str de exemplo utiliza a [System.Management.Automation.Providerintrinsics.Content\*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) propriedade para expor o conteúdo para analisar.</span><span class="sxs-lookup"><span data-stu-id="ca281-177">This sample Select-Str cmdlet uses the [System.Management.Automation.Providerintrinsics.Content\*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) property to expose the content to scan.</span></span> <span data-ttu-id="ca281-178">Em seguida, pode chamar o [System.Management.Automation.Contentcmdletproviderintrinsics.Getreader\*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) método, passando o caminho do Windows PowerShell necessário.</span><span class="sxs-lookup"><span data-stu-id="ca281-178">It can then call the [System.Management.Automation.Contentcmdletproviderintrinsics.Getreader\*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) method, passing the required Windows PowerShell path.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ca281-179">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="ca281-179">Code Sample</span></span>

<span data-ttu-id="ca281-180">O código a seguir mostra a implementação desta versão deste cmdlet Select-Str.</span><span class="sxs-lookup"><span data-stu-id="ca281-180">The following code shows the implementation of this version of this Select-Str cmdlet.</span></span> <span data-ttu-id="ca281-181">Observe que esse código inclui a classe de cmdlet, utilizados pelo cmdlet de métodos privados e o Windows PowerShell snap-in do código usado para registrar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ca281-181">Note that this code includes the cmdlet class, private methods used by the cmdlet, and the Windows PowerShell snap-in code used to register the cmdlet.</span></span> <span data-ttu-id="ca281-182">Para obter mais informações sobre como registar o cmdlet, consulte [criando o Cmdlet](#building-the-cmdlet).</span><span class="sxs-lookup"><span data-stu-id="ca281-182">For more information about registering the cmdlet, see [Building the Cmdlet](#building-the-cmdlet).</span></span>

```csharp
//
// Copyright (c) 2006 Microsoft Corporation. All rights reserved.
//
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
// PARTICULAR PURPOSE.
//
using System;
using System.Text.RegularExpressions;
using System.Collections;
using System.Collections.ObjectModel;
using System.Management.Automation;
using System.Management.Automation.Provider;
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{
  #region SelectStringCommand
  /// <summary>
  /// This cmdlet searches through PSObjects for particular patterns.
  /// </summary>
  /// <remarks>
  /// This cmdlet can be used to search any object, such as a file or a
  /// variable, whose provider exposes methods for reading and writing
  /// content.
  /// </remarks>
  [Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
  public class SelectStringCommand : PSCmdlet
  {
    #region Parameters
    /// <summary>
    /// Declare a Path parameter that specifies where the data is stored.
    /// This parameter must specify a PowerShell that indicates the
    /// PowerShell provider that is used to access the objects to be
    /// searched for matching patterns. This parameter should also have
    /// a PSPath alias to provide consistency with other cmdlets that use
    /// PowerShell providers.
    /// </summary>
    /// <value>Path of the object(s) to search.</value>
    [Parameter(
               Position = 0,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    [Parameter(
               Position = 0,
               ParameterSetName = "PatternParameterSet",
               ValueFromPipeline = true,
               Mandatory = true)]
               [Alias("PSPath")]
    public string[] Path
    {
      get { return paths; }
      set { paths = value; }
    }
    private string[] paths;

    /// <summary>
    /// Declare a Pattern parameter that specifies the pattern(s)
    /// used to find matching patterns in the string representation
    /// of the objects. A positive result will be returned
    /// if any of the patterns are found in the objects.
    /// </summary>
    /// <remarks>
    /// The patterns will be compiled into an array of wildcard
    /// patterns for a simple match (literal string matching),
    /// or the patterns will be converted into an array of compiled
    /// regular expressions.
    /// </remarks>
    /// <value>Array of patterns to search.</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "PatternParameterSet",
               Mandatory = true)]
    public string[] Pattern
    {
      get { return patterns; }
      set { patterns = value; }
    }
    private string[] patterns;
    private Regex[] regexPattern;
    private WildcardPattern[] wildcardPattern;

    /// <summary>
    /// Declare a Script parameter that specifies a script block
    /// that is called to perform the matching operations
    /// instead of the matching performed by the cmdlet.
    /// </summary>
    /// <value>Script block that will be called for matching</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    public ScriptBlock Script
    {
      set { script = value; }
      get { return script; }
    }
    ScriptBlock script;

    /// <summary>
    /// Declare a switch parameter that specifies if the pattern(s) are used
    /// literally. If not (default), searching is
    /// done using regular expressions.
    /// </summary>
    /// <value>If True, a literal pattern is used.</value>
    [Parameter]
    public SwitchParameter SimpleMatch
    {
      get { return simpleMatch; }
      set { simpleMatch = value; }
    }
    private bool simpleMatch;

    /// <summary>
    /// Declare a switch parameter that specifies if a case-sensitive
    /// search is performed.  If not (default), a case-insensitive search
    /// is performed.
    /// </summary>
    /// <value>If True, a case-sensitive search is made.</value>
    [Parameter]
    public SwitchParameter CaseSensitive
    {
      get { return caseSensitive; }
      set { caseSensitive = value; }
    }
    private bool caseSensitive;

    /// <summary>
    /// Declare an Include parameter that species which
    /// specific items are searched.  When this parameter
    /// is used, items that are not listed here are omitted
    /// from the search.
    /// </summary>
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Include
    {
      get
      {
        return includeStrings;
      }
      set
      {
        includeStrings = value;

        this.include = new WildcardPattern[includeStrings.Length];
        for (int i = 0; i < includeStrings.Length; i++)
        {
          this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }

    internal string[] includeStrings = null;
    internal WildcardPattern[] include = null;

    /// <summary>
    /// Declare an Exclude parameter that species which
    /// specific items are omitted from the search.
    /// </summary>
    ///
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Exclude
    {
      get
      {
        return excludeStrings;
      }
      set
      {
        excludeStrings = value;

        this.exclude = new WildcardPattern[excludeStrings.Length];
        for (int i = 0; i < excludeStrings.Length; i++)
        {
          this.exclude[i] = new WildcardPattern(excludeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }
    internal string[] excludeStrings;
    internal WildcardPattern[] exclude;

    #endregion Parameters

    #region Overrides
    /// <summary>
    /// If regular expressions are used for pattern matching,
    /// then build an array of compiled regular expressions
    /// at startup. This increases performance during scanning
    /// operations when simple matching is not used.
    /// </summary>
    protected override void BeginProcessing()
    {
      WriteDebug("Validating patterns.");
      if (patterns != null)
      {
        foreach(string pattern in patterns)
        {
          if (pattern == null)
          ThrowTerminatingError(new ErrorRecord(
                                new ArgumentNullException(
                                "Search pattern cannot be null."),
                                "NullSearchPattern",
                                ErrorCategory.InvalidArgument,
                                pattern)
                                );
        }

        WriteVerbose("Search pattern(s) are valid.");

        // If a simple match is not specified, then
        // compile the regular expressions once.
        if (!simpleMatch)
        {
          WriteDebug("Compiling search regular expressions.");

          RegexOptions regexOptions = RegexOptions.Compiled;
          if (!caseSensitive)
             regexOptions |= RegexOptions.Compiled;
          regexPattern = new Regex[patterns.Length];

          for (int i = 0; i < patterns.Length; i++)
          {
            try
            {
              regexPattern[i] = new Regex(patterns[i], regexOptions);
            }
            catch (ArgumentException ex)
            {
              ThrowTerminatingError(new ErrorRecord(
                            ex,
                            "InvalidRegularExpression",
                            ErrorCategory.InvalidArgument,
                            patterns[i]
                         ));
            }
          } //Loop through patterns to create RegEx objects.

          WriteVerbose("Pattern(s) compiled into regular expressions.");
        }// If not a simple match.

        // If a simple match is specified, then compile the
        // wildcard patterns once.
        else
        {
          WriteDebug("Compiling search wildcards.");

          WildcardOptions wildcardOptions = WildcardOptions.Compiled;

          if (!caseSensitive)
          {
            wildcardOptions |= WildcardOptions.IgnoreCase;
          }

          wildcardPattern = new WildcardPattern[patterns.Length];
          for (int i = 0; i < patterns.Length; i++)
          {
            wildcardPattern[i] =
                         new WildcardPattern(patterns[i], wildcardOptions);
          }

          WriteVerbose("Pattern(s) compiled into wildcard expressions.");
        }// If match is a simple match.
      }// If valid patterns are available.
    }// End of function BeginProcessing().

    /// <summary>
    /// Process the input and search for the specified patterns.
    /// </summary>
    protected override void ProcessRecord()
    {
      UInt64 lineNumber = 0;
      MatchInfo result;
      ArrayList nonMatches = new ArrayList();

      // Walk the list of paths and search the contents for
      // any of the specified patterns.
      foreach (string psPath in paths)
      {
        // Once the filepaths are expanded, we may have more than one
        // path, so process all referenced paths.
        foreach(PathInfo path in
                SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
               )
        {
          WriteVerbose("Processing path " + path.Path);

          // Check if the path represents one of the items to be
          // excluded. If so, continue to next path.
          if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
             continue;

          // Get the content reader for the item(s) at the
          // specified path.
          Collection<IContentReader> readerCollection = null;
          try
          {
            readerCollection =
                        this.InvokeProvider.Content.GetReader(path.Path);
          }
          catch (PSNotSupportedException ex)
          {
            WriteError(new ErrorRecord(ex,
                       "ContentAccessNotSupported",
                        ErrorCategory.NotImplemented,
                        path.Path)
                       );
            return;
          }

          foreach(IContentReader reader in readerCollection)
          {
            // Reset the line number for this path.
            lineNumber = 0;

            // Read in a single block (line in case of a file)
            // from the object.
            IList items = reader.Read(1);

            // Read and process one block(line) at a time until
            // no more blocks(lines) exist.
            while (items != null && items.Count == 1)
            {
              // Increment the line number each time a line is
              // processed.
              lineNumber++;

              String message = String.Format("Testing line {0} : {1}",
                                            lineNumber, items[0]);

              WriteDebug(message);

              result = SelectString(items[0]);

              if (result != null)
              {
                result.Path = path.Path;
                result.LineNumber = lineNumber;

                WriteObject(result);
              }
              else
              {
                // Add the block(line) that did not match to the
                // collection of non matches , which will be stored
                // in the SessionState variable $NonMatches
                nonMatches.Add(items[0]);
              }

              // Get the next line from the object.
              items = reader.Read(1);

            }// While loop for reading one line at a time.
          }// Foreach loop for reader collection.
        }// Foreach loop for processing referenced paths.
      }// Foreach loop for walking of path list.

      // Store the list of non-matches in the
      // session state variable $NonMatches.
      try
      {
        this.SessionState.PSVariable.Set("NonMatches", nonMatches);
      }
      catch (SessionStateUnauthorizedAccessException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "CannotWriteVariableNonMatches",
                   ErrorCategory.InvalidOperation,
                   nonMatches)
                  );
      }

    }// End of protected override void ProcessRecord().
    #endregion Overrides

    #region PrivateMethods
    /// <summary>
    /// Check for a match using the input string and the pattern(s)
    /// specified.
    /// </summary>
    /// <param name="input">The string to test.</param>
    /// <returns>MatchInfo object containing information about
    /// result of a match</returns>
    private MatchInfo SelectString(object input)
    {
      string line = null;

      try
      {
        // Convert the object to a string type
        // safely using language support methods
        line = (string)LanguagePrimitives.ConvertTo(
                                                    input,
                                                    typeof(string)
                                                    );
        line = line.Trim(' ','\t');
      }
      catch (PSInvalidCastException ex)
      {
        WriteError(new ErrorRecord(
                   ex,
                   "CannotCastObjectToString",
                   ErrorCategory.InvalidOperation,
                   input)
                   );

        return null;
      }

      MatchInfo result = null;

      // If a scriptblock has been specified, call it
      // with the path for processing.  It will return
      // one object.
      if (script != null)
      {
        WriteDebug("Executing script block.");

        Collection<PSObject> psObjects =
                             script.Invoke(
                                           line,
                                           simpleMatch,
                                           caseSensitive
                                          );

        foreach (PSObject psObject in psObjects)
        {
          if (LanguagePrimitives.IsTrue(psObject))
          {
            result = new MatchInfo();
            result.Line = line;
            result.IgnoreCase = !caseSensitive;

            break;
          } //End of If.
        } //End ForEach loop.
      } // End of If if script exists.

      // If script block exists, see if this line matches any
      // of the match patterns.
      else
      {
        int patternIndex = 0;

        while (patternIndex < patterns.Length)
        {
          if ((simpleMatch &&
              wildcardPattern[patternIndex].IsMatch(line))
              || (regexPattern != null
              && regexPattern[patternIndex].IsMatch(line))
             )
          {
            result = new MatchInfo();
            result.IgnoreCase = !caseSensitive;
            result.Line = line;
            result.Pattern = patterns[patternIndex];

            break;
          }

          patternIndex++;

        }// While loop through patterns.
      }// Else for no script block specified.

      return result;

    }// End of SelectString

    /// <summary>
    /// Check whether the supplied name meets the include/exclude criteria.
    /// That is - it's on the include list if the include list was
    /// specified, and not on the exclude list if the exclude list was specified.
    /// </summary>
    /// <param name="path">path to validate</param>
    /// <returns>True if the path is acceptable.</returns>
    private bool MeetsIncludeExcludeCriteria(string path)
    {
      bool ok = false;

      // See if the file is on the include list.
      if (this.include != null)
      {
        foreach (WildcardPattern patternItem in this.include)
        {
          if (patternItem.IsMatch(path))
          {
            ok = true;
            break;
          }
        }
      }
      else
      {
        ok = true;
      }

      if (!ok)
         return false;

      // See if the file is on the exclude list.
      if (this.exclude != null)
      {
        foreach (WildcardPattern patternItem in this.exclude)
        {
          if (patternItem.IsMatch(path))
          {
            ok = false;
            break;
          }
        }
      }

      return ok;
    } //MeetsIncludeExcludeCriteria
    #endregion Private Methods

  }// class SelectStringCommand

  #endregion SelectStringCommand

  #region MatchInfo

  /// <summary>
  /// Class representing the result of a pattern/literal match
  /// that is passed through the pipeline by the Select-Str cmdlet.
  /// </summary>
  public class MatchInfo
  {
    /// <summary>
    /// Indicates if the match was done ignoring case.
    /// </summary>
    /// <value>True if case was ignored.</value>
    public bool IgnoreCase
    {
      get { return ignoreCase; }
      set { ignoreCase = value; }
    }
    private bool ignoreCase;

    /// <summary>
    /// Specifies the number of the matching line.
    /// </summary>
    /// <value>The number of the matching line.</value>
    public UInt64 LineNumber
    {
      get { return lineNumber; }
      set { lineNumber = value; }
    }
    private UInt64 lineNumber;

    /// <summary>
    /// Specifies the text of the matching line.
    /// </summary>
    /// <value>The text of the matching line.</value>
    public string Line
    {
      get { return line; }
      set { line = value; }
    }
    private string line;

    /// <summary>
    /// Specifies the full path of the object(file) containing the
    /// matching line.
    /// </summary>
    /// <remarks>
    /// It will be "inputStream" if the object came from the input
    /// stream.
    /// </remarks>
    /// <value>The path name</value>
    public string Path
    {
      get { return path; }
      set
      {
        pathSet = true;
        path = value;
      }
    }
    private string path;
    private bool pathSet;

    /// <summary>
    /// Specifies the pattern that was used in the match.
    /// </summary>
    /// <value>The pattern string</value>
    public string Pattern
    {
      get { return pattern; }
      set { pattern = value; }
    }
    private string pattern;

    private const string MatchFormat = "{0}:{1}:{2}";

    /// <summary>
    /// Returns the string representation of this object. The format
    /// depends on whether a path has been set for this object or
    /// not.
    /// </summary>
    /// <remarks>
    /// If the path component is set, as would be the case when
    /// matching in a file, ToString() returns the path, line
    /// number and line text.  If path is not set, then just the
    /// line text is presented.
    /// </remarks>
    /// <returns>The string representation of the match object.</returns>
    public override string ToString()
    {
      if (pathSet)
         return String.Format(
         System.Threading.Thread.CurrentThread.CurrentCulture,
         MatchFormat,
         this.path,
         this.lineNumber,
         this.line
         );
      else
         return this.line;
    }
  }// End class MatchInfo

  #endregion

  #region PowerShell snap-in

  /// <summary>
  /// Create a PowerShell snap-in for the Select-Str cmdlet.
  /// </summary>
  [RunInstaller(true)]
  public class SelectStringPSSnapIn : PSSnapIn
  {
    /// <summary>
    /// Create an instance of the SelectStrPSSnapin class.
    /// </summary>
    public SelectStringPSSnapIn()
           : base()
    {
    }

    /// <summary>
    /// Specify the name of the PowerShell snap-in.
    /// </summary>
    public override string Name
    {
      get
      {
        return "SelectStrPSSnapIn";
      }
    }

    /// <summary>
    /// Specify the vendor of the PowerShell snap-in.
    /// </summary>
    public override string Vendor
    {
      get
      {
        return "Microsoft";
      }
    }

    /// <summary>
    /// Specify the localization resource information for the vendor.
    /// Use the format: SnapinName,VendorName.
    /// </summary>
    public override string VendorResource
    {
      get
      {
        return "SelectStrSnapIn,Microsoft";
      }
    }

    /// <summary>
    /// Specify the description of the PowerShell snap-in.
    /// </summary>
    public override string Description
    {
      get
        {
          return "This is a PowerShell snap-in for the Select-Str cmdlet.";
        }
    }

    /// <summary>
    /// Specify the localization resource information for the description.
    /// Use the format: SnapinName,Description.

    /// </summary>
    public override string DescriptionResource
    {
      get
      {
          return "SelectStrSnapIn,This is a PowerShell snap-in for the Select-Str cmdlet.";
      }
    }
  }
  #endregion PowerShell snap-in

} //namespace Microsoft.Samples.PowerShell.Commands;
```

## <a name="building-the-cmdlet"></a><span data-ttu-id="ca281-183">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ca281-183">Building the Cmdlet</span></span>

<span data-ttu-id="ca281-184">Depois de implementar um cmdlet, tem de registá-lo com o Windows PowerShell através de um snap-in do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca281-184">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="ca281-185">Para obter mais informações sobre como registar os cmdlets, consulte [como registrar Cmdlets, fornecedores e alojar aplicações](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="ca281-185">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="ca281-186">O Cmdlet de teste</span><span class="sxs-lookup"><span data-stu-id="ca281-186">Testing the Cmdlet</span></span>

<span data-ttu-id="ca281-187">Quando seu cmdlet foi registado com o Windows PowerShell, pode testá-lo executando-a na linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="ca281-187">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="ca281-188">O procedimento seguinte pode ser utilizado para testar o cmdlet Select-Str de exemplo.</span><span class="sxs-lookup"><span data-stu-id="ca281-188">The following procedure can be used to test the sample Select-Str cmdlet.</span></span>

1. <span data-ttu-id="ca281-189">Inicie o Windows PowerShell e procure o ficheiro de notas para ocorrências de linhas com a expressão ".NET".</span><span class="sxs-lookup"><span data-stu-id="ca281-189">Start Windows PowerShell, and search the Notes file for occurrences of lines with the expression ".NET".</span></span> <span data-ttu-id="ca281-190">Tenha em atenção que as aspas à volta o nome do caminho são necessárias apenas se o caminho é composta por mais de uma palavra.</span><span class="sxs-lookup"><span data-stu-id="ca281-190">Note that the quotation marks around the name of the path are required only if the path consists of more than one word.</span></span>

    ```powershell
    select-str -Path "notes" -Pattern ".NET" -SimpleMatch=$false
    ```

    <span data-ttu-id="ca281-191">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="ca281-191">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 8
    Line         : Because Windows PowerShell works directly with .NET objects, there is often a .NET object
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    IgnoreCase   : True
    LineNumber   : 21
    Line         : You should normally define the class for a cmdlet in a .NET namespace
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    ```

2. <span data-ttu-id="ca281-192">Procure o ficheiro de notas para ocorrências de linhas com a palavra "em", seguido de qualquer outro texto.</span><span class="sxs-lookup"><span data-stu-id="ca281-192">Search the Notes file for occurrences of lines with the word "over", followed by any other text.</span></span> <span data-ttu-id="ca281-193">O `SimpleMatch` parâmetro estiver a utilizar o valor predefinido de `false`.</span><span class="sxs-lookup"><span data-stu-id="ca281-193">The `SimpleMatch` parameter is using the default value of `false`.</span></span> <span data-ttu-id="ca281-194">A pesquisa é sensível porque o `CaseSensitive` parâmetro estiver definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="ca281-194">The search is case-insensitive because the `CaseSensitive` parameter is set to `false`.</span></span>

    ```powershell
    select-str -Path notes -Pattern "over*" -SimpleMatch -CaseSensitive:$false
    ```

    <span data-ttu-id="ca281-195">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="ca281-195">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 45
    Line         : Override StopProcessing
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    IgnoreCase   : True
    LineNumber   : 49
    Line         : overriding the StopProcessing method
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    ```

3. <span data-ttu-id="ca281-196">O ficheiro de notas com uma expressão regular como o padrão de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="ca281-196">Search the Notes file using a regular expression as the pattern.</span></span> <span data-ttu-id="ca281-197">O cmdlet procura carateres alfabéticos e espaços em branco entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="ca281-197">The cmdlet searches for alphabetical characters and blank spaces enclosed in parentheses.</span></span>

    ```powershell
    select-str -Path notes -Pattern "\([A-Za-z:blank:]" -SimpleMatch:$false
    ```

    <span data-ttu-id="ca281-198">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="ca281-198">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : Advisory Guidelines (Consider Following)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    IgnoreCase   : True
    LineNumber   : 53
    Line         : If your cmdlet has objects that are not disposed of (written to the pipeline)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    ```

4. <span data-ttu-id="ca281-199">Execute uma pesquisa diferenciando maiúsculas de minúsculas do arquivo de notas para ocorrências da palavra "Parâmetro".</span><span class="sxs-lookup"><span data-stu-id="ca281-199">Perform a case-sensitive search of the Notes file for occurrences of the word "Parameter".</span></span>

    ```powershell
    select-str -Path notes -Pattern Parameter -CaseSensitive
    ```

    <span data-ttu-id="ca281-200">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="ca281-200">The following output appears.</span></span>

    ```output
    IgnoreCase   : False
    LineNumber   : 6
    Line         : Support an InputObject Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    IgnoreCase   : False
    LineNumber   : 30
    Line         : Support Force Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    ```

5. <span data-ttu-id="ca281-201">O fornecedor de variável de pesquisa foi fornecido com o Windows PowerShell para variáveis que têm valores numéricos de 0 a 9.</span><span class="sxs-lookup"><span data-stu-id="ca281-201">Search the variable provider shipped with Windows PowerShell for variables that have numerical values from 0 through 9.</span></span>

    ```powershell
    select-str -Path * -Pattern "[0-9]"
    ```

    <span data-ttu-id="ca281-202">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="ca281-202">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : 64
    Path         : Variable:\MaximumHistoryCount
    Pattern      : [0-9]
    ```

6. <span data-ttu-id="ca281-203">Utilize um bloco de script para procurar o ficheiro SelectStrCommandSample.cs para a cadeia de caracteres "Pos".</span><span class="sxs-lookup"><span data-stu-id="ca281-203">Use a script block to search the file SelectStrCommandSample.cs for the string "Pos".</span></span> <span data-ttu-id="ca281-204">O **cmatch** funcionar para o script executa uma correspondência de padrão de maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="ca281-204">The **cmatch** function for the script performs a case-insensitive pattern match.</span></span>

    ```powershell
    select-str -Path "SelectStrCommandSample.cs" -Script { if ($args[0] -cmatch "Pos"){ return $true } return $false }
    ```

    <span data-ttu-id="ca281-205">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="ca281-205">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 37
    Line         :    Position = 0.
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\SelectStrCommandSample.cs
    Pattern      :
    ```

## <a name="see-also"></a><span data-ttu-id="ca281-206">Veja Também</span><span class="sxs-lookup"><span data-stu-id="ca281-206">See Also</span></span>

[<span data-ttu-id="ca281-207">Como criar um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca281-207">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="ca281-208">Criando seu primeiro Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ca281-208">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="ca281-209">Criar um Cmdlet que modifica o sistema</span><span class="sxs-lookup"><span data-stu-id="ca281-209">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="ca281-210">Estruturar o seu fornecedor do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca281-210">Design Your Windows PowerShell Provider</span></span>](../prog-guide/designing-your-windows-powershell-provider.md)

[<span data-ttu-id="ca281-211">Como funciona o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca281-211">How Windows PowerShell Works</span></span>](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[<span data-ttu-id="ca281-212">Como registar os Cmdlets, fornecedores e alojar aplicações</span><span class="sxs-lookup"><span data-stu-id="ca281-212">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="ca281-213">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca281-213">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
