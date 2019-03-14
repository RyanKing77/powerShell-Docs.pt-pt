---
ms.date: 05/17/2018
keywords: PowerShell, core
title: Alterações recentes ao PowerShell 6.0
ms.openlocfilehash: 975c978629f81f0f13a235c3d304e5ec03bae6d0
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795696"
---
# <a name="breaking-changes-for-powershell-60"></a>Alterações recentes ao PowerShell 6.0

## <a name="features-no-longer-available-in-powershell-core"></a>Funcionalidades já não está disponíveis no PowerShell Core

### <a name="powershell-workflow"></a>Fluxo de trabalho do PowerShell

[Fluxo de trabalho do PowerShell] [ workflow] é uma funcionalidade no Windows PowerShell que baseia-se na parte superior do [Windows Workflow Foundation (WF)] [ workflow-foundation] que permite a criação de obter runbooks robusto para tarefas de longa execução ou em paralelo.

Devido à falta de suporte para Windows Workflow Foundation no .NET Core, continuaremos não suportar o fluxo de trabalho do PowerShell no PowerShell Core.

No futuro, gostaríamos de ativar o paralelismo/simultaneidade nativa no idioma do PowerShell sem a necessidade de fluxo de trabalho do PowerShell.

[workflow]: https://docs.microsoft.com/powershell/scripting/core-powershell/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Snap-ins personalizados

[Snap-ins do PowerShell] [ snapin] são um predecessor de módulos do PowerShell que não têm impedem uma adoção na Comunidade do PowerShell.

Devido à complexidade do suporte de snap-ins e a falta de utilização da Comunidade, já não suportamos a snap-ins personalizados no PowerShell Core.

Hoje em dia, divide o `ActiveDirectory` e `DnsClient` módulos no Windows e Windows Server.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>Cmdlets do WMI v1

Devido à complexidade do suporte a dois conjuntos de módulos baseados no WMI, removemos os cmdlets do WMI v1 do PowerShell Core:

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

Em vez disso, recomendamos que o utilize os cmdlets do CIM (também conhecido como WMI v2) que fornecem a mesma funcionalidade com novas funcionalidades e uma sintaxe reprojetada:

- `Get-CimAssociatedInstance`
- `Get-CimClass`
- `Get-CimInstance`
- `Get-CimSession`
- `Invoke-CimMethod`
- `New-CimInstance`
- `New-CimSession`
- `New-CimSessionOption`
- `Register-CimIndicationEvent`
- `Remove-CimInstance`
- `Remove-CimSession`
- `Set-CimInstance`

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft.PowerShell.LocalAccounts

Devido à utilização de APIs sem suporte, `Microsoft.PowerShell.LocalAccounts` foi removido do PowerShell Core até encontra uma solução melhor.

### <a name="-counter-cmdlets"></a>Cmdlets `*-Counter`

Devido à utilização de APIs sem suporte, o `*-Counter` foi removido do PowerShell Core até encontra uma solução melhor.

### <a name="-eventlog-cmdlets"></a>Cmdlets `*-EventLog`

Devido à utilização de APIs sem suporte, o `*-EventLog` foi removido do PowerShell Core. até que seja encontrada uma solução melhor. `Get-WinEvent` e `Create-WinEvent` estão disponíveis para obter e criar eventos no Windows.

