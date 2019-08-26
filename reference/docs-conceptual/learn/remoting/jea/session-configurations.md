---
ms.date: 07/10/2019
keywords: Jea, PowerShell, segurança
title: Configurações de sessão JEA
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017882"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="ea045-103">Configurações de sessão JEA</span><span class="sxs-lookup"><span data-stu-id="ea045-103">JEA Session Configurations</span></span>

<span data-ttu-id="ea045-104">Um ponto de extremidade JEA é registrado em um sistema criando e registrando um arquivo de configuração de sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea045-104">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file.</span></span> <span data-ttu-id="ea045-105">As configurações de sessão definem quem pode usar o ponto de extremidade JEA e a quais funções elas têm acesso.</span><span class="sxs-lookup"><span data-stu-id="ea045-105">Session configurations define who can use the JEA endpoint and which roles they have access to.</span></span> <span data-ttu-id="ea045-106">Eles também definem as configurações globais que se aplicam a todos os usuários da sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="ea045-106">They also define global settings that apply to all users of the JEA session.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="ea045-107">Criar um arquivo de configuração de sessão</span><span class="sxs-lookup"><span data-stu-id="ea045-107">Create a session configuration file</span></span>

<span data-ttu-id="ea045-108">Para registrar um ponto de extremidade JEA, você deve especificar como esse ponto de extremidade é configurado.</span><span class="sxs-lookup"><span data-stu-id="ea045-108">To register a JEA endpoint, you must specify how that endpoint is configured.</span></span> <span data-ttu-id="ea045-109">Há muitas opções a serem consideradas.</span><span class="sxs-lookup"><span data-stu-id="ea045-109">There are many options to consider.</span></span> <span data-ttu-id="ea045-110">As opções mais importantes são:</span><span class="sxs-lookup"><span data-stu-id="ea045-110">The most important options are:</span></span>

- <span data-ttu-id="ea045-111">Quem tem acesso ao ponto de extremidade JEA</span><span class="sxs-lookup"><span data-stu-id="ea045-111">Who has access to the JEA endpoint</span></span>
- <span data-ttu-id="ea045-112">Quais funções eles são atribuídas</span><span class="sxs-lookup"><span data-stu-id="ea045-112">Which roles they be assigned</span></span>
- <span data-ttu-id="ea045-113">Qual identidade JEA usa nos bastidores</span><span class="sxs-lookup"><span data-stu-id="ea045-113">Which identity JEA uses under the covers</span></span>
- <span data-ttu-id="ea045-114">O nome do ponto de extremidade JEA</span><span class="sxs-lookup"><span data-stu-id="ea045-114">The name of the JEA endpoint</span></span>

<span data-ttu-id="ea045-115">Essas opções são definidas em um arquivo de dados do PowerShell `.pssc` com uma extensão conhecida como um arquivo de configuração de sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea045-115">These options are defined in a PowerShell data file with a `.pssc` extension known as a PowerShell session configuration file.</span></span> <span data-ttu-id="ea045-116">O arquivo de configuração de sessão pode ser editado usando qualquer editor de texto.</span><span class="sxs-lookup"><span data-stu-id="ea045-116">The session configuration file can be edited using any text editor.</span></span>

<span data-ttu-id="ea045-117">Execute o comando a seguir para criar um arquivo de configuração de modelo em branco.</span><span class="sxs-lookup"><span data-stu-id="ea045-117">Run the following command to create a blank template configuration file.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="ea045-118">Somente as opções de configuração mais comuns são incluídas no arquivo de modelo por padrão.</span><span class="sxs-lookup"><span data-stu-id="ea045-118">Only the most common configuration options are included in the template file by default.</span></span> <span data-ttu-id="ea045-119">Use a `-Full` opção para incluir todas as configurações aplicáveis no PSSC gerado.</span><span class="sxs-lookup"><span data-stu-id="ea045-119">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="ea045-120">O `-SessionType RestrictedRemoteServer` campo indica que a configuração de sessão é usada pelo Jea para gerenciamento seguro.</span><span class="sxs-lookup"><span data-stu-id="ea045-120">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration is used by JEA for secure management.</span></span> <span data-ttu-id="ea045-121">As sessões desse tipo operam no modo nolanguage e só têm acesso aos seguintes comandos padrão (e aliases):</span><span class="sxs-lookup"><span data-stu-id="ea045-121">Sessions of this type operate in **NoLanguage** mode and only have access to the following default commands (and aliases):</span></span>

