---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Utilizar a palavra-chave Import-DSCResource
ms.openlocfilehash: ee0b2f0469c6507c8f0148138198597a9e57cdd7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080106"
---
# <a name="using-import-dscresource"></a>Utilizar a palavra-chave Import-DSCResource

`Import-DScResource` é uma palavra-chave dynamic, o que só pode ser utilizada dentro de um bloco de script de configuração. O `Import-DSCResource` palavra-chave para importar todos os recursos necessários na sua configuração. Recursos sob `$pshome` são importados automaticamente, mas ainda é considerada uma prática recomendada para importar explicitamente todos os recursos utilizados na sua [configuração](Configurations.md).

A sintaxe para `Import-DSCResource` é mostrado abaixo.  Ao especificar módulos por nome, é um requisito para listar cada numa nova linha.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|Parâmetro  |Descrição  |
|---------|---------|
|`-Name`|Os nomes de recursos de DSC que tem de importar. Se não for especificado o nome do módulo, o comando procura estes recursos de DSC dentro deste módulo; caso contrário, o comando procura os recursos de DSC em todos os caminhos de recursos de DSC. São suportados carateres universais.|
|`-ModuleName`|O nome do módulo, ou a especificação de módulo.  Se especificar recursos para importar a partir de um módulo, irá tentar o comando importar apenas os recursos. Se especificar apenas o módulo, o comando importa todos os recursos de DSC no módulo.|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Exemplo: Utilizar Import-DSCResource dentro de uma configuração

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry
    
    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> Especificar vários valores para os nomes de recursos e nomes de módulos no mesmo comando não são suportadas. Ele pode ter um comportamento determinística sobre o recurso a carregar a partir do qual módulo no caso o mesmo recurso existe em vários módulos. Comando abaixo resultará no erro durante a compilação.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Aspetos a considerar ao utilizar apenas o parâmetro de nome:

- É uma operação com muitos recursos, dependendo do número de módulos instalados no computador.
- Ele carregará o primeiro recurso encontrado com o nome fornecido. No caso em que existe mais do que um recurso com o mesmo nome instalado, ele foi possível carregar o recurso de errado.

A utilização recomendada consiste em especificar `–ModuleName` com o `-Name` parâmetro, conforme descrito abaixo.

Esta utilização tem as seguintes vantagens:

- Reduz o impacto no desempenho ao limitar o âmbito de pesquisa para o recurso especificado.
- Ele define explicitamente o módulo de definição do recurso, garantir que o recurso correto é carregado.

> [!NOTE]
> No PowerShell 5.0, recursos de DSC podem ter várias versões e versões podem ser instaladas numa computador lado a lado. Isso é implementado fazendo com que várias versões de um módulo de recursos que estão contidas na mesma pasta do módulo.
> Para obter mais informações, consulte [utilizar recursos com várias versões](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>IntelliSense com Import-DSCResource

Ao criar a configuração de DSC no ISE, o PowerShell fornece IntelliSence para recursos e propriedades de recurso. Definições de recursos sob o `$pshome` caminho do módulo são carregados automaticamente. Ao importar recursos com o `Import-DSCResource` palavra-chave, as definições de recurso especificado são adicionadas e Intellisense é expandido para incluir o esquema do recurso importados.

![Recurso Intellisense](/media/resource-intellisense.png)

> [!NOTE]
> A partir do PowerShell 5.0, conclusão de tabulação foi adicionado ao ISE para recursos de DSC e as respetivas propriedades. Para obter mais informações, consulte [recursos](../resources/resources.md).

Ao compilar a configuração, o PowerShell utiliza definições de recursos importada para validar todos os blocos de recursos na configuração.
Cada bloco de recursos é validado, com a definição de esquema do recurso, para as seguintes regras.

- Apenas as propriedades definidas no esquema são utilizadas.
- Os tipos de dados para cada propriedade estão corretos.
- As propriedades de chaves são especificadas.
- Nenhuma propriedade só de leitura é utilizada.
- Validação no valor mapeia tipos.

Considere a seguinte configuração:

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

Compilar esta resultados de configuração num erro.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

Validação de esquema e IntelliSense permitem-lhe capturar mais erros durante o tempo de análise e compilação, evitando complicações em tempo de execução.

> [!NOTE]
> Cada recurso de DSC pode ter um nome e um **FriendlyName** definida pelo esquema do recurso. Seguem-se as duas primeiras linhas de "MSFT_ServiceResource.shema.mof".
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> Ao usar este recurso numa configuração, pode especificar **MSFT_ServiceResource** ou **serviço**.

## <a name="powershell-v4-and-v5-differences"></a>Diferenças de PowerShell v4 e v5

Existem várias diferenças que verá quando a criação de configurações no PowerShell 4.0 vs. PowerShell 5.0 e posterior. Esta secção irá realçar as diferenças que vê relevantes para este artigo.

### <a name="multiple-resource-versions"></a>Várias versões de recursos

Instalar e utilizar várias versões de recursos lado a lado não era suportada no PowerShell 4.0. Caso se depare com problemas importar recursos para a sua configuração, certifique-se de que tem apenas uma versão do recurso instalada.

Na imagem abaixo, duas versões dos **xPSDesiredStateConfiguration** módulo são instalados.

![Várias versões de recursos foi corrigidas](/media/multiple-resource-versions-broken.md)

Copie o conteúdo da sua versão do módulo pretendido para o nível superior do diretório de módulo.

![Várias versões de recursos foi corrigidas](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>Localização do recurso

Ao criar e compilar configurações, os seus recursos podem ser armazenados em qualquer diretório especificado pelo seu [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). No PowerShell 4.0, o LCM requer que todos os módulos de recursos de DSC sejam armazenados em "Programa Files\WindowsPowerShell\Modules" ou `$pshome\Modules`. A partir do PowerShell 5.0, este requisito foi removido e módulos de recursos podem ser armazenados em qualquer diretório especificado por `PSModulePath`.

## <a name="see-also"></a>Consulte também

- [Recursos](../resources/resources.md)
