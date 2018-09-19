---
title: Quais são as novidades no PowerShell Core 6.0
description: Novos recursos e alterações lançadas no PowerShell Core 6.0
ms.date: 08/06/2018
ms.openlocfilehash: 83c104d838db9d86fe1d485e92245a9c8f2d2057
ms.sourcegitcommit: 59e568ac9fa8ba28e2c96932b7c84d4a855fed2f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/18/2018
ms.locfileid: "46289247"
---
# <a name="whats-new-in-powershell-core-60"></a>Quais são as novidades no PowerShell Core 6.0

[PowerShell Core 6.0] [ github] é uma nova edição do PowerShell que é Multiplataforma (Windows, macOS e Linux), código-fonte aberto e criada para ambientes heterogêneos e a cloud híbrida.

## <a name="moved-from-net-framework-to-net-core"></a>Movido do .NET Framework para o .NET Core

Utiliza o PowerShell Core [.NET Core 2.0][] como seu tempo de execução.
.NET core 2.0 permite que o PowerShell Core trabalhar em várias plataformas (Windows, macOS e Linux).
O PowerShell Core também expõe o conjunto de APIS oferecido pelo .NET Core 2.0 para ser usado em scripts e cmdlets do PowerShell.

Windows PowerShell utilizados o tempo de execução do .NET Framework para alojar o motor do PowerShell.
Isso significa que o Windows PowerShell expõe o conjunto de APIS oferecido pelo .NET Framework.

As APIs partilhadas entre o .NET Core e o .NET Framework são definidas como parte da [.NET Standard][].

