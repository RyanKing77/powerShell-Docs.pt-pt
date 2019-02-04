---
ms.date: 11/06/2018
contributor: JKeithB
keywords: Galeria, powershell, cmdlet, psgallery, psget
title: Trabalhar com local PSRepositories
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688393"
---
# <a name="working-with-local-powershellget-repositories"></a><span data-ttu-id="774d6-103">Trabalhar com repositórios locais do PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="774d6-103">Working with local PowerShellGet Repositories</span></span>

<span data-ttu-id="774d6-104">Os repositórios suporte do módulo PowerShellGet que se diferente da galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="774d6-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="774d6-105">Estes cmdlets permitem os cenários seguintes:</span><span class="sxs-lookup"><span data-stu-id="774d6-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="774d6-106">Suporta um conjunto de módulos do PowerShell confiável e previamente validado para utilização no seu ambiente</span><span class="sxs-lookup"><span data-stu-id="774d6-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="774d6-107">Um pipeline de CI/CD que cria módulos do PowerShell ou scripts de teste</span><span class="sxs-lookup"><span data-stu-id="774d6-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="774d6-108">Fornecer scripts do PowerShell e módulos aos sistemas que não é possível aceder à internet</span><span class="sxs-lookup"><span data-stu-id="774d6-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>

<span data-ttu-id="774d6-109">Este artigo descreve como configurar um repositório local do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="774d6-109">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="774d6-110">O artigo também abrange o [OfflinePowerShellGetDeploy][] módulo disponível a partir da galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="774d6-110">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="774d6-111">Este módulo contém cmdlets para instalar a versão mais recente do PowerShellGet no seu repositório local.</span><span class="sxs-lookup"><span data-stu-id="774d6-111">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="774d6-112">Tipos de repositório local</span><span class="sxs-lookup"><span data-stu-id="774d6-112">Local repository types</span></span>

<span data-ttu-id="774d6-113">Existem duas formas de criar um PSRepository local: Partilha de servidor ou ficheiro de NuGet.</span><span class="sxs-lookup"><span data-stu-id="774d6-113">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="774d6-114">Cada tipo tem vantagens e desvantagens:</span><span class="sxs-lookup"><span data-stu-id="774d6-114">Each type has advantages and disadvantages:</span></span>

<span data-ttu-id="774d6-115">Servidor do NuGet</span><span class="sxs-lookup"><span data-stu-id="774d6-115">NuGet Server</span></span>

| <span data-ttu-id="774d6-116">Vantagens</span><span class="sxs-lookup"><span data-stu-id="774d6-116">Advantages</span></span>| <span data-ttu-id="774d6-117">Desvantagens</span><span class="sxs-lookup"><span data-stu-id="774d6-117">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="774d6-118">Estreitamente imita a funcionalidade de PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="774d6-118">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="774d6-119">Aplicação de várias camada requer planeamento de operações e suporte</span><span class="sxs-lookup"><span data-stu-id="774d6-119">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="774d6-120">NuGet integra-se com o Visual Studio, outras ferramentas</span><span class="sxs-lookup"><span data-stu-id="774d6-120">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="774d6-121">Modelo de autenticação e gestão de contas do NuGet necessário</span><span class="sxs-lookup"><span data-stu-id="774d6-121">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="774d6-122">NuGet oferece suporte a metadados em `.Nupkg` pacotes</span><span class="sxs-lookup"><span data-stu-id="774d6-122">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="774d6-123">A publicação requer gerenciamento de chave de API e manutenção</span><span class="sxs-lookup"><span data-stu-id="774d6-123">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="774d6-124">Fornece pesquisa, administração de pacote, etc.</span><span class="sxs-lookup"><span data-stu-id="774d6-124">Provides search, package administration, etc.</span></span> | |

<span data-ttu-id="774d6-125">Partilha de ficheiros</span><span class="sxs-lookup"><span data-stu-id="774d6-125">File Share</span></span>

