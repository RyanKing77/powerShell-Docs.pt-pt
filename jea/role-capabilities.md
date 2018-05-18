---
ms.date: 06/12/2017
keywords: jea, powershell, segurança
title: Capacidades de função JEA
ms.openlocfilehash: 0531baa284e66a42a162329ea20ecfdca6d0b526
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="f6845-103">Capacidades de função JEA</span><span class="sxs-lookup"><span data-stu-id="f6845-103">JEA Role Capabilities</span></span>

> <span data-ttu-id="f6845-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f6845-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="f6845-105">Quando criar um ponto final JEA, terá de definir uma ou mais "função capacidades" que descrevem *que* alguém pode efetuar numa sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="f6845-105">When creating a JEA endpoint, you will need to define one or more "role capabilities" which describe *what* someone can do in a JEA session.</span></span>
<span data-ttu-id="f6845-106">Uma capacidade de função é um ficheiro de dados do PowerShell com a extensão de .psrc apresenta uma lista de todos os cmdlets, funções, fornecedores e programas externos que devem ser disponibilizados para os utilizadores a ligar.</span><span class="sxs-lookup"><span data-stu-id="f6845-106">A role capability is a PowerShell data file with the .psrc extension that lists all the cmdlets, functions, providers, and external programs that should be made available to connecting users.</span></span>

<span data-ttu-id="f6845-107">Este tópico descreve como criar um ficheiro de capacidade de função do PowerShell para os seus utilizadores JEA.</span><span class="sxs-lookup"><span data-stu-id="f6845-107">This topic describes how to create a PowerShell role capability file for your JEA users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="f6845-108">Determinar quais os comandos para permitir</span><span class="sxs-lookup"><span data-stu-id="f6845-108">Determine which commands to allow</span></span>

<span data-ttu-id="f6845-109">O primeiro passo quando criar um ficheiro de capacidade da função está a ter em consideração que os utilizadores a quem são atribuídos a função terá acesso a.</span><span class="sxs-lookup"><span data-stu-id="f6845-109">The first step when creating a role capability file is to consider what the users who are assigned the role will need access to.</span></span>
<span data-ttu-id="f6845-110">Este processo de recolha de requisitos podem demorar algum tempo, mas é um processo muito importante.</span><span class="sxs-lookup"><span data-stu-id="f6845-110">This requirements gathering process can take a while, but it is a very important process.</span></span>
<span data-ttu-id="f6845-111">Fornecer acesso de utilizadores à poucos cmdlets e funções pode impedi-los obtenham o trabalho feito.</span><span class="sxs-lookup"><span data-stu-id="f6845-111">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span>
<span data-ttu-id="f6845-112">Permitir o acesso à demasiados cmdlets e funções pode levar aos utilizadores efetuar mais do que o pretendido com os respetivos privilégios de administrador implícita, weakening a sua postura perante o segurança.</span><span class="sxs-lookup"><span data-stu-id="f6845-112">Allowing access to too many cmdlets and functions can lead to users doing more than you intended with their implicit admin privileges, weakening your security stance.</span></span>

<span data-ttu-id="f6845-113">Como aceda sobre este processo irá depender da organização e os objetivos, no entanto, as sugestões seguintes podem ajudar a assegurar que está no caminho certo.</span><span class="sxs-lookup"><span data-stu-id="f6845-113">How you go about this process will depend on your organization and goals, however the following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="f6845-114">**Identificar** os utilizadores de comandos estiver a utilizar para obter as respetivas tarefas causadas.</span><span class="sxs-lookup"><span data-stu-id="f6845-114">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="f6845-115">Isto poderá envolver o método surveying equipa de TI, a verificação de scripts de automatização ou analisar registos ou transcrições de sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f6845-115">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts or logs.</span></span>
2. <span data-ttu-id="f6845-116">**Atualização** utilizar das ferramentas de linha de comandos para PowerShell equivalentes, sempre que possível, para o melhor de auditoria e a experiência de personalização de JEA.</span><span class="sxs-lookup"><span data-stu-id="f6845-116">**Update** use of command line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="f6845-117">Programas externos não podem estar limitados como granularly como os cmdlets do PowerShell nativos e funções no JEA.</span><span class="sxs-lookup"><span data-stu-id="f6845-117">External programs cannot be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="f6845-118">**Restringir** o âmbito dos cmdlets se for necessário para apenas permite parâmetros específicos ou valores de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f6845-118">**Restrict** the scope of the cmdlets if necessary to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="f6845-119">Isto é especialmente importante se os utilizadores só devem ser capazes de gerir a parte de um sistema.</span><span class="sxs-lookup"><span data-stu-id="f6845-119">This is particularly important if users should only be able to manage part of a system.</span></span>
4. <span data-ttu-id="f6845-120">**Criar** funções personalizadas para substituir comandos complexos ou comandos que são difíceis de restringir no JEA.</span><span class="sxs-lookup"><span data-stu-id="f6845-120">**Create** custom functions to replace complex commands or commands which are difficult to constrain in JEA.</span></span> <span data-ttu-id="f6845-121">Uma função simple que encapsula num wrapper um comando complexo ou se aplica a lógica de validação adicionais pode oferecer controlo adicional para administradores e pelo utilizador final simplicidade.</span><span class="sxs-lookup"><span data-stu-id="f6845-121">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="f6845-122">**Teste** a lista de âmbito de comandos permitidos com os utilizadores e/ou a automatização de serviços e ajustar conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="f6845-122">**Test** the scoped list of allowable commands with your users and/or automation services and adjust as necessary.</span></span>

