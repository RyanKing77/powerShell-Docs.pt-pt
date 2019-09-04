---
ms.date: 12/12/2018
keywords: DSC, PowerShell, configuração, instalação
title: Utilizar a palavra-chave Import-DSCResource
ms.openlocfilehash: e1c2c06d756a70c2de516f330e3123235ce740ba
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215402"
---
# <a name="using-import-dscresource"></a>Utilizar a palavra-chave Import-DSCResource

`Import-DScResource`é uma palavra-chave Dynamic, que só pode ser usada dentro de um bloco de script de configuração. A `Import-DSCResource` palavra-chave para importar todos os recursos necessários em sua configuração. Os recursos `$pshome` em são importados automaticamente, mas ainda é considerado uma prática recomendada importar explicitamente todos os recursos usados em sua [configuração](Configurations.md).

A sintaxe do `Import-DSCResource` é mostrada abaixo.  Ao especificar módulos por nome, é um requisito para listar cada um em uma nova linha.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|Parâmetro  |Descrição  |
|---------|---------|
|`-Name`|Os nomes de recursos de DSC que você deve importar. Se o nome do módulo for especificado, o comando pesquisará esses recursos de DSC dentro desse módulo; caso contrário, o comando pesquisará os recursos de DSC em todos os caminhos de recurso de DSC. Há suporte para curingas.|
|`-ModuleName`|O nome do módulo ou a especificação do módulo.  Se você especificar os recursos a serem importados de um módulo, o comando tentará importar somente esses recursos. Se você especificar apenas o módulo, o comando importará todos os recursos de DSC no módulo.|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Exemplo: Usar Import-DSCResource em uma configuração

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
> Não há suporte para a especificação de vários valores para nomes de recursos e nomes de módulos no mesmo comando. Ele pode ter um comportamento não determinístico sobre qual recurso carregar a partir de qual módulo no caso do mesmo recurso existe em vários módulos. O comando abaixo resultará em erro durante a compilação.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Coisas a considerar ao usar apenas o parâmetro Name:

- É uma operação com uso intensivo de recursos, dependendo do número de módulos instalados no computador.
- Ele carregará o primeiro recurso encontrado com o nome fornecido. No caso em que há mais de um recurso com o mesmo nome instalado, ele pode carregar o recurso errado.

O uso recomendado é especificar `–ModuleName` com o `-Name` parâmetro, conforme descrito abaixo.

Esse uso tem os seguintes benefícios:

- Ele reduz o impacto no desempenho limitando o escopo de pesquisa para o recurso especificado.
- Ele define explicitamente o módulo que define o recurso, garantindo que o recurso correto seja carregado.

> [!NOTE]
> No PowerShell 5,0, os recursos de DSC podem ter várias versões, e as versões podem ser instaladas em um computador lado a lado. Isso é implementado com a existência de várias versões de um módulo de recurso que estão contidas na mesma pasta de módulo.
> Para obter mais informações, consulte [usando recursos com várias versões](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>IntelliSense com Import-DSCResource

Ao criar a configuração de DSC no ISE, o PowerShell fornece IntelliSence para recursos e propriedades de recurso. As definições de recurso `$pshome` no caminho do módulo são carregadas automaticamente. Quando você importa recursos usando a `Import-DSCResource` palavra-chave, as definições de recurso especificadas são adicionadas e o IntelliSense é expandido para incluir o esquema do recurso importado.

![IntelliSense de recurso](../media/resource-intellisense.png)

> [!NOTE]
> A partir do PowerShell 5,0, o preenchimento com Tab foi adicionado ao ISE para recursos de DSC e suas propriedades. Para obter mais informações, consulte [recursos](../resources/resources.md).

Ao compilar a configuração, o PowerShell usa as definições de recursos importados para validar todos os blocos de recursos na configuração.
Cada bloco de recursos é validado, usando a definição de esquema do recurso, para as regras a seguir.

- Somente as propriedades definidas no esquema são usadas.
- Os tipos de dados para cada propriedade estão corretos.
- As propriedades das chaves são especificadas.
- Nenhuma propriedade somente leitura é usada.
- Validação em tipos de mapas de valor.

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

A compilação dessa configuração resulta em um erro.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

O IntelliSense e a validação de esquema permitem que você pegue mais erros durante a análise e o tempo de compilação, evitando complicações no tempo de execução.

> [!NOTE]
> Cada recurso de DSC pode ter um nome e um **FriendlyName** definido pelo esquema do recurso. Abaixo estão as duas primeiras linhas de "MSFT_ServiceResource. Shema. mof".
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> Ao usar esse recurso em uma configuração, você pode especificar **MSFT_ServiceResource** ou **Service**.

## <a name="powershell-v4-and-v5-differences"></a>Diferenças do PowerShell v4 e V5

Há várias diferenças que você vê ao criar configurações no PowerShell 4,0 versus PowerShell 5,0 e posterior. Esta seção irá destacar as diferenças que você vê relevantes para este artigo.

### <a name="multiple-resource-versions"></a>Várias versões de recurso

Não há suporte para a instalação e o uso de várias versões de recursos lado a lado no PowerShell 4,0. Se você notar problemas ao importar recursos para sua configuração, certifique-se de ter apenas uma versão do recurso instalada.

Na imagem abaixo, são instaladas duas versões do módulo **xPSDesiredStateConfiguration** .

![Várias versões de recurso corrigidas](../media/multiple-resource-versions-broken.png)

Copie o conteúdo da versão do módulo desejada para o nível superior do diretório do módulo.

![Várias versões de recurso corrigidas](../media/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a>Local do recurso

Ao criar e compilar configurações, seus recursos podem ser armazenados em qualquer diretório especificado por seu [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). No PowerShell 4,0, o LCM requer que todos os módulos de recursos de DSC sejam armazenados em "Program `$pshome\Modules`Files\WindowsPowerShell\Modules" ou. A partir do PowerShell 5,0, esse requisito foi removido e os módulos de recursos podem ser armazenados em qualquer diretório `PSModulePath`especificado por.

## <a name="see-also"></a>Consulte também

- [Recursos](../resources/resources.md)