## <a name="enginelanguage-changes"></a>Alterações de motor/linguagem

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>Mudar o nome `powershell.exe` para `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

Para conceder aos utilizadores uma forma determinista para chamar o PowerShell Core no Windows (ao contrário do Windows PowerShell), o binário do PowerShell Core foi alterado para `pwsh.exe` em Windows e `pwsh` em plataformas não Windows.

O nome abreviado também é consistente com a nomenclatura de shells em plataformas não Windows.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>Não inserir quebras de linha de saída (exceto para tabelas) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Anteriormente, a saída foi alinhada com a largura da consola e quebras de linha foram adicionadas a largura final do console, que significa que a saída não obter reformatada conforme esperado se terminal foi redimensionado. Esta alteração não foi aplicada a tabelas, as quebras de linha forem necessárias para manter as colunas alinhadas.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>Ignorar verificação de elemento nulo para coleções com um tipo de elemento do tipo de valor [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

Para o `Mandatory` parâmetro e `ValidateNotNull` e `ValidateNotNullOrEmpty` atributos, ignorar a verificação de elemento nulo se o tipo de elemento da coleção é o tipo de valor.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>Alteração `$OutputEncoding` utilizar `UTF-8 NoBOM` codificação em vez de ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

A codificação anteriores, ASCII (7 bits), iria resultar na alteração incorreta da saída em alguns casos. Esta alteração é tornar `UTF-8 NoBOM` padrão, o que preserva a saída de Unicode com uma codificação suportados pela maioria das ferramentas e sistemas operativos.

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>Remova `AllScope` da maioria dos aliases de padrão [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

Para acelerar a criação de âmbito, `AllScope` foi removido da maioria dos aliases de predefinição. `AllScope` foi deixada durante alguns aliases usados com freqüência em que a pesquisa tenha mais rápida.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose` e `-Debug` já não substitui `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

Anteriormente, se `-Verbose` ou `-Debug` foram especificadas, ele overrode o comportamento de `$ErrorActionPreference`. Com esta alteração `-Verbose` e `-Debug` já não afeta o comportamento do `$ErrorActionPreference`.

## <a name="cmdlet-changes"></a>Alterações de cmdlet

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>RestMethod invocar não retorna informações úteis quando não existem dados são devolvidos. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

Quando uma API devolve apenas `null`, Invoke-RestMethod foi serializar isso como a cadeia de caracteres `"null"` em vez de `$null`. Esta alteração corrige a lógica na `Invoke-RestMethod` corretamente serializar um único valor JSON válido `null` literal como `$null`.

### <a name="remove--computername-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>Remova `-ComputerName` partir `*-Computer` cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

Devido a problemas com a comunicação remota RPC em CoreFX (particularmente em plataformas não Windows) e garantir uma experiência de comunicação remota consistente no PowerShell, o `-ComputerName` parâmetro foi removido o `\*-Computer` cmdlets. Utilize `Invoke-Command` em vez disso, como a forma de executar cmdlets remotamente.

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>Remova `-ComputerName` partir `*-Service` cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

Para incentivarmos a utilização consistente de PSRP, o `-ComputerName` parâmetro foi removido do `*-Service` cmdlets.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>Corrigir `Get-Item -LiteralPath a*b` se `a*b` , na verdade, não existe para retornar erro [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

Anteriormente, `-LiteralPath` devido um caráter universal deve tratá-lo a mesma como `-Path` e se nenhum arquivo não encontrado o caráter universal, seriam silenciosamente sair. Correto de comportamento deve ser a `-LiteralPath` é literal, portanto, se o ficheiro não existir, o que deveria erro. Alteração é tratar os caracteres curinga utilizada com `-Literal` como um.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>`Import-Csv` deve ser aplicada `PSTypeNames` após a importação quando as informações de tipo estão presentes no CSV [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

Anteriormente, objetos exportados usando `Export-CSV` com `TypeInformation` importados com `ConvertFrom-Csv` não foram mantendo as informações de tipo. Esta alteração adiciona as informações de tipo para `PSTypeNames` membro se estiver disponível. o ficheiro. CSV.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`-NoTypeInformation` deve ser a predefinição no `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Esta alteração foi feita a comentários de clientes de endereço no comportamento padrão de `Export-CSV` para incluir informações de tipo.

