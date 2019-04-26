---
ms.date: 06/12/2017
keywords: jea, powershell, segurança
title: Funcionalidades de função JEA
ms.openlocfilehash: b93d206680de485d6cb7a8cb26d63afda5bf8421
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084798"
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="509f1-103">Funcionalidades de função JEA</span><span class="sxs-lookup"><span data-stu-id="509f1-103">JEA Role Capabilities</span></span>

> <span data-ttu-id="509f1-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="509f1-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="509f1-105">Ao criar um ponto final JEA, terá de definir uma ou mais "funcionalidades de função" que descrevem *o que* alguém pode fazer numa sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="509f1-105">When creating a JEA endpoint, you will need to define one or more "role capabilities" which describe *what* someone can do in a JEA session.</span></span>
<span data-ttu-id="509f1-106">Um recurso de função é um arquivo de dados do PowerShell com a extensão de .psrc que lista todos os cmdlets, funções, fornecedores e programas externos que devem ser disponibilizados para os utilizadores a ligar.</span><span class="sxs-lookup"><span data-stu-id="509f1-106">A role capability is a PowerShell data file with the .psrc extension that lists all the cmdlets, functions, providers, and external programs that should be made available to connecting users.</span></span>

<span data-ttu-id="509f1-107">Este tópico descreve como criar um arquivo de recurso de função do PowerShell para os seus utilizadores JEA.</span><span class="sxs-lookup"><span data-stu-id="509f1-107">This topic describes how to create a PowerShell role capability file for your JEA users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="509f1-108">Determinar quais comandos para permitir</span><span class="sxs-lookup"><span data-stu-id="509f1-108">Determine which commands to allow</span></span>

<span data-ttu-id="509f1-109">A primeira etapa ao criar um arquivo de recurso de função é considerar o que os utilizadores a quem são atribuídos a função precisarem acessar.</span><span class="sxs-lookup"><span data-stu-id="509f1-109">The first step when creating a role capability file is to consider what the users who are assigned the role will need access to.</span></span>
<span data-ttu-id="509f1-110">Este processo de recolha de requisitos podem demorar algum tempo, mas é um processo muito importante.</span><span class="sxs-lookup"><span data-stu-id="509f1-110">This requirements gathering process can take a while, but it is a very important process.</span></span>
<span data-ttu-id="509f1-111">Fornecer acesso de utilizadores à muito poucos cmdlets e funções pode impedi-los de seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="509f1-111">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span>
<span data-ttu-id="509f1-112">Permitir o acesso a muitos cmdlets e funções pode levar a fazer mais do que pretendia com seus privilégios de administrador implícito, enfraquecer a sua postura de segurança de utilizadores.</span><span class="sxs-lookup"><span data-stu-id="509f1-112">Allowing access to too many cmdlets and functions can lead to users doing more than you intended with their implicit admin privileges, weakening your security stance.</span></span>

<span data-ttu-id="509f1-113">Como para este processo irá depender sua organização e os objetivos, no entanto, as dicas a seguir podem ajudar a garantir que está no caminho certo.</span><span class="sxs-lookup"><span data-stu-id="509f1-113">How you go about this process will depend on your organization and goals, however the following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="509f1-114">**Identificar** os utilizadores de comandos estiver a utilizar para realizar seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="509f1-114">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="509f1-115">Isso pode envolver a apurar o departamento de TI, a verificação de scripts de automatização ou analisar transcrições de sessão do PowerShell ou os registos.</span><span class="sxs-lookup"><span data-stu-id="509f1-115">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts or logs.</span></span>
2. <span data-ttu-id="509f1-116">**Atualização** utilizar das ferramentas de linha de comandos para PowerShell equivalentes, sempre que possível, para o melhor de auditoria e a experiência de personalização de JEA.</span><span class="sxs-lookup"><span data-stu-id="509f1-116">**Update** use of command line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="509f1-117">Não podem ser restrita programas externos como granularmente como cmdlets do PowerShell nativo e funções no JEA.</span><span class="sxs-lookup"><span data-stu-id="509f1-117">External programs cannot be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="509f1-118">**Restringir** o âmbito dos cmdlets, se necessário, para apenas permite parâmetros específicos ou valores de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="509f1-118">**Restrict** the scope of the cmdlets if necessary to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="509f1-119">Isso é particularmente importante se os utilizadores só devem ser capazes de gerir a parte de um sistema.</span><span class="sxs-lookup"><span data-stu-id="509f1-119">This is particularly important if users should only be able to manage part of a system.</span></span>
4. <span data-ttu-id="509f1-120">**Criar** funções personalizadas para substituir comandos complexos ou comandos que são difíceis de restringir na JEA.</span><span class="sxs-lookup"><span data-stu-id="509f1-120">**Create** custom functions to replace complex commands or commands which are difficult to constrain in JEA.</span></span> <span data-ttu-id="509f1-121">Uma função simples que encapsula um comando complexo ou se aplicar lógica de validação pode oferecer controle adicional para simplificar os administradores e utilizadores finais.</span><span class="sxs-lookup"><span data-stu-id="509f1-121">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="509f1-122">**Teste** a lista de âmbito de comandos permitidos com os seus utilizadores e/ou a automatização de serviços e ajustar conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="509f1-122">**Test** the scoped list of allowable commands with your users and/or automation services and adjust as necessary.</span></span>

