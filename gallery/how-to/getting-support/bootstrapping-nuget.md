---
ms.date: 06/12/2017
contributor: manikb
keywords: cmdlet do powershell do galeria, psget
title: Efetuar o arranque do NuGet
ms.openlocfilehash: 2d321097fda201c0d8f843b2194a161eceabe4e1
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094022"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a>Inicializar o fornecedor NuGet e NuGet.exe

NuGet.exe não está incluído no fornecedor mais recente do NuGet.
Para operações de um módulo ou o script de publicação, PowerShellGet requer o NuGet.exe executável binário.
Apenas o fornecedor de NuGet é necessário para todas as outras operações, incluindo *encontrar*, *instalar*, *guardar*, e *desinstalar*.
O PowerShellGet inclui lógica para lidar com qualquer um combinado fazer a inicialização do fornecedor NuGet e NuGet.exe ou o arranque de apenas o fornecedor do NuGet.
Em ambos os casos, deve ocorrer apenas uma única mensagem de linha de comandos.
Se a máquina não estiver ligada à Internet, o utilizador ou um administrador tem de copiar uma instância fidedigna do fornecedor NuGet e/ou o ficheiro de NuGet.exe para a máquina desligada.

> [!NOTE]
> A partir da versão 6, o fornecedor de NuGet está incluído na instalação do PowerShell. [http://github.com/powershell/powershell](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a>Resolver o erro quando o fornecedor de NuGet não foi instalado num computador que é a Internet ligado

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ Find-Module -Repository PSGallery -Verbose -Name Contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module
```

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Resolver o erro quando o fornecedor de NuGet estiver disponível e NuGet.exe não está disponível durante a operação de publicação num computador que está a Internet ligado

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Resolver o erro quando o fornecedor NuGet e NuGet.exe não estão disponíveis durante a operação de publicação num computador que está a Internet ligado

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed and NuGet.exe is available under
one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetBinaries,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a>O fornecedor do NuGet numa máquina que não está ligado à Internet de inicialização manualmente

Os processos demonstrados acima partem do princípio da máquina está conectada à Internet e pode transferir os ficheiros de um local público.
Se não for possível, a única opção é inicializar uma máquina com os processos indicados acima e copie manualmente o fornecedor para o nó isolado através de um processo offline de confiança.
O caso de uso mais comum para este cenário é quando uma galeria privada está disponível para suportar um ambiente isolado.

Depois de seguir o processo acima para inicializar um computador de ligado à Internet, encontrará os ficheiros de fornecedor na localização:

```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

A estrutura de pasta/ficheiro do fornecedor NuGet será (possivelmente com um número de versão diferentes):

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

Copie estas pastas e ficheiros através de um processo fidedigno para as máquinas offline.

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a>Manualmente de inicialização NuGet.exe para suportar operações num computador que não está ligado à Internet de publicação

Além do processo para iniciar manualmente o fornecedor do NuGet, se a máquina será utilizada para publicar módulos ou scripts numa galeria privada utilizando o `Publish-Module` ou `Publish-Script` cmdlets, o arquivo executável binário do NuGet.exe será necessário.

O caso de uso mais comum para este cenário é quando uma galeria privada está disponível para suportar um ambiente isolado.
Existem duas opções para obter o ficheiro de NuGet.exe.

É uma opção inicializar uma máquina que está ligados à Internet e copie os ficheiros para as máquinas offline usando um processo fidedigno.
Depois de efetuar o arranque do computador ligado à Internet, o binário NuGet.exe estarão localizado em uma das duas pastas:

Se o `Publish-Module` ou `Publish-Script` cmdlets foram executados com permissões elevadas (como administrador):

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Se os cmdlets foram executados como um utilizador sem permissões elevadas:

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

Uma segunda opção consiste em transferir NuGet.exe a partir do site da NuGet.Org: [ https://dist.nuget.org/index.html ](https://www.nuget.org/downloads) ao selecionar uma versão de Preciosidade para máquinas de produção, certifique-se de que é posterior à 2.8.5.208 e identificar a versão que foi intitulada " recomendado".
Lembre-se desbloquear o ficheiro se este foi transferido através de um browser.
Isto pode ser efetuado utilizando o `Unblock-File` cmdlet.

Em ambos os casos, o ficheiro de NuGet.exe pode ser copiado para qualquer localização no `$env:path`, mas os locais padrão são:

Para disponibilizar o executável para que todos os utilizadores possam utilizar `Publish-Module` e `Publish-Script` cmdlets:

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Para disponibilizar o executável para apenas um utilizador específico, copiar para a localização dentro de apenas do perfil do usuário:

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```