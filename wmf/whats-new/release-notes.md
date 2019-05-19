---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Notas de versão do WMF 5.x
ms.openlocfilehash: 8bdc423234cf0b104b72b1bee1de35e50783d8a4
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856400"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a><span data-ttu-id="45aed-103">Notas de versão do Windows Management Framework (WMF) 5.x</span><span class="sxs-lookup"><span data-stu-id="45aed-103">Windows Management Framework (WMF) 5.x Release Notes</span></span>

## <a name="wmf-50-changes"></a><span data-ttu-id="45aed-104">Altera o WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="45aed-104">WMF 5.0 Changes</span></span>

- <span data-ttu-id="45aed-105">PowerShell 5.0 adiciona um novo estruturado **informações** stream</span><span class="sxs-lookup"><span data-stu-id="45aed-105">PowerShell 5.0 adds a new structured **Information** stream</span></span>
- <span data-ttu-id="45aed-106">Melhorias do DSC, incluindo quatro novos recursos de DSC:</span><span class="sxs-lookup"><span data-stu-id="45aed-106">Improvements to DSC including four new DSC resources:</span></span>
  - <span data-ttu-id="45aed-107">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="45aed-107">WindowsFeatureSet</span></span>
  - <span data-ttu-id="45aed-108">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="45aed-108">WindowsOptionalFeatureSet</span></span>
  - <span data-ttu-id="45aed-109">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="45aed-109">ServiceSet</span></span>
  - <span data-ttu-id="45aed-110">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="45aed-110">ProcessSet</span></span>
- <span data-ttu-id="45aed-111">Foi adicionado a administração apenas suficiente para ativar a administração baseada em funções por meio de comunicação remota do PowerShell</span><span class="sxs-lookup"><span data-stu-id="45aed-111">Added Just Enough Administration to enable role-based administration through PowerShell remoting</span></span>
- <span data-ttu-id="45aed-112">PowerShell 5.0 estende a linguagem para incluir classes definidas pelo utilizador e enumerações</span><span class="sxs-lookup"><span data-stu-id="45aed-112">PowerShell 5.0 extends the language to include user-defined classes and enumerations</span></span>
- <span data-ttu-id="45aed-113">Recursos do ISE do PowerShell e a depuração remota foi adicionado de depuração aprimorada</span><span class="sxs-lookup"><span data-stu-id="45aed-113">Improved debugging features in PowerShell ISE and added remote debugging</span></span>
- <span data-ttu-id="45aed-114">Adicionados os módulos do PowerShellGet e PackageManagement</span><span class="sxs-lookup"><span data-stu-id="45aed-114">Added the PowerShellGet and PackageManagement modules</span></span>
- <span data-ttu-id="45aed-115">O registo melhorado do script de PowerShell e transcrições</span><span class="sxs-lookup"><span data-stu-id="45aed-115">Enhanced PowerShell script logging and transcripts</span></span>
- <span data-ttu-id="45aed-116">Adição de cmdlets de sintaxe de mensagem criptográfica</span><span class="sxs-lookup"><span data-stu-id="45aed-116">Add Cryptographic Message Syntax cmdlets</span></span>
- <span data-ttu-id="45aed-117">WMF 5.0 inclui o módulo de NetworkSwitchManager para Windows</span><span class="sxs-lookup"><span data-stu-id="45aed-117">WMF 5.0 includes the NetworkSwitchManager module for Windows</span></span>
- <span data-ttu-id="45aed-118">Adicionado o módulo de Microsoft.PowerShell.ODataUtils</span><span class="sxs-lookup"><span data-stu-id="45aed-118">Added the Microsoft.PowerShell.ODataUtils module</span></span>
- <span data-ttu-id="45aed-119">Foi adicionado suporte para Software de registo de inventário (SIL)</span><span class="sxs-lookup"><span data-stu-id="45aed-119">Added support for Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="45aed-120">Novo servidor ou ao atualizar cmdlets em resposta a pedidos de utilizador e problemas</span><span class="sxs-lookup"><span data-stu-id="45aed-120">Sever new or update cmdlets in response to user requests and issues</span></span>

