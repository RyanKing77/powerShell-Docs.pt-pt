---
ms.date: 10/17/2017
contributor: keithb
keywords: cmdlet do powershell do galeria, psget
title: Versões de pré-lançamento de scripts
ms.openlocfilehash: 4e7eab682008ed57163c51fe3a61a744b347bef2
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002740"
---
# <a name="prerelease-versions-of-scripts"></a>Versões de pré-lançamento de scripts

A partir da versão 1.6.0, PowerShellGet e da galeria do PowerShell fornecem suporte para versões superiores a 1.0.0 como uma versão de pré-lançamento de marcação. Antes desta funcionalidade, os pacotes de pré-lançamento eram limitado a ter um início de versão com 0. O objetivo desses recursos é oferecem maior suporte para [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) Convenção de controle de versão sem perder com versões anteriores a compatibilidade com o PowerShell versões existentes e 3 ou acima versões do PowerShellGet. Este tópico foca-se os recursos específicos de script. As funcionalidades equivalentes para módulos estão na [versões do módulo de pré-lançamento](module-prerelease-support.md) tópico. Utilizar estas funcionalidades, os publicadores podem identificar um script como versão 2.5.0-alpha e mais tarde lançar uma versão de prontos para produção 2.5.0 que substitui a versão de pré-lançamento.

Num alto nível, as funcionalidades de pré-lançamento do script incluem:

- Adicionando o sufixo PrereleaseString para a cadeia de versão no manifesto do script. Quando os scripts é publicado na galeria do PowerShell, estes dados são extraídos de manifesto e utilizados para identificar pacotes de pré-lançamento.
- Aquisição de pacotes de pré-lançamento é necessário adicionar o sinalizador - AllowPrerelease para os comandos do PowerShellGet Find-Script, Script de instalação, Script de atualização e Save-Script. Se o sinalizador não for especificado, os pacotes de pré-lançamento não será apresentado.
- Apresentado por Find-Script, Get-InstalledScript e na galeria do PowerShell de versões de script serão apresentadas com o PrereleaseString, como no 2.5.0-alpha.

Detalhes para as funcionalidades estão incluídas abaixo.

## <a name="identifying-a-script-version-as-a-prerelease"></a>Identificar uma versão do script como uma versão de pré-lançamento

Suporte do PowerShellGet para versões de pré-lançamento é mais fácil para os scripts do que módulos. Controle de versão do script só é suportado pelo PowerShellGet, pelo que existem não existem problemas de compatibilidade causados por adicionar a cadeia de caracteres de pré-lançamento. Para identificar um script na galeria do PowerShell como uma versão de pré-lançamento, adicione um sufixo de pré-lançamento para uma cadeia de versão corretamente formatado nos metadados do script.

Uma seção de exemplo de um manifesto de script com uma versão de pré-lançamento seria semelhante ao seguinte:

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

Para utilizar um sufixo de pré-lançamento, a cadeia de versão tem de cumprir os seguintes requisitos:

- Só pode ser especificado um sufixo de pré-lançamento quando a versão é 3 segmentos para major.
  Isso se alinha com SemVer v1.0.0
- O sufixo de pré-lançamento é uma cadeia que começa com um hífen e pode conter carateres de alfanuméricos ASCII [0-9A-Za - z-]
- Apenas SemVer v1.0.0 pré-lançamento cadeias de caracteres são suportadas neste momento, por isso, o sufixo de pré-lançamento **não podem** conter qualquer um dos ponto ou + [. +], que é permitido em SemVer 2.0
- Exemplos de cadeias de PrereleaseString suportadas são:-alfa, - alpha1,-BETA, - update20171020

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>Impacto de controlo de versões de pré-lançamento nas pastas de instalação e a ordem de ordenação

Ordem de classificação é alterado quando utilizar uma versão de pré-lançamento, que é importante durante a publicação na galeria do PowerShell, e durante a instalação de scripts com comandos do PowerShellGet. Se dois scripts de versões com o número da versão existe, a ordem de classificação baseia-se a parte da cadeia de caracteres a seguir o hífen. Então, versão 2.5.0-alpha é menor que 2.5.0-beta, que é menor que 2.5.0-gamma. Se dois scripts têm o mesmo número de versão e apenas um tem um PrereleaseString, o script **sem** o sufixo de pré-lançamento é considerado como a versão de prontos para produção e será classificado como uma versão mais recente do que a versão de pré-lançamento versão. Por exemplo, ao comparar versões 2.5.0 e 2.5.0-beta, o 2.5.0 versão será considerada o maior dos dois.

Durante a publicação na galeria do PowerShell, por predefinição a versão do script a ser publicado tem de ter uma versão maior do que qualquer versão publicada anteriormente que está na galeria do PowerShell. Um publicador pode atualizar a versão 2.5.0-alpha 2.5.0-beta ou com 2.5.0 (com sem sufixo pré-lançamento).

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>Encontrar e adquirir os pacotes de pré-lançamento utilizar comandos do PowerShellGet

Lidar com pacotes de pré-lançamento usando o PowerShellGet Find-Script, Script de instalação, atualização-Script, e os comandos de Save-Script é necessário adicionar o sinalizador - AllowPrerelease. Se não for especificado - AllowPrerelease, pacotes de pré-lançamento serão incluído, se estiverem presentes. Se não for especificado o sinalizador - AllowPrerelease, pacotes de pré-lançamento não será apresentado.

As únicas exceções a esta nos comandos de script do PowerShellGet são Get-InstalledScript e alguns casos com Script de desinstalação.

- Get-InstalledScript sempre mostrará automaticamente as informações de pré-lançamento na cadeia de versão se estiver presente.
- Script de desinstalação irá por predefinição desinstalar a versão mais recente de um script, se **nenhuma versão** está especificado. Esse comportamento não mudou. No entanto, se não for especificada uma versão de pré-lançamento usando `-RequiredVersion`, `-AllowPrerelease` será necessária.

## <a name="examples"></a>Exemplos

```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> Find-Script TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Find-Script TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# To install a prerelease, you must specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha

PackageManagement\Find-Package : No match was found for the specified search criteria and script name 'TestPackage'.
Try Get-PSRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage)[Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# Note that Get-InstalledScript shows the prerelease version.
# If -RequiredVersion is not specified, all installed scripts will be displayed by Get-InstalledScript
```

Script de desinstalação irá remover a versão atual de um script quando - RequiredVersion não é fornecido.
Se - RequiredVersion for especificada e é uma versão de pré-lançamento, - AllowPrerelease tem de ser adicionado ao comando.

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-script


C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
# Since script versions are not installed side-by-side, the above could be simply "Uninstall-Script TestPackage"

C:\windows\system32> Get-Installedscript TestPackage
PackageManagement\Get-Package : No match was found for the specified search criteria and script names 'testpackage'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.5.0.0\PSModule.psm1:4088 char:9
+         PackageManagement\Get-Package @PSBoundParameters | Microsoft. ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...lets.GetPackage:GetPackage) [Get-Package], Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.GetPackage
```

## <a name="more-details"></a>Obter mais detalhes

- [Versões de pré-lançamento do módulo](module-prerelease-support.md)
- [Find-script](/powershell/module/powershellget/find-script)
- [Script de instalação](/powershell/module/powershellget/install-script)
- [Save-script](/powershell/module/powershellget/save-script)
- [Script de atualização](/powershell/module/powershellget/update-script)
- [Get-Installedscript](/powershell/module/powershellget/get-installedscript)
- [Script de desinstalação](/powershell/module/powershellget/uninstall-script)
