---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Ajuda da Linha de Comandos PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 60b6a7e310821a4092b0972b7abbdae0e2d5f738
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="powershellexe-command-line-help"></a>Ajuda da linha de comandos PowerShell.exe

Pode utilizar o PowerShell.exe para iniciar uma sessão do PowerShell na linha de comandos de outra ferramenta, tais como Cmd.exe, ou utilizá-lo na linha de comandos do PowerShell para iniciar uma sessão de novo. Utilize os parâmetros para personalizar a sessão.

## <a name="syntax"></a>Sintaxe

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

## <a name="parameters"></a>Parâmetros

### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand <Base64EncodedCommand>

Aceita uma versão de cadeia com codificação base-64 de um comando. Utilize este parâmetro para submeter os comandos do PowerShell que requerem aspas complexas ou chavetas.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>

Define a política de execução predefinido para a sessão atual e guarda-o no $env: PSExecutionPolicyPreference variável de ambiente. Este parâmetro não altera a política de execução do PowerShell que está definida no registo. Para obter informações sobre as políticas de execução do PowerShell, incluindo uma lista de valores válidos, consulte [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

### <a name="-file-filepath-parameters"></a>-Ficheiro <FilePath> \[ <Parameters>]

Executa o script especificado no âmbito local ("dot-obtido"), para que as funções e as variáveis que cria o script estão disponíveis na sessão atual. Introduza o caminho do ficheiro de script e quaisquer parâmetros. **Ficheiro** tem de ser o último parâmetro no comando, porque todos os caracteres escritos após o **ficheiro** nome do parâmetro são interpretados como o caminho do ficheiro de script seguido os parâmetros do script e os respetivos valores.

Pode incluir os parâmetros de um script e os valores de parâmetros, o valor da **ficheiro** parâmetro. Por exemplo: `-File .\Get-Script.ps1 -Domain Central` tenha em atenção que os parâmetros transmitidos para o script são transmitidos como literal cadeias (após a interpretação através da shell do atual).
Por exemplo, se estiverem em cmd.exe e pretende transmita um valor de variável de ambiente, teria de utilizar a sintaxe de cmd.exe: `powershell -File .\test.ps1 -Sample %windir%` se pretendesse utilizar a sintaxe do PowerShell, em seguida, neste exemplo, o script receberia o literal "$env: windir" e não o valor do que variável de ambiente: `powershell -File .\test.ps1 -Sample $env:windir`

Normalmente, os parâmetros de comutador de um script estiverem incluídos ou for omitidos. Por exemplo, o seguinte comando utiliza o **todos os** parâmetro do ficheiro de script Get-Script.ps1: `-File .\Get-Script.ps1 -All`

### <a name="-inputformat-text--xml"></a>\-InputFormat {texto | XML}

Descreve o formato dos dados enviados para o PowerShell. Os valores válidos são "Text" (cadeias de texto) ou "XML" (CLIXML o formato serializado).

### <a name="-mta"></a>-Mta

É iniciado através de um apartment multi-thread do PowerShell. Este parâmetro é apresentado no PowerShell 3.0. No PowerShell 3.0, single-threaded apartment (STA) é a predefinição. PowerShell 2.0, vários threads apartment (MTA) é a predefinição.

### <a name="-noexit"></a>-NoExit

Não for fechada depois de executar os comandos de arranque.

### <a name="-nologo"></a>-NoLogo

Oculta a faixa de copyright no arranque.

### <a name="-noninteractive"></a>-NonInteractive

Não está presente uma linha de comandos interativa ao utilizador.

### <a name="-noprofile"></a>-NoProfile

Não carregue o perfil do PowerShell.

### <a name="-outputformat-text--xml"></a>-OutputFormat {texto | XML}

Determina a forma como saída do PowerShell está formatada. Os valores válidos são "Text" (cadeias de texto) ou "XML" (CLIXML o formato serializado).

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>

Carrega o ficheiro de consola do PowerShell especificado. Introduza o caminho e nome do ficheiro de consola. Para criar um ficheiro de consola, utilize o [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet do PowerShell.

### <a name="-sta"></a>-Sta

Inicia o PowerShell com um apartamento de thread único. No PowerShell 3.0, single-threaded apartment (STA) é a predefinição. PowerShell 2.0, vários threads apartment (MTA) é a predefinição.

### <a name="-version-powershell-version"></a>-Versão <PowerShell Version>

Inicia a versão especificada do PowerShell. A versão que especificar tem de estar instalada no sistema. Se o PowerShell 3.0 está instalado no computador, os valores válidos são "2.0" e "3.0". O valor predefinido é "3.0".

Se o PowerShell 3.0 não está instalado, o único valor válido é "2.0". Outros valores são ignorados.

Para obter mais informações, consulte "[instalar o Windows PowerShell](../../setup/installing-windows-powershell.md)".

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>

Define o estilo de janela para a sessão. Os valores válidos são Normal, minimizado, maximizado e oculto.

### <a name="-command"></a>-Comando

Executa os comandos especificados (e quaisquer parâmetros) como se se tratasse foram escritas na linha de comandos do PowerShell e, em seguida, sai, a menos que o parâmetro NoExit for especificado.
Essencialmente, qualquer texto após `-Command` é enviada como uma única linha de comandos para o PowerShell (isto é diferente do como `-File` processa parâmetros enviados para um script).

O valor do comando pode ser "-", uma cadeia. ou um bloco de scripts. Se o valor do comando é "-", o texto de comando é ler a partir da entrada padrão.

Blocos de script tem de ser colocado entre chavetas ({}). Pode especificar um bloco de script apenas quando executar o PowerShell.exe no PowerShell. São apresentados os resultados do script para a shell de principal como objetos XML de serialização anulados, objetos não dinâmicos.

Se o valor do comando é uma cadeia, **comando** tem de ser o último parâmetro no comando, porque os caracteres escritos depois do comando são interpretados como os argumentos de comando.

Para escrever uma cadeia que é executado um comando do PowerShell, utilize o formato:

```powershell
"& {<command>}"
```

onde as aspas indicam uma cadeia e o operador de invoke (&) faz com que o comando ser executada.

### <a name="-help---"></a>-Help,-?, /?

Mostra esta mensagem. Se escrever um comando PowerShell.exe no PowerShell, preceder os parâmetros de comando com um hífen (-), não uma barra (/). Pode utilizar um hífen ou uma barra no Cmd.exe.

> [!NOTE]
> Nota de resolução de problemas: No PowerShell 2.0, começar alguns programas no Windows PowerShell consola falha com um LastExitCode de 0xc0000142.

## <a name="examples"></a>EXEMPLOS

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