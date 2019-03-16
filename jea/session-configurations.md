---
ms.date: 06/12/2017
keywords: jea, powershell, segurança
title: Configurações de sessão JEA
ms.openlocfilehash: b98726ea7ed3aabdfd05034c3b70118e327160cd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056602"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="b3f06-103">Configurações de sessão JEA</span><span class="sxs-lookup"><span data-stu-id="b3f06-103">JEA Session Configurations</span></span>

> <span data-ttu-id="b3f06-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b3f06-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="b3f06-105">Um ponto final JEA está registado num sistema ao criar e registar um ficheiro de configuração de sessão do PowerShell de uma forma específica.</span><span class="sxs-lookup"><span data-stu-id="b3f06-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file in a specific way.</span></span>
<span data-ttu-id="b3f06-106">Determinam as configurações de sessão *quem* pode utilizar o ponto final da JEA e quais funções elas têm acesso a.</span><span class="sxs-lookup"><span data-stu-id="b3f06-106">Session configurations determine *who* can use the JEA endpoint, and which role(s) they will have access to.</span></span>
<span data-ttu-id="b3f06-107">Elas também definem as definições globais que se aplicam aos utilizadores de qualquer função na sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="b3f06-107">They also define global settings that apply to users of any role in the JEA session.</span></span>

<span data-ttu-id="b3f06-108">Este tópico descreve como criar um ficheiro de configuração de sessão do PowerShell e registar um ponto final JEA.</span><span class="sxs-lookup"><span data-stu-id="b3f06-108">This topic describes how to create a PowerShell session configuration file and register a JEA endpoint.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="b3f06-109">Criar um ficheiro de configuração de sessão</span><span class="sxs-lookup"><span data-stu-id="b3f06-109">Create a session configuration file</span></span>

<span data-ttu-id="b3f06-110">Para registar um ponto final JEA, terá de especificar a forma como ponto de extremidade deve ser configurado.</span><span class="sxs-lookup"><span data-stu-id="b3f06-110">In order to register a JEA endpoint, you need to specify how that endpoint should be configured.</span></span>
<span data-ttu-id="b3f06-111">Existem muitas opções a serem considerados aqui, o mais importante dos quais sendo que devem ter acesso ao ponto final JEA, quais funções vão ser atribuído, que identidade JEA utilizará nos bastidores, e o que vai ser o nome do ponto final JEA.</span><span class="sxs-lookup"><span data-stu-id="b3f06-111">There are many options to consider here, the most important of which being who should have access to the JEA endpoint, which roles will they be assigned, which identity will JEA use under the covers, and what will be the name of the JEA endpoint.</span></span>
<span data-ttu-id="b3f06-112">Eles estão todos definidos num arquivo de configuração de sessão do PowerShell, que é um ficheiro de dados do PowerShell que termina com uma extensão de .pssc.</span><span class="sxs-lookup"><span data-stu-id="b3f06-112">These are all defined in a PowerShell session configuration file, which is a PowerShell data file ending with a .pssc extension.</span></span>

