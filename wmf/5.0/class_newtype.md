---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9aa7e92632c671751020687ddbfc374eeda7148b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="81be2-102">Novas funcionalidades de idioma no PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="81be2-102">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="81be2-103">PowerShell 5.0 apresenta os seguintes elementos de linguagem nova no Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="81be2-103">PowerShell 5.0 introduces the following new language elements in Windows PowerShell:</span></span>

## <a name="class-keyword"></a><span data-ttu-id="81be2-104">Classe de palavra-chave</span><span class="sxs-lookup"><span data-stu-id="81be2-104">Class keyword</span></span>

<span data-ttu-id="81be2-105">O **classe** palavra-chave define uma nova classe.</span><span class="sxs-lookup"><span data-stu-id="81be2-105">The **class** keyword defines a new class.</span></span> <span data-ttu-id="81be2-106">Este é um valor de true tipo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="81be2-106">This is a true .NET Framework type.</span></span>
<span data-ttu-id="81be2-107">São membros de classe pública, mas apenas público no âmbito do módulo.</span><span class="sxs-lookup"><span data-stu-id="81be2-107">Class members are public, but only public within the module scope.</span></span>
<span data-ttu-id="81be2-108">Não pode referenciar o nome do tipo como uma cadeia (por exemplo, `New-Object` não funciona), e nesta versão, não é possível utilizar um literal do tipo (por exemplo, `[MyClass]`) fora o ficheiro de módulo do script no qual a classe estiver definida.</span><span class="sxs-lookup"><span data-stu-id="81be2-108">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script/module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="81be2-109">Palavra-chave de enum e enumerações</span><span class="sxs-lookup"><span data-stu-id="81be2-109">Enum keyword and enumerations</span></span>

<span data-ttu-id="81be2-110">Suporte para o **enum** palavra-chave foi adicionado, que utiliza a nova linha como o delimitador.</span><span class="sxs-lookup"><span data-stu-id="81be2-110">Support for the **enum** keyword has been added, which uses newline as the delimiter.</span></span>
<span data-ttu-id="81be2-111">Limitações atuais: não é possível definir um enumerador em termos de si próprio, mas pode inicializar uma enumeração em termos de outro enum, conforme mostrado no exemplo seguinte.</span><span class="sxs-lookup"><span data-stu-id="81be2-111">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize an enum in terms of another enum, as shown in the following example.</span></span>
<span data-ttu-id="81be2-112">Além disso, atualmente não é possível especificar o tipo base; é sempre [int].</span><span class="sxs-lookup"><span data-stu-id="81be2-112">Also, the base type cannot currently be specified; it is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="81be2-113">Um valor de enumerador tem de ser uma constante de tempo de análise; Não é possível defini-lo para o resultado de um comando invocado.</span><span class="sxs-lookup"><span data-stu-id="81be2-113">An enumerator value must be a parse time constant; you cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="81be2-114">As enumerações suportam operações aritméticas, conforme mostrado no exemplo seguinte.</span><span class="sxs-lookup"><span data-stu-id="81be2-114">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a><span data-ttu-id="81be2-115">Importar DscResource</span><span class="sxs-lookup"><span data-stu-id="81be2-115">Import-DscResource</span></span>

<span data-ttu-id="81be2-116">**Importar DscResource** agora é uma palavra-chave dinâmica verdadeira.</span><span class="sxs-lookup"><span data-stu-id="81be2-116">**Import-DscResource** is now a true dynamic keyword.</span></span>
<span data-ttu-id="81be2-117">PowerShell analisa o módulo de raiz do módulo especificado, a procurar classes que contêm o **DscResource** atributo.</span><span class="sxs-lookup"><span data-stu-id="81be2-117">PowerShell parses the specified module’s root module, searching for classes that contain the **DscResource** attribute.</span></span>

## <a name="implementingassembly"></a><span data-ttu-id="81be2-118">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="81be2-118">ImplementingAssembly</span></span>

