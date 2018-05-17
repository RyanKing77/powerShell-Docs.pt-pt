---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9aa7e92632c671751020687ddbfc374eeda7148b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="new-language-features-in-powershell-50"></a>Novas funcionalidades de idioma no PowerShell 5.0

PowerShell 5.0 apresenta os seguintes elementos de linguagem nova no Windows PowerShell:

## <a name="class-keyword"></a>Classe de palavra-chave

O **classe** palavra-chave define uma nova classe. Este é um valor de true tipo .NET Framework.
São membros de classe pública, mas apenas público no âmbito do módulo.
Não pode referenciar o nome do tipo como uma cadeia (por exemplo, `New-Object` não funciona), e nesta versão, não é possível utilizar um literal do tipo (por exemplo, `[MyClass]`) fora o ficheiro de módulo do script no qual a classe estiver definida.

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a>Palavra-chave de enum e enumerações

Suporte para o **enum** palavra-chave foi adicionado, que utiliza a nova linha como o delimitador.
Limitações atuais: não é possível definir um enumerador em termos de si próprio, mas pode inicializar uma enumeração em termos de outro enum, conforme mostrado no exemplo seguinte.
Além disso, atualmente não é possível especificar o tipo base; é sempre [int].

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Um valor de enumerador tem de ser uma constante de tempo de análise; Não é possível defini-lo para o resultado de um comando invocado.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

As enumerações suportam operações aritméticas, conforme mostrado no exemplo seguinte.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a>Importar DscResource

**Importar DscResource** agora é uma palavra-chave dinâmica verdadeira.
PowerShell analisa o módulo de raiz do módulo especificado, a procurar classes que contêm o **DscResource** atributo.

## <a name="implementingassembly"></a>ImplementingAssembly

Um novo campo **ImplementingAssembly**, foi adicionada ao ModuleInfo. Está definido para a assemblagem dinâmica criado para um módulo de script, se o script define as classes, ou a assemblagem carregada para módulos binários. Não é definido quando ModuleType = manifesto.

Reflexão no **ImplementingAssembly** campo Deteta recursos num módulo. Isto significa que pode descobrir recursos escritos no PowerShell ou outros idiomas geridos.

Campos com inicializadores:

```powershell
[int] $i = 5
```

Estática é suportada; funciona como um atributo, tal como as restrições de tipo, pelo que pode ser especificado por qualquer ordem.

```powershell
static [int] $count = 0
```

Um tipo é opcional.

```powershell
$s = "hello"
```

Todos os membros são públicos.

## <a name="constructors-and-instantiation"></a>Construtores e Instanciação

Classes do Windows PowerShell podem ter construtores; têm o mesmo nome que a respetiva classe. Construtores podem estar sobrecarregados. São suportados construtores estáticos. Propriedades com expressões de inicialização são inicializadas antes de executar qualquer código num construtor. As propriedades estáticas são inicializadas antes do corpo do construtor estático e as propriedades da instância estão inicializadas antes do corpo do construtor não estático. Atualmente, não há nenhuma sintaxe para chamar um construtor de outro construtor (como o C\# sintaxe ": this()"). A solução é para definir um método Init comum.

Seguem-se formas de classes instanciar nesta versão.

Instanciar utilizando o construtor predefinido. Tenha em atenção que o New-Object não é suportado nesta versão.

```powershell
$a = [MyClass]::new()
```

Chamar um construtor com um parâmetro

```powershell
$b = [MyClass]::new(42)
```

Transmitir uma matriz para um construtor com vários parâmetros
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

Nesta versão, New-Object não funciona com classes definidas no Windows PowerShell. Também nesta versão, o nome do tipo só é visível lexically, ou seja, não são visível fora do módulo ou script que define a classe. As funções podem devolver instâncias de uma classe definida no Windows PowerShell e instâncias de trabalho também fora do módulo ou script.

`Get-Member -Static` lista construtores, para que possa vê sobrecargas como qualquer outro método. O desempenho desta sintaxe também é significativamente mais rápido do que New-Object.

O método pseudo-estático denominado **novo** funciona com tipos de .NET, conforme mostrado no exemplo seguinte.

```powershell
[hashtable]::new()
```

Agora, pode ver as sobrecargas de construtor com membro Get, ou como o mostrado neste exemplo:

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a>Métodos

Um método de classe do Windows PowerShell é implementado como um ScriptBlock que tenha apenas um bloco de fim. Todos os métodos são públicos. O seguinte mostra um exemplo de definir um método denominado **DoSomething**.

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

Invocação de métodos:

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

Sobrecarregado métodos - ou seja, os que são com o mesmo método existente, mas diferenciadas pelos respetivos valores especificados – também são suportados.

## <a name="properties"></a>Propriedades

Todas as propriedades são públicas. Propriedades necessitam de uma nova linha ou um ponto e vírgula. Não se for especificado nenhum tipo de objeto, o tipo de propriedade é o objeto.

Propriedades que utilizam os atributos de validação ou atributos de transformação do argumento (por exemplo, `[ValidateSet("aaa")]`) funcionam como esperado.

## <a name="hidden"></a>Oculto

Uma nova palavra-chave, **Hidden**, foi adicionado. **Oculto** podem ser aplicadas às propriedades e métodos (incluindo construtores).

Os membros ocultos são públicos, mas não são apresentados no resultado de Get-membro, a menos que-Force é adicionado o parâmetro.

Oculta a membros não estão incluídos quando separador concluir ou utilizando o Intellisense, a menos que ocorre após a conclusão da classe que define o membro oculto.

Um novo atributo **System.Management.Automation.HiddenAttribute** foi adicionada para que o código c# pode ter a mesma semântica dentro do Windows PowerShell.

## <a name="return-types"></a>Tipos de retorno

Tipo de retorno é um contrato; o valor de retorno é convertido para o tipo esperado. Não se for especificado nenhum tipo de retorno, o tipo de retorno é nulo. Não há nenhum de transmissão em fluxo de objetos; Objetos não podem ser escritos para o pipeline intencionalmente ou acidentalmente.

## <a name="attributes"></a>Atributos

Dois novos atributos, **DscResource** e **DscProperty** foram adicionados.

## <a name="lexical-scoping-of-variables"></a>Controlo de âmbito lexical das variáveis

O seguinte mostra um exemplo de como lexical funciona âmbito nesta versão.

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

O exemplo seguinte cria várias classes novas e personalizadas para implementar um idioma de folha de estilo dinâmica HTML (DSL).
Em seguida, o exemplo adiciona funções de programa auxiliar para criar tipos de elemento específico como parte da classe de elemento, tais como os estilos do cabeçalho e tabelas, porque os tipos não podem ser utilizados fora do âmbito de um módulo.

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