<span data-ttu-id="b3f06-113">Para criar um ficheiro de configuração de sessão de esqueleto para pontos finais JEA, execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="b3f06-113">To create a skeleton session configuration file for JEA endpoints, run the following command.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="b3f06-114">Apenas as opções de configuração mais comuns estão incluídas no ficheiro de esqueleto por predefinição.</span><span class="sxs-lookup"><span data-stu-id="b3f06-114">Only the most common configuration options are included in the skeleton file by default.</span></span>
> <span data-ttu-id="b3f06-115">Utilize o `-Full` comutador para incluir todas as configurações aplicáveis no PSSC gerado.</span><span class="sxs-lookup"><span data-stu-id="b3f06-115">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="b3f06-116">É possível abrir o ficheiro de configuração de sessão em qualquer editor de texto.</span><span class="sxs-lookup"><span data-stu-id="b3f06-116">You can open the session configuration file in any text editor.</span></span>
<span data-ttu-id="b3f06-117">O `-SessionType RestrictedRemoteServer` campo indica que a configuração de sessão será utilizada pelo JEA para a gestão segura.</span><span class="sxs-lookup"><span data-stu-id="b3f06-117">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration will be used by JEA for secure management.</span></span>
<span data-ttu-id="b3f06-118">Sessões configurado dessa forma funcionarão [NoLanguage modo](https://technet.microsoft.com/library/dn433292.aspx) e só ter os seguintes comandos de predefinição de 8 (e aliases) disponível:</span><span class="sxs-lookup"><span data-stu-id="b3f06-118">Sessions configured this way will operate in [NoLanguage mode](https://technet.microsoft.com/library/dn433292.aspx) and only have the following 8 default commands (and aliases) available:</span></span>

- <span data-ttu-id="b3f06-119">Clear-Host (cls, claro)</span><span class="sxs-lookup"><span data-stu-id="b3f06-119">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="b3f06-120">Exit-PSSession (exsn, exit)</span><span class="sxs-lookup"><span data-stu-id="b3f06-120">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="b3f06-121">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="b3f06-121">Get-Command (gcm)</span></span>
- <span data-ttu-id="b3f06-122">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="b3f06-122">Get-FormatData</span></span>
- <span data-ttu-id="b3f06-123">Get-Help</span><span class="sxs-lookup"><span data-stu-id="b3f06-123">Get-Help</span></span>
- <span data-ttu-id="b3f06-124">Objeto de medida (medidas)</span><span class="sxs-lookup"><span data-stu-id="b3f06-124">Measure-Object (measure)</span></span>
- <span data-ttu-id="b3f06-125">Out-Default</span><span class="sxs-lookup"><span data-stu-id="b3f06-125">Out-Default</span></span>
- <span data-ttu-id="b3f06-126">Select-Object (selecionar)</span><span class="sxs-lookup"><span data-stu-id="b3f06-126">Select-Object (select)</span></span>

<span data-ttu-id="b3f06-127">Não existem fornecedores de PowerShell estão disponíveis, nem são que programas de qualquer externo (executáveis, scripts, etc.).</span><span class="sxs-lookup"><span data-stu-id="b3f06-127">No PowerShell providers are available, nor are any external programs (executables, scripts, etc.).</span></span>

<span data-ttu-id="b3f06-128">Existem vários outros campos que pretende configurar para a sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="b3f06-128">There are several other fields you will want to configure for the JEA session.</span></span>
<span data-ttu-id="b3f06-129">Eles são abordados nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="b3f06-129">They are covered in the following sections.</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="b3f06-130">Escolha a identidade JEA</span><span class="sxs-lookup"><span data-stu-id="b3f06-130">Choose the JEA identity</span></span>

<span data-ttu-id="b3f06-131">Em segundo plano, JEA tem uma identidade (conta) para utilizar durante a execução de comandos de um usuário conectado.</span><span class="sxs-lookup"><span data-stu-id="b3f06-131">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="b3f06-132">Decide que identidade JEA irá utilizar no ficheiro de configuração de sessão.</span><span class="sxs-lookup"><span data-stu-id="b3f06-132">You decide which identity JEA will use in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="b3f06-133">Conta Virtual local</span><span class="sxs-lookup"><span data-stu-id="b3f06-133">Local Virtual Account</span></span>

<span data-ttu-id="b3f06-134">Se as funções suportadas por este ponto final da JEA são utilizadas para gerir a máquina local e uma conta de administrador local é suficiente para executar os comandos com êxito, deve configurar JEA para utilizar uma conta virtual local.</span><span class="sxs-lookup"><span data-stu-id="b3f06-134">If the roles supported by this JEA endpoint are all used to manage the local machine, and a local administrator account is sufficient to run the commands successfully, you should configure JEA to use a local virtual account.</span></span>
<span data-ttu-id="b3f06-135">Contas virtuais são contas temporárias que são exclusivas para um utilizador específico e apenas os últimos durante a sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3f06-135">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span>
<span data-ttu-id="b3f06-136">Num servidor membro ou estação de trabalho, contas virtuais pertencem ao computador local **administradores** agrupar e ter acesso a maioria dos recursos do sistema.</span><span class="sxs-lookup"><span data-stu-id="b3f06-136">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group, and have access to most system resources.</span></span>
<span data-ttu-id="b3f06-137">Num controlador de domínio do Active Directory, contas virtuais pertencem ao domínio **Admins do domínio** grupo.</span><span class="sxs-lookup"><span data-stu-id="b3f06-137">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="b3f06-138">Se as funções com suporte a configuração de sessão não necessitar desses privilégios amplo, opcionalmente, pode especificar os grupos de segurança para o qual irá pertencer a conta virtual.</span><span class="sxs-lookup"><span data-stu-id="b3f06-138">If the roles supported by the session configuration do not require such broad privileges, you can optionally specify the security groups to which the virtual account will belong.</span></span>
<span data-ttu-id="b3f06-139">Num servidor membro ou estação de trabalho, os grupos de segurança especificado tem de ser grupos locais, não os grupos de um domínio.</span><span class="sxs-lookup"><span data-stu-id="b3f06-139">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="b3f06-140">Quando é especificado um ou mais grupos de segurança, a conta virtual já não irão pertencer ao grupo de administradores locais ou de domínio.</span><span class="sxs-lookup"><span data-stu-id="b3f06-140">When one or more security groups is specified, the virtual account will no longer belong to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="b3f06-141">Contas virtuais recebem temporariamente o início de sessão como um direito de serviço na política de segurança de servidor local.</span><span class="sxs-lookup"><span data-stu-id="b3f06-141">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span>  <span data-ttu-id="b3f06-142">Se um dos VirtualAccountGroups especificado já foi concedido este direito na política, a conta virtual individual já não será adicionada e removida da política.</span><span class="sxs-lookup"><span data-stu-id="b3f06-142">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span>  <span data-ttu-id="b3f06-143">Isso pode ser útil em cenários como controladores de domínio em que a revisões para a política de segurança do controlador de domínio de perto são auditados.</span><span class="sxs-lookup"><span data-stu-id="b3f06-143">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span>  <span data-ttu-id="b3f06-144">Isso só está disponível no Windows Server 2016 com a Novembro de 2018 ou rollup posterior e Windows Server 2019 com o de 2019 de Janeiro ou rollup posterior.</span><span class="sxs-lookup"><span data-stu-id="b3f06-144">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="b3f06-145">Conta de Serviço Gerida de Grupo</span><span class="sxs-lookup"><span data-stu-id="b3f06-145">Group Managed Service Account</span></span>


<span data-ttu-id="b3f06-146">Para cenários de exigir que o utilizador JEA para aceder aos recursos de rede, tais como outras máquinas ou serviços da web, uma conta de serviço geridas de grupo (gMSA) é uma identidade mais adequada para utilizar.</span><span class="sxs-lookup"><span data-stu-id="b3f06-146">For scenarios requiring the JEA user to access network resources such as other machines or web services, a group managed service account (gMSA) is a more appropriate identity to use.</span></span>
<span data-ttu-id="b3f06-147">contas de gMSA dão-lhe uma identidade de domínio que pode ser utilizada para autenticar em recursos em qualquer computador no domínio.</span><span class="sxs-lookup"><span data-stu-id="b3f06-147">gMSA accounts give you a domain identity which can be used to authenticate against resources on any machine within the domain.</span></span>
<span data-ttu-id="b3f06-148">Os direitos a oferece de conta gMSA é determinado pelos recursos que está a aceder.</span><span class="sxs-lookup"><span data-stu-id="b3f06-148">The rights the gMSA account gives you is determined by the resources you are accessing.</span></span>
<span data-ttu-id="b3f06-149">Não terão automaticamente os direitos de administrador em qualquer máquinas ou serviços, a menos que o administrador de serviço/machine concedeu explicitamente a conta gMSA privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="b3f06-149">You will not automatically have admin rights on any machines or services unless the machine/service administrator has explicitly granted the gMSA account admin privileges.</span></span>

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

<span data-ttu-id="b3f06-150">contas de gMSA só devem ser utilizadas quando o acesso a recursos de rede são necessários para alguns dos motivos:</span><span class="sxs-lookup"><span data-stu-id="b3f06-150">gMSA accounts should only be used when access to network resources are required for a few reasons:</span></span>

- <span data-ttu-id="b3f06-151">É mais difícil de efectuar o rastreio ações para um utilizador ao utilizar uma conta gMSA, uma vez que cada usuário compartilha a mesma identidade Run.</span><span class="sxs-lookup"><span data-stu-id="b3f06-151">It is harder to trace back actions to a user when using a gMSA account since every user shares the same run-as identity.</span></span> <span data-ttu-id="b3f06-152">Precisará consultar transcrições de sessão do PowerShell e registos para correlacionar os utilizadores com as suas ações.</span><span class="sxs-lookup"><span data-stu-id="b3f06-152">You will need to consult PowerShell session transcripts and logs to correlate users with their actions.</span></span>

- <span data-ttu-id="b3f06-153">A conta gMSA pode ter acesso a vários recursos de rede que o usuário conectado não precisam de acesso a.</span><span class="sxs-lookup"><span data-stu-id="b3f06-153">The gMSA account may have access to many network resources which the connecting user does not need access to.</span></span> <span data-ttu-id="b3f06-154">Sempre tente limitar as permissões efetivas numa sessão JEA para acompanhar o princípio de privilégio mínimo.</span><span class="sxs-lookup"><span data-stu-id="b3f06-154">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="b3f06-155">Contas de serviço geridas de grupo só estão disponíveis no Windows PowerShell 5.1 ou mais recente e em computadores associados a um domínio.</span><span class="sxs-lookup"><span data-stu-id="b3f06-155">Group managed service accounts are only available in Windows PowerShell 5.1 or newer and on domain-joined machines.</span></span>

#### <a name="more-information-about-run-as-users"></a><span data-ttu-id="b3f06-156">Obter mais informações sobre a execução como usuários</span><span class="sxs-lookup"><span data-stu-id="b3f06-156">More information about run as users</span></span>

<span data-ttu-id="b3f06-157">Pode encontrar informações adicionais sobre a execução como identidades e como eles fatorar em segurança de uma sessão JEA no [considerações de segurança](security-considerations.md) artigo.</span><span class="sxs-lookup"><span data-stu-id="b3f06-157">Additional information about run as identities and how they factor into the security of a JEA session can be found in the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="b3f06-158">Transcrições de sessão</span><span class="sxs-lookup"><span data-stu-id="b3f06-158">Session transcripts</span></span>

<span data-ttu-id="b3f06-159">Recomenda-se que configure um ficheiro de configuração de sessão JEA para transcrições automaticamente registos de sessões dos utilizadores.</span><span class="sxs-lookup"><span data-stu-id="b3f06-159">It is recommended that you configure a JEA session configuration file to automatically record transcripts of users' sessions.</span></span>
<span data-ttu-id="b3f06-160">Transcrições de sessão do PowerShell contêm informações sobre o usuário conectado, a execução como identidade atribuída, e os comandos são executados pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="b3f06-160">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span>
<span data-ttu-id="b3f06-161">Eles podem ser úteis para uma equipe de auditoria que precisa entender quem efetuou uma alteração específica para um sistema.</span><span class="sxs-lookup"><span data-stu-id="b3f06-161">They can be useful to an auditing team who needs to understand who performed a specific change to a system.</span></span>

<span data-ttu-id="b3f06-162">Para configurar a transcrição automática no ficheiro de configuração de sessão, forneça um caminho para uma pasta onde as transcrições devem ser armazenadas.</span><span class="sxs-lookup"><span data-stu-id="b3f06-162">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="b3f06-163">A pasta especificada deve ser configurada para impedir que os usuários modifiquem ou eliminem dados na mesma.</span><span class="sxs-lookup"><span data-stu-id="b3f06-163">The specified folder should be configured to prevent users from modifying or deleting any data in it.</span></span>
<span data-ttu-id="b3f06-164">Transcrições são escritas para a pasta por conta do sistema Local, o que requer a leitura e de acesso de escrita para o diretório.</span><span class="sxs-lookup"><span data-stu-id="b3f06-164">Transcripts are written to the folder by the Local System account, which requires read and write access to the directory.</span></span>
<span data-ttu-id="b3f06-165">Os usuários padrão não devem ter acesso à pasta e um conjunto limitado de administradores de segurança deve ter acesso ao auditar as transcrições.</span><span class="sxs-lookup"><span data-stu-id="b3f06-165">Standard users should have no access to the folder, and a limited set of security administrators should have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="b3f06-166">Unidade de utilizador</span><span class="sxs-lookup"><span data-stu-id="b3f06-166">User drive</span></span>

<span data-ttu-id="b3f06-167">Se os utilizadores de ligação terá de copiar ficheiros de/para o ponto final da JEA para executar um comando, pode ativar a unidade de utilizador no ficheiro de configuração de sessão.</span><span class="sxs-lookup"><span data-stu-id="b3f06-167">If your connecting users will need to copy files to/from the JEA endpoint in order to run a command, you can enable the user drive in the session configuration file.</span></span>
<span data-ttu-id="b3f06-168">A unidade de utilizador é um [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) que está mapeado para uma pasta exclusiva para cada usuário conectado.</span><span class="sxs-lookup"><span data-stu-id="b3f06-168">The user drive is a [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) that is mapped to a unique folder for each connecting user.</span></span>
<span data-ttu-id="b3f06-169">Esta pasta serve como um espaço para os mesmos copiar ficheiros de/para o sistema, sem conceder acesso ao sistema de ficheiros completa ou expor o fornecedor do sistema de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="b3f06-169">This folder serves as a space for them to copy files to/from the system, without giving them access to the full file system or exposing the FileSystem provider.</span></span>
<span data-ttu-id="b3f06-170">O conteúdo da unidade de utilizador é persistente entre sessões para acomodar as situações em que a conectividade de rede pode ser interrompida.</span><span class="sxs-lookup"><span data-stu-id="b3f06-170">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="b3f06-171">Por predefinição, a unidade de utilizador permite-lhe armazenar um máximo de 50MB de dados por utilizador.</span><span class="sxs-lookup"><span data-stu-id="b3f06-171">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span>
<span data-ttu-id="b3f06-172">Pode limitar a quantidade de dados de um utilizador pode consumir com o *UserDriveMaximumSize* campo.</span><span class="sxs-lookup"><span data-stu-id="b3f06-172">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="b3f06-173">Se não pretender que os dados na unidade do utilizador para ser persistente, pode configurar uma tarefa agendada no sistema para limpar automaticamente a pasta de todas as noites.</span><span class="sxs-lookup"><span data-stu-id="b3f06-173">If you do not want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="b3f06-174">A unidade de utilizador só está disponível no Windows PowerShell 5.1 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="b3f06-174">The user drive is only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="role-definitions"></a><span data-ttu-id="b3f06-175">Definições de funções</span><span class="sxs-lookup"><span data-stu-id="b3f06-175">Role definitions</span></span>

<span data-ttu-id="b3f06-176">Definições de funções num arquivo de configuração de sessão definem o mapeamento dos *usuários* ao *funções*.</span><span class="sxs-lookup"><span data-stu-id="b3f06-176">Role definitions in a session configuration file define the mapping of *users* to *roles*.</span></span>
<span data-ttu-id="b3f06-177">Cada utilizador ou grupo incluído neste campo receberá automaticamente permissão para o ponto final da JEA quando é registado.</span><span class="sxs-lookup"><span data-stu-id="b3f06-177">Every user or group included in this field will automatically be granted permission to the JEA endpoint when it is registered.</span></span>
<span data-ttu-id="b3f06-178">Cada utilizador ou grupo pode ser incluído como uma chave da tabela de hash apenas uma vez, mas pode ser atribuído várias funções.</span><span class="sxs-lookup"><span data-stu-id="b3f06-178">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span>
<span data-ttu-id="b3f06-179">O nome da capacidade de função deve ser o nome do arquivo de recurso de função, sem a extensão de .psrc.</span><span class="sxs-lookup"><span data-stu-id="b3f06-179">The name of the role capability should be the name of the role capability file, without the .psrc extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="b3f06-180">Se um utilizador pertencer a mais de um grupo na definição de função, obterá acesso às funções de cada.</span><span class="sxs-lookup"><span data-stu-id="b3f06-180">If a user belongs to more than one group in the role definition, they will get access to the roles of each.</span></span>
<span data-ttu-id="b3f06-181">Se duas funções de concedem acesso para os mesmos cmdlets, o conjunto de parâmetros mais permissivo será concedido ao utilizador.</span><span class="sxs-lookup"><span data-stu-id="b3f06-181">If two roles grant access to the same cmdlets, the most permissive parameter set will be granted to the user.</span></span>

<span data-ttu-id="b3f06-182">Ao especificar grupos de utilizadores ou no campo de definições de função, certifique-se de que utiliza o nome do computador (não *localhost* ou *.*) antes da barra invertida.</span><span class="sxs-lookup"><span data-stu-id="b3f06-182">When specifying local users or groups in the role definitions field, be sure to use the computer name (not *localhost* or *.*) before the backslash.</span></span>
<span data-ttu-id="b3f06-183">Pode verificar o nome do computador ao inspecionar o `$env:computername` variável.</span><span class="sxs-lookup"><span data-stu-id="b3f06-183">You can check the computer name by inspecting the `$env:computername` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="b3f06-184">Ordem de pesquisa de capacidade de função</span><span class="sxs-lookup"><span data-stu-id="b3f06-184">Role capability search order</span></span>

<span data-ttu-id="b3f06-185">Conforme mostrado no exemplo acima, as funcionalidades de função são referenciadas pelo nome simples (nome de ficheiro sem a extensão) do arquivo de recurso de função.</span><span class="sxs-lookup"><span data-stu-id="b3f06-185">As shown in the example above, role capabilities are referenced by the flat name (filename without the extension) of the role capability file.</span></span>
<span data-ttu-id="b3f06-186">Se várias funcionalidades de função estão disponíveis no sistema com o mesmo nome simples, o PowerShell irá utilizar sua ordem de pesquisa implícito para selecionar o ficheiro de recurso de função em vigor.</span><span class="sxs-lookup"><span data-stu-id="b3f06-186">If multiple role capabilities are available on the system with the same flat name, PowerShell will use its implicit search order to select the effective role capability file.</span></span>
<span data-ttu-id="b3f06-187">Ele será **não** conceder acesso a todos os ficheiros de recurso de função com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="b3f06-187">It will **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="b3f06-188">JEA utiliza o `$env:PSModulePath` variável de ambiente para determinar os caminhos para verificar a existência de arquivos de recurso de função.</span><span class="sxs-lookup"><span data-stu-id="b3f06-188">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span>
<span data-ttu-id="b3f06-189">Dentro de cada um desses caminhos, JEA irá procurar válidos módulos do PowerShell que contêm uma subpasta do "RoleCapabilities".</span><span class="sxs-lookup"><span data-stu-id="b3f06-189">Within each of those paths, JEA will look for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span>
<span data-ttu-id="b3f06-190">Tal como acontece com a importação de módulos JEA prefere funcionalidades de função que são fornecidas com o Windows às capacidades de função personalizada com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="b3f06-190">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>
<span data-ttu-id="b3f06-191">Para todos os outros conflitos de nomenclatura, a precedência é determinada pela ordem em que o Windows enumera os ficheiros no diretório (não garantida que ser por ordem alfabética).</span><span class="sxs-lookup"><span data-stu-id="b3f06-191">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory (not guaranteed to be alphabetically).</span></span>
<span data-ttu-id="b3f06-192">O primeiro arquivo de recurso de função encontrado que corresponda ao desejada nome será utilizado para o usuário conectado.</span><span class="sxs-lookup"><span data-stu-id="b3f06-192">The first role capability file found that matches the desired name will be used for the connecting user.</span></span>

<span data-ttu-id="b3f06-193">Uma vez que a ordem de pesquisa de capacidade de função não é determinística quando dois ou mais funcionalidades de função partilham o mesmo nome, é **vivamente recomendado** que é garantir que os recursos de função têm nomes exclusivos no seu computador.</span><span class="sxs-lookup"><span data-stu-id="b3f06-193">Since the role capability search order is not deterministic when two or more role capabilities share the same name, it is **strongly recommended** that you ensure role capabilities have unique names on your machine.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="b3f06-194">Regras de acesso condicional</span><span class="sxs-lookup"><span data-stu-id="b3f06-194">Conditional access rules</span></span>

<span data-ttu-id="b3f06-195">Todos os utilizadores e grupos incluídos no campo RoleDefinitions recebem automaticamente acesso a pontos finais JEA.</span><span class="sxs-lookup"><span data-stu-id="b3f06-195">All users and groups included in the RoleDefinitions field are automatically granted access to JEA endpoints.</span></span>
<span data-ttu-id="b3f06-196">Regras de acesso condicional permitem-lhe refinar este acesso e exigir que os utilizadores pertencem a grupos de segurança adicionais que não afetam as funções que estão atribuídos.</span><span class="sxs-lookup"><span data-stu-id="b3f06-196">Conditional access rules allow you to refine this access and require users to belong to additional security groups which do not impact the roles which they are assigned.</span></span>
<span data-ttu-id="b3f06-197">Isso pode ser útil se pretender integrar um "apenas no tempo" privilegiado aceder a solução de gestão, autenticação de smart card ou outra solução de autenticação multifator com JEA.</span><span class="sxs-lookup"><span data-stu-id="b3f06-197">This can be useful if you want to integrate a "just in time" privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="b3f06-198">Regras de acesso condicional são definidas no campo RequiredGroups num arquivo de configuração de sessão.</span><span class="sxs-lookup"><span data-stu-id="b3f06-198">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="b3f06-199">Lá, pode fornecer uma tabela de hash (opcionalmente aninhada) que utiliza "E" e "Ou" chaves para construir as suas regras.</span><span class="sxs-lookup"><span data-stu-id="b3f06-199">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="b3f06-200">Aqui estão alguns exemplos de como tirar partido deste campo:</span><span class="sxs-lookup"><span data-stu-id="b3f06-200">Here are some examples of how to leverage this field:</span></span>

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
> <span data-ttu-id="b3f06-201">Regras de acesso condicional só estão disponíveis no Windows PowerShell 5.1 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="b3f06-201">Conditional access rules are only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="b3f06-202">Outras propriedades</span><span class="sxs-lookup"><span data-stu-id="b3f06-202">Other properties</span></span>

<span data-ttu-id="b3f06-203">Ficheiros de configuração de sessão também podem fazer tudo o que um arquivo de recurso de função pode fazer, basta sem a capacidade de conceder o acesso de utilizadores ao ligar a comandos diferentes.</span><span class="sxs-lookup"><span data-stu-id="b3f06-203">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span>
<span data-ttu-id="b3f06-204">Se quiser permitir aos utilizadores acesso a cmdlets específicos, funções ou os fornecedores, pode fazê-lo diretamente no ficheiro de configuração de sessão.</span><span class="sxs-lookup"><span data-stu-id="b3f06-204">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="b3f06-205">Para obter uma lista completa de propriedades suportadas no ficheiro de configuração de sessão, execute `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="b3f06-205">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="b3f06-206">Teste de um ficheiro de configuração de sessão</span><span class="sxs-lookup"><span data-stu-id="b3f06-206">Testing a session configuration file</span></span>

<span data-ttu-id="b3f06-207">Pode testar uma configuração de sessão através da [teste PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3f06-207">You can test a session configuration using the [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span>
<span data-ttu-id="b3f06-208">É altamente recomendável que teste seu arquivo de configuração de sessão se editou o ficheiro de pssc manualmente usando um editor de texto para verificar que a sintaxe está correta.</span><span class="sxs-lookup"><span data-stu-id="b3f06-208">It is strongly recommended that you test your session configuration file if you have edited the pssc file manually using a text editor to ensure the syntax is correct.</span></span>
<span data-ttu-id="b3f06-209">Se um ficheiro de configuração de sessão não passam no teste, não será capaz de ser registado com êxito no sistema.</span><span class="sxs-lookup"><span data-stu-id="b3f06-209">If a session configuration file does not pass this test, it will not be able to be successfully registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="b3f06-210">Ficheiro de configuração de sessão de exemplo</span><span class="sxs-lookup"><span data-stu-id="b3f06-210">Sample session configuration file</span></span>

<span data-ttu-id="b3f06-211">Segue-se um exemplo completo que mostra como criar e validar uma configuração de sessão para JEA.</span><span class="sxs-lookup"><span data-stu-id="b3f06-211">Below is a complete example showing how to create and validate a session configuration for JEA.</span></span>
<span data-ttu-id="b3f06-212">Tenha em atenção que as definições de funções são criadas e armazenadas no `$roles` variável por conveniência e legibilidade.</span><span class="sxs-lookup"><span data-stu-id="b3f06-212">Note that the role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span>
<span data-ttu-id="b3f06-213">Não é um requisito para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="b3f06-213">It is not a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="b3f06-214">A atualizar ficheiros de configuração de sessão</span><span class="sxs-lookup"><span data-stu-id="b3f06-214">Updating session configuration files</span></span>

<span data-ttu-id="b3f06-215">Se precisar de alterar propriedades de uma configuração de sessão JEA, incluindo o mapeamento de utilizadores às funções, deve [anular o registo](register-jea.md#unregistering-jea-configurations) e [voltar a registar](register-jea.md) a configuração de sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="b3f06-215">If you need to change properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations) and [re-register](register-jea.md) the JEA session configuration.</span></span>
<span data-ttu-id="b3f06-216">Quando voltar a registar a configuração de sessão JEA, utilize um ficheiro de configuração sessão atualizado PowerShell inclui as alterações necessárias.</span><span class="sxs-lookup"><span data-stu-id="b3f06-216">When you re-register the JEA session configuration, use an updated PowerShell session configuration file that includes your desired changes.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b3f06-217">Próximos passos</span><span class="sxs-lookup"><span data-stu-id="b3f06-217">Next steps</span></span>

- [<span data-ttu-id="b3f06-218">Registe-se de uma configuração de JEA</span><span class="sxs-lookup"><span data-stu-id="b3f06-218">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="b3f06-219">Funções JEA do autor</span><span class="sxs-lookup"><span data-stu-id="b3f06-219">Author JEA roles</span></span>](role-capabilities.md)
