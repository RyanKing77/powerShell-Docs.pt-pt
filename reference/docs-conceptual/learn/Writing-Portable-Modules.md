---
ms.date: 12/14/2018
keywords: PowerShell, o cmdlet
title: Escrever módulos portátil
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086413"
---
# <a name="portable-modules"></a><span data-ttu-id="dd023-103">Módulos portátil</span><span class="sxs-lookup"><span data-stu-id="dd023-103">Portable Modules</span></span>

<span data-ttu-id="dd023-104">Windows PowerShell foi escrito para o [.NET Framework][] enquanto o PowerShell Core é escrito para [.NET Core][].</span><span class="sxs-lookup"><span data-stu-id="dd023-104">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="dd023-105">Módulos portáteis são módulos que funcionam no Windows PowerShell e o PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="dd023-105">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="dd023-106">Embora o .NET Framework e .NET Core são altamente compatíveis, existem diferenças nas APIs disponíveis entre os dois.</span><span class="sxs-lookup"><span data-stu-id="dd023-106">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="dd023-107">Também existem diferenças nas APIs disponíveis no Windows PowerShell e o PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="dd023-107">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="dd023-108">Módulos que se destina a ser utilizado nos dois ambientes precisam estar atento essas diferenças.</span><span class="sxs-lookup"><span data-stu-id="dd023-108">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="dd023-109">Portando um módulo existente</span><span class="sxs-lookup"><span data-stu-id="dd023-109">Porting an Existing Module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="dd023-110">Portando um PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="dd023-110">Porting a PSSnapIn</span></span>

<span data-ttu-id="dd023-111">PowerShell SnapIns (PSSnapIn) não são suportados no PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="dd023-111">PowerShell SnapIns (PSSnapIn) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="dd023-112">No entanto, é comum para converter um PSSnapIn para um módulo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd023-112">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="dd023-113">Normalmente, o código de registo de PSSnapIn está num único arquivo de origem de uma classe que deriva [PSSnapIn][].</span><span class="sxs-lookup"><span data-stu-id="dd023-113">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span> <span data-ttu-id="dd023-114">Remover este ficheiro de origem da compilação; já não é necessária.</span><span class="sxs-lookup"><span data-stu-id="dd023-114">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="dd023-115">Uso [New-ModuleManifest][] para criar um novo manifesto de módulo substitui a necessidade do código de registo de PSSnapIn.</span><span class="sxs-lookup"><span data-stu-id="dd023-115">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="dd023-116">Alguns dos valores de PSSnapIn (por exemplo, descrição) podem ser reutilizados no manifesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="dd023-116">Some of the values from the PSSnapIn (such as Description) can be reused within the module manifest.</span></span>

<span data-ttu-id="dd023-117">O `RootModule` propriedade no manifesto do módulo deve ser definida como o nome do assembly (dll) implementando os cmdlets.</span><span class="sxs-lookup"><span data-stu-id="dd023-117">The `RootModule` property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="dd023-118">O analisador de portabilidade do .NET (também conhecido como APIPort)</span><span class="sxs-lookup"><span data-stu-id="dd023-118">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="dd023-119">Para os módulos de porta escritos para o Windows PowerShell trabalhar com o PowerShell Core, começar com o [analisador de portabilidade do .NET][].</span><span class="sxs-lookup"><span data-stu-id="dd023-119">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="dd023-120">Execute essa ferramenta em seu assembly compilado para determinar se as APIs do .NET usado no módulo são compatíveis com o .NET Framework, .NET Core e outros tempos de execução do .NET.</span><span class="sxs-lookup"><span data-stu-id="dd023-120">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="dd023-121">A ferramenta sugere APIs alternativas, caso existam.</span><span class="sxs-lookup"><span data-stu-id="dd023-121">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="dd023-122">Caso contrário, poderá ter de adicionar [verificações de tempo de execução][] e restringir as capacidades não disponíveis em tempos de execução específicos.</span><span class="sxs-lookup"><span data-stu-id="dd023-122">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="dd023-123">Criar um novo módulo</span><span class="sxs-lookup"><span data-stu-id="dd023-123">Creating a New Module</span></span>

<span data-ttu-id="dd023-124">Se criar um novo módulo, recomenda-se utilizar o [.NET CLI][].</span><span class="sxs-lookup"><span data-stu-id="dd023-124">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="dd023-125">Instalar o modelo de módulo do PowerShell Standard</span><span class="sxs-lookup"><span data-stu-id="dd023-125">Installing the PowerShell Standard Module Template</span></span>

