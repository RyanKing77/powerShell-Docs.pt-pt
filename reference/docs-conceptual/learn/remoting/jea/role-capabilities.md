---
ms.date: 07/10/2019
keywords: Jea, PowerShell, segurança
title: Recursos de função JEA
ms.openlocfilehash: 7191b90e198ffb539da6870a8ddc3e449ad9e8ae
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017959"
---
# <a name="jea-role-capabilities"></a>Recursos de função JEA

Ao criar um ponto de extremidade JEA, você precisa definir um ou mais recursos de função que descrevem o que alguém pode fazer em uma sessão JEA. Uma capacidade de função é um arquivo de dados do `.psrc` PowerShell com a extensão que lista todos os cmdlets, funções, provedores e programas externos que são disponibilizados para conectar usuários.

## <a name="determine-which-commands-to-allow"></a>Determinar quais comandos permitir

A primeira etapa na criação de um arquivo de capacidade de função é considerar o que os usuários precisam acessar. O processo de coleta de requisitos pode demorar um pouco, mas é um processo importante. Conceder aos usuários acesso a poucos cmdlets e funções pode impedi-los de realizar seu trabalho. Permitir acesso a muitos cmdlets e funções pode permitir que os usuários façam mais do que você pretendia e enfraquecem sua postura de segurança.

O modo como você vai para esse processo depende de sua organização e metas. As dicas a seguir podem ajudar a garantir que você esteja no caminho certo.

1. **Identifique** os comandos que os usuários estão usando para fazer seus trabalhos. Isso pode envolver a pesquisa da equipe de ti, a verificação de scripts de automação ou a análise de logs e transcrições de sessão do PowerShell.
2. **Atualize** o uso de ferramentas de linha de comando para equivalentes do PowerShell, sempre que possível, para obter a melhor experiência de auditoria e de personalização de Jea. Os programas externos não podem ser restritos de forma granular como cmdlets e funções nativos do PowerShell no JEA.
3. **Restrinja** o escopo dos cmdlets para permitir apenas parâmetros específicos ou valores de parâmetro. Isso é especialmente importante se os usuários devem gerenciar apenas parte de um sistema.
4. **Crie** funções personalizadas para substituir comandos complexos ou comandos que são difíceis de restringir em Jea. Uma função simples que encapsula um comando complexo ou aplica uma lógica de validação adicional pode oferecer controle adicional aos administradores e à simplicidade do usuário final.
5. **Teste** a lista com escopo de comandos permitidos com seus usuários ou serviços de automação e ajuste conforme necessário.

### <a name="examples-of-potentially-dangerous-commands"></a>Exemplos de comandos potencialmente perigosos

A seleção cuidadosa de comandos é importante para garantir que o ponto de extremidade JEA não permita que o usuário eleve suas permissões.

> [!IMPORTANT]
> As informações essenciais necessárias para successCommands de usuário em uma sessão JEA geralmente são executadas com privilégios elevados.

A tabela a seguir contém exemplos de comandos que podem ser usados de forma mal-intencionada, se permitido em um estado irrestrito. Essa não é uma lista exaustiva e só deve ser usada como ponto de partida preventiva.

|                                            Risco                                            |                                Exemplo                                |                                                                              Comandos relacionados                                                                              |
| ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Concedendo privilégios de administrador de usuário que se conecta para ignorar JEA                                | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`                                                                                                        |
| Executando código arbitrário, como malware, explorações ou scripts personalizados para ignorar as proteções | `Start-Process -FilePath '\\san\share\malware.exe'`                   | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob` |

## <a name="create-a-role-capability-file"></a>Criar um arquivo de capacidade de função

Você pode criar um novo arquivo de capacidade de função do PowerShell com o cmdlet [New-PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-6) .

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

O arquivo de capacidade de função resultante deve ser editado para permitir os comandos necessários para a função. A documentação de ajuda do PowerShell contém vários exemplos de como você pode configurar o arquivo.

### <a name="allowing-powershell-cmdlets-and-functions"></a>Permitindo cmdlets e funções do PowerShell

