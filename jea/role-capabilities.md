---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea, powershell, segurança"
title: "Capacidades de função JEA"
ms.openlocfilehash: 083cab3b44348168fe20e8355f5076b28be78702
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="jea-role-capabilities"></a>Capacidades de função JEA

> Aplica-se a: Windows PowerShell 5.0

Quando criar um ponto final JEA, terá de definir uma ou mais "função capacidades" que descrevem *que* alguém pode efetuar numa sessão JEA.
Uma capacidade de função é um ficheiro de dados do PowerShell com a extensão de .psrc apresenta uma lista de todos os cmdlets, funções, fornecedores e programas externos que devem ser disponibilizados para os utilizadores a ligar.

Este tópico descreve como criar um ficheiro de capacidade de função do PowerShell para os seus utilizadores JEA.

## <a name="determine-which-commands-to-allow"></a>Determinar quais os comandos para permitir

O primeiro passo quando criar um ficheiro de capacidade da função está a ter em consideração que os utilizadores a quem são atribuídos a função terá acesso a.
Este processo de recolha de requisitos podem demorar algum tempo, mas é um processo muito importante.
Fornecer acesso de utilizadores à poucos cmdlets e funções pode impedi-los obtenham o trabalho feito.
Permitir o acesso à demasiados cmdlets e funções pode levar aos utilizadores efetuar mais do que o pretendido com os respetivos privilégios de administrador implícita, weakening a sua postura perante o segurança.

Como aceda sobre este processo irá depender da organização e os objetivos, no entanto, as sugestões seguintes podem ajudar a assegurar que está no caminho certo.

1. **Identificar** os utilizadores de comandos estiver a utilizar para obter as respetivas tarefas causadas. Isto poderá envolver o método surveying equipa de TI, a verificação de scripts de automatização ou analisar registos ou transcrições de sessão do PowerShell.
2. **Atualização** utilizar das ferramentas de linha de comandos para PowerShell equivalentes, sempre que possível, para o melhor de auditoria e a experiência de personalização de JEA. Programas externos não podem estar limitados como granularly como os cmdlets do PowerShell nativos e funções no JEA.
3. **Restringir** o âmbito dos cmdlets se for necessário para apenas permite parâmetros específicos ou valores de parâmetros. Isto é especialmente importante se os utilizadores só devem ser capazes de gerir a parte de um sistema.
4. **Criar** funções personalizadas para substituir comandos complexos ou comandos que são difíceis de restringir no JEA. Uma função simple que encapsula num wrapper um comando complexo ou se aplica a lógica de validação adicionais pode oferecer controlo adicional para administradores e pelo utilizador final simplicidade.
5. **Teste** a lista de âmbito de comandos permitidos com os utilizadores e/ou a automatização de serviços e ajustar conforme necessário.

É importante lembrar-se de que os comandos numa sessão JEA, muitas vezes, são privilégios executar com o administrador (ou, caso contrário elevada).
A seleção tenha o cuidado de comandos disponíveis é importante certificar-se de que o ponto final JEA não permite que o utilizador ao ligar as respetivas permissões de elevação.
Seguem-se alguns exemplos de comandos que podem ser utilizados como se permitido num Estado.
Tenha em atenção que isto não é uma lista exaustiva e só deve ser utilizado como um ponto de partida cautelar de começar por.

### <a name="examples-of-potentially-dangerous-commands"></a>Exemplos de comandos potencialmente perigosos

Risco | Exemplo | Comandos relacionados
-----|---------|-----------------
Conceder privilégios de administrador para ignorar JEA do utilizador ao ligar | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`
Executar código arbitrário, como software maligno, exploits ou scripts personalizados para ignorar proteções | `Start-Process -FilePath '\\san\share\malware.exe'` | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`

## <a name="create-a-role-capability-file"></a>Criar um ficheiro de capacidade de função

