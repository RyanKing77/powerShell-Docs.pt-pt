---
ms.date: 12/14/2018
keywords: PowerShell, o cmdlet
title: Escrever módulos portátil
ms.openlocfilehash: 237f6aaea0ed019c54d04a8477d7a456edf00910
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470991"
---
# <a name="portable-modules"></a>Módulos portátil

Windows PowerShell foi escrito para o [.NET Framework][] enquanto o PowerShell Core é escrito para [.NET Core][]. Módulos portáteis são módulos que funcionam no Windows PowerShell e o PowerShell Core. Embora o .NET Framework e .NET Core são altamente compatíveis, existem diferenças nas APIs disponíveis entre os dois. Também existem diferenças nas APIs disponíveis no Windows PowerShell e o PowerShell Core. Módulos que se destina a ser utilizado nos dois ambientes precisam estar atento essas diferenças.

## <a name="porting-an-existing-module"></a>Portando um módulo existente

### <a name="porting-a-pssnapin"></a>Portando um PSSnapIn

PowerShell [SnapIns](/powershell/developer/cmdlet/modules-and-snap-ins) não são suportados no PowerShell Core. No entanto, é comum para converter um PSSnapIn para um módulo do PowerShell. Normalmente, o código de registo de PSSnapIn está num único arquivo de origem de uma classe que deriva [PSSnapIn][].
Remover este ficheiro de origem da compilação; já não é necessária.

Uso [New-ModuleManifest][] para criar um novo manifesto de módulo substitui a necessidade do código de registo de PSSnapIn. Alguns dos valores do **PSSnapIn** (tal como **Descrição**) podem ser reutilizados no manifesto de módulo.

O **RootModule** propriedade no manifesto do módulo deve ser definida como o nome do assembly (dll) implementando os cmdlets.

### <a name="the-net-portability-analyzer-aka-apiport"></a>O analisador de portabilidade do .NET (também conhecido como APIPort)

Para os módulos de porta escritos para o Windows PowerShell trabalhar com o PowerShell Core, começar com o [analisador de portabilidade do .NET][]. Execute essa ferramenta em seu assembly compilado para determinar se as APIs do .NET usado no módulo são compatíveis com o .NET Framework, .NET Core e outros tempos de execução do .NET. A ferramenta sugere APIs alternativas, caso existam. Caso contrário, poderá ter de adicionar [verificações de tempo de execução][] e restringir as capacidades não disponíveis em tempos de execução específicos.

## <a name="creating-a-new-module"></a>Criar um novo módulo

Se criar um novo módulo, recomenda-se utilizar o [.NET CLI][].

### <a name="installing-the-powershell-standard-module-template"></a>Instalar o modelo de módulo do PowerShell Standard

Depois de instalar a CLI do .NET, instale uma biblioteca de modelos para gerar um módulo do PowerShell simple.
O módulo será compatível com o Windows PowerShell, PowerShell Core, Windows, Linux e macOS.

O exemplo seguinte mostra como instalar o modelo:

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

### <a name="creating-a-new-module-project"></a>Criar um novo projeto de módulo

Depois do modelo estiver instalado, pode criar um novo projeto de módulo de PowerShell usando esse modelo. Neste exemplo, o módulo de exemplo é chamado 'myModule'.

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

### <a name="building-the-module"></a>Criar o módulo

Utilize comandos da CLI do .NET padrão para compilar o projeto.

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

### <a name="testing-the-module"></a>O módulo de teste

Depois de criar o módulo, pode importá-lo e executar o cmdlet de exemplo.

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

As secções seguintes descrevem detalhadamente algumas das tecnologias utilizadas por este modelo.

## <a name="net-standard-library"></a>Biblioteca de padrão do .NET

[.NET standard][] é uma especificação formal de APIs de .NET que estão disponíveis em todas as implementações de .NET. Visando o .NET Standard funciona com as versões do .NET Framework e .NET Core que são compatíveis com essa versão do .NET Standard de código gerenciado.