Para autorizar os usuários a executarem cmdlets ou funções do PowerShell, adicione o cmdlet ou o nome da função aos campos VisibleCmdlets ou VisibleFunctions. Se você não tiver certeza se um comando é um cmdlet ou uma função, poderá `Get-Command <name>` executar e verificar a propriedade **CommandType** na saída.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Às vezes, o escopo de um cmdlet ou função específica é muito amplo para as necessidades dos usuários. Um administrador de DNS, por exemplo, provavelmente precisa apenas de acesso para reiniciar o serviço DNS. Em ambientes multilocatários, os locatários têm acesso a ferramentas de gerenciamento de autoatendimento. Os locatários devem ser limitados ao gerenciamento de seus próprios recursos. Nesses casos, você pode restringir quais parâmetros são expostos do cmdlet ou da função.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}
```

Em cenários mais avançados, talvez você também precise restringir os valores que um usuário pode usar com esses parâmetros. Os recursos de função permitem definir um conjunto de valores ou um padrão de expressão regular que determina qual entrada é permitida.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> Os [parâmetros comuns do PowerShell](/powershell/module/microsoft.powershell.core/about/about_commonparameters) sempre são permitidos, mesmo se você restringir os parâmetros disponíveis.
> Você não deve listá-los explicitamente no campo parâmetros.

A tabela a seguir descreve as várias maneiras que você pode personalizar um cmdlet ou função visível.
Você pode misturar e corresponder qualquer um dos campos abaixo no campo **VisibleCmdlets** .

|                                           Exemplo                                           |                                                             Caso de utilização                                                              |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `'My-Func'` ou `@{ Name = 'My-Func' }`                                                      | Permite que o usuário execute `My-Func` sem restrições nos parâmetros.                                                      |
| `'MyModule\My-Func'`                                                                        | Permite que o usuário execute `My-Func` a partir do `MyModule` módulo sem restrições nos parâmetros.                           |
| `'My-*'`                                                                                    | Permite que o usuário execute qualquer cmdlet ou função com o verbo `My`.                                                                 |
| `'*-Func'`                                                                                  | Permite que o usuário execute qualquer cmdlet ou função com o substantivo `Func`.                                                               |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`              | Permite que o usuário execute `My-Func` com os `Param1` parâmetros `Param2` e. Qualquer valor pode ser fornecido para os parâmetros.          |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}` | Permite que o usuário execute `My-Func` com o `Param1` parâmetro. Somente "value1" e "value2" podem ser fornecidos para o parâmetro.        |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`    | Permite que o usuário execute `My-Func` com o `Param1` parâmetro. Qualquer valor que comece com "contoso" pode ser fornecido para o parâmetro. |

> [!WARNING]
> Para práticas recomendadas de segurança, não é recomendável usar curingas ao definir cmdlets ou funções visíveis. Em vez disso, você deve listar explicitamente cada comando confiável para garantir que não haja outros comandos que compartilhem o mesmo esquema de nomenclatura.

Você não pode aplicar um **ValidatePattern** e o ValidateSet ao mesmo cmdlet ou função.

Se você fizer isso, o **ValidatePattern** substituirá o **ValidateSet**.

Para obter mais informações sobre **ValidatePattern**, confira [esta postagem do *Ei, equipe de scripts!* post](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/) e o conteúdo de referência de [expressões regulares do PowerShell](/powershell/module/microsoft.powershell.core/about/about_regular_expressions) .

### <a name="allowing-external-commands-and-powershell-scripts"></a>Permitindo comandos externos e scripts do PowerShell

Para permitir que os usuários executem executáveis e scripts do PowerShell (. ps1) em uma sessão do JEA, você precisa adicionar o caminho completo para cada programa no campo **VisibleExternalCommands** .

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Sempre que possível, para usar o cmdlet do PowerShell ou equivalentes de função para quaisquer executáveis externos que você autorizar, pois você tem controle sobre os parâmetros permitidos com os cmdlets e funções do PowerShell.

Muitos executáveis permitem que você leia o estado atual e, em seguida, altere-o fornecendo parâmetros diferentes.

Por exemplo, considere a função de um administrador de servidor de arquivos que gerencia os compartilhamentos de rede hospedados em um sistema. Uma maneira de gerenciar compartilhamentos é `net share`usar o. No entanto, permitir que **net. exe** seja perigoso porque o usuário pode usar o comando para obter `net group Administrators unprivilegedjeauser /add`privilégios de administrador com o. Uma opção mais segura é permitir [Get-SmbShare](/powershell/module/smbshare/get-smbshare), que obtém o mesmo resultado, mas tem um escopo muito mais limitado.

