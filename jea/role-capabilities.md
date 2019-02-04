---
ms.date: 06/12/2017
keywords: jea, powershell, segurança
title: Funcionalidades de função JEA
ms.openlocfilehash: bd0a995adc60e50049ff99d6b23e7c2aeb745a18
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685495"
---
# <a name="jea-role-capabilities"></a>Funcionalidades de função JEA

> Aplica-se a: Windows PowerShell 5.0

Ao criar um ponto final JEA, terá de definir uma ou mais "funcionalidades de função" que descrevem *o que* alguém pode fazer numa sessão JEA.
Um recurso de função é um arquivo de dados do PowerShell com a extensão de .psrc que lista todos os cmdlets, funções, fornecedores e programas externos que devem ser disponibilizados para os utilizadores a ligar.

Este tópico descreve como criar um arquivo de recurso de função do PowerShell para os seus utilizadores JEA.

## <a name="determine-which-commands-to-allow"></a>Determinar quais comandos para permitir

A primeira etapa ao criar um arquivo de recurso de função é considerar o que os utilizadores a quem são atribuídos a função precisarem acessar.
Este processo de recolha de requisitos podem demorar algum tempo, mas é um processo muito importante.
Fornecer acesso de utilizadores à muito poucos cmdlets e funções pode impedi-los de seu trabalho.
Permitir o acesso a muitos cmdlets e funções pode levar a fazer mais do que pretendia com seus privilégios de administrador implícito, enfraquecer a sua postura de segurança de utilizadores.

Como para este processo irá depender sua organização e os objetivos, no entanto, as dicas a seguir podem ajudar a garantir que está no caminho certo.

1. **Identificar** os utilizadores de comandos estiver a utilizar para realizar seu trabalho. Isso pode envolver a apurar o departamento de TI, a verificação de scripts de automatização ou analisar transcrições de sessão do PowerShell ou os registos.
2. **Atualização** utilizar das ferramentas de linha de comandos para PowerShell equivalentes, sempre que possível, para o melhor de auditoria e a experiência de personalização de JEA. Não podem ser restrita programas externos como granularmente como cmdlets do PowerShell nativo e funções no JEA.
3. **Restringir** o âmbito dos cmdlets, se necessário, para apenas permite parâmetros específicos ou valores de parâmetros. Isso é particularmente importante se os utilizadores só devem ser capazes de gerir a parte de um sistema.
4. **Criar** funções personalizadas para substituir comandos complexos ou comandos que são difíceis de restringir na JEA. Uma função simples que encapsula um comando complexo ou se aplicar lógica de validação pode oferecer controle adicional para simplificar os administradores e utilizadores finais.
5. **Teste** a lista de âmbito de comandos permitidos com os seus utilizadores e/ou a automatização de serviços e ajustar conforme necessário.

É importante lembrar-se de que os comandos numa sessão JEA, muitas vezes, são privilégios de execução com o administrador (ou, caso contrário elevados).
Seleção de cuidado de comandos disponíveis é importante certificar-se de que o ponto final da JEA não permite que o usuário conectado elevar as respetivas permissões.
Seguem-se alguns exemplos de comandos que podem ser usados maliciosamente se permitido num Estado irrestrita.
Tenha em atenção que isto não é uma lista exaustiva e só deve ser utilizado como um ponto de partida cautelar de começar por.

### <a name="examples-of-potentially-dangerous-commands"></a>Exemplos de comandos potencialmente perigosos

Risco | Exemplo | Comandos relacionados
-----|---------|-----------------
O usuário conectado a conceder privilégios de administrador para ignorar a JEA | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`
Executar código arbitrário, como software maligno, explorações ou scripts personalizados para ignorar as proteções | `Start-Process -FilePath '\\san\share\malware.exe'` | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`

## <a name="create-a-role-capability-file"></a>Crie um ficheiro de recurso de função

