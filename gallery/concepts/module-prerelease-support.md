---
ms.date: 09/26/2017
contributor: keithb
keywords: cmdlet do powershell do galeria, psget
title: Versões de pré-lançamento do módulo
ms.openlocfilehash: 2a4fcd40353450e5ba03910984c5a05772a93d0d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189844"
---
# <a name="prerelease-module-versions"></a>Versões de pré-lançamento do módulo

A partir da versão 1.6.0, PowerShellGet e galeria do PowerShell fornecem suporte para marcação maiores 1.0.0 como uma pré-lançamento versões. Antes desta funcionalidade, os itens de pré-lançamento foram limitadas ao facto de ter um início de versão com 0. O objetivo destas funcionalidades é oferecem maior suporte para [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) Convenção de controlo de versões sem ultrapassar efeitos de compatibilidade com o PowerShell versões existentes e 3 ou acima versões do PowerShellGet. Este tópico centra-se as funcionalidades específicas do módulo. As funcionalidades equivalentes para os scripts estão no [versões de pré-lançamento de Scripts](script-prerelease-support.md) tópico. Utilizar estas funcionalidades, publicadores podem identificar um módulo ou script como versão 2.5.0-alpha e mais tarde na versão de um prontos para produção 2.5.0 que substitui a versão de pré-lançamento.

Um nível elevado, as funcionalidades de pré-lançamento módulo incluem:

- Adicionar uma cadeia de pré-lançamento à secção PSData do manifesto do módulo identifica o módulo como uma versão de pré-lançamento. Quando o módulo for publicado na galeria do PowerShell, estes dados são extraídos do manifesto e utilizados para identificar os itens de pré-lançamento.
- Adquirir itens pré-lançamento exija a adição de sinalizador - AllowPrerelease para os comandos de PowerShellGet módulo de encontrar o módulo de instalação, atualização módulo e o módulo de guardar. Se não for especificado o sinalizador, itens de pré-lançamento não serão apresentados.
- Serão apresentadas como uma cadeia única com a cadeia de pré-lançamento anexada, tal como em 2.5.0-alpha versões de módulo apresentadas pelo módulo de localizar, Get-InstalledModule e na galeria do PowerShell.

Detalhes para as funcionalidades são incluídos abaixo.

Estas alterações não afetam o suporte de versão do módulo que está incorporado no PowerShell e são compatíveis com o PowerShell 3.0, 4.0 e 5.

## <a name="identifying-a-module-version-as-a-prerelease"></a>Identificar uma versão do módulo como uma pré-lançamento

O suporte para versões de pré-lançamento PowerShellGet requer a utilização de dois campos no manifesto de módulo:

- ModuleVersion incluído no manifesto do módulo tem de ser uma versão 3 partes se for utilizada uma versão de pré-lançamento e deve ser compatível com controlo de versões existente do PowerShell. O formato de versão seria A.B.C, onde A, B e C estão todos os números inteiros.
- A cadeia de pré-lançamento é especificada no manifesto do módulo, na secção PSData PrivateData.

Os requisitos detalhados na cadeia de pré-lançamento estão abaixo.

Uma secção de exemplo de um manifesto de módulo que define um módulo como uma pré-lançamento seria o seguinte aspeto:

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

- Cadeia de pré-lançamento só pode ser especificada quando o ModuleVersion é 3 segmentos para major. Isto está alinhada com SemVer v1.0.0.
- Um hífen é o delimitador entre o número de compilação e a cadeia de pré-lançamento. Um hífen pode ser incluído na cadeia de pré-lançamento, como o primeiro caráter, apenas.
- A cadeia de pré-lançamento pode conter apenas ASCII alphanumerics [0-9A-Za - z-]. É uma melhor prática para iniciar a pré-lançamento cadeia com um caráter alfa, tal como será mais fácil de identificar que esta é uma versão de pré-lançamento quando efetua a análise de uma lista de itens.
- Apenas SemVer v1.0.0 pré-lançamento cadeias são suportadas neste momento. Cadeia de pré-lançamento __tem não__ conter qualquer um dos período ou + [. +], que são permitidos em SemVer 2.0.
- Exemplos de cadeias de pré-lançamento suportados são:-alpha, - alpha1,-BETA, - update20171020

