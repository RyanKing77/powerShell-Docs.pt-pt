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
# <a name="jea-session-configurations"></a>Configurações de sessão JEA

Um ponto de extremidade JEA é registrado em um sistema criando e registrando um arquivo de configuração de sessão do PowerShell. As configurações de sessão definem quem pode usar o ponto de extremidade JEA e a quais funções elas têm acesso. Eles também definem as configurações globais que se aplicam a todos os usuários da sessão JEA.

## <a name="create-a-session-configuration-file"></a>Criar um arquivo de configuração de sessão

Para registrar um ponto de extremidade JEA, você deve especificar como esse ponto de extremidade é configurado. Há muitas opções a serem consideradas. As opções mais importantes são:

- Quem tem acesso ao ponto de extremidade JEA
- Quais funções eles são atribuídas
- Qual identidade JEA usa nos bastidores
- O nome do ponto de extremidade JEA

Essas opções são definidas em um arquivo de dados do PowerShell `.pssc` com uma extensão conhecida como um arquivo de configuração de sessão do PowerShell. O arquivo de configuração de sessão pode ser editado usando qualquer editor de texto.

Execute o comando a seguir para criar um arquivo de configuração de modelo em branco.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Somente as opções de configuração mais comuns são incluídas no arquivo de modelo por padrão. Use a `-Full` opção para incluir todas as configurações aplicáveis no PSSC gerado.

O `-SessionType RestrictedRemoteServer` campo indica que a configuração de sessão é usada pelo Jea para gerenciamento seguro. As sessões desse tipo operam no modo nolanguage e só têm acesso aos seguintes comandos padrão (e aliases):

- Clear – host (CLS, Clear)
- Exit-PSSession (exsn, sair)
- Get-Command (GCM)
- Get-FormatData
- Obter ajuda
- Measure-Object (medida)
- Out-padrão
- Select-Object (selecionar)

Nenhum provedor do PowerShell está disponível, nem todos os programas externos (executáveis ou scripts).

Para obter mais informações sobre modos de linguagem, consulte [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).

### <a name="choose-the-jea-identity"></a>Escolha a identidade JEA

Nos bastidores, o JEA precisa de uma identidade (conta) para usar ao executar os comandos de um usuário conectado.
Você define qual identidade JEA usa no arquivo de configuração de sessão.

#### <a name="local-virtual-account"></a>Conta virtual local

As contas virtuais locais são úteis quando todas as funções definidas para o ponto de extremidade JEA são usadas para gerenciar o computador local e uma conta de administrador local é suficiente para executar os comandos com êxito.
As contas virtuais são contas temporárias que são exclusivas para um usuário específico e são apenas por último pela duração de sua sessão do PowerShell. Em um servidor membro ou estação de trabalho, as contas virtuais pertencem ao grupo **Administradores** do computador local. Em um controlador de Domínio do Active Directory, as contas virtuais pertencem ao grupo **Admins** . do domínio do domínio.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Se as funções definidas pela configuração de sessão não exigirem privilégio administrativo completo, você poderá especificar os grupos de segurança aos quais a conta virtual pertencerá. Em um servidor membro ou estação de trabalho, os grupos de segurança especificados devem ser grupos locais, não grupos de um domínio.

Quando um ou mais grupos de segurança são especificados, a conta virtual não é atribuída ao grupo de administradores de domínio ou local.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> As contas virtuais recebem temporariamente o direito de logon como um serviço na política de segurança do servidor local. Se um dos VirtualAccountGroups especificado já tiver sido concedido a esse direito na política, a conta virtual individual não será mais adicionada e removida da política. Isso pode ser útil em cenários como controladores de domínio em que as revisões para a diretiva de segurança do controlador de domínio são rigorosamente auditadas. Isso só está disponível no Windows Server 2016 com o rollup de novembro de 2018 ou posterior e o Windows Server 2019 com o rollup de janeiro de 2019 ou posterior.

#### <a name="group-managed-service-account"></a>Grupo-conta de serviço gerenciado