> [!NOTE]
> Embora uma API pode existir em .NET Standard, a implementação de API em .NET Core poderão emitir um `PlatformNotSupportedException` em tempo de execução, portanto, para verificar a compatibilidade com o Windows PowerShell e o PowerShell Core, a prática recomendada é executar testes para seu módulo em ambos os ambientes.
> Também execute testes em Linux e macOS, se seu módulo deve ser entre plataformas.

Direcionamento padrão do .NET ajuda a garantir que, à medida que o módulo evolui, APIs incompatíveis não acidentalmente são introduzidas no módulo. Incompatibilidades são detetadas no momento da compilação, em vez de tempo de execução.

No entanto, não é necessária para o destino .NET Standard para um módulo para trabalhar com o Windows PowerShell e o PowerShell Core, desde que usar APIs compatíveis. A linguagem intermediária (IL) é compatível entre os dois tempos de execução. Pode direcionar .NET Framework 4.6.1, que é compatível com .NET Standard 2.0. Se não usar APIs fora do .NET Standard 2.0, em seguida, seu módulo funciona com o PowerShell Core 6 sem recompilação.

## <a name="powershell-standard-library"></a>Biblioteca de padrão de PowerShell

O [padrão de PowerShell][] biblioteca é uma especificação formal de APIs do PowerShell disponíveis em todas as versões do PowerShell igual ou superior para a versão esse padrão.

Por exemplo, [PowerShell Standard 5.1][] é compatível com o PowerShell Core 6.0 e o Windows PowerShell 5.1 ou mais recente.

Recomendamos que compilar seu módulo usando a biblioteca padrão do PowerShell. A biblioteca garante que as APIs estão disponíveis e implementado no Windows PowerShell e o PowerShell Core 6.
Padrão de PowerShell destina-se sempre ser compatível com reencaminhamentos. Um módulo criado com o PowerShell 5.1 de biblioteca padrão sempre serão compatível com versões futuras do PowerShell.

## <a name="module-manifest"></a>Manifesto do módulo

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a>Com a indicação de compatibilidade com o Windows PowerShell e o PowerShell Core

Depois de confirmar que o seu módulo funciona com o Windows PowerShell e o PowerShell Core, o manifesto de módulo deve indicar explicitamente compatibilidade utilizando o [CompatiblePSEditions][] propriedade. Um valor de `Desktop` significa que o módulo é compatível com o Windows PowerShell, enquanto um valor de `Core` significa que o módulo é compatível com o PowerShell Core. Incluindo ambos `Desktop` e `Core` significa que o módulo é compatível com o Windows PowerShell e o PowerShell Core.

> [!NOTE]
> `Core` não automaticamente significa que o módulo é compatível com Windows, Linux e macOS.
> O **CompatiblePSEditions** propriedade foi introduzida no PowerShell v5. Manifestos de módulo que utilizam o **CompatiblePSEditions** propriedade falhe ao carregar nas versões anteriores ao v5 do PowerShell.

### <a name="indicating-os-compatibility"></a>Com a indicação de compatibilidade do SO

Em primeiro lugar, confirme que o seu módulo funciona em Linux e macOS. Em seguida, indicam compatibilidade com esses sistemas operacionais no manifesto do módulo. Isto torna mais fácil do que os utilizadores encontrem seu módulo para seu sistema operativo quando publicado para o [galeria do PowerShell][].

No manifesto do módulo, o `PrivateData` propriedade tem um `PSData` subpropriedade. O opcional `Tags` propriedade do `PSData` assume uma matriz de valores que aparecem na galeria do PowerShell. A galeria do PowerShell suporta os seguintes valores de compatibilidade:

| Sinalizador               | Descrição                                |
|-------------------|--------------------------------------------|
| PSEdition_Core    | Compatível com o PowerShell Core 6          |
| PSEdition_Desktop | Compatível com o Windows PowerShell         |
| Windows           | Compatível com Windows                    |
| Linux             | Compatível com o Linux (sem distro específica) |
| macOS             | Compatível com macOS                      |

Exemplo:

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
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[Padrão de PowerShell]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[Galeria do PowerShell]: https://www.powershellgallery.com
[Analisador de portabilidade do .NET]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