- <span data-ttu-id="ea045-122">Clear – host (CLS, Clear)</span><span class="sxs-lookup"><span data-stu-id="ea045-122">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="ea045-123">Exit-PSSession (exsn, sair)</span><span class="sxs-lookup"><span data-stu-id="ea045-123">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="ea045-124">Get-Command (GCM)</span><span class="sxs-lookup"><span data-stu-id="ea045-124">Get-Command (gcm)</span></span>
- <span data-ttu-id="ea045-125">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="ea045-125">Get-FormatData</span></span>
- <span data-ttu-id="ea045-126">Obter ajuda</span><span class="sxs-lookup"><span data-stu-id="ea045-126">Get-Help</span></span>
- <span data-ttu-id="ea045-127">Measure-Object (medida)</span><span class="sxs-lookup"><span data-stu-id="ea045-127">Measure-Object (measure)</span></span>
- <span data-ttu-id="ea045-128">Out-padrão</span><span class="sxs-lookup"><span data-stu-id="ea045-128">Out-Default</span></span>
- <span data-ttu-id="ea045-129">Select-Object (selecionar)</span><span class="sxs-lookup"><span data-stu-id="ea045-129">Select-Object (select)</span></span>

<span data-ttu-id="ea045-130">Nenhum provedor do PowerShell está disponível, nem todos os programas externos (executáveis ou scripts).</span><span class="sxs-lookup"><span data-stu-id="ea045-130">No PowerShell providers are available, nor are any external programs (executables or scripts).</span></span>