| <span data-ttu-id="774d6-126">Vantagens</span><span class="sxs-lookup"><span data-stu-id="774d6-126">Advantages</span></span>| <span data-ttu-id="774d6-127">Desvantagens</span><span class="sxs-lookup"><span data-stu-id="774d6-127">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="774d6-128">Fácil de configurar, criar cópias de segurança e manter</span><span class="sxs-lookup"><span data-stu-id="774d6-128">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="774d6-129">Metadados usados pelo PowerShellGet não estão disponível</span><span class="sxs-lookup"><span data-stu-id="774d6-129">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="774d6-130">Modelo de segurança simples - permissões de utilizador na partilha</span><span class="sxs-lookup"><span data-stu-id="774d6-130">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="774d6-131">Nenhuma interface do Usuário para além da partilha de ficheiros básico</span><span class="sxs-lookup"><span data-stu-id="774d6-131">No UI beyond basic file share</span></span> |
| <span data-ttu-id="774d6-132">Sem restrições, como substituição de itens existentes</span><span class="sxs-lookup"><span data-stu-id="774d6-132">No constraints such as replacing existing items</span></span> | <span data-ttu-id="774d6-133">Segurança limitada e sem gravação de que atualiza o que</span><span class="sxs-lookup"><span data-stu-id="774d6-133">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="774d6-134">O PowerShellGet funciona com o tipo e suporta a localizar as versões e a instalação da dependência.</span><span class="sxs-lookup"><span data-stu-id="774d6-134">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="774d6-135">No entanto, algumas funcionalidades que funcionam para a galeria do PowerShell não estão disponíveis para servidores de bases NuGet ou partilhas de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="774d6-135">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="774d6-136">Tudo o que é um pacote - sem diferenciação de scripts, módulos, recursos de DSC ou funcionalidades de função.</span><span class="sxs-lookup"><span data-stu-id="774d6-136">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="774d6-137">Servidores de partilha de ficheiros não conseguem ver os metadados do pacote, incluindo etiquetas.</span><span class="sxs-lookup"><span data-stu-id="774d6-137">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="774d6-138">Criar um repositório local</span><span class="sxs-lookup"><span data-stu-id="774d6-138">Creating a local repository</span></span>

<span data-ttu-id="774d6-139">O artigo seguinte lista os passos para configurar o seu próprio servidor do NuGet.</span><span class="sxs-lookup"><span data-stu-id="774d6-139">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="774d6-140">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="774d6-140">[NuGet.Server][]</span></span>

