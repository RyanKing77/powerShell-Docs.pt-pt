---
ms.date: 12/12/2018
keywords: DSC, do powershell, a configuração, a configuração
title: Utilizar a palavra-chave Import-DSCResource
ms.openlocfilehash: f22c741969b1429074e7307a00a5c014cf563089
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265506"
---
# <a name="using-import-dscresource"></a>Utilizar a palavra-chave Import-DSCResource

`Import-DScResource` é uma palavra-chave dinâmica, o que só pode ser utilizada dentro de um bloco de script de configuração. O `Import-DSCResource` palavra-chave para importar todos os recursos necessários na sua configuração. Recursos sob `$phsome` são importados automaticamente, mas ainda é considerada como melhor prática explicitamente importar todos os recursos utilizados no seu [configuração](Configurations.md).

A sintaxe para `Import-DSCResource` é mostrado abaixo.  Ao especificar módulos por nome, é um requisito para listar cada numa nova linha.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|Parâmetro  |Descrição  |
|---------|---------|
|`-Name`|Os nomes de recursos de DSC tem de importar. Se não for especificado o nome do módulo, o comando de procura para estes recursos de DSC dentro deste módulo; caso contrário, o comando procura os recursos de DSC em todos os caminhos de recursos de DSC. São suportados carateres universais.|
|`-ModuleName`|O nome do módulo, ou a especificação de módulo.  Se especificar recursos para importar a partir de um módulo, irá tentar o comando importar apenas os recursos. Se especificar apenas o módulo, o comando importa todos os recursos de DSC no módulo.|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Exemplo: Utilizar DSCResource importação dentro de uma configuração

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
> Especificar vários valores para os nomes de recursos e nomes de módulos no mesmo comando não são suportadas. Pode ter um comportamento não determinística sobre qual o recurso para carregar a partir da qual módulo no caso de mesmo recurso existe em vários módulos. Comando abaixo resultará num erro durante a compilação.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Aspetos a considerar ao utilizar apenas o parâmetro de nome:

- É uma operação intensiva de recursos, dependendo do número de módulos instalados no computador.
- Este será carregado no primeiro recurso encontrado com o nome fornecido. No caso onde existe mais do que um recurso com o mesmo nome instalado, foi possível carregar o recurso errado.

A utilização recomendada é especificar `–ModuleName` com o `-Name` parâmetro, conforme descrito abaixo.

Esta utilização tem as seguintes vantagens:

- Reduz o impacto do desempenho ao limitar o âmbito de pesquisa para o recurso especificado.
- Define explicitamente o módulo de definição de recurso, garantindo que o recurso correto está carregado.

> [!NOTE]
> No PowerShell 5.0, recursos de DSC podem ter várias versões e versões podem ser instaladas num computador do lado do lado a lado. Isto é implementado por ter várias versões de um módulo de recursos que estão contidas na mesma pasta do módulo.
> Para obter mais informações, consulte [através de recursos com várias versões](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>IntelliSense com DSCResource importação

Quando criar a configuração de DSC no ISE, o PowerShell fornece IntelliSence para recursos e propriedades de recurso. Definições de recursos sob o `$pshome` do módulo caminho são carregados automaticamente. Ao importar recursos utilizando o `Import-DSCResource` palavra-chave, definições de recursos especificados são adicionadas e Intellisense é expandido para incluir o esquema do recurso importado.

![Intellisense de recursos](/media/resource-intellisense.png)

> [!NOTE]
> Conclusão de separador a partir do PowerShell 5.0, foi adicionada ao ISE para recursos de DSC e as respetivas propriedades. Para obter mais informações, consulte [recursos](../resources/resources.md).

Ao compilar a configuração, o PowerShell utiliza as definições de recursos importada para validar todos os blocos de recurso na configuração.
Cada bloco de recurso é validado, utilizando a definição do recurso de esquema, para as seguintes regras.

- São utilizadas apenas propriedades definidas no esquema.
- Os tipos de dados para cada propriedade estão corretos.
- Propriedades de chaves são especificadas.
- Nenhuma propriedade só de leitura é utilizada.
- Tipos de mapas de validação no valor.

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

O IntelliSense e esquema de validação permitem-lhe detetar mais erros durante a análise e compilação tempo, evitando complicações em tempo de execução.

> [!NOTE]
> Cada recurso de DSC pode ter um nome e uma **FriendlyName** definido pelo esquema do recurso. Seguem-se as primeiras duas linhas de "MSFT_ServiceResource.shema.mof".
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> Quando utilizar este recurso numa configuração, pode especificar **MSFT_ServiceResource** ou **serviço**.

## <a name="powershell-v4-and-v5-differences"></a>Diferenças de v4 e v5 do PowerShell

Existem várias diferenças que vir durante a criação de configurações no vs PowerShell 4.0. PowerShell 5.0 e posterior. Esta secção irá realce as diferenças que vê relevantes para este artigo.

### <a name="multiple-resource-versions"></a>Várias versões do recurso

Instalar e utilizar várias versões dos recursos lado a lado não era suportada no PowerShell 4.0. Se reparar problemas importar recursos para a configuração, certifique-se de que tem apenas uma versão do recurso instalada.

Na imagem abaixo, duas versões do **xPSDesiredStateConfiguration** módulo estão instalados.

![Várias versões do recurso fixo](/media/multiple-resource-versions-broken.md)

Copie o conteúdo da sua versão do módulo pretendido para o nível superior do diretório de módulo.

![Várias versões do recurso fixo](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>Localização do recurso

Quando a criação e compilar configurações, os recursos podem ser armazenados em qualquer diretório especificado pelo seu [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). No PowerShell 4.0, o MMC requer que todos os módulos de recursos de DSC sejam armazenados em "Programa Files\WindowsPowerShell\Modules" ou `$pshome\Modules`. A partir do PowerShell 5.0, este requisito foi removido e módulos de recursos podem ser armazenados em qualquer diretório especificado pelo `PSModulePath`.

## <a name="see-also"></a>Consulte também

- [Recursos](../resources/resources.md)