<span data-ttu-id="81be2-119">Um novo campo **ImplementingAssembly**, foi adicionada ao ModuleInfo.</span><span class="sxs-lookup"><span data-stu-id="81be2-119">A new field, **ImplementingAssembly**, has been added to ModuleInfo.</span></span> <span data-ttu-id="81be2-120">Está definido para a assemblagem dinâmica criado para um módulo de script, se o script define as classes, ou a assemblagem carregada para módulos binários.</span><span class="sxs-lookup"><span data-stu-id="81be2-120">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="81be2-121">Não é definido quando ModuleType = manifesto.</span><span class="sxs-lookup"><span data-stu-id="81be2-121">It is not set when ModuleType = Manifest.</span></span>

<span data-ttu-id="81be2-122">Reflexão no **ImplementingAssembly** campo Deteta recursos num módulo.</span><span class="sxs-lookup"><span data-stu-id="81be2-122">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="81be2-123">Isto significa que pode descobrir recursos escritos no PowerShell ou outros idiomas geridos.</span><span class="sxs-lookup"><span data-stu-id="81be2-123">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="81be2-124">Campos com inicializadores:</span><span class="sxs-lookup"><span data-stu-id="81be2-124">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="81be2-125">Estática é suportada; funciona como um atributo, tal como as restrições de tipo, pelo que pode ser especificado por qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="81be2-125">Static is supported; it works like an attribute, as do the type constraints, so it can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="81be2-126">Um tipo é opcional.</span><span class="sxs-lookup"><span data-stu-id="81be2-126">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="81be2-127">Todos os membros são públicos.</span><span class="sxs-lookup"><span data-stu-id="81be2-127">All members are public.</span></span>

## <a name="constructors-and-instantiation"></a><span data-ttu-id="81be2-128">Construtores e Instanciação</span><span class="sxs-lookup"><span data-stu-id="81be2-128">Constructors and instantiation</span></span>