## <a name="wmf-51-changes"></a><span data-ttu-id="45aed-121">Alterações do WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="45aed-121">WMF 5.1 Changes</span></span>

<span data-ttu-id="45aed-122">WMF 5.1 inclui os componentes PowerShell, WMI, WinRM e registo de inventário de Software (SIL) que foram lançados com o Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="45aed-122">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span> <span data-ttu-id="45aed-123">WMF 5.1 pode ser instalado no Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 e 2012 R2 e fornece vários melhoramentos relativamente WMF 5.0 incluindo:</span><span class="sxs-lookup"><span data-stu-id="45aed-123">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides several improvements over WMF 5.0 including:</span></span>

- <span data-ttu-id="45aed-124">Novos cmdlets</span><span class="sxs-lookup"><span data-stu-id="45aed-124">New cmdlets</span></span>
- <span data-ttu-id="45aed-125">Melhorias do PowerShellGet com a imposição de módulos assinados e a instalação de módulos JEA</span><span class="sxs-lookup"><span data-stu-id="45aed-125">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="45aed-126">Adicionado suporte ao PackageManagement para Contentores, Configuração CBS, configuração com base em EXE, pacotes CAB</span><span class="sxs-lookup"><span data-stu-id="45aed-126">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="45aed-127">Melhorias na depuração para classes DSC e PowerShell</span><span class="sxs-lookup"><span data-stu-id="45aed-127">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="45aed-128">Melhorias de segurança, incluindo a imposição de módulos assinados de catálogo provenientes do Servidor de Solicitação e ao utilizar os cmdlets PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="45aed-128">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="45aed-129">Respostas a vários pedidos e problemas de utilizadores</span><span class="sxs-lookup"><span data-stu-id="45aed-129">Responses to a number of user requests and issues</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="45aed-130">Edições do PowerShell</span><span class="sxs-lookup"><span data-stu-id="45aed-130">PowerShell Editions</span></span>

<span data-ttu-id="45aed-131">A partir da versão 5.1, o PowerShell está disponível nas diferentes edições que denotam conjuntos diferentes de recursos e compatibilidade de plataforma.</span><span class="sxs-lookup"><span data-stu-id="45aed-131">Starting with version 5.1, PowerShell is available in different editions that denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="45aed-132">**Edição Desktop:** Criado no .NET Framework e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço total do Windows como núcleo de servidor e Desktop do Windows.</span><span class="sxs-lookup"><span data-stu-id="45aed-132">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="45aed-133">**Edição Core:** Incorporada no .NET Core e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço reduzido do Windows, como o servidor Nano e o Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="45aed-133">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="learn-more-about-using-powershell-editions"></a><span data-ttu-id="45aed-134">Saiba mais sobre como utilizar as edições do PowerShell</span><span class="sxs-lookup"><span data-stu-id="45aed-134">Learn more about using PowerShell Editions</span></span>

