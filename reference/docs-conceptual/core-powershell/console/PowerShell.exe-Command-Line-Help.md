---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Ajuda da linha de comandos PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 262c21e44e509746314ed44d91bb3de16a4b854b
ms.sourcegitcommit: 4807ab554d55fdee499980835bcc279368b1df68
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/07/2017
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="7d5da-103">Ajuda da linha de comandos PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="7d5da-103">PowerShell.exe Command-Line Help</span></span>
<span data-ttu-id="7d5da-104">uma sessão do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d5da-104">a Windows PowerShell session.</span></span> <span data-ttu-id="7d5da-105">Pode utilizar o PowerShell.exe para iniciar uma sessão do PowerShell na linha de comandos de outra ferramenta, tais como Cmd.exe, ou utilizá-lo na linha de comandos do PowerShell para iniciar uma sessão de novo.</span><span class="sxs-lookup"><span data-stu-id="7d5da-105">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="7d5da-106">Utilize os parâmetros para personalizar a sessão.</span><span class="sxs-lookup"><span data-stu-id="7d5da-106">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="7d5da-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7d5da-107">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="7d5da-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7d5da-108">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="7d5da-109">-EncodedCommand<Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="7d5da-109">-EncodedCommand <Base64EncodedCommand></span></span>
<span data-ttu-id="7d5da-110">Aceita uma versão de cadeia com codificação base-64 de um comando.</span><span class="sxs-lookup"><span data-stu-id="7d5da-110">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="7d5da-111">Utilize este parâmetro para submeter os comandos do PowerShell que requerem aspas complexas ou chavetas.</span><span class="sxs-lookup"><span data-stu-id="7d5da-111">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="7d5da-112">-ExecutionPolicy<ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="7d5da-112">-ExecutionPolicy <ExecutionPolicy></span></span>
<span data-ttu-id="7d5da-113">Define a política de execução predefinido para a sessão atual e guarda-o no $env: PSExecutionPolicyPreference variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="7d5da-113">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="7d5da-114">Este parâmetro não altera a política de execução do PowerShell que está definida no registo.</span><span class="sxs-lookup"><span data-stu-id="7d5da-114">This parameter does not change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="7d5da-115">Para obter informações sobre as políticas de execução do PowerShell, incluindo uma lista de valores válidos, consulte about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span><span class="sxs-lookup"><span data-stu-id="7d5da-115">For information about PowerShell execution policies, including a list of valid values, see about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="7d5da-116">-Ficheiro <FilePath> \[ <Parameters>]</span><span class="sxs-lookup"><span data-stu-id="7d5da-116">-File <FilePath> \[<Parameters>]</span></span>
<span data-ttu-id="7d5da-117">Executa o script especificado no âmbito local ("dot-obtido"), para que as funções e as variáveis que cria o script estão disponíveis na sessão atual.</span><span class="sxs-lookup"><span data-stu-id="7d5da-117">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="7d5da-118">Introduza o caminho do ficheiro de script e quaisquer parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7d5da-118">Enter the script file path and any parameters.</span></span> <span data-ttu-id="7d5da-119">**Ficheiro** tem de ser o último parâmetro no comando, porque todos os caracteres escritos após o **ficheiro** nome do parâmetro são interpretados como o caminho do ficheiro de script seguido os parâmetros do script e os respetivos valores.</span><span class="sxs-lookup"><span data-stu-id="7d5da-119">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="7d5da-120">Pode incluir os parâmetros de um script e os valores de parâmetros, o valor da **ficheiro** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7d5da-120">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="7d5da-121">Por exemplo: `-File .\Get-Script.ps1 -Domain Central` tenha em atenção que os parâmetros transmitidos para o script são transmitidos como literal cadeias (após a interpretação através da shell do atual).</span><span class="sxs-lookup"><span data-stu-id="7d5da-121">For example: `-File .\Get-Script.ps1 -Domain Central` Note that parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span>
<span data-ttu-id="7d5da-122">Por exemplo, se estiverem em cmd.exe e pretende transmita um valor de variável de ambiente, teria de utilizar a sintaxe de cmd.exe: `powershell -File .\test.ps1 -Sample %windir%` se pretendesse utilizar a sintaxe do PowerShell, em seguida, neste exemplo, o script receberia o literal "$env: windir" e não o valor do que variável de ambiente:`powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="7d5da-122">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` If you were to use PowerShell syntax, then in this example your script would receive the literal "$env:windir" and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

