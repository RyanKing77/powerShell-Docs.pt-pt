---
ms.date: 04/11/2018
keywords: DSC, powershell, configuração, a configuração
title: Configurar um servidor de solicitação SMB de DSC
ms.openlocfilehash: 9d087a08861b2f4683e81efd1e25f857b8b75e07
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079290"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a>Configurar um servidor de solicitação SMB de DSC

Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> O servidor de solicitação (recurso do Windows *DSC-serviço*) é um componente suportado do Windows Server no entanto, não existem planos para oferecer novas funcionalidades ou capacidades. É recomendado para começar a fazer a transição geridos os clientes [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação de mensagens em fila no Windows Server) ou uma das soluções da Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).

Um DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) servidor de solicitação é um computador que aloja partilhas de ficheiros SMB que tornam os ficheiros de configuração de DSC e recursos de DSC disponíveis para nós de destino quando esses nós peça para os mesmos.

Para utilizar um servidor de solicitação SMB de DSC, terá de:

- Configurar a partilha de ficheiros SMB num servidor com o PowerShell 4.0 ou superior
- Configurar um cliente a executar o PowerShell 4.0 ou superior para solicitar a partir de que a partilha de SMB

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>Usando o recurso de xSmbShare para criar uma partilha de ficheiros SMB

Existem várias formas de configurar a partilha de ficheiros SMB, mas vamos dar uma olhada em como pode fazer isso usando a DSC.

### <a name="install-the-xsmbshare-resource"></a>Instalar o recurso de xSmbShare

Chamar o [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet para instalar o **xSmbShare** módulo.

> [!NOTE]
> `Install-Module` está incluído nos **PowerShellGet** módulo, que está incluído no PowerShell 5.0. Pode baixar o **PowerShellGet** módulo para o PowerShell 3.0 e 4.0 na [pré-visualização de módulos do PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).
> O **xSmbShare** contém o recurso de DSC **xSmbShare**, que podem ser utilizadas para criar uma partilha de ficheiros SMB.

### <a name="create-the-directory-and-file-share"></a>Criar a partilha de ficheiro e diretório

Utiliza a seguinte configuração o **arquivo** recurso para criar o diretório para a partilha e o **xSmbShare** recurso para configurar a partilha SMB:

```powershell
Configuration SmbShare
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

A configuração cria o diretório `C:\DscSmbShare`, se ainda não existir e, em seguida, utiliza esse diretório como uma partilha de ficheiros SMB. **FullAccess** deve receber a qualquer conta que tem de escrever ou eliminar da partilha de ficheiros. **ReadAccess** tem de obter para quaisquer nós de cliente que obtém configurações de e/ou de recursos de DSC da partilha.

> [!NOTE]
> DSC é executado como a conta de sistema por predefinição, para que o próprio computador tem de ter acesso à partilha.

### <a name="give-file-system-access-to-the-pull-client"></a>Conceder acesso de sistema de ficheiros para o cliente de solicitação

Dando **ReadAccess** para um cliente nó permite nesse nó para aceder à partilha SMB, mas não para ficheiros ou pastas dentro dessa partilha. Tem de conceder explicitamente cliente acesso de nós para a pasta de partilha SMB e subpastas. Podemos fazer isso com DSC, adicionando a utilizar o **cNtfsPermissionEntry** recurso, o que está contido no [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) módulo. A seguinte configuração adiciona um **cNtfsPermissionEntry** bloco que concede acesso de ReadAndExecute para o cliente de solicitação:

```powershell
Configuration DSCSMB
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare
    Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }

        cNtfsPermissionEntry PermissionSet1
        {
            Ensure = 'Present'
            Path = 'C:\DscSmbShare'
            Principal = 'myDomain\Contoso-Server$'
            AccessControlInformation = @(
                cNtfsAccessControlInformation
                {
                    AccessControlType = 'Allow'
                    FileSystemRights = 'ReadAndExecute'
                    Inheritance = 'ThisFolderSubfoldersAndFiles'
                    NoPropagateInherit = $false
                }
            )
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

## <a name="placing-configurations-and-resources"></a>Colocar recursos e configurações

Guarde todos os ficheiros de MOF de configuração e/ou recursos de DSC que pretende que nós de cliente para obter a pasta de partilha do SMB.

Qualquer ficheiro MOF de configuração deve ser nomeado *ConfigurationID*arquivos. MOF, onde *ConfigurationID* é o valor do **ConfigurationID** propriedade do LCM o nó de destino. Para obter mais informações sobre como configurar clientes de extração, consulte [como configurar um cliente de solicitação através do ID de configuração](pullClientConfigID.md).

> [!NOTE]
> Se estiver a utilizar um servidor de solicitação SMB tem de utilizar os IDs de configuração. Nomes de configuração não são suportados para SMB.

Cada módulo de recursos tem de ser comprimido e nomeado de acordo com o seguinte padrão `{Module Name}_{Module Version}.zip`. Por exemplo, um módulo com o nome xWebAdminstration com uma versão do módulo do 3.1.2.0 teria o nome 'xWebAdministration_3.2.1.0.zip'. Cada versão de um módulo tem de estar contido num arquivo zip único. Não são suportadas versões separadas de um módulo num arquivo zip. Antes de empacotar os módulos de recursos de DSC para utilização com o servidor de solicitação, precisa fazer uma pequena alteração para a estrutura de diretórios.

O formato de padrão de módulos que contém o recurso de DSC no WMF 5.0 é `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.

Antes de empacotamento tendo em vista o servidor de solicitação simplesmente remover o `{Module version}` pasta para que o caminho se torna `{Module Folder}\DscResources\{DSC Resource Folder}\`. Com esta alteração, zip na pasta, conforme descrito acima e colocar esses arquivos zip na pasta de partilha SMB.

## <a name="creating-the-mof-checksum"></a>Criar a soma de verificação do MOF

Um ficheiro MOF de configuração tem de ser emparelhado com um ficheiro de soma de verificação para que um LCM num nó de destino pode validar a configuração.
Para criar uma soma de verificação, chamar o [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet. O cmdlet assume um `Path` parâmetro que especifica a pasta onde está localizada a MOF de configuração. O cmdlet cria um ficheiro de soma de verificação com o nome `ConfigurationMOFName.mof.checksum`, onde `ConfigurationMOFName` é o nome do ficheiro de mof de configuração.
Se existirem mais de uma configuração de MOF ficheiros na pasta especificada, é criada uma soma de verificação para cada configuração na pasta.

O ficheiro de soma de verificação deve estar presente no mesmo diretório que o ficheiro MOF de configuração (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` por predefinição), e ter o mesmo nome com o `.checksum` extensão acrescentada.