<span data-ttu-id="f6845-123">É importante lembrar-se de que os comandos numa sessão JEA, muitas vezes, são privilégios executar com o administrador (ou, caso contrário elevada).</span><span class="sxs-lookup"><span data-stu-id="f6845-123">It is important to remember that commands in a JEA session are often run with admin (or otherwise elevated) privileges.</span></span>
<span data-ttu-id="f6845-124">A seleção tenha o cuidado de comandos disponíveis é importante certificar-se de que o ponto final JEA não permite que o utilizador ao ligar as respetivas permissões de elevação.</span><span class="sxs-lookup"><span data-stu-id="f6845-124">Careful selection of available commands is important to ensure the JEA endpoint does not allow the connecting user to elevate their permissions.</span></span>
<span data-ttu-id="f6845-125">Seguem-se alguns exemplos de comandos que podem ser utilizados como se permitido num Estado.</span><span class="sxs-lookup"><span data-stu-id="f6845-125">Below are some examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span>
<span data-ttu-id="f6845-126">Tenha em atenção que isto não é uma lista exaustiva e só deve ser utilizado como um ponto de partida cautelar de começar por.</span><span class="sxs-lookup"><span data-stu-id="f6845-126">Note that this is not an exhaustive list and should only be used as a cautionary starting point.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="f6845-127">Exemplos de comandos potencialmente perigosos</span><span class="sxs-lookup"><span data-stu-id="f6845-127">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="f6845-128">Risco</span><span class="sxs-lookup"><span data-stu-id="f6845-128">Risk</span></span> | <span data-ttu-id="f6845-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6845-129">Example</span></span> | <span data-ttu-id="f6845-130">Comandos relacionados</span><span class="sxs-lookup"><span data-stu-id="f6845-130">Related commands</span></span>
-----|---------|-----------------
<span data-ttu-id="f6845-131">Conceder privilégios de administrador para ignorar JEA do utilizador ao ligar</span><span class="sxs-lookup"><span data-stu-id="f6845-131">Granting the connecting user admin privileges to bypass JEA</span></span> | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="f6845-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="f6845-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>
<span data-ttu-id="f6845-133">Executar código arbitrário, como software maligno, exploits ou scripts personalizados para ignorar proteções</span><span class="sxs-lookup"><span data-stu-id="f6845-133">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'` | <span data-ttu-id="f6845-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="f6845-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span>

## <a name="create-a-role-capability-file"></a><span data-ttu-id="f6845-135">Criar um ficheiro de capacidade de função</span><span class="sxs-lookup"><span data-stu-id="f6845-135">Create a role capability file</span></span>

