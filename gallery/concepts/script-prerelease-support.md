---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: Versões de pré-lançamento de scripts
ms.openlocfilehash: 2c7e1cbc352f8dc39fef9cd968b2f0c1964c30b3
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/10/2018
---
# <a name="prerelease-versions-of-scripts"></a>Versões de pré-lançamento de scripts

A partir da versão 1.6.0, PowerShellGet e galeria do PowerShell fornecem suporte para marcação maiores 1.0.0 como uma pré-lançamento versões. Antes desta funcionalidade, os itens de pré-lançamento foram limitadas ao facto de ter um início de versão com 0. O objetivo destas funcionalidades é oferecem maior suporte para [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) Convenção de controlo de versões sem ultrapassar efeitos de compatibilidade com o PowerShell versões existentes e 3 ou acima versões do PowerShellGet. Este tópico centra-se as funcionalidades específicas do script. As funcionalidades equivalentes para módulos são no [versões do módulo de pré-lançamento](module-prerelease-support.md) tópico. Utilizar estas funcionalidades, publicadores podem identificar um script como versão 2.5.0-alpha e mais tarde na versão de um prontos para produção 2.5.0 que substitui a versão de pré-lançamento.

Um nível elevado, as funcionalidades de pré-lançamento script incluem:

- Adicionar um sufixo de PrereleaseString para a cadeia de versão no manifesto de script. Quando os scripts for publicado na galeria do PowerShell, estes dados são extraídos do manifesto e utilizados para identificar os itens de pré-lançamento.
- Adquirir itens pré-lançamento exija a adição de sinalizador - AllowPrerelease para os comandos de PowerShellGet Script localizar, Script de instalação, Script de atualização e o Script de guardar. Se não for especificado o sinalizador, itens de pré-lançamento não serão apresentados.
- Versões de script apresentadas localizar-o script Get-InstalledScript e na galeria do PowerShell serão apresentadas com PrereleaseString, tal como em 2.5.0-alpha.

Detalhes para as funcionalidades são incluídos abaixo.

## <a name="identifying-a-script-version-as-a-prerelease"></a>Identificar uma versão do script como uma pré-lançamento

Suporte de PowerShellGet para versões de pré-lançamento é mais fácil para os scripts de módulos. Controlo de versões do script só é suportado pelo PowerShellGet, pelo que existem não existem problemas de compatibilidade causados por adicionar a cadeia de pré-lançamento. Para identificar um script na galeria do PowerShell como uma pré-lançamento, adicione um sufixo de pré-lançamento para uma cadeia de versão corretamente formatado nos metadados do script.

Uma secção de exemplo de um manifesto de script com uma versão de pré-lançamento deverá ter o seguinte aspeto:

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>

```

Para utilizar um sufixo de pré-lançamento, a cadeia de versão tem de cumprir os seguintes requisitos:

- Só pode ser especificado um sufixo de pré-lançamento quando a versão 3 segmentos para major.
  Isto está alinhada com SemVer v1.0.0
- O sufixo de pré-lançamento é uma cadeia que começa com um hífen e pode conter ASCII alphanumerics [0-9A-Za - z-]
- Cadeias de pré-lançamento apenas SemVer v1.0.0 são suportadas neste momento, por isso, o sufixo de pré-lançamento __tem não__ conter qualquer período ou + [. +], que são permitidos em SemVer 2.0
- Exemplos de cadeias de PrereleaseString suportadas são:-alpha, - alpha1,-BETA, - update20171020

__Impacto de controlo de versões de pré-lançamento nas pastas de instalação e a ordem de ordenação__

Sequência de ordenação alterações ao utilizar uma versão de pré-lançamento, que é importante quando publicar a galeria do PowerShell, e quando a instalação de scripts com PowerShellGet comandos. Se dois scripts versões com o número de versão existe, a sequência de ordenação baseia-se na parte de cadeia seguir o hífen. Por isso, versão 2.5.0-alpha é inferior ao 2.5.0-beta, que é inferior ao 2.5.0-gamma. Se dois scripts têm o mesmo número de versão e apenas um tiver um PrereleaseString, o script __sem__ o sufixo de pré-lançamento é pressupõe-se que a versão de prontos para produção e irá ser ordenado como uma versão superior que o pré-lançamento versão. Por exemplo, quando a comparação com versões 2.5.0 e 2.5.0-beta, o 2.5.0 versão será considerada superior dos dois.

Quando publicar a galeria do PowerShell, por predefinição a versão do script a ser publicado tem de ter uma versão superior que qualquer versão anteriormente publicado na galeria do PowerShell. Um fabricante poderá atualizar versão 2.5.0-alpha 2.5.0-beta ou com 2.5.0 (com o sufixo não pré-lançamento).

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a>Encontrar e adquirir itens pré-lançamento utilizando comandos de PowerShellGet

Lidar com itens de pré-lançamento utilizando o Script-PowerShellGet localizar Script, Script de instalação, atualização, e os comandos de Script de guardar necessita de adicionar o sinalizador - AllowPrerelease. Se não for especificado - AllowPrerelease, itens de pré-lançamento será incluídos, se estiverem presentes. Se não for especificado o sinalizador - AllowPrerelease, itens de pré-lançamento não serão apresentados.

As únicas exceções a este nos comandos de script PowerShellGet são Get-InstalledScript e alguns casos com Script de desinstalação.

- Get-InstalledScript sempre automaticamente mostrará as informações de pré-lançamento na cadeia de versão se estiver presente.
- Script de desinstalação irá por predefinição desinstalar a versão mais recente de um script, se __nenhuma versão__ está especificado. Se o comportamento não foi alterado. No entanto, se não for especificada uma versão de pré-lançamento utilizando - RequiredVersion, - AllowPrerelease será necessário.

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
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
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
Se - RequiredVersion for especificado, não sendo uma pré-lançamento, - AllowPrerelease tem de ser adicionado ao comando.

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

## <a name="more-details"></a>obter mais detalhes

- [Versões de pré-lançamento do módulo](module-prerelease-support.md)
- [Encontrar o script](/powershell/module/powershellget/find-script)
- [Script de instalação](/powershell/module/powershellget/install-script)
- [Script de guardar](/powershell/module/powershellget/save-script)
- [Script de atualização](/powershell/module/powershellget/update-script)
- [Get-Installedscript](/powershell/module/powershellget/get-installedscript)
- [Script de desinstalação](/powershell/module/powershellget/uninstall-script)