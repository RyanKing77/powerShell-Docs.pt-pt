---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
contributor: ryanpu
title: "Melhoramentos à administração Just Enough (JEA)"
ms.openlocfilehash: 2811b4deb3f4fca513791c7389ee5f9f877dbfe8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="improvements-to-just-enough-administration-jea"></a><span data-ttu-id="4e155-103">Melhoramentos à administração Just Enough (JEA)</span><span class="sxs-lookup"><span data-stu-id="4e155-103">Improvements to Just Enough Administration (JEA)</span></span>

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a><span data-ttu-id="4e155-104">Cópia de ficheiros restrita do pontos finais JEA</span><span class="sxs-lookup"><span data-stu-id="4e155-104">Constrained file copy to/from JEA endpoints</span></span>

<span data-ttu-id="4e155-105">Pode agora remotamente copiar ficheiros para/de uma JEA ponto final e rest a certeza de que o utilizador de ligação não é possível copiar apenas *qualquer* ficheiro no sistema.</span><span class="sxs-lookup"><span data-stu-id="4e155-105">You can now remotely copy files to/from a JEA endpoint and rest assured that the connecting user can't copy just *any* file on your system.</span></span>
<span data-ttu-id="4e155-106">Isto é possível ao configurar o seu ficheiro PSSC montar uma unidade de utilizador para ligar os utilizadores.</span><span class="sxs-lookup"><span data-stu-id="4e155-106">This is possible by configuring your PSSC file to mount a user drive for connecting users.</span></span>
<span data-ttu-id="4e155-107">A unidade de utilizador é um novo PSDrive que é exclusiva para cada utilizador de ligação e persistir entre sessões.</span><span class="sxs-lookup"><span data-stu-id="4e155-107">The user drive is a new PSDrive that is unique to each connecting user and persists across sessions.</span></span>
<span data-ttu-id="4e155-108">Quando o Item de cópia é utilizada para copiar ficheiros para ou a partir de uma sessão JEA, este está restringida para permitir apenas o acesso à unidade de utilizador.</span><span class="sxs-lookup"><span data-stu-id="4e155-108">When Copy-Item is used to copy files to or from a JEA session, it is constrained to only allow access to the user drive.</span></span>
<span data-ttu-id="4e155-109">As tentativas para copiar ficheiros para quaisquer outro PSDrive falharão.</span><span class="sxs-lookup"><span data-stu-id="4e155-109">Attempts to copy files to any other PSDrive will fail.</span></span>

<span data-ttu-id="4e155-110">Para configurar a unidade de utilizador no ficheiro de configuração de sessão JEA, utilize os seguintes campos novos:</span><span class="sxs-lookup"><span data-stu-id="4e155-110">To set up the user drive in your JEA session configuration file, use the following new fields:</span></span>

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

<span data-ttu-id="4e155-111">A pasta de cópia de unidade de utilizador será criada em`$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span><span class="sxs-lookup"><span data-stu-id="4e155-111">The folder backing the user drive will be created at `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span></span>

<span data-ttu-id="4e155-112">Para utilizar a unidade de utilizador e copiar ficheiros para/de um ponto final de JEA configurado para expor o disco do utilizador, utilize o `-ToSession` e `-FromSession` parâmetros num Item de cópia.</span><span class="sxs-lookup"><span data-stu-id="4e155-112">To utilize the user drive and copy files to/from a JEA endpoint configured to expose the User drive, use the `-ToSession` and `-FromSession` parameters on Copy-Item.</span></span>

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine. You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

<span data-ttu-id="4e155-113">Em seguida, pode escrever funções personalizadas para processar os dados armazenados na unidade de utilizador e os disponibilizar aos utilizadores no seu ficheiro de capacidade de função.</span><span class="sxs-lookup"><span data-stu-id="4e155-113">You can then write custom functions to process the data stored in the user drive and make those available to users in your Role Capability file.</span></span>

## <a name="support-for-group-managed-service-accounts"></a><span data-ttu-id="4e155-114">Suporte para o grupo de serviço geridas de contas</span><span class="sxs-lookup"><span data-stu-id="4e155-114">Support for Group Managed Service Accounts</span></span>

<span data-ttu-id="4e155-115">Em alguns casos, uma tarefa de que um utilizador precisa de realizar numa sessão JEA poderá ter de aceder a recursos para além do computador local.</span><span class="sxs-lookup"><span data-stu-id="4e155-115">In some cases, a task a user needs to perform in a JEA session may need to access resources beyond the local machine.</span></span>
<span data-ttu-id="4e155-116">Quando uma sessão JEA é configurada para utilizar uma conta virtual, qualquer tentativa de aceder esses recursos aparecerá vêm da identidade do computador local, não a conta virtual ou utilizador ligada.</span><span class="sxs-lookup"><span data-stu-id="4e155-116">When a JEA session is configured to use a virtual account, any attempt to reach such resources will appear to come from the local machine's identity, not the virtual account or connected user.</span></span>
<span data-ttu-id="4e155-117">No TP5, iremos ativar suporte para executar o JEA sob o contexto de uma [grupo de conta de serviço gerida] (https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx), tornando mais fácil e aceder a recursos de rede através da utilização de um domínio identidade.</span><span class="sxs-lookup"><span data-stu-id="4e155-117">In TP5, we have enabled support for running JEA under the context of a [Group Managed Service Account](https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx), making it much easier to access network resources by using a domain identity.</span></span>

