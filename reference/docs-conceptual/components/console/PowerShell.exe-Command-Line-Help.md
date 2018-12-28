---
ms.date: 08/14/2018
keywords: PowerShell, o cmdlet
title: Ajuda da Linha de Comandos PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404878"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="3869a-103">Ajuda da linha de comandos do PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="3869a-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="3869a-104">Pode utilizar PowerShell.exe para iniciar uma sessão do PowerShell a partir da linha de comandos de outra ferramenta, como Cmd.exe, ou usá-lo na linha de comandos do PowerShell para iniciar uma nova sessão.</span><span class="sxs-lookup"><span data-stu-id="3869a-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="3869a-105">Utilize os parâmetros para personalizar a sessão.</span><span class="sxs-lookup"><span data-stu-id="3869a-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="3869a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3869a-106">Syntax</span></span>

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}]
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive]
       [-NoProfile]
       [-OutputFormat {Text | XML}]
       [-PSConsoleFile <FilePath> | -Version <PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="3869a-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3869a-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="3869a-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="3869a-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="3869a-109">Aceita uma versão de cadeia com codificação base-64 de um comando.</span><span class="sxs-lookup"><span data-stu-id="3869a-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="3869a-110">Utilize este parâmetro para enviar comandos para o PowerShell, que requerem aspas complexas ou chavetas.</span><span class="sxs-lookup"><span data-stu-id="3869a-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="3869a-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="3869a-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="3869a-112">Define a política de execução padrão para a sessão atual e guarda-o no $env: PSExecutionPolicyPreference variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="3869a-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="3869a-113">Este parâmetro não altera a diretiva de execução do PowerShell que é definida no registo.</span><span class="sxs-lookup"><span data-stu-id="3869a-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="3869a-114">Para obter informações sobre as políticas de execução do PowerShell, incluindo uma lista de valores válidos, consulte [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="3869a-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="3869a-115">-Arquivo <FilePath> \[ <Parameters>]</span><span class="sxs-lookup"><span data-stu-id="3869a-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="3869a-116">Executa o script especificado no âmbito do local ("dot Source"), para que as funções e variáveis que cria o script estão disponíveis na sessão atual.</span><span class="sxs-lookup"><span data-stu-id="3869a-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="3869a-117">Introduza o caminho do ficheiro de script e quaisquer parâmetros.</span><span class="sxs-lookup"><span data-stu-id="3869a-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="3869a-118">**Ficheiro** tem de ser o último parâmetro no comando.</span><span class="sxs-lookup"><span data-stu-id="3869a-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="3869a-119">Todos os valores que escreveu depois do **-ficheiro** parâmetro são interpretados como o script de caminho do ficheiro e os parâmetros passados para esse script.</span><span class="sxs-lookup"><span data-stu-id="3869a-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="3869a-120">Parâmetros transmitidos para o script são transmitidos como cadeias de caracteres literais, após a interpretação pelo shell atual.</span><span class="sxs-lookup"><span data-stu-id="3869a-120">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="3869a-121">Por exemplo, se estiver no cmd.exe e quiser passar um valor da variável de ambiente, usaria a sintaxe de cmd.exe: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="3869a-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="3869a-122">Por outro lado, executando `powershell.exe -File .\test.ps1 -TestParam $env:windir` nos resultados de cmd.exe no script de receber a cadeia literal `$env:windir` porque não tem nenhum significado especial para o shell cmd.exe atual.</span><span class="sxs-lookup"><span data-stu-id="3869a-122">In contrast, running `powershell.exe -File .\test.ps1 -TestParam $env:windir` in cmd.exe results in the script receiving the literal string `$env:windir` because it has no special meaning to the current cmd.exe shell.</span></span>
<span data-ttu-id="3869a-123">O `$env:windir` estilo de referência de variável de ambiente _pode_ ser utilizado dentro de um `-Command` parâmetro, uma vez que existem será interpretado como o código do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3869a-123">The `$env:windir` style of environment variable reference _can_ be used inside a `-Command` parameter, since there it will be interpreted as PowerShell code.</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="3869a-124">\-InputFormat {texto | XML}</span><span class="sxs-lookup"><span data-stu-id="3869a-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="3869a-125">Descreve o formato dos dados enviados para o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3869a-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="3869a-126">Valores válidos são "Text" (cadeias de texto) ou "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="3869a-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="3869a-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="3869a-127">-Mta</span></span>

<span data-ttu-id="3869a-128">Inicia o PowerShell com um apartment com múltiplos threads.</span><span class="sxs-lookup"><span data-stu-id="3869a-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="3869a-129">Este parâmetro é introduzido no PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="3869a-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="3869a-130">No PowerShell 3.0, single-threaded apartment (STA) é a predefinição.</span><span class="sxs-lookup"><span data-stu-id="3869a-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="3869a-131">No PowerShell 2.0, a predefinição é multithread apartment (MTA).</span><span class="sxs-lookup"><span data-stu-id="3869a-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="3869a-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="3869a-132">-NoExit</span></span>

<span data-ttu-id="3869a-133">Não saia depois de executar comandos de inicialização.</span><span class="sxs-lookup"><span data-stu-id="3869a-133">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="3869a-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="3869a-134">-NoLogo</span></span>

<span data-ttu-id="3869a-135">Oculta a faixa de direitos de autor na inicialização.</span><span class="sxs-lookup"><span data-stu-id="3869a-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="3869a-136">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="3869a-136">-NonInteractive</span></span>

<span data-ttu-id="3869a-137">Não apresentar uma linha de comandos interativa ao usuário.</span><span class="sxs-lookup"><span data-stu-id="3869a-137">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="3869a-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="3869a-138">-NoProfile</span></span>

<span data-ttu-id="3869a-139">Não carrega o perfil do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3869a-139">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="3869a-140">-OutputFormat {texto | XML}</span><span class="sxs-lookup"><span data-stu-id="3869a-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="3869a-141">Determina a forma como o resultado do PowerShell é formatado.</span><span class="sxs-lookup"><span data-stu-id="3869a-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="3869a-142">Valores válidos são "Text" (cadeias de texto) ou "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="3869a-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="3869a-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="3869a-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="3869a-144">Carrega o ficheiro de consola do PowerShell especificado.</span><span class="sxs-lookup"><span data-stu-id="3869a-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="3869a-145">Introduza o caminho e nome do arquivo de console.</span><span class="sxs-lookup"><span data-stu-id="3869a-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="3869a-146">Para criar um arquivo de console, utilize o [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet no PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3869a-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="3869a-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="3869a-147">-Sta</span></span>

<span data-ttu-id="3869a-148">Inicia o PowerShell com um apartamento de thread único.</span><span class="sxs-lookup"><span data-stu-id="3869a-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="3869a-149">No PowerShell 3.0, single-threaded apartment (STA) é a predefinição.</span><span class="sxs-lookup"><span data-stu-id="3869a-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="3869a-150">No PowerShell 2.0, a predefinição é multithread apartment (MTA).</span><span class="sxs-lookup"><span data-stu-id="3869a-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="3869a-151">-Versão <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="3869a-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="3869a-152">Inicia a versão especificada do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3869a-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="3869a-153">A versão que especificar tem de estar instalada no sistema.</span><span class="sxs-lookup"><span data-stu-id="3869a-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="3869a-154">Se o PowerShell 3.0 está instalado no computador, os valores válidos são "2.0" e "3.0".</span><span class="sxs-lookup"><span data-stu-id="3869a-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="3869a-155">O valor predefinido é "3.0".</span><span class="sxs-lookup"><span data-stu-id="3869a-155">The default value is "3.0".</span></span>

<span data-ttu-id="3869a-156">Se o PowerShell 3.0 não estiver instalado, o único valor válido é "2.0".</span><span class="sxs-lookup"><span data-stu-id="3869a-156">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="3869a-157">Outros valores são ignorados.</span><span class="sxs-lookup"><span data-stu-id="3869a-157">Other values are ignored.</span></span>

<span data-ttu-id="3869a-158">Para obter mais informações, consulte [instalar o Windows PowerShell](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="3869a-158">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="3869a-159">-NONE <Window style></span><span class="sxs-lookup"><span data-stu-id="3869a-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="3869a-160">Define o estilo da janela para a sessão.</span><span class="sxs-lookup"><span data-stu-id="3869a-160">Sets the window style for the session.</span></span> <span data-ttu-id="3869a-161">Valores válidos são Normal, minimizado, maximizado e Hidden.</span><span class="sxs-lookup"><span data-stu-id="3869a-161">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="3869a-162">-Comando</span><span class="sxs-lookup"><span data-stu-id="3869a-162">-Command</span></span>

<span data-ttu-id="3869a-163">Executa os comandos especificados (com quaisquer parâmetros) como se eles foram digitados na linha de comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3869a-163">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span>
<span data-ttu-id="3869a-164">Após a execução, PowerShell é encerrado, a menos que o **NoExit** parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="3869a-164">After execution, PowerShell exits unless the **NoExit** parameter is specified.</span></span>
<span data-ttu-id="3869a-165">Qualquer texto depois do `-Command` é enviada como uma única linha de comando para o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3869a-165">Any text after `-Command` is sent as a single command line to PowerShell.</span></span>
<span data-ttu-id="3869a-166">Isso é diferente de como `-File` processa parâmetros enviados para um script.</span><span class="sxs-lookup"><span data-stu-id="3869a-166">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="3869a-167">O valor de `-Command` pode ser "-", uma cadeia de caracteres ou um bloco de script.</span><span class="sxs-lookup"><span data-stu-id="3869a-167">The value of `-Command` can be "-", a string, or a script block.</span></span>
<span data-ttu-id="3869a-168">Os resultados do comando são devolvidos ao shell principal como objetos XML de serialização anulados, objetos não em direto.</span><span class="sxs-lookup"><span data-stu-id="3869a-168">The results of the command are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="3869a-169">Se o valor de `-Command` é "-", o texto do comando é lidos a partir de entrada padrão.</span><span class="sxs-lookup"><span data-stu-id="3869a-169">If the value of `-Command` is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="3869a-170">Quando o valor de `-Command` é uma cadeia de caracteres **comando** _tem_ ser o último parâmetro especificado porque nenhum dos caracteres digitados depois do comando são interpretados como os argumentos de comando.</span><span class="sxs-lookup"><span data-stu-id="3869a-170">When the value of `-Command` is a string, **Command** _must_ be the last parameter specified because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="3869a-171">O **comando** parâmetro só aceita um bloco de script para execução quando ele pode reconhecer o valor transmitido para `-Command` como um tipo de ScriptBlock.</span><span class="sxs-lookup"><span data-stu-id="3869a-171">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to `-Command` as a ScriptBlock type.</span></span>
<span data-ttu-id="3869a-172">Isto é _apenas_ possível durante a execução PowerShell.exe a partir de outro anfitrião do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3869a-172">This is _only_ possible when running PowerShell.exe from another PowerShell host.</span></span>
<span data-ttu-id="3869a-173">O ScriptBlock tipo possa estar contido num existente variável, retornar numa expressão ou analisado os comandos do PowerShell do anfitrião como um bloco de literal script entre chavetas `{}`, antes de que está sendo passada para PowerShell.exe.</span><span class="sxs-lookup"><span data-stu-id="3869a-173">The ScriptBlock type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces `{}`, before being passed to PowerShell.exe.</span></span>

<span data-ttu-id="3869a-174">No cmd.exe, há sem algo como um bloco de script (ou tipo de ScriptBlock), então, o valor transmitido ao **comando** será _sempre_ ser uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3869a-174">In cmd.exe, there is no such thing as a script block (or ScriptBlock type), so the value passed to **Command** will _always_ be a string.</span></span>
<span data-ttu-id="3869a-175">Pode escrever um bloco de script dentro da cadeia, mas em vez de em execução irão comportar-se exatamente como se que o escreveu numa linha de comandos do PowerShell típico, imprimir o conteúdo do script bloquear o novamente para si.</span><span class="sxs-lookup"><span data-stu-id="3869a-175">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="3869a-176">Uma cadeia de caracteres passada para `-Command` ainda será executado como o PowerShell, para que as chaves de bloco por script, muitas vezes, não são necessárias em primeiro lugar quando em execução a partir cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="3869a-176">A string passed to `-Command` will still be executed as PowerShell, so the script block curly braces are often not required in the first place when running from cmd.exe.</span></span>
<span data-ttu-id="3869a-177">Para executar um bloco de script inline definido dentro de uma cadeia de caracteres, o [operador de chamada](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` pode ser utilizado:</span><span class="sxs-lookup"><span data-stu-id="3869a-177">To execute an inline script block defined inside a string, the [call operator](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` can be used:</span></span>

```console
"& {<command>}"
```

### <a name="-help---"></a><span data-ttu-id="3869a-178">-Help,-?, /?</span><span class="sxs-lookup"><span data-stu-id="3869a-178">-Help, -?, /?</span></span>

<span data-ttu-id="3869a-179">Mostra a sintaxe de powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="3869a-179">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="3869a-180">Se estiver escrevendo um comando de PowerShell.exe no PowerShell, preceda os parâmetros de comando com um hífen (-), não uma barra (/).</span><span class="sxs-lookup"><span data-stu-id="3869a-180">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="3869a-181">Pode utilizar um hífen ou de uma barra no Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="3869a-181">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="3869a-182">Nota de Resolução de Problemas: No PowerShell 2.0, a iniciar alguns programas no Windows PowerShell consola não com um LastExitCode de 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="3869a-182">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="3869a-183">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="3869a-183">EXAMPLES</span></span>

```powershell
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a PowerShell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate way to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```
