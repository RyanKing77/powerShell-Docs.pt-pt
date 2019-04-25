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
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="fd1df-103">Quais são as novidades no PowerShell Core 6.2</span><span class="sxs-lookup"><span data-stu-id="fd1df-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="fd1df-104">A versão do PowerShell Core 6.2 se concentrou em melhorias de desempenho, correções de erros e melhorias de cmdlet e idioma menores que melhoram a qualidade.</span><span class="sxs-lookup"><span data-stu-id="fd1df-104">The PowerShell Core 6.2 release focused on performance improvements, bug fixes, and smaller cmdlet and language enhancements that improve the quality.</span></span> <span data-ttu-id="fd1df-105">Para ver uma lista completa das melhorias, confira nossas [changelogs](https://github.com/PowerShell/PowerShell/releases) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="fd1df-105">To see a full list of improvements, check out our detailed [changelogs](https://github.com/PowerShell/PowerShell/releases) on GitHub.</span></span>

## <a name="experimental-features"></a><span data-ttu-id="fd1df-106">Funcionalidades experimentais</span><span class="sxs-lookup"><span data-stu-id="fd1df-106">Experimental Features</span></span>

<span data-ttu-id="fd1df-107">Anteriormente, o suporte para nós habilitamos [funcionalidades experimentais][].</span><span class="sxs-lookup"><span data-stu-id="fd1df-107">Previously, we enabled support for [Experimental Features][].</span></span> <span data-ttu-id="fd1df-108">Na versão 6.2, temos quatro funcionalidades experimentais para experimentar. Envie comentários, de modo que melhoramos e decidir se o recurso é aconselhável promover para o status de base.</span><span class="sxs-lookup"><span data-stu-id="fd1df-108">In the 6.2 release, we have four experimental features to try out. Please provide feedback so we can make improvements and to decide whether the feature is worth promoting to mainstream status.</span></span>

<span data-ttu-id="fd1df-109">Utilize `Get-ExperimentalFeature` para obter uma lista das funcionalidades experimentais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="fd1df-109">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="fd1df-110">Pode ativar ou desativar estas funcionalidades com `Enable-ExperimentalFeature` e `Disable-ExperimentalFeature`.</span><span class="sxs-lookup"><span data-stu-id="fd1df-110">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

### <a name="command-not-found-suggestions"></a><span data-ttu-id="fd1df-111">Comando não foi encontrado sugestões</span><span class="sxs-lookup"><span data-stu-id="fd1df-111">Command Not Found Suggestions</span></span>

<span data-ttu-id="fd1df-112">Esse recurso usa correspondência difusa para encontrar sugestões para comandos ou os cmdlets, que pode ter escrito incorretamente.</span><span class="sxs-lookup"><span data-stu-id="fd1df-112">This feature uses fuzzy matching to find suggestions for commands or cmdlets you may have mistyped.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a><span data-ttu-id="fd1df-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fd1df-113">Example</span></span>

<span data-ttu-id="fd1df-114">Neste exemplo, o nome do cmdlet com erros ortográficos é difusa correspondido a várias sugestões de maior probabilidade de, pelo menos, provavelmente.</span><span class="sxs-lookup"><span data-stu-id="fd1df-114">In this example, the misspelled cmdlet name is fuzzy matched to several suggestions from most likely to least likely.</span></span>

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

### <a name="implicit-remoting-batching"></a><span data-ttu-id="fd1df-115">A criação de batches de comunicação remota implícita</span><span class="sxs-lookup"><span data-stu-id="fd1df-115">Implicit Remoting Batching</span></span>

<span data-ttu-id="fd1df-116">Ao usar [comunicação remota implícita](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) num pipeline, PowerShell trata cada comando no pipeline de forma independente.</span><span class="sxs-lookup"><span data-stu-id="fd1df-116">When using [implicit remoting](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) in a pipeline, PowerShell treats each command in the pipeline independently.</span></span> <span data-ttu-id="fd1df-117">Os objetos são serializados repetidamente e `de-serialized` entre o cliente e o sistema remoto sobre a execução do pipeline.</span><span class="sxs-lookup"><span data-stu-id="fd1df-117">Objects are repeatedly serialized and `de-serialized` between the client and remote system over the execution of the pipeline.</span></span>

