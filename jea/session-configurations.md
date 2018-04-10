---
ms.date: 06/12/2017
author: rpsqrd
ms.topic: conceptual
keywords: jea, powershell, segurança
title: Configurações de sessão JEA
ms.openlocfilehash: 317a549ed20b5800d5bafdabd266e93ba7cd321c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="jea-session-configurations"></a>Configurações de sessão JEA

> Aplica-se a: Windows PowerShell 5.0

Um ponto final JEA é registado num sistema através da criação e registar um ficheiro de configuração de sessão do PowerShell de uma forma específica.
Determinam as configurações de sessão *quem* pode utilizar o ponto final JEA, e que funções selecionadas terão acesso a.
Também definem as definições globais que se aplicam aos utilizadores de qualquer função na sessão JEA.

Este tópico descreve como criar um ficheiro de configuração de sessão do PowerShell e registar um ponto final JEA.

## <a name="create-a-session-configuration-file"></a>Criar um ficheiro de configuração de sessão

Para registar um ponto final JEA, terá de especificar a forma como esse ponto final deve ser configurado.
Existem muitas opções a considerar aqui, o mais importante do que a ser que devem ter acesso ao ponto final do JEA, que funções vão ser atribuídos, que identity JEA utilizará nos bastidores, e o que será o nome do ponto final JEA.
Estes estão todas definidas num ficheiro de configuração de sessão do PowerShell, que é um ficheiro de dados do PowerShell que termina com uma extensão de .pssc.

Para criar um ficheiro de configuração de sessão de estrutura para pontos finais JEA, execute o seguinte comando.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Por predefinição, apenas as opções mais comuns de configuração estão incluídas no ficheiro de estrutura.
> Utilize o `-Full` comutador para incluir todas as definições aplicáveis no PSSC gerado.

