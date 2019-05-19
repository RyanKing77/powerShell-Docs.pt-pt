---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Criar Tipos Personalizados com as Classes do PowerShell
ms.openlocfilehash: 0dd5bbaca50abb746e15a7bb64a706c7eceee905
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856239"
---
# <a name="creating-custom-types-using-powershell-classes"></a>Criar Tipos Personalizados com as Classes do PowerShell

PowerShell 5.0 adicionada a capacidade de definir as classes e outros tipos definidos pelo usuário usando a sintaxe formal e semântica, como de outras linguagens de programação orientada a objeto. O objetivo é permitir que desenvolvedores e profissionais de TI a adotar o PowerShell para um maior número de casos de utilização, simplificar o desenvolvimento de artefatos de PowerShell (como recursos de DSC) e acelerar a cobertura de superfícies de gestão.

## <a name="supported-scenarios-in-this-release"></a>Cenários suportados nesta versão

- Definir os recursos de DSC e seus tipos associado através da linguagem do PowerShell
- Defina tipos personalizados no PowerShell com o familiares e orientada a objeto construções de programação, como classes, propriedades, métodos, etc.
- Suporte de herança com a classe no PowerShell e a classe base recursos de DSC
- Tipos de depuração através da linguagem do PowerShell
- Gerar e manipular exceções, utilizando os mecanismos formais e no nível certo

# <a name="declare-base-class"></a>Declarar a Classe Base

É possível declarar uma classe do PowerShell como um tipo base para outra classe de PowerShell.

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

Também pode utilizar tipos existentes do .NET Framework como base classes:

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

# <a name="call-base-class-constructor"></a>Chamar o Construtor de Classe Base

Para chamar um construtor de classe base a partir de uma subclasse, utilize a palavra-chave **base**:

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

Se uma classe base tem um construtor padrão (nenhum parâmetro), pode omitir uma chamada de construtor explícito:

```powershell
class C : B
{
    C([int]$c) {}
}
```

# <a name="call-base-class-method"></a>Chamar o Método de Classe Base

Pode substituir os métodos existentes numa subclasse. Para tal, declare métodos, utilizando o mesmo nome e assinatura:

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

Para chamar os métodos de classe base das implementações substituídas, converter para a classe base (`[baseClass]$this`) na invocação:

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

Todos os métodos do PowerShell são virtuais. Pode ocultar métodos não virtuais do .NET numa subclasse usando a mesma sintaxe tal como sucede para uma substituição, ao declarar métodos com o mesmo nome e assinatura.

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

# <a name="declare-implemented-interface"></a>Declarar a Interface Implementada

É possível declarar interfaces implementadas após tipos base ou imediatamente após dois pontos (:), se não houver nenhum tipo base especificado. Separe todos os nomes de tipo utilizando vírgulas. Isso é semelhante a C# sintaxe.

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

# <a name="new-language-features-in-powershell-50"></a>Novos recursos de linguagem no PowerShell 5.0

PowerShell 5.0 introduz os seguintes novos elementos de linguagem no PowerShell:

## <a name="class-keyword"></a>Palavra-chave de classe

O `class` palavra-chave define uma nova classe. Esta é uma verdadeira tipo do .NET Framework. Membros de classe são públicos, mas apenas público dentro do escopo do módulo. Não é possível consultar o nome do tipo como cadeia de caracteres (por exemplo, `New-Object` não funciona), e nesta versão, não é possível utilizar um literal de tipo (por exemplo, `[MyClass]`) fora o ficheiro de script ou módulo no qual a classe é definida.

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a>Palavra-chave de enumeração e enumerações

Suporte para o `enum` palavra-chave tiver sido adicionado, que utiliza o caractere de nova linha como o delimitador. Atualmente, não é possível definir um enumerador em termos de propriamente dito. No entanto, pode inicializar um enum em termos de outro enum, conforme mostrado no exemplo a seguir. Além disso, não é possível especificar o tipo base; é sempre `[int]`.

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Um valor de enumerador tem de ser uma constante de tempo de análise. Não é possível defini-lo para o resultado de um comando invocado.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Enums suporta operações aritméticas, conforme mostrado no exemplo a seguir.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a>Import-DscResource

`Import-DscResource` Agora é uma palavra-chave dynamic verdadeira. PowerShell analisa o módulo de raiz do módulo especificado, pesquisa de classes que contêm os **DscResource** atributo.

## <a name="implementingassembly"></a>ImplementingAssembly

Um novo campo **ImplementingAssembly**, foi adicionado ao **ModuleInfo**. Ele é definido para o assembly dinâmico criado para um módulo de script, se o script define classes ou o assembly carregado para módulos binários. Não é definida quando **ModuleType** é **manifesto**.

