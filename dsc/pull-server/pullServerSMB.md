---
ms.date: 04/11/2018
keywords: DSC, powershell, configuração, a configuração
title: Configurar um servidor de solicitação SMB de DSC
ms.openlocfilehash: 722120369df9ff383a02c69111e0bacf2e2e76a5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404728"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="b1961-103">Configurar um servidor de solicitação SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="b1961-103">Setting up a DSC SMB pull server</span></span>

<span data-ttu-id="b1961-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b1961-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b1961-105">O servidor de solicitação (recurso do Windows *DSC-serviço*) é um componente suportado do Windows Server no entanto, não existem planos para oferecer novas funcionalidades ou capacidades.</span><span class="sxs-lookup"><span data-stu-id="b1961-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="b1961-106">É recomendado para começar a fazer a transição geridos os clientes [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação de mensagens em fila no Windows Server) ou uma das soluções da Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="b1961-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="b1961-107">Um DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) servidor de solicitação é um computador que aloja partilhas de ficheiros SMB que tornam os ficheiros de configuração de DSC e recursos de DSC disponíveis para nós de destino quando esses nós peça para os mesmos.</span><span class="sxs-lookup"><span data-stu-id="b1961-107">A DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="b1961-108">Para utilizar um servidor de solicitação SMB de DSC, terá de:</span><span class="sxs-lookup"><span data-stu-id="b1961-108">To use an SMB pull server for DSC, you have to:</span></span>

- <span data-ttu-id="b1961-109">Configurar a partilha de ficheiros SMB num servidor com o PowerShell 4.0 ou superior</span><span class="sxs-lookup"><span data-stu-id="b1961-109">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="b1961-110">Configurar um cliente a executar o PowerShell 4.0 ou superior para solicitar a partir de que a partilha de SMB</span><span class="sxs-lookup"><span data-stu-id="b1961-110">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="b1961-111">Usando o recurso de xSmbShare para criar uma partilha de ficheiros SMB</span><span class="sxs-lookup"><span data-stu-id="b1961-111">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="b1961-112">Existem várias formas de configurar a partilha de ficheiros SMB, mas vamos dar uma olhada em como pode fazer isso usando a DSC.</span><span class="sxs-lookup"><span data-stu-id="b1961-112">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="b1961-113">Instalar o recurso de xSmbShare</span><span class="sxs-lookup"><span data-stu-id="b1961-113">Install the xSmbShare resource</span></span>

