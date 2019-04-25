---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a96a4a58dafa01fb43f5bdffb52ef833816148e7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058374"
---
# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="5f9b3-102">Novos recursos de linguagem no PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5f9b3-102">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="5f9b3-103">PowerShell 5.0 introduz os seguintes elementos de linguagem de novo no Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5f9b3-103">PowerShell 5.0 introduces the following new language elements in Windows PowerShell:</span></span>

## <a name="class-keyword"></a><span data-ttu-id="5f9b3-104">Palavra-chave de classe</span><span class="sxs-lookup"><span data-stu-id="5f9b3-104">Class keyword</span></span>

<span data-ttu-id="5f9b3-105">O **classe** palavra-chave define uma nova classe.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-105">The **class** keyword defines a new class.</span></span> <span data-ttu-id="5f9b3-106">Esta é uma verdadeira tipo do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-106">This is a true .NET Framework type.</span></span>
<span data-ttu-id="5f9b3-107">Membros de classe são públicos, mas apenas público dentro do escopo do módulo.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-107">Class members are public, but only public within the module scope.</span></span>
<span data-ttu-id="5f9b3-108">Não é possível consultar o nome do tipo como cadeia de caracteres (por exemplo, `New-Object` não funciona), e nesta versão, não é possível utilizar um literal de tipo (por exemplo, `[MyClass]`) fora o ficheiro de script/módulo no qual a classe é definida.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-108">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script/module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="5f9b3-109">Palavra-chave de enumeração e enumerações</span><span class="sxs-lookup"><span data-stu-id="5f9b3-109">Enum keyword and enumerations</span></span>

<span data-ttu-id="5f9b3-110">Suporte para o **enum** palavra-chave tiver sido adicionado, que utiliza o caractere de nova linha como o delimitador.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-110">Support for the **enum** keyword has been added, which uses newline as the delimiter.</span></span>
<span data-ttu-id="5f9b3-111">Limitações atuais: não é possível definir um enumerador em termos de em si, mas pode inicializar um enum em termos de outro enum, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-111">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize an enum in terms of another enum, as shown in the following example.</span></span>
<span data-ttu-id="5f9b3-112">Além disso, atualmente não é possível especificar o tipo base; é sempre [int].</span><span class="sxs-lookup"><span data-stu-id="5f9b3-112">Also, the base type cannot currently be specified; it is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="5f9b3-113">Um valor de enumerador tem de ser uma constante de tempo de análise; Não é possível defini-lo para o resultado de um comando invocado.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-113">An enumerator value must be a parse time constant; you cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="5f9b3-114">Enums suporta operações aritméticas, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-114">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a><span data-ttu-id="5f9b3-115">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="5f9b3-115">Import-DscResource</span></span>

<span data-ttu-id="5f9b3-116">**Import-DscResource** agora é uma palavra-chave dynamic verdadeira.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-116">**Import-DscResource** is now a true dynamic keyword.</span></span>
<span data-ttu-id="5f9b3-117">PowerShell analisa o módulo de raiz do módulo especificado, pesquisa de classes que contêm os **DscResource** atributo.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-117">PowerShell parses the specified module’s root module, searching for classes that contain the **DscResource** attribute.</span></span>

## <a name="implementingassembly"></a><span data-ttu-id="5f9b3-118">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="5f9b3-118">ImplementingAssembly</span></span>

<span data-ttu-id="5f9b3-119">Um novo campo **ImplementingAssembly**, foi adicionado ao ModuleInfo.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-119">A new field, **ImplementingAssembly**, has been added to ModuleInfo.</span></span> <span data-ttu-id="5f9b3-120">Ele é definido para o assembly dinâmico criado para um módulo de script, se o script define classes ou o assembly carregado para módulos binários.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-120">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="5f9b3-121">Não é definida quando ModuleType = manifesto.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-121">It is not set when ModuleType = Manifest.</span></span>

<span data-ttu-id="5f9b3-122">Reflexão sobre o **ImplementingAssembly** campo Deteta os recursos num módulo.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-122">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="5f9b3-123">Isso significa que pode detetar recursos escritos no PowerShell ou outras linguagens gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-123">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="5f9b3-124">Campos com inicializadores de:</span><span class="sxs-lookup"><span data-stu-id="5f9b3-124">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="5f9b3-125">Estática é suportada; ele funciona como um atributo, tal como as restrições de tipo, portanto, podem ser especificado por qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-125">Static is supported; it works like an attribute, as do the type constraints, so it can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="5f9b3-126">Um tipo é opcional.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-126">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="5f9b3-127">Todos os membros são públicos.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-127">All members are public.</span></span>