<span data-ttu-id="4e155-118">Para configurar uma sessão JEA para ser executado sob uma conta gMSA, utilize a seguinte chave de novo no seu ficheiro PSSC:</span><span class="sxs-lookup"><span data-stu-id="4e155-118">To configure a JEA session to run under a gMSA account, use the following new key in your PSSC file:</span></span>

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> <span data-ttu-id="4e155-119">**Nota:** contas de serviço geridas de grupo não suportar o isolamento ou âmbito limitado de contas virtuais.</span><span class="sxs-lookup"><span data-stu-id="4e155-119">**Note:** Group Managed Service Accounts do not afford the isolation or limited scope of virtual accounts.</span></span>
> <span data-ttu-id="4e155-120">Todos os utilizadores de ligação em curso irão partilhar a mesma identidade de gMSA, que pode ter as permissões em toda a empresa completa.</span><span class="sxs-lookup"><span data-stu-id="4e155-120">Every connecting user will share the same gMSA identity, which may have permissions across your entire enterprise.</span></span>
> <span data-ttu-id="4e155-121">Tenha muito cuidado quando selecionar a utilizar uma gMSA e preferir sempre contas virtuais que estão limitadas para a máquina local sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="4e155-121">Be very careful when selecting to use a gMSA, and always prefer virtual accounts which are limited to the local machine when possible.</span></span>

## <a name="conditional-access-policies"></a><span data-ttu-id="4e155-122">Políticas de acesso condicional</span><span class="sxs-lookup"><span data-stu-id="4e155-122">Conditional access policies</span></span>

<span data-ttu-id="4e155-123">O JEA é excelente ao limitar o que alguém pode fazer quando tiver ligados a um sistema geri-lo, mas que se pode também pretende limitar *quando* alguém pode utilizar o JEA?</span><span class="sxs-lookup"><span data-stu-id="4e155-123">JEA is great at limiting what someone can do when they've connected to a system to manage it, but what if you also want to limit *when* someone can use JEA?</span></span>
<span data-ttu-id="4e155-124">Opções de configuração para os ficheiros de configuração de sessão (.pssc) para permitem-lhe especificar os grupos de segurança para os quais um utilizador tem de pertencer para estabelecer uma sessão JEA, foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="4e155-124">We have added configuration options into the session configuration files (.pssc) to let you specify security groups to which a user must belong in order to establish a JEA session.</span></span>
<span data-ttu-id="4e155-125">Isto pode ser particularmente útil se tiver um sistema de apenas no tempo (JIT) no seu ambiente e pretende tornar os seus utilizadores elevar os seus privilégios antes de aceder a um ponto final da JEA altamente privilegiados.</span><span class="sxs-lookup"><span data-stu-id="4e155-125">This can be particularly helpful if you have a Just In Time (JIT) system in your environment, and want to make your users elevate their privileges before accessing a highly-privileged JEA endpoint.</span></span>

<span data-ttu-id="4e155-126">A nova *RequiredGroups* campo no ficheiro PSSC permite-lhe especificar a lógica para determinar se um utilizador poder ligar ao JEA.</span><span class="sxs-lookup"><span data-stu-id="4e155-126">The new *RequiredGroups* field in the PSSC file allows you to specify the logic to determine if a user can connect to JEA.</span></span>
<span data-ttu-id="4e155-127">É composto por uma tabela hash (opcionalmente aninhada) que utiliza a especificação de 'E' e 'Ou' chaves construir as regras.</span><span class="sxs-lookup"><span data-stu-id="4e155-127">It consists of specifying a hashtable (optionally nested) that uses the 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="4e155-128">Seguem-se alguns exemplos de como tirar partido deste campo:</span><span class="sxs-lookup"><span data-stu-id="4e155-128">Here are some examples of how to leverage this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a><span data-ttu-id="4e155-129">Fixo: Contas virtuais são agora suportadas no Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="4e155-129">Fixed: Virtual accounts are now supported on Windows Server 2008 R2</span></span>
<span data-ttu-id="4e155-130">No WMF 5.1, está agora podem utilizar as contas virtual no Windows Server 2008 R2, ativar paridade de funcionalidades e configurações consistentes em todos os Windows Server 2008 R2 - 2016.</span><span class="sxs-lookup"><span data-stu-id="4e155-130">In WMF 5.1, you are now able to use virtual accounts on Windows Server 2008 R2, enabling consistent configurations and feature parity across Windows Server 2008 R2 - 2016.</span></span>
<span data-ttu-id="4e155-131">As contas virtual permanecem não suportadas ao utilizar o JEA no Windows 7.</span><span class="sxs-lookup"><span data-stu-id="4e155-131">Virtual accounts remain unsupported when using JEA on Windows 7.</span></span>

