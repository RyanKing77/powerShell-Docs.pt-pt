---
ms.date: 05/17/2018
keywords: PowerShell, core
title: Eliminar as alterações para o PowerShell 6.0
ms.openlocfilehash: 60ce7a1676403bb08b57bf852ba725acde86a30c
ms.sourcegitcommit: 2d9cf1ccb9a653db7726a408ebcb65530dcb1522
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/19/2018
---
# <a name="breaking-changes-for-powershell-60"></a>Eliminar as alterações para o PowerShell 6.0

## <a name="features-no-longer-available-in-powershell-core"></a>Funcionalidades já não está disponíveis no PowerShell Core

### <a name="powershell-workflow"></a>Fluxo de trabalho do PowerShell

[Fluxo de trabalho do PowerShell] [ workflow] é uma funcionalidade no Windows PowerShell que é criada de [Windows Workflow Foundation (WF)] [ workflow-foundation] que permite a criação do obter runbooks robustos para tarefas de longa execução ou paralelizadas.

Devido à falta de suporte para Windows Workflow Foundation em .NET Core, não irá continuar suportar o fluxo de trabalho do PowerShell no PowerShell Core.

No futuro, gostaríamos de ativar o paralelismo/simultaneidade nativa no idioma do PowerShell sem a necessidade de fluxo de trabalho do PowerShell.

[workflow]: https://docs.microsoft.com/powershell/scripting/core-powershell/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Snap-ins personalizados

[Snap-ins do PowerShell] [ snapin] são um predecessor módulos do PowerShell que não tenham adoção ampla Comunidade do PowerShell.

Devido à complexidade de suportar o snap-ins e os respetivos falta de utilização na Comunidade, já não suportamos o snap-ins personalizados no PowerShell Core.

Hoje em dia, interrompe o `ActiveDirectory` e `DnsClient` módulos no Windows e Windows Server.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>Cmdlets do WMI v1

Devido à complexidade de suportar dois conjuntos de módulos com base em WMI, iremos remover os cmdlets de v1 WMI do PowerShell Core:

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

Em vez disso, recomendamos que é a utilização de cmdlets CIM (também conhecido como WMI v2) que fornecem a mesma funcionalidade com novas funcionalidades e uma sintaxe reestruturada:

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

Devido à utilização de APIs não suportadas, `Microsoft.PowerShell.LocalAccounts` foi removido do PowerShell Core até a melhor solução é encontrada.

### <a name="-counter-cmdlets"></a>Cmdlets `*-Counter`

Devido à utilização de APIs não suportadas, o `*-Counter` foi removido do PowerShell Core até a melhor solução é encontrada.