## <a name="constructors-and-instantiation"></a><span data-ttu-id="5f9b3-128">Construtores e a instanciação</span><span class="sxs-lookup"><span data-stu-id="5f9b3-128">Constructors and instantiation</span></span>

<span data-ttu-id="5f9b3-129">Classes do Windows PowerShell podem ter construtores; eles têm o mesmo nome que sua classe.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-129">Windows PowerShell classes can have constructors; they have the same name as their class.</span></span> <span data-ttu-id="5f9b3-130">Construtores podem ser sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-130">Constructors can be overloaded.</span></span> <span data-ttu-id="5f9b3-131">São suportados construtores estáticos.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-131">Static constructors are supported.</span></span> <span data-ttu-id="5f9b3-132">Propriedades com expressões de inicialização são inicializadas antes de executar qualquer código num construtor.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-132">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="5f9b3-133">Propriedades estáticas são inicializadas antes do corpo de um construtor estático e propriedades de instância são inicializadas antes do corpo do construtor não estático.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-133">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="5f9b3-134">Atualmente, não há nenhuma sintaxe para chamar um construtor de outro construtor (como o C\# sintaxe ": this()").</span><span class="sxs-lookup"><span data-stu-id="5f9b3-134">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="5f9b3-135">A solução alternativa é definir um método comum de Init.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-135">The workaround is to define a common Init method.</span></span>

<span data-ttu-id="5f9b3-136">Seguem-se formas de criar uma instância de classes nesta versão.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-136">The following are ways of instantiating classes in this release.</span></span>

<span data-ttu-id="5f9b3-137">Criar uma instância ao utilizar o construtor padrão.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-137">Instantiating by using the default constructor.</span></span> <span data-ttu-id="5f9b3-138">Tenha em atenção que New-Object não é suportado nesta versão.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-138">Note that New-Object is not supported in this release.</span></span>

```powershell
$a = [MyClass]::new()
```

<span data-ttu-id="5f9b3-139">Chamar um construtor com um parâmetro</span><span class="sxs-lookup"><span data-stu-id="5f9b3-139">Calling a constructor with a parameter</span></span>

```powershell
$b = [MyClass]::new(42)
```

<span data-ttu-id="5f9b3-140">Transmitir uma matriz para um construtor com vários parâmetros</span><span class="sxs-lookup"><span data-stu-id="5f9b3-140">Passing an array to a constructor with multiple parameters</span></span>
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

<span data-ttu-id="5f9b3-141">Nesta versão, New-Object não funciona com classes definidas no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-141">In this release, New-Object does not work with classes defined in Windows PowerShell.</span></span> <span data-ttu-id="5f9b3-142">Também nesta versão, o nome do tipo só é visível lexicalmente, ou seja, não são visível fora da módulo ou script que define a classe.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-142">Also for this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="5f9b3-143">As funções podem devolver instâncias de uma classe definida no Windows PowerShell e instâncias funcionam bem fora o módulo ou script.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-143">Functions can return instances of a class defined in Windows PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="5f9b3-144">`Get-Member -Static` lista construtores, para que pode exibir sobrecargas como qualquer outro método.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-144">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="5f9b3-145">O desempenho dessa sintaxe também é consideravelmente mais rápido do que New-Object.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-145">The performance of this syntax is also considerably faster than New-Object.</span></span>

<span data-ttu-id="5f9b3-146">O método de pseudo-estático denominado **novo** funciona com tipos .NET, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-146">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

<span data-ttu-id="5f9b3-147">Agora, pode ver as sobrecargas de construtor com Get-Member, ou como mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="5f9b3-147">You can now see constructor overloads with Get-Member, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a><span data-ttu-id="5f9b3-148">Métodos</span><span class="sxs-lookup"><span data-stu-id="5f9b3-148">Methods</span></span>

<span data-ttu-id="5f9b3-149">Um método de classe do Windows PowerShell é implementado como um ScriptBlock que tenha apenas um bloco final.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-149">A Windows PowerShell class method is implemented as a ScriptBlock that has only an end block.</span></span> <span data-ttu-id="5f9b3-150">Todos os métodos são públicos.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-150">All methods are public.</span></span> <span data-ttu-id="5f9b3-151">O seguinte mostra um exemplo de definir um método chamado **DoSomething**.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-151">The following shows an example of defining a method named **DoSomething**.</span></span>

