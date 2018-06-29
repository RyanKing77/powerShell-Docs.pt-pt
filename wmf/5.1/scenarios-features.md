---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Novos cenários e funcionalidades no WMF 5.1
ms.openlocfilehash: b00069aad7422f86d1462a62a6c4bc8a91e46705
ms.sourcegitcommit: 50b66cada6943784b8d3c103cebc3c1e3e286a16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/28/2018
ms.locfileid: "37090368"
---
# <a name="new-scenarios-and-features-in-wmf-51"></a><span data-ttu-id="d4daf-103">Novos cenários e funcionalidades no WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="d4daf-103">New Scenarios and Features in WMF 5.1</span></span>

> <span data-ttu-id="d4daf-104">Nota: Estas informações são preliminares e estão sujeitos a alterações.</span><span class="sxs-lookup"><span data-stu-id="d4daf-104">Note: This information is preliminary and subject to change.</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="d4daf-105">Edições do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d4daf-105">PowerShell Editions</span></span>

<span data-ttu-id="d4daf-106">Começando na versão 5.1, o PowerShell está disponível nas diferentes edições que denotam conjuntos de funcionalidade e compatibilidade de plataforma variados.</span><span class="sxs-lookup"><span data-stu-id="d4daf-106">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="d4daf-107">**Edição Desktop:** incorporada no .NET Framework e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço total do Windows, tais como Server Core e o Ambiente de trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="d4daf-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="d4daf-108">**Edição Core:** incorporada no .NET Core e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço reduzido do Windows, tais como Servidor Nano e o IoT do Windows.</span><span class="sxs-lookup"><span data-stu-id="d4daf-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="d4daf-109">**Saiba mais sobre como utilizar as edições do PowerShell**</span><span class="sxs-lookup"><span data-stu-id="d4daf-109">**Learn more about using PowerShell Editions**</span></span>

- [<span data-ttu-id="d4daf-110">Determinar a edição em execução do PowerShell com $PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="d4daf-110">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="d4daf-111">Filtrar os resultados de Get-Module pelos CompatiblePSEditions utilizando o parâmetro PSEdition</span><span class="sxs-lookup"><span data-stu-id="d4daf-111">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="d4daf-112">Impedir a execução do script, exceto se executar uma edição compatíveis do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d4daf-112">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="d4daf-113">Declarar a compatibilidade com um módulo versões específicas do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d4daf-113">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/gallery/concepts/module-psedition-support)

## <a name="catalog-cmdlets"></a><span data-ttu-id="d4daf-114">Cmdlets de catálogo</span><span class="sxs-lookup"><span data-stu-id="d4daf-114">Catalog Cmdlets</span></span>

<span data-ttu-id="d4daf-115">Foram adicionados dois novos cmdlets no [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) módulo; estas gerar e validar os ficheiros de catálogo do Windows.</span><span class="sxs-lookup"><span data-stu-id="d4daf-115">Two new cmdlets have been added in the [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) module; these generate and validate Windows catalog files.</span></span>