Pode criar um novo ficheiro de capacidade de função de PowerShell com o [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

O ficheiro de capacidade de função resultante pode ser aberto num editor de texto e modificado para permitir que os comandos pretendidos para a função.
A documentação de ajuda do PowerShell contém vários exemplos de como pode configurar o ficheiro.

### <a name="allowing-powershell-cmdlets-and-functions"></a>Permitir que as funções e cmdlets do PowerShell

Para autorizar os utilizadores a executar os cmdlets do PowerShell ou as funções, adicione o nome do cmdlet ou uma função para os campos VisbibleCmdlets ou VisibleFunctions.
Se não tem a certeza se um comando é um cmdlet ou uma função, pode executar `Get-Command <name>` e verificar a propriedade "CommandType" na saída.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Por vezes, o âmbito de um cmdlet específico ou a função é demasiado abrangente para as necessidades dos seus utilizadores.
Um administrador DNS, por exemplo, provavelmente, só tem de aceder para reiniciar o serviço DNS.
Num ambiente multi-inquilino onde inquilinos são concedidos acesso aos ferramentas de gestão personalizado, os inquilinos devem ser limitados para gestão com os seus próprios recursos.
Nestes casos, pode restringir os parâmetros são expostos a partir de uma função ou o cmdlet.

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

Em cenários mais avançados, também poderá ter de restringir os valores que alguém pode fornecer estes parâmetros.
Capacidades de função permitem-lhe definir um conjunto de valores permitidos ou um padrão de expressão regular que é avaliado para determinar se é permitida uma entrada fornecida.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> O [parâmetros comuns do PowerShell](https://technet.microsoft.com/library/hh847884.aspx) são sempre permitidas, mesmo se restringir os parâmetros disponíveis.
> A não deve explicitamente listá-los no campo de parâmetros.

A tabela abaixo descreve as várias formas como pode personalizar um cmdlet visível ou uma função.
Pode combinar e corresponde a nenhum do abaixo no VisibleCmdlets campo.

Exemplo                                                                                      | Caso de utilização
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
`'My-Func'` ou `@{ Name = 'My-Func' }`                                                       | Permite que o utilizador executar `My-Func` sem restrições nos parâmetros.
`'MyModule\My-Func'`                                                                         | Permite que o utilizador executar `My-Func` do módulo `MyModule` sem restrições nos parâmetros.
`'My-*'`                                                                                     | Permite ao utilizador executar qualquer cmdlet ou uma função com o verbo `My`.
`'*-Func'`                                                                                   | Permite ao utilizador executar qualquer cmdlet ou uma função com o substantivo `Func`.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | Permite que o utilizador executar `My-Func` com o `Param1` e/ou `Param2` parâmetros. Qualquer valor pode ser fornecida para os parâmetros.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | Permite que o utilizador executar `My-Func` com o `Param1` parâmetro. Apenas "Value1" e "Value2" podem ser fornecido para o parâmetro.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | Permite que o utilizador executar `My-Func` com o `Param1` parâmetro. Qualquer valor começar com "contoso" pode ser fornecido para o parâmetro.


> [!WARNING]
> Para melhores práticas de segurança, não se recomenda utilizar carateres universais, quando definir cmdlets visível ou funções.
> Em vez disso, deve listar explicitamente cada comando fidedigno para garantir que nenhum outro comando que partilham o mesmo esquema de nomenclatura inadvertidamente está autorizado.

Não é possível aplicar um ValidatePattern e ValidateSet para o mesmo cmdlet ou uma função.

Se o fizer, o ValidatePattern irá substituir o ValidateSet.

Para mais informações sobre ValidatePattern, veja [isto *Hey, Scripting Guy!* publique](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) e o [expressões regulares PowerShell](https://technet.microsoft.com/library/hh847880.aspx) conteúdo de referência.

### <a name="allowing-external-commands-and-powershell-scripts"></a>Permitir comandos externos e scripts do PowerShell

Para permitir que os utilizadores executar executáveis e scripts do PowerShell (. ps1) numa sessão JEA, tem de adicionar o caminho completo para cada programa no campo VisibleExternalCommands.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

É recomendado, sempre que possível utilizar o PowerShell equivalentes de cmdlet/função de qualquer executáveis externo que autorizar uma vez que tem controlo sobre o qual são permitidos parâmetros com os cmdlets do PowerShell/funções.

Executáveis muitos permitem-lhe para o estado atual de leitura e alterá-lo, em seguida, fornecendo diferentes parâmetros.

Por exemplo, considere a função de um administrador do servidor de ficheiros que pretende verificar as partilhas de rede estão alojadas pelo computador local.
Uma forma de verificar é utilizar `net share`.
No entanto, permitindo net.exe é muito perigosas porque o administrador pode utilizar apenas como facilmente o comando para obter os privilégios de administrador com `net group Administrators unprivilegedjeauser /add`.
Uma abordagem de melhor é permitir [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) que alcance o mesmo resultado mas tem um âmbito muito mais limitado.

Ao disponibilizar comandos externos aos utilizadores numa sessão JEA, sempre especificar o caminho completo para o executável para garantir um programa nome semelhante (e potencialmente malicous) colocado noutro local no sistema de não ser executado em vez disso.

### <a name="allowing-access-to-powershell-providers"></a>Permitir o acesso aos fornecedores de PowerShell

Por predefinição, não existem fornecedores de PowerShell estão disponíveis em sessões JEA.

Isto é principalmente reduzir o risco de informações confidenciais e definições de configuração que está a ser divulgadas ao utilizador ao ligar.

Quando for necessário, pode permitir o acesso aos fornecedores de PowerShell utilizando o `VisibleProviders` comando.
Para obter uma lista completa dos fornecedores, executar `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

Para as tarefas simples que necessitam de acesso para o sistema de ficheiros, o registo, o arquivo de certificados ou outros fornecedores de confidenciais, pode considerar ao escrever uma função personalizada que funciona com o fornecedor em nome do utilizador.
Funções, cmdlets e programas externos que estão disponíveis numa sessão JEA não estão sujeitas as restrições mesmas JEA – poderem aceder ao fornecedor de qualquer por predefinição.
Considere também a utilização de [unidade utilizador](session-configurations.md#user-drive) quando é necessário copiar ficheiros para/de um ponto final JEA.

### <a name="creating-custom-functions"></a>Criar funções personalizadas

Pode criar funções personalizadas num ficheiro de capacidade de função para simplificar as tarefas complexas para os utilizadores finais.
Funções personalizadas também são úteis quando precisa de lógica de validação avançada para os valores de parâmetros de cmdlet.
Pode escrever funções simples **FunctionDefinitions** campo:

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
> Não se esqueça de adicionar o nome das suas funções personalizadas para o **VisibleFunctions** campo, pelo que pode ser executados pelos utilizadores JEA.


O corpo (bloco de script) de funções personalizadas é executado no modo de idioma predefinido para o sistema e não está sujeito a restrições de idioma do JEA.
Isto significa que funções podem aceder ao sistema de ficheiros e registo e executar comandos que não foram efetuados visível no ficheiro de capacidade de função.
Asseguramos para evitar a permitir que o código arbitrário a ser executada ao utilizar parâmetros e evitar a intervenção do utilizador piping diretamente para os cmdlets, como `Invoke-Expression`.

No exemplo acima, irá reparar que o nome do módulo completamente qualificado (FQMN) `Microsoft.PowerShell.Utility\Select-Object` foi utilizado em vez da expressão compacta `Select-Object`.
Funções definidas nos ficheiros de capacidade de função estão ainda sujeitos o âmbito das sessões JEA, que inclui as funções de proxy JEA cria para restringir os comandos existentes.

Select-Object é uma predefinição, o cmdlet restrita em todas as sessões JEA que não permite que selecione arbitrários propriedades em objetos.
Para utilizar o Select-Object nas funções, tem de solicitar explicitamente a implementação completa, especificando o FQMN.
Qualquer cmdlet numa sessão JEA restrita plantas possuir o mesmo comportamento quando invocada a partir de uma função, de acordo com a do PowerShell [precedência de comandos](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).

Se estiver a escrever uma grande quantidade de funções personalizadas, poderá ser mais fácil para colocá-los [módulo de Script do PowerShell](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).
Em seguida, pode efetuar essas funções visíveis na sessão JEA utilizando o campo de VisibleFunctions como faria com módulos incorporados e de terceiros.

## <a name="place-role-capabilities-in-a-module"></a>Capacidades de função local num módulo

Ordem de PowerShell para localizar um ficheiro de capacidade de função, terá de estar armazenado numa pasta "RoleCapabilities" num módulo do PowerShell.
O módulo pode ser armazenado em qualquer pasta incluída no `$env:PSModulePath` variável de ambiente, no entanto, deve não colocá-lo num System32 (reservadas para módulos incorporados) ou uma pasta onde o não fidedigna, os utilizadores a ligar pode modificar os ficheiros.
Segue-se um exemplo de criação de um módulo de script do PowerShell básico chamado *ContosoJEA* no caminho "Ficheiros de programa".

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

Consulte [compreender um módulo do PowerShell](https://msdn.microsoft.com/en-us/library/dd878324.aspx) para obter mais informações sobre o módulos do PowerShell, manifestos de módulo e a variável de ambiente de PSModulePath.

## <a name="updating-role-capabilities"></a>Atualizar as capacidades de função


Pode atualizar um ficheiro de capacidade de função em qualquer altura ao simplesmente a guardar as alterações para o ficheiro de capacidade de função.
Quaisquer novas sessões JEA iniciadas depois da capacidade de função tiver sido atualizada irão refletir as capacidades revistas.

É por isso controlar o acesso à pasta de capacidades de função é tão importante.
Apenas administradores altamente fidedignos devem poder alterar ficheiros de capacidade de função.
Se um utilizador não fidedigno pode alterar os ficheiros de capacidade de função, pode facilmente fornecem próprios acesso aos cmdlets que permitem que os seus privilégios de elevação.


Para administradores que procuram bloqueio para baixo de acesso para as capacidades de função, certifique-se de que sistema Local tem acesso de leitura aos ficheiros de capacidade de função e os módulos que contêm.

## <a name="how-role-capabilities-are-merged"></a>Como são intercaladas capacidades de função

Podem ser concedido acesso aos utilizadores várias capacidades de função quando que introduza uma sessão JEA consoante os mapeamentos de função no [ficheiro de configuração de sessão](session-configurations.md).
Quando isto acontecer, JEA tenta conceder ao utilizador o *mais permissivo* conjunto de comandos permitido por qualquer uma das funções.

**VisibleCmdlets e VisibleFunctions**

A lógica de intercalação mais complexa afeta cmdlets e funções, o que podem ter os parâmetros e valores de parâmetro no JEA limitados.

As regras são os seguintes:

1. Se um cmdlet só ficam visível numa função, vai estar visível ao utilizador com as eventuais restrições no parâmetro aplicável.
2. Se um cmdlet ficam visível em mais de uma função, e cada função tem as mesmas restrições sobre o cmdlet, o cmdlet vai estar visível ao utilizador com essas restrições.
3. Se um cmdlet ficam visível em mais de uma função, e cada função permite que um conjunto diferente de parâmetros, o cmdlet e todos os parâmetros definidos em cada função vai estar visíveis ao utilizador. Se uma função de não ter restrições nos parâmetros, terão permissão de todos os parâmetros.
4. Se uma função define um conjunto de validar ou validar padrão para um parâmetro de cmdlet, e a outras funções permite que o parâmetro, mas não restringir os valores de parâmetros, o conjunto de validar ou padrão será ignorada.
5. Se um conjunto de validar está definido para o mesmo parâmetro de cmdlet em mais de uma função, todos os valores de todos os conjuntos de validar serão permitidos.
6. Se um padrão de validar está definido para o mesmo parâmetro de cmdlet em mais de uma função, os valores que correspondem a nenhum dos padrões de serão permitidos.
7. Se está definido um conjunto de validar uma ou mais funções e um padrão de validar está definido na outra função para o mesmo parâmetro de cmdlet, o conjunto de validar é ignorado e a regra (6) se aplica os padrões de validar restantes.

Abaixo está um exemplo de como as funções são intercaladas, de acordo com estas regras:

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



**VisibleExternalCommands, ScriptsToProcess VisibleAliases, VisibleProviders,**

Todos os outros campos no ficheiro de capacidade de função simplesmente são adicionados a um conjunto cumulativo de comandos externos permitidos, aliases, fornecedores e scripts de arranque.
Qualquer comando, alias, fornecedor ou script disponível numa capacidade de função estará disponível para o utilizador JEA.

Tenha cuidado garantir que o conjunto combinado de fornecedores de uma capacidade de função e as funções/cmdlets/comandos de outro não permitem estabelecer ligação aos utilizadores não intencional acesso aos recursos de sistema.
Por exemplo, se uma função permite que o `Remove-Item` cmdlet e outra permite que o `FileSystem` fornecedor, está em risco de um utilizador JEA eliminar ficheiros arbitrários no seu computador.
Pode encontrar informações adicionais sobre como identificar as permissões efetivas dos utilizadores no [auditoria tópico JEA](audit-and-report.md).

## <a name="next-steps"></a>Próximos passos

- [Criar um ficheiro de configuração de sessão](session-configurations.md)

