---
ms.date: 12/12/2018
keywords: DSC, powershell, recurso, galeria, a configuração
title: Adicionar Parâmetros a uma Configuração
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685404"
---
# <a name="add-parameters-to-a-configuration"></a>Adicionar Parâmetros a uma Configuração

Como as funções, [configurações](configurations.md) pode ser parametrizada para permitir que as configurações mais dinâmicas com base na entrada do usuário. Os passos são semelhantes às descritas [as funções com parâmetros](/powershell/module/microsoft.powershell.core/about/about_functions).

Este exemplo começa com uma configuração básica que configura o serviço de "Spooler" de "Executar".

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a>Parâmetros de configuração incorporados

Ao contrário de uma função no entanto, o [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) atributo não adiciona nenhuma funcionalidade. Para além [parâmetros comuns de](/powershell/module/microsoft.powershell.core/about/about_commonparameters), configurações também podem utilizar o seguinte criado nos parâmetros, sem exigir a defini-las.

|Parâmetro  |Descrição  |
|---------|---------|
|`-InstanceName`|Utilizadas na definição de [configurações compostos](compositeconfigs.md)|
|`-DependsOn`|Utilizadas na definição de [configurações compostos](compositeconfigs.md)|
|`-PSDSCRunAsCredential`|Utilizadas na definição de [configurações compostos](compositeconfigs.md)|
|`-ConfigurationData`|Usado para transmitir em estruturado [dados de configuração](configData.md) para utilização na configuração.|
|`-OutputPath`|Utilizado para especificar onde sua "\<computername\>. MOF" ficheiro será compilado|

## <a name="adding-your-own-parameters-to-configurations"></a>Adicionar os seus parâmetros para configurações

Além dos parâmetros internos, também pode adicionar seus próprios parâmetros para suas configurações. O bloco de parâmetro vai diretamente dentro da declaração de configuração, assim como uma função. Um bloco de parâmetro de configuração deve estar fora de qualquer **nó** declarações e acima qualquer *importar* instruções. Ao adicionar parâmetros, pode fazer suas configurações mais robusto e dinâmico.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>Adicione um parâmetro ComputerName

O primeiro parâmetro, pode adicionar é uma `-Computername` parâmetro para que pode compilar dinamicamente um arquivo de ". MOF" para qualquer `-Computername` passar para a configuração. Como funções, também pode definir um valor predefinido, no caso do utilizador não introduzir um valor para `-ComputerName`

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

Na sua configuração, em seguida, pode especificar seu `-ComputerName` parâmetro ao definir seu bloco de nó.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>Chamar a configuração com parâmetros

Depois de adicionar parâmetros à sua configuração, pode usá-los tal como faria com um cmdlet.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>Compilação de vários arquivos. MOF

O bloco de nó também pode aceitar uma lista separada por vírgulas de nomes de computador e irá gerar arquivos ". MOF" para cada um. Pode executar o exemplo a seguir para gerar arquivos de ". MOF" para todos os computadores passados para o `-ComputerName` parâmetro.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a>Parâmetros avançados em configurações

Para além um `-ComputerName` parâmetro, podemos adicionar parâmetros para o nome do serviço e o estado. O exemplo seguinte adiciona um bloco de parâmetro com um `-ServiceName` parâmetro e utiliza-a para definir dinamicamente o **serviço** bloco de recursos. Também adiciona uma `-State` parâmetro para definir dinamicamente o **estado** no **serviço** bloco de recursos.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> Em mais cenários de advacned, pode fazer mais sentido para mover os dados dinâmicos para uma estruturados [dados de configuração](configData.md).

O exemplo de configuração agora demora dinâmico `$ServiceName`, mas se não for especificado, os resultados num erro de compilação. Poderia adicionar um valor predefinido, como neste exemplo.

```powershell
[String]
$ServiceName="Spooler"
```

Neste caso, faz mais sentido simplesmente forçar o utilizador especifique um valor para o `$ServiceName` parâmetro. O `parameter` atributo permite-lhe adicionar suporte a mais de validação e pipeline para parâmetros de sua configuração.

Acima de qualquer declaração de parâmetro, adicione o `parameter` bloco de atributo como no exemplo abaixo.

```powershell
[parameter()]
[String]
$ServiceName
```

Pode especificar argumentos para cada `parameter` atributo, a controlem aspectos do parâmetro definido. O exemplo a seguir faz com que o `$ServiceName` um **obrigatório** parâmetro.

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

Para o `$State` parâmetro, também gostaria de evitar que o utilizador especificar valores fora de um conjunto predefinido (como em execução, parado) a `ValidationSet*`atributo seria impedir que o utilizador especificar valores fora de um conjunto predefinido (como em execução, Parado). O exemplo seguinte adiciona o `ValidationSet` atributo para o `$State` parâmetro. Uma vez que não queremos tornar a `$State` parâmetro **obrigatório**, precisamos de adicionar um valor predefinido para o mesmo.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> Não é necessário especificar um `parameter` atributo ao utilizar um `validation` atributo.

Pode ler mais sobre o `parameter` e atributos de validação na [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).

## <a name="fully-parameterized-configuration"></a>Configuração totalmente parametrizada

Agora, temos uma configuração parametrizada que força o utilizador especifique um `-InstanceName`, `-ServiceName`e valida o `-State` parâmetro.

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a>Consulte também

- [Escrever ajuda para configurações de DSC](configHelp.md)
- [Configurações dinâmicas](flow-control-in-configurations.md)
- [Utilizar dados de configuração nas suas configurações](configData.md)
- [Dados de configuração e ambiente separado](separatingEnvData.md)
