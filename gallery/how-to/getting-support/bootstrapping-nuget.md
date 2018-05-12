
---
MS. Date: 06/12/2017 contribuinte: MS. topic de manikb: referência de palavras-chave: cmdlet do powershell do galeria, psget título: Bootstrapping NuGet
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a>Arranque o fornecedor do NuGet e NuGet.exe

NuGet.exe não está incluído no fornecedor mais recente do NuGet.
Para publicar operações de um módulo ou script, PowerShellGet requer o binário NuGet.exe executável.
Apenas é necessário para todas as outras operações o fornecedor do NuGet, incluindo *localizar*, *instalar*, *guardar*, e *desinstalar*.
PowerShellGet inclui lógica para lidar com qualquer um combinado o arranque de configuração do fornecedor do NuGet e NuGet.exe ou o arranque de configuração de apenas o fornecedor do NuGet.
Em ambos os casos, deve ocorrer apenas uma única mensagem de pedido.
Se a máquina não estiver ligada à Internet, o utilizador ou um administrador tem de copiar uma instância do fornecedor de NuGet e/ou o ficheiro NuGet.exe fidedigna para a máquina desligada.

>**Tenha em atenção**: a partir da versão 6, o fornecedor do NuGet está incluído na instalação do PowerShell. [http://github.com/powershell/powershell](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a>Resolver erros quando o fornecedor do NuGet não foi instalado num computador onde é Internet ligado

```powershell
PS> Find-Module -Repository PSGallery -Verbose -Name Contoso

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

PS> Find-Module -Repository PSGallery -Verbose -Name Contoso

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

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Resolver erros quando o fornecedor do NuGet está disponível e NuGet.exe não está disponível durante a operação de publicar num computador onde é Internet ligado

```powershell
PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module

PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Resolver erros quando o fornecedor do NuGet e NuGet.exe não estão disponíveis durante a operação de publicar num computador onde é Internet ligado

```powershell
PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

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

PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a>Bootstrapping manualmente o fornecedor do NuGet num computador que não está ligado à Internet

Os processos demonstrados acima partem do princípio da máquina está ligada à Internet e pode transferir os ficheiros a partir de uma localização pública.
Se não for possível, é a única opção para arranque de uma máquina através de processos indicados acima e copiar manualmente o fornecedor para o nó isolado através de um processo offline fidedigno.
O caso de utilização mais comum para este cenário é quando uma galeria privada está disponível para suportar um ambiente isolado.

Depois de seguir o processo acima para arranque de um computador ligado à Internet, irá encontrar os ficheiros de fornecedor na localização:

```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

A estrutura de pasta/ficheiro do fornecedor do NuGet será (possivelmente com um número de versão diferentes):

NuGet<br>
-2.8.5.208<br>
---Microsoft.PackageManagement.NuGetProvider.dll

Copie estas pastas e ficheiros através de um processo fidedigno para as máquinas offline.

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a>Manualmente bootstrapping NuGet.exe para suportar a publicar operações num computador que não está ligado à Internet

Para além do processo de arranque manualmente o fornecedor do NuGet, se a máquina será utilizada para publicar módulos ou scripts para uma galeria privada utilizando o *publicar-Module* ou *publicar Script* cmdlets, ficheiro executável binário NuGet.exe será necessário.
O caso de utilização mais comum para este cenário é quando uma galeria privada está disponível para suportar um ambiente isolado.
Existem duas opções para obter o ficheiro NuGet.exe.

É uma opção de arranque de uma máquina que se ligadas à Internet e copie os ficheiros para as máquinas offline através de um processo fidedigno.
Após bootstrapping a máquina ligada à Internet, o binário NuGet.exe estarão localizado em uma das duas pastas:

Se o *publicar-Module* ou *publicar Script* cmdlets foram executados com permissões elevadas (como um administrador):

```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Se os cmdlets foram executados como um utilizador sem permissões elevadas:

```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

É uma segunda opção transferir NuGet.exe do Web site NuGet.Org: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)<br>
Quando selecionar uma versão de NugGet para máquinas de produção, certifique-se de que é posterior à 2.8.5.208 e identificar a versão que tenha sido com a etiqueta "recomendados".
Lembre-se desbloquear o ficheiro se este foi transferido utilizando um browser.
Isto pode ser efetuado utilizando o *desbloqueio ficheiro* cmdlet.

Em ambos os casos, o ficheiro NuGet.exe pode ser copiado para qualquer localização em *$env: caminho*, mas as localizações padrão são:

Para disponibilizar o executável para que todos os utilizadores possam utilizar *publicar-Module* e *publicar Script* cmdlets:

```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Para disponibilizar o ficheiro executável a apenas um utilizador específico, copiar para a localização dentro do perfil desse utilizador apenas:

```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```