<span data-ttu-id="509f1-123">É importante lembrar-se de que os comandos numa sessão JEA, muitas vezes, são privilégios de execução com o administrador (ou, caso contrário elevados).</span><span class="sxs-lookup"><span data-stu-id="509f1-123">It is important to remember that commands in a JEA session are often run with admin (or otherwise elevated) privileges.</span></span>
<span data-ttu-id="509f1-124">Seleção de cuidado de comandos disponíveis é importante certificar-se de que o ponto final da JEA não permite que o usuário conectado elevar as respetivas permissões.</span><span class="sxs-lookup"><span data-stu-id="509f1-124">Careful selection of available commands is important to ensure the JEA endpoint does not allow the connecting user to elevate their permissions.</span></span>
<span data-ttu-id="509f1-125">Seguem-se alguns exemplos de comandos que podem ser usados maliciosamente se permitido num Estado irrestrita.</span><span class="sxs-lookup"><span data-stu-id="509f1-125">Below are some examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span>
<span data-ttu-id="509f1-126">Tenha em atenção que isto não é uma lista exaustiva e só deve ser utilizado como um ponto de partida cautelar de começar por.</span><span class="sxs-lookup"><span data-stu-id="509f1-126">Note that this is not an exhaustive list and should only be used as a cautionary starting point.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="509f1-127">Exemplos de comandos potencialmente perigosos</span><span class="sxs-lookup"><span data-stu-id="509f1-127">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="509f1-128">Risco</span><span class="sxs-lookup"><span data-stu-id="509f1-128">Risk</span></span> | <span data-ttu-id="509f1-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="509f1-129">Example</span></span> | <span data-ttu-id="509f1-130">Comandos relacionados</span><span class="sxs-lookup"><span data-stu-id="509f1-130">Related commands</span></span>
-----|---------|-----------------
<span data-ttu-id="509f1-131">O usuário conectado a conceder privilégios de administrador para ignorar a JEA</span><span class="sxs-lookup"><span data-stu-id="509f1-131">Granting the connecting user admin privileges to bypass JEA</span></span> | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="509f1-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="509f1-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>
<span data-ttu-id="509f1-133">Executar código arbitrário, como software maligno, explorações ou scripts personalizados para ignorar as proteções</span><span class="sxs-lookup"><span data-stu-id="509f1-133">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'` | <span data-ttu-id="509f1-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="509f1-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span>

## <a name="create-a-role-capability-file"></a><span data-ttu-id="509f1-135">Crie um ficheiro de recurso de função</span><span class="sxs-lookup"><span data-stu-id="509f1-135">Create a role capability file</span></span>