<span data-ttu-id="fd1df-118">Com esta funcionalidade, o PowerShell analisa o pipeline para determinar se o comando é seguro executar e existe no sistema de destino.</span><span class="sxs-lookup"><span data-stu-id="fd1df-118">With this feature, PowerShell analyzes the pipeline to determine if the command is safe to run and it exists on the target system.</span></span> <span data-ttu-id="fd1df-119">Quando verdadeiro, o PowerShell executa todo o pipeline remotamente e apenas serializa e `de-serializes` os resultados de volta para o cliente.</span><span class="sxs-lookup"><span data-stu-id="fd1df-119">When true, PowerShell executes the entire pipeline remotely and only serializes and `de-serializes` the results back to the client.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

<span data-ttu-id="fd1df-120">Um teste reais `Get-Process | Sort-Object` ao longo do localhost diminui de 10 a 15 segundos para 20 a 30 **milissegundos**.</span><span class="sxs-lookup"><span data-stu-id="fd1df-120">A real-world test of `Get-Process | Sort-Object` over localhost decreases from 10-15 seconds to 20-30 **milliseconds**.</span></span> <span data-ttu-id="fd1df-121">A funcionalidade apenas precisa de ser ativada no cliente.</span><span class="sxs-lookup"><span data-stu-id="fd1df-121">The feature only needs to be enabled on the client.</span></span> <span data-ttu-id="fd1df-122">Sem alterações são necessárias no servidor.</span><span class="sxs-lookup"><span data-stu-id="fd1df-122">No changes are required on the server.</span></span>

### <a name="temp-drive"></a><span data-ttu-id="fd1df-123">Temp Drive</span><span class="sxs-lookup"><span data-stu-id="fd1df-123">Temp Drive</span></span>

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

<span data-ttu-id="fd1df-124">Se estiver a utilizar o PowerShell Core nos sistemas operativos diferentes, descobrirá que a variável de ambiente para localizar o diretório temporário é diferente no Windows, macOS e Linux!</span><span class="sxs-lookup"><span data-stu-id="fd1df-124">If you're using PowerShell Core on different operating systems, you'll discover that the environment variable for finding the temporary directory is different on Windows, macOS, and Linux!</span></span> <span data-ttu-id="fd1df-125">Com esta funcionalidade, tem um [PSDrive][] chamado `Temp:` que é automaticamente mapeado para a pasta temporária para o sistema operativo que está a utilizar.</span><span class="sxs-lookup"><span data-stu-id="fd1df-125">With this feature, you get a [PSDrive][] called `Temp:` that is automatically mapped to the temporary folder for the operating system you are using.</span></span>

