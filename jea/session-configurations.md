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
# <a name="jea-session-configurations"></a>Configurações de sessão JEA

Um ponto final JEA está registado num sistema ao criar e registar um ficheiro de configuração de sessão do PowerShell. Configurações de sessão definem quem pode usar o ponto final da JEA e quais funções aos quais têm acesso. Elas também definem as definições globais que se aplicam a todos os utilizadores da sessão JEA.

## <a name="create-a-session-configuration-file"></a>Criar um ficheiro de configuração de sessão

Para registar um ponto final JEA, tem de especificar a configuração do ponto de extremidade. Existem muitas opções a serem considerados. As opções mais importantes são:

- Quem tem acesso ao ponto final JEA
- Que funções de ser atribuídos
- Que identidade JEA utiliza nos bastidores
- O nome do ponto final JEA

Estas opções são definidas num arquivo de dados do PowerShell com um `.pssc` extensão conhecido como um ficheiro de configuração de sessão do PowerShell. O ficheiro de configuração de sessão pode ser editado com qualquer editor de texto.

Execute o seguinte comando para criar um ficheiro de configuração de modelo em branco.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Por predefinição, apenas as opções de configuração mais comuns são incluídas no ficheiro de modelo. Utilize o `-Full` comutador para incluir todas as configurações aplicáveis no PSSC gerado.

O `-SessionType RestrictedRemoteServer` campo indica que a configuração de sessão é utilizada pelo JEA para a gestão segura. Sessões deste tipo operam **NoLanguage** modo e só tem acesso para os seguintes comandos padrão (e aliases):

- Clear-Host (cls, claro)
- Exit-PSSession (exsn, exit)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Objeto de medida (medidas)
- Out-Default
- Select-Object (selecionar)

Não existem fornecedores de PowerShell estão disponíveis, nem são que programas de qualquer externo (executáveis ou scripts).

Para obter mais informações sobre os modos de idioma, consulte [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).

### <a name="choose-the-jea-identity"></a>Escolha a identidade JEA

Em segundo plano, JEA tem uma identidade (conta) para utilizar durante a execução de comandos de um usuário conectado.
Definir que identidade JEA utiliza no ficheiro de configuração de sessão.

#### <a name="local-virtual-account"></a>Conta Virtual local

Contas virtuais locais são úteis quando todas as funções definidas para o ponto final da JEA são utilizadas para gerir o computador local e uma conta de administrador local é suficiente para executar os comandos com êxito.
Contas virtuais são contas temporárias que são exclusivas para um utilizador específico e apenas os últimos durante a sessão do PowerShell. Num servidor membro ou estação de trabalho, contas virtuais pertencem ao computador local **administradores** grupo. Num controlador de domínio do Active Directory, contas virtuais pertencem ao domínio **Admins do domínio** grupo.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Se as funções definidas na configuração da sessão não exigem privilégios administrativos completos, pode especificar os grupos de segurança para o qual irá pertencer a conta virtual. Num servidor membro ou estação de trabalho, os grupos de segurança especificado tem de ser grupos locais, não os grupos de um domínio.

Quando um ou mais grupos de segurança são especificados, a conta virtual não está atribuída ao grupo de administradores locais ou de domínio.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> Contas virtuais recebem temporariamente o início de sessão como um direito de serviço na política de segurança de servidor local. Se um dos VirtualAccountGroups especificado já foi concedido este direito na política, a conta virtual individual já não será adicionada e removida da política. Isso pode ser útil em cenários como controladores de domínio em que a revisões para a política de segurança do controlador de domínio de perto são auditados. Isso só está disponível no Windows Server 2016 com a Novembro de 2018 ou rollup posterior e Windows Server 2019 com o de 2019 de Janeiro ou rollup posterior.

#### <a name="group-managed-service-account"></a>Conta de serviço gerida de grupo

Uma conta de serviço gerida de grupo (GMSA) é a identidade adequada a utilizar quando os utilizadores JEA precisam de aceder a recursos de rede, como partilhas de ficheiros e serviços da web. As GMSAs dão-lhe uma identidade de domínio que é utilizada para autenticar com recursos em qualquer computador no domínio. Os direitos de que uma GMSA fornece são determinados pelos recursos que está a aceder. Não tem direitos de administrador em qualquer máquinas ou serviços, a menos que o administrador de máquina ou serviço lhe tiver concedido explicitamente esses direitos a GMSA.

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

