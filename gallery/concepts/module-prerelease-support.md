---
ms.date: 09/26/2017
contributor: keithb
keywords: cmdlet do powershell do galeria, psget
title: Versões de pré-lançamento do módulo
ms.openlocfilehash: eced067dd21082de0db653daf3b838217154f1dd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056250"
---
# <a name="prerelease-module-versions"></a>Versões de pré-lançamento do módulo

A partir da versão 1.6.0, PowerShellGet e da galeria do PowerShell fornecem suporte para versões superiores a 1.0.0 como uma versão de pré-lançamento de marcação. Antes desta funcionalidade, os pacotes de pré-lançamento eram limitado a ter um início de versão com 0. O objetivo desses recursos é oferecem maior suporte para [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) Convenção de controle de versão sem perder com versões anteriores a compatibilidade com o PowerShell versões existentes e 3 ou acima versões do PowerShellGet. Este tópico concentra-se nos recursos específicos de módulo. As funcionalidades equivalentes para os scripts estão na [versões de pré-lançamento de Scripts](script-prerelease-support.md) tópico. Utilizar estas funcionalidades, os publicadores podem identificar um módulo ou o script como versão 2.5.0-alpha e mais tarde lançar uma versão de prontos para produção 2.5.0 que substitui a versão de pré-lançamento.

Num alto nível, as funcionalidades de pré-lançamento do módulo incluem:

- Adicionar uma cadeia de caracteres de pré-lançamento para a secção de PSData do manifesto do módulo identifica o módulo como uma versão de pré-lançamento. Quando o módulo é publicado na galeria do PowerShell, estes dados são extraídos de manifesto e utilizados para identificar pacotes de pré-lançamento.
- Aquisição de pacotes de pré-lançamento exige a inclusão `-AllowPrerelease` sinalizador para os comandos do PowerShellGet `Find-Module`, `Install-Module`, `Update-Module`, e `Save-Module`. Se o sinalizador não for especificado, os pacotes de pré-lançamento não será apresentado.
- Versões do módulo exibidas pelo `Find-Module`, `Get-InstalledModule`e na galeria do PowerShell será apresentada como uma única cadeia de caracteres com a cadeia de pré-lançamento anexada, como no 2.5.0-alpha.

Detalhes para as funcionalidades estão incluídas abaixo.

Estas alterações não afetam o suporte da versão do módulo que está incorporado no PowerShell e são compatíveis com o PowerShell 3.0, 4.0 e 5.

## <a name="identifying-a-module-version-as-a-prerelease"></a>Identificar uma versão do módulo como uma versão de pré-lançamento

Suporte do PowerShellGet para versões de pré-lançamento requer a utilização de dois campos no manifesto do módulo:

- ModuleVersion incluído no manifesto do módulo tem de ser uma versão de 3 partes se é utilizada uma versão de pré-lançamento e deve estar em conformidade com o controle de versão do PowerShell existente. O formato de versão seria A.B.C, onde A, B e C estão todos os números inteiros.
- A cadeia de caracteres de pré-lançamento é especificada no manifesto do módulo, na secção PSData PrivateData.

Os requisitos detalhados sobre a cadeia de caracteres de pré-lançamento estão abaixo.

Uma seção de exemplo de um manifesto de módulo que define um módulo como uma versão de pré-lançamento seria semelhante ao seguinte:

```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

Os requisitos detalhados para a cadeia de pré-lançamento são:

- Cadeia de caracteres de pré-lançamento só pode ser especificada quando o ModuleVersion é 3 segmentos para major. Isso se alinha com SemVer v1.0.0.
- Um hífen é o delimitador entre o número de compilação e a cadeia de pré-lançamento. Um hífen pode ser incluído na cadeia de pré-lançamento, como o primeiro caráter, apenas.
- A cadeia de caracteres de pré-lançamento pode conter apenas carateres de alfanuméricos ASCII [0-9A-Za - z-]. É melhor prática para iniciar a versão de pré-lançamento de cadeias de caracteres com um caractere alfa, como será mais fácil de identificar que esta é uma versão de pré-lançamento quando efetua a análise de uma lista de pacotes.
- Apenas SemVer v1.0.0 pré-lançamento cadeias de caracteres são suportadas neste momento. Cadeia de caracteres de pré-lançamento **não podem** conter qualquer um dos ponto ou + [. +], que é permitido em SemVer 2.0.
- Exemplos de cadeia de caracteres de pré-lançamento suportado são:-alfa, - alpha1,-BETA, - update20171020

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>Impacto de controlo de versões de pré-lançamento nas pastas de instalação e a ordem de ordenação

Ordem de classificação é alterado quando utilizar uma versão de pré-lançamento, que é importante durante a publicação na galeria do PowerShell, e ao instalar os módulos com comandos do PowerShellGet. Se a cadeia de caracteres de pré-lançamento é especificada para dois módulos, a ordem de classificação baseia-se na parte de cadeia de caracteres a seguir o hífen. Então, versão 2.5.0-alpha é menor que 2.5.0-beta, que é menor que 2.5.0-gamma. Se dois módulos têm o mesmo ModuleVersion e apenas um tem uma cadeia de caracteres de pré-lançamento, o módulo sem a cadeia de caracteres de pré-lançamento é considerado como a versão de prontos para produção e será classificado como uma versão superior à versão de pré-lançamento (que inclui a versão de pré-lançamento cadeia de caracteres). Por exemplo, ao comparar versões 2.5.0 e 2.5.0-beta, o 2.5.0 versão será considerada o maior dos dois.

Durante a publicação na galeria do PowerShell, por predefinição a versão do módulo a ser publicado tem de ter uma versão maior do que qualquer versão publicada anteriormente que está na galeria do PowerShell.

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>Encontrar e adquirir os pacotes de pré-lançamento utilizar comandos do PowerShellGet

Lidar com pacotes de pré-lançamento com atualização Find-Module PowerShellGet, Install-Module-Module, e os comandos de Save-Module é necessário adicionar o sinalizador - AllowPrerelease. Se não for especificado - AllowPrerelease, pacotes de pré-lançamento serão incluído, se estiverem presentes. Se não for especificado o sinalizador - AllowPrerelease, pacotes de pré-lançamento não será apresentado.

As únicas exceções a esta nos comandos de módulo PowerShellGet são Get-InstalledModule e alguns casos com o módulo de desinstalação.

- Get-InstalledModule sempre mostrará automaticamente as informações de pré-lançamento na cadeia de versão para módulos.
- Desinstalar-Module por predefinição desinstalará a versão mais recente de um módulo, se __nenhuma versão__ está especificado. Esse comportamento não mudou. No entanto, se não for especificada uma versão de pré-lançamento usando - RequiredVersion, - AllowPrerelease será necessária.

## <a name="examples"></a>Exemplos

Assumir que a galeria do PowerShell tem versões do módulo TestPackage 1.8.0 e 1.9.0-alpha. Se `-AllowPrerelease` não é especificado, apenas a versão 1.8.0 será retornado.

```powershell
find-module TestPackage
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.8.0          TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

```powershell
find-module TestPackage -AllowPrerelease
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.9.0-alpha    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

Para instalar uma versão de pré-lançamento, sempre Especifica - AllowPrerelease. Especificar uma cadeia de versão de pré-lançamento não é suficiente.

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha
```

```output
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage
```

O comando anterior falhou porque - AllowPrerelease não foi especificado. Adicionar `-AllowPrerelease` irá resultar no sucesso.

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

Não é suportada a instalação lado a lado das versões de um módulo que diferem apenas devido a versão de pré-lançamento especificado. Ao instalar um módulo com o PowerShellGet, versões diferentes do mesmo módulo são instalada lado a lado através da criação de um nome de pasta com o ModuleVersion. ModuleVersion, sem a cadeia de pré-lançamento, é utilizada para o nome da pasta. Se um usuário instala MyModule versão 2.5.0-alpha, esta será instalada para o `MyModule\2.5.0` pasta. Se o utilizador, em seguida, instala 2.5.0-beta, poderá ser a versão de 2.5.0-beta **substituir** o conteúdo da pasta `MyModule\2.5.0`. Uma vantagem dessa abordagem é que não é necessário desinstalar a versão de pré-lançamento depois de instalar a versão de prontos para produção. O exemplo abaixo mostra o que esperar:

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-alpha     TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name            Repository  Description
-------        ----            ----------  -----------
1.9.0-beta     TestPackage     PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

```

Desinstalar-Module irá remover a versão mais recente de um módulo quando - RequiredVersion não é fornecido.
Se - RequiredVersion for especificada e é uma versão de pré-lançamento, - AllowPrerelease tem de ser adicionado ao comando.

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
2.0.0-alpha1    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta

Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-Module

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
2.0.0-alpha1    TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...
```

## <a name="more-details"></a>Obter mais detalhes

- [Versões de pré-lançamento do Script](script-prerelease-support.md)
- [Find-Module](/powershell/module/powershellget/find-module)
- [Install-Module](/powershell/module/powershellget/install-module)
- [Save-Module](/powershell/module/powershellget/save-module)
- [Update-Module](/powershell/module/powershellget/Update-Module)
- [Get-InstalledModule](/powershell/module/powershellget/get-installedmodule)
- [UnInstall-Module](/powershell/module/powershellget/uninstall-module)