<span data-ttu-id="774d6-141">Siga os passos até ao ponto da adição de pacotes.</span><span class="sxs-lookup"><span data-stu-id="774d6-141">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="774d6-142">Os passos para [publicando um pacote](#publishing-to-a-local-repository) serão abordadas mais adiante neste artigo.</span><span class="sxs-lookup"><span data-stu-id="774d6-142">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="774d6-143">Para um repositório baseadas em partilha de ficheiros, certifique-se de que os utilizadores têm permissões para aceder à partilha de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="774d6-143">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="774d6-144">Registar um repositório local</span><span class="sxs-lookup"><span data-stu-id="774d6-144">Registering a local repository</span></span>

<span data-ttu-id="774d6-145">Antes de um repositório pode ser utilizado, tem de ser registado com o `Register-PSRepository` comando.</span><span class="sxs-lookup"><span data-stu-id="774d6-145">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="774d6-146">Nos exemplos abaixo, o **InstallationPolicy** está definida como *fidedigna*, no pressuposto de que confia seu próprio repositório.</span><span class="sxs-lookup"><span data-stu-id="774d6-146">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="774d6-147">Tome nota da diferença entre a forma como os dois comandos processam **ScriptSourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="774d6-147">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="774d6-148">Para repositórios baseadas em partilha de ficheiros, o **SourceLocation** e **ScriptSourceLocation** tem de corresponder.</span><span class="sxs-lookup"><span data-stu-id="774d6-148">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="774d6-149">Para um repositório baseada na web, têm de ser diferentes, por isso, neste exemplo, à direita "/" é adicionado para o **SourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="774d6-149">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="774d6-150">Se pretender que o PSRepository recentemente criado para ser o repositório de predefinido, tem de anular o registo todos os outros PSRepositories.</span><span class="sxs-lookup"><span data-stu-id="774d6-150">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="774d6-151">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="774d6-151">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="774d6-152">O nome do repositório 'PSGallery' está reservado para utilização da galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="774d6-152">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="774d6-153">Pode anular o registo PSGallery, mas não é possível reutilizar o nome PSGallery para qualquer outro repositório.</span><span class="sxs-lookup"><span data-stu-id="774d6-153">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="774d6-154">Se tiver de restaurar o PSGallery, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="774d6-154">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="774d6-155">Publicação de um repositório local</span><span class="sxs-lookup"><span data-stu-id="774d6-155">Publishing to a local repository</span></span>

<span data-ttu-id="774d6-156">Assim que tiver registado a PSRepository local, pode publicar a sua PSRepository local.</span><span class="sxs-lookup"><span data-stu-id="774d6-156">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="774d6-157">Existem dois cenários de publicação principais: publicar o seu próprio módulo e publicação de um módulo do PSGallery.</span><span class="sxs-lookup"><span data-stu-id="774d6-157">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="774d6-158">Publicação de um módulo que criado</span><span class="sxs-lookup"><span data-stu-id="774d6-158">Publishing a module you authored</span></span>

<span data-ttu-id="774d6-159">Uso `Publish-Module` e `Publish-Script` para publicar seu módulo para seu local PSRepository da mesma forma que para a galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="774d6-159">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="774d6-160">Especifique a localização para o seu código</span><span class="sxs-lookup"><span data-stu-id="774d6-160">Specify the location for your code</span></span>
- <span data-ttu-id="774d6-161">Fornecer uma chave de API</span><span class="sxs-lookup"><span data-stu-id="774d6-161">Supply an API key</span></span>
- <span data-ttu-id="774d6-162">Especifique o nome do repositório.</span><span class="sxs-lookup"><span data-stu-id="774d6-162">Specify the repository name.</span></span> <span data-ttu-id="774d6-163">Por exemplo, `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="774d6-163">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="774d6-164">Tem de criar uma conta no servidor do NuGet, e inicie sessão gerar e salvar a chave de API.</span><span class="sxs-lookup"><span data-stu-id="774d6-164">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="774d6-165">Para uma partilha de ficheiros, utilize qualquer cadeia não vazia para o valor de NuGetApiKey.</span><span class="sxs-lookup"><span data-stu-id="774d6-165">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="774d6-166">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="774d6-166">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="774d6-167">Para garantir a segurança, as chaves de API não devem ser codificada em scripts.</span><span class="sxs-lookup"><span data-stu-id="774d6-167">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="774d6-168">Utilize um sistema de gestão de chaves segura.</span><span class="sxs-lookup"><span data-stu-id="774d6-168">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="774d6-169">Publicação de um módulo do PSGallery</span><span class="sxs-lookup"><span data-stu-id="774d6-169">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="774d6-170">Para publicar um módulo do PSGallery para sua PSRepository local, pode utilizar o cmdlet Save-Package.</span><span class="sxs-lookup"><span data-stu-id="774d6-170">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="774d6-171">Especifique o nome do pacote</span><span class="sxs-lookup"><span data-stu-id="774d6-171">Specify the Name of the Package</span></span>
- <span data-ttu-id="774d6-172">Especificar 'NuGet' como o fornecedor</span><span class="sxs-lookup"><span data-stu-id="774d6-172">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="774d6-173">Especificar a localização de PSGallery como o (de origem https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="774d6-173">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="774d6-174">Especifique o caminho para o seu repositório local</span><span class="sxs-lookup"><span data-stu-id="774d6-174">Specify the path to your local Repository</span></span>

<span data-ttu-id="774d6-175">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="774d6-175">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="774d6-176">Se sua PSRepository local é baseada na web, requer um passo adicional que utiliza nuget.exe para publicar.</span><span class="sxs-lookup"><span data-stu-id="774d6-176">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="774d6-177">Consulte a documentação para usar [nuget.exe][].</span><span class="sxs-lookup"><span data-stu-id="774d6-177">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="774d6-178">Instalar o PowerShellGet num sistema desligado</span><span class="sxs-lookup"><span data-stu-id="774d6-178">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="774d6-179">Implantar o PowerShellGet é difícil em ambientes que necessitam de sistemas para ser desligado da internet.</span><span class="sxs-lookup"><span data-stu-id="774d6-179">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="774d6-180">O PowerShellGet tem um processo de arranque que instala a versão mais recente na primeira vez que é utilizado.</span><span class="sxs-lookup"><span data-stu-id="774d6-180">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="774d6-181">O módulo de OfflinePowerShellGetDeploy na galeria do PowerShell fornece cmdlets que oferecem suporte a esse processo de arranque de configuração.</span><span class="sxs-lookup"><span data-stu-id="774d6-181">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="774d6-182">Para inicializar uma implantação offline, terá de:</span><span class="sxs-lookup"><span data-stu-id="774d6-182">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="774d6-183">Transferir e instalar o sistema de OfflinePowerShellGetDeploy sua ligação à internet e de seus sistemas desligados</span><span class="sxs-lookup"><span data-stu-id="774d6-183">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="774d6-184">Baixe o PowerShellGet e suas dependências no sistema de ligação à internet com o `Save-PowerShellGetForOffline` cmdlet</span><span class="sxs-lookup"><span data-stu-id="774d6-184">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="774d6-185">Copie o PowerShellGet e as respetivas dependências do sistema de ligação à internet para o sistema desligado</span><span class="sxs-lookup"><span data-stu-id="774d6-185">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="774d6-186">Utilize o `Install-PowerShellGetOffline` no sistema desligado para colocar o PowerShellGet e as respetivas dependências para as pastas apropriadas</span><span class="sxs-lookup"><span data-stu-id="774d6-186">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="774d6-187">Os seguintes comandos utilização `Save-PowerShellGetForOffline` para colocar todos os componentes numa pasta `f:\OfflinePowerShellGet`</span><span class="sxs-lookup"><span data-stu-id="774d6-187">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="774d6-188">Neste momento, tem de tornar o conteúdo do `F:\OfflinePowerShellGet` disponível para seus sistemas desconectados.</span><span class="sxs-lookup"><span data-stu-id="774d6-188">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="774d6-189">Execute o `Install-PowerShellGetOffline` cmdlet para instalar o PowerShellGet no sistema desligado.</span><span class="sxs-lookup"><span data-stu-id="774d6-189">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="774d6-190">É importante que não execute o PowerShellGet na sessão do PowerShell antes de executar estes comandos.</span><span class="sxs-lookup"><span data-stu-id="774d6-190">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="774d6-191">Uma vez PowerShellGet é carregado para a sessão, não não possível atualizar os componentes.</span><span class="sxs-lookup"><span data-stu-id="774d6-191">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="774d6-192">Se iniciar o PowerShellGet por engano, sair e reiniciar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="774d6-192">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="774d6-193">Depois de executar estes comandos, está pronto para publicar o PowerShellGet ao seu repositório local.</span><span class="sxs-lookup"><span data-stu-id="774d6-193">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="774d6-194">Para garantir a segurança, as chaves de API não devem ser codificada em scripts.</span><span class="sxs-lookup"><span data-stu-id="774d6-194">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="774d6-195">Utilize um sistema de gestão de chaves segura.</span><span class="sxs-lookup"><span data-stu-id="774d6-195">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