<span data-ttu-id="f6845-136">Pode criar um novo ficheiro de capacidade de função de PowerShell com o [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f6845-136">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="f6845-137">O ficheiro de capacidade de função resultante pode ser aberto num editor de texto e modificado para permitir que os comandos pretendidos para a função.</span><span class="sxs-lookup"><span data-stu-id="f6845-137">The resulting role capability file can be opened in a text editor and modified to allow the desired commands for the role.</span></span>
<span data-ttu-id="f6845-138">A documentação de ajuda do PowerShell contém vários exemplos de como pode configurar o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="f6845-138">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="f6845-139">Permitir que as funções e cmdlets do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6845-139">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="f6845-140">Para autorizar os utilizadores a executar os cmdlets do PowerShell ou as funções, adicione o nome do cmdlet ou uma função para os campos VisbibleCmdlets ou VisibleFunctions.</span><span class="sxs-lookup"><span data-stu-id="f6845-140">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisbibleCmdlets or VisibleFunctions fields.</span></span>
<span data-ttu-id="f6845-141">Se não tem a certeza se um comando é um cmdlet ou uma função, pode executar `Get-Command <name>` e verificar a propriedade "CommandType" na saída.</span><span class="sxs-lookup"><span data-stu-id="f6845-141">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the "CommandType" property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="f6845-142">Por vezes, o âmbito de um cmdlet específico ou a função é demasiado abrangente para as necessidades dos seus utilizadores.</span><span class="sxs-lookup"><span data-stu-id="f6845-142">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span>
<span data-ttu-id="f6845-143">Um administrador DNS, por exemplo, provavelmente, só tem de aceder para reiniciar o serviço DNS.</span><span class="sxs-lookup"><span data-stu-id="f6845-143">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span>
<span data-ttu-id="f6845-144">Num ambiente multi-inquilino onde inquilinos são concedidos acesso aos ferramentas de gestão personalizado, os inquilinos devem ser limitados para gestão com os seus próprios recursos.</span><span class="sxs-lookup"><span data-stu-id="f6845-144">In a multi-tenant environment where tenants are granted access to self-service management tools, tenants should be limited to managing with their own resources.</span></span>
<span data-ttu-id="f6845-145">Nestes casos, pode restringir os parâmetros são expostos a partir de uma função ou o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f6845-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

<span data-ttu-id="f6845-146">Em cenários mais avançados, também poderá ter de restringir os valores que alguém pode fornecer estes parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f6845-146">In more advanced scenarios, you may also need to restrict which values someone can supply to these parameters.</span></span>
<span data-ttu-id="f6845-147">Capacidades de função permitem-lhe definir um conjunto de valores permitidos ou um padrão de expressão regular que é avaliado para determinar se é permitida uma entrada fornecida.</span><span class="sxs-lookup"><span data-stu-id="f6845-147">Role capabilities let you define a set of allowed values or a regular expression pattern that is evaluated to determine if a given input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="f6845-148">O [parâmetros comuns do PowerShell](https://technet.microsoft.com/library/hh847884.aspx) são sempre permitidas, mesmo se restringir os parâmetros disponíveis.</span><span class="sxs-lookup"><span data-stu-id="f6845-148">The [common PowerShell parameters](https://technet.microsoft.com/library/hh847884.aspx) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="f6845-149">A não deve explicitamente listá-los no campo de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f6845-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="f6845-150">A tabela abaixo descreve as várias formas como pode personalizar um cmdlet visível ou uma função.</span><span class="sxs-lookup"><span data-stu-id="f6845-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="f6845-151">Pode combinar e corresponde a nenhum do abaixo no VisibleCmdlets campo.</span><span class="sxs-lookup"><span data-stu-id="f6845-151">You can mix and match any of the below in the VisibleCmdlets field.</span></span>

<span data-ttu-id="f6845-152">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6845-152">Example</span></span>                                                                                      | <span data-ttu-id="f6845-153">Caso de utilização</span><span class="sxs-lookup"><span data-stu-id="f6845-153">Use case</span></span>
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="f6845-154">`'My-Func'` ou `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="f6845-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                       | <span data-ttu-id="f6845-155">Permite que o utilizador executar `My-Func` sem restrições nos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f6845-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>
`'MyModule\My-Func'`                                                                         | <span data-ttu-id="f6845-156">Permite que o utilizador executar `My-Func` do módulo `MyModule` sem restrições nos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f6845-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>
`'My-*'`                                                                                     | <span data-ttu-id="f6845-157">Permite ao utilizador executar qualquer cmdlet ou uma função com o verbo `My`.</span><span class="sxs-lookup"><span data-stu-id="f6845-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>
`'*-Func'`                                                                                   | <span data-ttu-id="f6845-158">Permite ao utilizador executar qualquer cmdlet ou uma função com o substantivo `Func`.</span><span class="sxs-lookup"><span data-stu-id="f6845-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | <span data-ttu-id="f6845-159">Permite que o utilizador executar `My-Func` com o `Param1` e/ou `Param2` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f6845-159">Allows the user to run `My-Func` with the `Param1` and/or `Param2` parameters.</span></span> <span data-ttu-id="f6845-160">Qualquer valor pode ser fornecida para os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f6845-160">Any value can be supplied to the parameters.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | <span data-ttu-id="f6845-161">Permite que o utilizador executar `My-Func` com o `Param1` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f6845-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="f6845-162">Apenas "Value1" e "Value2" podem ser fornecido para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f6845-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | <span data-ttu-id="f6845-163">Permite que o utilizador executar `My-Func` com o `Param1` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f6845-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="f6845-164">Qualquer valor começar com "contoso" pode ser fornecido para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f6845-164">Any value starting with "contoso" can be supplied to the parameter.</span></span>


> [!WARNING]
> <span data-ttu-id="f6845-165">Para melhores práticas de segurança, não se recomenda utilizar carateres universais, quando definir cmdlets visível ou funções.</span><span class="sxs-lookup"><span data-stu-id="f6845-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span>
> <span data-ttu-id="f6845-166">Em vez disso, deve listar explicitamente cada comando fidedigno para garantir que nenhum outro comando que partilham o mesmo esquema de nomenclatura inadvertidamente está autorizado.</span><span class="sxs-lookup"><span data-stu-id="f6845-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="f6845-167">Não é possível aplicar um ValidatePattern e ValidateSet para o mesmo cmdlet ou uma função.</span><span class="sxs-lookup"><span data-stu-id="f6845-167">You cannot apply both a ValidatePattern and ValidateSet to the same cmdlet or function.</span></span>

<span data-ttu-id="f6845-168">Se o fizer, o ValidatePattern irá substituir o ValidateSet.</span><span class="sxs-lookup"><span data-stu-id="f6845-168">If you do, the ValidatePattern will override the ValidateSet.</span></span>

<span data-ttu-id="f6845-169">Para mais informações sobre ValidatePattern, veja [isto *Hey, Scripting Guy!* publique](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) e o [expressões regulares PowerShell](https://technet.microsoft.com/library/hh847880.aspx) conteúdo de referência.</span><span class="sxs-lookup"><span data-stu-id="f6845-169">For more information about ValidatePattern, check out [this *Hey, Scripting Guy!* post](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](https://technet.microsoft.com/library/hh847880.aspx) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="f6845-170">Permitir comandos externos e scripts do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6845-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="f6845-171">Para permitir que os utilizadores executar executáveis e scripts do PowerShell (. ps1) numa sessão JEA, tem de adicionar o caminho completo para cada programa no campo VisibleExternalCommands.</span><span class="sxs-lookup"><span data-stu-id="f6845-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the VisibleExternalCommands field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="f6845-172">É recomendado, sempre que possível utilizar o PowerShell equivalentes de cmdlet/função de qualquer executáveis externo que autorizar uma vez que tem controlo sobre o qual são permitidos parâmetros com os cmdlets do PowerShell/funções.</span><span class="sxs-lookup"><span data-stu-id="f6845-172">It is advised, where possible, to use PowerShell cmdlet/function equivalents of any external executables you authorize since you have control over which parameters are allowed with PowerShell cmdlets/functions.</span></span>

<span data-ttu-id="f6845-173">Executáveis muitos permitem-lhe para o estado atual de leitura e alterá-lo, em seguida, fornecendo diferentes parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f6845-173">Many executables allow you to both read the current state and then change it just by providing different parameters.</span></span>

<span data-ttu-id="f6845-174">Por exemplo, considere a função de um administrador do servidor de ficheiros que pretende verificar as partilhas de rede estão alojadas pelo computador local.</span><span class="sxs-lookup"><span data-stu-id="f6845-174">For example, consider the role of a file server admin who wants to check which network shares are hosted by the local machine.</span></span>
<span data-ttu-id="f6845-175">Uma forma de verificar é utilizar `net share`.</span><span class="sxs-lookup"><span data-stu-id="f6845-175">One way to check is to use `net share`.</span></span>
<span data-ttu-id="f6845-176">No entanto, permitindo net.exe é muito perigosas porque o administrador pode utilizar apenas como facilmente o comando para obter os privilégios de administrador com `net group Administrators unprivilegedjeauser /add`.</span><span class="sxs-lookup"><span data-stu-id="f6845-176">However, allowing net.exe is very dangerous becuase the admin could just as easily use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span>
<span data-ttu-id="f6845-177">Uma abordagem de melhor é permitir [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) que alcance o mesmo resultado mas tem um âmbito muito mais limitado.</span><span class="sxs-lookup"><span data-stu-id="f6845-177">A better approach is to allow [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="f6845-178">Ao disponibilizar comandos externos aos utilizadores numa sessão JEA, sempre especificar o caminho completo para o executável para garantir um programa nome semelhante (e potencialmente malicous) colocado noutro local no sistema de não ser executado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="f6845-178">When making external commands available to users in a JEA session, always specify the complete path to the executable to ensure a similarly named (and potentially malicous) program placed elsewhere on the system does not get executed instead.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="f6845-179">Permitir o acesso aos fornecedores de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6845-179">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="f6845-180">Por predefinição, não existem fornecedores de PowerShell estão disponíveis em sessões JEA.</span><span class="sxs-lookup"><span data-stu-id="f6845-180">By default, no PowerShell providers are available in JEA sessions.</span></span>

<span data-ttu-id="f6845-181">Isto é principalmente reduzir o risco de informações confidenciais e definições de configuração que está a ser divulgadas ao utilizador ao ligar.</span><span class="sxs-lookup"><span data-stu-id="f6845-181">This is primarily to reduce the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="f6845-182">Quando for necessário, pode permitir o acesso aos fornecedores de PowerShell utilizando o `VisibleProviders` comando.</span><span class="sxs-lookup"><span data-stu-id="f6845-182">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span>
<span data-ttu-id="f6845-183">Para obter uma lista completa dos fornecedores, executar `Get-PSProvider`.</span><span class="sxs-lookup"><span data-stu-id="f6845-183">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="f6845-184">Para as tarefas simples que necessitam de acesso para o sistema de ficheiros, o registo, o arquivo de certificados ou outros fornecedores de confidenciais, pode considerar ao escrever uma função personalizada que funciona com o fornecedor em nome do utilizador.</span><span class="sxs-lookup"><span data-stu-id="f6845-184">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, you can also consider writing a custom function that works with the provider on the user's behalf.</span></span>
<span data-ttu-id="f6845-185">Funções, cmdlets e programas externos que estão disponíveis numa sessão JEA não estão sujeitas as restrições mesmas JEA – poderem aceder ao fornecedor de qualquer por predefinição.</span><span class="sxs-lookup"><span data-stu-id="f6845-185">Functions, cmdlets, and external programs that are available in a JEA session are not subject to the same constraints as JEA -- they can access any provider by default.</span></span>
<span data-ttu-id="f6845-186">Considere também a utilização de [unidade utilizador](session-configurations.md#user-drive) quando é necessário copiar ficheiros para/de um ponto final JEA.</span><span class="sxs-lookup"><span data-stu-id="f6845-186">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to/from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="f6845-187">Criar funções personalizadas</span><span class="sxs-lookup"><span data-stu-id="f6845-187">Creating custom functions</span></span>

<span data-ttu-id="f6845-188">Pode criar funções personalizadas num ficheiro de capacidade de função para simplificar as tarefas complexas para os utilizadores finais.</span><span class="sxs-lookup"><span data-stu-id="f6845-188">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span>
<span data-ttu-id="f6845-189">Funções personalizadas também são úteis quando precisa de lógica de validação avançada para os valores de parâmetros de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f6845-189">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span>
<span data-ttu-id="f6845-190">Pode escrever funções simples **FunctionDefinitions** campo:</span><span class="sxs-lookup"><span data-stu-id="f6845-190">You can write simple functions in the **FunctionDefinitions** field:</span></span>

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
> <span data-ttu-id="f6845-191">Não se esqueça de adicionar o nome das suas funções personalizadas para o **VisibleFunctions** campo, pelo que pode ser executados pelos utilizadores JEA.</span><span class="sxs-lookup"><span data-stu-id="f6845-191">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>


<span data-ttu-id="f6845-192">O corpo (bloco de script) de funções personalizadas é executado no modo de idioma predefinido para o sistema e não está sujeito a restrições de idioma do JEA.</span><span class="sxs-lookup"><span data-stu-id="f6845-192">The body (script block) of custom functions runs in the default language mode for the system and is not subject to JEA's language constraints.</span></span>
<span data-ttu-id="f6845-193">Isto significa que funções podem aceder ao sistema de ficheiros e registo e executar comandos que não foram efetuados visível no ficheiro de capacidade de função.</span><span class="sxs-lookup"><span data-stu-id="f6845-193">This means that functions can access the file system and registry, and run commands that were not made visible in the role capability file.</span></span>
<span data-ttu-id="f6845-194">Asseguramos para evitar a permitir que o código arbitrário a ser executada ao utilizar parâmetros e evitar a intervenção do utilizador piping diretamente para os cmdlets, como `Invoke-Expression`.</span><span class="sxs-lookup"><span data-stu-id="f6845-194">Take care to avoid allowing arbitrary code to be run when using parameters and avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="f6845-195">No exemplo acima, irá reparar que o nome do módulo completamente qualificado (FQMN) `Microsoft.PowerShell.Utility\Select-Object` foi utilizado em vez da expressão compacta `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="f6845-195">In the above example, you will notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="f6845-196">Funções definidas nos ficheiros de capacidade de função estão ainda sujeitos o âmbito das sessões JEA, que inclui as funções de proxy JEA cria para restringir os comandos existentes.</span><span class="sxs-lookup"><span data-stu-id="f6845-196">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="f6845-197">Select-Object é uma predefinição, o cmdlet restrita em todas as sessões JEA que não permite que selecione arbitrários propriedades em objetos.</span><span class="sxs-lookup"><span data-stu-id="f6845-197">Select-Object is a default, constrained cmdlet in all JEA sessions that doesn't allow you to select arbitrary properties on objects.</span></span>
<span data-ttu-id="f6845-198">Para utilizar o Select-Object nas funções, tem de solicitar explicitamente a implementação completa, especificando o FQMN.</span><span class="sxs-lookup"><span data-stu-id="f6845-198">To use the unconstrained Select-Object in functions, you must explicitly request the full implementation by specifying the FQMN.</span></span>
<span data-ttu-id="f6845-199">Qualquer cmdlet numa sessão JEA restrita plantas possuir o mesmo comportamento quando invocada a partir de uma função, de acordo com a do PowerShell [precedência de comandos](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span><span class="sxs-lookup"><span data-stu-id="f6845-199">Any constrained cmdlet in a JEA session will exhibit the same behavior when invoked from a function, in line with PowerShell's [command precedence](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="f6845-200">Se estiver a escrever uma grande quantidade de funções personalizadas, poderá ser mais fácil para colocá-los [módulo de Script do PowerShell](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="f6845-200">If you are writing a lot of custom functions, it may be easier to put them in a [PowerShell Script Module](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).</span></span>
<span data-ttu-id="f6845-201">Em seguida, pode efetuar essas funções visíveis na sessão JEA utilizando o campo de VisibleFunctions como faria com módulos incorporados e de terceiros.</span><span class="sxs-lookup"><span data-stu-id="f6845-201">You can then make those functions visible in the JEA session using the VisibleFunctions field like you would with built-in and third party modules.</span></span>

## <a name="place-role-capabilities-in-a-module"></a><span data-ttu-id="f6845-202">Capacidades de função local num módulo</span><span class="sxs-lookup"><span data-stu-id="f6845-202">Place role capabilities in a module</span></span>

<span data-ttu-id="f6845-203">Ordem de PowerShell para localizar um ficheiro de capacidade de função, terá de estar armazenado numa pasta "RoleCapabilities" num módulo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f6845-203">In order for PowerShell to find a role capability file, it must be stored in a "RoleCapabilities" folder in a PowerShell module.</span></span>
<span data-ttu-id="f6845-204">O módulo pode ser armazenado em qualquer pasta incluída no `$env:PSModulePath` variável de ambiente, no entanto, deve não colocá-lo num System32 (reservadas para módulos incorporados) ou uma pasta onde o não fidedigna, os utilizadores a ligar pode modificar os ficheiros.</span><span class="sxs-lookup"><span data-stu-id="f6845-204">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you should not place it in System32 (reserved for built-in modules) or a folder where the untrusted, connecting users could modify the files.</span></span>
<span data-ttu-id="f6845-205">Segue-se um exemplo de criação de um módulo de script do PowerShell básico chamado *ContosoJEA* no caminho "Ficheiros de programa".</span><span class="sxs-lookup"><span data-stu-id="f6845-205">Below is an example of creating a basic PowerShell script module called *ContosoJEA* in the "Program Files" path.</span></span>

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

<span data-ttu-id="f6845-206">Consulte [compreender um módulo do PowerShell](https://msdn.microsoft.com/en-us/library/dd878324.aspx) para obter mais informações sobre o módulos do PowerShell, manifestos de módulo e a variável de ambiente de PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="f6845-206">See [Understanding a PowerShell Module](https://msdn.microsoft.com/en-us/library/dd878324.aspx) for more information about PowerShell modules, module manifests, and the PSModulePath environment variable.</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="f6845-207">Atualizar as capacidades de função</span><span class="sxs-lookup"><span data-stu-id="f6845-207">Updating role capabilities</span></span>


<span data-ttu-id="f6845-208">Pode atualizar um ficheiro de capacidade de função em qualquer altura ao simplesmente a guardar as alterações para o ficheiro de capacidade de função.</span><span class="sxs-lookup"><span data-stu-id="f6845-208">You can update a role capability file at any time by simply saving changes to the role capability file.</span></span>
<span data-ttu-id="f6845-209">Quaisquer novas sessões JEA iniciadas depois da capacidade de função tiver sido atualizada irão refletir as capacidades revistas.</span><span class="sxs-lookup"><span data-stu-id="f6845-209">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="f6845-210">É por isso controlar o acesso à pasta de capacidades de função é tão importante.</span><span class="sxs-lookup"><span data-stu-id="f6845-210">This is why controlling access to the role capabilities folder is so important.</span></span>
<span data-ttu-id="f6845-211">Apenas administradores altamente fidedignos devem poder alterar ficheiros de capacidade de função.</span><span class="sxs-lookup"><span data-stu-id="f6845-211">Only highly trusted administrators should be able to change role capability files.</span></span>
<span data-ttu-id="f6845-212">Se um utilizador não fidedigno pode alterar os ficheiros de capacidade de função, pode facilmente fornecem próprios acesso aos cmdlets que permitem que os seus privilégios de elevação.</span><span class="sxs-lookup"><span data-stu-id="f6845-212">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets which allow them to elevate their privileges.</span></span>


<span data-ttu-id="f6845-213">Para administradores que procuram bloqueio para baixo de acesso para as capacidades de função, certifique-se de que sistema Local tem acesso de leitura aos ficheiros de capacidade de função e os módulos que contêm.</span><span class="sxs-lookup"><span data-stu-id="f6845-213">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="f6845-214">Como são intercaladas capacidades de função</span><span class="sxs-lookup"><span data-stu-id="f6845-214">How role capabilities are merged</span></span>

<span data-ttu-id="f6845-215">Podem ser concedido acesso aos utilizadores várias capacidades de função quando que introduza uma sessão JEA consoante os mapeamentos de função no [ficheiro de configuração de sessão](session-configurations.md).</span><span class="sxs-lookup"><span data-stu-id="f6845-215">Users can be granted access to multiple role capabilities when they enter a JEA session depending on the role mappings in the [session configuration file](session-configurations.md).</span></span>
<span data-ttu-id="f6845-216">Quando isto acontecer, JEA tenta conceder ao utilizador o *mais permissivo* conjunto de comandos permitido por qualquer uma das funções.</span><span class="sxs-lookup"><span data-stu-id="f6845-216">When this happens, JEA tries to give the user the *most permissive* set of commands allowed by any of the roles.</span></span>

<span data-ttu-id="f6845-217">**VisibleCmdlets e VisibleFunctions**</span><span class="sxs-lookup"><span data-stu-id="f6845-217">**VisibleCmdlets and VisibleFunctions**</span></span>

<span data-ttu-id="f6845-218">A lógica de intercalação mais complexa afeta cmdlets e funções, o que podem ter os parâmetros e valores de parâmetro no JEA limitados.</span><span class="sxs-lookup"><span data-stu-id="f6845-218">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="f6845-219">As regras são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="f6845-219">The rules are as follows:</span></span>

1. <span data-ttu-id="f6845-220">Se um cmdlet só ficam visível numa função, vai estar visível ao utilizador com as eventuais restrições no parâmetro aplicável.</span><span class="sxs-lookup"><span data-stu-id="f6845-220">If a cmdlet is only made visible in one role, it will be visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="f6845-221">Se um cmdlet ficam visível em mais de uma função, e cada função tem as mesmas restrições sobre o cmdlet, o cmdlet vai estar visível ao utilizador com essas restrições.</span><span class="sxs-lookup"><span data-stu-id="f6845-221">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet will be visible to the user with those constraints.</span></span>
3. <span data-ttu-id="f6845-222">Se um cmdlet ficam visível em mais de uma função, e cada função permite que um conjunto diferente de parâmetros, o cmdlet e todos os parâmetros definidos em cada função vai estar visíveis ao utilizador.</span><span class="sxs-lookup"><span data-stu-id="f6845-222">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all of the parameters defined across every role will be visible to the user.</span></span> <span data-ttu-id="f6845-223">Se uma função de não ter restrições nos parâmetros, terão permissão de todos os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f6845-223">If one role doesn't have constraints on the parameters, all parameters will be allowed.</span></span>
4. <span data-ttu-id="f6845-224">Se uma função define um conjunto de validar ou validar padrão para um parâmetro de cmdlet, e a outras funções permite que o parâmetro, mas não restringir os valores de parâmetros, o conjunto de validar ou padrão será ignorada.</span><span class="sxs-lookup"><span data-stu-id="f6845-224">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern will be ignored.</span></span>
5. <span data-ttu-id="f6845-225">Se um conjunto de validar está definido para o mesmo parâmetro de cmdlet em mais de uma função, todos os valores de todos os conjuntos de validar serão permitidos.</span><span class="sxs-lookup"><span data-stu-id="f6845-225">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets will be allowed.</span></span>
6. <span data-ttu-id="f6845-226">Se um padrão de validar está definido para o mesmo parâmetro de cmdlet em mais de uma função, os valores que correspondem a nenhum dos padrões de serão permitidos.</span><span class="sxs-lookup"><span data-stu-id="f6845-226">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns will be allowed.</span></span>
7. <span data-ttu-id="f6845-227">Se está definido um conjunto de validar uma ou mais funções e um padrão de validar está definido na outra função para o mesmo parâmetro de cmdlet, o conjunto de validar é ignorado e a regra (6) se aplica os padrões de validar restantes.</span><span class="sxs-lookup"><span data-stu-id="f6845-227">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="f6845-228">Abaixo está um exemplo de como as funções são intercaladas, de acordo com estas regras:</span><span class="sxs-lookup"><span data-stu-id="f6845-228">Below is an example of how roles are merged according to these rules:</span></span>

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



<span data-ttu-id="f6845-229">**VisibleExternalCommands, ScriptsToProcess VisibleAliases, VisibleProviders,**</span><span class="sxs-lookup"><span data-stu-id="f6845-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span></span>

<span data-ttu-id="f6845-230">Todos os outros campos no ficheiro de capacidade de função simplesmente são adicionados a um conjunto cumulativo de comandos externos permitidos, aliases, fornecedores e scripts de arranque.</span><span class="sxs-lookup"><span data-stu-id="f6845-230">All other fields in the role capability file are simply added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span>
<span data-ttu-id="f6845-231">Qualquer comando, alias, fornecedor ou script disponível numa capacidade de função estará disponível para o utilizador JEA.</span><span class="sxs-lookup"><span data-stu-id="f6845-231">Any command, alias, provider, or script available in one role capability will be available to the JEA user.</span></span>

<span data-ttu-id="f6845-232">Tenha cuidado garantir que o conjunto combinado de fornecedores de uma capacidade de função e as funções/cmdlets/comandos de outro não permitem estabelecer ligação aos utilizadores não intencional acesso aos recursos de sistema.</span><span class="sxs-lookup"><span data-stu-id="f6845-232">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another do not allow connecting users unintentional access to system resources.</span></span>
<span data-ttu-id="f6845-233">Por exemplo, se uma função permite que o `Remove-Item` cmdlet e outra permite que o `FileSystem` fornecedor, está em risco de um utilizador JEA eliminar ficheiros arbitrários no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f6845-233">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span>
<span data-ttu-id="f6845-234">Pode encontrar informações adicionais sobre como identificar as permissões efetivas dos utilizadores no [auditoria tópico JEA](audit-and-report.md).</span><span class="sxs-lookup"><span data-stu-id="f6845-234">Additional information about identifying users' effective permissions can be found in the [auditing JEA topic](audit-and-report.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="f6845-235">Próximos passos</span><span class="sxs-lookup"><span data-stu-id="f6845-235">Next steps</span></span>

- [<span data-ttu-id="f6845-236">Criar um ficheiro de configuração de sessão</span><span class="sxs-lookup"><span data-stu-id="f6845-236">Create a session configuration file</span></span>](session-configurations.md)