<span data-ttu-id="509f1-136">Pode criar um novo arquivo de recurso de função de PowerShell com o [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="509f1-136">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="509f1-137">O arquivo de recurso de função resultante pode ser aberto num editor de texto e modificado para permitir que os comandos desejados para a função.</span><span class="sxs-lookup"><span data-stu-id="509f1-137">The resulting role capability file can be opened in a text editor and modified to allow the desired commands for the role.</span></span>
<span data-ttu-id="509f1-138">A documentação de ajuda do PowerShell contém vários exemplos de como pode configurar o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="509f1-138">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="509f1-139">Permitir que as funções e cmdlets do PowerShell</span><span class="sxs-lookup"><span data-stu-id="509f1-139">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="509f1-140">Para autorizar os utilizadores executem funções ou os cmdlets do PowerShell, adicione o nome do cmdlet ou uma função aos campos VisibleCmdlets ou VisibleFunctions.</span><span class="sxs-lookup"><span data-stu-id="509f1-140">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisibleCmdlets or VisibleFunctions fields.</span></span>
<span data-ttu-id="509f1-141">Se não souber ao certo se um comando é um cmdlet ou uma função, pode executar `Get-Command <name>` e verificar a propriedade de "CommandType" na saída.</span><span class="sxs-lookup"><span data-stu-id="509f1-141">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the "CommandType" property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="509f1-142">Por vezes, o escopo de um cmdlet específico ou a função é demasiado abrangente para as necessidades dos seus utilizadores.</span><span class="sxs-lookup"><span data-stu-id="509f1-142">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span>
<span data-ttu-id="509f1-143">Um administrador de DNS, por exemplo, provavelmente só precisa de acesso para reiniciar o serviço DNS.</span><span class="sxs-lookup"><span data-stu-id="509f1-143">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span>
<span data-ttu-id="509f1-144">Num ambiente de vários inquilino em que os inquilinos recebem acesso a ferramentas de gestão self-service, os inquilinos devem ser limitados para a gestão com seus próprios recursos.</span><span class="sxs-lookup"><span data-stu-id="509f1-144">In a multi-tenant environment where tenants are granted access to self-service management tools, tenants should be limited to managing with their own resources.</span></span>
<span data-ttu-id="509f1-145">Nesses casos, pode restringir quais parâmetros são expostos a partir de uma função ou o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="509f1-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

<span data-ttu-id="509f1-146">Em cenários mais avançados, também poderá restringir os valores que alguém pode fornecer a esses parâmetros.</span><span class="sxs-lookup"><span data-stu-id="509f1-146">In more advanced scenarios, you may also need to restrict which values someone can supply to these parameters.</span></span>
<span data-ttu-id="509f1-147">Funcionalidades de função permitem-lhe definir um conjunto de valores permitidos ou um padrão de expressão regular que é avaliado para determinar se uma determinada entrada é permitida.</span><span class="sxs-lookup"><span data-stu-id="509f1-147">Role capabilities let you define a set of allowed values or a regular expression pattern that is evaluated to determine if a given input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="509f1-148">O [parâmetros comuns do PowerShell](https://technet.microsoft.com/library/hh847884.aspx) sempre são permitidos, mesmo que restrinja os parâmetros disponíveis.</span><span class="sxs-lookup"><span data-stu-id="509f1-148">The [common PowerShell parameters](https://technet.microsoft.com/library/hh847884.aspx) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="509f1-149">Deve não explicitamente listá-los no campo de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="509f1-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="509f1-150">A tabela abaixo descreve as várias formas como pode personalizar uma função ou o cmdlet visível.</span><span class="sxs-lookup"><span data-stu-id="509f1-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="509f1-151">Pode combinar e corresponde a nenhum do abaixo no VisibleCmdlets campo.</span><span class="sxs-lookup"><span data-stu-id="509f1-151">You can mix and match any of the below in the VisibleCmdlets field.</span></span>

<span data-ttu-id="509f1-152">Exemplo</span><span class="sxs-lookup"><span data-stu-id="509f1-152">Example</span></span>                                                                                      | <span data-ttu-id="509f1-153">Caso de utilização</span><span class="sxs-lookup"><span data-stu-id="509f1-153">Use case</span></span>
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="509f1-154">`'My-Func'` ou `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="509f1-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                       | <span data-ttu-id="509f1-155">Permite que o usuário execute `My-Func` sem quaisquer restrições nos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="509f1-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>
`'MyModule\My-Func'`                                                                         | <span data-ttu-id="509f1-156">Permite que o usuário execute `My-Func` do módulo `MyModule` sem quaisquer restrições nos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="509f1-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>
`'My-*'`                                                                                     | <span data-ttu-id="509f1-157">Permite que o usuário execute qualquer cmdlet ou uma função com o verbo `My`.</span><span class="sxs-lookup"><span data-stu-id="509f1-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>
`'*-Func'`                                                                                   | <span data-ttu-id="509f1-158">Permite que o usuário execute qualquer cmdlet ou uma função com o substantivo `Func`.</span><span class="sxs-lookup"><span data-stu-id="509f1-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | <span data-ttu-id="509f1-159">Permite que o usuário execute `My-Func` com o `Param1` e/ou `Param2` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="509f1-159">Allows the user to run `My-Func` with the `Param1` and/or `Param2` parameters.</span></span> <span data-ttu-id="509f1-160">Qualquer valor pode ser fornecido para os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="509f1-160">Any value can be supplied to the parameters.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | <span data-ttu-id="509f1-161">Permite que o usuário execute `My-Func` com o `Param1` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="509f1-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="509f1-162">Apenas "Value1" e "Value2" podem ser fornecidos para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="509f1-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | <span data-ttu-id="509f1-163">Permite que o usuário execute `My-Func` com o `Param1` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="509f1-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="509f1-164">Qualquer valor a partir do "contoso" pode ser fornecido para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="509f1-164">Any value starting with "contoso" can be supplied to the parameter.</span></span>

> [!WARNING]
> <span data-ttu-id="509f1-165">Para melhores práticas de segurança, não é recomendado para utilizar carateres universais, quando se definem cmdlets visível ou funções.</span><span class="sxs-lookup"><span data-stu-id="509f1-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span>
> <span data-ttu-id="509f1-166">Em vez disso, deve listar explicitamente cada comando confiável para garantir que nenhum outro comando que partilham o mesmo esquema de nomenclatura inadvertidamente está autorizado.</span><span class="sxs-lookup"><span data-stu-id="509f1-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="509f1-167">Não é possível aplicar um ValidatePattern e ValidateSet para o mesmo cmdlet ou função.</span><span class="sxs-lookup"><span data-stu-id="509f1-167">You cannot apply both a ValidatePattern and ValidateSet to the same cmdlet or function.</span></span>

<span data-ttu-id="509f1-168">Se o fizer, o ValidatePattern irá substituir o ValidateSet.</span><span class="sxs-lookup"><span data-stu-id="509f1-168">If you do, the ValidatePattern will override the ValidateSet.</span></span>

<span data-ttu-id="509f1-169">Para obter mais informações sobre ValidatePattern, confira [isso *Hey, Scripting Guy!* publicar](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) e o [expressões regulares do PowerShell](https://technet.microsoft.com/library/hh847880.aspx) conteúdo de referência.</span><span class="sxs-lookup"><span data-stu-id="509f1-169">For more information about ValidatePattern, check out [this *Hey, Scripting Guy!* post](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](https://technet.microsoft.com/library/hh847880.aspx) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="509f1-170">Permitir que os comandos externos e scripts do PowerShell</span><span class="sxs-lookup"><span data-stu-id="509f1-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="509f1-171">Para permitir que os usuários executem executáveis e scripts do PowerShell (. ps1) numa sessão JEA, terá de adicionar o caminho completo para cada programa no campo VisibleExternalCommands.</span><span class="sxs-lookup"><span data-stu-id="509f1-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the VisibleExternalCommands field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="509f1-172">Recomenda-se, sempre que possível utilizar o PowerShell equivalentes de cmdlet/função de quaisquer executáveis externos que autorizar, uma vez que tem controle sobre quais os parâmetros são permitidos com cmdlets do PowerShell/funções.</span><span class="sxs-lookup"><span data-stu-id="509f1-172">It is advised, where possible, to use PowerShell cmdlet/function equivalents of any external executables you authorize since you have control over which parameters are allowed with PowerShell cmdlets/functions.</span></span>

<span data-ttu-id="509f1-173">Número de executáveis permite ao ler o estado atual e, em seguida, altere-o apenas ao fornecer parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="509f1-173">Many executables allow you to both read the current state and then change it just by providing different parameters.</span></span>

<span data-ttu-id="509f1-174">Por exemplo, considere a função de um administrador de servidor de ficheiro que deseja verificar quais compartilhamentos de rede estão alojados pelo computador local.</span><span class="sxs-lookup"><span data-stu-id="509f1-174">For example, consider the role of a file server admin who wants to check which network shares are hosted by the local machine.</span></span>
<span data-ttu-id="509f1-175">Uma forma de verificar é usar `net share`.</span><span class="sxs-lookup"><span data-stu-id="509f1-175">One way to check is to use `net share`.</span></span>
<span data-ttu-id="509f1-176">No entanto, permitindo que net.exe é muito perigoso porque o administrador pode facilmente utilizar o comando para obter privilégios de administrador com `net group Administrators unprivilegedjeauser /add`.</span><span class="sxs-lookup"><span data-stu-id="509f1-176">However, allowing net.exe is very dangerous because the admin could just as easily use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span>
<span data-ttu-id="509f1-177">Uma abordagem melhor é permitir que [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) que ofereça o mesmo resultado, mas tem um âmbito muito mais limitado.</span><span class="sxs-lookup"><span data-stu-id="509f1-177">A better approach is to allow [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="509f1-178">Ao disponibilizar comandos externos para os usuários numa sessão JEA, sempre Especifica o caminho completo para o executável para garantir um programa com o mesmo nome (e potencialmente malicioso) colocado em outro lugar no sistema não é executado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="509f1-178">When making external commands available to users in a JEA session, always specify the complete path to the executable to ensure a similarly named (and potentially malicious) program placed elsewhere on the system does not get executed instead.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="509f1-179">Permitir o acesso aos provedores de PowerShell</span><span class="sxs-lookup"><span data-stu-id="509f1-179">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="509f1-180">Por predefinição, não existem fornecedores de PowerShell estão disponíveis em sessões JEA.</span><span class="sxs-lookup"><span data-stu-id="509f1-180">By default, no PowerShell providers are available in JEA sessions.</span></span>

<span data-ttu-id="509f1-181">Isto é principalmente para reduzir o risco de informações confidenciais e definições de configuração que está a ser reveladas para o usuário conectado.</span><span class="sxs-lookup"><span data-stu-id="509f1-181">This is primarily to reduce the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="509f1-182">Quando for necessário, pode permitir o acesso para os fornecedores de PowerShell utilizando o `VisibleProviders` comando.</span><span class="sxs-lookup"><span data-stu-id="509f1-182">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span>
<span data-ttu-id="509f1-183">Para obter uma lista completa dos fornecedores, executar `Get-PSProvider`.</span><span class="sxs-lookup"><span data-stu-id="509f1-183">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="509f1-184">Para tarefas simples que necessitam de acesso para o sistema de arquivos, registro, arquivo de certificados ou outros fornecedores de serviços confidenciais, também pode considerar o escrever uma função personalizada que funciona com o fornecedor em nome do utilizador.</span><span class="sxs-lookup"><span data-stu-id="509f1-184">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, you can also consider writing a custom function that works with the provider on the user's behalf.</span></span>
<span data-ttu-id="509f1-185">As funções, cmdlets e programas externos que estão disponíveis numa sessão JEA não estão sujeitas às mesmas restrições quanto como JEA--eles podem aceder a qualquer fornecedor por padrão.</span><span class="sxs-lookup"><span data-stu-id="509f1-185">Functions, cmdlets, and external programs that are available in a JEA session are not subject to the same constraints as JEA -- they can access any provider by default.</span></span>
<span data-ttu-id="509f1-186">Considere também a utilização a [unidade utilizador](session-configurations.md#user-drive) quando é necessário copiar os ficheiros de/para um ponto final JEA.</span><span class="sxs-lookup"><span data-stu-id="509f1-186">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to/from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="509f1-187">Criar funções personalizadas</span><span class="sxs-lookup"><span data-stu-id="509f1-187">Creating custom functions</span></span>

<span data-ttu-id="509f1-188">Pode criar funções personalizadas num arquivo de recurso de função para simplificar as tarefas complexas para seus usuários finais.</span><span class="sxs-lookup"><span data-stu-id="509f1-188">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span>
<span data-ttu-id="509f1-189">Funções personalizadas também são úteis quando necessitar de lógica de validação avançada para valores de parâmetros de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="509f1-189">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span>
<span data-ttu-id="509f1-190">Pode escrever funções simples no **FunctionDefinitions** campo:</span><span class="sxs-lookup"><span data-stu-id="509f1-190">You can write simple functions in the **FunctionDefinitions** field:</span></span>

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
> <span data-ttu-id="509f1-191">Não se esqueça de adicionar o nome das suas funções personalizadas para o **VisibleFunctions** campo para que podem ser executadas pelos utilizadores JEA.</span><span class="sxs-lookup"><span data-stu-id="509f1-191">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>

<span data-ttu-id="509f1-192">O corpo (bloco de script) de funções personalizadas é executado no modo de idioma predefinido para o sistema e não está sujeita a restrições de idioma da JEA.</span><span class="sxs-lookup"><span data-stu-id="509f1-192">The body (script block) of custom functions runs in the default language mode for the system and is not subject to JEA's language constraints.</span></span>
<span data-ttu-id="509f1-193">Isso significa que as funções podem aceder ao sistema de arquivos e registro e executar comandos que não foram feitos visível no arquivo de recurso de função.</span><span class="sxs-lookup"><span data-stu-id="509f1-193">This means that functions can access the file system and registry, and run commands that were not made visible in the role capability file.</span></span>
<span data-ttu-id="509f1-194">Tenha cuidado para evitar a permitir que código arbitrário a ser executada quando o uso de parâmetros e evitar diretamente para os cmdlets, como a entrada do usuário de piping `Invoke-Expression`.</span><span class="sxs-lookup"><span data-stu-id="509f1-194">Take care to avoid allowing arbitrary code to be run when using parameters and avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="509f1-195">No exemplo acima, irá notar que o nome de módulo completamente qualificado (FQMN) `Microsoft.PowerShell.Utility\Select-Object` foi utilizado em vez da forma abreviada `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="509f1-195">In the above example, you will notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="509f1-196">Funções definidas nos arquivos de recurso de função são ainda pode ser o escopo de sessões JEA, que inclui as funções de proxy JEA cria para restringir comandos existentes.</span><span class="sxs-lookup"><span data-stu-id="509f1-196">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="509f1-197">Select-Object é um padrão, o cmdlet restrita em todas as sessões JEA que não permite que selecione propriedades arbitrárias em objetos.</span><span class="sxs-lookup"><span data-stu-id="509f1-197">Select-Object is a default, constrained cmdlet in all JEA sessions that doesn't allow you to select arbitrary properties on objects.</span></span>
<span data-ttu-id="509f1-198">Para utilizar o Select-Object irrestrita nas funções, tem de solicitar explicitamente a implementação completa, especificando o FQMN.</span><span class="sxs-lookup"><span data-stu-id="509f1-198">To use the unconstrained Select-Object in functions, you must explicitly request the full implementation by specifying the FQMN.</span></span>
<span data-ttu-id="509f1-199">Qualquer cmdlet restrita numa sessão JEA exibirão o mesmo comportamento quando invocado a partir de uma função, seguindo a linha do PowerShell [precedência de comandos](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span><span class="sxs-lookup"><span data-stu-id="509f1-199">Any constrained cmdlet in a JEA session will exhibit the same behavior when invoked from a function, in line with PowerShell's [command precedence](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="509f1-200">Se estiver a escrever muitas funções personalizadas, pode ser mais fácil de colocá-los [módulo de Script do PowerShell](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="509f1-200">If you are writing a lot of custom functions, it may be easier to put them in a [PowerShell Script Module](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx).</span></span>
<span data-ttu-id="509f1-201">Em seguida, pode tornar essas funções visível na sessão usando o campo de VisibleFunctions como faria com módulos de terceiros, incorporados e JEA.</span><span class="sxs-lookup"><span data-stu-id="509f1-201">You can then make those functions visible in the JEA session using the VisibleFunctions field like you would with built-in and third party modules.</span></span>

## <a name="place-role-capabilities-in-a-module"></a><span data-ttu-id="509f1-202">Funcionalidades de função local num módulo</span><span class="sxs-lookup"><span data-stu-id="509f1-202">Place role capabilities in a module</span></span>

<span data-ttu-id="509f1-203">Por ordem para o PowerShell localizar um ficheiro de recurso de função, ele deve ser armazenado numa pasta "RoleCapabilities" num módulo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="509f1-203">In order for PowerShell to find a role capability file, it must be stored in a "RoleCapabilities" folder in a PowerShell module.</span></span>
<span data-ttu-id="509f1-204">O módulo pode ser armazenado em qualquer pasta incluída no `$env:PSModulePath` variável de ambiente, no entanto, deve não colocá-lo na System32 (reservado para módulos internos) ou uma pasta em que o não fidedigno, os utilizadores a ligar foi possível modificar os ficheiros.</span><span class="sxs-lookup"><span data-stu-id="509f1-204">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you should not place it in System32 (reserved for built-in modules) or a folder where the untrusted, connecting users could modify the files.</span></span>
<span data-ttu-id="509f1-205">Segue-se um exemplo de criação de um módulo de script de PowerShell básico chamado *ContosoJEA* no caminho "Arquivos de programas".</span><span class="sxs-lookup"><span data-stu-id="509f1-205">Below is an example of creating a basic PowerShell script module called *ContosoJEA* in the "Program Files" path.</span></span>

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

<span data-ttu-id="509f1-206">Ver [Noções básicas sobre um módulo do PowerShell](https://msdn.microsoft.com/library/dd878324.aspx) para obter mais informações sobre os módulos do PowerShell, manifestos de módulo e a variável de ambiente de PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="509f1-206">See [Understanding a PowerShell Module](https://msdn.microsoft.com/library/dd878324.aspx) for more information about PowerShell modules, module manifests, and the PSModulePath environment variable.</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="509f1-207">Atualizar funcionalidades de função</span><span class="sxs-lookup"><span data-stu-id="509f1-207">Updating role capabilities</span></span>

<span data-ttu-id="509f1-208">Pode atualizar um ficheiro de recurso de função em qualquer altura ao simplesmente a guardar as alterações no arquivo de recurso de função.</span><span class="sxs-lookup"><span data-stu-id="509f1-208">You can update a role capability file at any time by simply saving changes to the role capability file.</span></span>
<span data-ttu-id="509f1-209">Quaisquer novas sessões JEA iniciados depois do recurso de função foi atualizado irão refletir as capacidades revisadas.</span><span class="sxs-lookup"><span data-stu-id="509f1-209">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="509f1-210">É por isso controlar o acesso para a pasta de recursos de função é tão importante.</span><span class="sxs-lookup"><span data-stu-id="509f1-210">This is why controlling access to the role capabilities folder is so important.</span></span>
<span data-ttu-id="509f1-211">Apenas administradores altamente fidedignos devem ser capazes de alterar os arquivos de recurso de função.</span><span class="sxs-lookup"><span data-stu-id="509f1-211">Only highly trusted administrators should be able to change role capability files.</span></span>
<span data-ttu-id="509f1-212">Se um usuário não confiável pode alterar os arquivos de recurso de função, eles podem facilmente atribuir acesso aos cmdlets que permitem-los elevar seus privilégios.</span><span class="sxs-lookup"><span data-stu-id="509f1-212">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets which allow them to elevate their privileges.</span></span>

<span data-ttu-id="509f1-213">Para administradores que procuram para bloquear o acesso a funcionalidades de função, certifique-se de que o sistema Local tem acesso de leitura aos ficheiros de recurso de função e módulos que contêm.</span><span class="sxs-lookup"><span data-stu-id="509f1-213">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="509f1-214">Como as funcionalidades de função são intercaladas</span><span class="sxs-lookup"><span data-stu-id="509f1-214">How role capabilities are merged</span></span>

<span data-ttu-id="509f1-215">Os utilizadores podem ser concedidos acesso às várias funcionalidades de função quando entram numa sessão JEA consoante os mapeamentos de função na [o ficheiro de configuração de sessão](session-configurations.md).</span><span class="sxs-lookup"><span data-stu-id="509f1-215">Users can be granted access to multiple role capabilities when they enter a JEA session depending on the role mappings in the [session configuration file](session-configurations.md).</span></span>
<span data-ttu-id="509f1-216">Quando isto acontecer, JEA tenta dar ao usuário a *mais permissivo* conjunto de comandos permitidos por qualquer uma das funções.</span><span class="sxs-lookup"><span data-stu-id="509f1-216">When this happens, JEA tries to give the user the *most permissive* set of commands allowed by any of the roles.</span></span>

<span data-ttu-id="509f1-217">**VisibleCmdlets e VisibleFunctions**</span><span class="sxs-lookup"><span data-stu-id="509f1-217">**VisibleCmdlets and VisibleFunctions**</span></span>

<span data-ttu-id="509f1-218">A lógica mais complexa de intercalação afeta cmdlets e funções, o que podem ter seus parâmetros e valores de parâmetro nos JEA.</span><span class="sxs-lookup"><span data-stu-id="509f1-218">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="509f1-219">As regras são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="509f1-219">The rules are as follows:</span></span>

1. <span data-ttu-id="509f1-220">Se um cmdlet só ficam visível numa função, é visível para o usuário com quaisquer restrições de parâmetro aplicável.</span><span class="sxs-lookup"><span data-stu-id="509f1-220">If a cmdlet is only made visible in one role, it will be visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="509f1-221">Se um cmdlet ficam visível em mais de uma função, e cada função tem as mesmas restrições sobre o cmdlet, o cmdlet irá ser visível para o usuário com essas restrições.</span><span class="sxs-lookup"><span data-stu-id="509f1-221">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet will be visible to the user with those constraints.</span></span>
3. <span data-ttu-id="509f1-222">Se um cmdlet ficam visível em mais de uma função, e cada função permite que um conjunto diferente de parâmetros, o cmdlet e todos os parâmetros definidos em cada função estarão visíveis para o utilizador.</span><span class="sxs-lookup"><span data-stu-id="509f1-222">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all of the parameters defined across every role will be visible to the user.</span></span> <span data-ttu-id="509f1-223">Se uma função não tiver restrições nos parâmetros, todos os parâmetros serão permitidos.</span><span class="sxs-lookup"><span data-stu-id="509f1-223">If one role doesn't have constraints on the parameters, all parameters will be allowed.</span></span>
4. <span data-ttu-id="509f1-224">Se uma função define um conjunto de validar ou validar padrão para um parâmetro de cmdlet, e a outra função permite que o parâmetro, mas não restrinja os valores de parâmetros, o conjunto de validar ou padrão será ignorada.</span><span class="sxs-lookup"><span data-stu-id="509f1-224">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern will be ignored.</span></span>
5. <span data-ttu-id="509f1-225">Se um conjunto de validar for definido para o mesmo parâmetro de cmdlet em mais de uma função, todos os valores de todos os conjuntos de validar serão permitidos.</span><span class="sxs-lookup"><span data-stu-id="509f1-225">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets will be allowed.</span></span>
6. <span data-ttu-id="509f1-226">Se um padrão de validar for definido para o mesmo parâmetro de cmdlet em mais de uma função, serão permitidos quaisquer valores que correspondam a qualquer um dos padrões.</span><span class="sxs-lookup"><span data-stu-id="509f1-226">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns will be allowed.</span></span>
7. <span data-ttu-id="509f1-227">Se um conjunto de validar é definido numa ou mais funções e um padrão de validar é definido em outra função para o mesmo parâmetro de cmdlet, o conjunto de validar é ignorado e regra (6) aplica-se para os padrões de validar restantes.</span><span class="sxs-lookup"><span data-stu-id="509f1-227">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="509f1-228">Segue-se um exemplo de como as funções são mescladas, de acordo com essas regras:</span><span class="sxs-lookup"><span data-stu-id="509f1-228">Below is an example of how roles are merged according to these rules:</span></span>

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

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

<span data-ttu-id="509f1-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span><span class="sxs-lookup"><span data-stu-id="509f1-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span></span>

<span data-ttu-id="509f1-230">Todos os outros campos no ficheiro de recurso de função são simplesmente adicionados a um conjunto cumulativo de comandos externos permitidos, aliases, provedores e scripts de inicialização.</span><span class="sxs-lookup"><span data-stu-id="509f1-230">All other fields in the role capability file are simply added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span>
<span data-ttu-id="509f1-231">Qualquer comando, o alias, o fornecedor ou o script disponível num recurso de função vai estar disponível para o utilizador JEA.</span><span class="sxs-lookup"><span data-stu-id="509f1-231">Any command, alias, provider, or script available in one role capability will be available to the JEA user.</span></span>

<span data-ttu-id="509f1-232">Tenha cuidado para garantir que o conjunto combinado de provedores a partir de um recurso de função e cmdlets/funções/comandos a partir de outro permite ao ligar aos utilizadores não intencional acesso aos recursos do sistema.</span><span class="sxs-lookup"><span data-stu-id="509f1-232">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another do not allow connecting users unintentional access to system resources.</span></span>
<span data-ttu-id="509f1-233">Por exemplo, se uma função permite que o `Remove-Item` cmdlet e outro permite que o `FileSystem` fornecedor, está em risco de um utilizador JEA a eliminar ficheiros arbitrários no seu computador.</span><span class="sxs-lookup"><span data-stu-id="509f1-233">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span>
<span data-ttu-id="509f1-234">Pode encontrar informações adicionais sobre como identificar as permissões efetivas dos utilizadores no [auditoria tópico JEA](audit-and-report.md).</span><span class="sxs-lookup"><span data-stu-id="509f1-234">Additional information about identifying users' effective permissions can be found in the [auditing JEA topic](audit-and-report.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="509f1-235">Próximos passos</span><span class="sxs-lookup"><span data-stu-id="509f1-235">Next steps</span></span>

- [<span data-ttu-id="509f1-236">Criar um ficheiro de configuração de sessão</span><span class="sxs-lookup"><span data-stu-id="509f1-236">Create a session configuration file</span></span>](session-configurations.md)
