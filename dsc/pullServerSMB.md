---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Configurar um servidor de solicitação do DSC SMB"
ms.openlocfilehash: 5efd8a822e4420484391f7a5a9832d5d51883e8d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="setting-up-a-dsc-smb-pull-server"></a>Configurar um servidor de solicitação do DSC SMB

>Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

Um DSC [SMB](https://technet.microsoft.com/en-us/library/hh831795.aspx) do servidor de solicitação é um computador que aloja partilhas de ficheiros SMB que fazer com que os ficheiros de configuração de DSC e recursos de DSC disponíveis para nós de destino quando os nós peça-lhes.

Para utilizar um servidor de solicitação do SMB para DSC, tem de:
- Configurar uma partilha de ficheiros SMB num servidor com o PowerShell 4.0 ou superior
- Configurar um cliente com o PowerShell 4.0 ou superior para solicitar a partir de que a partilha de SMB

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>Para criar uma partilha de ficheiros SMB utilizando o recurso de xSmbShare

Existem várias formas de configurar uma partilha de ficheiros SMB, mas vamos ver como pode fazer isto utilizando DSC.

### <a name="install-the-xsmbshare-resource"></a>Instalar o recurso de xSmbShare

Chamar o [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet para instalar o **xSmbShare** módulo.
>**Tenha em atenção**: **Install-Module** está incluído no **PowerShellGet** módulo, que está incluído no PowerShell 5.0. Pode transferir o **PowerShellGet** módulo para o PowerShell 3.0 e 4.0 em [pré-visualização de módulos do PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186). O **xSmbShare** contém os recursos de DSC **xSmbShare**, que pode ser utilizado para criar uma partilha de ficheiros SMB.

### <a name="create-the-directory-and-file-share"></a>Criar a partilha de ficheiros e diretórios

Utiliza a seguinte configuração de [ficheiro](fileResource.md) recurso para criar o diretório para a partilha e o **xSmbShare** recursos para configurar a partilha SMB:

```powershell
Configuration SmbShare {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare
 
    Node localhost {
 
        File CreateFolder {
 
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
 
        }
 
        xSMBShare CreateShare {
 
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'admininstrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
 
        }
        
    }
 
}
```

A configuração cria o diretório `C:\DscSmbShare` se este já não existe e, em seguida, utiliza esse directório como uma partilha de ficheiros SMB. **FullAccess** deve ser-lhe concedido a qualquer conta que tem de escrever ou eliminar da partilha de ficheiros, e **ReadAccess** deve ser dada para quaisquer nós de cliente que aproveitar a partilha (Isto acontece porque as configurações e/ou recursos de DSC DSC é executado como conta do sistema por predefinição, pelo que o próprio computador tem de ter acesso à partilha).


### <a name="give-file-system-access-to-the-pull-client"></a>Dê ao sistema de ficheiros para o cliente de solicitação

Dar **ReadAccess** para um cliente nó permite esse nó aceder à partilha de SMB, mas não para ficheiros ou pastas dentro que partilha. Tem de conceder explicitamente cliente acesso de nós para a pasta de partilha SMB e as subpastas. Podemos fazer isto com DSC adicionando utilizando o **cNtfsPermissionEntry** recurso, o que faz a [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) módulo. A seguinte configuração adiciona um **cNtfsPermissionEntry** bloco que concede acesso de ReadAndExecute para o cliente de extração:

```powershell
Configuration DSCSMB {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare
Import-DscResource -ModuleName cNtfsAccessControl
 
    Node localhost {
 
        File CreateFolder {
 
            DestinationPath = 'DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
 
        }
 
        xSMBShare CreateShare {
 
            Name = 'DscSmbShare'
            Path = 'DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
 
        }

        cNtfsPermissionEntry PermissionSet1 {
            
        Ensure = 'Present'
        Path = 'C:\DSCSMB'
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

Guarde quaisquer ficheiros MOF de configuração e/ou recursos de DSC que pretende que nós de cliente para obter a pasta de partilha SMB.

Qualquer ficheiro de configuração de MOF deve ter o nome _ConfigurationID_. MOF, onde _ConfigurationID_ valor o **ConfigurationID** propriedade do MMC do nó de destino. Para obter mais informações sobre como configurar clientes de solicitação, consulte [configurar um cliente de extração com o ID de configuração](pullClientConfigID.md).

>**Nota:** tem de utilizar os IDs de configuração se estiver a utilizar um servidor de solicitação do SMB. Nomes de configuração não são suportados para SMB.

Cada módulo de recursos tem de ser zipado e com o nome de acordo com o padrão de seguinte `{Module Name}_{Module Version}.zip`. Por exemplo, um módulo com o nome xWebAdminstration com uma versão do módulo de 3.1.2.0 seria possível com o nome 'xWebAdministration_3.2.1.0.zip'. Cada versão do módulo tem de estar contido num ficheiro zip único. Uma vez que existe apenas uma única versão de um recurso em cada ficheiro zip o formato de módulo adicionado no WMF 5.0 com suporte para várias versões de módulo num único diretório não é suportado. Isto significa que antes do empacotamento dos módulos de recursos de DSC para utilização com o servidor de solicitação tem de efetuar uma alteração de pequena para a estrutura de diretórios. O formato predefinido de módulos que contém os recursos de DSC na WMF 5.0 é ' {pasta do módulo}\{versão do módulo} \DscResources\{pasta de recursos de DSC}\'. Antes de empacotamento para o servidor de solicitação basta remover a **{versão do módulo}** pasta para o caminho fica ' {pasta do módulo} \DscResources\{pasta de recursos de DSC}\'. Com esta alteração, zip a pasta, conforme descrito acima e colocar esses ficheiros zip na pasta de partilha SMB. 

## <a name="creating-the-mof-checksum"></a>Criar a soma de verificação MOF
Um ficheiro MOF de configuração tem de estar associados a um ficheiro de soma de verificação para que o MMC num nó de destino pode validar a configuração. Para criar uma soma de verificação, chame o [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet. O cmdlet assume um **caminho** parâmetro que especifica a pasta onde está localizada a configuração MOF. O cmdlet cria um ficheiro de soma de verificação chamado `ConfigurationMOFName.mof.checksum`, onde `ConfigurationMOFName` é o nome do ficheiro mof configuração. Se existirem mais de uma configuração MOF ficheiros na pasta especificada, é criada uma soma de verificação para cada configuração na pasta.

O ficheiro de soma de verificação deve estar presente no mesmo diretório do ficheiro MOF configuration (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` por predefinição), e ter o mesmo nome com o `.checksum` extensão anexado.

>**Tenha em atenção**: Se alterar o ficheiro MOF de configuração de qualquer forma, também tem de recriar o ficheiro de soma de verificação.

## <a name="setting-up-a-pull-client-for-smb"></a>Configurar um cliente de solicitação para SMB

Para configurar um cliente solicita configurações de e/ou recursos a partir de uma partilha de SMB, configurar Local Configuration Manager (o MMC o cliente) com **ConfigurationRepositoryShare** e **ResourceRepositoryShare** blocos que especifique a partilha a partir do qual solicitar configurações e os recursos de DSC.

Para obter mais informações sobre como configurar o MMC, consulte [configurar um cliente de extração com o ID de configuração](pullClientConfigID.md).

>**Nota:** de simplicidade, este exemplo utiliza o **PSDscAllowPlainTextPassword** para permitir a passagem de uma palavra-passe de texto simples para o **credencial** parâmetro. Para obter informações sobre a forma mais segura a transmitir as credenciais, consulte [opções de credenciais nos dados de configuração](configDataCredentials.md).

>**Nota:** tem de especificar um **ConfigurationID** no **definições** bloco de uma configuração meta para um servidor de solicitação do SMB, mesmo que apenas são extrair recursos.

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

Especial obrigado às seguintes:

- Mike F. Robbins, cuja cronologia utilizando SMB para DSC ajudou a informar o conteúdo deste tópico. O blogue é [Mike F Robbins](http://mikefrobbins.com/).
- Serge Nikalaichyk, que tiver criado o **cNtfsAccessControl** módulo. A origem para este módulo é em https://github.com/SNikalaichyk/cNtfsAccessControl.

## <a name="see-also"></a>Consulte também
- [Descrição geral da configuração do estado pretendido do Windows PowerShell](overview.md)
- [Enacting configurações](enactingConfigurations.md)
- [Configurar um cliente de extração com o ID de configuração](pullClientConfigID.md)

 
