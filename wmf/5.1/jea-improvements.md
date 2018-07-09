---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: ryanpu
title: Melhorias à administração Just Enough (JEA)
ms.openlocfilehash: 79271e77a539764e7a18842efd919413cdc8ab9f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892724"
---
# <a name="improvements-to-just-enough-administration-jea"></a><span data-ttu-id="482fb-103">Melhorias à administração Just Enough (JEA)</span><span class="sxs-lookup"><span data-stu-id="482fb-103">Improvements to Just Enough Administration (JEA)</span></span>

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a><span data-ttu-id="482fb-104">Cópia de ficheiros restrita em pontos finais JEA</span><span class="sxs-lookup"><span data-stu-id="482fb-104">Constrained file copy to/from JEA endpoints</span></span>

<span data-ttu-id="482fb-105">Pode agora remotamente copiar ficheiros para/de um JEA rest e de ponto final ter a certeza de que o usuário conectado não é possível copiar apenas *qualquer* ficheiro no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="482fb-105">You can now remotely copy files to/from a JEA endpoint and rest assured that the connecting user can't copy just *any* file on your system.</span></span>
<span data-ttu-id="482fb-106">Isso é possível ao configurar o seu ficheiro PSSC para montar uma unidade de usuário para conectar usuários.</span><span class="sxs-lookup"><span data-stu-id="482fb-106">This is possible by configuring your PSSC file to mount a user drive for connecting users.</span></span>
<span data-ttu-id="482fb-107">A unidade de utilizador é um novo PSDrive, que é exclusiva para cada usuário conectado e presentes em sessões.</span><span class="sxs-lookup"><span data-stu-id="482fb-107">The user drive is a new PSDrive that is unique to each connecting user and persists across sessions.</span></span>
<span data-ttu-id="482fb-108">Quando `Copy-Item` é usado para copiar ficheiros de ou para uma sessão JEA, é restrito para permitir apenas o acesso para a unidade de utilizador.</span><span class="sxs-lookup"><span data-stu-id="482fb-108">When `Copy-Item` is used to copy files to or from a JEA session, it is constrained to only allow access to the user drive.</span></span>
<span data-ttu-id="482fb-109">Tentativas de copiar ficheiros para quaisquer outro PSDrive irão falhar.</span><span class="sxs-lookup"><span data-stu-id="482fb-109">Attempts to copy files to any other PSDrive will fail.</span></span>

<span data-ttu-id="482fb-110">Para configurar a unidade de utilizador no seu ficheiro de configuração de sessão JEA, utilize os seguintes novos campos:</span><span class="sxs-lookup"><span data-stu-id="482fb-110">To set up the user drive in your JEA session configuration file, use the following new fields:</span></span>

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

<span data-ttu-id="482fb-111">A pasta da unidade de utilizador de segurança será criada em `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span><span class="sxs-lookup"><span data-stu-id="482fb-111">The folder backing the user drive will be created at `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span></span>

<span data-ttu-id="482fb-112">Para utilizar a unidade de utilizador e copiar ficheiros de/para um ponto final JEA configurado para expor a unidade de utilizador, utilize o `-ToSession` e `-FromSession` parâmetros no `Copy-Item`.</span><span class="sxs-lookup"><span data-stu-id="482fb-112">To utilize the user drive and copy files to/from a JEA endpoint configured to expose the User drive, use the `-ToSession` and `-FromSession` parameters on `Copy-Item`.</span></span>

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine. You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

<span data-ttu-id="482fb-113">Em seguida, pode criar funções personalizadas para processar os dados armazenados na unidade de utilizador e as disponibilizar aos utilizadores no seu arquivo de recurso de função.</span><span class="sxs-lookup"><span data-stu-id="482fb-113">You can then write custom functions to process the data stored in the user drive and make those available to users in your Role Capability file.</span></span>

## <a name="support-for-group-managed-service-accounts"></a><span data-ttu-id="482fb-114">Serviço gerido de suporte para o grupo de contas</span><span class="sxs-lookup"><span data-stu-id="482fb-114">Support for Group Managed Service Accounts</span></span>

<span data-ttu-id="482fb-115">Em alguns casos, uma tarefa que um utilizador precisa de realizar numa sessão JEA poderá ter de aceder aos recursos além do computador local.</span><span class="sxs-lookup"><span data-stu-id="482fb-115">In some cases, a task a user needs to perform in a JEA session may need to access resources beyond the local machine.</span></span>
<span data-ttu-id="482fb-116">Quando uma sessão JEA é configurada para utilizar uma conta virtual, será apresentado qualquer tentativa de atingir tais recursos provenientes de identidade do computador local, não a conta virtual ou o usuário conectado.</span><span class="sxs-lookup"><span data-stu-id="482fb-116">When a JEA session is configured to use a virtual account, any attempt to reach such resources will appear to come from the local machine's identity, not the virtual account or connected user.</span></span>
<span data-ttu-id="482fb-117">Na TP5, ativámos o suporte para a execução de JEA sob o contexto de um [grupo de conta de serviço gerida] (https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx), tornando muito mais fácil aceder aos recursos de rede com uma identidade de domínio.</span><span class="sxs-lookup"><span data-stu-id="482fb-117">In TP5, we have enabled support for running JEA under the context of a [Group Managed Service Account](https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx), making it much easier to access network resources by using a domain identity.</span></span>

