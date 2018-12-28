---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Publicar um servidor de solicitação com IDs de configuração (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404833"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>Publicar um servidor de solicitação com IDs de configuração (v4/v5)

As secções abaixo partem do princípio de que já configurou um servidor de solicitação. Se não tiver configurado o servidor de solicitação, pode utilizar os seguintes guias:

- [Configurar um servidor de solicitação de SMB de DSC](pullServerSmb.md)
- [Configurar um servidor de solicitação de HTTP de DSC](pullServer.md)

Cada nó de destino pode ser configurado para transferir configurações, recursos e até mesmo comunicou o seu estado. Este artigo irá mostrar como carregar recursos para que estejam disponíveis para transferir e configurar os clientes transfiram os recursos automaticamente. Quando o nó recebe uma configuração atribuídos, por meio **extrair** ou **Push** (v5), é transferida automaticamente quaisquer recursos de que a configuração a partir da localização especificada no LCM.

## <a name="compile-configurations"></a>Compilar configurações

A primeira etapa para armazenar [configurações](../configurations/configurations.md) num servidor de solicitação é compilá-los na arquivos ". MOF". Para fazer uma configuração genérica e aplicáveis a mais clientes, use `localhost` em seu bloco de nó. O exemplo abaixo mostra um shell de configuração que utiliza `localhost` em vez de um nome de cliente específico.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

Após ter compilado seu configuração genérico, deve ter um ficheiro de "localhost.mof".

## <a name="renaming-the-mof-file"></a>Mudar o nome de ficheiro MOF

Pode armazenar ficheiros de ". MOF" de configuração num servidor de solicitação por **ConfigurationName** ou **ConfigurationID**. Dependendo de como pretende configurar os clientes de solicitação, pode escolher uma secção abaixo para corretamente mudar o nome de seus arquivos compilados ". MOF".

### <a name="configuration-ids-guid"></a>IDs de configuração (GUID)

Terá de mudar o nome do seu arquivo de "localhost.mof" para "<GUID>. MOF" ficheiro. Pode criar um aleatório **Guid** usando o exemplo abaixo, ou utilizando o [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.

```powershell
[System.Guid]::NewGuid()
```

Saída de Exemplo

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

Em seguida, pode mudar o nome do arquivo de ". MOF" usando qualquer método aceitável. O exemplo abaixo, utiliza a [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

Para obter mais informações sobre como utilizar **Guids** no seu ambiente, consulte [planear Guids](/powershell/dsc/secureserver#guids).

### <a name="configuration-names"></a>Nomes de configuração

Terá de mudar o nome do seu arquivo de "localhost.mof" para "<Configuration Name>. MOF" ficheiro. No exemplo a seguir, é utilizado o nome da configuração da secção anterior. Em seguida, pode mudar o nome do arquivo de ". MOF" usando qualquer método aceitável. O exemplo abaixo, utiliza a [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>Criar a soma de verificação

Cada arquivo de ". MOF" armazenados num servidor de solicitação ou partilha SMB tem de ter um ficheiro associado ".checksum". Este ficheiro permite que os clientes a saber quando o ficheiro associado ". MOF" foi alterado e deve ser transferido novamente.

Pode criar uma **soma de verificação** com o [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet. Também pode executar `New-DSCCheckSum` com um diretório de arquivos usando o `-Path` parâmetro. Se já existir uma soma de verificação, pode forçá-lo de ser recriadas com o `-Force` parâmetro. O exemplo seguinte especificado um diretório que contém o ficheiro ". MOF" da secção anterior e utiliza o `-Force` parâmetro.

```powershell
New-DscChecksum -Path '.\' -Force
```

Não será apresentada nenhuma saída, mas agora, deverá ver um "<GUID or Configuration Name>. mof.checksum" ficheiro.

## <a name="where-to-store-mof-files-and-checksums"></a>Onde pretende armazenar os arquivos MOF e somas de verificação

### <a name="on-a-dsc-http-pull-server"></a>Num servidor de solicitação de HTTP de DSC

Quando configurar seu servidor de solicitação de HTTP, conforme explicado na [configurar um servidor de solicitação de HTTP para DSC](pullServer.md), que especificar diretórios para o **ModulePath** e **ConfigurationPath** chaves. O **ConfigurationPath** key indica onde devem ser armazenados ficheiros ". MOF". O **ConfigurationPath** indica onde todos os arquivos ". MOF" e ".checksum" arquivos devem ser armazenados.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a>Numa partilha SMB

Quando configurar um cliente solicitar a utilizar uma partilha de SMB, especifique um **ConfigurationRepositoryShare**. Todos os arquivos de ". MOF" e ".checksum", em seguida, devem ser armazenados na **SourcePath** diretório da **ConfigurationRepositoryShare** bloco.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>Próximos Passos

Em seguida, desejará configurar clientes de Pull para extrair a configuração especificada. Para obter mais informações, consulte um dos seguintes guias:

- [Configurar um cliente de solicitação através de IDs de configuração (v4)](pullClientConfigId4.md)
- [Configurar um cliente de solicitação através de IDs de configuração (v5)](pullClientConfigId.md)
- [Configurar um cliente de solicitação através de nomes de configuração (v5)](pullClientConfigNames.md)

## <a name="see-also"></a>Consulte também

- [Configurar um servidor de solicitação de SMB de DSC](pullServerSmb.md)
- [Configurar um servidor de solicitação de HTTP de DSC](pullServer.md)
- [Pacote e o carregamento de recursos para um servidor de solicitação](package-upload-resources.md)