Ao disponibilizar comandos externos para os usuários em uma sessão do JEA, sempre especifique o caminho completo para o executável. Isso impede a execução de programas com nomes semelhantes e potencialmente mal-intencionados localizados em outro lugar no sistema.

### <a name="allowing-access-to-powershell-providers"></a>Permitindo o acesso aos provedores do PowerShell

Por padrão, nenhum provedor do PowerShell está disponível em sessões do JEA. Isso reduz o risco de informações confidenciais e de definições de configuração serem divulgadas para o usuário que está se conectando.

Quando necessário, você pode permitir o acesso aos provedores do PowerShell usando `VisibleProviders` o comando. Para obter uma lista completa de provedores, `Get-PSProvider`execute.

```powershell
VisibleProviders = 'Registry'
```

Para tarefas simples que exigem acesso ao sistema de arquivos, ao registro, ao repositório de certificados ou a outros provedores confidenciais, considere escrever uma função personalizada que funcione com o provedor em nome do usuário. As funções, os cmdlets e os programas externos disponíveis em uma sessão JEA não estão sujeitos às mesmas restrições que JEA. Eles podem acessar qualquer provedor por padrão. Considere também o uso da [unidade do usuário](session-configurations.md#user-drive) ao copiar arquivos de ou para um ponto de extremidade Jea é necessário.

### <a name="creating-custom-functions"></a>Criando funções personalizadas

Você pode criar funções personalizadas em um arquivo de capacidade de função para simplificar tarefas complexas para seus usuários finais. As funções personalizadas também são úteis quando você precisa de lógica de validação avançada para valores de parâmetro de cmdlet. Você pode escrever funções simples no campo **FunctionDefinitions** :

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending |
            Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> Não se esqueça de adicionar o nome de suas funções personalizadas ao campo **VisibleFunctions** para que elas possam ser executadas pelos usuários do Jea.

O corpo (bloco de script) de funções personalizadas é executado no modo de idioma padrão do sistema e não está sujeito às restrições de idioma do JEA. Isso significa que as funções podem acessar o sistema de arquivos e o registro e executar comandos que não se tornaram visíveis no arquivo de capacidade de função. Tome cuidado para evitar a execução de código arbitrário ao usar parâmetros. Evite a entrada do usuário de tubulação diretamente em `Invoke-Expression`cmdlets como.

No exemplo acima, observe que o nome do módulo totalmente qualificado (FQMN) `Microsoft.PowerShell.Utility\Select-Object` foi usado em vez da abreviação. `Select-Object`
As funções definidas em arquivos de capacidade de função ainda estão sujeitas ao escopo de sessões JEA, que inclui as funções de proxy que o JEA cria para restringir os comandos existentes.

Por padrão, `Select-Object` o é um cmdlet restrito em todas as sessões Jea que não permite a seleção de propriedades arbitrárias em objetos. Para usar as funções não restringidas `Select-Object` , você deve solicitar explicitamente a implementação completa usando o FQMN. Qualquer cmdlet restrito em uma sessão JEA tem as mesmas restrições quando invocado a partir de uma função. Para obter mais informações, consulte [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence).

Se você estiver escrevendo várias funções personalizadas, será mais conveniente colocá-las em um módulo de script do PowerShell. Você torna essas funções visíveis na sessão JEA usando o campo **VisibleFunctions** como faria com módulos internos e de terceiros.

Para que o preenchimento com Tab funcione corretamente em sessões do Jea, você deve incluir a `tabexpansion2` função interna na lista **VisibleFunctions** .

## <a name="place-role-capabilities-in-a-module"></a>Coloque os recursos de função em um módulo

Para que o PowerShell encontre um arquivo de capacidade de função, ele deve ser armazenado em uma pasta **RoleCapabilities** em um módulo do PowerShell. O módulo pode ser armazenado em qualquer pasta incluída na `$env:PSModulePath` variável de ambiente, no entanto, você não deve colocá-lo em system32 ou em uma pasta em que os usuários de conexão não confiáveis possam modificar os arquivos. Abaixo está um exemplo de criação de um módulo de script do PowerShell básico chamado `$env:ProgramFiles` ContosoJEA no caminho.

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest.
# At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

Para obter mais informações sobre os módulos do PowerShell, consulte [noções básicas sobre um módulo do PowerShell](/powershell/developer/windows-powershell).

## <a name="updating-role-capabilities"></a>Atualizando recursos de função

Você pode editar um arquivo de capacidade de função para atualizar as configurações a qualquer momento. Todas as novas sessões JEA iniciadas após a atualização da capacidade de função refletirão os recursos revisados.

É por isso que controlar o acesso à pasta de recursos de função é tão importante. Somente administradores altamente confiáveis devem ter permissão para alterar arquivos de capacidade de função. Se um usuário não confiável puder alterar os arquivos de capacidade de função, ele poderá facilmente conceder acesso a cmdlets que lhes permitam elevar seus privilégios.

Para os administradores que procuram bloquear o acesso aos recursos de função, verifique se o sistema local tem acesso de leitura aos arquivos de capacidade de função e aos módulos que os contém.

## <a name="how-role-capabilities-are-merged"></a>Como os recursos de função são mesclados

Os usuários recebem acesso a todos os recursos de função correspondentes no [arquivo de configuração de sessão](session-configurations.md) quando inserem uma sessão Jea. O JEA tenta conceder ao usuário o conjunto de comandos mais permissivos permitido por qualquer uma das funções.

### <a name="visiblecmdlets-and-visiblefunctions"></a>VisibleCmdlets e VisibleFunctions

A lógica de mesclagem mais complexa afeta cmdlets e funções, que podem ter seus parâmetros e valores de parâmetro limitados em JEA.

As regras são as seguintes:

1. Se um cmdlet só tornar-se visível em uma função, ele ficará visível para o usuário com quaisquer restrições de parâmetro aplicáveis.
2. Se um cmdlet se tornar visível em mais de uma função e cada função tiver as mesmas restrições no cmdlet, o cmdlet ficará visível para o usuário com essas restrições.
3. Se um cmdlet se tornar visível em mais de uma função, e cada função permitir um conjunto diferente de parâmetros, o cmdlet e todos os parâmetros definidos em cada função ficarão visíveis para o usuário.
   Se uma função não tiver restrições nos parâmetros, todos os parâmetros serão permitidos.
4. Se uma função definir um padrão de validação ou validação definida para um parâmetro de cmdlet, e a outra função permitir o parâmetro, mas não restringir os valores de parâmetro, o padrão ou o conjunto de validação será ignorado.
5. Se um conjunto de validação for definido para o mesmo parâmetro de cmdlet em mais de uma função, todos os valores de todos os conjuntos de validação serão permitidos.
6. Se um padrão de validação for definido para o mesmo parâmetro de cmdlet em mais de uma função, todos os valores que corresponderem a qualquer um dos padrões serão permitidos.
7. Se um conjunto de validação for definido em uma ou mais funções e um padrão de validação for definido em outra função para o mesmo parâmetro de cmdlet, o conjunto de validação será ignorado e a regra (6) se aplicará aos padrões de validação restantes.

Abaixo está um exemplo de como as funções são mescladas de acordo com estas regras:

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service
#   is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use
#   ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

### <a name="visibleexternalcommands-visiblealiases-visibleproviders-scriptstoprocess"></a>VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess

Todos os outros campos no arquivo de capacidade de função são adicionados a um conjunto cumulativo de comandos externos permitidos, aliases, provedores e scripts de inicialização. Qualquer comando, alias, provedor ou script disponível em uma capacidade de função está disponível para o usuário JEA.

Tenha cuidado para garantir que o conjunto combinado de provedores de um recurso de função e cmdlets/funções/comandos de outro não permita que os usuários tenham acesso não intencional aos recursos do sistema.
Por exemplo, se uma função permitir o `Remove-Item` cmdlet e outro permitir o `FileSystem` provedor, você corre o risco de um usuário Jea excluir arquivos arbitrários no seu computador. Informações adicionais sobre como identificar as permissões efetivas dos usuários podem ser encontradas no artigo [auditoria do Jea](audit-and-report.md) .

## <a name="next-steps"></a>Passos Seguintes

[Criar um arquivo de configuração de sessão](session-configurations.md)
