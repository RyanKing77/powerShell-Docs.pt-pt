---
ms.date: 06/12/2017
keywords: jea, powershell, segurança
title: Configurações de sessão JEA
ms.openlocfilehash: bdf3659357045203d90e8083613e51cce657da1a
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522967"
---
# <a name="jea-session-configurations"></a>Configurações de sessão JEA

> Aplica-se a: Windows PowerShell 5.0

Um ponto final JEA está registado num sistema ao criar e registar um ficheiro de configuração de sessão do PowerShell de uma forma específica.
Determinam as configurações de sessão *quem* pode utilizar o ponto final da JEA e quais funções elas têm acesso a.
Elas também definem as definições globais que se aplicam aos utilizadores de qualquer função na sessão JEA.

Este tópico descreve como criar um ficheiro de configuração de sessão do PowerShell e registar um ponto final JEA.

## <a name="create-a-session-configuration-file"></a>Criar um ficheiro de configuração de sessão

Para registar um ponto final JEA, terá de especificar a forma como ponto de extremidade deve ser configurado.
Existem muitas opções a serem considerados aqui, o mais importante dos quais sendo que devem ter acesso ao ponto final JEA, quais funções vão ser atribuído, que identidade JEA utilizará nos bastidores, e o que vai ser o nome do ponto final JEA.
Eles estão todos definidos num arquivo de configuração de sessão do PowerShell, que é um ficheiro de dados do PowerShell que termina com uma extensão de .pssc.

Para criar um ficheiro de configuração de sessão de esqueleto para pontos finais JEA, execute o seguinte comando.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Apenas as opções de configuração mais comuns estão incluídas no ficheiro de esqueleto por predefinição.
> Utilize o `-Full` comutador para incluir todas as configurações aplicáveis no PSSC gerado.