- [<span data-ttu-id="45aed-135">Determinar a edição em execução do PowerShell com $PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="45aed-135">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="45aed-136">Filtrar os resultados de Get-Module por CompatiblePSEditions utilizando o parâmetro PSEdition</span><span class="sxs-lookup"><span data-stu-id="45aed-136">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="45aed-137">Impedir a execução do script, a menos que execute numa edição compatível do PowerShell</span><span class="sxs-lookup"><span data-stu-id="45aed-137">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="45aed-138">Declarar a compatibilidade de um módulo para versões específicas do PowerShell</span><span class="sxs-lookup"><span data-stu-id="45aed-138">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a><span data-ttu-id="45aed-139">Cache de análise de módulo</span><span class="sxs-lookup"><span data-stu-id="45aed-139">Module Analysis Cache</span></span>

<span data-ttu-id="45aed-140">A partir do WMF 5.1, o PowerShell fornece controlo sobre o ficheiro que é utilizado para sobre um módulo, tal como os comandos que exporta os dados em cache.</span><span class="sxs-lookup"><span data-stu-id="45aed-140">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="45aed-141">Por predefinição, esta cache é armazenado no arquivo `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="45aed-141">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="45aed-142">A cache, durante a pesquisa por um comando, normalmente é lidos na inicialização e é escrita num thread em segundo plano algum tempo, após a importação de um módulo.</span><span class="sxs-lookup"><span data-stu-id="45aed-142">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="45aed-143">Para alterar a localização predefinida da cache, defina o `$env:PSModuleAnalysisCachePath` variável de ambiente antes de iniciar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45aed-143">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="45aed-144">As alterações a esta variável de ambiente só afetarão a processos filhos.</span><span class="sxs-lookup"><span data-stu-id="45aed-144">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="45aed-145">O valor deve atribuir um nome um caminho completo (incluindo filename) que o PowerShell tem permissão para criar e escrever ficheiros.</span><span class="sxs-lookup"><span data-stu-id="45aed-145">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="45aed-146">Para desativar a cache de ficheiros, defina este valor para uma localização inválida, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="45aed-146">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="45aed-147">Isso define o caminho para um dispositivo inválido.</span><span class="sxs-lookup"><span data-stu-id="45aed-147">This sets the path to an invalid device.</span></span> <span data-ttu-id="45aed-148">Se o PowerShell não é possível escrever para o caminho, não é devolvido nenhum erro, mas pode ver o relatório através de uma análise de erros:</span><span class="sxs-lookup"><span data-stu-id="45aed-148">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="45aed-149">Quando o gravar o cache, o PowerShell irá verificar para módulos que não existem mais para evitar uma cache de grande desnecessariamente.</span><span class="sxs-lookup"><span data-stu-id="45aed-149">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="45aed-150">Por vezes, essas verificações não são desejáveis, caso em que pode desativá-las através da definição:</span><span class="sxs-lookup"><span data-stu-id="45aed-150">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="45aed-151">A definição desta variável de ambiente entrarão em vigor imediatamente no processo atual.</span><span class="sxs-lookup"><span data-stu-id="45aed-151">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="45aed-152">Especificar a versão do módulo</span><span class="sxs-lookup"><span data-stu-id="45aed-152">Specifying module version</span></span>

<span data-ttu-id="45aed-153">No WMF 5.1, `using module` se comporta da mesma forma que outras construções relacionados com o módulo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45aed-153">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="45aed-154">Anteriormente, tinha que há como especificar uma versão do módulo específico; Se existirem várias versões de presentes, isso resultou num erro.</span><span class="sxs-lookup"><span data-stu-id="45aed-154">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="45aed-155">No WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="45aed-155">In WMF 5.1:</span></span>

- <span data-ttu-id="45aed-156">Pode usar [ModuleSpecification construtor (tabela de hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="45aed-156">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
  <span data-ttu-id="45aed-157">Esta tabela de hash tem o mesmo formato que `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="45aed-157">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

  <span data-ttu-id="45aed-158">**Exemplo:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="45aed-158">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="45aed-159">Se existirem várias versões do módulo, PowerShell utiliza a **mesma lógica de resolução** como `Import-Module` e não retorna um erro - o mesmo comportamento `Import-Module` e `Import-DscResource`.</span><span class="sxs-lookup"><span data-stu-id="45aed-159">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="45aed-160">Melhorias à Pester</span><span class="sxs-lookup"><span data-stu-id="45aed-160">Improvements to Pester</span></span>

<span data-ttu-id="45aed-161">No WMF 5.1, a versão do Pester que é fornecido com o PowerShell foi atualizada de 3.3.5 para 3.4.0.</span><span class="sxs-lookup"><span data-stu-id="45aed-161">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0.</span></span>
<span data-ttu-id="45aed-162">Esta atualização permite que o melhor comportamento para Pester no servidor Nano.</span><span class="sxs-lookup"><span data-stu-id="45aed-162">This update enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="45aed-163">Pode rever as alterações no pestes inspecionando o [registo de alterações](https://github.com/pester/Pester/blob/master/CHANGELOG.md) no repositório do GitHub.</span><span class="sxs-lookup"><span data-stu-id="45aed-163">You can review the changes in Pest by inspecting the [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) in the GitHub repository.</span></span>