<span data-ttu-id="dd023-126">Depois de instalar a CLI do .NET, instale uma biblioteca de modelos para gerar um módulo do PowerShell simple.</span><span class="sxs-lookup"><span data-stu-id="dd023-126">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="dd023-127">O módulo será compatível com o Windows PowerShell, PowerShell Core, Windows, Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="dd023-127">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="dd023-128">O exemplo seguinte mostra como instalar o modelo:</span><span class="sxs-lookup"><span data-stu-id="dd023-128">The following example shows how to install the template:</span></span>

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
```

```output
  Restoring packages for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj...
  Installing Microsoft.PowerShell.Standard.Module.Template 0.1.3.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.targets.
  Restore completed in 1.66 sec for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj.

Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.
  -n, --name          The name for the output being created. If no name is specified, the name of the current directory is used.
  -o, --output        Location to place the generated output.
  -i, --install       Installs a source or a template pack.
  -u, --uninstall     Uninstalls a source or a template pack.
  --nuget-source      Specifies a NuGet source to use during install.
  --type              Filters templates based on available types. Predefined values are "project", "item" or "other".
  --force             Forces content to be generated even if it would change existing files.
  -lang, --language   Filters templates based on language and specifies the language of the template to create.


Templates                                         Short Name         Language          Tags
----------------------------------------------------------------------------------------------------------------------------
Console Application                               console            [C#], F#, VB      Common/Console
Class library                                     classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module                        psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a><span data-ttu-id="dd023-129">Criar um novo projeto de módulo</span><span class="sxs-lookup"><span data-stu-id="dd023-129">Creating a New Module Project</span></span>

<span data-ttu-id="dd023-130">Depois do modelo estiver instalado, pode criar um novo projeto de módulo de PowerShell usando esse modelo.</span><span class="sxs-lookup"><span data-stu-id="dd023-130">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="dd023-131">Neste exemplo, o módulo de exemplo é chamado 'myModule'.</span><span class="sxs-lookup"><span data-stu-id="dd023-131">In this example, the sample module is called 'myModule'.</span></span>

```
PS> mkdir myModule

    Directory: C:\Users\Steve

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 8/3/2018 2:41 PM myModule

PS> cd myModule
PS C:\Users\Steve\myModule> dotnet new psmodule

The template "PowerShell Standard Module" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Steve\myModule\myModule.csproj...
  Restoring packages for C:\Users\Steve\myModule\myModule.csproj...
  Installing PowerShellStandard.Library 5.1.0.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.targets.
  Restore completed in 1.76 sec for C:\Users\Steve\myModule\myModule.csproj.

Restore succeeded.
```

### <a name="building-the-module"></a><span data-ttu-id="dd023-132">Criar o módulo</span><span class="sxs-lookup"><span data-stu-id="dd023-132">Building the Module</span></span>

<span data-ttu-id="dd023-133">Utilize comandos da CLI do .NET padrão para compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="dd023-133">Use standard .NET CLI commands to build the project.</span></span>

```powershell
dotnet build
```

```output
PS C:\Users\Steve\myModule> dotnet build
Microsoft (R) Build Engine version 15.7.179.6572 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 76.85 ms for C:\Users\Steve\myModule\myModule.csproj.
  myModule -> C:\Users\Steve\myModule\bin\Debug\netstandard2.0\myModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:05.40
```

### <a name="testing-the-module"></a><span data-ttu-id="dd023-134">O módulo de teste</span><span class="sxs-lookup"><span data-stu-id="dd023-134">Testing the Module</span></span>

<span data-ttu-id="dd023-135">Depois de criar o módulo, pode importá-lo e executar o cmdlet de exemplo.</span><span class="sxs-lookup"><span data-stu-id="dd023-135">After building the module, you can import it and execute the sample cmdlet.</span></span>

```powershell
ipmo .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
PS C:\Users\Steve\myModule> ipmo .\bin\Debug\netstandard2.0\myModule.dll
PS C:\Users\Steve\myModule> Test-SampleCmdlet -?

NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


PS C:\Users\Steve\myModule> Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat

FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

<span data-ttu-id="dd023-136">As secções seguintes descrevem detalhadamente algumas das tecnologias utilizadas por este modelo.</span><span class="sxs-lookup"><span data-stu-id="dd023-136">The following sections describe in detail some of the technologies used by this template.</span></span>

## <a name="net-standard-library"></a><span data-ttu-id="dd023-137">Biblioteca de padrão do .NET</span><span class="sxs-lookup"><span data-stu-id="dd023-137">.NET Standard Library</span></span>

<span data-ttu-id="dd023-138">[.NET standard][] é uma especificação formal de APIs de .NET que estão disponíveis em todas as implementações de .NET.</span><span class="sxs-lookup"><span data-stu-id="dd023-138">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="dd023-139">Visando o .NET Standard funciona com as versões do .NET Framework e .NET Core que são compatíveis com essa versão do .NET Standard de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="dd023-139">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="dd023-140">Embora uma API pode existir em .NET Standard, a implementação de API em .NET Core poderão emitir um `PlatformNotSupportedException` em tempo de execução, portanto, para verificar a compatibilidade com o Windows PowerShell e o PowerShell Core, a prática recomendada é executar testes para seu módulo em ambos os ambientes.</span><span class="sxs-lookup"><span data-stu-id="dd023-140">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="dd023-141">Também execute testes em Linux e macOS, se seu módulo deve ser entre plataformas.</span><span class="sxs-lookup"><span data-stu-id="dd023-141">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="dd023-142">Direcionamento padrão do .NET ajuda a garantir que, à medida que o módulo evolui, APIs incompatíveis não acidentalmente são introduzidas no módulo.</span><span class="sxs-lookup"><span data-stu-id="dd023-142">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="dd023-143">Incompatibilidades são detetadas no momento da compilação, em vez de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="dd023-143">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="dd023-144">No entanto, não é necessária para o destino .NET Standard para um módulo para trabalhar com o Windows PowerShell e o PowerShell Core, desde que usar APIs compatíveis.</span><span class="sxs-lookup"><span data-stu-id="dd023-144">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="dd023-145">A linguagem intermediária (IL) é compatível entre os dois tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="dd023-145">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="dd023-146">Pode direcionar .NET Framework 4.6.1, que é compatível com .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="dd023-146">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="dd023-147">Se não usar APIs fora do .NET Standard 2.0, em seguida, seu módulo funciona com o PowerShell Core 6 sem recompilação.</span><span class="sxs-lookup"><span data-stu-id="dd023-147">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

## <a name="powershell-standard-library"></a><span data-ttu-id="dd023-148">Biblioteca de padrão de PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd023-148">PowerShell Standard Library</span></span>

<span data-ttu-id="dd023-149">O [padrão de PowerShell][] biblioteca é uma especificação formal de APIs do PowerShell disponíveis em todas as versões do PowerShell igual ou superior para a versão esse padrão.</span><span class="sxs-lookup"><span data-stu-id="dd023-149">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="dd023-150">Por exemplo, [PowerShell Standard 5.1][] é compatível com o PowerShell Core 6.0 e o Windows PowerShell 5.1 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="dd023-150">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="dd023-151">Recomendamos que compilar seu módulo usando a biblioteca padrão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd023-151">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="dd023-152">A biblioteca garante que as APIs estão disponíveis e implementado no Windows PowerShell e o PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="dd023-152">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="dd023-153">Padrão de PowerShell destina-se sempre ser compatível com reencaminhamentos.</span><span class="sxs-lookup"><span data-stu-id="dd023-153">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="dd023-154">Um módulo criado com o PowerShell 5.1 de biblioteca padrão sempre serão compatível com versões futuras do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd023-154">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

## <a name="module-manifest"></a><span data-ttu-id="dd023-155">Manifesto do módulo</span><span class="sxs-lookup"><span data-stu-id="dd023-155">Module Manifest</span></span>

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="dd023-156">Com a indicação de compatibilidade com o Windows PowerShell e o PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="dd023-156">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="dd023-157">Depois de confirmar que o seu módulo funciona com o Windows PowerShell e o PowerShell Core, o manifesto de módulo deve indicar explicitamente compatibilidade utilizando o [CompatiblePSEditions][] propriedade.</span><span class="sxs-lookup"><span data-stu-id="dd023-157">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="dd023-158">Um valor de `Desktop` significa que o módulo é compatível com o Windows PowerShell, enquanto um valor de `Core` significa que o módulo é compatível com o PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="dd023-158">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="dd023-159">Incluindo ambos `Desktop` e `Core` significa que o módulo é compatível com o Windows PowerShell e o PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="dd023-159">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="dd023-160">`Core` não automaticamente significa que o módulo é compatível com Windows, Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="dd023-160">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="dd023-161">O **CompatiblePSEditions** propriedade foi introduzida no PowerShell v5.</span><span class="sxs-lookup"><span data-stu-id="dd023-161">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="dd023-162">Manifestos de módulo que utilizam o **CompatiblePSEditions** propriedade falhe ao carregar nas versões anteriores ao v5 do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd023-162">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="dd023-163">Com a indicação de compatibilidade do SO</span><span class="sxs-lookup"><span data-stu-id="dd023-163">Indicating OS Compatibility</span></span>

<span data-ttu-id="dd023-164">Em primeiro lugar, confirme que o seu módulo funciona em Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="dd023-164">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="dd023-165">Em seguida, indicam compatibilidade com esses sistemas operacionais no manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="dd023-165">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="dd023-166">Isto torna mais fácil do que os utilizadores encontrem seu módulo para seu sistema operativo quando publicado para o [galeria do PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="dd023-166">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="dd023-167">No manifesto do módulo, o `PrivateData` propriedade tem um `PSData` subpropriedade.</span><span class="sxs-lookup"><span data-stu-id="dd023-167">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="dd023-168">O opcional `Tags` propriedade do `PSData` assume uma matriz de valores que aparecem na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd023-168">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="dd023-169">A galeria do PowerShell suporta os seguintes valores de compatibilidade:</span><span class="sxs-lookup"><span data-stu-id="dd023-169">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="dd023-170">Sinalizador</span><span class="sxs-lookup"><span data-stu-id="dd023-170">Tag</span></span>               | <span data-ttu-id="dd023-171">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd023-171">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="dd023-172">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="dd023-172">PSEdition_Core</span></span>    | <span data-ttu-id="dd023-173">Compatível com o PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="dd023-173">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="dd023-174">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="dd023-174">PSEdition_Desktop</span></span> | <span data-ttu-id="dd023-175">Compatível com o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd023-175">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="dd023-176">Windows</span><span class="sxs-lookup"><span data-stu-id="dd023-176">Windows</span></span>           | <span data-ttu-id="dd023-177">Compatível com Windows</span><span class="sxs-lookup"><span data-stu-id="dd023-177">Compatible with Windows</span></span>                    |
| <span data-ttu-id="dd023-178">Linux</span><span class="sxs-lookup"><span data-stu-id="dd023-178">Linux</span></span>             | <span data-ttu-id="dd023-179">Compatível com o Linux (sem distro específica)</span><span class="sxs-lookup"><span data-stu-id="dd023-179">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="dd023-180">macOS</span><span class="sxs-lookup"><span data-stu-id="dd023-180">macOS</span></span>             | <span data-ttu-id="dd023-181">Compatível com macOS</span><span class="sxs-lookup"><span data-stu-id="dd023-181">Compatible with macOS</span></span>                      |

<span data-ttu-id="dd023-182">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="dd023-182">Example:</span></span>

```powershell
@{
    GUID = "4ae9fd46-338a-459c-8186-07f910774cb8"
    Author = "Microsoft Corporation"
    CompanyName = "Microsoft Corporation"
    Copyright = "(C) Microsoft Corporation. All rights reserved."
    HelpInfoUri = "https://go.microsoft.com/fwlink/?linkid=855962"
    ModuleVersion = "1.2.4"
    PowerShellVersion = "3.0"
    ClrVersion = "4.0"
    RootModule = "PackageManagement.psm1"
    Description = 'PackageManagement (a.k.a. OneGet) is a new way to discover and install software packages from around the web.
 It is a manager or multiplexer of existing package managers (also called package providers) that unifies Windows package management with a single Windows PowerShell interface. With PackageManagement, you can do the following.
  - Manage a list of software repositories in which packages can be searched, acquired and installed
  - Discover software packages
  - Seamlessly install, uninstall, and inventory packages from one or more software repositories'

    CmdletsToExport = @(
        'Find-Package',
        'Get-Package',
        'Get-PackageProvider',
        'Get-PackageSource',
        'Install-Package',
        'Import-PackageProvider'
        'Find-PackageProvider'
        'Install-PackageProvider'
        'Register-PackageSource',
        'Set-PackageSource',
        'Unregister-PackageSource',
        'Uninstall-Package'
        'Save-Package'
    )

    FormatsToProcess  = @('PackageManagement.format.ps1xml')

    PrivateData = @{
        PSData = @{
            Tags = @('PackageManagement', 'PSEdition_Core', 'PSEdition_Desktop', 'Windows', 'Linux', 'macOS')
            ProjectUri = 'https://oneget.org'
        }
    }
}
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[verificações de tempo de execução]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[runtime checks]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[Padrão de PowerShell]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[Galeria do PowerShell]: https://www.powershellgallery.com
[PowerShell Gallery]: https://www.powershellgallery.com
[Analisador de portabilidade do .NET]: https://github.com/Microsoft/dotnet-apiport
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
