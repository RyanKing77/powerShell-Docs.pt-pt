---
ms.date: 08/14/2018
keywords: PowerShell, o cmdlet
title: Ajuda da Linha de Comandos PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: 03c7672ee72698fe88a73e99702ceaadf87e702f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51691835"
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

Parâmetros transmitidos para o script são transmitidos como cadeias de caracteres literais, após a interpretação pelo shell atual. Por exemplo, se estiver no cmd.exe e quiser passar um valor da variável de ambiente, usaria a sintaxe de cmd.exe: `powershell.exe -File .\test.ps1 -TestParam %windir%`

Por outro lado, executando `powershell.exe -File .\test.ps1 -TestParam $env:windir` nos resultados de cmd.exe no script de receber a cadeia literal `$env:windir` porque não tem nenhum significado especial para o shell cmd.exe atual.
O `$env:windir` estilo de referência de variável de ambiente _pode_ ser utilizado dentro de um `-Command` parâmetro, uma vez que existem será interpretado como o código do PowerShell.

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

Executa os comandos especificados (com quaisquer parâmetros) como se eles foram digitados na linha de comando do PowerShell.
Após a execução, PowerShell é encerrado, a menos que o **NoExit** parâmetro for especificado.
Qualquer texto depois do `-Command` é enviada como uma única linha de comando para o PowerShell.
Isso é diferente de como `-File` processa parâmetros enviados para um script.

O valor de `-Command` pode ser "-", uma cadeia de caracteres ou um bloco de script.
Os resultados do comando são devolvidos ao shell principal como objetos XML de serialização anulados, objetos não em direto.

Se o valor de `-Command` é "-", o texto do comando é lidos a partir de entrada padrão.

Quando o valor de `-Command` é uma cadeia de caracteres **comando** _tem_ ser o último parâmetro especificado porque nenhum dos caracteres digitados depois do comando são interpretados como os argumentos de comando.

O **comando** parâmetro só aceita um bloco de script para execução quando ele pode reconhecer o valor transmitido para `-Command` como um tipo de ScriptBlock.
Isto é _apenas_ possível durante a execução PowerShell.exe a partir de outro anfitrião do PowerShell.
O ScriptBlock tipo possa estar contido num existente variável, retornar numa expressão ou analisado os comandos do PowerShell do anfitrião como um bloco de literal script entre chavetas `{}`, antes de que está sendo passada para PowerShell.exe.

No cmd.exe, há sem algo como um bloco de script (ou tipo de ScriptBlock), então, o valor transmitido ao **comando** será _sempre_ ser uma cadeia de caracteres.
Pode escrever um bloco de script dentro da cadeia, mas em vez de em execução irão comportar-se exatamente como se que o escreveu numa linha de comandos do PowerShell típico, imprimir o conteúdo do script bloquear o novamente para si.

Uma cadeia de caracteres passada para `-Command` ainda será executado como o PowerShell, para que as chaves de bloco por script, muitas vezes, não são necessárias em primeiro lugar quando em execução a partir cmd.exe.
Para executar um bloco de script inline definido dentro de uma cadeia de caracteres, o [operador de chamada](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` pode ser utilizado:

```console
"& {<command>}"
```

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