Para obter mais informações sobre como isso afeta a compatibilidade de módulo/script entre o PowerShell Core e o Windows PowerShell, consulte [compatibilidade com versões anteriores com o Windows PowerShell](#backwards-compatibility-with-windows-powershell).

## <a name="support-for-macos-and-linux"></a>Suporte para macOS e Linux

PowerShell agora oficialmente suporta o macOS e Linux, incluindo:

- Windows 7, 8.1 e 10
- Windows Server 2008 R2, 2012 R2, 2016
- [Canal Semianual do Windows Server][semi-annual]
- Ubuntu 14.04 e 17.04 16.04
- Debian 8,7 + e 9
- CentOS 7
- Red Hat Enterprise Linux 7
- OpenSUSE 42.2
- Fedora 25, 26
- macOS 10.12 +

Nossa Comunidade também contribuiu pacotes para as seguintes plataformas, mas não são suportadas oficialmente:

- Arch Linux
- Kali Linux
- AppImage (funciona em várias plataformas Linux)

Também temos experimentais versões (não suportados) para as seguintes plataformas:

- Windows no ARM32/ARM64
- Raspbian (Stretch.)

Um número de alterações foram efetuado no PowerShell Core 6.0 fazê-lo funcionar melhor em sistemas de não-Windows.
Alguns deles são significativas alterações, que também afetam o Windows.
Outras pessoas só estão presentes ou aplicável em instalações de não-Windows, do PowerShell Core.

- Foi adicionado suporte para globbing comando nativo em plataformas Unix.
- O `more` funcionalidade respeita a Linux `$PAGER` e o padrão é `less`.
  Isso significa que agora pode utilizar carateres universais com binários/comandos nativos (por exemplo, `ls *.txt`). (#3463)
- À direita barra invertida é automaticamente escape ao lidar com argumentos de comando nativo. (#4965)
- Ignorar o `-ExecutionPolicy` mude durante a execução do PowerShell em plataformas não Windows, porque a assinatura de script não é atualmente suportada. (#3481)
- Corrigido ConsoleHost honrando `NoEcho` em plataformas Unix. (#3801)
- Foi corrigido `Get-Help` para suportar a correspondência de padrões maiúsculas de minúsculas em plataformas Unix. (#3852)
- `powershell` adicionado ao pacote de página de Man

### <a name="logging"></a>Registo

No macOS, PowerShell utiliza nativa `os_log` APIs para iniciar sessão da Apple [unificada do sistema de registo][os_log].
No Linux, utiliza o PowerShell [Syslog][], uma solução de registo onipresente.

### <a name="filesystem"></a>Sistema de ficheiros

Foram feitas várias alterações no macOS e Linux para dar suporte a caracteres de nome de ficheiro não tradicionalmente suportados no Windows:

- Caminhos para cmdlets são agora barra agnóstico (tanto / e \ profissional como separador de diretório)
- Especificação de diretório de Base de XDG é agora respeitada e utilizada por predefinição:
  - O caminho de perfil do Linux/macOS está localizado em `~/.config/powershell/profile.ps1`
  - O histórico de caminho para guardar está localizado em `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`
  - O caminho do módulo de utilizador está localizado em `~/.local/share/powershell/Modules`
- Suporte para nomes de arquivo e pasta que contém o caráter de vírgula no Unix. (#4959)
- Suporte para nomes de script ou caminhos completos com vírgulas. (#4136) (Graças à [ @TimCurwick ](https://github.com/TimCurwick)!)
- Detetar quando `-LiteralPath` é utilizado para suprimir a expansão de caráter universal para cmdlets de navegação. (#5038)
- Atualizado `Get-ChildItem` trabalhar o mais semelhante a * nix `ls -R` e o Windows `DIR /S` comandos nativos.
  `Get-ChildItem` Agora, retorna as ligações simbólicas durante uma pesquisa recursiva e não a pesquisar os diretórios que destino essas ligações. (#3780)

### <a name="case-sensitivity"></a>Maiúsculas e minúsculas

Linux e macOS tendem a ser diferencia maiúsculas de minúsculas, embora Windows diferencia maiúsculas de minúsculas, preservando a caso.
Em geral, o PowerShell diferencia maiúsculas de minúsculas.

Por exemplo, as variáveis de ambiente são maiúsculas e minúsculas no macOS e Linux, pelo que a maiúsculas/minúsculas do `PSModulePath` variável de ambiente foi padronizada. (#3255) `Import-Module` diferencia maiúsculas de minúsculas, quando está a utilizar um caminho de ficheiro para determinar o nome do módulo. (#5097)

## <a name="support-for-side-by-side-installations"></a>Suporte para instalações lado a lado

O PowerShell Core é instalado, configurado e executado separadamente a partir do Windows PowerShell.
O PowerShell Core tem um pacote ZIP "portátil".
Utilizar o pacote ZIP, pode instalar qualquer número de versões em qualquer lugar no disco, incluindo o local a uma aplicação que utiliza o PowerShell como uma dependência.
Instalação lado a lado torna mais fácil testar novas versões do PowerShell e scripts existentes de migração ao longo do tempo.
Lado a lado também habilita com versões anteriores compatibilidade como scripts podem ser afixados para versões específicas que necessitam.

> [!NOTE]
> Por padrão, o instalador baseado em MSI do Windows faz uma instalação de atualização no local.
>

## <a name="renamed-powershellexe-to-pwshexe"></a>Mudar o nome `powershell(.exe)` para `pwsh(.exe)`

O nome do binário para o PowerShell Core foi alterado de `powershell(.exe)` para `pwsh(.exe)`.
Esta alteração fornece uma forma determinista para os utilizadores executarem o PowerShell Core em máquinas para oferecer suporte a side-by-side Windows PowerShell e as instalações do PowerShell Core.
`pwsh` Também é muito menor e mais fácil digitar.

Alterações adicionais aos `pwsh(.exe)` partir `powershell.exe`:

- Foi alterado o parâmetro posicional primeiro partir `-Command` para `-File`.
  Esta alteração corrige a utilização de `#!` (também conhecido como como um shebang) nos scripts do PowerShell que estão a ser executados a partir de shells de não-PowerShell em plataformas não Windows.
  Isso também significa que pode executar comandos como `pwsh foo.ps1` ou `pwsh fooScript` sem especificar `-File`.
  No entanto, esta alteração requer que especifique explicitamente `-c` ou `-Command` ao tentar executar comandos como `pwsh.exe -Command Get-Command`. (#4019)
- O PowerShell Core aceita a `-i` (ou `-Interactive`) comutador para indicar uma shell interativa. (#3558) Isso permite que o PowerShell ser utilizado como um shell predefinida em plataformas Unix.
- Remover parâmetros `-importsystemmodules` e `-psconsoleFile` partir `pwsh.exe`. (#4995)
- Alterado `pwsh -version` e a ajuda interna para `pwsh.exe` para alinhar com outras ferramentas nativas. (#4958 & #4931) (Obrigado [ @iSazonov ](https://github.com/iSazonov))
- Mensagens de erro de argumento inválido para `-File` e `-Command` e códigos consistentes com as normas de Unix de saída (#4573)
- Adicionado `-WindowStyle` parâmetro no Windows. (#4573) Da mesma forma, as atualizações de instalações baseadas em pacote em plataformas não Windows são atualizações no local.

## <a name="backwards-compatibility-with-windows-powershell"></a>Com versões anteriores a compatibilidade com o Windows PowerShell

O objetivo do PowerShell Core é permanecer como compatível possível com o Windows PowerShell.
Utiliza o PowerShell Core [.NET Standard][] 2.0 para fornecer a compatibilidade binária com assemblies do .NET existentes.
Muitos módulos do PowerShell dependem desses assemblies (normalmente a horas de DLLs), para que o .NET Standard permite-lhes continuar a trabalhar com .NET Core.
O PowerShell Core também inclui uma heurística para procurar pastas bem conhecidas, como em que a Global Assembly Cache normalmente reside no disco, para encontrar as dependências de DLL do .NET Framework.

Pode saber mais sobre o .NET Standard na [Blog do .NET][], neste [YouTube][] e vídeo, por isso [PERGUNTAS FREQUENTES][] no GitHub.

Foram efetuados melhores esforços para garantir que os módulos do PowerShell de idioma e "incorporado" (como `Microsoft.PowerShell.Management`, `Microsoft.PowerShell.Utility`, etc.) funcionam da mesma forma que no Windows PowerShell.
Em muitos casos, com a ajuda da Comunidade, adicionámos novas funcionalidades e correções de erros para esses cmdlets.
Em alguns casos, devido a uma dependência em falta nas camadas subjacentes do .NET, a funcionalidade foi removida ou não está disponível.

A maioria dos módulos que são fornecidos como parte do Windows (por exemplo, `DnsClient`, `Hyper-V`, `NetTCPIP`, `Storage`, etc.) e outros produtos da Microsoft, incluindo Azure e Office não foram *explicitamente* transportado para o. Ainda NET Core.
A equipe do PowerShell está a funcionar com essas equipes e grupos de produtos, para validar e os módulos existentes para o PowerShell Core de porta.
Com o .NET Standard e [CDXML][], muitos destes módulos tradicionais do Windows PowerShell parece funcionar no PowerShell Core, mas eles não foram formalmente validados e formalmente não são suportados.

Ao instalar o [ `WindowsPSModulePath` ] [ windowspsmodulepath] módulo, pode utilizar módulos do Windows PowerShell ao acrescentar o Windows PowerShell `PSModulePath` para o PowerShell Core `PSModulePath`.

Primeiro, instale o `WindowsPSModulePath` módulo a partir da galeria do PowerShell:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Depois de instalar este módulo, execute o `Add-WindowsPSModulePath` cmdlet para adicionar o Windows PowerShell `PSModulePath` para o PowerShell Core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="docker-support"></a>Suporte do docker

O PowerShell Core adiciona suporte para contentores do Docker para todas as plataformas principais, que fornecemos suporte (incluindo várias distribuições Linux, Windows Server Core e o servidor Nano).

Para obter uma lista completa, visite as etiquetas no [ `microsoft/powershell` no Docker Hub][docker-hub].
Para obter mais informações sobre o Docker e o PowerShell Core, consulte [Docker][] no GitHub.

## <a name="ssh-based-powershell-remoting"></a>Comunicação remota do PowerShell baseado no SSH

O protocolo de comunicação remota do PowerShell (PSRP) agora funciona com o protocolo Secure Shell (SSH), além do tradicional PSRP com base em WinRM.

Isso significa que pode utilizar os cmdlets, como `Enter-PSSession` e `New-PSSession` e autenticar através de SSH.
Tudo o que precisa fazer é registrar o PowerShell como um subsistema com um servidor SSH com base em OpenSSH, e pode usar sua existente baseado no SSH autenticar mecanismos (como as palavras-passe ou chaves privadas) com o tradicional `PSSession` semântica.

Para obter mais informações sobre como configurar e utilizar a comunicação remota baseado no SSH, veja [comunicação remota do PowerShell através de SSH][ssh-remoting].

## <a name="default-encoding-is-utf-8-without-a-bom-except-for-new-modulemanifest"></a>Codificação padrão é UTF-8, sem uma BOM, exceto para New-ModuleManifest

No passado, como o Windows PowerShell cmdlets `Get-Content`, `Set-Content` utilizado codificações diferentes, como ASCII e UTF-16.
A variação nos padrões de codificação criava problemas ao misturar cmdlets sem especificar uma codificação.

Plataformas não Windows tradicionalmente usam UTF-8 sem uma marca de ordem de Byte (LM) como a codificação predefinida para ficheiros de texto.
Mais aplicações do Windows e ferramentas estão a migrar para fora do UTF-16 e em direção à codificação sem BOM UTF-8.
O PowerShell Core altera a codificação predefinida a estar em conformidade com a ecossistema mais abrangente.

Isso significa que todos os cmdlets incorporados que utilizam o `-Encoding` uso do parâmetro a `UTF8NoBOM` valor por predefinição.
Os seguintes cmdlets são afetados por esta alteração:

- Adicionar-conteúdo
- Export-Clixml
- Export-Csv
- Export-PSSession
- Format-Hex
- Get-Content
- Import-Csv
- Out-File
- SELECT-String
- Enviar-MailMessage
- Set-Content

Estes cmdlets também foram atualizados para que o `-Encoding` parâmetro universalmente aceita `System.Text.Encoding`.

O valor predefinido de `$OutputEncoding` também foi alterado para UTF-8.

Como melhor prática, deve definir explicitamente codificações em scripts usando o `-Encoding` parâmetro para produzir o comportamento determinístico entre plataformas.

`New-ModuleManifest` cmdlet não tiver **Encoding** parâmetro. A codificação do ficheiro de manifesto (. psd1) módulo criado com `New-ModuleManifest` cmdlet depende do ambiente: se é o PowerShell Core em execução no Linux, em seguida, a codificação UTF-8 (não BOM); caso contrário, a codificação é UTF-16 (com BOM). (#3940)

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>Suportar backgrounding dos pipelines com "e" comercial (`&`) (#3360)

Colocando `&` no final de um pipeline faz com que o pipeline ser executado como um trabalho do PowerShell.
Quando um pipeline é backgrounded, é devolvido um objeto de tarefa.
Assim que o pipeline está em execução como uma tarefa, todos do padrão `*-Job` cmdlets podem ser utilizados para gerir a tarefa.
Variáveis (ignorando variáveis específicas de processo) usadas no pipeline são copiadas automaticamente para a tarefa tão `Copy-Item $foo $bar &` simplesmente funciona.
Também é executada a tarefa no diretório atual em vez do diretório raiz do utilizador.
Para obter mais informações sobre tarefas do PowerShell, consulte [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs).

## <a name="semantic-versioning"></a>Controle de versão semântica

- Feitas `SemanticVersion` compatível com `SemVer 2.0`. (#5037) (Obrigado [ @iSazonov ](https://github.com/iSazonov)!)
- Alterar a predefinição `ModuleVersion` no `New-ModuleManifest` para `0.0.1` para alinhar com SemVer. (#4842) (Obrigado [ @LDSpits ](https://github.com/LDSpits))
- Adicionado `semver` como um acelerador de tipo para `System.Management.Automation.SemanticVersion`. (#4142) (Graças à [ @oising ](https://github.com/oising)!)
- Ativada a comparação entre um `SemanticVersion` instância e um `Version` instância construída apenas com `Major` e `Minor` valores de versão.

## <a name="language-updates"></a>Atualizações de idioma

- Implemente o escape de Unicode, análise, para que os utilizadores podem utilizar carateres Unicode como argumentos, cadeias de caracteres ou nomes de variáveis. (#3958) (Graças à [ @rkeithhill ](https://github.com/rkeithhill)!)
- Caráter de escape novos foram adicionados para ESC: `` `e``
- Foi adicionado suporte para a conversão de enums para (#4318) de cadeias de caracteres (obrigado [ @KirkMunro ](https://github.com/KirkMunro))
- Matriz de elemento único de conversão fixo para uma coleção genérica. (#3170)
- Sobrecarga de intervalo de carateres foi adicionado para o `..` operador, por isso, `'a'..'z'` devolve os carateres de "a" a "z". (#5026) (Obrigado [ @IISResetMe ](https://github.com/IISResetMe)!)
- Atribuição de variáveis fixa para não substituir variáveis só de leitura
- Push locais das variáveis automáticas para 'DottedScopes' quando dotting cmdlets de script (#4709)
- Ativar a utilização da opção "Linha única, Multiline" no operador de divisão (#4721) (obrigado [ @iSazonov ](https://github.com/iSazonov))

## <a name="engine-updates"></a>Atualizações de mecanismos

- `$PSVersionTable` tem quatro novas propriedades:
  - `PSEdition`: Este é definido como `Core` no PowerShell Core e `Desktop` no Windows PowerShell
  - `GitCommitId`: Este é o ID de consolidação de Git da ramificação Git ou etiqueta em que o PowerShell foi criado.
    Nas compilações de lançamento, provavelmente será o mesmo que `PSVersion`.
  - `OS`: Este é uma cadeia de caracteres de versão do SO devolvida pelo `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription`
  - `Platform`: Este é devolvido pelo `[System.Environment]::OSVersion.Platform` está definido como `Win32NT` no Windows, `Unix` no macOS, e `Unix` no Linux.
- Removida a `BuildVersion` propriedade de `$PSVersionTable`.
  Esta propriedade foi fortemente ligada para a versão de compilação do Windows.
  Em vez disso, recomendamos que utilize `GitCommitId` para obter a versão de compilação exata do PowerShell Core. (#3877) (Graças à [ @iSazonov ](https://github.com/iSazonov)!)
- Remova `ClrVersion` propriedade de `$PSVersionTable`.
  Esta propriedade é irrelevante para .NET Core e apenas mantida no .NET Core para fins específicos de legado que são não aplicáveis ao PowerShell.
- Adicionadas três novas variáveis automáticas para determinar se o PowerShell está em execução num determinado sistema operacional: `$IsWindows`, `$IsMacOs`, e `$IsLinux`.
- Adicionar `GitCommitId` a faixa de PowerShell Core.
  Agora, não precisa executar `$PSVersionTable` assim que inicie o PowerShell para obter a versão! (#3916) (Graças à [ @iSazonov ](https://github.com/iSazonov)!)
- Adicione um arquivo de configuração JSON chamado `powershell.config.json` no `$PSHome` para armazenar algumas definições necessárias antes de tempo de inicialização (por exemplo, `ExecutionPolicy`).
- Não bloquear o pipeline durante a execução do Windows EXE
- Ativado enumeração de coleções de COM. (#4553)

## <a name="cmdlet-updates"></a>Atualizações do cmdlet

### <a name="new-cmdlets"></a>Novos cmdlets

- Adicione `Get-Uptime` para `Microsoft.PowerShell.Utility`.
- Adicionar `Remove-Alias` comando. (#5143) (Obrigado [ @PowershellNinja ](https://github.com/PowershellNinja)!)
- Adicionar `Remove-Service` ao módulo de gestão. (#4858) (Obrigado [ @joandrsn ](https://github.com/joandrsn)!)

### <a name="web-cmdlets"></a>Cmdlets de Web

- Adicione suporte de autenticação de certificado para cmdlets de web. (#4646) (Obrigado [ @markekraus ](https://github.com/markekraus))
- Adicione suporte para cabeçalhos de conteúdo aos cmdlets de web. (#4494 & #4640) (Obrigado [ @markekraus ](https://github.com/markekraus))
- Adicione suporte a vários cabeçalho ligação aos Cmdlets de Web. (#5265) (Obrigado [ @markekraus ](https://github.com/markekraus)!)
- Suporte de paginação de cabeçalho de ligação nos cmdlets de web (#3828)
  - Para `Invoke-WebRequest`, quando a resposta inclui um cabeçalho de ligação, criamos uma propriedade de RelationLink como um dicionário que representa os URLs e `rel` atributos e certifique-se de que os URLs são absolutos para torná-lo mais fácil para o desenvolvedor a utilizar.
  - Para `Invoke-RestMethod`, quando a resposta inclui um cabeçalho de ligação expomos um `-FollowRelLink` comutador automaticamente seguir `next` `rel` ligações até que eles já não existem ou uma vez atingir o opcional `-MaximumFollowRelLink` valor do parâmetro.
- Adicionar `-CustomMethod` parâmetro aos cmdlets de web para permitir verbos de método não padrão. (#3142) (Graças à [ @Lee303 ](https://github.com/Lee303)!)
- Adicionar `SslProtocol` oferecer suporte aos Cmdlets de Web. (#5329) (Obrigado [ @markekraus ](https://github.com/markekraus)!)
- Adicionar Multipart suporte aos cmdlets de web. (#4782) (Obrigado [ @markekraus ](https://github.com/markekraus))
- Adicionar `-NoProxy` aos cmdlets de web, para que eles ignorem a definição de proxy de todo o sistema. (#3447) (Graças à [ @TheFlyingCorpse ](https://github.com/TheFlyingCorpse)!)
- Agente de utilizador de Cmdlets do Web relatórios agora a plataforma de SO (#4937) (obrigado [ @LDSpits ](https://github.com/LDSpits))
- Adicionar `-SkipHeaderValidation` mudar para cmdlets de web para suportar a adição de cabeçalhos sem validar o valor do cabeçalho. (#4085)
- Ative web cmdlets não valide o certificado HTTPS do servidor, se necessário.
- Adicione parâmetros de autenticação aos cmdlets de web. (#5052) (Obrigado [ @markekraus ](https://github.com/markekraus))
  - Adicionar `-Authentication` que fornece três opções: básico, OAuth e portador.
  - Adicionar `-Token` para obter o portador token OAuth e portador opções.
  - Adicionar `-AllowUnencryptedAuthentication` para ignorar a autenticação que é fornecida para qualquer esquema de transporte que não seja HTTPS.
- Adicione `-ResponseHeadersVariable` para `Invoke-RestMethod` para ativar a captura de cabeçalhos de resposta. (#4888) (Obrigado [ @markekraus ](https://github.com/markekraus))
- Corrija os cmdlets de web para incluir a resposta HTTP da exceção, quando o código de estado de resposta não é um sucesso. (#3201)
- Alterar web cmdlets `UserAgent` partir `WindowsPowerShell` para `PowerShell`. (#4914) (Obrigado [ @markekraus ](https://github.com/markekraus))
- Adicionar explícita `ContentType` detecção de `Invoke-RestMethod` (#4692)
- Corrigir web cmdlets `-SkipHeaderValidation` para trabalhar com cabeçalhos de agente do usuário não padrão. (#4479 & #4512) (Obrigado [ @markekraus ](https://github.com/markekraus))

### <a name="json-cmdlets"></a>Cmdlets JSON

- Adicione `-AsHashtable` para `ConvertFrom-Json` para devolver uma `Hashtable` em vez disso. (#5043) (Obrigado [ @bergmeister ](https://github.com/bergmeister)!)
- Utilizar o formatador mais bonito com `ConvertTo-Json` saída. (#2787) (Graças a @kittholland!)
- Adicione `Jobject` suporte de serialização para `ConvertTo-Json`. (#5141)
- Corrigir `ConvertFrom-Json` para anular a serialização de uma matriz de cadeias de caracteres do pipeline que juntos construir uma cadeia de caracteres do JSON completa.
  Isso resolve alguns casos em que garantidamente destruiria a análise de JSON. (#3823)
- Remover os `AliasProperty "Count"` definidos para `System.Array`.
  Esta ação remove o estranhas `Count` propriedade em algumas `ConvertFrom-Json` saída. (#3231) (Graças à [ @PetSerAl ](https://github.com/PetSerAl)!)

### <a name="csv-cmdlets"></a>Cmdlets CSV

- Adicione `PSTypeName` suporte para `Import-Csv` e `ConvertFrom-Csv`. (#5389) (Obrigado [ @markekraus ](https://github.com/markekraus)!)
- Tornar `Import-Csv` suportar `CR`, `LF`, e `CRLF` como delimitadores de linha. (#5363) (Obrigado [ @iSazonov ](https://github.com/iSazonov)!)
- Tornar `-NoTypeInformation` a predefinição no `Export-Csv` e `ConvertTo-Csv`. (#5164) (Obrigado [ @markekraus ](https://github.com/markekraus))

### <a name="service-cmdlets"></a>Cmdlets de serviço

- Adicionar propriedades `UserName`, `Description`, `DelayedAutoStart`, `BinaryPathName`, e `StartupType` para o `ServiceController` objectos devolvidos pelo `Get-Service`. (#4907) (Obrigado [ @joandrsn ](https://github.com/joandrsn))
- Adicionar a funcionalidade para definir credenciais no `Set-Service` comando. (#4844) (Obrigado [ @joandrsn ](https://github.com/joandrsn))

### <a name="other-cmdlets"></a>Outros cmdlets

- Adicionar um parâmetro para `Get-ChildItem` chamado `-FollowSymlink` que atravessa links simbólicos sob demanda, com verificações de loops de ligação. (#4020)
- Atualização `Add-Type` para suportar `CSharpVersion7`. (#3933) (Graças à [ @iSazonov ](https://github.com/iSazonov))
- Remover o `Microsoft.PowerShell.LocalAccounts` módulo devido à utilização de APIs não suportadas até que seja encontrada uma solução melhor. (#4302)
- Remover os `*-Counter` cmdlets no `Microsoft.PowerShell.Diagnostics` devido à utilização de APIs não suportadas até que seja encontrada uma solução melhor. (#4303)
- Adicionar suporte para `Invoke-Item -Path <folder>`. (#4262)
- Adicione `-Extension` e `-LeafBase` muda para `Split-Path` para que pode dividir caminhos entre a extensão de nome de ficheiro e o restante do nome de ficheiro. (#2721) (Graças à [ @powercode ](https://github.com/powercode)!)
- Adicionar parâmetros `-Top` e `-Bottom` para `Sort-Object` de ordenação de superiores/inferiores N
- Expor o processo pai de um processo adicionando a `CodeProperty "Parent"` para `System.Diagnostics.Process`. (#2850) (Graças à [ @powercode ](https://github.com/powercode)!)
- Utilizar MB em vez de KB para colunas de memória de `Get-Process`
- Adicione `-NoNewLine` mudar para `Out-String`. (#5056) (Obrigado [ @raghav710 ](https://github.com/raghav710))
- `Move-Item` cmdlet honra `-Include`, `-Exclude`, e `-Filter` parâmetros. (#3878)
- Permitir `*` a ser utilizado no caminho de registo para `Remove-Item`. (#4866)
- Adicione `-Title` para `Get-Credential` e unificar a experiência de linha de comandos entre plataformas.
- Adicionar a `-TimeOut` parâmetro `Test-Connection`. (#2492)
- `Get-AuthenticodeSignature` cmdlets agora pode obter timestamp de assinatura de ficheiro. (#4061)
- Remover não suportado `-ShowWindow` mudar da `Get-Help`. (#4903)
- Corrigir `Get-Content -Delimiter` para não incluir o delimitador a elementos da matriz retornada (#3706) (obrigado [ @mklement0 ](https://github.com/mklement0))
- Adicione `Meta`, `Charset`, e `Transitional` parâmetros `ConvertTo-HTML` (#4184) (obrigado [ @ergo3114 ](https://github.com/ergo3114))
- Adicione `WindowsUBR` e `WindowsVersion` as propriedades para `Get-ComputerInfo` resultado
- Adicionar `-Group` parâmetro `Get-Verb`
- Adicione `ShouldProcess` suporte para `New-FileCatalog` e `Test-FileCatalog` (correções `-WhatIf` e `-Confirm`). (#3074) (Graças à [ @iSazonov ](https://github.com/iSazonov)!)
- Adicione `-WhatIf` mude para `Start-Process` cmdlet (#4735) (obrigado [ @sarithsutha ](https://github.com/sarithsutha))
- Adicionar `ValidateNotNullOrEmpty` demasiados parâmetros existentes.

## <a name="tab-completion"></a>Conclusão de tabulação

- Melhorada a inferência de tipos na conclusão de tabulação, com base nos valores de variáveis do tempo de execução. (#2744) (Graças à [ @powercode ](https://github.com/powercode)!) Isto permite a conclusão de tabulação em situações como:

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- Adicionar tabela hash conclusão de tabulação para `-Property` de `Select-Object`. (#3625) (Graças à [ @powercode ](https://github.com/powercode))
- Permitir Preenchimento automático argumento para `-ExcludeProperty` e `-ExpandProperty` de `Select-Object`. (#3443) (Graças à [ @iSazonov ](https://github.com/iSazonov)!)
- Corrigir um erro na conclusão de tabulação para tornar `native.exe --<tab>` chamada nativa adicionada a conclusão. (#3633) (Graças à [ @powercode ](https://github.com/powercode)!)

## <a name="breaking-changes"></a>Alterações recentes

Introduzimos um número de alterações significativas feitas no PowerShell Core 6.0.
Para ler mais sobre os mesmos em detalhes, consulte [alterações significativas no PowerShell Core 6.0][breaking-changes].

## <a name="debugging"></a>Depuração

- Suporte para depuração step-in remota para `Invoke-Command -ComputerName`. (#3015)
- Ativar a depuração de associador iniciar sessão no PowerShell Core

## <a name="filesystem-updates"></a>Atualizações do sistema de ficheiros

- Ative a utilização do fornecedor de sistema de ficheiros num caminho UNC. (US $4998)
- `Split-Path` agora funciona com raízes UNC
- `cd` sem argumentos agora se comporta como `cd ~`
- Foi corrigido o PowerShell Core para permitir o uso de caminhos que são mais de 260 carateres de comprimento. (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>Correções de erros e melhorias de desempenho

Fizemos *muitos* melhorias de desempenho em PowerShell, incluindo no tempo de inicialização, vários cmdlets incorporados e interação com binários nativos.

Corrigimos também um número de bugs no PowerShell Core.
Para obter uma lista completa de correções e alterações, confira nossos [registo de alterações][] no GitHub.

## <a name="telemetry"></a>Telemetria

- Telemetria de núcleo 6.0 adicionada do PowerShell para o host de console para o relatório dois valores (#3620):
  - a plataforma de SO (`$PSVersionTable.OSDescription`)
  - a versão exata do PowerShell (`$PSVersionTable.GitCommitId`)

Se quiser por cancelar esta telemetria, simplesmente crie `POWERSHELL_TELEMETRY_OPTOUT` variável de ambiente com um dos seguintes valores: `true`, `1` ou `yes`.
Criar a variável ignora a toda a telemetria até mesmo antes de primeira execução do PowerShell.
Também planejamos expor esses dados de telemetria e as informações que podemos notar a partir da telemetria no [dashboard de Comunidade][community-dashboard].
Pode encontrar mais informações sobre como utilizamos esses dados desta [mensagem de blogue][telemetry-blog].

[github]: https://github.com/PowerShell/PowerShell
[.NET core 2.0]: https://docs.microsoft.com/dotnet/core/
[.NET standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[os_log]: https://developer.apple.com/documentation/os/logging
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[breaking-changes]: breaking-changes-ps6.md
[registo de alterações]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[telemetry-blog]: https://blogs.msdn.microsoft.com/powershell/2017/01/31/powershell-open-source-community-dashboard/
[.NET standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[Blog do .NET]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
[PERGUNTAS FREQUENTES]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[CDXML]: https://msdn.microsoft.com/library/jj542525(v=vs.85).aspx
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