É possível abrir o ficheiro de configuração de sessão em qualquer editor de texto.
O `-SessionType RestrictedRemoteServer` campo indica que a configuração de sessão será utilizada pelo JEA para a gestão segura.
Sessões configurado dessa forma funcionarão [NoLanguage modo](https://technet.microsoft.com/library/dn433292.aspx) e só ter os seguintes comandos de predefinição de 8 (e aliases) disponível:

- Clear-Host (cls, claro)
- Exit-PSSession (exsn, saída)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Objeto de medida (medidas)
- Out-predefinido
- Select-Object (selecionar)

Não existem fornecedores de PowerShell estão disponíveis, nem são que programas de qualquer externo (executáveis, scripts, etc.).

Existem vários outros campos que pretende configurar para a sessão JEA.
Eles são abordados nas seções a seguir.

### <a name="choose-the-jea-identity"></a>Escolha a identidade JEA

Em segundo plano, JEA tem uma identidade (conta) para utilizar durante a execução de comandos de um usuário conectado.
Decide que identidade JEA irá utilizar no ficheiro de configuração de sessão.

#### <a name="local-virtual-account"></a>Conta Virtual local

Se as funções suportadas por este ponto final da JEA são utilizadas para gerir a máquina local e uma conta de administrador local é suficiente para executar o comandos foi com êxito, deve configurar JEA para utilizar uma conta virtual local.
Contas virtuais são contas temporárias que são exclusivas para um utilizador específico e apenas os últimos durante a sessão do PowerShell.
Num servidor membro ou estação de trabalho, contas virtuais pertencem ao computador local **administradores** agrupar e ter acesso a maioria dos recursos do sistema.
Num controlador de domínio do Active Directory, contas virtuais pertencem ao domínio **Admins do domínio** grupo.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Se as funções com suporte a configuração de sessão não necessitar desses privilégios amplo, opcionalmente, pode especificar os grupos de segurança para o qual irá pertencer a conta virtual.
Num servidor membro ou estação de trabalho, os grupos de segurança especificado tem de ser grupos locais, não os grupos de um domínio.

Quando é especificado um ou mais grupos de segurança, a conta virtual já não irão pertencer ao grupo de administradores locais ou de domínio.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a>Conta de Serviço Gerida de Grupo


Para cenários de exigir que o utilizador JEA para aceder aos recursos de rede, tais como outras máquinas ou serviços da web, uma conta de serviço geridas de grupo (gMSA) é uma identidade mais adequada para utilizar.
contas de gMSA dão-lhe uma identidade de domínio que pode ser utilizada para autenticar em recursos em qualquer computador no domínio.
Os direitos a oferece de conta gMSA é determinado pelos recursos que está a aceder.
Não terão automaticamente os direitos de administrador em qualquer máquinas ou serviços, a menos que o administrador de serviço/machine concedeu explicitamente a conta gMSA privilégios de administrador.

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

contas de gMSA só devem ser utilizadas quando o acesso a recursos de rede são necessários para alguns dos motivos:

- É mais difícil de efectuar o rastreio ações para um utilizador ao utilizar uma conta gMSA, uma vez que cada usuário compartilha a mesma identidade Run. Precisará consultar transcrições de sessão do PowerShell e registos para correlacionar os utilizadores com as suas ações.

- A conta gMSA pode ter acesso a vários recursos de rede que o usuário conectado não precisam de acesso a. Sempre tente limitar as permissões efetivas numa sessão JEA para acompanhar o princípio de privilégio mínimo.

> [!NOTE]
> Contas de serviço geridas de grupo só estão disponíveis no Windows PowerShell 5.1 ou mais recente e em computadores associados a um domínio.


#### <a name="more-information-about-run-as-users"></a>Obter mais informações sobre a execução como usuários

Pode encontrar informações adicionais sobre a execução como identidades e como eles fatorar em segurança de uma sessão JEA no [considerações de segurança](security-considerations.md) artigo.

### <a name="session-transcripts"></a>Transcrições de sessão

Recomenda-se que configure um ficheiro de configuração de sessão JEA para transcrições automaticamente registos de sessões dos utilizadores.
Transcrições de sessão do PowerShell contêm informações sobre o usuário conectado, a execução como identidade atribuída, e os comandos são executados pelo utilizador.
Eles podem ser úteis para uma equipe de auditoria que precisa entender quem efetuou uma alteração específica para um sistema.

Para configurar a transcrição automática no ficheiro de configuração de sessão, forneça um caminho para uma pasta onde as transcrições devem ser armazenadas.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

A pasta especificada deve ser configurada para impedir que os usuários modifiquem ou eliminem dados na mesma.
Transcrições são escritas para a pasta por conta do sistema Local, o que requer a leitura e de acesso de escrita para o diretório.
Os usuários padrão não devem ter acesso à pasta e um conjunto limitado de administradores de segurança deve ter acesso ao auditar as transcrições.

### <a name="user-drive"></a>Unidade de utilizador

Se os utilizadores de ligação terá de copiar ficheiros de/para o ponto final da JEA para executar um comando, pode ativar a unidade de utilizador no ficheiro de configuração de sessão.
A unidade de utilizador é um [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) que está mapeado para uma pasta exclusiva para cada usuário conectado.
Esta pasta serve como um espaço para os mesmos copiar ficheiros de/para o sistema, sem conceder acesso ao sistema de ficheiros completa ou expor o fornecedor do sistema de ficheiros.
O conteúdo da unidade de utilizador é persistente entre sessões para acomodar as situações em que a conectividade de rede pode ser interrompida.

```powershell
MountUserDrive = $true
```

Por predefinição, a unidade de utilizador permite-lhe armazenar um máximo de 50MB de dados por utilizador.
Pode limitar a quantidade de dados de um utilizador pode consumir com o *UserDriveMaximumSize* campo.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Se não pretender que os dados na unidade do utilizador para ser persistente, pode configurar uma tarefa agendada no sistema para limpar automaticamente a pasta de todas as noites.

> [!NOTE]
> A unidade de utilizador só está disponível no Windows PowerShell 5.1 ou mais recente.

### <a name="role-definitions"></a>Definições de funções

Definições de funções num arquivo de configuração de sessão definem o mapeamento dos *usuários* ao *funções*.
Cada utilizador ou grupo incluído neste campo receberá automaticamente permissão para o ponto final da JEA quando é registado.
Cada utilizador ou grupo pode ser incluído como uma chave da tabela de hash apenas uma vez, mas pode ser atribuído várias funções.
O nome da capacidade de função deve ser o nome do arquivo de recurso de função, sem a extensão de .psrc.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Se um utilizador pertencer a mais de um grupo na definição de função, obterá acesso às funções de cada.
Se duas funções de concedem acesso para os mesmos cmdlets, o conjunto de parâmetros mais permissivo será concedido ao utilizador.

Ao especificar grupos de utilizadores ou no campo de definições de função, certifique-se de que utiliza o nome do computador (não *localhost* ou *.*) antes da barra invertida.
Pode verificar o nome do computador ao inspecionar o `$env:computername` variável.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Ordem de pesquisa de capacidade de função
Conforme mostrado no exemplo acima, as funcionalidades de função são referenciadas pelo nome simples (nome de ficheiro sem a extensão) do arquivo de recurso de função.
Se várias funcionalidades de função estão disponíveis no sistema com o mesmo nome simples, o PowerShell irá utilizar sua ordem de pesquisa implícito para selecionar o ficheiro de recurso de função em vigor.
Ele será **não** conceder acesso a todos os ficheiros de recurso de função com o mesmo nome.

JEA utiliza o `$env:PSModulePath` variável de ambiente para determinar os caminhos para verificar a existência de arquivos de recurso de função.
Dentro de cada um desses caminhos, JEA irá procurar válidos módulos do PowerShell que contêm uma subpasta do "RoleCapabilities".
Tal como acontece com a importação de módulos JEA prefere funcionalidades de função que são fornecidas com o Windows às capacidades de função personalizada com o mesmo nome.
Para todos os outros conflitos de nomenclatura, a precedência é determinada pela ordem em que o Windows enumera os ficheiros no diretório (não garantida que ser por ordem alfabética).
O primeiro arquivo de recurso de função encontrado que corresponda ao desejada nome será utilizado para o usuário conectado.

Uma vez que a ordem de pesquisa de capacidade de função não é determinística quando dois ou mais funcionalidades de função partilham o mesmo nome, é **vivamente recomendado** que é garantir que os recursos de função têm nomes exclusivos no seu computador.

### <a name="conditional-access-rules"></a>Regras de acesso condicional

Todos os utilizadores e grupos incluídos no campo RoleDefinitions recebem automaticamente acesso a pontos finais JEA.
Regras de acesso condicional permitem-lhe refinar este acesso e exigir que os utilizadores pertencem a grupos de segurança adicionais que não afetam as funções que estão atribuídos.
Isso pode ser útil se pretender integrar um "apenas no tempo" privilegiado aceder a solução de gestão, autenticação de smart card ou outra solução de autenticação multifator com JEA.

Regras de acesso condicional são definidas no campo RequiredGroups num arquivo de configuração de sessão.
Lá, pode fornecer uma tabela de hash (opcionalmente aninhada) que utiliza "E" e "Ou" chaves para construir as suas regras.
Aqui estão alguns exemplos de como tirar partido deste campo:

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
> Regras de acesso condicional só estão disponíveis no Windows PowerShell 5.1 ou mais recente.

### <a name="other-properties"></a>Outras propriedades
Ficheiros de configuração de sessão também podem fazer tudo o que um arquivo de recurso de função pode fazer, basta sem a capacidade de conceder o acesso de utilizadores ao ligar a comandos diferentes.
Se quiser permitir aos utilizadores acesso a cmdlets específicos, funções ou os fornecedores, pode fazê-lo diretamente no ficheiro de configuração de sessão.
Para obter uma lista completa de propriedades suportadas no ficheiro de configuração de sessão, execute `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Teste de um ficheiro de configuração de sessão

Pode testar uma configuração de sessão através da [teste PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.
É altamente recomendável que teste seu arquivo de configuração de sessão se editou o ficheiro de pssc manualmente usando um editor de texto para verificar que a sintaxe está correta.
Se um ficheiro de configuração de sessão não passam no teste, não será capaz de ser registado com êxito no sistema.

## <a name="sample-session-configuration-file"></a>Ficheiro de configuração de sessão de exemplo

Segue-se um exemplo completo que mostra como criar e validar uma configuração de sessão para JEA.
Tenha em atenção que as definições de funções são criadas e armazenadas no `$roles` variável por conveniência e legibilidade.
Não é um requisito para fazer isso.

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

Se precisar de alterar propriedades de uma configuração de sessão JEA, incluindo o mapeamento de utilizadores às funções, deve [anular o registo](register-jea.md#unregistering-jea-configurations) e [voltar a registar](register-jea.md) a configuração de sessão JEA.
Quando voltar a registar a configuração de sessão JEA, utilize um ficheiro de configuração sessão atualizado PowerShell inclui as alterações necessárias.

## <a name="next-steps"></a>Próximos passos

- [Registe-se de uma configuração de JEA](register-jea.md)
- [Funções JEA do autor](role-capabilities.md)