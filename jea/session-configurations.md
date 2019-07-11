---
ms.date: 07/10/2019
keywords: jea, powershell, segurança
title: Configurações de sessão JEA
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726542"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="8caa9-103">Configurações de sessão JEA</span><span class="sxs-lookup"><span data-stu-id="8caa9-103">JEA Session Configurations</span></span>

<span data-ttu-id="8caa9-104">Um ponto final JEA está registado num sistema ao criar e registar um ficheiro de configuração de sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8caa9-104">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file.</span></span> <span data-ttu-id="8caa9-105">Configurações de sessão definem quem pode usar o ponto final da JEA e quais funções aos quais têm acesso.</span><span class="sxs-lookup"><span data-stu-id="8caa9-105">Session configurations define who can use the JEA endpoint and which roles they have access to.</span></span> <span data-ttu-id="8caa9-106">Elas também definem as definições globais que se aplicam a todos os utilizadores da sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="8caa9-106">They also define global settings that apply to all users of the JEA session.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="8caa9-107">Criar um ficheiro de configuração de sessão</span><span class="sxs-lookup"><span data-stu-id="8caa9-107">Create a session configuration file</span></span>

<span data-ttu-id="8caa9-108">Para registar um ponto final JEA, tem de especificar a configuração do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="8caa9-108">To register a JEA endpoint, you must specify how that endpoint is configured.</span></span> <span data-ttu-id="8caa9-109">Existem muitas opções a serem considerados.</span><span class="sxs-lookup"><span data-stu-id="8caa9-109">There are many options to consider.</span></span> <span data-ttu-id="8caa9-110">As opções mais importantes são:</span><span class="sxs-lookup"><span data-stu-id="8caa9-110">The most important options are:</span></span>

- <span data-ttu-id="8caa9-111">Quem tem acesso ao ponto final JEA</span><span class="sxs-lookup"><span data-stu-id="8caa9-111">Who has access to the JEA endpoint</span></span>
- <span data-ttu-id="8caa9-112">Que funções de ser atribuídos</span><span class="sxs-lookup"><span data-stu-id="8caa9-112">Which roles they be assigned</span></span>
- <span data-ttu-id="8caa9-113">Que identidade JEA utiliza nos bastidores</span><span class="sxs-lookup"><span data-stu-id="8caa9-113">Which identity JEA uses under the covers</span></span>
- <span data-ttu-id="8caa9-114">O nome do ponto final JEA</span><span class="sxs-lookup"><span data-stu-id="8caa9-114">The name of the JEA endpoint</span></span>

<span data-ttu-id="8caa9-115">Estas opções são definidas num arquivo de dados do PowerShell com um `.pssc` extensão conhecido como um ficheiro de configuração de sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8caa9-115">These options are defined in a PowerShell data file with a `.pssc` extension known as a PowerShell session configuration file.</span></span> <span data-ttu-id="8caa9-116">O ficheiro de configuração de sessão pode ser editado com qualquer editor de texto.</span><span class="sxs-lookup"><span data-stu-id="8caa9-116">The session configuration file can be edited using any text editor.</span></span>

<span data-ttu-id="8caa9-117">Execute o seguinte comando para criar um ficheiro de configuração de modelo em branco.</span><span class="sxs-lookup"><span data-stu-id="8caa9-117">Run the following command to create a blank template configuration file.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="8caa9-118">Por predefinição, apenas as opções de configuração mais comuns são incluídas no ficheiro de modelo.</span><span class="sxs-lookup"><span data-stu-id="8caa9-118">Only the most common configuration options are included in the template file by default.</span></span> <span data-ttu-id="8caa9-119">Utilize o `-Full` comutador para incluir todas as configurações aplicáveis no PSSC gerado.</span><span class="sxs-lookup"><span data-stu-id="8caa9-119">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="8caa9-120">O `-SessionType RestrictedRemoteServer` campo indica que a configuração de sessão é utilizada pelo JEA para a gestão segura.</span><span class="sxs-lookup"><span data-stu-id="8caa9-120">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration is used by JEA for secure management.</span></span> <span data-ttu-id="8caa9-121">Sessões deste tipo operam **NoLanguage** modo e só tem acesso para os seguintes comandos padrão (e aliases):</span><span class="sxs-lookup"><span data-stu-id="8caa9-121">Sessions of this type operate in **NoLanguage** mode and only have access to the following default commands (and aliases):</span></span>