Pode abrir o ficheiro de configuração de sessão em qualquer editor de texto.
O `-SessionType RestrictedRemoteServer` campo indica que a configuração de sessão será utilizada pelo JEA para gestão segura.
Sessões configuradas desta forma irão funcionar no [NoLanguage modo](https://technet.microsoft.com/library/dn433292.aspx) e conter apenas os seguintes comandos de 8 predefinida (e aliases) disponíveis:

- Desmarque-Host (conformidade com cls, desmarque)
- Sair-PSSession (exsn, saída)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Objeto de medida (medidas)
- Out-predefinido
- Select-Object (selecionar)

Não existem fornecedores de PowerShell estão disponíveis nem são que programas de qualquer externo (executáveis, scripts, etc.).

Existem vários outros campos que pretende configurar para a sessão JEA.
Estes são abordadas nas secções seguintes.

### <a name="choose-the-jea-identity"></a>Escolha a identidade JEA

Nos bastidores, JEA tem uma identidade (conta) para utilizar durante a execução de comandos de um utilizador ligado.
Decida qual identidade JEA irá utilizar no ficheiro de configuração de sessão.

#### <a name="local-virtual-account"></a>Conta Virtual local

Se as funções suportadas por este ponto final JEA são utilizadas para gerir o computador local e uma conta de administrador local é suficiente para executar o com êxito de comandos, deve configurar JEA para utilizar uma conta virtual local.
As contas virtuais têm temporária que são exclusivas para um utilizador específico e apenas os últimos durante a sessão do PowerShell.
Num servidor membro ou estação de trabalho, as contas virtual pertencerem no computador local **administradores** agrupar e tem acesso a maioria dos recursos do sistema.
Num controlador de domínio do Active Directory, as contas virtual pertencerem para o domínio **Admins do domínio** grupo.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Se as funções suportadas na configuração da sessão não necessitam desses privilégios abrangentes, opcionalmente, pode especificar os grupos de segurança para que a conta virtual irá pertencer.
Num servidor membro ou estação de trabalho, os grupos de segurança especificado tem de ser grupos locais, não os grupos de um domínio.

Quando um ou mais grupos de segurança for especificado, a conta virtual já não irão pertencer ao grupo de administradores local ou domínio.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a>Conta de Serviço Gerida de Grupo


Para cenários que requerem o utilizador JEA para aceder a recursos de rede, tais como outras máquinas ou serviços web, uma conta de serviço geridas de grupo (gMSA) é uma identidade de mais adequada para utilizar.
contas de gMSA dão-lhe uma identidade de domínio que pode ser utilizada para autenticar relativamente aos recursos em qualquer máquina dentro do domínio.
Os direitos fornecem de conta gMSA é determinado pelos recursos está a aceder.
Não automaticamente tem direitos de administrador em qualquer máquinas ou serviços, a menos que o administrador de serviço de machine/concedeu explicitamente a conta gMSA privilégios de administrador.

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

contas de gMSA só devem ser utilizadas quando o acesso a recursos de rede são necessários para algumas razões:

- É harder efectuar o rastreio ações para um utilizador ao utilizar uma conta de gMSA, uma vez que todos os utilizadores partilham a mesma identidade de executar como. Terá de consulte os registos para correlacionar os utilizadores com as respetivas ações e transcrições de sessão do PowerShell.

- A conta de gMSA poderá ter acesso a vários recursos de rede que o utilizador de ligação não necessitam de aceder a. Tente sempre limitar as permissões efetivas numa sessão JEA a seguir o princípio do menor privilégio.

> [!NOTE]
> Contas de serviço geridas de grupo só estão disponíveis no Windows PowerShell 5.1 ou mais recente e, em computadores associados a um domínio.


#### <a name="more-information-about-run-as-users"></a>Mais informações sobre como executar como os utilizadores

Informações adicionais sobre executados como identidades e como de fator para a segurança de uma sessão JEA podem ser encontradas no [considerações de segurança](security-considerations.md) artigo.

### <a name="session-transcripts"></a>Transcrições de sessão

Recomenda-se que configure um ficheiro de configuração de sessão JEA para transcrições automaticamente registos de sessões dos utilizadores.
Transcrições de sessão do PowerShell contêm informações sobre o utilizador de ligação, a run as atribuída, de identidade e os comandos são executados pelo utilizador.
Podem ser úteis para uma equipa de auditoria que precise de compreender quem efetuou uma alteração a um sistema específico.

Para configurar transcription automática no ficheiro de configuração de sessão, forneça um caminho para uma pasta onde as transcrições devem ser armazenadas.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

A pasta especificada deve ser configurada para impedir que utilizadores modificar ou eliminar quaisquer dados no mesmo.
Transcrições são escritas para a pasta pela conta de sistema Local, o que requer a leitura e de acesso de escrita ao diretório.
Utilizadores padrão devem ter sem acesso à pasta e um conjunto limitado de administradores de segurança deve ter acesso para as transcrições de auditoria.

### <a name="user-drive"></a>Unidade de utilizador

Se os utilizadores de ligação terá de copiar ficheiros para/a partir do ponto final JEA para executar um comando, pode ativar a unidade de utilizador no ficheiro de configuração de sessão.
A unidade de utilizador é um [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) que está mapeado para uma pasta exclusiva para cada utilizador de ligação.
Esta pasta serve como um espaço para os mesmos copiar ficheiros para/a partir do sistema, sem conceder acesso ao sistema de ficheiros completo ou expor o fornecedor do sistema de ficheiros.
O conteúdo de unidade do utilizador sejam persistente nos sessões para acomodar situações em que a conectividade de rede pode ser interrompida.

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

Se não pretender que os dados na unidade de utilizador para ser persistente, pode configurar uma tarefa agendada no sistema automaticamente limpar a pasta cada noite.

> [!NOTE]
> A unidade de utilizador só está disponível no Windows PowerShell 5.1 ou mais recente.

### <a name="role-definitions"></a>Definições de função

Definições de funções num ficheiro de configuração de sessão definem o mapeamento do *utilizadores* para *funções*.
Cada utilizador ou grupo incluídos neste campo será automaticamente ser concedido permissão para o ponto final JEA quando é registado.
Cada utilizador ou grupo pode ser incluído como uma chave na tabela hash de uma só vez, mas pode ser atribuído várias funções.
O nome da capacidade de função deve ser o nome do ficheiro de capacidade de função, sem a extensão de .psrc.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Se um utilizador pertence a mais do que um grupo na definição de função, que irão obter acesso às funções de cada.
Se duas funções de conceder acesso aos cmdlets do mesmos, o conjunto de parâmetros mais permissivo será concedido ao utilizador.

Ao especificar grupos ou utilizadores locais no campo de definições de função, não se esqueça de utilizar o nome do computador (não *localhost* ou *.*) antes da barra invertida.
Pode verificar o nome do computador inspecionando a `$env:computername` variável.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Ordem de pesquisa de capacidade de função
Como é mostrado no exemplo acima, as capacidades de função são referenciadas por nome simples (nome de ficheiro sem a extensão) do ficheiro de capacidade de função.
Se várias capacidades de função estão disponíveis no sistema com o mesmo nome simples, o PowerShell irá utilizar a ordem de pesquisa implícito para selecionar o ficheiro de capacidade de função Efetivo.
Este irá **não** conceder acesso a todos os ficheiros de capacidade de função com o mesmo nome.

JEA utiliza o `$env:PSModulePath` variável de ambiente para determinar os caminhos para procurar ficheiros de capacidade de função.
Dentro de cada um desses caminhos, irá procurar JEA válidos módulos do PowerShell que contém uma subpasta "RoleCapabilities".
Tal como com a importação de módulos, JEA prefers capacidades de função que são fornecidas com o Windows para capacidades de função personalizada com o mesmo nome.
Para todos os outros conflitos de nomenclatura, precedência é determinada pela ordem em que o Windows enumera os ficheiros no diretório (não garantido estar por ordem alfabética).
O primeiro ficheiro de capacidade de função encontrado que corresponda à pretendido nome será utilizado para o utilizador ao ligar.

Uma vez que a ordem de pesquisa de capacidade de função não é determinística quando duas ou mais capacidades de função partilham o mesmo nome, é **vivamente** assegurar as capacidades de função têm nomes exclusivos no seu computador.

### <a name="conditional-access-rules"></a>Regras de acesso condicional

Todos os utilizadores e grupos incluídos no campo RoleDefinitions automaticamente são concedidos acesso aos pontos finais JEA.
Regras de acesso condicional permitem-lhe refinar este acesso e exigir que os utilizadores pertencem a grupos de segurança adicional que não afetam as funções que estão atribuídos.
Isto pode ser útil se pretender integrar uma "apenas no tempo" privilegiado aceder à solução de gestão, a autenticação de smart card ou outra solução de autenticação multifator com JEA.

Regras de acesso condicional são definidas no campo RequiredGroups um ficheiro de configuração de sessão.
Aqui, pode fornecer uma tabela hash (opcionalmente aninhada) que utiliza 'E' e 'Ou' chaves construir as regras.
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

> [!NOTE]
> Regras de acesso condicional só estão disponíveis no Windows PowerShell 5.1 ou mais recente.

### <a name="other-properties"></a>Outras propriedades
Ficheiros de configuração de sessão também podem fazer tudo que um ficheiro de capacidade de função pode fazer, basta sem a capacidade de conceder acesso de utilizadores ligados a diferentes comandos.
Se pretende permitir acesso a cmdlets específicos, funções ou fornecedores de todos os utilizadores, pode fazê-diretamente no ficheiro de configuração de sessão.
Para obter uma lista completa de propriedades suportadas no ficheiro de configuração de sessão, execute `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Testar um ficheiro de configuração de sessão

Pode testar uma configuração de sessão utilizando o [teste PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.
Recomenda-se vivamente que teste o ficheiro de configuração de sessão se tiver editado o ficheiro de pssc manualmente utilizando um editor de texto para garantir a sintaxe correta.
Se um ficheiro de configuração de sessão não obtiver este teste, não será capaz de ser registado com êxito no sistema.

## <a name="sample-session-configuration-file"></a>Ficheiro de configuração de sessão de exemplo

Abaixo está um exemplo completo que mostra como criar e validar uma configuração de sessão para JEA.
Tenha em atenção que as definições de função são criadas e armazenadas no `$roles` variável por conveniência e o facilitar a leitura.
Não é um requisito para tal.

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a>Atualizar os ficheiros de configuração de sessão

Se precisar de alterar propriedades de uma configuração de sessão JEA, incluindo o mapeamento de utilizadores a funções, deve [anular o registo](register-jea.md#unregistering-jea-configurations) e [voltar a registar](register-jea.md) a configuração de sessão JEA.
Quando voltar a registar a configuração de sessão JEA, utilize um ficheiro de configuração sessão atualizado PowerShell inclui as alterações pretendidas.

## <a name="next-steps"></a>Próximos passos

- [Registar uma configuração de JEA](register-jea.md)
- [Funções JEA do autor](role-capabilities.md)