<span data-ttu-id="81be2-129">Classes do Windows PowerShell podem ter construtores; têm o mesmo nome que a respetiva classe.</span><span class="sxs-lookup"><span data-stu-id="81be2-129">Windows PowerShell classes can have constructors; they have the same name as their class.</span></span> <span data-ttu-id="81be2-130">Construtores podem estar sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="81be2-130">Constructors can be overloaded.</span></span> <span data-ttu-id="81be2-131">São suportados construtores estáticos.</span><span class="sxs-lookup"><span data-stu-id="81be2-131">Static constructors are supported.</span></span> <span data-ttu-id="81be2-132">Propriedades com expressões de inicialização são inicializadas antes de executar qualquer código num construtor.</span><span class="sxs-lookup"><span data-stu-id="81be2-132">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="81be2-133">As propriedades estáticas são inicializadas antes do corpo do construtor estático e as propriedades da instância estão inicializadas antes do corpo do construtor não estático.</span><span class="sxs-lookup"><span data-stu-id="81be2-133">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="81be2-134">Atualmente, não há nenhuma sintaxe para chamar um construtor de outro construtor (como o C\# sintaxe ": this()").</span><span class="sxs-lookup"><span data-stu-id="81be2-134">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="81be2-135">A solução é para definir um método Init comum.</span><span class="sxs-lookup"><span data-stu-id="81be2-135">The workaround is to define a common Init method.</span></span>

<span data-ttu-id="81be2-136">Seguem-se formas de classes instanciar nesta versão.</span><span class="sxs-lookup"><span data-stu-id="81be2-136">The following are ways of instantiating classes in this release.</span></span>

<span data-ttu-id="81be2-137">Instanciar utilizando o construtor predefinido.</span><span class="sxs-lookup"><span data-stu-id="81be2-137">Instantiating by using the default constructor.</span></span> <span data-ttu-id="81be2-138">Tenha em atenção que o New-Object não é suportado nesta versão.</span><span class="sxs-lookup"><span data-stu-id="81be2-138">Note that New-Object is not supported in this release.</span></span>

```powershell
$a = [MyClass]::new()
```

<span data-ttu-id="81be2-139">Chamar um construtor com um parâmetro</span><span class="sxs-lookup"><span data-stu-id="81be2-139">Calling a constructor with a parameter</span></span>

```powershell
$b = [MyClass]::new(42)
```

<span data-ttu-id="81be2-140">Transmitir uma matriz para um construtor com vários parâmetros</span><span class="sxs-lookup"><span data-stu-id="81be2-140">Passing an array to a constructor with multiple parameters</span></span>
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

<span data-ttu-id="81be2-141">Nesta versão, New-Object não funciona com classes definidas no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="81be2-141">In this release, New-Object does not work with classes defined in Windows PowerShell.</span></span> <span data-ttu-id="81be2-142">Também nesta versão, o nome do tipo só é visível lexically, ou seja, não são visível fora do módulo ou script que define a classe.</span><span class="sxs-lookup"><span data-stu-id="81be2-142">Also for this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="81be2-143">As funções podem devolver instâncias de uma classe definida no Windows PowerShell e instâncias de trabalho também fora do módulo ou script.</span><span class="sxs-lookup"><span data-stu-id="81be2-143">Functions can return instances of a class defined in Windows PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="81be2-144">`Get-Member -Static` lista construtores, para que possa vê sobrecargas como qualquer outro método.</span><span class="sxs-lookup"><span data-stu-id="81be2-144">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="81be2-145">O desempenho desta sintaxe também é significativamente mais rápido do que New-Object.</span><span class="sxs-lookup"><span data-stu-id="81be2-145">The performance of this syntax is also considerably faster than New-Object.</span></span>

<span data-ttu-id="81be2-146">O método pseudo-estático denominado **novo** funciona com tipos de .NET, conforme mostrado no exemplo seguinte.</span><span class="sxs-lookup"><span data-stu-id="81be2-146">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

<span data-ttu-id="81be2-147">Agora, pode ver as sobrecargas de construtor com membro Get, ou como o mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="81be2-147">You can now see constructor overloads with Get-Member, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a><span data-ttu-id="81be2-148">Métodos</span><span class="sxs-lookup"><span data-stu-id="81be2-148">Methods</span></span>

<span data-ttu-id="81be2-149">Um método de classe do Windows PowerShell é implementado como um ScriptBlock que tenha apenas um bloco de fim.</span><span class="sxs-lookup"><span data-stu-id="81be2-149">A Windows PowerShell class method is implemented as a ScriptBlock that has only an end block.</span></span> <span data-ttu-id="81be2-150">Todos os métodos são públicos.</span><span class="sxs-lookup"><span data-stu-id="81be2-150">All methods are public.</span></span> <span data-ttu-id="81be2-151">O seguinte mostra um exemplo de definir um método denominado **DoSomething**.</span><span class="sxs-lookup"><span data-stu-id="81be2-151">The following shows an example of defining a method named **DoSomething**.</span></span>

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

<span data-ttu-id="81be2-152">Invocação de métodos:</span><span class="sxs-lookup"><span data-stu-id="81be2-152">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="81be2-153">Sobrecarregado métodos - ou seja, os que são com o mesmo método existente, mas diferenciadas pelos respetivos valores especificados – também são suportados.</span><span class="sxs-lookup"><span data-stu-id="81be2-153">Overloaded methods--that is, those that are named the same as an existing method, but differentiated by their specified values--are also supported.</span></span>

## <a name="properties"></a><span data-ttu-id="81be2-154">Propriedades</span><span class="sxs-lookup"><span data-stu-id="81be2-154">Properties</span></span>

<span data-ttu-id="81be2-155">Todas as propriedades são públicas.</span><span class="sxs-lookup"><span data-stu-id="81be2-155">All properties are public.</span></span> <span data-ttu-id="81be2-156">Propriedades necessitam de uma nova linha ou um ponto e vírgula.</span><span class="sxs-lookup"><span data-stu-id="81be2-156">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="81be2-157">Não se for especificado nenhum tipo de objeto, o tipo de propriedade é o objeto.</span><span class="sxs-lookup"><span data-stu-id="81be2-157">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="81be2-158">Propriedades que utilizam os atributos de validação ou atributos de transformação do argumento (por exemplo, `[ValidateSet("aaa")]`) funcionam como esperado.</span><span class="sxs-lookup"><span data-stu-id="81be2-158">Properties that use validation attributes or argument transformation attributes (e.g. `[ValidateSet("aaa")]`) work as expected.</span></span>

## <a name="hidden"></a><span data-ttu-id="81be2-159">Oculto</span><span class="sxs-lookup"><span data-stu-id="81be2-159">Hidden</span></span>

<span data-ttu-id="81be2-160">Uma nova palavra-chave, **Hidden**, foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="81be2-160">A new keyword, **Hidden**, has been added.</span></span> <span data-ttu-id="81be2-161">**Oculto** podem ser aplicadas às propriedades e métodos (incluindo construtores).</span><span class="sxs-lookup"><span data-stu-id="81be2-161">**Hidden** can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="81be2-162">Os membros ocultos são públicos, mas não são apresentados no resultado de Get-membro, a menos que-Force é adicionado o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="81be2-162">Hidden members are public, but do not appear in the output of Get-Member unless the -Force parameter is added.</span></span>

<span data-ttu-id="81be2-163">Oculta a membros não estão incluídos quando separador concluir ou utilizando o Intellisense, a menos que ocorre após a conclusão da classe que define o membro oculto.</span><span class="sxs-lookup"><span data-stu-id="81be2-163">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="81be2-164">Um novo atributo **System.Management.Automation.HiddenAttribute** foi adicionada para que o código c# pode ter a mesma semântica dentro do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="81be2-164">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C# code can have the same semantics within Windows PowerShell.</span></span>

## <a name="return-types"></a><span data-ttu-id="81be2-165">Tipos de retorno</span><span class="sxs-lookup"><span data-stu-id="81be2-165">Return types</span></span>

<span data-ttu-id="81be2-166">Tipo de retorno é um contrato; o valor de retorno é convertido para o tipo esperado.</span><span class="sxs-lookup"><span data-stu-id="81be2-166">Return type is a contract; the return value is converted to the expected type.</span></span> <span data-ttu-id="81be2-167">Não se for especificado nenhum tipo de retorno, o tipo de retorno é nulo.</span><span class="sxs-lookup"><span data-stu-id="81be2-167">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="81be2-168">Não há nenhum de transmissão em fluxo de objetos; Objetos não podem ser escritos para o pipeline intencionalmente ou acidentalmente.</span><span class="sxs-lookup"><span data-stu-id="81be2-168">There is no streaming of objects; objects cannot be written to the pipeline either intentionally or by accident.</span></span>

## <a name="attributes"></a><span data-ttu-id="81be2-169">Atributos</span><span class="sxs-lookup"><span data-stu-id="81be2-169">Attributes</span></span>

<span data-ttu-id="81be2-170">Dois novos atributos, **DscResource** e **DscProperty** foram adicionados.</span><span class="sxs-lookup"><span data-stu-id="81be2-170">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

## <a name="lexical-scoping-of-variables"></a><span data-ttu-id="81be2-171">Controlo de âmbito lexical das variáveis</span><span class="sxs-lookup"><span data-stu-id="81be2-171">Lexical scoping of variables</span></span>

<span data-ttu-id="81be2-172">O seguinte mostra um exemplo de como lexical funciona âmbito nesta versão.</span><span class="sxs-lookup"><span data-stu-id="81be2-172">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="81be2-173">Exemplo de ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="81be2-173">End-to-End Example</span></span>

<span data-ttu-id="81be2-174">O exemplo seguinte cria várias classes novas e personalizadas para implementar um idioma de folha de estilo dinâmica HTML (DSL).</span><span class="sxs-lookup"><span data-stu-id="81be2-174">The following example creates several new, custom classes to implement an HTML dynamic style sheet language (DSL).</span></span>
<span data-ttu-id="81be2-175">Em seguida, o exemplo adiciona funções de programa auxiliar para criar tipos de elemento específico como parte da classe de elemento, tais como os estilos do cabeçalho e tabelas, porque os tipos não podem ser utilizados fora do âmbito de um módulo.</span><span class="sxs-lookup"><span data-stu-id="81be2-175">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
        TR (-join $Properties.Foreach{ TD ($row.$\_) } )
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