```powershell
class MyClass
{
    DoSomething($x)
    {
        $this._doSomething($x) # method syntax
    }
    private _doSomething($a) {}
}
```

<span data-ttu-id="5f9b3-152">Invocação de método:</span><span class="sxs-lookup"><span data-stu-id="5f9b3-152">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="5f9b3-153">Sobrecarregado métodos – ou seja, aqueles que estão com o mesmo nome como um método existente, mas diferenciadas por seus valores especificados – também são suportados.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-153">Overloaded methods--that is, those that are named the same as an existing method, but differentiated by their specified values--are also supported.</span></span>

## <a name="properties"></a><span data-ttu-id="5f9b3-154">Propriedades</span><span class="sxs-lookup"><span data-stu-id="5f9b3-154">Properties</span></span>

<span data-ttu-id="5f9b3-155">Todas as propriedades são públicas.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-155">All properties are public.</span></span> <span data-ttu-id="5f9b3-156">As propriedades requerem uma nova linha ou um ponto e vírgula.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-156">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="5f9b3-157">Se não for especificado nenhum tipo de objeto, o tipo de propriedade é o objeto.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-157">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="5f9b3-158">Propriedades que usam os atributos de validação ou atributos de transformação do argumento (por exemplo, `[ValidateSet("aaa")]`) funcionar conforme esperado.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-158">Properties that use validation attributes or argument transformation attributes (e.g. `[ValidateSet("aaa")]`) work as expected.</span></span>

## <a name="hidden"></a><span data-ttu-id="5f9b3-159">Oculto</span><span class="sxs-lookup"><span data-stu-id="5f9b3-159">Hidden</span></span>

<span data-ttu-id="5f9b3-160">Uma nova palavra-chave **Hidden**, foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-160">A new keyword, **Hidden**, has been added.</span></span> <span data-ttu-id="5f9b3-161">**Oculto** podem ser aplicados a propriedades e métodos (incluindo construtores).</span><span class="sxs-lookup"><span data-stu-id="5f9b3-161">**Hidden** can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="5f9b3-162">Os membros ocultos são públicos, mas não aparecem na saída do Get-Member, a menos que a opção - Force adicionado o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-162">Hidden members are public, but do not appear in the output of Get-Member unless the -Force parameter is added.</span></span>

<span data-ttu-id="5f9b3-163">Oculto a membros não estão incluídos quando separador a conclusão ou usando o Intellisense, a menos que a conclusão ocorre na classe definindo o membro oculto.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-163">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="5f9b3-164">Um novo atributo **System.Management.Automation.HiddenAttribute** foi adicionada para que C# código pode ter a mesma semântica dentro do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-164">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C# code can have the same semantics within Windows PowerShell.</span></span>

## <a name="return-types"></a><span data-ttu-id="5f9b3-165">Tipos de retorno</span><span class="sxs-lookup"><span data-stu-id="5f9b3-165">Return types</span></span>

<span data-ttu-id="5f9b3-166">Tipo de retorno é um contrato; o valor de retorno é convertido para o tipo esperado.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-166">Return type is a contract; the return value is converted to the expected type.</span></span> <span data-ttu-id="5f9b3-167">Se não for especificado nenhum tipo de retorno, o tipo de retorno é void.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-167">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="5f9b3-168">Não existe nenhum de transmissão em fluxo de objetos; Objetos não podem ser escritos para o pipeline, intencionalmente ou acidentalmente.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-168">There is no streaming of objects; objects cannot be written to the pipeline either intentionally or by accident.</span></span>

## <a name="attributes"></a><span data-ttu-id="5f9b3-169">Atributos</span><span class="sxs-lookup"><span data-stu-id="5f9b3-169">Attributes</span></span>

<span data-ttu-id="5f9b3-170">Dois novos atributos **DscResource** e **DscProperty** foram adicionados.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-170">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

## <a name="lexical-scoping-of-variables"></a><span data-ttu-id="5f9b3-171">Controlo de âmbito léxica de variáveis</span><span class="sxs-lookup"><span data-stu-id="5f9b3-171">Lexical scoping of variables</span></span>

<span data-ttu-id="5f9b3-172">O seguinte mostra um exemplo de como léxico funciona âmbito nesta versão.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-172">The following shows an example of how lexical scoping works in this release.</span></span>

