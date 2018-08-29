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
# <a name="powershellexe-command-line-help"></a>Ajuda da linha de comandos do PowerShell.exe

Pode utilizar PowerShell.exe para iniciar uma sessão do PowerShell a partir da linha de comandos de outra ferramenta, como Cmd.exe, ou usá-lo na linha de comandos do PowerShell para iniciar uma nova sessão. Utilize os parâmetros para personalizar a sessão.

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

Aceita uma versão de cadeia com codificação base-64 de um comando. Utilize este parâmetro para enviar comandos para o PowerShell, que requerem aspas complexas ou chavetas.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>

Define a política de execução padrão para a sessão atual e guarda-o no $env: PSExecutionPolicyPreference variável de ambiente. Este parâmetro não altera a diretiva de execução do PowerShell que é definida no registo. Para obter informações sobre as políticas de execução do PowerShell, incluindo uma lista de valores válidos, consulte [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

### <a name="-file-filepath-parameters"></a>-Arquivo <FilePath> \[ <Parameters>]

Executa o script especificado no âmbito do local ("dot Source"), para que as funções e variáveis que cria o script estão disponíveis na sessão atual. Introduza o caminho do ficheiro de script e quaisquer parâmetros. **Ficheiro** tem de ser o último parâmetro no comando. Todos os valores que escreveu depois do **-ficheiro** parâmetro são interpretados como o script de caminho do ficheiro e os parâmetros passados para esse script.

Parâmetros transmitidos para o script são transmitidos como cadeias de caracteres literais (depois de interpretação pelo shell do atual). Por exemplo, se estiver no cmd.exe e quiser passar um valor da variável de ambiente, usaria a sintaxe de cmd.exe: `powershell -File .\test.ps1 -Sample %windir%` neste exemplo, o script recebe a cadeia literal `$env:windir` e não o valor dessa variável ambiental: `powershell -File .\test.ps1 -Sample $env:windir`

### <a name="-inputformat-text--xml"></a>\-InputFormat {texto | XML}

Descreve o formato dos dados enviados para o PowerShell. Valores válidos são "Text" (cadeias de texto) ou "XML" (formato CLIXML serializado).

### <a name="-mta"></a>-Mta

Inicia o PowerShell com um apartment com múltiplos threads. Este parâmetro é introduzido no PowerShell 3.0. No PowerShell 3.0, single-threaded apartment (STA) é a predefinição. No PowerShell 2.0, a predefinição é multithread apartment (MTA).

### <a name="-noexit"></a>-NoExit

Não saia depois de executar comandos de inicialização.

### <a name="-nologo"></a>-NoLogo

Oculta a faixa de direitos de autor na inicialização.

### <a name="-noninteractive"></a>-NonInteractive

Não apresentar uma linha de comandos interativa ao usuário.

### <a name="-noprofile"></a>-NoProfile

Não carrega o perfil do PowerShell.

### <a name="-outputformat-text--xml"></a>-OutputFormat {texto | XML}

Determina a forma como o resultado do PowerShell é formatado. Valores válidos são "Text" (cadeias de texto) ou "XML" (formato CLIXML serializado).

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>

Carrega o ficheiro de consola do PowerShell especificado. Introduza o caminho e nome do arquivo de console. Para criar um arquivo de console, utilize o [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet no PowerShell.

### <a name="-sta"></a>-Sta

Inicia o PowerShell com um apartamento de thread único. No PowerShell 3.0, single-threaded apartment (STA) é a predefinição. No PowerShell 2.0, a predefinição é multithread apartment (MTA).

### <a name="-version-powershell-version"></a>-Versão <PowerShell Version>

Inicia a versão especificada do PowerShell. A versão que especificar tem de estar instalada no sistema. Se o PowerShell 3.0 está instalado no computador, os valores válidos são "2.0" e "3.0". O valor predefinido é "3.0".

Se o PowerShell 3.0 não estiver instalado, o único valor válido é "2.0". Outros valores são ignorados.

Para obter mais informações, consulte [instalar o Windows PowerShell](../../setup/installing-windows-powershell.md).

### <a name="-windowstyle-window-style"></a>-NONE <Window style>

Define o estilo da janela para a sessão. Valores válidos são Normal, minimizado, maximizado e Hidden.

### <a name="-command"></a>-Comando

Executa os comandos especificados (com quaisquer parâmetros) como se eles foram digitados na linha de comando do PowerShell. Após a execução, PowerShell é encerrado, a menos que o `-NoExit` parâmetro for especificado.
Qualquer texto depois do `-Command` é enviada como uma única linha de comando para o PowerShell. Isso é diferente de como `-File` processa parâmetros enviados para um script.

O valor do comando pode ser "-", uma cadeia de caracteres. ou um bloco de scripts. Se for o valor do comando "-", o texto do comando é lidos a partir de entrada padrão.

Blocos de script têm de estar entre chavetas ({}). Pode especificar um bloco de scripts apenas quando executar PowerShell.exe no PowerShell. Os resultados do script são devolvidos ao shell principal como objetos XML de serialização anulados, objetos não em direto.

Se o valor do comando é uma cadeia de caracteres **comando** tem de ser o último parâmetro no comando, porque qualquer caracteres digitados depois do comando são interpretados como os argumentos de comando.

Para escrever uma cadeia de caracteres que executa um comando do PowerShell, utilize o formato:

```powershell
"& {<command>}"
```

As aspas indicam uma cadeia de caracteres e o operador de invoke (&) faz com que o comando a ser executado.

### <a name="-help---"></a>-Help,-?, /?

Mostra a sintaxe de powershell.exe. Se estiver escrevendo um comando de PowerShell.exe no PowerShell, preceda os parâmetros de comando com um hífen (-), não uma barra (/). Pode utilizar um hífen ou de uma barra no Cmd.exe.

> [!NOTE]
> Nota de resolução de problemas: No PowerShell 2.0, a partir de alguns programas no Windows PowerShell consola não com um LastExitCode de 0xc0000142.

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
