---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Melhorias à administração Just Enough (JEA)
ms.openlocfilehash: 847ae92a6225023bcd0ee3dfe7c7058bdc356836
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856204"
---
# <a name="improvements-to-just-enough-administration-jea"></a>Melhorias à administração Just Enough (JEA)

Administração just Enough é um novo recurso do WMF 5.0, que permite a administração baseada em funções por meio de comunicação remota do PowerShell. Ele estende a infra-estrutura existente do ponto de extremidade restrita, permitindo que os não-administradores executar comandos específicos, scripts e executáveis como administrador. Isto permite-lhe reduzir o número de administradores totais no seu ambiente e melhorar a segurança.

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a>Cópia de ficheiros restrita em pontos finais JEA

Pode agora remotamente copiar ficheiros de/para um ponto final JEA e ter a garantia de que o usuário conectado não é possível copiar apenas *qualquer* ficheiro no seu sistema. Isso é possível ao configurar o seu ficheiro PSSC para montar uma unidade de usuário para conectar usuários. A unidade de utilizador é um novo PSDrive, que é exclusiva para cada usuário conectado e presentes em sessões. Quando `Copy-Item` é usado para copiar ficheiros de ou para uma sessão JEA, é restrito para permitir apenas o acesso para a unidade de utilizador. Tentativas de copiar ficheiros para quaisquer outro PSDrive irão falhar.

Para configurar a unidade de utilizador no seu ficheiro de configuração de sessão JEA, utilize os seguintes novos campos:

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

A pasta da unidade de utilizador de segurança será criada em `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`

Para utilizar a unidade de utilizador e copiar ficheiros de/para um ponto final JEA configurado para expor a unidade de utilizador, utilize o `-ToSession` e `-FromSession` parâmetros no `Copy-Item`.

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine.
# You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

Em seguida, pode criar funções personalizadas para processar os dados armazenados na unidade de utilizador e as disponibilizar aos utilizadores no seu arquivo de recurso de função.

## <a name="support-for-group-managed-service-accounts"></a>Serviço gerido de suporte para o grupo de contas

Em alguns casos, uma tarefa que um utilizador precisa de realizar numa sessão JEA poderá ter de aceder aos recursos além do computador local. Quando uma sessão JEA é configurada para utilizar uma conta virtual, será apresentado qualquer tentativa de atingir tais recursos provenientes de identidade do computador local, não a conta virtual ou o usuário conectado. Na TP5, ativámos o suporte para a execução de JEA sob o contexto de um [conta de serviço gerida de grupo](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), tornando muito mais fácil aceder aos recursos de rede com uma identidade de domínio.

Para configurar uma sessão JEA para ser executado sob uma conta gMSA, utilize a seguinte chave de novo no seu ficheiro PSSC:

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> Contas de serviço geridas de grupo não conseguir pagar o isolamento ou âmbito limitado de contas virtuais.
> Cada usuário conectado irá partilhar a mesma identidade de gMSA, que pode ter as permissões em toda a empresa inteira. Tenha muito cuidado ao selecionar a utilizar uma gMSA e prefere sempre o contas virtuais que estão limitadas a máquina local sempre que possível.

## <a name="conditional-access-policies"></a>Políticas de acesso condicional

O JEA é excelente para limitar o que alguém pode fazer quando eles já ligado a um sistema para geri-la, mas e se também queira limitar *quando* alguém pode utilizar a JEA? Adicionámos as opções de configuração nos arquivos de configuração de sessão (.pssc) para permitem-lhe especificar os grupos de segurança para o qual um utilizador tem de pertencer a fim de estabelecer uma sessão JEA. Isso é especialmente útil se tiver um sistema apenas no Time (JIT) no seu ambiente e desejar que seus usuários elevar seus privilégios antes de aceder a um ponto final JEA de privilégios elevados.

A nova *RequiredGroups* campo no ficheiro PSSC permite-lhe especificar a lógica para determinar se um utilizador pode ligar ao JEA. Ele consiste em especificar uma tabela de hash (opcionalmente aninhada) que utiliza o "E" e "Ou" chaves para construir as suas regras. Aqui estão alguns exemplos de como utilizar este campo:

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a>Corrigido: Contas virtuais são agora suportadas no Windows Server 2008 R2

No WMF 5.1, agora é possível utilizar contas virtuais no Windows Server 2008 R2, permitindo configurações consistentes e paridade de funcionalidades entre o Windows Server 2008 R2 - 2016. Contas virtuais permanecem não suportadas ao utilizar a JEA no Windows 7.