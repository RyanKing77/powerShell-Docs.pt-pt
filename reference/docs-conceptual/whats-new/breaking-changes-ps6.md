---
ms.date: 05/17/2018
keywords: PowerShell, núcleo
title: Alterações recentes para o PowerShell 6,0
ms.openlocfilehash: 186e55c1ac46ce3fc172df18995f8c15d9eeb8eb
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/26/2019
ms.locfileid: "67843946"
---
# <a name="breaking-changes-for-powershell-60"></a>Alterações recentes para o PowerShell 6,0

## <a name="features-no-longer-available-in-powershell-core"></a>Recursos que não estão mais disponíveis no PowerShell Core

### <a name="powershell-workflow"></a>Fluxo de trabalho do PowerShell

O [fluxo de trabalho do PowerShell][workflow] é um recurso do Windows PowerShell que se baseia no [Windows Workflow Foundation (WF)][workflow-foundation] , que permite a criação de runbooks robustos para tarefas de longa execução ou paralelizadas.

Devido à falta de suporte para Windows Workflow Foundation no .NET Core, não continuaremos a dar suporte ao fluxo de trabalho do PowerShell no PowerShell Core.

No futuro, gostaríamos de habilitar o paralelismo/simultaneidade nativa na linguagem do PowerShell sem a necessidade do fluxo de trabalho do PowerShell.

[workflow]: https://docs.microsoft.com/powershell/scripting/core-powershell/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Snap-ins personalizados

Os [snap-ins do PowerShell][snapin] são um predecessor dos módulos do PowerShell que não têm adoção generalizada na Comunidade do PowerShell.

Devido à complexidade de dar suporte a snap-ins e à falta de uso na Comunidade, não damos mais suporte a snap-ins personalizados no PowerShell Core.

Hoje, isso quebra os `ActiveDirectory` módulos `DnsClient` e no Windows Server.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>Cmdlets do WMI v1

Devido à complexidade de dar suporte a dois conjuntos de módulos baseados em WMI, removemos os cmdlets do WMI v1 do PowerShell Core:

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

Em vez disso, recomendamos que você use os cmdlets CIM (também conhecido como WMI v2) que fornecem a mesma funcionalidade com novas funcionalidades e uma sintaxe reprojetada:

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

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft. PowerShell. LocalAccounts

Devido ao uso de APIs sem suporte, `Microsoft.PowerShell.LocalAccounts` o foi removido do PowerShell Core até que uma solução melhor seja encontrada.

### <a name="-computer-cmdlets"></a>`*-Computer`cmdlets

Devido ao uso de APIs sem suporte, os cmdlets a seguir foram removidos do PowerShell Core até que uma solução melhor seja encontrada.

- Adicionar computador
- Checkpoint-Computer
- Remover computador
- Restaurar computador

### <a name="-counter-cmdlets"></a>`*-Counter`cmdlets

Devido ao uso de APIs sem suporte, o `*-Counter` foi removido do PowerShell Core até que uma solução melhor seja encontrada.

### <a name="-eventlog-cmdlets"></a>`*-EventLog`cmdlets

Devido ao uso de APIs sem suporte, o `*-EventLog` foi removido do PowerShell Core. até que uma solução melhor seja encontrada. `Get-WinEvent`e `Create-WinEvent` estão disponíveis para obter e criar eventos no Windows.

