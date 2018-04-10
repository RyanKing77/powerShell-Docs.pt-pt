---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
contributor: ryanpu
title: Melhoramentos à administração Just Enough (JEA)
ms.openlocfilehash: c80472fa4372331bf2cf9ab0b7513021354d1408
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="improvements-to-just-enough-administration-jea"></a>Melhoramentos à administração Just Enough (JEA)

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a>Cópia de ficheiros restrita do pontos finais JEA

Pode agora remotamente copiar ficheiros para/de uma JEA ponto final e rest a certeza de que o utilizador de ligação não é possível copiar apenas *qualquer* ficheiro no sistema.
Isto é possível ao configurar o seu ficheiro PSSC montar uma unidade de utilizador para ligar os utilizadores.
A unidade de utilizador é um novo PSDrive que é exclusiva para cada utilizador de ligação e persistir entre sessões.
Quando o Item de cópia é utilizada para copiar ficheiros para ou a partir de uma sessão JEA, este está restringida para permitir apenas o acesso à unidade de utilizador.
As tentativas para copiar ficheiros para quaisquer outro PSDrive falharão.

Para configurar a unidade de utilizador no ficheiro de configuração de sessão JEA, utilize os seguintes campos novos:

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

A pasta de cópia de unidade de utilizador será criada em `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`

Para utilizar a unidade de utilizador e copiar ficheiros para/de um ponto final de JEA configurado para expor o disco do utilizador, utilize o `-ToSession` e `-FromSession` parâmetros num Item de cópia.

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine. You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

Em seguida, pode escrever funções personalizadas para processar os dados armazenados na unidade de utilizador e os disponibilizar aos utilizadores no seu ficheiro de capacidade de função.

## <a name="support-for-group-managed-service-accounts"></a>Suporte para o grupo de serviço geridas de contas

Em alguns casos, uma tarefa de que um utilizador precisa de realizar numa sessão JEA poderá ter de aceder a recursos para além do computador local.
Quando uma sessão JEA é configurada para utilizar uma conta virtual, qualquer tentativa de aceder esses recursos aparecerá vêm da identidade do computador local, não a conta virtual ou utilizador ligada.
No TP5, iremos ativar suporte para executar o JEA sob o contexto de uma [grupo de conta de serviço gerida] (https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\). aspx), tornando mais fácil e aceder a recursos de rede ao utilizar uma identidade de domínio.

Para configurar uma sessão JEA para ser executado sob uma conta gMSA, utilize a seguinte chave de novo no seu ficheiro PSSC:

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> **Nota:** contas de serviço geridas de grupo não suportar o isolamento ou âmbito limitado de contas virtuais.
> Todos os utilizadores de ligação em curso irão partilhar a mesma identidade de gMSA, que pode ter as permissões em toda a empresa completa.
> Tenha muito cuidado quando selecionar a utilizar uma gMSA e preferir sempre contas virtuais que estão limitadas para a máquina local sempre que possível.

## <a name="conditional-access-policies"></a>Políticas de acesso condicional

O JEA é excelente ao limitar o que alguém pode fazer quando tiver ligados a um sistema geri-lo, mas que se pode também pretende limitar *quando* alguém pode utilizar o JEA?
Opções de configuração para os ficheiros de configuração de sessão (.pssc) para permitem-lhe especificar os grupos de segurança para os quais um utilizador tem de pertencer para estabelecer uma sessão JEA, foi adicionado.
Isto pode ser particularmente útil se tiver um sistema de apenas no tempo (JIT) no seu ambiente e pretende tornar os seus utilizadores elevar os seus privilégios antes de aceder a um ponto final da JEA altamente privilegiados.

A nova *RequiredGroups* campo no ficheiro PSSC permite-lhe especificar a lógica para determinar se um utilizador poder ligar ao JEA.
É composto por uma tabela hash (opcionalmente aninhada) que utiliza a especificação de 'E' e 'Ou' chaves construir as regras.
Seguem-se alguns exemplos de como tirar partido deste campo:

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a>Fixo: Contas virtuais são agora suportadas no Windows Server 2008 R2
No WMF 5.1, está agora podem utilizar as contas virtual no Windows Server 2008 R2, ativar paridade de funcionalidades e configurações consistentes em todos os Windows Server 2008 R2 - 2016.
As contas virtual permanecem não suportadas ao utilizar o JEA no Windows 7.