---
ms.date: 12/12/2018
keywords: DSC, PowerShell, recurso, Galeria, instalação
title: Adicionar Parâmetros a uma Configuração
ms.openlocfilehash: 72e6c15593d11ed39d7fe8ea79f794089f410cf8
ms.sourcegitcommit: d1ba596f9e0d4df9565601a70687a126d535c917
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/05/2019
ms.locfileid: "70386320"
---
# <a name="add-parameters-to-a-configuration"></a>Adicionar Parâmetros a uma Configuração

Como as funções, [as configurações](configurations.md) podem ser parametrizadas para permitir mais configurações dinâmicas com base na entrada do usuário. As etapas são semelhantes às descritas em [funções com parâmetros](/powershell/module/microsoft.powershell.core/about/about_functions).

Este exemplo começa com uma configuração básica que configura o serviço de "spooler" como "em execução".

```powershell
Configuration TestConfig
{
    # It is best practice to explicitly import any required resources or modules.
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

## <a name="built-in-configuration-parameters"></a>Parâmetros de configuração internos

No entanto, ao contrário de uma função, o atributo [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) não adiciona nenhuma funcionalidade. Além dos [parâmetros comuns](/powershell/module/microsoft.powershell.core/about/about_commonparameters), as configurações também podem usar os seguintes parâmetros internos, sem exigir que você os defina.

|Parâmetro  |Descrição  |
|---------|---------|
|`-InstanceName`|Usado na definição de [configurações compostas](compositeconfigs.md)|
|`-DependsOn`|Usado na definição de [configurações compostas](compositeconfigs.md)|
|`-PSDSCRunAsCredential`|Usado na definição de [configurações compostas](compositeconfigs.md)|
|`-ConfigurationData`|Usado para passar dados de [configuração](configData.md) estruturados para uso na configuração.|
|`-OutputPath`|Usado para especificar onde o arquivo\<"\>ComputerName. mof" será compilado|

## <a name="adding-your-own-parameters-to-configurations"></a>Adicionando seus próprios parâmetros às configurações

Além dos parâmetros internos, você também pode adicionar seus próprios parâmetros às suas configurações. O bloco de parâmetro fica diretamente dentro da declaração de configuração, assim como uma função. Um bloco de parâmetro de configuração deve estar fora de qualquer declaração de **nó** e acima de qualquer instrução de *importação* . Ao adicionar parâmetros, você pode tornar suas configurações mais robustas e dinâmicas.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>Adicionar um parâmetro ComputerName

O primeiro parâmetro que você pode adicionar é `-Computername` um parâmetro para que você possa compilar dinamicamente um arquivo ". mof" `-Computername` para qualquer passagem para sua configuração. Como as funções, você também pode definir um valor padrão, caso o usuário não passe um valor para`-ComputerName`

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

Em sua configuração, você pode especificar o `-ComputerName` parâmetro ao definir o bloco de nó.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>Chamando sua configuração com parâmetros

Depois de adicionar parâmetros à sua configuração, você pode usá-los exatamente como faria com um cmdlet.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>Compilando vários arquivos. mof

O bloco de nó também pode aceitar uma lista separada por vírgulas de nomes de computador e gerará arquivos ". mof" para cada um. Você pode executar o exemplo a seguir para gerar arquivos ". mof" para todos os computadores passados para o `-ComputerName` parâmetro.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
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

Além de um `-ComputerName` parâmetro, podemos adicionar parâmetros para o nome do serviço e o estado. O exemplo a seguir adiciona um bloco de parâmetro `-ServiceName` com um parâmetro e o usa para definir dinamicamente o bloco de recursos de **serviço** . Ele também adiciona um `-State` parâmetro para definir dinamicamente o **estado** no bloco de recursos de **serviço** .

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

    # It is best practice to explicitly import any required resources or modules.
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
> Em cenários mais Advacned, pode fazer mais sentido mover seus dados dinâmicos para [dados de configuração](configData.md)estruturados.

A configuração de exemplo agora usa um `$ServiceName`dinâmico, mas se um não for especificado, a compilação resultará em um erro. Você pode adicionar um valor padrão como este exemplo.

```powershell
[String]
$ServiceName="Spooler"
```

No entanto, nesse caso, faz mais sentido simplesmente forçar o usuário a especificar um valor para o `$ServiceName` parâmetro. O `parameter` atributo permite que você adicione validação adicional e suporte a pipeline aos parâmetros da configuração.

Acima de qualquer declaração de parâmetro, `parameter` adicione o bloco de atributo como no exemplo a seguir.

```powershell
[parameter()]
[String]
$ServiceName
```

Você pode especificar argumentos para cada `parameter` atributo, para controlar aspectos do parâmetro definido. O exemplo a seguir cria `$ServiceName` um parâmetro **obrigatório** .

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

Para o `$State` parâmetro, gostaríamos de impedir que o usuário especifique valores fora de um conjunto predefinido (como em execução, parado) `ValidationSet*`o atributo impediria que o usuário especificasse valores fora de um conjunto predefinido (como em execução, Parado). O exemplo a seguir adiciona `ValidationSet` o atributo `$State` ao parâmetro. Como não queremos tornar o `$State` parâmetro **obrigatório**, precisaremos adicionar um valor padrão para ele.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> Você não precisa especificar um `parameter` atributo ao usar um `validation` atributo.

Você pode ler mais sobre os `parameter` atributos de validação e em [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).

## <a name="fully-parameterized-configuration"></a>Configuração totalmente parametrizada

Agora temos uma configuração com parâmetros que força o usuário a especificar um `-InstanceName`, `-ServiceName`e valida o `-State` parâmetro.

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

    # It is best practice to explicitly import any required resources or modules.
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

- [Escrever ajuda para configurações DSC](configHelp.md)
- [Configurações dinâmicas](flow-control-in-configurations.md)
- [Usar dados de configuração em suas configurações](configData.md)
- [Dados de configuração e de ambiente separados](separatingEnvData.md)