## <a name="enginelanguage-changes"></a>Alterações do motor de linguagem

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>Mudar o nome `powershell.exe` para `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

Para conceder aos utilizadores uma forma determinística efetuar chamadas PowerShell Core do Windows (por oposição a Windows PowerShell), o binário de PowerShell Core foi alterado para `pwsh.exe` no Windows e `pwsh` em plataformas não Windows.

O nome encurtado também é consistente com a atribuição de nomes de shells em plataformas não Windows.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>Não insira as quebras de linha de saída (exceto para tabelas) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Anteriormente, saída foi alinhada com a largura da consola e foram adicionadas quebras de linha em que a largura final da consola, que significa que o resultado não obter reformatado conforme esperado se o terminal foi redimensionado. Esta alteração não foi aplicada a tabelas, tal como as quebras de linha são necessárias para manter as colunas alinhadas.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>Ignorar verificação de elemento nulo para coleções com um tipo de elemento do tipo de valor [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

Para o `Mandatory` parâmetro e `ValidateNotNull` e `ValidateNotNullOrEmpty` atributos, ignorar a verificação de elemento nulo se o tipo de elemento da coleção é o tipo de valor.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>Alteração `$OutputEncoding` utilizar `UTF-8 NoBOM` codificação em vez de ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

A codificação anterior, ASCII (7 bits), resultaria numa alteração incorreta de saída em alguns casos. Esta alteração é certificar- `UTF-8 NoBOM` predefinido, que ela vai preservando Unicode saída com uma codificação suportado pela maioria das ferramentas e sistemas operativos.

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>Remover `AllScope` da maioria dos aliases de predefinição [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

Para acelerar a criação de âmbito, `AllScope` foi removida da maioria dos aliases de predefinição. `AllScope` foi deixada para alguns aliases utilizados com frequência, em que a pesquisa foi mais rápida.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose` e `-Debug` já não substitui `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

Anteriormente, se `-Verbose` ou `-Debug` foram especificados, que overrode o comportamento de `$ErrorActionPreference`. Com esta alteração, `-Verbose` e `-Debug` já não afetar o comportamento de `$ErrorActionPreference`.

## <a name="cmdlet-changes"></a>Alterações de cmdlet

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>RestMethod invocar não devolve informações úteis quando não são devolvidos dados. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

Quando uma API devolve apenas `null`, Invoke RestMethod foi serializar este como cadeia `"null"` em vez de `$null`. Esta alteração corrige a lógica na `Invoke-RestMethod` corretamente serializar um valor único válido JSON `null` literal como `$null`.

### <a name="remove--computername-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>Remover `-ComputerName` de `*-Computer` cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

Devido a problemas de comunicação remota RPC na CoreFX (particularmente em plataformas não Windows) e garantir uma experiência consistente comunicação remota do PowerShell, o `-ComputerName` parâmetro foi removido a `\*-Computer` cmdlets. Utilize `Invoke-Command` em vez disso, como a forma de executar cmdlets remotamente.

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>Remover `-ComputerName` de `*-Service` cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

Para poder encorajar a utilização consistente de PSRP, o `-ComputerName` parâmetro foi removido do `*-Service` cmdlets.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>Corrigir `Get-Item -LiteralPath a*b` se `a*b` , na verdade, não existe para devolver o erro [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

Anteriormente, `-LiteralPath` fornecido um caráter universal seria processá-lo a mesma como `-Path` e se o caráter universal não encontrado nenhum ficheiro, seria sair silenciosamente. Correto de comportamento deve ser a `-LiteralPath` é literal, pelo que o se o ficheiro não existir, devia erro. Alteração é tratar carateres universais utilizado com `-Literal` como literal.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>`Import-Csv` deve aplicar `PSTypeNames` após a importação quando as informações de tipo não estão presentes no CSV [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

Anteriormente, objetos exportados utilizando `Export-CSV` com `TypeInformation` importados com `ConvertFrom-Csv` não foram manter as informações de tipo. Esta alteração adiciona as informações de tipo para `PSTypeNames` membro se estiver disponível do ficheiro CSV.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`-NoTypeInformation` deve ser predefinido no `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Esta alteração foi efetuada a comentários de clientes de endereço no comportamento predefinido da `Export-CSV` para incluir informações de tipo.