Uma conta de serviço gerenciado por grupo (GMSA) é a identidade apropriada a ser usada quando os usuários do JEA precisam acessar recursos de rede, como compartilhamentos de arquivos e serviços Web. GMSAs fornece uma identidade de domínio que é usada para autenticar com recursos em qualquer computador dentro do domínio. Os direitos que um GMSA fornece são determinados pelos recursos que você está acessando. Você não tem direitos de administrador em nenhum computador ou serviço, a menos que o administrador de computador ou serviço tenha concedido explicitamente esses direitos ao GMSA.

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

GMSAs só deve ser usado quando necessário:

- É difícil rastrear ações de back para um usuário ao usar um GMSA. Cada usuário compartilha a mesma identidade de execução como. Você deve examinar os logs e transcrições de sessão do PowerShell para correlacionar usuários individuais com suas ações.

- O GMSA pode ter acesso a vários recursos de rede aos quais o usuário que está se conectando não precisa acessar. Sempre tente limitar as permissões efetivas em uma sessão JEA para seguir o princípio de privilégios mínimos.

> [!NOTE]
> Contas de serviço gerenciado de grupo só estão disponíveis em computadores ingressados no domínio usando o PowerShell 5,1 ou mais recente.

Para obter mais informações sobre como proteger uma sessão do JEA, consulte o artigo [Considerações sobre segurança](security-considerations.md) .

### <a name="session-transcripts"></a>Transcrições de sessão

É recomendável que você configure um ponto de extremidade JEA para registrar automaticamente transcrições de sessões de usuários. As transcrições de sessão do PowerShell contêm informações sobre o usuário que está se conectando, a identidade executar como atribuída a eles e os comandos executados pelo usuário. Eles podem ser úteis para uma equipe de auditoria que precisa entender quem fez uma alteração específica em um sistema.

Para configurar a transcrição automática no arquivo de configuração de sessão, forneça um caminho para uma pasta onde as transcrições devem ser armazenadas.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

As transcrições são gravadas na pasta pela conta do **sistema local** , o que exige acesso de leitura e gravação ao diretório. Os usuários padrão não devem ter acesso à pasta. Limite o número de administradores de segurança que têm acesso para auditar as transcrições.

### <a name="user-drive"></a>Unidade do usuário

Se os usuários que estão se conectando precisarem copiar arquivos de ou para o ponto de extremidade JEA, você poderá habilitar a unidade de usuário no arquivo de configuração de sessão. A unidade do usuário é uma **PSDrive** que é mapeada para uma pasta exclusiva para cada usuário que está se conectando. Essa pasta permite que os usuários copiem arquivos de ou para o sistema sem conceder a eles acesso ao sistema de arquivos completo ou expondo o provedor FileSystem. O conteúdo da unidade do usuário é persistente entre as sessões para acomodar situações em que a conectividade de rede pode ser interrompida.

```powershell
MountUserDrive = $true
```

Por padrão, a unidade de usuário permite que você armazene um máximo de 50 MB de dados por usuário. Você pode limitar a quantidade de dados que um usuário pode consumir com o campo *UserDriveMaximumSize* .

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Se não quiser que os dados na unidade de usuário sejam persistentes, você poderá configurar uma tarefa agendada no sistema para limpar automaticamente a pasta todas as noites.

> [!NOTE]
> A unidade de usuário só está disponível no PowerShell 5,1 ou mais recente.

Para obter mais informações sobre PSDrives, consulte [gerenciando unidades do PowerShell](/powershell/scripting/samples/managing-windows-powershell-drives).

### <a name="role-definitions"></a>Definições de função

As definições de função em um arquivo de configuração de sessão definem o mapeamento de **usuários** para **funções**. Cada usuário ou grupo incluído nesse campo recebe permissão para o ponto de extremidade JEA quando registrado.
Cada usuário ou grupo pode ser incluído como uma chave na tabela de hash apenas uma vez, mas pode ser atribuído a várias funções. O nome da capacidade de função deve ser o nome do arquivo de capacidade de função, sem `.psrc` a extensão.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Se um usuário pertencer a mais de um grupo na definição de função, ele obterá acesso às funções de cada um. Quando duas funções concedem acesso aos mesmos cmdlets, o conjunto de parâmetros mais permissivos é concedido ao usuário.