- <span data-ttu-id="8caa9-122">Clear-Host (cls, claro)</span><span class="sxs-lookup"><span data-stu-id="8caa9-122">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="8caa9-123">Exit-PSSession (exsn, exit)</span><span class="sxs-lookup"><span data-stu-id="8caa9-123">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="8caa9-124">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="8caa9-124">Get-Command (gcm)</span></span>
- <span data-ttu-id="8caa9-125">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="8caa9-125">Get-FormatData</span></span>
- <span data-ttu-id="8caa9-126">Get-Help</span><span class="sxs-lookup"><span data-stu-id="8caa9-126">Get-Help</span></span>
- <span data-ttu-id="8caa9-127">Objeto de medida (medidas)</span><span class="sxs-lookup"><span data-stu-id="8caa9-127">Measure-Object (measure)</span></span>
- <span data-ttu-id="8caa9-128">Out-Default</span><span class="sxs-lookup"><span data-stu-id="8caa9-128">Out-Default</span></span>
- <span data-ttu-id="8caa9-129">Select-Object (selecionar)</span><span class="sxs-lookup"><span data-stu-id="8caa9-129">Select-Object (select)</span></span>

<span data-ttu-id="8caa9-130">Não existem fornecedores de PowerShell estão disponíveis, nem são que programas de qualquer externo (executáveis ou scripts).</span><span class="sxs-lookup"><span data-stu-id="8caa9-130">No PowerShell providers are available, nor are any external programs (executables or scripts).</span></span>

