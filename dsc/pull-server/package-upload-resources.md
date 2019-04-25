---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Pacote e o carregamento de recursos para um servidor de solicitação
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079574"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>Pacote e o carregamento de recursos para um servidor de solicitação

As secções abaixo partem do princípio de que já configurou um servidor de solicitação. Se não tiver configurado o servidor de solicitação, pode utilizar os seguintes guias:

- [Configurar um servidor de solicitação de SMB de DSC](pullServerSmb.md)
- [Configurar um servidor de solicitação de HTTP de DSC](pullServer.md)

Cada nó de destino pode ser configurado para transferir configurações, recursos e até mesmo comunicou o seu estado. Este artigo irá mostrar como carregar recursos para que estejam disponíveis para transferir e configurar os clientes transfiram os recursos automaticamente. Quando o nó recebe uma configuração atribuídos, por meio **extrair** ou **Push** (v5), é transferida automaticamente quaisquer recursos de que a configuração a partir da localização especificada no LCM.

## <a name="package-resource-modules"></a>Módulos de recursos de pacote

Cada recurso disponível para um cliente transferir deve ser armazenado num arquivo de ". zip". O exemplo abaixo mostra os passos necessários para utilizar o [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) recursos.

> [!NOTE]
> Se tiver quaisquer clientes usando o PowerShell 4.0, será preciso flaten a estrutura de pastas de recursos e remover quaisquer pastas de versão. Para obter mais informações, consulte [várias versões de recursos](../configurations/import-dscresource.md#multiple-resource-versions).

É possível compactar o diretório de recursos em qualquer utilitário, um script ou um método que preferir. No Windows, pode *com o botão direito* no diretório de "xPSDesiredStateConfiguration" e selecione "Enviar para", em seguida, "Pasta comprimida".

![Clique com botão direito](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a>O arquivo de recursos de atribuição de nomes

O arquivo de recursos tem de ser chamado com o seguinte formato:

```
{ModuleName}_{Version}.zip
```

No exemplo acima, "xPSDesiredStateConfiguration.zip" deve ser o nome mudado "xPSDesiredStateConfiguration_8.4.4.0.zip".

### <a name="create-checksums"></a>Crie somas de verificação

Assim que o módulo de recursos foi compactado e mudar o nome, tem de criar uma **soma de verificação**.  O **soma de verificação** é utilizada, pelo LCM no cliente, para determinar se o recurso foi alterado e tem de ser transferida novamente. Pode criar uma **soma de verificação** com o [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, conforme mostrado no exemplo abaixo.

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

Não será apresentada nenhuma saída, mas agora, deverá ver um "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum". Também pode executar `New-DSCCheckSum` com um diretório de arquivos usando o `-Path` parâmetro. Se já existir uma soma de verificação, pode forçá-lo de ser recriadas com o `-Force` parâmetro.

### <a name="where-to-store-resource-archives"></a>Onde pretende armazenar os arquivos de recursos

#### <a name="on-a-dsc-http-pull-server"></a>Num servidor de solicitação de HTTP de DSC

Quando configurar seu servidor de solicitação de HTTP, conforme explicado na [configurar um servidor de solicitação de HTTP para DSC](pullServer.md), que especificar diretórios para o **ModulePath** e **ConfigurationPath** chaves. O **ConfigurationPath** key indica onde devem ser armazenados ficheiros ". MOF". O **ModulePath** indica onde quaisquer módulos de recursos de DSC devem ser armazenados.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a>Numa partilha SMB

Se tiver especificado um **ResourceRepositoryShare**, quando configurar o seu cliente de solicitação, armazenar arquivos e as somas de verificação no **SourcePath** diretório da **ResourceRepositoryShare** bloco.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

Se tiver especificado apenas uma **ConfigurationRepositoryShare**, quando configurar o seu cliente de solicitação, armazenar arquivos e as somas de verificação no **SourcePath** diretório da  **ConfigurationRepositoryShare** bloco.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>A atualizar os recursos

Pode forçar um nó para atualizar os seus recursos ao alterar o número de versão no nome do arquivo, ou ao criar uma nova soma de verificação. O cliente de solicitação irá verificar as versões mais recentes dos recursos necessários, bem como atualizadas as somas de verificação, quando atualiza o LCM.

## <a name="see-also"></a>Consulte também

- [Configurar um servidor de solicitação de SMB de DSC](pullServerSmb.md)
- [Configurar um servidor de solicitação de HTTP de DSC](pullServer.md)