Anteriormente, o cmdlet seria saída um comentário como a primeira linha que contém o nome do tipo do objeto. A alteração é suprimir esta por predefinição, não é compreendido pela maioria das ferramentas. Utilize `-IncludeTypeInformation` para manter o comportamento de anterior.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>Cmdlets de Web deve avisar quando `-Credential` é enviado através de ligações não encriptadas [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

Quando utilizar HTTP, o conteúdo, incluindo palavras-passe é enviado como texto não encriptado. Esta alteração é não permitir esta por predefinição e devolver um erro se as credenciais estão a ser passadas de forma inseguras. Os utilizadores podem ignorar este utilizando o `-AllowUnencryptedAuthentication` mudar.

## <a name="api-changes"></a>Alterações de API

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>Remover `AddTypeCommandBase` classe [#5407](https://github.com/PowerShell/PowerShell/issues/5407)

O `AddTypeCommandBase` classe foi removida do `Add-Type` para melhorar o desempenho. Esta classe é apenas utilizado pelo cmdlet Add-Type e não deve afetar os utilizadores.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>Unificar cmdlets com o parâmetro `-Encoding` seja do tipo `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

O `-Encoding` valor `Byte` foi removido dos cmdlets do fornecedor de sistema de ficheiros. Um novo parâmetro `-AsByteStream`, agora é utilizada para especificar que um fluxo de bytes, é necessário como entrada ou de que o resultado é um fluxo de bytes.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>Adicionar melhores mensagem de erro para vazio e nulo `-UFormat` parâmetro [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

Anteriormente, quando transmitir um formato vazio string para `-UFormat`, aparece uma mensagem de erro inúteis. Foi adicionado um erro de mais descritivo.

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>Limpar o código de consola [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

As seguintes funcionalidades foram removidas à medida que não são suportados no PowerShell Core, existem não planos para adicionar suporte, conforme existem por motivos de legado para o Windows PowerShell: `-psconsolefile` comutador e o código, `-importsystemmodules` comutador e o código e o tipo de letra a alteração do código.

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>Remover `RunspaceConfiguration` suporta [#4942](https://github.com/PowerShell/PowerShell/issues/4942)

Anteriormente, quando criar um espaço de execução do PowerShell através de programação utilizando a API pode utilizar o legado [ `RunspaceConfiguration` ] [ runspaceconfig] ou o mais recente [ `InitialSessionState` ] [ iss]. Esta alteração removeu o suporte para `RunspaceConfiguration` e só suporta `InitialSessionState`.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript` vincular argumentos `$input` em vez de `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

Uma posição incorreta de um parâmetro resultou numa args foi transmitida uma entrada em vez de como argumentos.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>Remover não suportado `-showwindow` mudar da `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow` depende do WPF, que não é suportado no CoreCLR.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>Permitir * a ser utilizado no caminho de registo para `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

Anteriormente, `-LiteralPath` fornecido um caráter universal seria processá-lo a mesma como `-Path` e se o caráter universal não encontrado nenhum ficheiro, seria sair silenciosamente. Correto de comportamento deve ser a `-LiteralPath` é literal, pelo que o se o ficheiro não existir, devia erro. Alteração é tratar carateres universais utilizado com `-Literal` como literal.

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>Corrigir `Set-Service` falhar teste [#4802](https://github.com/PowerShell/PowerShell/issues/4802)

Anteriormente, se `New-Service -StartupType foo` foi utilizada, `foo` foi ignorada e o serviço foi criado com algum tipo de arranque predefinidas. Esta alteração é explicitamente gerar um erro para um tipo de arranque inválida.

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>Mudar o nome `$IsOSX` para `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

A nomenclatura do PowerShell deve estar consistente com a nossa nomenclatura e em conformidade com a utilização da Apple macOS em vez de OSX. No entanto, para facilitar a leitura e consistentemente iremos são permanecendo com Pascal tem maiúsculas e minúsculas.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>Fazer com que mensagens de erro consistente quando o script inválido foi transmitido para - ficheiro, melhor erro quando transmitido argumento ambíguo [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

Alterar os códigos de saída de `pwsh.exe` para alinhar com as convenções de Unix

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>Remoção de `LocalAccount` e os cmdlets da `Diagnostics` módulos. [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

Devido a APIs não suportadas, o `LocalAccounts` módulo e a `Counter` cmdlets no `Diagnostics` módulo foram removidas até a melhor solução é encontrada.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>Executar script do powershell com o parâmetro booleano não funciona [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

Anteriormente, utilizando o powershell.exe (agora `pwsh.exe`) para executar um script do PowerShell utilizando `-File` não fornecida nenhuma forma de passar $true/$false como valores de parâmetros. Suporte para $true/$false como analisados valores para parâmetros foi adicionado. Valores de comutador também são suportados como sintaxe atualmente documentado não funciona.

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>Remover `ClrVersion` propriedade da `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

O `ClrVersion` propriedade `$PSVersionTable` é não útil com CoreCLR, os utilizadores finais devem não estar a utilizar esse valor para determinar a compatibilidade.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>Alterar o parâmetro posicional `powershell.exe` de `-Command` para `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

Ative a utilização de shebang do PowerShell em plataformas não Windows. Isto significa que em sistemas Unix com base, pode efetuar um executável de script do PowerShell invocará automaticamente em vez de invocar explicitamente `pwsh`. Isto também significa que agora pode efetuar ações como `powershell foo.ps1` ou `powershell fooScript` sem especificar `-File`. No entanto, esta alteração requer agora que especifique explicitamente `-c` ou `-Command` ao tentar efetuar ações como `powershell.exe Get-Command`.

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>Implementar a análise de escape Unicode [#3958](https://github.com/PowerShell/PowerShell/issues/3958)

`` `u#### `` ou `` `u{####} `` é convertido para o carácter Unicode correspondente. Para um literal de saída `` `u ``, como o backtick de escape: ``` ``u ```.

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>Alteração `New-ModuleManifest` codificação a `UTF8NoBOM` em plataformas do Windows não [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

Anteriormente, `New-ModuleManifest` cria psd1 manifestos em UTF-16 com LM, criação de um problema para ferramentas de Linux. Esta alteração inovadora altera a codificação de `New-ModuleManifest` ser UTF (nenhum LM) não sejam Windows plataformas.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>Impedir `Get-ChildItem` de recursing para symlinks (#1875). [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Esta alteração coloca `Get-ChildItem` mais de acordo com o Unix `ls -r` e o Windows `dir /s` comandos nativos. Como os comandos mencionados, o cmdlet apresenta as ligações simbólicas encontrado durante a recursão de diretórios, mas não recurse em-los.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>Corrigir `Get-Content -Delimiter` por não incluir o delimitador de linhas devolvido [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Anteriormente, o resultado ao utilizar `Get-Content -Delimiter` foi inconsistente e inconveniente, conforme é necessário processamento adicional dos dados para remover o delimitador. Esta alteração remove o delimitador de linhas devolvido.

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>Implementar o formato hexadecimal em c# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

O `-Raw` parâmetro é agora uma "sem operações" (que faz nada). Passa todas a saída serão apresentadas com uma representação fiel dos números existentes que incluem todos os bytes para o respetivo tipo (o que o `-Raw` parâmetro formally estava a fazer antes desta alteração).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>PowerShell como um shell predefinida não funciona com o comando de scripts [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

Em Unix, é uma convenção de shells aceitar `-i` para uma shell interativa e muitas ferramentas de esperam este comportamento (`script` por exemplo e quando a definição do PowerShell como a shell predefinida) e chama o shell com o `-i` mudar. Esta alteração é interrompendo que `-i` anteriormente podia ser utilizado como mão curta para corresponder `-inputformat`, que agora tem de ser `-in`.

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Correção de erro de digitação no nome da propriedade Get-ComputerInfo [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber` foi mal escritos como `BiosSeralNumber` e foi alterada para a ortografia correta.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>Adicionar `Get-StringHash` e `Get-FileHash` cmdlets [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Esta alteração é que algumas algoritmos de hash não são suportados pelo CoreFX, pelo que já não estão disponíveis:

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>Adicionar a validação no `Get-*` cmdlets onde transmitir $null devolve todos os objetos em vez de erro [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

Transmitir `$null` para qualquer um da seguinte gera agora um erro:

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

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a>Adicionar suportam o formato de ficheiro expandidos de registo do W3C em `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

Anteriormente, o `Import-Csv` cmdlet não pode ser utilizado diretamente a importar os ficheiros de registo no formato de registo expandido de W3C e ação adicional, seria necessária. Com esta alteração, o formato de registo expandido de W3C é suportado.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>Problema de enlace de parâmetro com `ValueFromRemainingArguments` nas funções de PS [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments` Agora que devolve os valores como uma matriz em vez de um único valor que próprio é uma matriz.

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>`BuildVersion` é removido do `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Remova o `BuildVersion` propriedade da `$PSVersionTable`. Esta propriedade foi associada para a versão de compilação do Windows. Em vez disso, recomendamos que utilize `GitCommitId` para obter a versão de compilação exato do PowerShell Core.

### <a name="changes-to-web-cmdlets"></a>Alterações aos Cmdlets da Web

A API .NET subjacente dos Web Cmdlets foi alterada para `System.Net.Http.HttpClient`. Esta alteração fornece várias vantagens. No entanto, esta alteração, juntamente com uma falta de interoperabilidade com o Internet Explorer resultaram em várias alterações numa `Invoke-WebRequest` e `Invoke-RestMethod`.

- `Invoke-WebRequest` suporta agora básico HTML analisar apenas. `Invoke-WebRequest` devolve sempre um `BasicHtmlWebResponseObject` objeto. O `ParsedHtml` e `Forms` propriedades foram removidas.
- `BasicHtmlWebResponseObject.Headers` os valores são agora `String[]` em vez de `String`.
- `BasicHtmlWebResponseObject.BaseResponse` é agora um `System.Net.Http.HttpResponseMessage` objeto.
- O `Response` propriedade Web Cmdlet exceções está agora um `System.Net.Http.HttpResponseMessage` objeto.
- Análise de cabeçalho RFC Strict agora é a predefinição para o `-Headers` e `-UserAgent` parâmetro. Isto pode ser omitido com `-SkipHeaderValidation`.
- `file://` e `ftp://` já não são suportados esquemas URI.
- `System.Net.ServicePointManager` definições já não são cumpridas.
- Não é atualmente a autenticação não baseada em certificado disponível no macOS.
- A utilização de `-Credential` através de um `http://` URI resultará num erro. Utilize um `https://` URI ou forneça o `-AllowUnencryptedAuthentication` parâmetro para suprimir o erro.
