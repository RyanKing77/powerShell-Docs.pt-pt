---
title: Quais são as novidades no PowerShell Core 6.2
description: Novos recursos e alterações lançadas no PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 6a0da8a410e602ae3963e0bc7bace745317d7d4b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058102"
---
# <a name="whats-new-in-powershell-core-62"></a>Quais são as novidades no PowerShell Core 6.2

A versão do PowerShell Core 6.2 se concentrou em melhorias de desempenho, correções de erros e melhorias de cmdlet e idioma menores que melhoram a qualidade. Para ver uma lista completa das melhorias, confira nossas [changelogs](https://github.com/PowerShell/PowerShell/releases) no GitHub.

## <a name="experimental-features"></a>Funcionalidades experimentais

Anteriormente, o suporte para nós habilitamos [funcionalidades experimentais][]. Na versão 6.2, temos quatro funcionalidades experimentais para experimentar. Envie comentários, de modo que melhoramos e decidir se o recurso é aconselhável promover para o status de base.

Utilize `Get-ExperimentalFeature` para obter uma lista das funcionalidades experimentais disponíveis. Pode ativar ou desativar estas funcionalidades com `Enable-ExperimentalFeature` e `Disable-ExperimentalFeature`.

### <a name="command-not-found-suggestions"></a>Comando não foi encontrado sugestões

Esse recurso usa correspondência difusa para encontrar sugestões para comandos ou os cmdlets, que pode ter escrito incorretamente.

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a>Exemplo

Neste exemplo, o nome do cmdlet com erros ortográficos é difusa correspondido a várias sugestões de maior probabilidade de, pelo menos, provavelmente.

```powershell
Get-Commnd
```

```Output
Get-Commnd : The term 'Get-Commnd' is not recognized as the name of a cmdlet, function, script file, or operable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-Commnd
+ ~~~~~~~~~~
+ CategoryInfo          : ObjectNotFound: (Get-Commnd:String) [], CommandNotFoundException
+ FullyQualifiedErrorId : CommandNotFoundException


Suggestion [4,General]: The most similar commands are: Get-Command, Get-Content, Get-Job, Get-Module, Get-Event, Get-Host, Get-Member, Get-Item, Set-Content.
```

### <a name="implicit-remoting-batching"></a>A criação de batches de comunicação remota implícita

Ao usar [comunicação remota implícita](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) num pipeline, PowerShell trata cada comando no pipeline de forma independente. Os objetos são serializados repetidamente e `de-serialized` entre o cliente e o sistema remoto sobre a execução do pipeline.

Com esta funcionalidade, o PowerShell analisa o pipeline para determinar se o comando é seguro executar e existe no sistema de destino. Quando verdadeiro, o PowerShell executa todo o pipeline remotamente e apenas serializa e `de-serializes` os resultados de volta para o cliente.

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

Um teste reais `Get-Process | Sort-Object` ao longo do localhost diminui de 10 a 15 segundos para 20 a 30 **milissegundos**. A funcionalidade apenas precisa de ser ativada no cliente. Sem alterações são necessárias no servidor.

### <a name="temp-drive"></a>Temp Drive

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

Se estiver a utilizar o PowerShell Core nos sistemas operativos diferentes, descobrirá que a variável de ambiente para localizar o diretório temporário é diferente no Windows, macOS e Linux! Com esta funcionalidade, tem um [PSDrive][] chamado `Temp:` que é automaticamente mapeado para a pasta temporária para o sistema operativo que está a utilizar.

#### <a name="example"></a>Exemplo

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> `Get-Content` Temp:/hello.txt
Hello World!
```

Tenha em atenção que comandos nativos de ficheiros (como `ls` no Linux) não estão cientes PSDrives e não verá isto `Temp:` unidade.

### <a name="abbreviation-expansion"></a>Expansão de abreviatura

Cmdlets do PowerShell devem ter nomes descritivos. Isso resulta em nomes longos que são mais difíceis de tipo. Esta funcionalidade permite-lhe apenas escrever os carateres em maiúsculas do cmdlet e usar a conclusão de tabulação para encontrar uma correspondência.

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a>Exemplo

```powershell
PS> i-arsavsf
```

Se pressionar tab e o Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) módulo instalado, este irá autocompletar para:

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> Esta funcionalidade destina-se para ser usado interativamente. Não não possível executar a formas abreviadas dos cmdlets.
> Esta funcionalidade não é um substituto para aliases.

## <a name="breaking-changes"></a>Alterações Interruptivas

- Corrigir `-NoEnumerate` comportamento no `Write-Output` para ser consistente com o Windows PowerShell. (#9069)
- Tornar `Join-String -InputObject 1,2,3` resultar igual a `1,2,3 | Join-String` resultar (#8611) (obrigado @sethvs!)
- Adicione `-Stable` para `Sort-Object` e relacionadas a testes (#7862) (obrigado @KirkMunro!)
- Melhorar `Start-Sleep` cmdlet para aceitar segundos fracionais (#8537) (obrigado @Prototyyppi!)
- Alterar a tabela de hash para utilizar OrdinalIgnoreCase ser `case-insensitive` em todas as culturas (#8566)
- Corrigir **LiteralPath** na `Import-Csv` vincular à `Get-ChildItem` (#8277) de saída (obrigado @iSazonov!)
- Já não ignora uma coluna sem nome se o delimitador de aspas duplas for utilizado numa `Import-Csv` (#7899) (obrigado @Topping!)
- `Get-ExperimentalFeature` não tem mais `-ListAvailable` mudar (#8318)
- Depurar o parâmetro agora conjuntos `$DebugPreference` para **continuar** em vez de **Inquire** (#8195) (obrigado @KirkMunro!)
- Honra `-OutputFormat` se for especificado no comando não interativa, redirecionado, codificado, utilizado com pwsh (#8115)
- Carregar a assemblagem do caminho de base do módulo antes de tentar carregar a partir do GAC (#8073)
- Remover til de pacotes de pré-visualização do Linux (#8244)
- Mover o processamento de `-WorkingDirectory` antes do processamento de perfis (#8079)
- Não adicione `PATHEXT` variável de ambiente Unix (#7697) (obrigado @iSazonov!)

## <a name="known-issues"></a>Problemas Conhecidos

- Comunicação remota em plataformas Windows IOT ARM tem um problema ao carregar módulos. Consulte o (n. º 8053)

## <a name="general-updates-and-fixes"></a>Geral atualizações e correções

- Ativar a conclusão de tabulação de maiúsculas e minúsculas para ficheiros e pastas no sistema de ficheiros de maiúsculas e minúsculas (#8128)
- Tornar PSVersionInfo.PSVersion e PSVersionInfo.PSEdition pública (#8054) (obrigado @KirkMunro!)
- Adicionar a inferência de tipo para `$_`  /  `$PSItem` no `catch{ }` bloqueia (#8020) (obrigado @vexx32!)
- Corrigir a inferência de tipo de invocação de método estático (#8018) (obrigado @SeeminglyScience!)
- Criar tipos de inferido para `Select-Object`, `Group-Object`, **PSObject** e **Hashtable** (#7231) (obrigado @powercode!)
- Suporta o método de chamada com `ByRef-like` escreva parâmetros (#7721)
- Administrar o caso em que o caminho do módulo Windows PowerShell já está a ser PSModulePath o ambiente (#7727)
- Ativar `SecureString` cmdlets para não-Windows-armazenando o texto simples (#9199)
- Melhorar a mensagem de erro não Windows, ao importar clixml com securestring (#7997)
- Adicionar parâmetro ReplyTo para `Send-MailMessage` (#8727) (obrigado @replicaJunction!)
- Adicionar a mensagem obsoleta para `Send-MailMessage` (#9178)
- Corrigir `Restart-Computer` para trabalhar em `localhost` quando WinRM não está presente (#9160)
- Tornar `Start-Job` gera erro de terminação, quando o PowerShell está a ser alojada (#9128)
- Adicionar C# Aceleradores de tipo de estilo e sufixos para ushort, uint, ulong e literais curtos (#7813) (obrigado @vexx32!)
- Foram adicionados sufixos de novo para literais numéricos - consulte [about_Numeric_Literals][] (#7901) (obrigado @vexx32!)
- Comunicar corretamente a nível de impacto quando SupportsShouldProcess não estiver definido como 'true' (#8209) (obrigado @vexx32!)
- Corrigir problemas de conjunto de carateres de pedido nos Cmdlets de Web (#8742) (obrigado @markekraus!)
- Corrigir Expect `100-continue` problema com os Cmdlets da Web (#8679) (obrigado @markekraus!)
- Corrigir o problema de bloqueio de ficheiros com os cmdlets da web (#7676) (obrigado @Claustn!)
- Corrigir o problema de análise de página de código `Invoke-RestMethod` (#8694) (obrigado @markekraus!)
- Refatorar `ConvertTo-Json` para expor JsonObject.ConvertToJson como uma API pública (#8682)
- Adicionar a profundidade máxima configurável no `ConvertFrom-Json` com - profundidade (#8199) (obrigado @louistio!)
- Adicionar parâmetro EscapeHandling `ConvertTo-Json` cmdlet (#7775) (obrigado @iSazonov!)
- Adicione `-CustomPipeName` para pwsh e `Enter-PSHostProcess` (#8889)
- Ativar a criação de links simbólicos relativos no Windows com `New-Item` (#8783)
- Permitir que os utilizadores do Windows no modo de programador para criar links simbólicos sem elevação (#8534)
- Ativar `Write-Information` para aceitar `$null` (#8774)
- Corrigir `Get-Help` para funções avançadas com MAML conteúdo de ajuda (#8353)
- Corrigir `Get-Help` PSTypeName problema com o - parâmetro quando apenas um parâmetro é declarado (#8754) (obrigado @pougetat!)
- Correção de cálculo de token para `Get-Help` executado no ScriptBlock para obter ajuda de comentário. (#8238) (Obrigado @hubuk!)
- Alteração `Get-Help` cmdlet-parâmetro de parâmetro para que ele aceita a cadeia de caracteres matrizes (#8454) (obrigado @sethvs!)
- Resolver PAGER se o caminho contiver espaços (#8571) (obrigado @pougetat!)
- Adicionar linha para a utilização de `less` na função de ajuda para instruir o utilizador como sair (#7998)
- Adicionar suporte para enum e char tipos na `Format-Hex` cmdlet (#8191) (obrigado @iSazonov!)
- Remover ShouldProcess de `Format-Hex` (#8178)
- Adicione novos parâmetros de deslocamento e a contagem para `Format-Hex` e refatorar o cmdlet (#7877) (obrigado @iSazonov!)
- Permitir que "name" como uma chave de alias para "etiqueta" na `ConvertTo-Html`, a entrada 'width' ser um número inteiro de permissão (#8426) (obrigado @mklement0!)
- Scriptblock marca com base calculada propriedades voltem a funcionar `ConvertTo-Html` (#8427) (obrigado @mklement0!)
- Adicionar o cmdlet `Join-String` para a criação de texto de entrada (#7660) do pipeline (obrigado @powercode!)
- Corrigir `Join-String` FormatString lógica de parâmetro de cmdlet (#8449) (obrigado @sethvs!)
- Alteração `Clear-Host` a utilização da `$RAWUI` e desmarque para funcionar em comunicação remota (#8609)
- Alteração `Clear-Host` simplesmente chamado `[console]::clear` e remover o alias clara do Unix (#8603)
- Corrigir LiteralPath na `Import-Csv` vincular à `Get-ChildItem` (#8277) de saída (obrigado @iSazonov!)
- função de ajuda não deve utilizar pager para AliasHelpInfo (#8552)
- Adicione `-UseMinimalHeader` para `Start-Transcript` para minimizar o cabeçalho de transcrição (#8402) (obrigado @lukexjeremy!)
- Adicione `Enable-ExperimentalFeature` e `Disable-ExperimentalFeature` cmdlets (#8318)
- Expor todos os cmdlets da **PSDiagnostics** se logman.exe estiver disponível (#8366)
- Remover **Persist** parâmetro partir `New-PSDrive` no `non-Windows` plataforma (#8291) (obrigado @lukexjeremy!)
- Adicionar suporte para `cd +` (#7206) (obrigado @bergmeister!)
- Ativar `Set-Location -LiteralPath` para trabalhar com pastas com o nome - e + (#8089)
- `Test-Path` Devolve `$false` quando dado vazio ou `$null` (#8080) de valor do caminho (obrigado @vexx32!)
- Permitir que o parâmetro dinâmico a serem retornados, mesmo que o caminho não corresponde a qualquer fornecedor de serviços (#7957)
- Suporte `Get-PSHostProcessInfo` e `Enter-PSHostProcess` em plataformas Unix (#8232)
- Reduzir as alocações no `Get-Content` cmdlet (#8103) (obrigado @iSazonov!)
- Ativar `Add-Content` partilhar o acesso de leitura com outras ferramentas ao escrever o conteúdo (#8091)
- `Get/Add-Content` gera o erro melhorado para criar aplicativos para um contentor (#7823) (obrigado @kvprasoon!)
- Adicione `-Name`, `-NoUserOverrides` e `-ListAvailable` parâmetros `Get-Culture` cmdlet (#7702) (obrigado @iSazonov!)
- Adicionar atributo unificado para conclusão para **Encoding** parâmetro. (#7732) (Obrigado @ThreeFive-O!)
- Permitir numérico Ids e nome de páginas de código registado num **Encoding** parâmetros (#7636) (obrigado @iSazonov!)
- Corrigir `Rename-Item -Path` com o caráter universal char (n. º 7398) (obrigado @kwkam!)
- Ao usar `Start-Transcript` e o ficheiro existe, vazio em vez disso, o ficheiro que a eliminar o (n. º 8131) (obrigado @paalbra!)
- Tornar `Add-Type` abra arquivos de origem com **FileAccess.Read** e **Funkce** explicitamente (#7915) (obrigado @IISResetMe!)
- Corrigir `Enter-PSSession -ContainerId` para o Windows mais recente (#7883)
- Certifique-se **NestedModules** propriedade fica preenchida por `Test-ModuleManifest` (#7859)
- Adicione `%F` maiúsculas para `Get-Date` - UFormat (#7630) (obrigado @britishben!)
- Corrigir `Set-Service -Status Stopped` para parar serviços com dependências (#5525) (obrigado @zhenggu!)

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Funcionalidades experimentais]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