```powershell
$d = 42 # Script scope

function bar
{
    $d = 0 # Function scope
    [MyClass]::DoSomething()
}

class MyClass
{
    static [object] DoSomething()
    {
        return $d # error, not found dynamically
        return $script:d # no error
        $d = $script:d
        return $d # no error, found lexically
    }
}

$v = bar
$v -eq $d # true
```

## <a name="end-to-end-example"></a><span data-ttu-id="5f9b3-173">Exemplo de ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="5f9b3-173">End-to-End Example</span></span>

<span data-ttu-id="5f9b3-174">O exemplo seguinte cria várias classes novas, personalizados para implementar uma linguagem de folha de estilo dinâmica de HTML (DSL).</span><span class="sxs-lookup"><span data-stu-id="5f9b3-174">The following example creates several new, custom classes to implement an HTML dynamic style sheet language (DSL).</span></span>
<span data-ttu-id="5f9b3-175">Em seguida, o exemplo adiciona funções de programa auxiliar para criar tipos de elementos específicos como parte da classe elemento, como estilos de cabeçalho e tabelas, porque os tipos não podem ser utilizados fora do escopo de um módulo.</span><span class="sxs-lookup"><span data-stu-id="5f9b3-175">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

```powershell
# Classes that define the structure of the document
#
class Html
{
    [string] $docType
    [HtmlHead] $Head
    [Element[]] $Body

    [string] Render()
    {
        $text = "<html>`n<head>`n"
        $text += $this.Head
        $text += "`n</head>`n<body>`n"
        $text += $this.Body -join "`n" # Render all of the body elements
        $text += "</body>`n</html>"
        return $text
    }
    [string] ToString() { return $this.Render() }
}

class HtmlHead
{
    $Title
    $Base
    $Link
    $Style
    $Meta
    $Script
    [string] Render() { return "<title>$($this.Title)</title>" }
    [string] ToString() { return $this.Render() }
}

class Element
{
    [string] $Tag
    [string] $Text
    [hashtable] $Attributes
    [string] Render() {
        $attributesText= ""
        if ($this.Attributes)
        {
            foreach ($attr in $this.Attributes.Keys)
            {
                #BUGBUG - need to validate keys against attribute
                $attributesText += " $attr=`"$($this.Attributes[$attr])\`""
            }
        }
        return "<$($this.tag)${attributesText}>$($this.text)</$($this.tag)>`n"
    }
[string] ToString() { return $this.Render() }
}

#
# Helper functions for creating specific element types on top of the classes.
# These are required because types aren’t visible outside of the module.
#

function H1 { [Element] @{ Tag = "H1" ; Text = $args.foreach{$_} -join " " }}
function H2 { [Element] @{ Tag = "H2" ; Text = $args.foreach{$_} -join " " }}
function H3 { [Element] @{ Tag = "H3" ; Text = $args.foreach{$_} -join " " }}
function P { [Element] @{ Tag = "P" ; Text = $args.foreach{$_} -join " " }}
function B { [Element] @{ Tag = "B" ; Text = $args.foreach{$_} -join " " }}
function I { [Element] @{ Tag = "I" ; Text = $args.foreach{$_} -join " " }}
function HREF
{
    param (
        $Name,
        $Link
    )
    return [Element] @{
        Tag = "A"
        Attributes = @{ HREF = $link }
        Text = $name
    }
}
function Table
{
    param (
    [Parameter(Mandatory)]
    [object[]]
        $Data,
    [Parameter()]
    [string[]]
        $Properties = "*",
    [Parameter()]
    [hashtable]
        $Attributes = @{ border=2; cellpadding=2; cellspacing=2 }
    )
$bodyText = ""
# Add the header tags
$bodyText += $Properties.foreach{TH $_}
# Add the rows
$bodyText += foreach ($row in $Data)
    {
        TR (-join $Properties.Foreach{ TD ($row.$_) } )
    }

    $table = [Element] @{
        Tag = "Table"
        Attributes = $Attributes
        Text = $bodyText
    }
$table
}
function TH { ([Element] @{ Tag = "TH" ; Text = $args.foreach{$_} -join " " }) }
function TR { ([Element] @{ Tag = "TR" ; Text = $args.foreach{$_} -join " " }) }
function TD { ([Element] @{ Tag = "TD" ; Text = $args.foreach{$_} -join " " }) }
function Style

{
    return [Element] @{
        Tag = "style"
        Text = "$args"
    }
}

# Takes a hash table, casts it to and HTML document
# and then returns the resulting type.
#
function Html ([HTML] $doc) { return $doc }
```