<span data-ttu-id="ea045-131">Para obter mais informações sobre modos de linguagem, consulte [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span><span class="sxs-lookup"><span data-stu-id="ea045-131">For more information about language modes, see [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="ea045-132">Escolha a identidade JEA</span><span class="sxs-lookup"><span data-stu-id="ea045-132">Choose the JEA identity</span></span>

<span data-ttu-id="ea045-133">Nos bastidores, o JEA precisa de uma identidade (conta) para usar ao executar os comandos de um usuário conectado.</span><span class="sxs-lookup"><span data-stu-id="ea045-133">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="ea045-134">Você define qual identidade JEA usa no arquivo de configuração de sessão.</span><span class="sxs-lookup"><span data-stu-id="ea045-134">You define which identity JEA uses in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="ea045-135">Conta virtual local</span><span class="sxs-lookup"><span data-stu-id="ea045-135">Local Virtual Account</span></span>

<span data-ttu-id="ea045-136">As contas virtuais locais são úteis quando todas as funções definidas para o ponto de extremidade JEA são usadas para gerenciar o computador local e uma conta de administrador local é suficiente para executar os comandos com êxito.</span><span class="sxs-lookup"><span data-stu-id="ea045-136">Local virtual accounts are useful when all roles defined for the JEA endpoint are used to manage the local machine and a local administrator account is sufficient to run the commands successfully.</span></span>
<span data-ttu-id="ea045-137">As contas virtuais são contas temporárias que são exclusivas para um usuário específico e são apenas por último pela duração de sua sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea045-137">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span> <span data-ttu-id="ea045-138">Em um servidor membro ou estação de trabalho, as contas virtuais pertencem ao grupo **Administradores** do computador local.</span><span class="sxs-lookup"><span data-stu-id="ea045-138">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group.</span></span> <span data-ttu-id="ea045-139">Em um controlador de Domínio do Active Directory, as contas virtuais pertencem ao grupo **Admins** . do domínio do domínio.</span><span class="sxs-lookup"><span data-stu-id="ea045-139">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="ea045-140">Se as funções definidas pela configuração de sessão não exigirem privilégio administrativo completo, você poderá especificar os grupos de segurança aos quais a conta virtual pertencerá.</span><span class="sxs-lookup"><span data-stu-id="ea045-140">If the roles defined by the session configuration don't require full administrative privilege, you can specify the security groups to which the virtual account will belong.</span></span> <span data-ttu-id="ea045-141">Em um servidor membro ou estação de trabalho, os grupos de segurança especificados devem ser grupos locais, não grupos de um domínio.</span><span class="sxs-lookup"><span data-stu-id="ea045-141">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="ea045-142">Quando um ou mais grupos de segurança são especificados, a conta virtual não é atribuída ao grupo de administradores de domínio ou local.</span><span class="sxs-lookup"><span data-stu-id="ea045-142">When one or more security groups are specified, the virtual account isn't assigned to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="ea045-143">As contas virtuais recebem temporariamente o direito de logon como um serviço na política de segurança do servidor local.</span><span class="sxs-lookup"><span data-stu-id="ea045-143">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span> <span data-ttu-id="ea045-144">Se um dos VirtualAccountGroups especificado já tiver sido concedido a esse direito na política, a conta virtual individual não será mais adicionada e removida da política.</span><span class="sxs-lookup"><span data-stu-id="ea045-144">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span> <span data-ttu-id="ea045-145">Isso pode ser útil em cenários como controladores de domínio em que as revisões para a diretiva de segurança do controlador de domínio são rigorosamente auditadas.</span><span class="sxs-lookup"><span data-stu-id="ea045-145">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span> <span data-ttu-id="ea045-146">Isso só está disponível no Windows Server 2016 com o rollup de novembro de 2018 ou posterior e o Windows Server 2019 com o rollup de janeiro de 2019 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="ea045-146">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="ea045-147">Grupo-conta de serviço gerenciado</span><span class="sxs-lookup"><span data-stu-id="ea045-147">Group-managed service account</span></span>

<span data-ttu-id="ea045-148">Uma conta de serviço gerenciado por grupo (GMSA) é a identidade apropriada a ser usada quando os usuários do JEA precisam acessar recursos de rede, como compartilhamentos de arquivos e serviços Web.</span><span class="sxs-lookup"><span data-stu-id="ea045-148">A group-managed service account (GMSA) is the appropriate identity to use when JEA users need to access network resources such as file shares and web services.</span></span> <span data-ttu-id="ea045-149">GMSAs fornece uma identidade de domínio que é usada para autenticar com recursos em qualquer computador dentro do domínio.</span><span class="sxs-lookup"><span data-stu-id="ea045-149">GMSAs give you a domain identity that is used to authenticate with resources on any machine within the domain.</span></span> <span data-ttu-id="ea045-150">Os direitos que um GMSA fornece são determinados pelos recursos que você está acessando.</span><span class="sxs-lookup"><span data-stu-id="ea045-150">The rights that a GMSA provides are determined by the resources you're accessing.</span></span> <span data-ttu-id="ea045-151">Você não tem direitos de administrador em nenhum computador ou serviço, a menos que o administrador de computador ou serviço tenha concedido explicitamente esses direitos ao GMSA.</span><span class="sxs-lookup"><span data-stu-id="ea045-151">You don't have admin rights on any machines or services unless the machine or service administrator has explicitly granted those rights to the GMSA.</span></span>

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

<span data-ttu-id="ea045-152">GMSAs só deve ser usado quando necessário:</span><span class="sxs-lookup"><span data-stu-id="ea045-152">GMSAs should only be used when necessary:</span></span>

- <span data-ttu-id="ea045-153">É difícil rastrear ações de back para um usuário ao usar um GMSA.</span><span class="sxs-lookup"><span data-stu-id="ea045-153">It's difficult to trace back actions to a user when using a GMSA.</span></span> <span data-ttu-id="ea045-154">Cada usuário compartilha a mesma identidade de execução como.</span><span class="sxs-lookup"><span data-stu-id="ea045-154">Every user shares the same run-as identity.</span></span> <span data-ttu-id="ea045-155">Você deve examinar os logs e transcrições de sessão do PowerShell para correlacionar usuários individuais com suas ações.</span><span class="sxs-lookup"><span data-stu-id="ea045-155">You must review PowerShell session transcripts and logs to correlate individual users with their actions.</span></span>

- <span data-ttu-id="ea045-156">O GMSA pode ter acesso a vários recursos de rede aos quais o usuário que está se conectando não precisa acessar.</span><span class="sxs-lookup"><span data-stu-id="ea045-156">The GMSA may have access to many network resources that the connecting user doesn't need access to.</span></span> <span data-ttu-id="ea045-157">Sempre tente limitar as permissões efetivas em uma sessão JEA para seguir o princípio de privilégios mínimos.</span><span class="sxs-lookup"><span data-stu-id="ea045-157">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="ea045-158">Contas de serviço gerenciado de grupo só estão disponíveis em computadores ingressados no domínio usando o PowerShell 5,1 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="ea045-158">Group managed service accounts are only available on domain-joined machines using PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="ea045-159">Para obter mais informações sobre como proteger uma sessão do JEA, consulte o artigo [Considerações sobre segurança](security-considerations.md) .</span><span class="sxs-lookup"><span data-stu-id="ea045-159">For more information about securing a JEA session, see the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="ea045-160">Transcrições de sessão</span><span class="sxs-lookup"><span data-stu-id="ea045-160">Session transcripts</span></span>

<span data-ttu-id="ea045-161">É recomendável que você configure um ponto de extremidade JEA para registrar automaticamente transcrições de sessões de usuários.</span><span class="sxs-lookup"><span data-stu-id="ea045-161">It's recommended that you configure a JEA endpoint to automatically record transcripts of users' sessions.</span></span> <span data-ttu-id="ea045-162">As transcrições de sessão do PowerShell contêm informações sobre o usuário que está se conectando, a identidade executar como atribuída a eles e os comandos executados pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="ea045-162">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span> <span data-ttu-id="ea045-163">Eles podem ser úteis para uma equipe de auditoria que precisa entender quem fez uma alteração específica em um sistema.</span><span class="sxs-lookup"><span data-stu-id="ea045-163">They can be useful to an auditing team who needs to understand who made a specific change to a system.</span></span>

<span data-ttu-id="ea045-164">Para configurar a transcrição automática no arquivo de configuração de sessão, forneça um caminho para uma pasta onde as transcrições devem ser armazenadas.</span><span class="sxs-lookup"><span data-stu-id="ea045-164">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="ea045-165">As transcrições são gravadas na pasta pela conta do **sistema local** , o que exige acesso de leitura e gravação ao diretório.</span><span class="sxs-lookup"><span data-stu-id="ea045-165">Transcripts are written to the folder by the **Local System** account, which requires read and write access to the directory.</span></span> <span data-ttu-id="ea045-166">Os usuários padrão não devem ter acesso à pasta.</span><span class="sxs-lookup"><span data-stu-id="ea045-166">Standard users should have no access to the folder.</span></span> <span data-ttu-id="ea045-167">Limite o número de administradores de segurança que têm acesso para auditar as transcrições.</span><span class="sxs-lookup"><span data-stu-id="ea045-167">Limit the number of security administrators that have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="ea045-168">Unidade do usuário</span><span class="sxs-lookup"><span data-stu-id="ea045-168">User drive</span></span>

<span data-ttu-id="ea045-169">Se os usuários que estão se conectando precisarem copiar arquivos de ou para o ponto de extremidade JEA, você poderá habilitar a unidade de usuário no arquivo de configuração de sessão.</span><span class="sxs-lookup"><span data-stu-id="ea045-169">If your connecting users need to copy files to or from the JEA endpoint, you can enable the user drive in the session configuration file.</span></span> <span data-ttu-id="ea045-170">A unidade do usuário é uma **PSDrive** que é mapeada para uma pasta exclusiva para cada usuário que está se conectando.</span><span class="sxs-lookup"><span data-stu-id="ea045-170">The user drive is a **PSDrive** that is mapped to a unique folder for each connecting user.</span></span> <span data-ttu-id="ea045-171">Essa pasta permite que os usuários copiem arquivos de ou para o sistema sem conceder a eles acesso ao sistema de arquivos completo ou expondo o provedor FileSystem.</span><span class="sxs-lookup"><span data-stu-id="ea045-171">This folder allows users to copy files to or from the system without giving them access to the full file system or exposing the FileSystem provider.</span></span> <span data-ttu-id="ea045-172">O conteúdo da unidade do usuário é persistente entre as sessões para acomodar situações em que a conectividade de rede pode ser interrompida.</span><span class="sxs-lookup"><span data-stu-id="ea045-172">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="ea045-173">Por padrão, a unidade de usuário permite que você armazene um máximo de 50 MB de dados por usuário.</span><span class="sxs-lookup"><span data-stu-id="ea045-173">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span> <span data-ttu-id="ea045-174">Você pode limitar a quantidade de dados que um usuário pode consumir com o campo *UserDriveMaximumSize* .</span><span class="sxs-lookup"><span data-stu-id="ea045-174">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="ea045-175">Se não quiser que os dados na unidade de usuário sejam persistentes, você poderá configurar uma tarefa agendada no sistema para limpar automaticamente a pasta todas as noites.</span><span class="sxs-lookup"><span data-stu-id="ea045-175">If you don't want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="ea045-176">A unidade de usuário só está disponível no PowerShell 5,1 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="ea045-176">The user drive is only available in PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="ea045-177">Para obter mais informações sobre PSDrives, consulte [gerenciando unidades do PowerShell](/powershell/scripting/samples/managing-windows-powershell-drives).</span><span class="sxs-lookup"><span data-stu-id="ea045-177">For more information about PSDrives, see [Managing PowerShell drives](/powershell/scripting/samples/managing-windows-powershell-drives).</span></span>

### <a name="role-definitions"></a><span data-ttu-id="ea045-178">Definições de função</span><span class="sxs-lookup"><span data-stu-id="ea045-178">Role definitions</span></span>

<span data-ttu-id="ea045-179">As definições de função em um arquivo de configuração de sessão definem o mapeamento de **usuários** para **funções**.</span><span class="sxs-lookup"><span data-stu-id="ea045-179">Role definitions in a session configuration file define the mapping of **users** to **roles**.</span></span> <span data-ttu-id="ea045-180">Cada usuário ou grupo incluído nesse campo recebe permissão para o ponto de extremidade JEA quando registrado.</span><span class="sxs-lookup"><span data-stu-id="ea045-180">Every user or group included in this field is granted permission to the JEA endpoint when it's registered.</span></span>
<span data-ttu-id="ea045-181">Cada usuário ou grupo pode ser incluído como uma chave na tabela de hash apenas uma vez, mas pode ser atribuído a várias funções.</span><span class="sxs-lookup"><span data-stu-id="ea045-181">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span> <span data-ttu-id="ea045-182">O nome da capacidade de função deve ser o nome do arquivo de capacidade de função, sem `.psrc` a extensão.</span><span class="sxs-lookup"><span data-stu-id="ea045-182">The name of the role capability should be the name of the role capability file, without the `.psrc` extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="ea045-183">Se um usuário pertencer a mais de um grupo na definição de função, ele obterá acesso às funções de cada um.</span><span class="sxs-lookup"><span data-stu-id="ea045-183">If a user belongs to more than one group in the role definition, they get access to the roles of each.</span></span> <span data-ttu-id="ea045-184">Quando duas funções concedem acesso aos mesmos cmdlets, o conjunto de parâmetros mais permissivos é concedido ao usuário.</span><span class="sxs-lookup"><span data-stu-id="ea045-184">When two roles grant access to the same cmdlets, the most permissive parameter set is granted to the user.</span></span>

<span data-ttu-id="ea045-185">Ao especificar usuários ou grupos locais no campo definições de função, certifique-se de usar o nome do computador, não **localhost** ou curingas.</span><span class="sxs-lookup"><span data-stu-id="ea045-185">When specifying local users or groups in the role definitions field, be sure to use the computer name, not **localhost** or wildcards.</span></span> <span data-ttu-id="ea045-186">Você pode verificar o nome do computador inspecionando a `$env:COMPUTERNAME` variável.</span><span class="sxs-lookup"><span data-stu-id="ea045-186">You can check the computer name by inspecting the `$env:COMPUTERNAME` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="ea045-187">Ordem de pesquisa de capacidade de função</span><span class="sxs-lookup"><span data-stu-id="ea045-187">Role capability search order</span></span>

<span data-ttu-id="ea045-188">Conforme mostrado no exemplo acima, os recursos de função são referenciados pelo nome base do arquivo de capacidade de função.</span><span class="sxs-lookup"><span data-stu-id="ea045-188">As shown in the example above, role capabilities are referenced by the base name of the role capability file.</span></span> <span data-ttu-id="ea045-189">O nome de base de um arquivo é o FileName sem a extensão.</span><span class="sxs-lookup"><span data-stu-id="ea045-189">The base name of a file is the filename without the extension.</span></span> <span data-ttu-id="ea045-190">Se houver vários recursos de função disponíveis no sistema com o mesmo nome, o PowerShell usará sua ordem de pesquisa implícita para selecionar o arquivo de capacidade de função efetivo.</span><span class="sxs-lookup"><span data-stu-id="ea045-190">If multiple role capabilities are available on the system with the same name, PowerShell uses its implicit search order to select the effective role capability file.</span></span> <span data-ttu-id="ea045-191">JEA **não** dá acesso a todos os arquivos de capacidade de função com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="ea045-191">JEA does **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="ea045-192">Jea usa a `$env:PSModulePath` variável de ambiente para determinar quais caminhos verificar para arquivos de capacidade de função.</span><span class="sxs-lookup"><span data-stu-id="ea045-192">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span> <span data-ttu-id="ea045-193">Dentro de cada um desses caminhos, JEA procura módulos válidos do PowerShell que contenham uma subpasta "RoleCapabilities".</span><span class="sxs-lookup"><span data-stu-id="ea045-193">Within each of those paths, JEA looks for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span> <span data-ttu-id="ea045-194">Assim como acontece com a importação de módulos, o JEA prefere recursos de função que são fornecidos com o Windows para recursos de função personalizados com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="ea045-194">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>

<span data-ttu-id="ea045-195">Para todos os outros conflitos de nomenclatura, a precedência é determinada pela ordem em que o Windows enumera os arquivos no diretório.</span><span class="sxs-lookup"><span data-stu-id="ea045-195">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory.</span></span> <span data-ttu-id="ea045-196">Não há garantia de que a ordem seja alfabética.</span><span class="sxs-lookup"><span data-stu-id="ea045-196">The order isn't guaranteed to be alphabetical.</span></span> <span data-ttu-id="ea045-197">O primeiro arquivo de capacidade de função encontrado que corresponde ao nome especificado é usado para o usuário que está se conectando.</span><span class="sxs-lookup"><span data-stu-id="ea045-197">The first role capability file found that matches the specified name is used for the connecting user.</span></span> <span data-ttu-id="ea045-198">Como a ordem de pesquisa de capacidade de função não é determinística, é **altamente recomendável** que os recursos de função tenham nomes de um único.</span><span class="sxs-lookup"><span data-stu-id="ea045-198">Since the role capability search order isn't deterministic, it's **strongly recommended** that role capabilities have unique filenames.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="ea045-199">Regras de acesso condicional</span><span class="sxs-lookup"><span data-stu-id="ea045-199">Conditional access rules</span></span>

<span data-ttu-id="ea045-200">Todos os usuários e grupos incluídos no campo **RoleDefinitions** recebem acesso automaticamente aos pontos de extremidade Jea.</span><span class="sxs-lookup"><span data-stu-id="ea045-200">All users and groups included in the **RoleDefinitions** field are automatically granted access to JEA endpoints.</span></span> <span data-ttu-id="ea045-201">As regras de acesso condicional permitem que você refine esse acesso e exija que os usuários pertençam a grupos de segurança adicionais que não afetam as funções às quais estão atribuídos.</span><span class="sxs-lookup"><span data-stu-id="ea045-201">Conditional access rules allow you to refine this access and require users to belong to additional security groups that don't impact the roles to which they're assigned.</span></span> <span data-ttu-id="ea045-202">Isso é útil quando você deseja integrar uma solução de gerenciamento de acesso privilegiado just-in-time, autenticação de cartão inteligente ou outra solução de autenticação multifator com JEA.</span><span class="sxs-lookup"><span data-stu-id="ea045-202">This is useful when you want to integrate a just-in-time privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="ea045-203">As regras de acesso condicional são definidas no campo RequiredGroups em um arquivo de configuração de sessão.</span><span class="sxs-lookup"><span data-stu-id="ea045-203">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="ea045-204">Lá, você pode fornecer uma tabela de hash (opcionalmente aninhada) que usa as chaves ' and ' e ' or ' para construir suas regras.</span><span class="sxs-lookup"><span data-stu-id="ea045-204">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="ea045-205">Aqui estão alguns exemplos de como usar este campo:</span><span class="sxs-lookup"><span data-stu-id="ea045-205">Here are some examples of how to use this field:</span></span>

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
> <span data-ttu-id="ea045-206">As regras de acesso condicional estão disponíveis somente no PowerShell 5,1 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="ea045-206">Conditional access rules are only available in PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="ea045-207">Outras propriedades</span><span class="sxs-lookup"><span data-stu-id="ea045-207">Other properties</span></span>

<span data-ttu-id="ea045-208">Os arquivos de configuração de sessão também podem fazer tudo o que um arquivo de capacidade de função pode fazer, apenas sem a capacidade de conceder acesso aos usuários a comandos diferentes.</span><span class="sxs-lookup"><span data-stu-id="ea045-208">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span> <span data-ttu-id="ea045-209">Se você quiser permitir que todos os usuários acessem cmdlets, funções ou provedores específicos, você pode fazer isso diretamente no arquivo de configuração de sessão.</span><span class="sxs-lookup"><span data-stu-id="ea045-209">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="ea045-210">Para obter uma lista completa das propriedades com suporte no arquivo de configuração de `Get-Help New-PSSessionConfigurationFile -Full`sessão, execute.</span><span class="sxs-lookup"><span data-stu-id="ea045-210">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="ea045-211">Testando um arquivo de configuração de sessão</span><span class="sxs-lookup"><span data-stu-id="ea045-211">Testing a session configuration file</span></span>

<span data-ttu-id="ea045-212">Você pode testar uma configuração de sessão usando o cmdlet [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) .</span><span class="sxs-lookup"><span data-stu-id="ea045-212">You can test a session configuration using the [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span> <span data-ttu-id="ea045-213">É recomendável que você teste seu arquivo de configuração de sessão se tiver editado `.pssc` manualmente o arquivo.</span><span class="sxs-lookup"><span data-stu-id="ea045-213">It's recommended that you test your session configuration file if you've manually edited the `.pssc` file.</span></span> <span data-ttu-id="ea045-214">O teste garante que a sintaxe esteja correta.</span><span class="sxs-lookup"><span data-stu-id="ea045-214">Testing ensures the syntax is correct.</span></span> <span data-ttu-id="ea045-215">Se um arquivo de configuração de sessão falhar nesse teste, ele não poderá ser registrado no sistema.</span><span class="sxs-lookup"><span data-stu-id="ea045-215">If a session configuration file fails this test, it can't be registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="ea045-216">Arquivo de configuração de sessão de exemplo</span><span class="sxs-lookup"><span data-stu-id="ea045-216">Sample session configuration file</span></span>

<span data-ttu-id="ea045-217">O exemplo a seguir mostra como criar e validar uma configuração de sessão para JEA.</span><span class="sxs-lookup"><span data-stu-id="ea045-217">The following example shows how to create and validate a session configuration for JEA.</span></span> <span data-ttu-id="ea045-218">As definições de função são criadas e armazenadas na `$roles` variável para conveniência e legibilidade.</span><span class="sxs-lookup"><span data-stu-id="ea045-218">The role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span> <span data-ttu-id="ea045-219">Não é um requisito para isso.</span><span class="sxs-lookup"><span data-stu-id="ea045-219">It isn't a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="ea045-220">Atualizando arquivos de configuração de sessão</span><span class="sxs-lookup"><span data-stu-id="ea045-220">Updating session configuration files</span></span>

<span data-ttu-id="ea045-221">Para alterar as propriedades de uma configuração de sessão JEA, incluindo o mapeamento de usuários para funções, você deve [cancelar o registro](register-jea.md#unregistering-jea-configurations).</span><span class="sxs-lookup"><span data-stu-id="ea045-221">To change the properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations).</span></span> <span data-ttu-id="ea045-222">Em seguida, [Registre novamente](register-jea.md) a configuração de sessão Jea usando um arquivo de configuração de sessão atualizado.</span><span class="sxs-lookup"><span data-stu-id="ea045-222">Then, [re-register](register-jea.md) the JEA session configuration using an updated session configuration file.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ea045-223">Passos Seguintes</span><span class="sxs-lookup"><span data-stu-id="ea045-223">Next steps</span></span>

- [<span data-ttu-id="ea045-224">Registrar uma configuração do JEA</span><span class="sxs-lookup"><span data-stu-id="ea045-224">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="ea045-225">Criar funções JEA</span><span class="sxs-lookup"><span data-stu-id="ea045-225">Author JEA roles</span></span>](role-capabilities.md)