As GMSAs devem ser apenas quando necessário:

- É difícil efectuar o rastreio ações para um utilizador ao utilizar uma GMSA. Todos os usuários compartilha a mesma identidade Run. Tem de rever os registos para correlacionar a utilizadores individuais com as suas ações e de transcrições de sessão do PowerShell.

- A GMSA pode ter acesso a vários recursos de rede que o usuário conectado, não precisa acessar. Sempre tente limitar as permissões efetivas numa sessão JEA para acompanhar o princípio de privilégio mínimo.

> [!NOTE]
> Contas de serviço geridas de grupo só estão disponíveis em computadores associados a um domínio com o PowerShell 5.1 ou mais recente.

Para obter mais informações sobre como proteger uma sessão JEA, consulte a [considerações de segurança](security-considerations.md) artigo.

### <a name="session-transcripts"></a>Transcrições de sessão

Recomenda-se que configure um ponto final JEA para transcrições automaticamente registos de sessões dos utilizadores. Transcrições de sessão do PowerShell contêm informações sobre o usuário conectado, a execução como identidade atribuída, e os comandos são executados pelo utilizador. Eles podem ser úteis para uma equipe de auditoria que precisa entender quem as fez uma alteração específica para um sistema.

Para configurar a transcrição automática no ficheiro de configuração de sessão, forneça um caminho para uma pasta onde as transcrições devem ser armazenadas.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

Transcrições são escritas para a pasta, o **Sistema Local** conta, que requer a leitura e de acesso de escrita para o diretório. Os usuários padrão não devem ter acesso à pasta. Limite o número de administradores de segurança que têm acesso para auditar as transcrições.

### <a name="user-drive"></a>Unidade de utilizador

Se os utilizadores de ligação tem de copiar ficheiros de ou para o ponto final da JEA, pode ativar a unidade de utilizador no ficheiro de configuração de sessão. A unidade de utilizador é um **PSDrive** que está mapeado para uma pasta exclusiva para cada usuário conectado. Esta pasta permite que os usuários copiem arquivos de ou para o sistema sem dar-lhes acesso ao sistema de ficheiros completa ou expor o fornecedor do sistema de ficheiros. O conteúdo da unidade de utilizador é persistente entre sessões para acomodar as situações em que a conectividade de rede pode ser interrompida.

```powershell
MountUserDrive = $true
```

Por predefinição, a unidade de utilizador permite-lhe armazenar um máximo de 50MB de dados por utilizador. Pode limitar a quantidade de dados de um utilizador pode consumir com o *UserDriveMaximumSize* campo.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Se não pretender que os dados na unidade do utilizador para ser persistente, pode configurar uma tarefa agendada no sistema para limpar automaticamente a pasta de todas as noites.

> [!NOTE]
> A unidade de utilizador só está disponível no PowerShell 5.1 ou mais recente.

Para obter mais informações sobre PSDrives, consulte [unidades de gerenciamento PowerShell](/powershell/scripting/samples/managing-windows-powershell-drives).

### <a name="role-definitions"></a>Definições de funções

Definições de funções num arquivo de configuração de sessão definem o mapeamento dos **usuários** ao **funções**. Cada utilizador ou grupo incluído neste campo é concedido permissão para o ponto final da JEA quando é registado.
Cada utilizador ou grupo pode ser incluído como uma chave da tabela de hash apenas uma vez, mas pode ser atribuído várias funções. O nome da capacidade de função deve ser o nome do arquivo de recurso de função, sem o `.psrc` extensão.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Se um utilizador pertencer a mais de um grupo na definição de função, eles recebem acesso às funções de cada. Quando duas funções de concedem acesso para os mesmos cmdlets, o conjunto de parâmetros mais permissivo é concedido ao utilizador.

Ao especificar grupos de utilizadores ou no campo de definições de função, certifique-se de que utiliza o nome do computador, não **localhost** ou carateres universais. Pode verificar o nome do computador ao inspecionar o `$env:COMPUTERNAME` variável.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Ordem de pesquisa de capacidade de função