<span data-ttu-id="482fb-118">Para configurar uma sessão JEA para ser executado sob uma conta gMSA, utilize a seguinte chave de novo no seu ficheiro PSSC:</span><span class="sxs-lookup"><span data-stu-id="482fb-118">To configure a JEA session to run under a gMSA account, use the following new key in your PSSC file:</span></span>

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> <span data-ttu-id="482fb-119">Contas de serviço geridas de grupo não conseguir pagar o isolamento ou âmbito limitado de contas virtuais.</span><span class="sxs-lookup"><span data-stu-id="482fb-119">Group Managed Service Accounts do not afford the isolation or limited scope of virtual accounts.</span></span>
> <span data-ttu-id="482fb-120">Cada usuário conectado irá partilhar a mesma identidade de gMSA, que pode ter as permissões em toda a empresa inteira.</span><span class="sxs-lookup"><span data-stu-id="482fb-120">Every connecting user will share the same gMSA identity, which may have permissions across your entire enterprise.</span></span>
> <span data-ttu-id="482fb-121">Tenha muito cuidado ao selecionar a utilizar uma gMSA e prefere sempre o contas virtuais que estão limitadas a máquina local sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="482fb-121">Be very careful when selecting to use a gMSA, and always prefer virtual accounts which are limited to the local machine when possible.</span></span>

## <a name="conditional-access-policies"></a><span data-ttu-id="482fb-122">Políticas de acesso condicional</span><span class="sxs-lookup"><span data-stu-id="482fb-122">Conditional access policies</span></span>

<span data-ttu-id="482fb-123">O JEA é excelente para limitar o que alguém pode fazer quando eles já ligado a um sistema para geri-la, mas e se também queira limitar *quando* alguém pode utilizar a JEA?</span><span class="sxs-lookup"><span data-stu-id="482fb-123">JEA is great at limiting what someone can do when they've connected to a system to manage it, but what if you also want to limit *when* someone can use JEA?</span></span>
<span data-ttu-id="482fb-124">Adicionámos as opções de configuração nos arquivos de configuração de sessão (.pssc) para permitem-lhe especificar os grupos de segurança para o qual um utilizador tem de pertencer a fim de estabelecer uma sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="482fb-124">We have added configuration options into the session configuration files (.pssc) to let you specify security groups to which a user must belong in order to establish a JEA session.</span></span>
<span data-ttu-id="482fb-125">Isso pode ser particularmente útil se tiver um sistema apenas no Time (JIT) no seu ambiente e desejar que seus usuários elevar seus privilégios antes de aceder a um ponto final JEA de privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="482fb-125">This can be particularly helpful if you have a Just In Time (JIT) system in your environment, and want to make your users elevate their privileges before accessing a highly-privileged JEA endpoint.</span></span>

<span data-ttu-id="482fb-126">A nova *RequiredGroups* campo no ficheiro PSSC permite-lhe especificar a lógica para determinar se um utilizador pode ligar ao JEA.</span><span class="sxs-lookup"><span data-stu-id="482fb-126">The new *RequiredGroups* field in the PSSC file allows you to specify the logic to determine if a user can connect to JEA.</span></span>
<span data-ttu-id="482fb-127">Ele consiste em especificar uma tabela de hash (opcionalmente aninhada) que utiliza o "E" e "Ou" chaves para construir as suas regras.</span><span class="sxs-lookup"><span data-stu-id="482fb-127">It consists of specifying a hashtable (optionally nested) that uses the 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="482fb-128">Aqui estão alguns exemplos de como tirar partido deste campo:</span><span class="sxs-lookup"><span data-stu-id="482fb-128">Here are some examples of how to leverage this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a><span data-ttu-id="482fb-129">Foi corrigido: Contas virtuais agora são suportadas no Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="482fb-129">Fixed: Virtual accounts are now supported on Windows Server 2008 R2</span></span>

<span data-ttu-id="482fb-130">No WMF 5.1, agora é possível utilizar contas virtuais no Windows Server 2008 R2, permitindo configurações consistentes e paridade de funcionalidades entre o Windows Server 2008 R2 - 2016.</span><span class="sxs-lookup"><span data-stu-id="482fb-130">In WMF 5.1, you are now able to use virtual accounts on Windows Server 2008 R2, enabling consistent configurations and feature parity across Windows Server 2008 R2 - 2016.</span></span>
<span data-ttu-id="482fb-131">Contas virtuais permanecem não suportadas ao utilizar a JEA no Windows 7.</span><span class="sxs-lookup"><span data-stu-id="482fb-131">Virtual accounts remain unsupported when using JEA on Windows 7.</span></span>