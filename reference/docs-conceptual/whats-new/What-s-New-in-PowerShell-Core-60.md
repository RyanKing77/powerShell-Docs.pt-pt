# <a name="whats-new-in-powershell-core-60"></a>Novidades no PowerShell Core 6.0

[PowerShell Core 6.0] [ github] é uma edição nova do PowerShell que é a plataforma (Windows, macOS e Linux), open source e criados para ambientes heterogéneos e nuvem híbrida.

## <a name="moved-from-net-framework-to-net-core"></a>Movida do .NET Framework para o .NET Core

PowerShell Core utiliza [2.0 do .NET Core][] como o tempo de execução.
.NET core 2.0 permite núcleo de PowerShell para trabalhar em várias plataformas (Windows, macOS e Linux).
PowerShell Core também expõe o conjunto de API oferecido pelo .NET Core 2.0 para ser utilizado em cmdlets do PowerShell e scripts.

Windows PowerShell utilizados o runtime do .NET Framework para alojar o motor do PowerShell.
Isto significa que o Windows PowerShell expõe o conjunto de API oferecido pelo .NET Framework.

As APIs partilhadas entre o .NET Core e o .NET Framework são definidas como parte da [.NET padrão][].

Para obter mais informações sobre a forma como afeta a compatibilidade de módulo/script entre PowerShell Core e o Windows PowerShell, consulte [Backwards compatibilidade com o Windows PowerShell](#backwards-compatibility-with-windows-powershell).

## <a name="support-for-macos-and-linux"></a>Suporte para macOS e Linux

PowerShell oficialmente suporta agora macOS e do Linux, incluindo:

- Windows 7, 8.1 e 10
- Windows Server 2008 R2, 2012 R2, 2016
- [Canal de ponto e anual do Windows Server][semi-annual]
- Ubuntu 14.04, 16.04 e 17.04
- Debian 8.7 + e 9
- CentOS 7
- Red Hat Enterprise Linux 7
- OpenSUSE 42.2
- Fedora 25, 26
- macOS 10.12+

A nossa Comunidade também tem contribuíram pacotes para as seguintes plataformas, mas não são suportados oficialmente:

- Arch Linux
- Kali Linux
- AppImage (funciona em várias plataformas Linux)

Além disso, temos experimental versões (não suportadas) para as seguintes plataformas:

- Windows no ARM32/ARM64
- Raspbian (Stretch)

Um número de alterações foram efetuado às PowerShell Core 6.0 para torná-lo a funcionar melhor nos sistemas operativos não Windows.
Alguns deles são interrompendo as alterações que afetam o Windows.
Outras pessoas só estão presentes ou aplicável em instalações de não-Windows do PowerShell Core.

- Suporte adicionado para globbing comando nativo em plataformas Unix.
- O `more` funcionalidade respeita o Linux `$PAGER` e assume a predefinição `less`.
  Isto significa que agora pode utilizar carateres universais com binários/comandos nativos (por exemplo, `ls *.txt`). (#3463)
- À direita barra invertida é automaticamente escape ao lidar com os argumentos do comando nativo. (#4965)
- Ignorar o `-ExecutionPolicy` mudar durante a execução do PowerShell em plataformas do Windows não porque a assinatura de script não é atualmente suportado. (#3481)
- Corrigido ConsoleHost que respeite `NoEcho` em plataformas Unix. (#3801)
- Fixo `Get-Help` para suportar a correspondência de padrões sensível em plataformas Unix. (#3852)
- `powershell` página de Man adicionada ao pacote

### <a name="logging"></a>Registo

No macOS, PowerShell utiliza o nativo `os_log` APIs para iniciar sessão da Apple [unified registo sistema][os_log].
No Linux, PowerShell utiliza [Syslog][], uma solução de registo ubíquo.

### <a name="filesystem"></a>Filesystem

Um número de alterações foram efetuado no macOS e Linux para suportar carateres tradicionalmente não suportadas no Windows:

- Caminhos para os cmdlets desconhecem agora uma barra (tanto / e \ escolar como separador de diretório)
- Especificação de diretório de Base de XDG agora é respeitada e utilizada por predefinição:
  - O caminho de perfil do Linux/macOS está localizado em `~/.config/powershell/profile.ps1`
  - O histórico de caminho para guardar está localizado em `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`
  - O caminho do módulo de utilizador está localizado em `~/.local/share/powershell/Modules`
- Suporte para os nomes de ficheiros e pastas que contém o caráter de dois pontos no Unix. (#4959)
- Suporte para nomes de script ou caminhos completos com vírgulas. (#4136) (Thanks para @TimCurwick!)
- Detetar quando `-LiteralPath` é utilizado para suprimir a expansão de caráter universal para os cmdlets de navegação. (#5038)
- Atualizado `Get-ChildItem` funcione mais semelhante a * nix `ls -R` e o Windows `DIR /S` comandos nativos.
  `Get-ChildItem` agora devolve as ligações simbólicas encontradas durante uma pesquisa recursiva e não procura os diretórios que destino essas ligações. (#3780)

### <a name="case-sensitivity"></a>Sensibilidade às maiúsculas e minúsculas

Linux e macOS tendem a ser maiúsculas e minúsculas, enquanto o Windows é sensível preservando maiúsculas e minúsculas.
Em geral, o PowerShell é sensível a maiúsculas e minúsculas.

Por exemplo, as variáveis de ambiente são maiúsculas e minúsculas no macOS e Linux, o maiúsculas e minúsculas da `PSModulePath` variável de ambiente foi padronizada. (#3255) `Import-Module` é sensível a maiúsculas e minúsculas quando está a utilizar um caminho de ficheiro para determinar o nome do módulo. (#5097)

## <a name="support-for-side-by-side-installations"></a>Suporte para instalações de lado a lado

Núcleo de PowerShell está instalado, configurado e executado separadamente a partir do Windows PowerShell.
PowerShell Core tem um pacote ZIP "portáteis".
Utilizar o pacote ZIP, pode instalar qualquer número de versões em qualquer local no disco, incluindo local a uma aplicação que utiliza o PowerShell como uma dependência.
Instalação lado a lado torna mais fácil testar novas versões do PowerShell e migrar os scripts existentes ao longo do tempo.
Lado a lado permite também a efeitos de compatibilidade como scripts podem ser afixados versões específicas que necessitam.

> [!NOTE]
> Por predefinição, o Instalador MSI baseado no Windows efetua uma instalação de atualização no local.
>

## <a name="renamed-powershellexe-to-pwshexe"></a>Mudar o nome `powershell(.exe)` para `pwsh(.exe)`

O nome de binário para PowerShell Core foi alterado de `powershell(.exe)` para `pwsh(.exe)`.
Esta alteração é uma forma determinística para os utilizadores executar o PowerShell Core em máquinas para suportar lado a lado Windows PowerShell e as instalações do PowerShell Core.
`pwsh` Também é muito mais curto e mais fácil para o tipo.

Alterações adicionais para `pwsh(.exe)` de `powershell.exe`:

- Alterar o primeiro parâmetro posicional de `-Command` para `-File`.
  Esta alteração corrige a utilização de `#!` (aka como um shebang) em scripts do PowerShell que estão a ser executados a partir do PowerShell não shells em plataformas do Windows não.
  Também significa que pode executar comandos como `pwsh foo.ps1` ou `pwsh fooScript` sem especificar `-File`.
  No entanto, esta alteração requer que especifique explicitamente `-c` ou `-Command` ao tentar executar comandos como `pwsh.exe -Command Get-Command`. (#4019)
- PowerShell Core aceita o `-i` (ou `-Interactive`) comutador para indicar uma shell interativo. (#3558) Isto permite que o PowerShell para ser utilizado como uma shell predefinida em plataformas Unix.
- Remover parâmetros `-importsystemmodules` e `-psconsoleFile` de `pwsh.exe`. (#4995)
- Alterar `pwsh -version` e ajuda incorporado para `pwsh.exe` para alinhar com outras ferramentas nativas. (#4958 & #4931) (Obrigado @iSazonov)
- Mensagens de erro de um argumento inválido para `-File` e `-Command` e sair códigos consistentes com as normas de Unix (#4573)
- Adicionar `-WindowStyle` parâmetro no Windows. (#4573) Da mesma forma, atualizações de instalações baseadas no pacote em plataformas do Windows não são atualizações no local.

## <a name="backwards-compatibility-with-windows-powershell"></a>Efeitos compatibilidade com o Windows PowerShell

O objetivo principal do PowerShell é permaneça como compatível quanto possível com o Windows PowerShell.
PowerShell Core utiliza [.NET padrão][] 2.0 para proporcionar compatibilidade binária com assemblagens .NET existentes.
Muitos módulos do PowerShell dependem estas assemblagens (frequentemente vezes DLLs), pelo que o .NET padrão lhes permite continuar a trabalhar com .NET Core.
PowerShell Core também inclui um heuristic parecer nas pastas bem conhecidas – como onde a Global Assembly Cache normalmente reside no disco - para localizar as dependências de DLL do .NET Framework.

Pode saber mais sobre o padrão de .NET no [blogue .NET][], deste [YouTube][] vídeo e através de isto [FAQ][] no GitHub.

Foram efetuados melhor esforços para garantir que os módulos do PowerShell de idioma e "incorporado" (como `Microsoft.PowerShell.Management`, `Microsoft.PowerShell.Utility`, etc.) funcionar da mesma forma que no Windows PowerShell.
Em muitos casos, com a ajuda da Comunidade, adicionámos novas funcionalidades e correções de erros para os cmdlets.
Em alguns casos, devido a uma dependência em falta no subjacentes camadas de .NET, a funcionalidade foi removida ou não está disponível.

Maioria dos módulos que são enviados como parte do Windows (por exemplo, `DnsClient`, `Hyper-V`, `NetTCPIP`, `Storage`, etc.) e outros produtos Microsoft, incluindo o Azure e Office não tem sido *explicitamente* convertidos para serem. Ainda NET Core.
A equipa do PowerShell está a trabalhar com estes grupos de produto e equipas para validar e os módulos existentes para PowerShell Core de porta.
Com o padrão de .NET e [CDXML][], muitos destes módulos do Windows PowerShell tradicional funcionarem, aparentemente no PowerShell Core, mas não tiverem sido formally validados e formally não são suportados.

Ao instalar o [ `WindowsPSModulePath` ] [ windowspsmodulepath] módulo, pode utilizar módulos do Windows PowerShell, acrescentando o Windows PowerShell `PSModulePath` para o PowerShell Core `PSModulePath`.

Em primeiro lugar, instalar o `WindowsPSModulePath` módulo a partir da galeria do PowerShell:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin 
Install-Module WindowsPSModulePath -Force
```

Depois de instalar este módulo, execute o `Add-WindowsPSModulePath` cmdlet para adicionar o Windows PowerShell `PSModulePath` para núcleo de PowerShell:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="docker-support"></a>Suporte de docker

PowerShell Core adiciona suporte para contentores de Docker para todas as plataformas principais que suportamos (incluindo várias distros do Linux, Windows Server Core e servidor Nano).

Para obter uma lista completa, consulte as etiquetas em [ `microsoft/powershell` no Hub de Docker][docker-hub].
Para obter mais informações sobre o Docker e PowerShell Core, consulte [Docker][] no GitHub.

## <a name="ssh-based-powershell-remoting"></a>Comunicação remota do PowerShell baseado no SSH

O protocolo de comunicação remota do PowerShell (PSRP) funciona agora com o protocolo Secure Shell (SSH), para além de PSRP baseado em WinRM tradicional.

Isto significa que pode utilizar os cmdlets, como `Enter-PSSession` e `New-PSSession` e autenticar através de SSH.
Tudo o que precisa de executar é registar o PowerShell como um subsistema com um servidor baseado em OpenSSH SSH e pode utilizar existentes baseado no SSH autenticar mecanismos (como as palavras-passe ou chaves privadas) com o tradicional `PSSession` semântica.

Para obter mais informações sobre configuração e utilização do sistema de interação remota baseado no SSH, consulte [comunicação remota do PowerShell através de SSH][ssh-remoting].

## <a name="default-encoding-is-utf-8-without-a-bom"></a>Codificação predefinida é UTF-8 sem um LM

No passado, cmdlets do Windows PowerShell, como `Get-Content`, `Set-Content` utilizado codificações diferentes, tais como ASCII e UTF-16.
A variância na codificação predefinições criado problemas quando a combinação de cmdlets sem especificar uma codificação.

Plataformas do Windows sem utilizam tradicionalmente UTF-8 sem uma marca de ordem de bytes (LM) como a codificação predefinida para ficheiros de texto.
Mais aplicações do Windows e ferramentas são mover na direção oposta ao UTF-16 e para a codificação do LM sem UTF-8.
PowerShell Core altera a codificação predefinida a estar em conformidade com as ecossistemas mais ampla.

Isto significa que todos os cmdlets incorporados a utilizar o `-Encoding` utilização do parâmetro de `UTF8NoBOM` valor por predefinição.
Os seguintes cmdlets são afetados por esta alteração:

- Add-Content
- Export-Clixml
- Export-Csv
- Export-PSSession
- Formato hexadecimal
- Get-Content
- Import-Csv
- New-ModuleManifest
- Out-File
- Selecione cadeia
- Send-MailMessage
- Set-Content

Estes cmdlets também ter sido atualizados para que o `-Encoding` parâmetro universalmente aceita `System.Text.Encoding`.

O valor predefinido de `$OutputEncoding` também foi alterada para UTF-8.

Como melhor prática, deve definir explicitamente codificações de scripts com o `-Encoding` parâmetro para produzir o comportamento determinista entre plataformas.

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>Suporta backgrounding de pipelines com ' e ' comercial (`&`) (#3360)

Colocar `&` no final de um pipeline faz com que o pipeline ser executado como um trabalho do PowerShell.
Quando é backgrounded um pipeline, é devolvido um objeto de tarefa.
Assim que o pipeline está em execução como uma tarefa, todos os padrão `*-Job` cmdlets podem ser utilizados para gerir a tarefa.
Variáveis (ignorando específicos de processos variáveis) utilizadas no pipeline são copiadas automaticamente para a tarefa, por isso, `Copy-Item $foo $bar &` funciona.
A tarefa também é executada no diretório atual, em vez de diretório de raiz do utilizador.
Para mais informações sobre as tarefas do PowerShell, consulte [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs).

## <a name="semantic-versioning"></a>Controlo de versões semântico

- Efetuadas `SemanticVersion` compatível com `SemVer 2.0`. (#5037) (Obrigado @iSazonov!)
- Alterar a predefinição `ModuleVersion` no `New-ModuleManifest` para `0.0.1` para alinhar com SemVer. (#4842) (Obrigado @LDSpits)
- Adicionar `semver` como um acelerador de tipo para `System.Management.Automation.SemanticVersion`. (#4142) (Thanks para @oising!)
- Ativada a comparação entre um `SemanticVersion` instância e um `Version` instância que é criada apenas com `Major` e `Minor` valores da versão.

## <a name="language-updates"></a>Atualizações de idioma

- Implemente escape Unicode análise para que os utilizadores podem utilizar carateres Unicode como argumentos, as cadeias ou nomes de variáveis. (#3958) (Thanks para @rkeithhill!)
- Caráter de escape novo adicionado para ESC: `` `e``
- Foi adicionado suporte para a conversão enumerações a cadeia (#4318) (obrigado @KirkMunro)
- Matriz de elemento único fixo conversão para uma coleção genérica. (#3170)
- Sobrecarga de intervalo de carácter adicionado para o `..` operador, por isso, `'a'..'z'` devolve os carateres de 'a' para 'z'. (#5026) (Obrigado @IISResetMe!)
- Atribuição de variáveis fixa para substituir as variáveis só de leitura
- Push locais das variáveis automáticas 'DottedScopes' quando dotting cmdlets de script (#4709)
- Ativar a utilização da opção 'Singleline, múltiplas' no operador de divisão (#4721) (obrigado @iSazonov)

## <a name="engine-updates"></a>Atualizações do motor

- `$PSVersionTable` tem quatro novas propriedades:
  - `PSEdition`: Este é definido como `Core` no PowerShell Core e `Desktop` no Windows PowerShell
  - `GitCommitId`: Este é o ID de consolidação de Git do Git ramo ou etiqueta onde foi criado o PowerShell.
    Nas compilações de lançamento, provavelmente será o mesmo que `PSVersion`.
  - `OS`: Este é uma cadeia de versão do SO devolvida pelo `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription`
  - `Platform`: Este é devolvido pelo `[System.Environment]::OSVersion.Platform` estiver definido como `Win32NT` no Windows, `MacOSX` no macOS, e `Unix` no Linux.
- Remover o `BuildVersion` propriedade da `$PSVersionTable`.
  Esta propriedade foi vivamente associada para a versão de compilação do Windows.
  Em vez disso, recomendamos que utilize `GitCommitId` para obter a versão de compilação exato do PowerShell Core. (#3877) (Thanks para @iSazonov!)
- Remover `ClrVersion` propriedade da `$PSVersionTable`.
  Esta propriedade é irrelevantes para .NET Core e apenas mantida no .NET Core para fins de legado específicos que são forçando para o PowerShell.
- Adicionar três novas variáveis automáticas para determinar se o PowerShell está em execução no SO determinada: `$IsWindows`, `$IsMacOs`, e `$IsLinux`.
- Adicionar `GitCommitId` a faixa de PowerShell Core.
  Agora que não tem de executar `$PSVersionTable` assim que iniciar o PowerShell para obter a versão! (#3916) (Thanks para @iSazonov!)
- Adicionar um ficheiro de configuração JSON chamado `powershell.config.json` no `$PSHome` para armazenar algumas definições necessárias antes do tempo de arranque (por exemplo, `ExecutionPolicy`).
- Não bloqueia pipeline ao executar o Windows. EXE
- Enumeração ativada de coleções de COM. (#4553)

## <a name="cmdlet-updates"></a>Atualizações do cmdlet

### <a name="new-cmdlets"></a>Novos cmdlets

- Adicionar `Get-Uptime` para `Microsoft.PowerShell.Utility`.
- Adicionar `Remove-Alias` comando. (#5143) (Obrigado @PowershellNinja!)
- Adicionar `Remove-Service` para o módulo de gestão. (#4858) (Obrigado @joandrsn!)

### <a name="web-cmdlets"></a>Cmdlets da Web

- Adicione suporte de autenticação de certificado para os cmdlets do web. (#4646) (Obrigado @markekraus)
- Adicione suporte para os cabeçalhos do conteúdo para os cmdlets de web. (#4494 & #4640) (Obrigado @markekraus)
- Adicione suporte de cabeçalho de ligação vários Cmdlets do Web. (#5265) (Obrigado @markekraus!)
- Suporta paginação do cabeçalho de ligação na web cmdlets (#3828)
  - Para `Invoke-WebRequest`, quando a resposta inclui um cabeçalho de ligação criamos uma propriedade de RelationLink como um dicionário que representa os URLs e `rel` de atributos e certifique-se de que os URLs são absolutos para o tornar mais fácil para o programador utilizar.
  - Para `Invoke-RestMethod`, quando a resposta inclui um cabeçalho de ligação expomos um `-FollowRelLink` comutador automaticamente seguir `next` `rel` ligações até que já não existem ou uma vez atingiu o opcional `-MaximumFollowRelLink` valor do parâmetro.
- Adicionar `-CustomMethod` parâmetro para cmdlets do web para permitir verbos de método não padrão. (#3142) (Thanks para @Lee303!)
- Adicionar `SslProtocol` suportar a Web Cmdlets. (#5329) (Obrigado @markekraus!)
- Adicionar Multipart suporte aos cmdlets do web. (#4782) (Obrigado @markekraus)
- Adicionar `-NoProxy` aos cmdlets do web para que o se ignorar a definição de proxy de todo sistema. (#3447) (Thanks para @TheFlyingCorpse!)
- Agente de utilizador de Cmdlets do Web relatórios agora a plataforma do SO (#4937) (obrigado @LDSpits)
- Adicionar `-SkipHeaderValidation` mudar para cmdlets do web para suportar a adição de cabeçalhos sem validar o valor do cabeçalho. (#4085)
- Ative web cmdlets não valide o certificado HTTPS do servidor, se necessário.
- Adicione parâmetros de autenticação para cmdlets do web. (#5052) (Obrigado @markekraus)
  - Adicionar `-Authentication` que fornece as três opções: básico, OAuth e portador.
  - Adicionar `-Token` para obter o portador token para as opções de OAuth e portador.
  - Adicionar `-AllowUnencryptedAuthentication` para ignorar a autenticação é fornecida para qualquer esquema de transporte que não seja HTTPS.
- Adicionar `-ResponseHeadersVariable` para `Invoke-RestMethod` para ativar a captura de cabeçalhos de resposta. (#4888) (Obrigado @markekraus)
- Corrija os cmdlets de web para incluir a resposta HTTP a exceção quando o código de estado de resposta não se encontra com êxito. (#3201)
- Alterar web cmdlets `UserAgent` de `WindowsPowerShell` para `PowerShell`. (#4914) (Obrigado @markekraus)
- Adicionar explícita `ContentType` deteção para `Invoke-RestMethod` (#4692)
- Corrigir web cmdlets `-SkipHeaderValidation` para trabalhar com os cabeçalhos de agente de utilizador não padrão. (#4479 & #4512) (Obrigado @markekraus)

### <a name="json-cmdlets"></a>JSON cmdlets

- Adicionar `-AsHashtable` para `ConvertFrom-Json` para devolver um `Hashtable` em vez disso. (#5043) (Obrigado @bergmeister!)
- Utilize o formatador prettier com `ConvertTo-Json` saída. (#2787) (Thanks para @kittholland!)
- Adicionar `Jobject` suporte de serialização para `ConvertTo-Json`. (#5141)
- Corrigir `ConvertFrom-Json` para anular a serialização de uma matriz de cadeias partir do pipeline que em conjunto construir uma cadeia JSON concluída.
  Isto corrige alguns casos onde newlines seria quebrar JSON análise. (#3823)
- Remova o `AliasProperty "Count"` definida para `System.Array`.
  Esta ação remove o supérfluas `Count` propriedade nalguns `ConvertFrom-Json` saída. (#3231) (Thanks para @PetSerAl!)

### <a name="csv-cmdlets"></a>Cmdlets CSV

- Adicionar `PSTypeName` suporte para `Import-Csv` e `ConvertFrom-Csv`. (#5389) (Obrigado @markekraus!)
- Certifique- `Import-Csv` suporta `CR`, `LF`, e `CRLF` como delimitadores de linha. (#5363) (Obrigado @iSazonov!)
- Certifique- `-NoTypeInformation` a predefinição no `Export-Csv` e `ConvertTo-Csv`. (#5164) (Obrigado @markekraus)

### <a name="service-cmdlets"></a>Cmdlets de serviço

- Adicionar propriedades `UserName`, `Description`, `DelayedAutoStart`, `BinaryPathName`, e `StartupType` para o `ServiceController` objectos devolvidos pelo `Get-Service`. (#4907) (Obrigado @joandrsn)
- Adicionar a funcionalidade para definir credenciais no `Set-Service` comando. (#4844) (Obrigado @joandrsn)

### <a name="other-cmdlets"></a>Outros cmdlets

- Adicionar um parâmetro para `Get-ChildItem` chamado `-FollowSymlink` symlinks que atravessa a pedido, com verifica a existência de ciclos de ligação. (#4020)
- Atualização `Add-Type` para suportar `CSharpVersion7`. (#3933) (Thanks para @iSazonov)
- Remova o `Microsoft.PowerShell.LocalAccounts` módulo devido à utilização de APIs não suportadas até a melhor solução é encontrada. (#4302)
- Remova o `*-Counter` cmdlets no `Microsoft.PowerShell.Diagnostics` devido à utilização de APIs não suportadas até a melhor solução é encontrada. (#4303)
- Adicionar suporte para `Invoke-Item -Path <folder>`. (#4262)
- Adicionar `-Extension` e `-LeafBase` muda para `Split-Path` para que pode dividir caminhos entre a extensão de nome de ficheiro e o resto do nome de ficheiro. (#2721) (Thanks para @powercode!)
- Adicionar parâmetros `-Top` e `-Bottom` para `Sort-Object` de ordenação de parte superior/na parte inferior N
- Expor o processo de principal de um processo adicionando o `CodeProperty "Parent"` para `System.Diagnostics.Process`. (#2850) (Thanks para @powercode!)
- Utilizar MB, em vez de KB para colunas de memória do `Get-Process`
- Adicionar `-NoNewLine` mudar para `Out-String`. (#5056) (Obrigado @raghav710)
- `Move-Item` cmdlet honra `-Include`, `-Exclude`, e `-Filter` parâmetros. (#3878)
- Permitir `*` a ser utilizado no caminho de registo para `Remove-Item`. (#4866)
- Adicionar `-Title` para `Get-Credential` e unificar a experiência de linha de comandos entre plataformas.
- Adicionar o `-TimeOut` parâmetro `Test-Connection`. (#2492)
- `Get-AuthenticodeSignature` cmdlets agora podem obter timestamp de assinatura de ficheiro. (#4061)
- Remover não suportado `-ShowWindow` mudar da `Get-Help`. (#4903)
- Corrigir `Get-Content -Delimiter` por não incluir o delimitador dos elementos de matriz de devolvido (#3706) (obrigado @mklement0)
- Adicionar `Meta`, `Charset`, e `Transitional` parâmetros `ConvertTo-HTML` (#4184) (obrigado @ergo3114)
- Adicionar `WindowsUBR` e `WindowsVersion` propriedades `Get-ComputerInfo` resultado
- Adicionar `-Group` parâmetro `Get-Verb`
- Adicionar `ShouldProcess` suportar a `New-FileCatalog` e `Test-FileCatalog` (correções `-WhatIf` e `-Confirm`). (#3074) (Thanks para @iSazonov!)
- Adicionar `-WhatIf` mudar para `Start-Process` cmdlet (#4735) (obrigado @sarithsutha)
- Adicionar `ValidateNotNullOrEmpty` demasiados parâmetros existentes.

## <a name="tab-completion"></a>Conclusão de separador

- Melhorado a inferência do tipo na conclusão de separador com base nos valores de variáveis do tempo de execução. (#2744) (Thanks para @powercode!) Isto permite a conclusão de separador situações como:

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- Adicionar a conclusão de separador da tabela hash para `-Property` de `Select-Object`. (#3625) (Thanks para @powercode)
- Ativar a conclusão automática argumento para `-ExcludeProperty` e `-ExpandProperty` de `Select-Object`. (#3443) (Thanks para @iSazonov!)
- Corrigir um erro na conclusão de separador para tornar `native.exe --<tab>` chamada para nativo que conclua. (#3633) (Thanks para @powercode!)

## <a name="breaking-changes"></a>As alterações de última hora

Tiver introduzimos um número de alterações no PowerShell Core 6.0.
Para ler mais sobre os mesmos em detalhe, consulte [interrompendo as alterações no PowerShell Core 6.0][breaking-changes].

## <a name="debugging"></a>Depuração

- Suporte para depuração step-in remota para `Invoke-Command -ComputerName`. (#3015)
- Ativar depuração do Gestor de enlaces iniciar sessão PowerShell Core

## <a name="filesystem-updates"></a>Atualizações do sistema de ficheiros

- Ative a utilização do fornecedor do sistema de ficheiros a partir de um caminho UNC. ($4998)
- `Split-Path` agora funciona com o UNC raízes
- `cd` sem argumentos agora comporta-se como `cd ~`
- PowerShell Core fixo para permitir a utilização de caminhos que são mais de 260 caracteres de comprimento. (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>Correções de erros e melhorias de desempenho

Fizemos *muitos* melhorias de desempenho através do PowerShell, incluindo no tempo de arranque, vários cmdlets incorporados e interação com os binários nativos.

Podemos ter também um número fixo de erros no PowerShell Core.
Para obter uma lista completa das correções e as alterações, consulte a nossa [changelog][] no GitHub.

## <a name="telemetry"></a>Telemetria

- Telemetria de núcleos 6.0 adicionado do PowerShell para o anfitrião da consola ao relatório dois valores (#3620):
  - a plataforma do SO (`$PSVersionTable.OSDescription`)
  - a versão exata do PowerShell (`$PSVersionTable.GitCommitId`)

Se pretender ativamente de que esta telemetria, simplesmente elimine `$PSHome\DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` ou criar `POWERSHELL_TELEMETRY_OPTOUT` variável de ambiente com um dos seguintes valores: `true`, `1` ou `yes`.
Eliminar este ficheiro ou criar a variável ignora toda a telemetria mesmo antes de primeira execução do PowerShell.
Planeamos também no exposição estes dados de telemetria e as informações que glean de telemetria no [dashboard Comunidade][community-dashboard].
Pode encontrar mais informações sobre como utilizamos esses dados deste [blogue][telemetry-blog].

[github]: https://github.com/PowerShell/PowerShell
[2.0 do .NET Core]: https://docs.microsoft.com/dotnet/core/
[.NET padrão]: https://docs.microsoft.com/en-us/dotnet/standard/net-standard
[os_log]: https://developer.apple.com/documentation/os/logging
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[breaking-changes]: https://github.com/PowerShell/PowerShell/tree/master/docs/BREAKINGCHANGES.md
[changelog]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[telemetry-blog]: https://blogs.msdn.microsoft.com/powershell/2017/01/31/powershell-open-source-community-dashboard/
[Padrão de .NET]: https://docs.microsoft.com/dotnet/standard/net-standard
[blogue .NET]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
[FAQ]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[CDXML]: https://msdn.microsoft.com/library/jj542525(v=vs.85).aspx
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