Ao especificar usuários ou grupos locais no campo definições de função, certifique-se de usar o nome do computador, não **localhost** ou curingas. Você pode verificar o nome do computador inspecionando a `$env:COMPUTERNAME` variável.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Ordem de pesquisa de capacidade de função

Conforme mostrado no exemplo acima, os recursos de função são referenciados pelo nome base do arquivo de capacidade de função. O nome de base de um arquivo é o FileName sem a extensão. Se houver vários recursos de função disponíveis no sistema com o mesmo nome, o PowerShell usará sua ordem de pesquisa implícita para selecionar o arquivo de capacidade de função efetivo. JEA **não** dá acesso a todos os arquivos de capacidade de função com o mesmo nome.

Jea usa a `$env:PSModulePath` variável de ambiente para determinar quais caminhos verificar para arquivos de capacidade de função. Dentro de cada um desses caminhos, JEA procura módulos válidos do PowerShell que contenham uma subpasta "RoleCapabilities". Assim como acontece com a importação de módulos, o JEA prefere recursos de função que são fornecidos com o Windows para recursos de função personalizados com o mesmo nome.

Para todos os outros conflitos de nomenclatura, a precedência é determinada pela ordem em que o Windows enumera os arquivos no diretório. Não há garantia de que a ordem seja alfabética. O primeiro arquivo de capacidade de função encontrado que corresponde ao nome especificado é usado para o usuário que está se conectando. Como a ordem de pesquisa de capacidade de função não é determinística, é **altamente recomendável** que os recursos de função tenham nomes de um único.

### <a name="conditional-access-rules"></a>Regras de acesso condicional

Todos os usuários e grupos incluídos no campo **RoleDefinitions** recebem acesso automaticamente aos pontos de extremidade Jea. As regras de acesso condicional permitem que você refine esse acesso e exija que os usuários pertençam a grupos de segurança adicionais que não afetam as funções às quais estão atribuídos. Isso é útil quando você deseja integrar uma solução de gerenciamento de acesso privilegiado just-in-time, autenticação de cartão inteligente ou outra solução de autenticação multifator com JEA.

As regras de acesso condicional são definidas no campo RequiredGroups em um arquivo de configuração de sessão.
Lá, você pode fornecer uma tabela de hash (opcionalmente aninhada) que usa as chaves ' and ' e ' or ' para construir suas regras. Aqui estão alguns exemplos de como usar este campo:

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
> As regras de acesso condicional estão disponíveis somente no PowerShell 5,1 ou mais recente.

### <a name="other-properties"></a>Outras propriedades

Os arquivos de configuração de sessão também podem fazer tudo o que um arquivo de capacidade de função pode fazer, apenas sem a capacidade de conceder acesso aos usuários a comandos diferentes. Se você quiser permitir que todos os usuários acessem cmdlets, funções ou provedores específicos, você pode fazer isso diretamente no arquivo de configuração de sessão.
Para obter uma lista completa das propriedades com suporte no arquivo de configuração de `Get-Help New-PSSessionConfigurationFile -Full`sessão, execute.

## <a name="testing-a-session-configuration-file"></a>Testando um arquivo de configuração de sessão

Você pode testar uma configuração de sessão usando o cmdlet [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) . É recomendável que você teste seu arquivo de configuração de sessão se tiver editado `.pssc` manualmente o arquivo. O teste garante que a sintaxe esteja correta. Se um arquivo de configuração de sessão falhar nesse teste, ele não poderá ser registrado no sistema.

## <a name="sample-session-configuration-file"></a>Arquivo de configuração de sessão de exemplo

O exemplo a seguir mostra como criar e validar uma configuração de sessão para JEA. As definições de função são criadas e armazenadas na `$roles` variável para conveniência e legibilidade. Não é um requisito para isso.

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a>Atualizando arquivos de configuração de sessão

Para alterar as propriedades de uma configuração de sessão JEA, incluindo o mapeamento de usuários para funções, você deve [cancelar o registro](register-jea.md#unregistering-jea-configurations). Em seguida, [Registre novamente](register-jea.md) a configuração de sessão Jea usando um arquivo de configuração de sessão atualizado.

## <a name="next-steps"></a>Passos Seguintes

- [Registrar uma configuração do JEA](register-jea.md)
- [Criar funções JEA](role-capabilities.md)