Pode criar um novo arquivo de recurso de função de PowerShell com o [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

O arquivo de recurso de função resultante pode ser aberto num editor de texto e modificado para permitir que os comandos desejados para a função.
A documentação de ajuda do PowerShell contém vários exemplos de como pode configurar o ficheiro.

### <a name="allowing-powershell-cmdlets-and-functions"></a>Permitir que as funções e cmdlets do PowerShell

Para autorizar os utilizadores executem funções ou os cmdlets do PowerShell, adicione o nome do cmdlet ou uma função aos campos VisbibleCmdlets ou VisibleFunctions.
Se não souber ao certo se um comando é um cmdlet ou uma função, pode executar `Get-Command <name>` e verificar a propriedade de "CommandType" na saída.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Por vezes, o escopo de um cmdlet específico ou a função é demasiado abrangente para as necessidades dos seus utilizadores.
Um administrador de DNS, por exemplo, provavelmente só precisa de acesso para reiniciar o serviço DNS.
Num ambiente de vários inquilino em que os inquilinos recebem acesso a ferramentas de gestão self-service, os inquilinos devem ser limitados para a gestão com seus próprios recursos.
Nesses casos, pode restringir quais parâmetros são expostos a partir de uma função ou o cmdlet.

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

Em cenários mais avançados, também poderá restringir os valores que alguém pode fornecer a esses parâmetros.
Funcionalidades de função permitem-lhe definir um conjunto de valores permitidos ou um padrão de expressão regular que é avaliado para determinar se uma determinada entrada é permitida.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> O [parâmetros comuns do PowerShell](https://technet.microsoft.com/library/hh847884.aspx) sempre são permitidos, mesmo que restrinja os parâmetros disponíveis.
> Deve não explicitamente listá-los no campo de parâmetros.

A tabela abaixo descreve as várias formas como pode personalizar uma função ou o cmdlet visível.
Pode combinar e corresponde a nenhum do abaixo no VisibleCmdlets campo.

Exemplo                                                                                      | Caso de utilização
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
`'My-Func'` ou `@{ Name = 'My-Func' }`                                                       | Permite que o usuário execute `My-Func` sem quaisquer restrições nos parâmetros.
`'MyModule\My-Func'`                                                                         | Permite que o usuário execute `My-Func` do módulo `MyModule` sem quaisquer restrições nos parâmetros.
`'My-*'`                                                                                     | Permite que o usuário execute qualquer cmdlet ou uma função com o verbo `My`.
`'*-Func'`                                                                                   | Permite que o usuário execute qualquer cmdlet ou uma função com o substantivo `Func`.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | Permite que o usuário execute `My-Func` com o `Param1` e/ou `Param2` parâmetros. Qualquer valor pode ser fornecido para os parâmetros.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | Permite que o usuário execute `My-Func` com o `Param1` parâmetro. Apenas "Value1" e "Value2" podem ser fornecidos para o parâmetro.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | Permite que o usuário execute `My-Func` com o `Param1` parâmetro. Qualquer valor a partir do "contoso" pode ser fornecido para o parâmetro.


> [!WARNING]
> Para melhores práticas de segurança, não é recomendado para utilizar carateres universais, quando se definem cmdlets visível ou funções.
> Em vez disso, deve listar explicitamente cada comando confiável para garantir que nenhum outro comando que partilham o mesmo esquema de nomenclatura inadvertidamente está autorizado.

Não é possível aplicar um ValidatePattern e ValidateSet para o mesmo cmdlet ou função.

Se o fizer, o ValidatePattern irá substituir o ValidateSet.

Para obter mais informações sobre ValidatePattern, confira [isso *Hey, Scripting Guy!* publicar](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) e o [expressões regulares do PowerShell](https://technet.microsoft.com/library/hh847880.aspx) conteúdo de referência.

### <a name="allowing-external-commands-and-powershell-scripts"></a>Permitir que os comandos externos e scripts do PowerShell

Para permitir que os usuários executem executáveis e scripts do PowerShell (. ps1) numa sessão JEA, terá de adicionar o caminho completo para cada programa no campo VisibleExternalCommands.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Recomenda-se, sempre que possível utilizar o PowerShell equivalentes de cmdlet/função de quaisquer executáveis externos que autorizar, uma vez que tem controle sobre quais os parâmetros são permitidos com cmdlets do PowerShell/funções.

Número de executáveis permite ao ler o estado atual e, em seguida, altere-o apenas ao fornecer parâmetros diferentes.

Por exemplo, considere a função de um administrador de servidor de ficheiro que deseja verificar quais compartilhamentos de rede estão alojados pelo computador local.
Uma forma de verificar é usar `net share`.
No entanto, permitindo que net.exe é muito perigoso porque o administrador pode facilmente utilizar o comando para obter privilégios de administrador com `net group Administrators unprivilegedjeauser /add`.
Uma abordagem melhor é permitir que [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) que ofereça o mesmo resultado, mas tem um âmbito muito mais limitado.

Ao disponibilizar comandos externos para os usuários numa sessão JEA, sempre Especifica o caminho completo para o executável para garantir um programa com o mesmo nome (e potencialmente malicous) colocado em outro lugar no sistema não é executado em vez disso.

### <a name="allowing-access-to-powershell-providers"></a>Permitir o acesso aos provedores de PowerShell

Por predefinição, não existem fornecedores de PowerShell estão disponíveis em sessões JEA.

Isto é principalmente para reduzir o risco de informações confidenciais e definições de configuração que está a ser reveladas para o usuário conectado.

Quando for necessário, pode permitir o acesso para os fornecedores de PowerShell utilizando o `VisibleProviders` comando.
Para obter uma lista completa dos fornecedores, executar `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

Para tarefas simples que necessitam de acesso para o sistema de arquivos, registro, arquivo de certificados ou outros fornecedores de serviços confidenciais, também pode considerar o escrever uma função personalizada que funciona com o fornecedor em nome do utilizador.
As funções, cmdlets e programas externos que estão disponíveis numa sessão JEA não estão sujeitas às mesmas restrições quanto como JEA--eles podem aceder a qualquer fornecedor por padrão.
Considere também a utilização a [unidade utilizador](session-configurations.md#user-drive) quando é necessário copiar os ficheiros de/para um ponto final JEA.

### <a name="creating-custom-functions"></a>Criar funções personalizadas

Pode criar funções personalizadas num arquivo de recurso de função para simplificar as tarefas complexas para seus usuários finais.
Funções personalizadas também são úteis quando necessitar de lógica de validação avançada para valores de parâmetros de cmdlet.
Pode escrever funções simples no **FunctionDefinitions** campo:

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> Não se esqueça de adicionar o nome das suas funções personalizadas para o **VisibleFunctions** campo para que podem ser executadas pelos utilizadores JEA.


O corpo (bloco de script) de funções personalizadas é executado no modo de idioma predefinido para o sistema e não está sujeita a restrições de idioma da JEA.
Isso significa que as funções podem aceder ao sistema de arquivos e registro e executar comandos que não foram feitos visível no arquivo de recurso de função.
Tenha cuidado para evitar a permitir que código arbitrário a ser executada quando o uso de parâmetros e evitar diretamente para os cmdlets, como a entrada do usuário de piping `Invoke-Expression`.

No exemplo acima, irá notar que o nome de módulo completamente qualificado (FQMN) `Microsoft.PowerShell.Utility\Select-Object` foi utilizado em vez da forma abreviada `Select-Object`.
Funções definidas nos arquivos de recurso de função são ainda pode ser o escopo de sessões JEA, que inclui as funções de proxy JEA cria para restringir comandos existentes.

Select-Object é um padrão, o cmdlet restrita em todas as sessões JEA que não permite que selecione propriedades arbitrárias em objetos.
Para utilizar o Select-Object irrestrita nas funções, tem de solicitar explicitamente a implementação completa, especificando o FQMN.
Qualquer cmdlet restrita numa sessão JEA exibirão o mesmo comportamento quando invocado a partir de uma função, seguindo a linha do PowerShell [precedência de comandos](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).

Se estiver a escrever muitas funções personalizadas, pode ser mais fácil de colocá-los [módulo de Script do PowerShell](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx).
Em seguida, pode tornar essas funções visível na sessão usando o campo de VisibleFunctions como faria com módulos de terceiros, incorporados e JEA.

## <a name="place-role-capabilities-in-a-module"></a>Funcionalidades de função local num módulo

Por ordem para o PowerShell localizar um ficheiro de recurso de função, ele deve ser armazenado numa pasta "RoleCapabilities" num módulo do PowerShell.
O módulo pode ser armazenado em qualquer pasta incluída no `$env:PSModulePath` variável de ambiente, no entanto, deve não colocá-lo na System32 (reservado para módulos internos) ou uma pasta em que o não fidedigno, os utilizadores a ligar foi possível modificar os ficheiros.
Segue-se um exemplo de criação de um módulo de script de PowerShell básico chamado *ContosoJEA* no caminho "Arquivos de programas".

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

Ver [Noções básicas sobre um módulo do PowerShell](https://msdn.microsoft.com/library/dd878324.aspx) para obter mais informações sobre os módulos do PowerShell, manifestos de módulo e a variável de ambiente de PSModulePath.

## <a name="updating-role-capabilities"></a>Atualizar funcionalidades de função


Pode atualizar um ficheiro de recurso de função em qualquer altura ao simplesmente a guardar as alterações no arquivo de recurso de função.
Quaisquer novas sessões JEA iniciados depois do recurso de função foi atualizado irão refletir as capacidades revisadas.

É por isso controlar o acesso para a pasta de recursos de função é tão importante.
Apenas administradores altamente fidedignos devem ser capazes de alterar os arquivos de recurso de função.
Se um usuário não confiável pode alterar os arquivos de recurso de função, eles podem facilmente atribuir acesso aos cmdlets que permitem-los elevar seus privilégios.


Para administradores que procuram para bloquear o acesso a funcionalidades de função, certifique-se de que o sistema Local tem acesso de leitura aos ficheiros de recurso de função e módulos que contêm.

## <a name="how-role-capabilities-are-merged"></a>Como as funcionalidades de função são intercaladas

Os utilizadores podem ser concedidos acesso às várias funcionalidades de função quando entram numa sessão JEA consoante os mapeamentos de função na [o ficheiro de configuração de sessão](session-configurations.md).
Quando isto acontecer, JEA tenta dar ao usuário a *mais permissivo* conjunto de comandos permitidos por qualquer uma das funções.

**VisibleCmdlets e VisibleFunctions**

A lógica mais complexa de intercalação afeta cmdlets e funções, o que podem ter seus parâmetros e valores de parâmetro nos JEA.

As regras são os seguintes:

1. Se um cmdlet só ficam visível numa função, é visível para o usuário com quaisquer restrições de parâmetro aplicável.
2. Se um cmdlet ficam visível em mais de uma função, e cada função tem as mesmas restrições sobre o cmdlet, o cmdlet irá ser visível para o usuário com essas restrições.
3. Se um cmdlet ficam visível em mais de uma função, e cada função permite que um conjunto diferente de parâmetros, o cmdlet e todos os parâmetros definidos em cada função estarão visíveis para o utilizador. Se uma função não tiver restrições nos parâmetros, todos os parâmetros serão permitidos.
4. Se uma função define um conjunto de validar ou validar padrão para um parâmetro de cmdlet, e a outra função permite que o parâmetro, mas não restrinja os valores de parâmetros, o conjunto de validar ou padrão será ignorada.
5. Se um conjunto de validar for definido para o mesmo parâmetro de cmdlet em mais de uma função, todos os valores de todos os conjuntos de validar serão permitidos.
6. Se um padrão de validar for definido para o mesmo parâmetro de cmdlet em mais de uma função, serão permitidos quaisquer valores que correspondam a qualquer um dos padrões.
7. Se um conjunto de validar é definido numa ou mais funções e um padrão de validar é definido em outra função para o mesmo parâmetro de cmdlet, o conjunto de validar é ignorado e regra (6) aplica-se para os padrões de validar restantes.

Segue-se um exemplo de como as funções são mescladas, de acordo com essas regras:

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permisisons for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored becuase of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```



**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**

Todos os outros campos no ficheiro de recurso de função são simplesmente adicionados a um conjunto cumulativo de comandos externos permitidos, aliases, provedores e scripts de inicialização.
Qualquer comando, o alias, o fornecedor ou o script disponível num recurso de função vai estar disponível para o utilizador JEA.

Tenha cuidado para garantir que o conjunto combinado de provedores a partir de um recurso de função e cmdlets/funções/comandos a partir de outro permite ao ligar aos utilizadores não intencional acesso aos recursos do sistema.
Por exemplo, se uma função permite que o `Remove-Item` cmdlet e outro permite que o `FileSystem` fornecedor, está em risco de um utilizador JEA a eliminar ficheiros arbitrários no seu computador.
Pode encontrar informações adicionais sobre como identificar as permissões efetivas dos utilizadores no [auditoria tópico JEA](audit-and-report.md).

## <a name="next-steps"></a>Próximos passos

- [Criar um ficheiro de configuração de sessão](session-configurations.md)