Conforme mostrado no exemplo acima, as funcionalidades de função são referenciadas pelo nome de base do arquivo de recurso de função. O nome de base de um ficheiro é o nome de ficheiro sem a extensão. Se várias funcionalidades de função estão disponíveis no sistema com o mesmo nome, o PowerShell usa sua ordem de pesquisa implícito para selecionar o ficheiro de recurso de função em vigor. JEA faz **não** conceder acesso a todos os ficheiros de recurso de função com o mesmo nome.

JEA utiliza o `$env:PSModulePath` variável de ambiente para determinar os caminhos para verificar a existência de arquivos de recurso de função. Dentro de cada um desses caminhos, JEA procura válidos módulos do PowerShell que contêm uma subpasta do "RoleCapabilities". Tal como acontece com a importação de módulos JEA prefere funcionalidades de função que são fornecidas com o Windows às capacidades de função personalizada com o mesmo nome.

Para todos os outros conflitos de nomenclatura, a precedência é determinada pela ordem em que o Windows enumera os ficheiros no diretório. A ordem não é garantida que alfabética. O primeiro arquivo de recurso de função encontrado que corresponda ao especificado nome é utilizado para o usuário conectado. Desde a pesquisa de capacidade de função ordem não é determinística, é **vivamente recomendado** que funcionalidades de função têm nomes de arquivo exclusivo.

### <a name="conditional-access-rules"></a>Regras de acesso condicional

Todos os utilizadores e grupos incluídos os **RoleDefinitions** campo recebem automaticamente acesso a pontos finais JEA. Regras de acesso condicional permitem-lhe refinar este acesso e exigir que os utilizadores pertencem a grupos de segurança adicionais que não tenham impacto sobre as funções para o qual foram atribuídos. Isto é útil quando pretende integrar uma solução de gestão de acesso privilegiado just-in-time, a autenticação de smart card ou outra solução de autenticação multifator com JEA.

Regras de acesso condicional são definidas no campo RequiredGroups num arquivo de configuração de sessão.
Lá, pode fornecer uma tabela de hash (opcionalmente aninhada) que utiliza "E" e "Ou" chaves para construir as suas regras. Aqui estão alguns exemplos de como utilizar este campo:

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
> Regras de acesso condicional só estão disponíveis no PowerShell 5.1 ou mais recente.

### <a name="other-properties"></a>Outras propriedades

Ficheiros de configuração de sessão também podem fazer tudo o que um arquivo de recurso de função pode fazer, basta sem a capacidade de conceder o acesso de utilizadores ao ligar a comandos diferentes. Se quiser permitir aos utilizadores acesso a cmdlets específicos, funções ou os fornecedores, pode fazê-lo diretamente no ficheiro de configuração de sessão.
Para obter uma lista completa de propriedades suportadas no ficheiro de configuração de sessão, execute `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Teste de um ficheiro de configuração de sessão

Pode testar uma configuração de sessão através da [teste PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet. Recomenda-se que teste o seu ficheiro de configuração de sessão se tiver de ser editado manualmente o `.pssc` ficheiro. O teste assegura que a sintaxe está correta. Se um ficheiro de configuração de sessão falhar este teste, não é possível registar no sistema.

## <a name="sample-session-configuration-file"></a>Ficheiro de configuração de sessão de exemplo

O exemplo seguinte mostra como criar e validar uma configuração de sessão para JEA. As definições de funções são criadas e armazenadas no `$roles` variável por conveniência e legibilidade. Não é um requisito para fazer isso.

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a>A atualizar ficheiros de configuração de sessão

Para alterar as propriedades de uma configuração de sessão JEA, incluindo o mapeamento de utilizadores às funções, deve [anular o registo](register-jea.md#unregistering-jea-configurations). Em seguida, [volte a registar](register-jea.md) a configuração de sessão JEA utilizando um ficheiro de configuração de sessão atualizadas.

## <a name="next-steps"></a>Passos Seguintes

- [Registe-se de uma configuração de JEA](register-jea.md)
- [Funções JEA do autor](role-capabilities.md)