## <a name="enginelanguage-changes"></a>Alterações de mecanismo/idioma

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>Renomear `powershell.exe` para `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

Para fornecer aos usuários uma maneira determinística de chamar o PowerShell Core no Windows (em oposição ao Windows PowerShell), o binário do PowerShell Core foi alterado `pwsh.exe` para no Windows `pwsh` e em plataformas que não são do Windows.

O nome abreviado também é consistente com a nomenclatura de shells em plataformas não Windows.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>Não inserir quebras de linha para saída (exceto para tabelas) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Anteriormente, a saída foi alinhada com a largura do console e as quebras de linha foram adicionadas na largura final do console, o que significa que a saída não foi reformatada como esperado se o terminal fosse redimensionado. Essa alteração não foi aplicada a tabelas, pois as quebras de linha são necessárias para manter as colunas alinhadas.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>Ignorar verificação de elemento nulo para coleções com um tipo de elemento de tipo de valor [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

Para o `Mandatory` `ValidateNotNull` parâmetro`ValidateNotNullOrEmpty` e atributos, ignore a verificação de elemento nulo se o tipo de elemento da coleção for de tipo Value.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>Alterar `$OutputEncoding` para usar `UTF-8 NoBOM` codificação em vez de ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

A codificação anterior, ASCII (7 bits), resultaria na alteração incorreta da saída em alguns casos. Essa alteração é para tornar `UTF-8 NoBOM` padrão, o que preserva a saída de Unicode com uma codificação com suporte na maioria das ferramentas e sistemas operacionais.

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>Remover `AllScope` da maioria dos aliases padrão [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

Para acelerar a criação de escopo `AllScope` , o foi removido da maioria dos aliases padrão. `AllScope`foi deixado por alguns aliases usados com frequência em que a pesquisa foi mais rápida.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose`e `-Debug` não substitui `$ErrorActionPreference` mais [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

Anteriormente, se `-Verbose` ou `-Debug` foi especificado, ele substituiu o comportamento de `$ErrorActionPreference`. Com essa alteração, `-Verbose` e `-Debug` não afeta mais o comportamento de `$ErrorActionPreference`.

## <a name="cmdlet-changes"></a>Alterações de cmdlet

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>Invoke-RestMethod não retorna informações úteis quando nenhum dado é retornado. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

Quando uma API retorna apenas `null`, Invoke-RestMethod estava serializando isso como a `"null"` cadeia de `$null`caracteres em vez de. Essa alteração corrige a lógica no `Invoke-RestMethod` para serializar corretamente um valor único literal `null` JSON válido `$null`como.

### <a name="remove--protocol-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>Remover `-Protocol` dos`*-Computer` cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

Devido a problemas com a comunicação remota RPC no CoreFX (especialmente em plataformas não Windows) e garantindo uma experiência de comunicação remota consistente `-Protocol` no PowerShell, o parâmetro `\*-Computer` foi removido dos cmdlets. O DCOM não tem mais suporte para comunicação remota. Os cmdlets a seguir dão suporte apenas a comunicação remota WSMAN:

- Renomear-computador
- Reiniciar computador
- Parar computador

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>Remover `-ComputerName` dos`*-Service` cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

Para incentivar o uso consistente de PSRP, o `-ComputerName` parâmetro foi removido dos `*-Service` cmdlets.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>Corrigir `Get-Item -LiteralPath a*b` se`a*b` realmente não existir para retornar o erro [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

Anteriormente, `-LiteralPath` dado um curinga o trataria da mesma forma `-Path` que e se o curinga não encontrou arquivos, ele sairá silenciosamente. O comportamento correto deve ser `-LiteralPath` literal, portanto, se o arquivo não existir, ele deverá ter um erro. A alteração é para tratar curingas usados `-Literal` com as literal.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>`Import-Csv`deve ser `PSTypeNames` aplicada após a importação quando as informações de tipo estão presentes no CSV [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

Anteriormente, os objetos exportados `Export-CSV` usando `ConvertFrom-Csv` with `TypeInformation` imported with não estão retendo as informações de tipo. Essa alteração adiciona as informações de tipo `PSTypeNames` para membro, se disponíveis no arquivo CSV.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`-NoTypeInformation`deve ser padrão em `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Essa alteração foi feita para endereçar os comentários do cliente sobre o `Export-CSV` comportamento padrão do para incluir informações de tipo.

Anteriormente, o cmdlet produziria um comentário como a primeira linha que contém o nome do tipo do objeto. A alteração é suprimir isso por padrão, pois ela não é compreendida pela maioria das ferramentas. Use `-IncludeTypeInformation` para manter o comportamento anterior.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>Os cmdlets da Web devem `-Credential` avisar quando são enviados por conexões não criptografadas [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

Ao usar HTTP, o conteúdo, incluindo senhas, é enviado como texto não criptografado. Essa alteração é não permitir isso por padrão e retornará um erro se as credenciais estiverem sendo passadas de maneira insegura. Os usuários podem ignorá-lo `-AllowUnencryptedAuthentication` usando a opção.

## <a name="api-changes"></a>Alterações de API

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>Remover `AddTypeCommandBase` [#5407](https://github.com/PowerShell/PowerShell/issues/5407) de classe

A `AddTypeCommandBase` classe foi removida `Add-Type` do para melhorar o desempenho. Essa classe só é usada pelo cmdlet Add-Type e não deve afetar os usuários.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>Unificar cmdlets com `-Encoding` parâmetro para ser do `System.Text.Encoding` tipo [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

O `-Encoding` valor`Byte` foi removido dos cmdlets do provedor FileSystem. Um novo parâmetro, `-AsByteStream`, agora é usado para especificar que um fluxo de bytes é necessário como entrada ou que a saída é um fluxo de bytes.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>Adicione uma melhor mensagem de erro para o `-UFormat` parâmetro vazio e nulo [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

Anteriormente, ao passar uma cadeia de caracteres de `-UFormat`formato vazio para, uma mensagem de erro não auxiliar seria exibida. Um erro mais descritivo foi adicionado.

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>Limpar o código do console [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

Os recursos a seguir foram removidos, pois não têm suporte no PowerShell Core e não há planos para adicionar suporte à medida que existem por motivos herdados para o Windows `-psconsolefile` PowerShell: switch e `-importsystemmodules` código, switch e Code e código de alteração de fonte.

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>Removido `RunspaceConfiguration` o suporte [#4942](https://github.com/PowerShell/PowerShell/issues/4942)

Anteriormente, ao criar um runspace do PowerShell programaticamente usando a API, você [`RunspaceConfiguration`][runspaceconfig] poderia usar o [`InitialSessionState`][iss]herdado ou o mais recente. Essa alteração removeu o `RunspaceConfiguration` suporte para e `InitialSessionState`só dá suporte ao.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript`associar argumentos `$input` em vez de `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

Uma posição incorreta de um parâmetro resultou em argumentos passados como entrada, e não como args.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>Remover o `-showwindow` comutador sem suporte `Get-Help` do [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow`o se baseia no WPF, que não tem suporte no CoreCLR.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>Permitir que * seja usado no caminho do registro `Remove-Item` para [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

Anteriormente, `-LiteralPath` dado um curinga o trataria da mesma forma `-Path` que e se o curinga não encontrou arquivos, ele sairá silenciosamente. O comportamento correto deve ser `-LiteralPath` literal, portanto, se o arquivo não existir, ele deverá ter um erro. A alteração é para tratar curingas usados `-Literal` com as literal.

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>Correção `Set-Service` de teste de falha [#4802](https://github.com/PowerShell/PowerShell/issues/4802)

Anteriormente, se `New-Service -StartupType foo` foi usado, `foo` foi ignorado e o serviço foi criado com algum tipo de inicialização padrão. Essa alteração é para gerar explicitamente um erro para um tipo de inicialização inválido.

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>Renomear `$IsOSX` para `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

A nomenclatura no PowerShell deve ser consistente com nossa nomenclatura e estar em conformidade com o uso da Apple no macOS, em vez de OSX. No entanto, para facilitar a leitura e estamos sempre com a capitalização de Pascal.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>Tornar a mensagem de erro consistente quando um script inválido for passado para o arquivo, melhor erro ao passar o argumento ambíguo [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

Alterar os códigos de saída `pwsh.exe` de para alinhar com as convenções UNIX

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>Remoção dos `LocalAccount` cmdlets e dos `Diagnostics` módulos. [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

Devido a APIs sem suporte, o `LocalAccounts` módulo e os `Counter` cmdlets no `Diagnostics` módulo foram removidos até que uma solução melhor seja encontrada.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>A execução do script do PowerShell com o parâmetro BOOL não funciona [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

Anteriormente, o uso do **PowerShell. exe** (agora **pwsh. exe**) para executar um script `-File` do PowerShell usando não forneceu uma maneira de passar `$true` / `$false` como valores de parâmetro. O suporte `$true` para /valoresdeas analisadosparaparâmetrosfoiadicionado`$false` . Os valores de switch também têm suporte, pois a sintaxe documentada atualmente não funciona.

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>Remover `ClrVersion` propriedade de `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

A `ClrVersion` propriedade de `$PSVersionTable` não é útil com o CoreCLR, os usuários finais não devem usar esse valor para determinar a compatibilidade.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>Alterar o parâmetro posicional `powershell.exe` de `-Command` de `-File` para [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

Habilite o uso Shebang do PowerShell em plataformas não Windows. Isso significa que, em sistemas baseados em UNIX, você pode criar um executável de script que invocaria o PowerShell automaticamente `pwsh`em vez de invocar explicitamente. Isso também significa que agora você pode fazer coisas como `powershell foo.ps1` ou `powershell fooScript` sem especificar `-File`. No entanto, essa alteração agora requer que você `-c` especifique `-Command` explicitamente ou ao tentar fazer coisas `powershell.exe Get-Command`como.

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>Implementar [#3958](https://github.com/PowerShell/PowerShell/issues/3958) de análise de escape Unicode

`` `u####``ou `` `u{####}`` é convertido para o caractere Unicode correspondente. Para gerar um literal `` `u``, escape a marca de fim ``` ``u```:.

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>Alterar `New-ModuleManifest` codificação para `UTF8NoBOM` em plataformas não Windows [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

Anteriormente, `New-ModuleManifest` criamos manifestos psd1 em UTF-16 com a bom, criando um problema para as ferramentas do Linux. Essa alteração significativa altera a codificação de `New-ModuleManifest` para ser UTF (sem bom) em plataformas não Windows.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>Evitar `Get-ChildItem` a recorrência do symlinks (#1875). [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Essa alteração traz `Get-ChildItem` mais em linha com os comandos `ls -r` nativos do UNIX `dir /s` e do Windows. Assim como os comandos mencionados, o cmdlet exibe links simbólicos para diretórios encontrados durante a recursão, mas não os recursiva.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>Correção `Get-Content -Delimiter` para não incluir o delimitador nas linhas retornadas [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Anteriormente, a saída enquanto estava `Get-Content -Delimiter` usando era inconsistente e inconveniente, pois exigia o processamento adicional dos dados para remover o delimitador. Essa alteração remove o delimitador nas linhas retornadas.

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>Implementar o formato-hex C# em [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

O `-Raw` parâmetro agora é um "não op" (no que não faz nada). O encaminhamento de toda a saída será exibido com uma representação real de números que inclui todos os bytes para seu tipo (o que o `-Raw` parâmetro estava formalmente antes dessa alteração).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>O PowerShell como um shell padrão não funciona com o comando de script [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

No UNIX, é uma Convenção para os shells aceitarem `-i` um shell interativo e muitas ferramentas esperam esse comportamento (`script` por exemplo, e ao definir o PowerShell como o shell padrão) e chama o shell com a `-i` opção. Essa alteração está se dividindo `-i` , que anteriormente poderia ser usada como uma correspondência `-inputformat`curta, que agora precisa ser `-in`.

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Correção de digitação no nome da propriedade Get-ComputerInfo [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber`foi digitado incorretamente `BiosSeralNumber` como e foi alterado para a grafia correta.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>Adicionar `Get-StringHash` cmdlets `Get-FileHash` e [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Essa alteração é que alguns algoritmos de hash não têm suporte do CoreFX, portanto, eles não estão mais disponíveis:

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>Adicione validação em `Get-*` cmdlets em que a passagem de $NULL retorna todos os objetos em vez de erro [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

Passar `$null` para qualquer um dos seguintes agora gera um erro:

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

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a>Adicionar suporte ao formato de arquivo de log `Import-Csv` estendido W3C no [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

Anteriormente, o `Import-Csv` cmdlet não pode ser usado para importar diretamente os arquivos de log no formato de log estendido W3C e uma ação adicional seria necessária. Com essa alteração, há suporte para o formato de log estendido do W3C.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>Problema de associação de `ValueFromRemainingArguments` parâmetro com nas funções do PS [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments`agora retorna os valores como uma matriz em vez de um único valor que é uma matriz.

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>`BuildVersion`é removido do `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Remova a `BuildVersion` propriedade de `$PSVersionTable`. Esta propriedade foi vinculada à versão de Build do Windows. Em vez disso, recomendamos que `GitCommitId` você use para recuperar a versão de Build exata do PowerShell Core.

### <a name="changes-to-web-cmdlets"></a>Alterações nos cmdlets da Web

A API .NET subjacente dos cmdlets da Web foi alterada para `System.Net.Http.HttpClient`. Essa alteração fornece muitos benefícios. No entanto, essa alteração, junto com a falta de interoperabilidade com o Internet Explorer, resultou `Invoke-WebRequest` em `Invoke-RestMethod`várias alterações significativas no e no.

- `Invoke-WebRequest`Agora dá suporte apenas à análise de HTML básica. `Invoke-WebRequest`sempre retorna um `BasicHtmlWebResponseObject` objeto. As `ParsedHtml` propriedades `Forms` e foram removidas.
- `BasicHtmlWebResponseObject.Headers`os valores agora `String[]` são em `String`vez de.
- `BasicHtmlWebResponseObject.BaseResponse`Agora é um `System.Net.Http.HttpResponseMessage` objeto.
- A `Response` Propriedade nas exceções do cmdlet Web agora é `System.Net.Http.HttpResponseMessage` um objeto.
- A análise estrita do cabeçalho RFC agora é padrão para `-Headers` o `-UserAgent` parâmetro e. Isso pode ser ignorado com `-SkipHeaderValidation`.
- `file://`e `ftp://` não há mais suporte para esquemas de URI.
- `System.Net.ServicePointManager`as configurações não são mais respeitadas.
- No momento, não há autenticação baseada em certificado disponível no macOS.
- O uso `-Credential` de em `http://` um URI resultará em um erro. Use um `https://` URI ou forneça o `-AllowUnencryptedAuthentication` parâmetro para suprimir o erro.
- `-MaximumRedirection`agora produz um erro de encerramento quando as tentativas de redirecionamento excedem o limite fornecido em vez de retornar os resultados do último redirecionamento.