Reflexão sobre o **ImplementingAssembly** campo Deteta os recursos num módulo. Isso significa que pode detetar recursos escritos no PowerShell ou outras linguagens gerenciadas.

Campos com inicializadores de:

```powershell
[int] $i = 5
```

`Static` é suportada. Ele funciona como um atributo, tal como as restrições de tipo. Podem ser especificado por qualquer ordem.

```powershell
static [int] $count = 0
```

Um tipo é opcional.

```powershell
$s = "hello"
```

Todos os membros são públicos.

## <a name="constructors-and-instantiation"></a>Construtores e a instanciação

Classes do PowerShell podem ter construtores. Eles têm o mesmo nome que sua classe. Construtores podem ser sobrecarregados. São suportados construtores estáticos. Propriedades com expressões de inicialização são inicializadas antes de executar qualquer código num construtor. Propriedades estáticas são inicializadas antes do corpo de um construtor estático e propriedades de instância são inicializadas antes do corpo do construtor não estático. Atualmente, não há nenhuma sintaxe para chamar um construtor de outro construtor (como o C\# sintaxe ": this()"). A solução alternativa é definir uma comum `Init()` método.

### <a name="creating-instances"></a>Criação de instâncias

> [!NOTE]
> No PowerShell 5.0, `New-Object` não funciona com classes definidas no PowerShell. Além disso, o nome do tipo só é visível lexicalmente, ou seja, não são visível fora da módulo ou script que define a classe. As funções podem devolver instâncias de uma classe definida no PowerShell. Essas instâncias de trabalho fora do módulo ou script.

1. Criar uma instância ao utilizar o construtor padrão.

   ```powershell
   $a = [MyClass]::new()
   ```

1. Chamar um construtor com um parâmetro

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. Transmitir uma matriz para um construtor com vários parâmetros.

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

O método pseudo-estático `new()` funciona com tipos .NET, conforme mostrado no exemplo a seguir.

```powershell
[hashtable]::new()
```

### <a name="discovering-constructors"></a>Construtores de deteção

Agora, pode ver sobrecargas de construtor com `Get-Member`, ou conforme mostrado neste exemplo:

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

`Get-Member -Static` lista construtores, para que pode exibir sobrecargas como qualquer outro método. O desempenho dessa sintaxe também é consideravelmente mais rápido do que `New-Object`.

## <a name="methods"></a>Métodos

Um método de classe do PowerShell é implementado como um **ScriptBlock** que tem apenas um bloco final. Todos os métodos são públicos. O seguinte mostra um exemplo de definir um método chamado **DoSomething**.

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

Invocação de método:

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

Também são suportados métodos sobrecarregados.

## <a name="properties"></a>Propriedades

Todas as propriedades são públicas. As propriedades requerem uma nova linha ou um ponto e vírgula. Se não for especificado nenhum tipo de objeto, o tipo de propriedade é o objeto.

Propriedades que utilizam a validação ou argumento atributos de transformação (como `[ValidateSet("aaa")]`) funcionar conforme esperado.

## <a name="hidden"></a>Oculto

Uma nova palavra-chave, `Hidden`, foi adicionado. `Hidden` podem ser aplicadas a propriedades e métodos (incluindo construtores).

Os membros ocultos são públicos, mas não aparecem na saída do `Get-Member` , a menos que a opção - Force adicionado o parâmetro. Oculto a membros não estão incluídos quando separador a conclusão ou usando o Intellisense, a menos que a conclusão ocorre na classe definindo o membro oculto.

Um novo atributo **System.Management.Automation.HiddenAttribute** foi adicionada para que C\# código pode ter a mesma semântica dentro do PowerShell.

## <a name="return-types"></a>Tipos de retorno

Tipo de retorno é um contrato. O valor de retorno é convertido para o tipo esperado. Se não for especificado nenhum tipo de retorno, o tipo de retorno é **void**. Não existe nenhum de transmissão em fluxo de objetos. Bbjects não pode ser escrito para o pipeline, intencionalmente ou acidentalmente.

## <a name="attributes"></a>Atributos

Dois novos atributos **DscResource** e **DscProperty** foram adicionados.

## <a name="lexical-scoping-of-variables"></a>Controlo de âmbito léxica de variáveis

O seguinte mostra um exemplo de como léxico funciona âmbito nesta versão.

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

## <a name="end-to-end-example"></a>Exemplo de ponto a ponto

O exemplo seguinte cria algumas classes personalizadas para implementar uma linguagem de folha de estilo dinâmica de HTML (DSL). Em seguida, o exemplo adiciona funções de programa auxiliar para criar tipos de elementos específicos como parte da classe elemento, como estilos de cabeçalho e tabelas, porque os tipos não podem ser utilizados fora do escopo de um módulo.

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
# These are required because types aren't visible outside of the module.
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