> [!NOTE]
> Se alterar o ficheiro MOF de configuração de qualquer forma, também tem de recriar o arquivo de soma de verificação.

## <a name="setting-up-a-pull-client-for-smb"></a>Como configurar um cliente de solicitação para SMB

Para configurar um cliente que solicita as configurações de e/ou os recursos a partir de uma partilha de SMB, configurou com, a Local Configuration Manager (LCM do cliente) **ConfigurationRepositoryShare** e **ResourceRepositoryShare** blocos que especifique a partilha do que solicitar configurações e recursos de DSC.

Para obter mais informações sobre como configurar o LCM, consulte [como configurar um cliente de solicitação através do ID de configuração](pullClientConfigID.md).

> [!NOTE]
> Para simplificar, este exemplo utiliza a **PSDscAllowPlainTextPassword** para permitir a passagem de uma palavra-passe de texto sem formatação para o **credencial** parâmetro. Para obter informações sobre passar credenciais de forma mais segura, consulte [opções de credenciais nos dados de configuração](../configurations/configDataCredentials.md).
>
> **Tem** especificar um **ConfigurationID** no **definições** bloco de um metaconfiguration para um servidor de solicitação SMB, mesmo se está extraindo apenas recursos.

```powershell
$secpasswd = ConvertTo-SecureString “Pass1Word” -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential (“TestUser”, $secpasswd)

[DSCLocalConfigurationManager()]
configuration SmbCredTest
{
    Node $AllNodes.NodeName
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
            ConfigurationID    = '16db7357-9083-4806-a80c-ebbaf4acd6c1'
        }

         ConfigurationRepositoryShare SmbConfigShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds
        }

        ResourceRepositoryShare SmbResourceShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds

        }
    }
}

$ConfigurationData = @{
    AllNodes = @(
        @{
            #the "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="localhost"
            PSDscAllowPlainTextPassword = $true
        })
}
```

## <a name="acknowledgements"></a>Confirmações

Agradecimentos especiais a seguintes pessoas:

- Mike F. Robbins, cujas postagens sobre como utilizar o SMB de DSC ajudaram a informar o conteúdo deste tópico. Seu blog está em [Mike F Robbins](http://mikefrobbins.com/).
- Serge Nikalaichyk, que são criados os **cNtfsAccessControl** módulo. A origem para este módulo é parte [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).

## <a name="see-also"></a>Consulte também

[Windows PowerShell Desired State Configuration descrição-geral](../overview/overview.md)

[Aplicar configurações](enactingConfigurations.md)

[Configurar um cliente de solicitação através de IDs de configuração](pullClientConfigID.md)