__Impacto de controlo de versões de pré-lançamento nas pastas de instalação e a ordem de ordenação__

Sequência de ordenação é alterado quando utilizar uma versão de pré-lançamento, que é importante quando publicar a galeria do PowerShell, e quando instalar módulos com PowerShellGet comandos. Se a cadeia de pré-lançamento é especificada para dois módulos, a sequência de ordenação baseia-se na parte de cadeia seguir o hífen. Por isso, versão 2.5.0-alpha é inferior ao 2.5.0-beta, que é inferior ao 2.5.0-gamma. Se dois módulos tem o mesmo ModuleVersion e apenas um tiver uma cadeia de pré-lançamento, o módulo sem a cadeia de pré-lançamento é pressupõe-se que a versão de prontos para produção e irá ser ordenado como uma versão superior à versão de pré-lançamento (que inclui a pré-lançamento cadeia). Por exemplo, quando a comparação com versões 2.5.0 e 2.5.0-beta, o 2.5.0 versão será considerada superior dos dois.

Quando publicar a galeria do PowerShell, por predefinição a versão do módulo que está a ser publicado tem de ter uma versão superior que qualquer versão anteriormente publicado na galeria do PowerShell.

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a>Encontrar e adquirir itens pré-lançamento utilizando comandos de PowerShellGet

Lidar com itens de pré-lançamento utilizando PowerShellGet localizar-Module, módulo de instalação, atualização-Module, e necessita de comandos do módulo de guardar o sinalizador - AllowPrerelease a adicionar. Se não for especificado - AllowPrerelease, itens de pré-lançamento será incluídos, se estiverem presentes. Se não for especificado o sinalizador - AllowPrerelease, itens de pré-lançamento não serão apresentados.

As únicas exceções a este nos comandos módulo PowerShellGet são Get-InstalledModule e alguns casos com o módulo de desinstalação.

- Get-InstalledModule sempre automaticamente mostrará as informações de pré-lançamento na cadeia de versão para módulos.
- Módulo de desinstalação irá por predefinição desinstalar a versão mais recente de um módulo, se __nenhuma versão__ está especificado. Se o comportamento não foi alterado. No entanto, se não for especificada uma versão de pré-lançamento utilizando - RequiredVersion, - AllowPrerelease será necessário.

## <a name="examples"></a>Exemplos

```powershell
# Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> find-module TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

# To install a prerelease, always specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

Não é suportada a instalação lado a lado das versões de um módulo que diferem apenas devido a pré-lançamento especificada. Ao instalar um módulo com o PowerShellGet, versões diferentes do mesmo módulo são instalado do lado do lado a lado através da criação de um nome de pasta com o ModuleVersion. ModuleVersion, sem a cadeia de pré-lançamento, é utilizada para o nome da pasta. Se um utilizador instala MyModule versão 2.5.0-alpha, será instalado para a pasta de MyModule\2.5.0. Se o utilizador instala, em seguida, 2.5.0-beta, a versão de 2.5.0-beta será __escrita superior__ o conteúdo da pasta MyModule\2.5.0. Uma vantagem para esta abordagem é que não é necessário para desinstalar a versão de pré-lançamento depois de instalar a versão de prontos para produção. O exemplo abaixo mostra o que pode esperar:

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-beta     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

Módulo de desinstalação irá remover a versão mais recente de um módulo quando - RequiredVersion não é fornecido.
Se - RequiredVersion for especificado, não sendo uma pré-lançamento, - AllowPrerelease tem de ser adicionado ao comando.

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-Module



C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...


```

## <a name="more-details"></a>obter mais detalhes

- [Versões de pré-lançamento do Script](script-prerelease-support.md)
- [Encontrar o módulo](/powershell/module/powershellget/find-module)
- [Install-Module](/powershell/module/powershellget/install-module)
- [Save-Module](/powershell/module/powershellget/save-module)
- [Update-Module](/powershell/module/powershellget/Update-Module)
- [Get-InstalledModule](/powershell/module/powershellget/get-installedmodule)
- [Módulo desinstalar](/powershell/gallery/psget/module/psget_uninstall-module)