---
ms.date: 04/11/2018
keywords: DSC, do powershell, a configuração, a configuração
title: Configurar um servidor de solicitação SMB de DSC
ms.openlocfilehash: 92c03c99afd612fa2b5475e8c26991ff080584e9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189674"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="9f0bb-103">Configurar um servidor de solicitação SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="9f0bb-103">Setting up a DSC SMB pull server</span></span>

><span data-ttu-id="9f0bb-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9f0bb-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9f0bb-105">O servidor de solicitação (funcionalidade do Windows *DSC serviço*) é um componente suportado do Windows Server no entanto, são não planos para oferecer novas funcionalidades ou capacidades.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="9f0bb-106">É recomendado para começar a transição geridos os clientes [Automation DSC do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação no Windows Server) ou uma das soluções de Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="9f0bb-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="9f0bb-107">Um DSC [SMB](https://technet.microsoft.com/library/hh831795.aspx) do servidor de solicitação é um computador que aloja partilhas de ficheiros SMB que fazer com que os ficheiros de configuração de DSC e recursos de DSC disponíveis para nós de destino quando os nós peça-lhes.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-107">A DSC [SMB](https://technet.microsoft.com/library/hh831795.aspx) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="9f0bb-108">Para utilizar um servidor de solicitação do SMB para DSC, tem de:</span><span class="sxs-lookup"><span data-stu-id="9f0bb-108">To use an SMB pull server for DSC, you have to:</span></span>
- <span data-ttu-id="9f0bb-109">Configurar uma partilha de ficheiros SMB num servidor com o PowerShell 4.0 ou superior</span><span class="sxs-lookup"><span data-stu-id="9f0bb-109">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="9f0bb-110">Configurar um cliente com o PowerShell 4.0 ou superior para solicitar a partir de que a partilha de SMB</span><span class="sxs-lookup"><span data-stu-id="9f0bb-110">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="9f0bb-111">Para criar uma partilha de ficheiros SMB utilizando o recurso de xSmbShare</span><span class="sxs-lookup"><span data-stu-id="9f0bb-111">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="9f0bb-112">Existem várias formas de configurar uma partilha de ficheiros SMB, mas vamos ver como pode fazer isto utilizando DSC.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-112">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="9f0bb-113">Instalar o recurso de xSmbShare</span><span class="sxs-lookup"><span data-stu-id="9f0bb-113">Install the xSmbShare resource</span></span>

<span data-ttu-id="9f0bb-114">Chamar o [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet para instalar o **xSmbShare** módulo.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-114">Call the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to install the **xSmbShare** module.</span></span>
><span data-ttu-id="9f0bb-115">**Tenha em atenção**: **Install-Module** está incluído no **PowerShellGet** módulo, que está incluído no PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-115">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="9f0bb-116">Pode transferir o **PowerShellGet** módulo para o PowerShell 3.0 e 4.0 em [pré-visualização de módulos do PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="9f0bb-116">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> <span data-ttu-id="9f0bb-117">O **xSmbShare** contém os recursos de DSC **xSmbShare**, que pode ser utilizado para criar uma partilha de ficheiros SMB.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-117">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="9f0bb-118">Criar a partilha de ficheiros e diretórios</span><span class="sxs-lookup"><span data-stu-id="9f0bb-118">Create the directory and file share</span></span>

<span data-ttu-id="9f0bb-119">Utiliza a seguinte configuração de [ficheiro](fileResource.md) recurso para criar o diretório para a partilha e o **xSmbShare** recursos para configurar a partilha SMB:</span><span class="sxs-lookup"><span data-stu-id="9f0bb-119">The following configuration uses the [File](fileResource.md) resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

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

<span data-ttu-id="9f0bb-120">A configuração cria o diretório `C:\DscSmbShare` se este já não existe e, em seguida, utiliza esse directório como uma partilha de ficheiros SMB.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-120">The configuration creates the directory `C:\DscSmbShare` if it doesn't already exists, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="9f0bb-121">**FullAccess** deve ser-lhe concedido a qualquer conta que tem de escrever ou eliminar da partilha de ficheiros, e **ReadAccess** deve ser dada para quaisquer nós de cliente que aproveitar a partilha (Isto acontece porque as configurações e/ou recursos de DSC DSC é executado como conta do sistema por predefinição, pelo que o próprio computador tem de ter acesso à partilha).</span><span class="sxs-lookup"><span data-stu-id="9f0bb-121">**FullAccess** should be given to any account that needs to write to or delete from the file share, and **ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share ( this is because DSC runs as the system account by default, so the computer itself has to have access to the share).</span></span>


### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="9f0bb-122">Dê ao sistema de ficheiros para o cliente de solicitação</span><span class="sxs-lookup"><span data-stu-id="9f0bb-122">Give file system access to the pull client</span></span>

<span data-ttu-id="9f0bb-123">Dar **ReadAccess** para um cliente nó permite esse nó aceder à partilha de SMB, mas não para ficheiros ou pastas dentro que partilha.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-123">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="9f0bb-124">Tem de conceder explicitamente cliente acesso de nós para a pasta de partilha SMB e as subpastas.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-124">You have to explicitly grant client nodes access to the SMB share folder and sub-folders.</span></span> <span data-ttu-id="9f0bb-125">Podemos fazer isto com DSC adicionando utilizando o **cNtfsPermissionEntry** recurso, o que faz a [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) módulo.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-125">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="9f0bb-126">A seguinte configuração adiciona um **cNtfsPermissionEntry** bloco que concede acesso de ReadAndExecute para o cliente de extração:</span><span class="sxs-lookup"><span data-stu-id="9f0bb-126">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

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

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="9f0bb-127">Colocar recursos e configurações</span><span class="sxs-lookup"><span data-stu-id="9f0bb-127">Placing configurations and resources</span></span>

<span data-ttu-id="9f0bb-128">Guarde quaisquer ficheiros MOF de configuração e/ou recursos de DSC que pretende que nós de cliente para obter a pasta de partilha SMB.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-128">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="9f0bb-129">Qualquer ficheiro de configuração de MOF deve ter o nome _ConfigurationID_. MOF, onde _ConfigurationID_ valor o **ConfigurationID** propriedade do MMC do nó de destino.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-129">Any configuration MOF file must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="9f0bb-130">Para obter mais informações sobre como configurar clientes de solicitação, consulte [configurar um cliente de extração com o ID de configuração](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="9f0bb-130">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

><span data-ttu-id="9f0bb-131">**Nota:** tem de utilizar os IDs de configuração se estiver a utilizar um servidor de solicitação do SMB.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-131">**Note:** You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="9f0bb-132">Nomes de configuração não são suportados para SMB.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-132">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="9f0bb-133">Cada módulo de recursos tem de ser zipado e com o nome de acordo com o padrão de seguinte `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-133">Each resource module needs to be zipped and named according the the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="9f0bb-134">Por exemplo, um módulo com o nome xWebAdminstration com uma versão do módulo de 3.1.2.0 seria possível com o nome 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-134">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="9f0bb-135">Cada versão do módulo tem de estar contido num ficheiro zip único.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-135">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="9f0bb-136">Uma vez que existe apenas uma única versão de um recurso em cada ficheiro zip o formato de módulo adicionado no WMF 5.0 com suporte para várias versões de módulo num único diretório não é suportado.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-136">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="9f0bb-137">Isto significa que antes do empacotamento dos módulos de recursos de DSC para utilização com o servidor de solicitação tem de efetuar uma alteração de pequena para a estrutura de diretórios.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-137">This means that before packaging up DSC resource modules for use with pull server you need to make a small change to the directory structure.</span></span> <span data-ttu-id="9f0bb-138">O formato predefinido de módulos que contém os recursos de DSC na WMF 5.0 é ' {pasta do módulo}\{versão do módulo} \DscResources\{pasta de recursos de DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-138">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="9f0bb-139">Antes de empacotamento para o servidor de solicitação basta remover a **{versão do módulo}** pasta para o caminho fica ' {pasta do módulo} \DscResources\{pasta de recursos de DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-139">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="9f0bb-140">Com esta alteração, zip a pasta, conforme descrito acima e colocar esses ficheiros zip na pasta de partilha SMB.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-140">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="9f0bb-141">Criar a soma de verificação MOF</span><span class="sxs-lookup"><span data-stu-id="9f0bb-141">Creating the MOF checksum</span></span>
<span data-ttu-id="9f0bb-142">Um ficheiro MOF de configuração tem de estar associados a um ficheiro de soma de verificação para que o MMC num nó de destino pode validar a configuração.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-142">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="9f0bb-143">Para criar uma soma de verificação, chame o [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-143">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span> <span data-ttu-id="9f0bb-144">O cmdlet assume um **caminho** parâmetro que especifica a pasta onde está localizada a configuração MOF.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-144">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="9f0bb-145">O cmdlet cria um ficheiro de soma de verificação chamado `ConfigurationMOFName.mof.checksum`, onde `ConfigurationMOFName` é o nome do ficheiro mof configuração.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-145">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="9f0bb-146">Se existirem mais de uma configuração MOF ficheiros na pasta especificada, é criada uma soma de verificação para cada configuração na pasta.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-146">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="9f0bb-147">O ficheiro de soma de verificação deve estar presente no mesmo diretório do ficheiro MOF configuration (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` por predefinição), e ter o mesmo nome com o `.checksum` extensão anexado.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-147">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

><span data-ttu-id="9f0bb-148">**Tenha em atenção**: Se alterar o ficheiro MOF de configuração de qualquer forma, também tem de recriar o ficheiro de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-148">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="9f0bb-149">Configurar um cliente de solicitação para SMB</span><span class="sxs-lookup"><span data-stu-id="9f0bb-149">Setting up a pull client for SMB</span></span>

<span data-ttu-id="9f0bb-150">Para configurar um cliente solicita configurações de e/ou recursos a partir de uma partilha de SMB, configurar Local Configuration Manager (o MMC o cliente) com **ConfigurationRepositoryShare** e **ResourceRepositoryShare** blocos que especifique a partilha a partir do qual solicitar configurações e os recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-150">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="9f0bb-151">Para obter mais informações sobre como configurar o MMC, consulte [configurar um cliente de extração com o ID de configuração](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="9f0bb-151">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

><span data-ttu-id="9f0bb-152">**Nota:** de simplicidade, este exemplo utiliza o **PSDscAllowPlainTextPassword** para permitir a passagem de uma palavra-passe de texto simples para o **credencial** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-152">**Note:** For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="9f0bb-153">Para obter informações sobre a forma mais segura a transmitir as credenciais, consulte [opções de credenciais nos dados de configuração](configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="9f0bb-153">For information about passing credentials more securely, see [Credentials Options in Configuration Data](configDataCredentials.md).</span></span>

><span data-ttu-id="9f0bb-154">**Nota:** tem de especificar um **ConfigurationID** no **definições** bloco de uma configuração meta para um servidor de solicitação do SMB, mesmo que apenas são extrair recursos.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-154">**Note:** You must specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

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

## <a name="acknowledgements"></a><span data-ttu-id="9f0bb-155">Confirmações</span><span class="sxs-lookup"><span data-stu-id="9f0bb-155">Acknowledgements</span></span>

<span data-ttu-id="9f0bb-156">Especial obrigado às seguintes:</span><span class="sxs-lookup"><span data-stu-id="9f0bb-156">Special thanks to the following:</span></span>

- <span data-ttu-id="9f0bb-157">Mike F. Robbins, cuja cronologia utilizando SMB para DSC ajudou a informar o conteúdo deste tópico.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-157">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="9f0bb-158">O blogue é [Mike F Robbins](http://mikefrobbins.com/).</span><span class="sxs-lookup"><span data-stu-id="9f0bb-158">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="9f0bb-159">Serge Nikalaichyk, que tiver criado o **cNtfsAccessControl** módulo.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-159">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="9f0bb-160">A origem para este módulo é https://github.com/SNikalaichyk/cNtfsAccessControl.</span><span class="sxs-lookup"><span data-stu-id="9f0bb-160">The source for this module is at https://github.com/SNikalaichyk/cNtfsAccessControl.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f0bb-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f0bb-161">See also</span></span>
- [<span data-ttu-id="9f0bb-162">Descrição geral da configuração do estado pretendido do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9f0bb-162">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="9f0bb-163">Aplicar configurações</span><span class="sxs-lookup"><span data-stu-id="9f0bb-163">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="9f0bb-164">Configurar um cliente de solicitação através de IDs de configuração</span><span class="sxs-lookup"><span data-stu-id="9f0bb-164">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)