<span data-ttu-id="b1961-114">Chamar o [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet para instalar o **xSmbShare** módulo.</span><span class="sxs-lookup"><span data-stu-id="b1961-114">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xSmbShare** module.</span></span>

> [!NOTE]
> <span data-ttu-id="b1961-115">`Install-Module` está incluído nos **PowerShellGet** módulo, que está incluído no PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="b1961-115">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="b1961-116">Pode baixar o **PowerShellGet** módulo para o PowerShell 3.0 e 4.0 na [pré-visualização de módulos do PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="b1961-116">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
> <span data-ttu-id="b1961-117">O **xSmbShare** contém o recurso de DSC **xSmbShare**, que podem ser utilizadas para criar uma partilha de ficheiros SMB.</span><span class="sxs-lookup"><span data-stu-id="b1961-117">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="b1961-118">Criar a partilha de ficheiro e diretório</span><span class="sxs-lookup"><span data-stu-id="b1961-118">Create the directory and file share</span></span>

<span data-ttu-id="b1961-119">Utiliza a seguinte configuração o **arquivo** recurso para criar o diretório para a partilha e o **xSmbShare** recurso para configurar a partilha SMB:</span><span class="sxs-lookup"><span data-stu-id="b1961-119">The following configuration uses the **File** resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

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
            FullAccess = 'admininstrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

<span data-ttu-id="b1961-120">A configuração cria o diretório `C:\DscSmbShare`, se ainda não existir e, em seguida, utiliza esse diretório como uma partilha de ficheiros SMB.</span><span class="sxs-lookup"><span data-stu-id="b1961-120">The configuration creates the directory `C:\DscSmbShare`, if it doesn't already exist, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="b1961-121">**FullAccess** deve receber a qualquer conta que tem de escrever ou eliminar da partilha de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="b1961-121">**FullAccess** should be given to any account that needs to write to or delete from the file share.</span></span> <span data-ttu-id="b1961-122">**ReadAccess** tem de obter para quaisquer nós de cliente que obtém configurações de e/ou de recursos de DSC da partilha.</span><span class="sxs-lookup"><span data-stu-id="b1961-122">**ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share.</span></span>

> [!NOTE]
> <span data-ttu-id="b1961-123">DSC é executado como a conta de sistema por predefinição, para que o próprio computador tem de ter acesso à partilha.</span><span class="sxs-lookup"><span data-stu-id="b1961-123">DSC runs as the system account by default, so the computer itself must have access to the share.</span></span>

### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="b1961-124">Conceder acesso de sistema de ficheiros para o cliente de solicitação</span><span class="sxs-lookup"><span data-stu-id="b1961-124">Give file system access to the pull client</span></span>

<span data-ttu-id="b1961-125">Dando **ReadAccess** para um cliente nó permite nesse nó para aceder à partilha SMB, mas não para ficheiros ou pastas dentro dessa partilha.</span><span class="sxs-lookup"><span data-stu-id="b1961-125">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="b1961-126">Tem de conceder explicitamente cliente acesso de nós para a pasta de partilha SMB e subpastas.</span><span class="sxs-lookup"><span data-stu-id="b1961-126">You have to explicitly grant client nodes access to the SMB share folder and subfolders.</span></span> <span data-ttu-id="b1961-127">Podemos fazer isso com DSC, adicionando a utilizar o **cNtfsPermissionEntry** recurso, o que está contido no [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) módulo.</span><span class="sxs-lookup"><span data-stu-id="b1961-127">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="b1961-128">A seguinte configuração adiciona um **cNtfsPermissionEntry** bloco que concede acesso de ReadAndExecute para o cliente de solicitação:</span><span class="sxs-lookup"><span data-stu-id="b1961-128">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

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

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="b1961-129">Colocar recursos e configurações</span><span class="sxs-lookup"><span data-stu-id="b1961-129">Placing configurations and resources</span></span>

<span data-ttu-id="b1961-130">Guarde todos os ficheiros de MOF de configuração e/ou recursos de DSC que pretende que nós de cliente para obter a pasta de partilha do SMB.</span><span class="sxs-lookup"><span data-stu-id="b1961-130">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="b1961-131">Qualquer ficheiro MOF de configuração deve ser nomeado *ConfigurationID*arquivos. MOF, onde *ConfigurationID* é o valor do **ConfigurationID** propriedade do LCM o nó de destino.</span><span class="sxs-lookup"><span data-stu-id="b1961-131">Any configuration MOF file must be named *ConfigurationID*.mof, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="b1961-132">Para obter mais informações sobre como configurar clientes de extração, consulte [como configurar um cliente de solicitação através do ID de configuração](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="b1961-132">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b1961-133">Se estiver a utilizar um servidor de solicitação SMB tem de utilizar os IDs de configuração.</span><span class="sxs-lookup"><span data-stu-id="b1961-133">You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="b1961-134">Nomes de configuração não são suportados para SMB.</span><span class="sxs-lookup"><span data-stu-id="b1961-134">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="b1961-135">Cada módulo de recursos tem de ser comprimido e nomeado de acordo com o seguinte padrão `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="b1961-135">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="b1961-136">Por exemplo, um módulo com o nome xWebAdminstration com uma versão do módulo do 3.1.2.0 teria o nome 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="b1961-136">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="b1961-137">Cada versão de um módulo tem de estar contido num arquivo zip único.</span><span class="sxs-lookup"><span data-stu-id="b1961-137">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="b1961-138">Não são suportadas versões separadas de um módulo num arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="b1961-138">Separate versions of a module in a zip file are not supported.</span></span> <span data-ttu-id="b1961-139">Antes de empacotar os módulos de recursos de DSC para utilização com o servidor de solicitação, precisa fazer uma pequena alteração para a estrutura de diretórios.</span><span class="sxs-lookup"><span data-stu-id="b1961-139">Before packaging up DSC resource modules for use with pull server, you need to make a small change to the directory structure.</span></span>

<span data-ttu-id="b1961-140">O formato de padrão de módulos que contém o recurso de DSC no WMF 5.0 é `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="b1961-140">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>

<span data-ttu-id="b1961-141">Antes de empacotamento tendo em vista o servidor de solicitação simplesmente remover o `{Module version}` pasta para que o caminho se torna `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="b1961-141">Before packaging up for the pull server simply remove the `{Module version}` folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="b1961-142">Com esta alteração, zip na pasta, conforme descrito acima e colocar esses arquivos zip na pasta de partilha SMB.</span><span class="sxs-lookup"><span data-stu-id="b1961-142">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="b1961-143">Criar a soma de verificação do MOF</span><span class="sxs-lookup"><span data-stu-id="b1961-143">Creating the MOF checksum</span></span>

<span data-ttu-id="b1961-144">Um ficheiro MOF de configuração tem de ser emparelhado com um ficheiro de soma de verificação para que um LCM num nó de destino pode validar a configuração.</span><span class="sxs-lookup"><span data-stu-id="b1961-144">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="b1961-145">Para criar uma soma de verificação, chamar o [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b1961-145">To create a checksum, call the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span></span> <span data-ttu-id="b1961-146">O cmdlet assume um `Path` parâmetro que especifica a pasta onde está localizada a MOF de configuração.</span><span class="sxs-lookup"><span data-stu-id="b1961-146">The cmdlet takes a `Path` parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="b1961-147">O cmdlet cria um ficheiro de soma de verificação com o nome `ConfigurationMOFName.mof.checksum`, onde `ConfigurationMOFName` é o nome do ficheiro de mof de configuração.</span><span class="sxs-lookup"><span data-stu-id="b1961-147">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="b1961-148">Se existirem mais de uma configuração de MOF ficheiros na pasta especificada, é criada uma soma de verificação para cada configuração na pasta.</span><span class="sxs-lookup"><span data-stu-id="b1961-148">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="b1961-149">O ficheiro de soma de verificação deve estar presente no mesmo diretório que o ficheiro MOF de configuração (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` por predefinição), e ter o mesmo nome com o `.checksum` extensão acrescentada.</span><span class="sxs-lookup"><span data-stu-id="b1961-149">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

> [!NOTE]
> <span data-ttu-id="b1961-150">Se alterar o ficheiro MOF de configuração de qualquer forma, também tem de recriar o arquivo de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="b1961-150">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="b1961-151">Como configurar um cliente de solicitação para SMB</span><span class="sxs-lookup"><span data-stu-id="b1961-151">Setting up a pull client for SMB</span></span>

<span data-ttu-id="b1961-152">Para configurar um cliente que solicita as configurações de e/ou os recursos a partir de uma partilha de SMB, configurou com, a Local Configuration Manager (LCM do cliente) **ConfigurationRepositoryShare** e **ResourceRepositoryShare** blocos que especifique a partilha do que solicitar configurações e recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="b1961-152">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="b1961-153">Para obter mais informações sobre como configurar o LCM, consulte [como configurar um cliente de solicitação através do ID de configuração](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="b1961-153">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b1961-154">Para simplificar, este exemplo utiliza a **PSDscAllowPlainTextPassword** para permitir a passagem de uma palavra-passe de texto sem formatação para o **credencial** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b1961-154">For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="b1961-155">Para obter informações sobre passar credenciais de forma mais segura, consulte [opções de credenciais nos dados de configuração](../configurations/configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="b1961-155">For information about passing credentials more securely, see [Credentials Options in Configuration Data](../configurations/configDataCredentials.md).</span></span>
>
> <span data-ttu-id="b1961-156">**Tem** especificar um **ConfigurationID** no **definições** bloco de um metaconfiguration para um servidor de solicitação SMB, mesmo se está extraindo apenas recursos.</span><span class="sxs-lookup"><span data-stu-id="b1961-156">You **MUST** specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

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

## <a name="acknowledgements"></a><span data-ttu-id="b1961-157">Confirmações</span><span class="sxs-lookup"><span data-stu-id="b1961-157">Acknowledgements</span></span>

<span data-ttu-id="b1961-158">Agradecimentos especiais a seguintes pessoas:</span><span class="sxs-lookup"><span data-stu-id="b1961-158">Special thanks to the following individuals:</span></span>

- <span data-ttu-id="b1961-159">Mike F. Robbins, cujas postagens sobre como utilizar o SMB de DSC ajudaram a informar o conteúdo deste tópico.</span><span class="sxs-lookup"><span data-stu-id="b1961-159">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="b1961-160">Seu blog está em [Mike F Robbins](http://mikefrobbins.com/).</span><span class="sxs-lookup"><span data-stu-id="b1961-160">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="b1961-161">Serge Nikalaichyk, que são criados os **cNtfsAccessControl** módulo.</span><span class="sxs-lookup"><span data-stu-id="b1961-161">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="b1961-162">A origem para este módulo é parte [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span><span class="sxs-lookup"><span data-stu-id="b1961-162">The source for this module is at [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span></span>

## <a name="see-also"></a><span data-ttu-id="b1961-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1961-163">See also</span></span>

[<span data-ttu-id="b1961-164">Windows PowerShell Desired State Configuration descrição-geral</span><span class="sxs-lookup"><span data-stu-id="b1961-164">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)

[<span data-ttu-id="b1961-165">Aplicar configurações</span><span class="sxs-lookup"><span data-stu-id="b1961-165">Enacting configurations</span></span>](enactingConfigurations.md)

[<span data-ttu-id="b1961-166">Configurar um cliente de solicitação através de IDs de configuração</span><span class="sxs-lookup"><span data-stu-id="b1961-166">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)