### <a name="new-filecatalog"></a><span data-ttu-id="d4daf-116">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="d4daf-116">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="d4daf-117">Novo FileCatalog cria um ficheiro de catálogo do Windows para o conjunto de ficheiros e pastas.</span><span class="sxs-lookup"><span data-stu-id="d4daf-117">New-FileCatalog creates a Windows catalog file for set of folders and files.</span></span>
<span data-ttu-id="d4daf-118">Este ficheiro de catálogo contém hashes para todos os ficheiros em caminhos especificados.</span><span class="sxs-lookup"><span data-stu-id="d4daf-118">This catalog file contains hashes for all files in specified paths.</span></span>
<span data-ttu-id="d4daf-119">Os utilizadores possam distribuir o conjunto de pastas, juntamente com o ficheiro de catálogo correspondente que representa essas pastas.</span><span class="sxs-lookup"><span data-stu-id="d4daf-119">Users can distribute the set of folders along with corresponding catalog file representing those folders.</span></span>
<span data-ttu-id="d4daf-120">Estas informações são úteis para validar se todas as alterações foram efetuadas às pastas desde a hora de criação do catálogo.</span><span class="sxs-lookup"><span data-stu-id="d4daf-120">This information is useful to validate whether any changes have been made to the folders since catalog creation time.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="d4daf-121">São suportadas versões do catálogo 1 e 2.</span><span class="sxs-lookup"><span data-stu-id="d4daf-121">Catalog versions 1 and 2 are supported.</span></span>
<span data-ttu-id="d4daf-122">Versão 1 utiliza o algoritmo de hash SHA1 para criar os hashes de ficheiro; versão 2 utiliza SHA256.</span><span class="sxs-lookup"><span data-stu-id="d4daf-122">Version 1 uses the SHA1 hashing algorithm to create file hashes; version 2 uses SHA256.</span></span>
<span data-ttu-id="d4daf-123">Versão 2 do catálogo não é suportada em *Windows Server 2008 R2* ou *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="d4daf-123">Catalog version 2 is not supported on *Windows Server 2008 R2* or *Windows 7*.</span></span>
<span data-ttu-id="d4daf-124">Deve utilizar a versão 2 do catálogo em *Windows 8*, *Windows Server 2012*e sistemas operativos posteriores.</span><span class="sxs-lookup"><span data-stu-id="d4daf-124">You should use catalog version 2 on *Windows 8*, *Windows Server 2012*, and later operating systems.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="d4daf-125">Esta ação cria o ficheiro de catálogo.</span><span class="sxs-lookup"><span data-stu-id="d4daf-125">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="d4daf-126">Para verificar a integridade dos ficheiros de catálogo (Pester.cat no acima exemplo), inicie sessão com [conjunto AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d4daf-126">To verify the integrity of catalog file (Pester.cat in above example), sign it using [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) cmdlet.</span></span>

### <a name="test-filecatalog"></a><span data-ttu-id="d4daf-127">Teste FileCatalog</span><span class="sxs-lookup"><span data-stu-id="d4daf-127">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="d4daf-128">Teste FileCatalog valida o catálogo que representa um conjunto de pastas.</span><span class="sxs-lookup"><span data-stu-id="d4daf-128">Test-FileCatalog validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="d4daf-129">Este cmdlet compara todos os hashes de ficheiros e os respetivos caminhos relativos encontrado na *catálogo* com aqueles no *disco*.</span><span class="sxs-lookup"><span data-stu-id="d4daf-129">This cmdlet compares all the files hashes and their relative paths found in *catalog* with ones on *disk*.</span></span>
<span data-ttu-id="d4daf-130">Se detetar qualquer erro de correspondência entre os hashes de ficheiros e caminhos devolve o estado como *ValidationFailed*.</span><span class="sxs-lookup"><span data-stu-id="d4daf-130">If it detects any mismatch between file hashes and paths it returns the status as *ValidationFailed*.</span></span>
<span data-ttu-id="d4daf-131">Os utilizadores podem obter todos os estas informações ao utilizar o *-detalhadas* parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d4daf-131">Users can retrieve all this information by using the *-Detailed* parameter.</span></span>
<span data-ttu-id="d4daf-132">Também apresenta assinatura estado do catálogo no *assinatura* propriedade que é equivalente a chamar [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) cmdlet no ficheiro de catálogo.</span><span class="sxs-lookup"><span data-stu-id="d4daf-132">It also displays signing status of catalog in *Signature* property which is equivalent to calling [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) cmdlet on the catalog file.</span></span>
<span data-ttu-id="d4daf-133">Os utilizadores também podem ignorar qualquer ficheiro durante a validação utilizando o *- FilesToSkip* parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d4daf-133">Users can also skip any file during validation by using the *-FilesToSkip* parameter.</span></span>

## <a name="module-analysis-cache"></a><span data-ttu-id="d4daf-134">Cache de análise do módulo</span><span class="sxs-lookup"><span data-stu-id="d4daf-134">Module Analysis Cache</span></span>

<span data-ttu-id="d4daf-135">A partir do WMF 5.1, PowerShell fornece controlo sobre o ficheiro que é utilizado para sobre um módulo, tal como os comandos que exporta os dados em cache.</span><span class="sxs-lookup"><span data-stu-id="d4daf-135">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="d4daf-136">Por predefinição, esta cache é armazenado no ficheiro `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="d4daf-136">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="d4daf-137">A cache, ao procurar um comando, normalmente é lido no arranque e é escrito num thread em segundo plano algum tempo depois de um módulo é importado.</span><span class="sxs-lookup"><span data-stu-id="d4daf-137">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="d4daf-138">Para alterar a localização predefinida da cache, defina o `$env:PSModuleAnalysisCachePath` variável de ambiente antes de iniciar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d4daf-138">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span>
<span data-ttu-id="d4daf-139">As alterações a esta variável de ambiente só afetarão processos subordinados.</span><span class="sxs-lookup"><span data-stu-id="d4daf-139">Changes to this environment variable will only affect children processes.</span></span>
<span data-ttu-id="d4daf-140">O valor deve nome um caminho completo (incluindo filename) PowerShell tem permissão para criar e escrever em ficheiros.</span><span class="sxs-lookup"><span data-stu-id="d4daf-140">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span>
<span data-ttu-id="d4daf-141">Para desativar a cache de ficheiros, defina este valor para uma localização inválida, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d4daf-141">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="d4daf-142">Define o caminho para um dispositivo inválido.</span><span class="sxs-lookup"><span data-stu-id="d4daf-142">This sets the path to an invalid device.</span></span>
<span data-ttu-id="d4daf-143">Se o PowerShell não é possível escrever o caminho, não é devolvido nenhum erro, mas pode ver através da utilização de uma análise do relatório de erros:</span><span class="sxs-lookup"><span data-stu-id="d4daf-143">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="d4daf-144">Ao escrever a saída da cache, o PowerShell irá verificar para módulos que já não existem para evitar uma cache desnecessariamente grande.</span><span class="sxs-lookup"><span data-stu-id="d4daf-144">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span>
<span data-ttu-id="d4daf-145">Por vezes, estas verificações não são desejável, caso em que pode desativá-los através da definição:</span><span class="sxs-lookup"><span data-stu-id="d4daf-145">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="d4daf-146">A definição desta variável de ambiente entrarão em vigor imediatamente no processo atual.</span><span class="sxs-lookup"><span data-stu-id="d4daf-146">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="d4daf-147">Especificar a versão do módulo</span><span class="sxs-lookup"><span data-stu-id="d4daf-147">Specifying module version</span></span>

<span data-ttu-id="d4daf-148">No WMF 5.1, `using module` comporta-se da mesma forma que outras construções relacionados com o módulo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d4daf-148">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="d4daf-149">Anteriormente, era necessário uma forma para especificar uma versão do módulo específico; Se existirem várias versões presentes, este resultou num erro.</span><span class="sxs-lookup"><span data-stu-id="d4daf-149">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="d4daf-150">No WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="d4daf-150">In WMF 5.1:</span></span>

- <span data-ttu-id="d4daf-151">Pode utilizar [ModuleSpecification construtor (tabela hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="d4daf-151">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
<span data-ttu-id="d4daf-152">Esta tabela hash tem o mesmo formato que `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="d4daf-152">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

<span data-ttu-id="d4daf-153">**Exemplo:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="d4daf-153">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="d4daf-154">Se existirem várias versões do módulo, PowerShell utiliza o **mesma lógica resolução** como `Import-Module` e não devolve um erro - o mesmo comportamento de `Import-Module` e `Import-DscResource`.</span><span class="sxs-lookup"><span data-stu-id="d4daf-154">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="d4daf-155">Melhoramentos à Pester</span><span class="sxs-lookup"><span data-stu-id="d4daf-155">Improvements to Pester</span></span>

<span data-ttu-id="d4daf-156">No WMF 5.1, a versão do Pester que é fornecido com o PowerShell foi atualizada de 3.3.5 para 3.4.0, com a adição de consolidação https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, que permite uma maior comportamento para Pester no servidor de nano for apresentado.</span><span class="sxs-lookup"><span data-stu-id="d4daf-156">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0, with the addition of commit https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, which enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="d4daf-157">Pode rever as alterações em versões 3.3.5 para 3.4.0 ao inspecionar o ficheiro de ChangeLog.md em: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span><span class="sxs-lookup"><span data-stu-id="d4daf-157">You can review the changes in versions 3.3.5 to 3.4.0 by inspecting the ChangeLog.md file at: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span></span>