#### <a name="example"></a><span data-ttu-id="fd1df-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fd1df-126">Example</span></span>

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> `Get-Content` Temp:/hello.txt
Hello World!
```

<span data-ttu-id="fd1df-127">Tenha em atenção que comandos nativos de ficheiros (como `ls` no Linux) não estão cientes PSDrives e não verá isto `Temp:` unidade.</span><span class="sxs-lookup"><span data-stu-id="fd1df-127">Be aware that native file commands (like `ls` on Linux) are not aware of PSDrives and won't see this `Temp:` drive.</span></span>

### <a name="abbreviation-expansion"></a><span data-ttu-id="fd1df-128">Expansão de abreviatura</span><span class="sxs-lookup"><span data-stu-id="fd1df-128">Abbreviation Expansion</span></span>

<span data-ttu-id="fd1df-129">Cmdlets do PowerShell devem ter nomes descritivos.</span><span class="sxs-lookup"><span data-stu-id="fd1df-129">PowerShell cmdlets are expected to have descriptive nouns.</span></span> <span data-ttu-id="fd1df-130">Isso resulta em nomes longos que são mais difíceis de tipo.</span><span class="sxs-lookup"><span data-stu-id="fd1df-130">This results in long names that are more difficult to type.</span></span> <span data-ttu-id="fd1df-131">Esta funcionalidade permite-lhe apenas escrever os carateres em maiúsculas do cmdlet e usar a conclusão de tabulação para encontrar uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="fd1df-131">This feature allows you to just type the uppercase characters of the cmdlet and use tab-completion to find a match.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a><span data-ttu-id="fd1df-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fd1df-132">Example</span></span>

```powershell
PS> i-arsavsf
```

<span data-ttu-id="fd1df-133">Se pressionar tab e o Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) módulo instalado, este irá autocompletar para:</span><span class="sxs-lookup"><span data-stu-id="fd1df-133">If you hit tab, and have the Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) module installed, it will autocomplete to:</span></span>

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> <span data-ttu-id="fd1df-134">Esta funcionalidade destina-se para ser usado interativamente.</span><span class="sxs-lookup"><span data-stu-id="fd1df-134">This feature is intended to be used interactively.</span></span> <span data-ttu-id="fd1df-135">Não não possível executar a formas abreviadas dos cmdlets.</span><span class="sxs-lookup"><span data-stu-id="fd1df-135">Abbreviated forms of cmdlets can't be executed.</span></span>
> <span data-ttu-id="fd1df-136">Esta funcionalidade não é um substituto para aliases.</span><span class="sxs-lookup"><span data-stu-id="fd1df-136">This feature is not a replacement for aliases.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="fd1df-137">Alterações Interruptivas</span><span class="sxs-lookup"><span data-stu-id="fd1df-137">Breaking Changes</span></span>

- <span data-ttu-id="fd1df-138">Corrigir `-NoEnumerate` comportamento no `Write-Output` para ser consistente com o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fd1df-138">Fix `-NoEnumerate` behavior in `Write-Output` to be consistent with Windows PowerShell.</span></span> <span data-ttu-id="fd1df-139">(#9069)</span><span class="sxs-lookup"><span data-stu-id="fd1df-139">(#9069)</span></span>
- <span data-ttu-id="fd1df-140">Tornar `Join-String -InputObject 1,2,3` resultar igual a `1,2,3 | Join-String` resultar (#8611) (obrigado @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-140">Make `Join-String -InputObject 1,2,3` result equal to `1,2,3 | Join-String` result (#8611) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="fd1df-141">Adicione `-Stable` para `Sort-Object` e relacionadas a testes (#7862) (obrigado @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-141">Add `-Stable` to `Sort-Object` and related tests (#7862) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="fd1df-142">Melhorar `Start-Sleep` cmdlet para aceitar segundos fracionais (#8537) (obrigado @Prototyyppi!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-142">Improve `Start-Sleep` cmdlet to accept fractional seconds (#8537) (Thanks @Prototyyppi!)</span></span>
- <span data-ttu-id="fd1df-143">Alterar a tabela de hash para utilizar OrdinalIgnoreCase ser `case-insensitive` em todas as culturas (#8566)</span><span class="sxs-lookup"><span data-stu-id="fd1df-143">Change hashtable to use OrdinalIgnoreCase to be `case-insensitive` in all Cultures (#8566)</span></span>
- <span data-ttu-id="fd1df-144">Corrigir **LiteralPath** na `Import-Csv` vincular à `Get-ChildItem` (#8277) de saída (obrigado @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-144">Fix **LiteralPath** in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="fd1df-145">Já não ignora uma coluna sem nome se o delimitador de aspas duplas for utilizado numa `Import-Csv` (#7899) (obrigado @Topping!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-145">No longer skips a column without name if double quote delimiter is used in `Import-Csv` (#7899) (Thanks @Topping!)</span></span>
- <span data-ttu-id="fd1df-146">`Get-ExperimentalFeature` não tem mais `-ListAvailable` mudar (#8318)</span><span class="sxs-lookup"><span data-stu-id="fd1df-146">`Get-ExperimentalFeature` no longer has `-ListAvailable` switch (#8318)</span></span>
- <span data-ttu-id="fd1df-147">Depurar o parâmetro agora conjuntos `$DebugPreference` para **continuar** em vez de **Inquire** (#8195) (obrigado @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-147">Debug parameter now sets `$DebugPreference` to **Continue** instead of **Inquire** (#8195) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="fd1df-148">Honra `-OutputFormat` se for especificado no comando não interativa, redirecionado, codificado, utilizado com pwsh (#8115)</span><span class="sxs-lookup"><span data-stu-id="fd1df-148">Honor `-OutputFormat` if specified in non-interactive, redirected, encoded command used with pwsh (#8115)</span></span>
- <span data-ttu-id="fd1df-149">Carregar a assemblagem do caminho de base do módulo antes de tentar carregar a partir do GAC (#8073)</span><span class="sxs-lookup"><span data-stu-id="fd1df-149">Load assembly from module base path before trying to load from the GAC (#8073)</span></span>
- <span data-ttu-id="fd1df-150">Remover til de pacotes de pré-visualização do Linux (#8244)</span><span class="sxs-lookup"><span data-stu-id="fd1df-150">Remove tilde from Linux preview packages (#8244)</span></span>
- <span data-ttu-id="fd1df-151">Mover o processamento de `-WorkingDirectory` antes do processamento de perfis (#8079)</span><span class="sxs-lookup"><span data-stu-id="fd1df-151">Move processing of `-WorkingDirectory` before processing of profiles (#8079)</span></span>
- <span data-ttu-id="fd1df-152">Não adicione `PATHEXT` variável de ambiente Unix (#7697) (obrigado @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-152">Do not add `PATHEXT` environment variable on Unix (#7697) (Thanks @iSazonov!)</span></span>

## <a name="known-issues"></a><span data-ttu-id="fd1df-153">Problemas Conhecidos</span><span class="sxs-lookup"><span data-stu-id="fd1df-153">Known Issues</span></span>

- <span data-ttu-id="fd1df-154">Comunicação remota em plataformas Windows IOT ARM tem um problema ao carregar módulos.</span><span class="sxs-lookup"><span data-stu-id="fd1df-154">Remoting on Windows IOT ARM platforms has an issue loading modules.</span></span> <span data-ttu-id="fd1df-155">Consulte o (n. º 8053)</span><span class="sxs-lookup"><span data-stu-id="fd1df-155">See (#8053)</span></span>

## <a name="general-updates-and-fixes"></a><span data-ttu-id="fd1df-156">Geral atualizações e correções</span><span class="sxs-lookup"><span data-stu-id="fd1df-156">General Updates and Fixes</span></span>

- <span data-ttu-id="fd1df-157">Ativar a conclusão de tabulação de maiúsculas e minúsculas para ficheiros e pastas no sistema de ficheiros de maiúsculas e minúsculas (#8128)</span><span class="sxs-lookup"><span data-stu-id="fd1df-157">Enable case-insensitive tab completion for files and folders on case-sensitive filesystem (#8128)</span></span>
- <span data-ttu-id="fd1df-158">Tornar PSVersionInfo.PSVersion e PSVersionInfo.PSEdition pública (#8054) (obrigado @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-158">Make PSVersionInfo.PSVersion and PSVersionInfo.PSEdition public (#8054) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="fd1df-159">Adicionar a inferência de tipo para `$_`  /  `$PSItem` no `catch{ }` bloqueia (#8020) (obrigado @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-159">Add Type Inference for `$_` / `$PSItem` in `catch{ }` blocks (#8020) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="fd1df-160">Corrigir a inferência de tipo de invocação de método estático (#8018) (obrigado @SeeminglyScience!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-160">Fix static method invocation type inference (#8018) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="fd1df-161">Criar tipos de inferido para `Select-Object`, `Group-Object`, **PSObject** e **Hashtable** (#7231) (obrigado @powercode!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-161">Create inferred types for `Select-Object`, `Group-Object`, **PSObject** and **Hashtable** (#7231) (Thanks @powercode!)</span></span>
- <span data-ttu-id="fd1df-162">Suporta o método de chamada com `ByRef-like` escreva parâmetros (#7721)</span><span class="sxs-lookup"><span data-stu-id="fd1df-162">Support calling method with `ByRef-like` type parameters (#7721)</span></span>
- <span data-ttu-id="fd1df-163">Administrar o caso em que o caminho do módulo Windows PowerShell já está a ser PSModulePath o ambiente (#7727)</span><span class="sxs-lookup"><span data-stu-id="fd1df-163">Handle the case where the Windows PowerShell module path is already in the environment's PSModulePath (#7727)</span></span>
- <span data-ttu-id="fd1df-164">Ativar `SecureString` cmdlets para não-Windows-armazenando o texto simples (#9199)</span><span class="sxs-lookup"><span data-stu-id="fd1df-164">Enable `SecureString` cmdlets for non-Windows by storing the plain text (#9199)</span></span>
- <span data-ttu-id="fd1df-165">Melhorar a mensagem de erro não Windows, ao importar clixml com securestring (#7997)</span><span class="sxs-lookup"><span data-stu-id="fd1df-165">Improve error message on non-Windows when importing clixml with securestring (#7997)</span></span>
- <span data-ttu-id="fd1df-166">Adicionar parâmetro ReplyTo para `Send-MailMessage` (#8727) (obrigado @replicaJunction!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-166">Adding parameter ReplyTo to `Send-MailMessage` (#8727) (Thanks @replicaJunction!)</span></span>
- <span data-ttu-id="fd1df-167">Adicionar a mensagem obsoleta para `Send-MailMessage` (#9178)</span><span class="sxs-lookup"><span data-stu-id="fd1df-167">Add Obsolete message to `Send-MailMessage` (#9178)</span></span>
- <span data-ttu-id="fd1df-168">Corrigir `Restart-Computer` para trabalhar em `localhost` quando WinRM não está presente (#9160)</span><span class="sxs-lookup"><span data-stu-id="fd1df-168">Fix `Restart-Computer` to work on `localhost` when WinRM is not present (#9160)</span></span>
- <span data-ttu-id="fd1df-169">Tornar `Start-Job` gera erro de terminação, quando o PowerShell está a ser alojada (#9128)</span><span class="sxs-lookup"><span data-stu-id="fd1df-169">Make `Start-Job` throw terminating error when PowerShell is being hosted (#9128)</span></span>
- <span data-ttu-id="fd1df-170">Adicionar C# Aceleradores de tipo de estilo e sufixos para ushort, uint, ulong e literais curtos (#7813) (obrigado @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-170">Add C# style type accelerators and suffixes for ushort, uint, ulong, and short literals (#7813) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="fd1df-171">Foram adicionados sufixos de novo para literais numéricos - consulte [about_Numeric_Literals][] (#7901) (obrigado @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-171">Added new suffixes for numeric literals - see [about_Numeric_Literals][] (#7901) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="fd1df-172">Comunicar corretamente a nível de impacto quando SupportsShouldProcess não estiver definido como 'true' (#8209) (obrigado @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-172">Correctly Report impact level when SupportsShouldProcess is not set to 'true' (#8209) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="fd1df-173">Corrigir problemas de conjunto de carateres de pedido nos Cmdlets de Web (#8742) (obrigado @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-173">Fix Request Charset Issues in Web Cmdlets (#8742) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="fd1df-174">Corrigir Expect `100-continue` problema com os Cmdlets da Web (#8679) (obrigado @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-174">Fix Expect `100-continue` issue with Web Cmdlets (#8679) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="fd1df-175">Corrigir o problema de bloqueio de ficheiros com os cmdlets da web (#7676) (obrigado @Claustn!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-175">Fix file blocking issue with web cmdlets (#7676) (Thanks @Claustn!)</span></span>
- <span data-ttu-id="fd1df-176">Corrigir o problema de análise de página de código `Invoke-RestMethod` (#8694) (obrigado @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-176">Fix code page parsing issue in `Invoke-RestMethod` (#8694) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="fd1df-177">Refatorar `ConvertTo-Json` para expor JsonObject.ConvertToJson como uma API pública (#8682)</span><span class="sxs-lookup"><span data-stu-id="fd1df-177">Refactor `ConvertTo-Json` to expose JsonObject.ConvertToJson as a public API (#8682)</span></span>
- <span data-ttu-id="fd1df-178">Adicionar a profundidade máxima configurável no `ConvertFrom-Json` com - profundidade (#8199) (obrigado @louistio!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-178">Add configurable maximum depth in `ConvertFrom-Json` with -Depth (#8199) (Thanks @louistio!)</span></span>
- <span data-ttu-id="fd1df-179">Adicionar parâmetro EscapeHandling `ConvertTo-Json` cmdlet (#7775) (obrigado @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-179">Add EscapeHandling parameter in `ConvertTo-Json` cmdlet (#7775) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="fd1df-180">Adicione `-CustomPipeName` para pwsh e `Enter-PSHostProcess` (#8889)</span><span class="sxs-lookup"><span data-stu-id="fd1df-180">Add `-CustomPipeName` to pwsh and `Enter-PSHostProcess` (#8889)</span></span>
- <span data-ttu-id="fd1df-181">Ativar a criação de links simbólicos relativos no Windows com `New-Item` (#8783)</span><span class="sxs-lookup"><span data-stu-id="fd1df-181">Enable creating relative symbolic links on Windows with `New-Item` (#8783)</span></span>
- <span data-ttu-id="fd1df-182">Permitir que os utilizadores do Windows no modo de programador para criar links simbólicos sem elevação (#8534)</span><span class="sxs-lookup"><span data-stu-id="fd1df-182">Allow Windows users in developer mode to create symlinks without elevation (#8534)</span></span>
- <span data-ttu-id="fd1df-183">Ativar `Write-Information` para aceitar `$null` (#8774)</span><span class="sxs-lookup"><span data-stu-id="fd1df-183">Enable `Write-Information` to accept `$null` (#8774)</span></span>
- <span data-ttu-id="fd1df-184">Corrigir `Get-Help` para funções avançadas com MAML conteúdo de ajuda (#8353)</span><span class="sxs-lookup"><span data-stu-id="fd1df-184">Fix `Get-Help` for advanced functions with MAML help content (#8353)</span></span>
- <span data-ttu-id="fd1df-185">Corrigir `Get-Help` PSTypeName problema com o - parâmetro quando apenas um parâmetro é declarado (#8754) (obrigado @pougetat!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-185">Fix `Get-Help` PSTypeName issue with -Parameter when only one parameter is declared (#8754) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="fd1df-186">Correção de cálculo de token para `Get-Help` executado no ScriptBlock para obter ajuda de comentário.</span><span class="sxs-lookup"><span data-stu-id="fd1df-186">Token calculation fix for `Get-Help` executed on ScriptBlock for comment help.</span></span> <span data-ttu-id="fd1df-187">(#8238) (Obrigado @hubuk!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-187">(#8238) (Thanks @hubuk!)</span></span>
- <span data-ttu-id="fd1df-188">Alteração `Get-Help` cmdlet-parâmetro de parâmetro para que ele aceita a cadeia de caracteres matrizes (#8454) (obrigado @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-188">Change `Get-Help` cmdlet -Parameter parameter so it accepts string arrays (#8454) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="fd1df-189">Resolver PAGER se o caminho contiver espaços (#8571) (obrigado @pougetat!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-189">Resolve PAGER if its path contains spaces (#8571) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="fd1df-190">Adicionar linha para a utilização de `less` na função de ajuda para instruir o utilizador como sair (#7998)</span><span class="sxs-lookup"><span data-stu-id="fd1df-190">Add prompt to the use of `less` in the function 'help' to instruct user how to quit (#7998)</span></span>
- <span data-ttu-id="fd1df-191">Adicionar suporte para enum e char tipos na `Format-Hex` cmdlet (#8191) (obrigado @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-191">Add support enum and char types in `Format-Hex` cmdlet (#8191) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="fd1df-192">Remover ShouldProcess de `Format-Hex` (#8178)</span><span class="sxs-lookup"><span data-stu-id="fd1df-192">Remove ShouldProcess from `Format-Hex` (#8178)</span></span>
- <span data-ttu-id="fd1df-193">Adicione novos parâmetros de deslocamento e a contagem para `Format-Hex` e refatorar o cmdlet (#7877) (obrigado @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-193">Add new Offset and Count parameters to `Format-Hex` and refactor the cmdlet (#7877) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="fd1df-194">Permitir que "name" como uma chave de alias para "etiqueta" na `ConvertTo-Html`, a entrada 'width' ser um número inteiro de permissão (#8426) (obrigado @mklement0!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-194">Allow 'name' as an alias key for 'label' in `ConvertTo-Html`, allow the 'width' entry to be an integer (#8426) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="fd1df-195">Scriptblock marca com base calculada propriedades voltem a funcionar `ConvertTo-Html` (#8427) (obrigado @mklement0!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-195">Make scriptblock based calculated properties work again in `ConvertTo-Html` (#8427) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="fd1df-196">Adicionar o cmdlet `Join-String` para a criação de texto de entrada (#7660) do pipeline (obrigado @powercode!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-196">Add cmdlet `Join-String` for creating text from pipeline input (#7660) (Thanks @powercode!)</span></span>
- <span data-ttu-id="fd1df-197">Corrigir `Join-String` FormatString lógica de parâmetro de cmdlet (#8449) (obrigado @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-197">Fix `Join-String` cmdlet FormatString parameter logic (#8449) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="fd1df-198">Alteração `Clear-Host` a utilização da `$RAWUI` e desmarque para funcionar em comunicação remota (#8609)</span><span class="sxs-lookup"><span data-stu-id="fd1df-198">Change `Clear-Host` back to using `$RAWUI` and clear to work over remoting (#8609)</span></span>
- <span data-ttu-id="fd1df-199">Alteração `Clear-Host` simplesmente chamado `[console]::clear` e remover o alias clara do Unix (#8603)</span><span class="sxs-lookup"><span data-stu-id="fd1df-199">Change `Clear-Host` to simply called `[console]::clear` and remove clear alias from Unix (#8603)</span></span>
- <span data-ttu-id="fd1df-200">Corrigir LiteralPath na `Import-Csv` vincular à `Get-ChildItem` (#8277) de saída (obrigado @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-200">Fix LiteralPath in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="fd1df-201">função de ajuda não deve utilizar pager para AliasHelpInfo (#8552)</span><span class="sxs-lookup"><span data-stu-id="fd1df-201">help function shouldn't use pager for AliasHelpInfo (#8552)</span></span>
- <span data-ttu-id="fd1df-202">Adicione `-UseMinimalHeader` para `Start-Transcript` para minimizar o cabeçalho de transcrição (#8402) (obrigado @lukexjeremy!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-202">Add `-UseMinimalHeader` to `Start-Transcript` to minimize transcript header (#8402) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="fd1df-203">Adicione `Enable-ExperimentalFeature` e `Disable-ExperimentalFeature` cmdlets (#8318)</span><span class="sxs-lookup"><span data-stu-id="fd1df-203">Add `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature` cmdlets (#8318)</span></span>
- <span data-ttu-id="fd1df-204">Expor todos os cmdlets da **PSDiagnostics** se logman.exe estiver disponível (#8366)</span><span class="sxs-lookup"><span data-stu-id="fd1df-204">Expose all cmdlets from **PSDiagnostics** if logman.exe is available (#8366)</span></span>
- <span data-ttu-id="fd1df-205">Remover **Persist** parâmetro partir `New-PSDrive` no `non-Windows` plataforma (#8291) (obrigado @lukexjeremy!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-205">Remove **Persist** parameter from `New-PSDrive` on `non-Windows` platform (#8291) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="fd1df-206">Adicionar suporte para `cd +` (#7206) (obrigado @bergmeister!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-206">Add support for `cd +` (#7206) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="fd1df-207">Ativar `Set-Location -LiteralPath` para trabalhar com pastas com o nome - e + (#8089)</span><span class="sxs-lookup"><span data-stu-id="fd1df-207">Enable `Set-Location -LiteralPath` to work with folders named - and + (#8089)</span></span>
- <span data-ttu-id="fd1df-208">`Test-Path` Devolve `$false` quando dado vazio ou `$null` (#8080) de valor do caminho (obrigado @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-208">`Test-Path` returns `$false` when given an empty or `$null` path value (#8080) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="fd1df-209">Permitir que o parâmetro dinâmico a serem retornados, mesmo que o caminho não corresponde a qualquer fornecedor de serviços (#7957)</span><span class="sxs-lookup"><span data-stu-id="fd1df-209">Allow dynamic parameter to be returned even if path does not match any provider (#7957)</span></span>
- <span data-ttu-id="fd1df-210">Suporte `Get-PSHostProcessInfo` e `Enter-PSHostProcess` em plataformas Unix (#8232)</span><span class="sxs-lookup"><span data-stu-id="fd1df-210">Support `Get-PSHostProcessInfo` and `Enter-PSHostProcess` on Unix platforms (#8232)</span></span>
- <span data-ttu-id="fd1df-211">Reduzir as alocações no `Get-Content` cmdlet (#8103) (obrigado @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-211">Reduce allocations in `Get-Content` cmdlet (#8103) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="fd1df-212">Ativar `Add-Content` partilhar o acesso de leitura com outras ferramentas ao escrever o conteúdo (#8091)</span><span class="sxs-lookup"><span data-stu-id="fd1df-212">Enable `Add-Content` to share read access with other tools while writing content (#8091)</span></span>
- <span data-ttu-id="fd1df-213">`Get/Add-Content` gera o erro melhorado para criar aplicativos para um contentor (#7823) (obrigado @kvprasoon!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-213">`Get/Add-Content` throws improved error when targeting a container (#7823) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="fd1df-214">Adicione `-Name`, `-NoUserOverrides` e `-ListAvailable` parâmetros `Get-Culture` cmdlet (#7702) (obrigado @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-214">Add `-Name`, `-NoUserOverrides` and `-ListAvailable` parameters to `Get-Culture` cmdlet (#7702) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="fd1df-215">Adicionar atributo unificado para conclusão para **Encoding** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fd1df-215">Add unified attribute for completion for **Encoding** parameter.</span></span> <span data-ttu-id="fd1df-216">(#7732) (Obrigado @ThreeFive-O!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-216">(#7732) (Thanks @ThreeFive-O!)</span></span>
- <span data-ttu-id="fd1df-217">Permitir numérico Ids e nome de páginas de código registado num **Encoding** parâmetros (#7636) (obrigado @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-217">Allow numeric Ids and name of registered code pages in **Encoding** parameters (#7636) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="fd1df-218">Corrigir `Rename-Item -Path` com o caráter universal char (n. º 7398) (obrigado @kwkam!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-218">Fix `Rename-Item -Path` with wildcard char (#7398) (Thanks @kwkam!)</span></span>
- <span data-ttu-id="fd1df-219">Ao usar `Start-Transcript` e o ficheiro existe, vazio em vez disso, o ficheiro que a eliminar o (n. º 8131) (obrigado @paalbra!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-219">When using `Start-Transcript` and file exists, empty file rather than deleting (#8131) (Thanks @paalbra!)</span></span>
- <span data-ttu-id="fd1df-220">Tornar `Add-Type` abra arquivos de origem com **FileAccess.Read** e **Funkce** explicitamente (#7915) (obrigado @IISResetMe!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-220">Make `Add-Type` open source files with **FileAccess.Read** and **FileShare.Read** explicitly (#7915) (Thanks @IISResetMe!)</span></span>
- <span data-ttu-id="fd1df-221">Corrigir `Enter-PSSession -ContainerId` para o Windows mais recente (#7883)</span><span class="sxs-lookup"><span data-stu-id="fd1df-221">Fix `Enter-PSSession -ContainerId` for the latest Windows (#7883)</span></span>
- <span data-ttu-id="fd1df-222">Certifique-se **NestedModules** propriedade fica preenchida por `Test-ModuleManifest` (#7859)</span><span class="sxs-lookup"><span data-stu-id="fd1df-222">Ensure **NestedModules** property gets populated by `Test-ModuleManifest` (#7859)</span></span>
- <span data-ttu-id="fd1df-223">Adicione `%F` maiúsculas para `Get-Date` - UFormat (#7630) (obrigado @britishben!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-223">Add `%F` case to `Get-Date` -UFormat (#7630) (Thanks @britishben!)</span></span>
- <span data-ttu-id="fd1df-224">Corrigir `Set-Service -Status Stopped` para parar serviços com dependências (#5525) (obrigado @zhenggu!)</span><span class="sxs-lookup"><span data-stu-id="fd1df-224">Fix `Set-Service -Status Stopped` to stop services with dependencies (#5525) (Thanks @zhenggu!)</span></span>

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Funcionalidades experimentais]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
