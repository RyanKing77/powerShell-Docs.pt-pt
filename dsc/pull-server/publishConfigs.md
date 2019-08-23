---
ms.date: 12/12/2018
keywords: DSC, PowerShell, configuração, instalação
title: Publicar em um servidor de pull usando IDs de configuração (v4/V5)
ms.openlocfilehash: c258814f480b91eba75c7ce9abf70c558f1f469e
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986567"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>Publicar em um servidor de pull usando IDs de configuração (v4/V5)

As seções a seguir pressupõem que você já configurou um servidor de pull. Se você ainda não configurou o servidor de pull, poderá usar os seguintes guias:

- [Configurar um servidor de pull de SMB de DSC](pullServerSmb.md)
- [Configurar um servidor de pull HTTP de DSC](pullServer.md)

Cada nó de destino pode ser configurado para baixar configurações, recursos e até mesmo relatar seu status. Este artigo mostra como carregar recursos para que eles fiquem disponíveis para download e configurar clientes para baixar automaticamente os recursos. Quando o nó recebe uma configuração atribuída, por **pull** ou **Push** (V5), ele baixa automaticamente todos os recursos exigidos pela configuração do local especificado no Configuration Manager local (LCM).

## <a name="compile-configurations"></a>Compilar configurações

A primeira etapa para armazenar [as configurações](../configurations/configurations.md) em um servidor de pull é compilá-las `.mof` em arquivos. Para tornar uma configuração genérica e aplicável a mais clientes, use `localhost` em seu bloco de nó. O exemplo a seguir mostra um shell de configuração `localhost` que usa em vez de um nome de cliente específico.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

Depois de Compilar sua configuração genérica, você deve ter um `localhost.mof` arquivo.

## <a name="renaming-the-mof-file"></a>Renomeando o arquivo MOF

Você pode armazenar arquivos `.mof` de configuração em um servidor de pull por **ConfigurationName** ou **ConfigurationId**. Dependendo de como você planeja configurar seus clientes de pull, você pode escolher uma seção abaixo para renomear corretamente os arquivos `.mof` compilados.

### <a name="configuration-ids-guid"></a>IDs de configuração (GUID)

Você precisará renomear `localhost.mof` o arquivo `<GUID>.mof` para o arquivo. Você pode criar um **GUID** aleatório usando o exemplo abaixo ou usando o cmdlet [New-GUID](/powershell/module/microsoft.powershell.utility/new-guid) .

```powershell
[System.Guid]::NewGuid()
```

Saída de exemplo

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

Em seguida, você pode `.mof` renomear o arquivo usando qualquer método aceitável. O exemplo a seguir usa o cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) .

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

Para obter mais informações sobre como usar GUIDs em seu ambiente, consulte [planejar GUIDs](/powershell/dsc/secureserver#guids).

### <a name="configuration-names"></a>Nomes de configuração

Você precisará renomear `localhost.mof` o arquivo `<Configuration Name>.mof` para o arquivo. No exemplo a seguir, o nome da configuração da seção anterior é usado. Em seguida, você pode `.mof` renomear o arquivo usando qualquer método aceitável. O exemplo a seguir usa o cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) .

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>Criar a soma de verificação

Cada `.mof` arquivo armazenado em um servidor de pull ou compartilhamento SMB precisa ter um arquivo associado `.checksum` .
Esse arquivo permite que os clientes saibam quando `.mof` o arquivo associado foi alterado e devem ser baixados novamente.

Você pode criar uma **soma de verificação** com o cmdlet [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) . Você também pode executar `New-DSCCheckSum` em um diretório de arquivos usando o `-Path` parâmetro.
Se já existir uma soma de verificação, você poderá forçá-la a ser recriada com o `-Force` parâmetro. O exemplo a seguir especificou um diretório `.mof` que contém o arquivo da seção anterior e usa `-Force` o parâmetro.

```powershell
New-DscChecksum -Path '.\' -Force
```

Nenhuma saída será mostrada, mas agora você verá um `<GUID or Configuration Name>.mof.checksum` arquivo.

## <a name="where-to-store-mof-files-and-checksums"></a>Onde armazenar os arquivos MOF e as somas de verificação

### <a name="on-a-dsc-http-pull-server"></a>Em um servidor de pull HTTP de DSC

Quando você configura seu servidor de pull HTTP, conforme explicado em [configurar um servidor de pull http de DSC](pullServer.md), você especifica diretórios para as chaves **ModulePath** e **ConfigurationPath** . A chave **ModulePath** indica onde os `.zip` arquivos empacotados de um módulo devem ser armazenados. O **ConfigurationPath** indica onde os `.mof` arquivos e `.checksum` arquivos devem ser armazenados.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a>Em um compartilhamento SMB

Ao configurar um cliente de pull para usar um compartilhamento SMB, você especifica um **ConfigurationRepositoryShare**.
Todos `.mof` os arquivos `.checksum` e arquivos devem ser armazenados no diretório **SourcePath** do bloco **ConfigurationRepositoryShare** .

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>Passos Seguintes

Em seguida, você desejará configurar clientes de pull para efetuar pull da configuração especificada. Para obter mais informações, consulte um dos seguintes guias:

- [Configurar um cliente de pull usando IDs de configuração (v4)](pullClientConfigId4.md)
- [Configurar um cliente de pull usando IDs de configuração (V5)](pullClientConfigId.md)
- [Configurar um cliente de pull usando nomes de configuração (V5)](pullClientConfigNames.md)

## <a name="see-also"></a>Consulte também

- [Configurar um servidor de pull de SMB de DSC](pullServerSmb.md)
- [Configurar um servidor de pull HTTP de DSC](pullServer.md)
- [Empacotar e carregar recursos para um servidor de pull](package-upload-resources.md)