Anteriormente, o cmdlet seria saída um comentário como a primeira linha que contém o nome do tipo do objeto. A alteração é suprimido por padrão, ele não é entendido pela maioria das ferramentas. Utilize `-IncludeTypeInformation` para reter o comportamento anterior.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>Cmdlets de Web adverti-quando `-Credential` são enviados através de conexões não criptografadas [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

Ao usar HTTP, conteúdo, incluindo palavras-passe é enviado como texto não encriptado. Esta alteração é não permitir isso por predefinição e devolver um erro, se as credenciais estão sendo passadas de maneira insegura. Os utilizadores podem ignorar isto utilizando o `-AllowUnencryptedAuthentication` mudar.

## <a name="api-changes"></a>Alterações à API

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>Remova `AddTypeCommandBase` classe [#5407](https://github.com/PowerShell/PowerShell/issues/5407)

O `AddTypeCommandBase` classe foi removida do `Add-Type` para melhorar o desempenho. Essa classe é apenas utilizado pelo cmdlet Add-Type e não deve afetar os utilizadores.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>Unifique os cmdlets com o parâmetro `-Encoding` seja do tipo `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

O `-Encoding` valor `Byte` foi removido do cmdlets de fornecedor do sistema de ficheiros. Um novo parâmetro `-AsByteStream`, agora é utilizado para especificar que um fluxo de bytes é necessário como entrada ou de que a saída é um fluxo de bytes.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>Adicionar a mensagem de erro para vazio e null melhores `-UFormat` parâmetro [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

Anteriormente, quando passar um formato vazio de cadeias de caracteres para `-UFormat`, aparecerá uma mensagem de erro inúteis. Foi adicionado um erro mais descritivo.

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>Limpar o código de consola [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

As seguintes funcionalidades foram removidas à medida que eles não são suportados no PowerShell Core, e existem não existem planos para adicionar suporte, tal como existem por motivos de herança para o Windows PowerShell: `-psconsolefile` comutador e o código, `-importsystemmodules` comutador e o código e o tipo de letra alterar o código.

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>Removido `RunspaceConfiguration` suportar [#4942](https://github.com/PowerShell/PowerShell/issues/4942)

Anteriormente, ao criar um espaço de execução do PowerShell através de programação com a API pode utilizar o legado [ `RunspaceConfiguration` ] [ runspaceconfig] ou o mais recente [ `InitialSessionState` ] [ iss]. Esta alteração removeu o suporte para `RunspaceConfiguration` e só suporta `InitialSessionState`.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript` vincular os argumentos para `$input` em vez de `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

Uma posição incorreta de um parâmetro resultou em args passados como entrada em vez de como argumentos.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>Remover não suportado `-showwindow` mudar da `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow` baseia-se no WPF, que não é suportado no CoreCLR.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>Permitir * a ser utilizado no caminho de registo para `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

Anteriormente, `-LiteralPath` devido um caráter universal deve tratá-lo a mesma como `-Path` e se nenhum arquivo não encontrado o caráter universal, seriam silenciosamente sair. Correto de comportamento deve ser a `-LiteralPath` é literal, portanto, se o ficheiro não existir, o que deveria erro. Alteração é tratar os caracteres curinga utilizada com `-Literal` como um.

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>Corrigir `Set-Service` falhar teste [#4802](https://github.com/PowerShell/PowerShell/issues/4802)

Anteriormente, se `New-Service -StartupType foo` foi utilizado, `foo` foi ignorada e o serviço foi criado com algum tipo de arranque predefinidas. Esta alteração é explicitamente emite um erro para um tipo de arranque inválida.

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>Mudar o nome `$IsOSX` para `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

A nomenclatura do PowerShell deve ser consistente com a nossa de nomenclatura e estar em conformidade com a utilização da Apple do macOS em vez de OSX. No entanto, para facilitar a leitura e consistente, mantendo-se com Pascal casing.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>Tornar consistente as mensagens de erro quando o script inválida é passado para - ficheiros, melhor Ocorreu um erro ao passado argumento ambíguo [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

Alterar códigos de saída de `pwsh.exe` para alinhar com as convenções de Unix

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>Remoção de `LocalAccount` e os cmdlets do `Diagnostics` módulos. [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

Devido a APIs sem suporte, o `LocalAccounts` módulo e o `Counter` cmdlets no `Diagnostics` módulo foram removidas até encontra uma solução melhor.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>Executar script do PowerShell com o parâmetro de bool não funciona [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

Anteriormente, utilizando **powershell.exe** (agora **pwsh.exe**) para executar um script do PowerShell com `-File` não fornecia meios para passar `$true` / `$false` como parâmetro valores. Suporte para `$true` / `$false` como valores analisados para parâmetros foi adicionado. Valores de comutador também são suportadas como atualmente documentado sintaxe não funciona.

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>Remova `ClrVersion` propriedade a partir `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

O `ClrVersion` propriedade do `$PSVersionTable` é não é útil com o CoreCLR, os utilizadores finais devem não estar a utilizar esse valor para determinar a compatibilidade.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>Alterar o parâmetro posicional `powershell.exe` partir `-Command` para `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

Ative a utilização de shebang do PowerShell em plataformas não Windows. Isso significa que em sistemas Unix com base, pode fazer um executável de script que invocará PowerShell automaticamente em vez de invocar explicitamente `pwsh`. Isso também significa que agora pode fazer coisas como `powershell foo.ps1` ou `powershell fooScript` sem especificar `-File`. No entanto, esta alteração requer agora que especifica explicitamente `-c` ou `-Command` ao tentar fazer coisas como `powershell.exe Get-Command`.

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>Implementar a análise de escape Unicode [#3958](https://github.com/PowerShell/PowerShell/issues/3958)

`` `u####`` ou `` `u{####}`` é convertido para o caráter Unicode correspondente. Para a saída de um literal `` `u``, o acento grave de escape: ``` ``u```.

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>Alteração `New-ModuleManifest` codificação `UTF8NoBOM` em plataformas não Windows [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

Anteriormente, `New-ModuleManifest` cria psd1 manifestos no UTF-16, com BOM, criação de um problema para ferramentas de Linux. Esta alteração de última hora altera a codificação de `New-ModuleManifest` ser UTF (sem BOM) em plataformas não Windows.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>Impedir `Get-ChildItem` de recursing em links simbólicos (#1875). [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Esta alteração traz `Get-ChildItem` mais em conformidade com o Unix `ls -r` e o Windows `dir /s` comandos nativos. Como os comandos mencionados, o cmdlet apresenta links simbólicos aos diretórios encontrados durante a recursão, mas não recurse neles.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>Corrigir `Get-Content -Delimiter` para não incluir o delimitador nas linhas retornadas [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Anteriormente, a saída ao utilizar `Get-Content -Delimiter` foi inconsistente e inconveniente como ele necessário processamento adicional dos dados para remover o delimitador. Esta alteração remove o delimitador de linhas retornado.

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>Implementar o formato Hex no C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

O `-Raw` parâmetro agora é uma "sem operações" (em que não faz nada). Daqui em diante toda a saída será apresentada uma representação verdadeira dos números que incluem todos os bytes para o respetivo tipo (o que o `-Raw` parâmetro formalmente estava fazendo antes desta alteração).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>PowerShell como um shell predefinida não funciona com o comando de scripts [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

UNIX, é uma convenção para shells aceitar `-i` para uma shell interativa e muitas ferramentas esperassem esse comportamento (`script` por exemplo e quando definir o PowerShell como o shell padrão) e chama o shell com o `-i` mudar. Esta alteração é a última hora em que `-i` anteriormente poderia ser usado como mão curta para corresponder `-inputformat`, que agora tem de ser `-in`.

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Correção de erro de digitação no nome da propriedade Get-ComputerInfo [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber` foi escrito incorretamente como `BiosSeralNumber` e foi alterada para a ortografia correta.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>Adicione `Get-StringHash` e `Get-FileHash` cmdlets [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Esta alteração é que alguns algoritmos de hash não são suportados pelo CoreFX, que, por conseguinte, já não estão disponíveis:

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>Adicionar a validação `Get-*` cmdlets onde passar $null devolve todos os objetos em vez de erro [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

Passando `$null` a qualquer uma da seguir gera agora um erro:

- `Get-Credential -UserName`
- `Get-Event -SourceIdentifier`
- `Get-EventSubscriber -SourceIdentifier`
- `Get-Help -Name`
- `Get-PSBreakpoint -Script`
- `Get-PSProvider -PSProvider`
- `Get-PSSessionConfiguration -Name`
- `Get-PSSnapin -Name`
- `Get-Runspace -Name`
- `Get-RunspaceDebug -RunspaceName`
- `Get-Service -Name`
- `Get-TraceSource -Name`
- `Get-Variable -Name`
- `Get-WmiObject -Class`
- `Get-WmiObject -Property`

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a>Adicionar suporta o formato de arquivo estendido de Log do W3C no `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

Anteriormente, o `Import-Csv` cmdlet não pode ser utilizado para importar diretamente os ficheiros de registo no formato de registo expandido de W3C e qualquer ação adicional, seria necessária. Com esta alteração, é suportado o formato de registo expandido de W3C.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>Problema de enlace de parâmetro com `ValueFromRemainingArguments` nas funções de PS [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments` Agora que devolve os valores como uma matriz em vez de um único valor que por si só é uma matriz.

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>`BuildVersion` é removido do `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Remover os `BuildVersion` propriedade de `$PSVersionTable`. Esta propriedade estava associada para a versão de compilação do Windows. Em vez disso, recomendamos que utilize `GitCommitId` para obter a versão de compilação exata do PowerShell Core.

### <a name="changes-to-web-cmdlets"></a>Alterações aos Cmdlets de Web

A API de .NET subjacente dos Cmdlets do Web foi alterada para `System.Net.Http.HttpClient`. Esta alteração fornece muitos benefícios. No entanto, esta alteração, juntamente com a falta de interoperabilidade com o Internet Explorer resultaram em várias alterações de última hora dentro `Invoke-WebRequest` e `Invoke-RestMethod`.

- `Invoke-WebRequest` agora oferece suporte a HTML análise básica apenas. `Invoke-WebRequest` sempre retorna um `BasicHtmlWebResponseObject` objeto. O `ParsedHtml` e `Forms` propriedades foram removidas.
- `BasicHtmlWebResponseObject.Headers` os valores são agora `String[]` em vez de `String`.
- `BasicHtmlWebResponseObject.BaseResponse` é agora um `System.Net.Http.HttpResponseMessage` objeto.
- O `Response` propriedade em exceções de Web Cmdlet é agora um `System.Net.Http.HttpResponseMessage` objeto.
- Análise de cabeçalho RFC Strict agora é a predefinição para o `-Headers` e `-UserAgent` parâmetro. Isso pode ser ignorado com `-SkipHeaderValidation`.
- `file://` e `ftp://` esquemas URI já não são suportadas.
- `System.Net.ServicePointManager` as definições já não são honradas.
- Não existe atualmente nenhuma autenticação baseada em certificado disponível no macOS.
- Usar `-Credential` através de um `http://` URI irá resultar num erro. Utilize um `https://` URI ou forneça o `-AllowUnencryptedAuthentication` parâmetro para suprimir o erro.
- `-MaximumRedirection` agora produz um erro de terminação quando tentativas de redirecionamento excederem o limite de fornecido em vez de retornar os resultados da última redirecionamento.
