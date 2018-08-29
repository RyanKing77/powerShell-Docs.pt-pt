---
ms.date: 08/14/2018
keywords: PowerShell, o cmdlet
title: Ajuda da Linha de Comandos PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: c7f35511e876e8e5189d8a2b949555603d43f731
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133868"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="24d22-103">Ajuda da linha de comandos do PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="24d22-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="24d22-104">Pode utilizar PowerShell.exe para iniciar uma sessão do PowerShell a partir da linha de comandos de outra ferramenta, como Cmd.exe, ou usá-lo na linha de comandos do PowerShell para iniciar uma nova sessão.</span><span class="sxs-lookup"><span data-stu-id="24d22-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="24d22-105">Utilize os parâmetros para personalizar a sessão.</span><span class="sxs-lookup"><span data-stu-id="24d22-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="24d22-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="24d22-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="24d22-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="24d22-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="24d22-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="24d22-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="24d22-109">Aceita uma versão de cadeia com codificação base-64 de um comando.</span><span class="sxs-lookup"><span data-stu-id="24d22-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="24d22-110">Utilize este parâmetro para enviar comandos para o PowerShell, que requerem aspas complexas ou chavetas.</span><span class="sxs-lookup"><span data-stu-id="24d22-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="24d22-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="24d22-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="24d22-112">Define a política de execução padrão para a sessão atual e guarda-o no $env: PSExecutionPolicyPreference variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="24d22-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="24d22-113">Este parâmetro não altera a diretiva de execução do PowerShell que é definida no registo.</span><span class="sxs-lookup"><span data-stu-id="24d22-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="24d22-114">Para obter informações sobre as políticas de execução do PowerShell, incluindo uma lista de valores válidos, consulte [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="24d22-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="24d22-115">-Arquivo <FilePath> \[ <Parameters>]</span><span class="sxs-lookup"><span data-stu-id="24d22-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="24d22-116">Executa o script especificado no âmbito do local ("dot Source"), para que as funções e variáveis que cria o script estão disponíveis na sessão atual.</span><span class="sxs-lookup"><span data-stu-id="24d22-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="24d22-117">Introduza o caminho do ficheiro de script e quaisquer parâmetros.</span><span class="sxs-lookup"><span data-stu-id="24d22-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="24d22-118">**Ficheiro** tem de ser o último parâmetro no comando.</span><span class="sxs-lookup"><span data-stu-id="24d22-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="24d22-119">Todos os valores que escreveu depois do **-ficheiro** parâmetro são interpretados como o script de caminho do ficheiro e os parâmetros passados para esse script.</span><span class="sxs-lookup"><span data-stu-id="24d22-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="24d22-120">Parâmetros transmitidos para o script são transmitidos como cadeias de caracteres literais (depois de interpretação pelo shell do atual).</span><span class="sxs-lookup"><span data-stu-id="24d22-120">Parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span> <span data-ttu-id="24d22-121">Por exemplo, se estiver no cmd.exe e quiser passar um valor da variável de ambiente, usaria a sintaxe de cmd.exe: `powershell -File .\test.ps1 -Sample %windir%` neste exemplo, o script recebe a cadeia literal `$env:windir` e não o valor dessa variável ambiental: `powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="24d22-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` In this example, the script receives the literal string `$env:windir` and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="24d22-122">\-InputFormat {texto | XML}</span><span class="sxs-lookup"><span data-stu-id="24d22-122">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="24d22-123">Descreve o formato dos dados enviados para o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24d22-123">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="24d22-124">Valores válidos são "Text" (cadeias de texto) ou "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="24d22-124">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="24d22-125">-Mta</span><span class="sxs-lookup"><span data-stu-id="24d22-125">-Mta</span></span>

<span data-ttu-id="24d22-126">Inicia o PowerShell com um apartment com múltiplos threads.</span><span class="sxs-lookup"><span data-stu-id="24d22-126">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="24d22-127">Este parâmetro é introduzido no PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="24d22-127">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="24d22-128">No PowerShell 3.0, single-threaded apartment (STA) é a predefinição.</span><span class="sxs-lookup"><span data-stu-id="24d22-128">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="24d22-129">No PowerShell 2.0, a predefinição é multithread apartment (MTA).</span><span class="sxs-lookup"><span data-stu-id="24d22-129">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="24d22-130">-NoExit</span><span class="sxs-lookup"><span data-stu-id="24d22-130">-NoExit</span></span>

<span data-ttu-id="24d22-131">Não saia depois de executar comandos de inicialização.</span><span class="sxs-lookup"><span data-stu-id="24d22-131">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="24d22-132">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="24d22-132">-NoLogo</span></span>

<span data-ttu-id="24d22-133">Oculta a faixa de direitos de autor na inicialização.</span><span class="sxs-lookup"><span data-stu-id="24d22-133">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="24d22-134">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="24d22-134">-NonInteractive</span></span>

<span data-ttu-id="24d22-135">Não apresentar uma linha de comandos interativa ao usuário.</span><span class="sxs-lookup"><span data-stu-id="24d22-135">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="24d22-136">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="24d22-136">-NoProfile</span></span>

<span data-ttu-id="24d22-137">Não carrega o perfil do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24d22-137">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="24d22-138">-OutputFormat {texto | XML}</span><span class="sxs-lookup"><span data-stu-id="24d22-138">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="24d22-139">Determina a forma como o resultado do PowerShell é formatado.</span><span class="sxs-lookup"><span data-stu-id="24d22-139">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="24d22-140">Valores válidos são "Text" (cadeias de texto) ou "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="24d22-140">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="24d22-141">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="24d22-141">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="24d22-142">Carrega o ficheiro de consola do PowerShell especificado.</span><span class="sxs-lookup"><span data-stu-id="24d22-142">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="24d22-143">Introduza o caminho e nome do arquivo de console.</span><span class="sxs-lookup"><span data-stu-id="24d22-143">Enter the path and name of the console file.</span></span> <span data-ttu-id="24d22-144">Para criar um arquivo de console, utilize o [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet no PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24d22-144">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="24d22-145">-Sta</span><span class="sxs-lookup"><span data-stu-id="24d22-145">-Sta</span></span>

<span data-ttu-id="24d22-146">Inicia o PowerShell com um apartamento de thread único.</span><span class="sxs-lookup"><span data-stu-id="24d22-146">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="24d22-147">No PowerShell 3.0, single-threaded apartment (STA) é a predefinição.</span><span class="sxs-lookup"><span data-stu-id="24d22-147">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="24d22-148">No PowerShell 2.0, a predefinição é multithread apartment (MTA).</span><span class="sxs-lookup"><span data-stu-id="24d22-148">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="24d22-149">-Versão <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="24d22-149">-Version <PowerShell Version></span></span>

<span data-ttu-id="24d22-150">Inicia a versão especificada do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24d22-150">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="24d22-151">A versão que especificar tem de estar instalada no sistema.</span><span class="sxs-lookup"><span data-stu-id="24d22-151">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="24d22-152">Se o PowerShell 3.0 está instalado no computador, os valores válidos são "2.0" e "3.0".</span><span class="sxs-lookup"><span data-stu-id="24d22-152">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="24d22-153">O valor predefinido é "3.0".</span><span class="sxs-lookup"><span data-stu-id="24d22-153">The default value is "3.0".</span></span>

<span data-ttu-id="24d22-154">Se o PowerShell 3.0 não estiver instalado, o único valor válido é "2.0".</span><span class="sxs-lookup"><span data-stu-id="24d22-154">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="24d22-155">Outros valores são ignorados.</span><span class="sxs-lookup"><span data-stu-id="24d22-155">Other values are ignored.</span></span>

<span data-ttu-id="24d22-156">Para obter mais informações, consulte [instalar o Windows PowerShell](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="24d22-156">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="24d22-157">-NONE <Window style></span><span class="sxs-lookup"><span data-stu-id="24d22-157">-WindowStyle <Window style></span></span>

<span data-ttu-id="24d22-158">Define o estilo da janela para a sessão.</span><span class="sxs-lookup"><span data-stu-id="24d22-158">Sets the window style for the session.</span></span> <span data-ttu-id="24d22-159">Valores válidos são Normal, minimizado, maximizado e Hidden.</span><span class="sxs-lookup"><span data-stu-id="24d22-159">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="24d22-160">-Comando</span><span class="sxs-lookup"><span data-stu-id="24d22-160">-Command</span></span>

<span data-ttu-id="24d22-161">Executa os comandos especificados (com quaisquer parâmetros) como se eles foram digitados na linha de comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24d22-161">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span> <span data-ttu-id="24d22-162">Após a execução, PowerShell é encerrado, a menos que o `-NoExit` parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="24d22-162">After execution, PowerShell exits unless the `-NoExit` parameter is specified.</span></span>
<span data-ttu-id="24d22-163">Qualquer texto depois do `-Command` é enviada como uma única linha de comando para o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24d22-163">Any text after `-Command` is sent as a single command line to PowerShell.</span></span> <span data-ttu-id="24d22-164">Isso é diferente de como `-File` processa parâmetros enviados para um script.</span><span class="sxs-lookup"><span data-stu-id="24d22-164">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="24d22-165">O valor do comando pode ser "-", uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="24d22-165">The value of Command can be "-", a string.</span></span> <span data-ttu-id="24d22-166">ou um bloco de scripts.</span><span class="sxs-lookup"><span data-stu-id="24d22-166">or a script block.</span></span> <span data-ttu-id="24d22-167">Se for o valor do comando "-", o texto do comando é lidos a partir de entrada padrão.</span><span class="sxs-lookup"><span data-stu-id="24d22-167">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="24d22-168">Blocos de script têm de estar entre chavetas ({}).</span><span class="sxs-lookup"><span data-stu-id="24d22-168">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="24d22-169">Pode especificar um bloco de scripts apenas quando executar PowerShell.exe no PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24d22-169">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="24d22-170">Os resultados do script são devolvidos ao shell principal como objetos XML de serialização anulados, objetos não em direto.</span><span class="sxs-lookup"><span data-stu-id="24d22-170">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="24d22-171">Se o valor do comando é uma cadeia de caracteres **comando** tem de ser o último parâmetro no comando, porque qualquer caracteres digitados depois do comando são interpretados como os argumentos de comando.</span><span class="sxs-lookup"><span data-stu-id="24d22-171">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="24d22-172">Para escrever uma cadeia de caracteres que executa um comando do PowerShell, utilize o formato:</span><span class="sxs-lookup"><span data-stu-id="24d22-172">To write a string that runs a PowerShell command, use the format:</span></span>

```powershell
"& {<command>}"
```

<span data-ttu-id="24d22-173">As aspas indicam uma cadeia de caracteres e o operador de invoke (&) faz com que o comando a ser executado.</span><span class="sxs-lookup"><span data-stu-id="24d22-173">The quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="24d22-174">-Help,-?, /?</span><span class="sxs-lookup"><span data-stu-id="24d22-174">-Help, -?, /?</span></span>

<span data-ttu-id="24d22-175">Mostra a sintaxe de powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="24d22-175">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="24d22-176">Se estiver escrevendo um comando de PowerShell.exe no PowerShell, preceda os parâmetros de comando com um hífen (-), não uma barra (/).</span><span class="sxs-lookup"><span data-stu-id="24d22-176">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="24d22-177">Pode utilizar um hífen ou de uma barra no Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="24d22-177">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="24d22-178">Nota de resolução de problemas: No PowerShell 2.0, a partir de alguns programas no Windows PowerShell consola não com um LastExitCode de 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="24d22-178">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="24d22-179">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="24d22-179">EXAMPLES</span></span>

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