<span data-ttu-id="7d5da-123">Normalmente, os parâmetros de comutador de um script estiverem incluídos ou for omitidos.</span><span class="sxs-lookup"><span data-stu-id="7d5da-123">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="7d5da-124">Por exemplo, o seguinte comando utiliza o **todos os** parâmetro do ficheiro de script Get-Script.ps1:`-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="7d5da-124">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="7d5da-125">\-InputFormat {texto | XML}</span><span class="sxs-lookup"><span data-stu-id="7d5da-125">\-InputFormat {Text | XML}</span></span>
<span data-ttu-id="7d5da-126">Descreve o formato dos dados enviados para o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d5da-126">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="7d5da-127">Os valores válidos são "Text" (cadeias de texto) ou "XML" (CLIXML o formato serializado).</span><span class="sxs-lookup"><span data-stu-id="7d5da-127">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="7d5da-128">-Mta</span><span class="sxs-lookup"><span data-stu-id="7d5da-128">-Mta</span></span>
<span data-ttu-id="7d5da-129">É iniciado através de um apartment multi-thread do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d5da-129">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="7d5da-130">Este parâmetro é apresentado no PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="7d5da-130">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="7d5da-131">No PowerShell 3.0, single-threaded apartment (STA) é a predefinição.</span><span class="sxs-lookup"><span data-stu-id="7d5da-131">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="7d5da-132">PowerShell 2.0, vários threads apartment (MTA) é a predefinição.</span><span class="sxs-lookup"><span data-stu-id="7d5da-132">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="7d5da-133">-NoExit</span><span class="sxs-lookup"><span data-stu-id="7d5da-133">-NoExit</span></span>
<span data-ttu-id="7d5da-134">Não for fechada depois de executar os comandos de arranque.</span><span class="sxs-lookup"><span data-stu-id="7d5da-134">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="7d5da-135">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="7d5da-135">-NoLogo</span></span>
<span data-ttu-id="7d5da-136">Oculta a faixa de copyright no arranque.</span><span class="sxs-lookup"><span data-stu-id="7d5da-136">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="7d5da-137">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="7d5da-137">-NonInteractive</span></span>
<span data-ttu-id="7d5da-138">Não está presente uma linha de comandos interativa ao utilizador.</span><span class="sxs-lookup"><span data-stu-id="7d5da-138">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="7d5da-139">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="7d5da-139">-NoProfile</span></span>
<span data-ttu-id="7d5da-140">Não carregue o perfil do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d5da-140">Does not load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="7d5da-141">-OutputFormat {texto | XML}</span><span class="sxs-lookup"><span data-stu-id="7d5da-141">-OutputFormat {Text | XML}</span></span>
<span data-ttu-id="7d5da-142">Determina a forma como saída do PowerShell está formatada.</span><span class="sxs-lookup"><span data-stu-id="7d5da-142">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="7d5da-143">Os valores válidos são "Text" (cadeias de texto) ou "XML" (CLIXML o formato serializado).</span><span class="sxs-lookup"><span data-stu-id="7d5da-143">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="7d5da-144">-PSConsoleFile<FilePath></span><span class="sxs-lookup"><span data-stu-id="7d5da-144">-PSConsoleFile <FilePath></span></span>
<span data-ttu-id="7d5da-145">Carrega o ficheiro de consola do PowerShell especificado.</span><span class="sxs-lookup"><span data-stu-id="7d5da-145">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="7d5da-146">Introduza o caminho e nome do ficheiro de consola.</span><span class="sxs-lookup"><span data-stu-id="7d5da-146">Enter the path and name of the console file.</span></span> <span data-ttu-id="7d5da-147">Para criar um ficheiro de consola, utilize o [exportação consola](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d5da-147">To create a console file, use the [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="7d5da-148">-Sta</span><span class="sxs-lookup"><span data-stu-id="7d5da-148">-Sta</span></span>
<span data-ttu-id="7d5da-149">Inicia o PowerShell com um apartamento de thread único.</span><span class="sxs-lookup"><span data-stu-id="7d5da-149">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="7d5da-150">No PowerShell 3.0, single-threaded apartment (STA) é a predefinição.</span><span class="sxs-lookup"><span data-stu-id="7d5da-150">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="7d5da-151">PowerShell 2.0, vários threads apartment (MTA) é a predefinição.</span><span class="sxs-lookup"><span data-stu-id="7d5da-151">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="7d5da-152">-Versão<PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="7d5da-152">-Version <PowerShell Version></span></span>
<span data-ttu-id="7d5da-153">Inicia a versão especificada do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d5da-153">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="7d5da-154">A versão que especificar tem de estar instalada no sistema.</span><span class="sxs-lookup"><span data-stu-id="7d5da-154">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="7d5da-155">Se o PowerShell 3.0 está instalado no computador, os valores válidos são "2.0" e "3.0".</span><span class="sxs-lookup"><span data-stu-id="7d5da-155">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="7d5da-156">O valor predefinido é "3.0".</span><span class="sxs-lookup"><span data-stu-id="7d5da-156">The default value is "3.0".</span></span>

<span data-ttu-id="7d5da-157">Se o PowerShell 3.0 não está instalado, o único valor válido é "2.0".</span><span class="sxs-lookup"><span data-stu-id="7d5da-157">If PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="7d5da-158">Outros valores são ignorados.</span><span class="sxs-lookup"><span data-stu-id="7d5da-158">Other values are ignored.</span></span>

<span data-ttu-id="7d5da-159">Para obter mais informações, consulte "Instalar o PowerShell" no [introdução com o PowerShell [MSDN antigo]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span><span class="sxs-lookup"><span data-stu-id="7d5da-159">For more information, see "Installing PowerShell" in the [Getting Started with PowerShell [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="7d5da-160">-WindowStyle<Window style></span><span class="sxs-lookup"><span data-stu-id="7d5da-160">-WindowStyle <Window style></span></span>
<span data-ttu-id="7d5da-161">Define o estilo de janela para a sessão.</span><span class="sxs-lookup"><span data-stu-id="7d5da-161">Sets the window style for the session.</span></span> <span data-ttu-id="7d5da-162">Os valores válidos são Normal, minimizado, maximizado e oculto.</span><span class="sxs-lookup"><span data-stu-id="7d5da-162">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="7d5da-163">-Comando</span><span class="sxs-lookup"><span data-stu-id="7d5da-163">-Command</span></span>
<span data-ttu-id="7d5da-164">Executa os comandos especificados (e quaisquer parâmetros) como se se tratasse foram escritas na linha de comandos do PowerShell e, em seguida, sai, a menos que o parâmetro NoExit for especificado.</span><span class="sxs-lookup"><span data-stu-id="7d5da-164">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>
<span data-ttu-id="7d5da-165">Essencialmente, qualquer texto após `-Command` é enviada como uma única linha de comandos para o PowerShell (isto é diferente do como `-File` processa parâmetros enviados para um script).</span><span class="sxs-lookup"><span data-stu-id="7d5da-165">Essentially, any text after `-Command` is sent as a single command line to PowerShell (this is different from how `-File` handles parameters sent to a script).</span></span>

<span data-ttu-id="7d5da-166">O valor do comando pode ser "-", uma cadeia.</span><span class="sxs-lookup"><span data-stu-id="7d5da-166">The value of Command can be "-", a string.</span></span> <span data-ttu-id="7d5da-167">ou um bloco de scripts.</span><span class="sxs-lookup"><span data-stu-id="7d5da-167">or a script block.</span></span> <span data-ttu-id="7d5da-168">Se o valor do comando é "-", o texto de comando é ler a partir da entrada padrão.</span><span class="sxs-lookup"><span data-stu-id="7d5da-168">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="7d5da-169">Blocos de script tem de ser colocado entre chavetas ({}).</span><span class="sxs-lookup"><span data-stu-id="7d5da-169">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="7d5da-170">Pode especificar um bloco de script apenas quando executar o PowerShell.exe no PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d5da-170">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="7d5da-171">São apresentados os resultados do script para a shell de principal como objetos XML de serialização anulados, objetos não dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="7d5da-171">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="7d5da-172">Se o valor do comando é uma cadeia, **comando** tem de ser o último parâmetro no comando, porque os caracteres escritos depois do comando são interpretados como os argumentos de comando.</span><span class="sxs-lookup"><span data-stu-id="7d5da-172">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="7d5da-173">Para escrever uma cadeia que é executado um comando do PowerShell, utilize o formato:</span><span class="sxs-lookup"><span data-stu-id="7d5da-173">To write a string that runs a PowerShell command, use the format:</span></span>

```
"& {<command>}"
```

<span data-ttu-id="7d5da-174">onde as aspas indicam uma cadeia e o operador de invoke (&) faz com que o comando ser executada.</span><span class="sxs-lookup"><span data-stu-id="7d5da-174">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="7d5da-175">-Help,-?, /?</span><span class="sxs-lookup"><span data-stu-id="7d5da-175">-Help, -?, /?</span></span>
<span data-ttu-id="7d5da-176">Mostra esta mensagem.</span><span class="sxs-lookup"><span data-stu-id="7d5da-176">Shows this message.</span></span> <span data-ttu-id="7d5da-177">Se escrever um comando PowerShell.exe no PowerShell, preceder os parâmetros de comando com um hífen (-), não uma barra (/).</span><span class="sxs-lookup"><span data-stu-id="7d5da-177">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="7d5da-178">Pode utilizar um hífen ou uma barra no Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="7d5da-178">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="7d5da-179">Nota de resolução de problemas: No PowerShell 2.0, começar alguns programas no Windows PowerShell consola falha com um LastExitCode de 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="7d5da-179">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="7d5da-180">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="7d5da-180">EXAMPLES</span></span>

```
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a Powerhell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate wayh to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```