<span data-ttu-id="8caa9-131">Para obter mais informações sobre os modos de idioma, consulte [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span><span class="sxs-lookup"><span data-stu-id="8caa9-131">For more information about language modes, see [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="8caa9-132">Escolha a identidade JEA</span><span class="sxs-lookup"><span data-stu-id="8caa9-132">Choose the JEA identity</span></span>

<span data-ttu-id="8caa9-133">Em segundo plano, JEA tem uma identidade (conta) para utilizar durante a execução de comandos de um usuário conectado.</span><span class="sxs-lookup"><span data-stu-id="8caa9-133">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="8caa9-134">Definir que identidade JEA utiliza no ficheiro de configuração de sessão.</span><span class="sxs-lookup"><span data-stu-id="8caa9-134">You define which identity JEA uses in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="8caa9-135">Conta Virtual local</span><span class="sxs-lookup"><span data-stu-id="8caa9-135">Local Virtual Account</span></span>

<span data-ttu-id="8caa9-136">Contas virtuais locais são úteis quando todas as funções definidas para o ponto final da JEA são utilizadas para gerir o computador local e uma conta de administrador local é suficiente para executar os comandos com êxito.</span><span class="sxs-lookup"><span data-stu-id="8caa9-136">Local virtual accounts are useful when all roles defined for the JEA endpoint are used to manage the local machine and a local administrator account is sufficient to run the commands successfully.</span></span>
<span data-ttu-id="8caa9-137">Contas virtuais são contas temporárias que são exclusivas para um utilizador específico e apenas os últimos durante a sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8caa9-137">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span> <span data-ttu-id="8caa9-138">Num servidor membro ou estação de trabalho, contas virtuais pertencem ao computador local **administradores** grupo.</span><span class="sxs-lookup"><span data-stu-id="8caa9-138">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group.</span></span> <span data-ttu-id="8caa9-139">Num controlador de domínio do Active Directory, contas virtuais pertencem ao domínio **Admins do domínio** grupo.</span><span class="sxs-lookup"><span data-stu-id="8caa9-139">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="8caa9-140">Se as funções definidas na configuração da sessão não exigem privilégios administrativos completos, pode especificar os grupos de segurança para o qual irá pertencer a conta virtual.</span><span class="sxs-lookup"><span data-stu-id="8caa9-140">If the roles defined by the session configuration don't require full administrative privilege, you can specify the security groups to which the virtual account will belong.</span></span> <span data-ttu-id="8caa9-141">Num servidor membro ou estação de trabalho, os grupos de segurança especificado tem de ser grupos locais, não os grupos de um domínio.</span><span class="sxs-lookup"><span data-stu-id="8caa9-141">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="8caa9-142">Quando um ou mais grupos de segurança são especificados, a conta virtual não está atribuída ao grupo de administradores locais ou de domínio.</span><span class="sxs-lookup"><span data-stu-id="8caa9-142">When one or more security groups are specified, the virtual account isn't assigned to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="8caa9-143">Contas virtuais recebem temporariamente o início de sessão como um direito de serviço na política de segurança de servidor local.</span><span class="sxs-lookup"><span data-stu-id="8caa9-143">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span> <span data-ttu-id="8caa9-144">Se um dos VirtualAccountGroups especificado já foi concedido este direito na política, a conta virtual individual já não será adicionada e removida da política.</span><span class="sxs-lookup"><span data-stu-id="8caa9-144">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span> <span data-ttu-id="8caa9-145">Isso pode ser útil em cenários como controladores de domínio em que a revisões para a política de segurança do controlador de domínio de perto são auditados.</span><span class="sxs-lookup"><span data-stu-id="8caa9-145">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span> <span data-ttu-id="8caa9-146">Isso só está disponível no Windows Server 2016 com a Novembro de 2018 ou rollup posterior e Windows Server 2019 com o de 2019 de Janeiro ou rollup posterior.</span><span class="sxs-lookup"><span data-stu-id="8caa9-146">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="8caa9-147">Conta de serviço gerida de grupo</span><span class="sxs-lookup"><span data-stu-id="8caa9-147">Group-managed service account</span></span>

<span data-ttu-id="8caa9-148">Uma conta de serviço gerida de grupo (GMSA) é a identidade adequada a utilizar quando os utilizadores JEA precisam de aceder a recursos de rede, como partilhas de ficheiros e serviços da web.</span><span class="sxs-lookup"><span data-stu-id="8caa9-148">A group-managed service account (GMSA) is the appropriate identity to use when JEA users need to access network resources such as file shares and web services.</span></span> <span data-ttu-id="8caa9-149">As GMSAs dão-lhe uma identidade de domínio que é utilizada para autenticar com recursos em qualquer computador no domínio.</span><span class="sxs-lookup"><span data-stu-id="8caa9-149">GMSAs give you a domain identity that is used to authenticate with resources on any machine within the domain.</span></span> <span data-ttu-id="8caa9-150">Os direitos de que uma GMSA fornece são determinados pelos recursos que está a aceder.</span><span class="sxs-lookup"><span data-stu-id="8caa9-150">The rights that a GMSA provides are determined by the resources you're accessing.</span></span> <span data-ttu-id="8caa9-151">Não tem direitos de administrador em qualquer máquinas ou serviços, a menos que o administrador de máquina ou serviço lhe tiver concedido explicitamente esses direitos a GMSA.</span><span class="sxs-lookup"><span data-stu-id="8caa9-151">You don't have admin rights on any machines or services unless the machine or service administrator has explicitly granted those rights to the GMSA.</span></span>

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

<span data-ttu-id="8caa9-152">As GMSAs devem ser apenas quando necessário:</span><span class="sxs-lookup"><span data-stu-id="8caa9-152">GMSAs should only be used when necessary:</span></span>

- <span data-ttu-id="8caa9-153">É difícil efectuar o rastreio ações para um utilizador ao utilizar uma GMSA.</span><span class="sxs-lookup"><span data-stu-id="8caa9-153">It's difficult to trace back actions to a user when using a GMSA.</span></span> <span data-ttu-id="8caa9-154">Todos os usuários compartilha a mesma identidade Run.</span><span class="sxs-lookup"><span data-stu-id="8caa9-154">Every user shares the same run-as identity.</span></span> <span data-ttu-id="8caa9-155">Tem de rever os registos para correlacionar a utilizadores individuais com as suas ações e de transcrições de sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8caa9-155">You must review PowerShell session transcripts and logs to correlate individual users with their actions.</span></span>

- <span data-ttu-id="8caa9-156">A GMSA pode ter acesso a vários recursos de rede que o usuário conectado, não precisa acessar.</span><span class="sxs-lookup"><span data-stu-id="8caa9-156">The GMSA may have access to many network resources that the connecting user doesn't need access to.</span></span> <span data-ttu-id="8caa9-157">Sempre tente limitar as permissões efetivas numa sessão JEA para acompanhar o princípio de privilégio mínimo.</span><span class="sxs-lookup"><span data-stu-id="8caa9-157">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="8caa9-158">Contas de serviço geridas de grupo só estão disponíveis em computadores associados a um domínio com o PowerShell 5.1 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="8caa9-158">Group managed service accounts are only available on domain-joined machines using PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="8caa9-159">Para obter mais informações sobre como proteger uma sessão JEA, consulte a [considerações de segurança](security-considerations.md) artigo.</span><span class="sxs-lookup"><span data-stu-id="8caa9-159">For more information about securing a JEA session, see the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="8caa9-160">Transcrições de sessão</span><span class="sxs-lookup"><span data-stu-id="8caa9-160">Session transcripts</span></span>

<span data-ttu-id="8caa9-161">Recomenda-se que configure um ponto final JEA para transcrições automaticamente registos de sessões dos utilizadores.</span><span class="sxs-lookup"><span data-stu-id="8caa9-161">It's recommended that you configure a JEA endpoint to automatically record transcripts of users' sessions.</span></span> <span data-ttu-id="8caa9-162">Transcrições de sessão do PowerShell contêm informações sobre o usuário conectado, a execução como identidade atribuída, e os comandos são executados pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="8caa9-162">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span> <span data-ttu-id="8caa9-163">Eles podem ser úteis para uma equipe de auditoria que precisa entender quem as fez uma alteração específica para um sistema.</span><span class="sxs-lookup"><span data-stu-id="8caa9-163">They can be useful to an auditing team who needs to understand who made a specific change to a system.</span></span>

<span data-ttu-id="8caa9-164">Para configurar a transcrição automática no ficheiro de configuração de sessão, forneça um caminho para uma pasta onde as transcrições devem ser armazenadas.</span><span class="sxs-lookup"><span data-stu-id="8caa9-164">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="8caa9-165">Transcrições são escritas para a pasta, o **Sistema Local** conta, que requer a leitura e de acesso de escrita para o diretório.</span><span class="sxs-lookup"><span data-stu-id="8caa9-165">Transcripts are written to the folder by the **Local System** account, which requires read and write access to the directory.</span></span> <span data-ttu-id="8caa9-166">Os usuários padrão não devem ter acesso à pasta.</span><span class="sxs-lookup"><span data-stu-id="8caa9-166">Standard users should have no access to the folder.</span></span> <span data-ttu-id="8caa9-167">Limite o número de administradores de segurança que têm acesso para auditar as transcrições.</span><span class="sxs-lookup"><span data-stu-id="8caa9-167">Limit the number of security administrators that have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="8caa9-168">Unidade de utilizador</span><span class="sxs-lookup"><span data-stu-id="8caa9-168">User drive</span></span>

<span data-ttu-id="8caa9-169">Se os utilizadores de ligação tem de copiar ficheiros de ou para o ponto final da JEA, pode ativar a unidade de utilizador no ficheiro de configuração de sessão.</span><span class="sxs-lookup"><span data-stu-id="8caa9-169">If your connecting users need to copy files to or from the JEA endpoint, you can enable the user drive in the session configuration file.</span></span> <span data-ttu-id="8caa9-170">A unidade de utilizador é um **PSDrive** que está mapeado para uma pasta exclusiva para cada usuário conectado.</span><span class="sxs-lookup"><span data-stu-id="8caa9-170">The user drive is a **PSDrive** that is mapped to a unique folder for each connecting user.</span></span> <span data-ttu-id="8caa9-171">Esta pasta permite que os usuários copiem arquivos de ou para o sistema sem dar-lhes acesso ao sistema de ficheiros completa ou expor o fornecedor do sistema de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="8caa9-171">This folder allows users to copy files to or from the system without giving them access to the full file system or exposing the FileSystem provider.</span></span> <span data-ttu-id="8caa9-172">O conteúdo da unidade de utilizador é persistente entre sessões para acomodar as situações em que a conectividade de rede pode ser interrompida.</span><span class="sxs-lookup"><span data-stu-id="8caa9-172">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="8caa9-173">Por predefinição, a unidade de utilizador permite-lhe armazenar um máximo de 50MB de dados por utilizador.</span><span class="sxs-lookup"><span data-stu-id="8caa9-173">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span> <span data-ttu-id="8caa9-174">Pode limitar a quantidade de dados de um utilizador pode consumir com o *UserDriveMaximumSize* campo.</span><span class="sxs-lookup"><span data-stu-id="8caa9-174">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="8caa9-175">Se não pretender que os dados na unidade do utilizador para ser persistente, pode configurar uma tarefa agendada no sistema para limpar automaticamente a pasta de todas as noites.</span><span class="sxs-lookup"><span data-stu-id="8caa9-175">If you don't want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="8caa9-176">A unidade de utilizador só está disponível no PowerShell 5.1 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="8caa9-176">The user drive is only available in PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="8caa9-177">Para obter mais informações sobre PSDrives, consulte [unidades de gerenciamento PowerShell](/powershell/scripting/samples/managing-windows-powershell-drives).</span><span class="sxs-lookup"><span data-stu-id="8caa9-177">For more information about PSDrives, see [Managing PowerShell drives](/powershell/scripting/samples/managing-windows-powershell-drives).</span></span>

### <a name="role-definitions"></a><span data-ttu-id="8caa9-178">Definições de funções</span><span class="sxs-lookup"><span data-stu-id="8caa9-178">Role definitions</span></span>

<span data-ttu-id="8caa9-179">Definições de funções num arquivo de configuração de sessão definem o mapeamento dos **usuários** ao **funções**.</span><span class="sxs-lookup"><span data-stu-id="8caa9-179">Role definitions in a session configuration file define the mapping of **users** to **roles**.</span></span> <span data-ttu-id="8caa9-180">Cada utilizador ou grupo incluído neste campo é concedido permissão para o ponto final da JEA quando é registado.</span><span class="sxs-lookup"><span data-stu-id="8caa9-180">Every user or group included in this field is granted permission to the JEA endpoint when it's registered.</span></span>
<span data-ttu-id="8caa9-181">Cada utilizador ou grupo pode ser incluído como uma chave da tabela de hash apenas uma vez, mas pode ser atribuído várias funções.</span><span class="sxs-lookup"><span data-stu-id="8caa9-181">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span> <span data-ttu-id="8caa9-182">O nome da capacidade de função deve ser o nome do arquivo de recurso de função, sem o `.psrc` extensão.</span><span class="sxs-lookup"><span data-stu-id="8caa9-182">The name of the role capability should be the name of the role capability file, without the `.psrc` extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="8caa9-183">Se um utilizador pertencer a mais de um grupo na definição de função, eles recebem acesso às funções de cada.</span><span class="sxs-lookup"><span data-stu-id="8caa9-183">If a user belongs to more than one group in the role definition, they get access to the roles of each.</span></span> <span data-ttu-id="8caa9-184">Quando duas funções de concedem acesso para os mesmos cmdlets, o conjunto de parâmetros mais permissivo é concedido ao utilizador.</span><span class="sxs-lookup"><span data-stu-id="8caa9-184">When two roles grant access to the same cmdlets, the most permissive parameter set is granted to the user.</span></span>

<span data-ttu-id="8caa9-185">Ao especificar grupos de utilizadores ou no campo de definições de função, certifique-se de que utiliza o nome do computador, não **localhost** ou carateres universais.</span><span class="sxs-lookup"><span data-stu-id="8caa9-185">When specifying local users or groups in the role definitions field, be sure to use the computer name, not **localhost** or wildcards.</span></span> <span data-ttu-id="8caa9-186">Pode verificar o nome do computador ao inspecionar o `$env:COMPUTERNAME` variável.</span><span class="sxs-lookup"><span data-stu-id="8caa9-186">You can check the computer name by inspecting the `$env:COMPUTERNAME` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="8caa9-187">Ordem de pesquisa de capacidade de função</span><span class="sxs-lookup"><span data-stu-id="8caa9-187">Role capability search order</span></span>

<span data-ttu-id="8caa9-188">Conforme mostrado no exemplo acima, as funcionalidades de função são referenciadas pelo nome de base do arquivo de recurso de função.</span><span class="sxs-lookup"><span data-stu-id="8caa9-188">As shown in the example above, role capabilities are referenced by the base name of the role capability file.</span></span> <span data-ttu-id="8caa9-189">O nome de base de um ficheiro é o nome de ficheiro sem a extensão.</span><span class="sxs-lookup"><span data-stu-id="8caa9-189">The base name of a file is the filename without the extension.</span></span> <span data-ttu-id="8caa9-190">Se várias funcionalidades de função estão disponíveis no sistema com o mesmo nome, o PowerShell usa sua ordem de pesquisa implícito para selecionar o ficheiro de recurso de função em vigor.</span><span class="sxs-lookup"><span data-stu-id="8caa9-190">If multiple role capabilities are available on the system with the same name, PowerShell uses its implicit search order to select the effective role capability file.</span></span> <span data-ttu-id="8caa9-191">JEA faz **não** conceder acesso a todos os ficheiros de recurso de função com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="8caa9-191">JEA does **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="8caa9-192">JEA utiliza o `$env:PSModulePath` variável de ambiente para determinar os caminhos para verificar a existência de arquivos de recurso de função.</span><span class="sxs-lookup"><span data-stu-id="8caa9-192">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span> <span data-ttu-id="8caa9-193">Dentro de cada um desses caminhos, JEA procura válidos módulos do PowerShell que contêm uma subpasta do "RoleCapabilities".</span><span class="sxs-lookup"><span data-stu-id="8caa9-193">Within each of those paths, JEA looks for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span> <span data-ttu-id="8caa9-194">Tal como acontece com a importação de módulos JEA prefere funcionalidades de função que são fornecidas com o Windows às capacidades de função personalizada com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="8caa9-194">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>

<span data-ttu-id="8caa9-195">Para todos os outros conflitos de nomenclatura, a precedência é determinada pela ordem em que o Windows enumera os ficheiros no diretório.</span><span class="sxs-lookup"><span data-stu-id="8caa9-195">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory.</span></span> <span data-ttu-id="8caa9-196">A ordem não é garantida que alfabética.</span><span class="sxs-lookup"><span data-stu-id="8caa9-196">The order isn't guaranteed to be alphabetical.</span></span> <span data-ttu-id="8caa9-197">O primeiro arquivo de recurso de função encontrado que corresponda ao especificado nome é utilizado para o usuário conectado.</span><span class="sxs-lookup"><span data-stu-id="8caa9-197">The first role capability file found that matches the specified name is used for the connecting user.</span></span> <span data-ttu-id="8caa9-198">Desde a pesquisa de capacidade de função ordem não é determinística, é **vivamente recomendado** que funcionalidades de função têm nomes de arquivo exclusivo.</span><span class="sxs-lookup"><span data-stu-id="8caa9-198">Since the role capability search order isn't deterministic, it's **strongly recommended** that role capabilities have unique filenames.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="8caa9-199">Regras de acesso condicional</span><span class="sxs-lookup"><span data-stu-id="8caa9-199">Conditional access rules</span></span>

<span data-ttu-id="8caa9-200">Todos os utilizadores e grupos incluídos os **RoleDefinitions** campo recebem automaticamente acesso a pontos finais JEA.</span><span class="sxs-lookup"><span data-stu-id="8caa9-200">All users and groups included in the **RoleDefinitions** field are automatically granted access to JEA endpoints.</span></span> <span data-ttu-id="8caa9-201">Regras de acesso condicional permitem-lhe refinar este acesso e exigir que os utilizadores pertencem a grupos de segurança adicionais que não tenham impacto sobre as funções para o qual foram atribuídos.</span><span class="sxs-lookup"><span data-stu-id="8caa9-201">Conditional access rules allow you to refine this access and require users to belong to additional security groups that don't impact the roles to which they're assigned.</span></span> <span data-ttu-id="8caa9-202">Isto é útil quando pretende integrar uma solução de gestão de acesso privilegiado just-in-time, a autenticação de smart card ou outra solução de autenticação multifator com JEA.</span><span class="sxs-lookup"><span data-stu-id="8caa9-202">This is useful when you want to integrate a just-in-time privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="8caa9-203">Regras de acesso condicional são definidas no campo RequiredGroups num arquivo de configuração de sessão.</span><span class="sxs-lookup"><span data-stu-id="8caa9-203">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="8caa9-204">Lá, pode fornecer uma tabela de hash (opcionalmente aninhada) que utiliza "E" e "Ou" chaves para construir as suas regras.</span><span class="sxs-lookup"><span data-stu-id="8caa9-204">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="8caa9-205">Aqui estão alguns exemplos de como utilizar este campo:</span><span class="sxs-lookup"><span data-stu-id="8caa9-205">Here are some examples of how to use this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> <span data-ttu-id="8caa9-206">Regras de acesso condicional só estão disponíveis no PowerShell 5.1 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="8caa9-206">Conditional access rules are only available in PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="8caa9-207">Outras propriedades</span><span class="sxs-lookup"><span data-stu-id="8caa9-207">Other properties</span></span>

<span data-ttu-id="8caa9-208">Ficheiros de configuração de sessão também podem fazer tudo o que um arquivo de recurso de função pode fazer, basta sem a capacidade de conceder o acesso de utilizadores ao ligar a comandos diferentes.</span><span class="sxs-lookup"><span data-stu-id="8caa9-208">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span> <span data-ttu-id="8caa9-209">Se quiser permitir aos utilizadores acesso a cmdlets específicos, funções ou os fornecedores, pode fazê-lo diretamente no ficheiro de configuração de sessão.</span><span class="sxs-lookup"><span data-stu-id="8caa9-209">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="8caa9-210">Para obter uma lista completa de propriedades suportadas no ficheiro de configuração de sessão, execute `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="8caa9-210">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="8caa9-211">Teste de um ficheiro de configuração de sessão</span><span class="sxs-lookup"><span data-stu-id="8caa9-211">Testing a session configuration file</span></span>

<span data-ttu-id="8caa9-212">Pode testar uma configuração de sessão através da [teste PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8caa9-212">You can test a session configuration using the [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span> <span data-ttu-id="8caa9-213">Recomenda-se que teste o seu ficheiro de configuração de sessão se tiver de ser editado manualmente o `.pssc` ficheiro.</span><span class="sxs-lookup"><span data-stu-id="8caa9-213">It's recommended that you test your session configuration file if you've manually edited the `.pssc` file.</span></span> <span data-ttu-id="8caa9-214">O teste assegura que a sintaxe está correta.</span><span class="sxs-lookup"><span data-stu-id="8caa9-214">Testing ensures the syntax is correct.</span></span> <span data-ttu-id="8caa9-215">Se um ficheiro de configuração de sessão falhar este teste, não é possível registar no sistema.</span><span class="sxs-lookup"><span data-stu-id="8caa9-215">If a session configuration file fails this test, it can't be registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="8caa9-216">Ficheiro de configuração de sessão de exemplo</span><span class="sxs-lookup"><span data-stu-id="8caa9-216">Sample session configuration file</span></span>

<span data-ttu-id="8caa9-217">O exemplo seguinte mostra como criar e validar uma configuração de sessão para JEA.</span><span class="sxs-lookup"><span data-stu-id="8caa9-217">The following example shows how to create and validate a session configuration for JEA.</span></span> <span data-ttu-id="8caa9-218">As definições de funções são criadas e armazenadas no `$roles` variável por conveniência e legibilidade.</span><span class="sxs-lookup"><span data-stu-id="8caa9-218">The role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span> <span data-ttu-id="8caa9-219">Não é um requisito para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="8caa9-219">It isn't a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="8caa9-220">A atualizar ficheiros de configuração de sessão</span><span class="sxs-lookup"><span data-stu-id="8caa9-220">Updating session configuration files</span></span>

<span data-ttu-id="8caa9-221">Para alterar as propriedades de uma configuração de sessão JEA, incluindo o mapeamento de utilizadores às funções, deve [anular o registo](register-jea.md#unregistering-jea-configurations).</span><span class="sxs-lookup"><span data-stu-id="8caa9-221">To change the properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations).</span></span> <span data-ttu-id="8caa9-222">Em seguida, [volte a registar](register-jea.md) a configuração de sessão JEA utilizando um ficheiro de configuração de sessão atualizadas.</span><span class="sxs-lookup"><span data-stu-id="8caa9-222">Then, [re-register](register-jea.md) the JEA session configuration using an updated session configuration file.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8caa9-223">Passos Seguintes</span><span class="sxs-lookup"><span data-stu-id="8caa9-223">Next steps</span></span>

- [<span data-ttu-id="8caa9-224">Registe-se de uma configuração de JEA</span><span class="sxs-lookup"><span data-stu-id="8caa9-224">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="8caa9-225">Funções JEA do autor</span><span class="sxs-lookup"><span data-stu-id="8caa9-225">Author JEA roles</span></span>](role-capabilities.md)
