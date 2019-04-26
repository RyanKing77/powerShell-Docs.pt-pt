---
ms.date: 11/06/2018
contributor: JKeithB
keywords: Galeria, powershell, cmdlet, psgallery, psget
title: Trabalhar com local PSRepositories
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084101"
---
# <a name="working-with-local-powershellget-repositories"></a>Trabalhar com repositórios locais do PowerShellGet

Os repositórios suporte do módulo PowerShellGet que se diferente da galeria do PowerShell.
Estes cmdlets permitem os cenários seguintes:

- Suporta um conjunto de módulos do PowerShell confiável e previamente validado para utilização no seu ambiente
- Um pipeline de CI/CD que cria módulos do PowerShell ou scripts de teste
- Fornecer scripts do PowerShell e módulos aos sistemas que não é possível aceder à internet

Este artigo descreve como configurar um repositório local do PowerShell. O artigo também abrange o [OfflinePowerShellGetDeploy][] módulo disponível a partir da galeria do PowerShell. Este módulo contém cmdlets para instalar a versão mais recente do PowerShellGet no seu repositório local.

## <a name="local-repository-types"></a>Tipos de repositório local

Existem duas formas de criar um PSRepository local: Partilha de servidor ou ficheiro de NuGet. Cada tipo tem vantagens e desvantagens:

Servidor do NuGet

| Vantagens| Desvantagens |
| --- | --- |
| Estreitamente imita a funcionalidade de PowerShellGallery | Aplicação de várias camada requer planeamento de operações e suporte |
| NuGet integra-se com o Visual Studio, outras ferramentas | Modelo de autenticação e gestão de contas do NuGet necessário |
| NuGet oferece suporte a metadados em `.Nupkg` pacotes | A publicação requer gerenciamento de chave de API e manutenção |
| Fornece pesquisa, administração de pacote, etc. | |

Partilha de ficheiros

| Vantagens| Desvantagens |
| --- | --- |
| Fácil de configurar, criar cópias de segurança e manter | Metadados usados pelo PowerShellGet não estão disponível |
| Modelo de segurança simples - permissões de utilizador na partilha | Nenhuma interface do Usuário para além da partilha de ficheiros básico |
| Sem restrições, como substituição de itens existentes | Segurança limitada e sem gravação de que atualiza o que |

O PowerShellGet funciona com o tipo e suporta a localizar as versões e a instalação da dependência.
No entanto, algumas funcionalidades que funcionam para a galeria do PowerShell não estão disponíveis para servidores de bases NuGet ou partilhas de ficheiros.

- Tudo o que é um pacote - sem diferenciação de scripts, módulos, recursos de DSC ou funcionalidades de função.
- Servidores de partilha de ficheiros não conseguem ver os metadados do pacote, incluindo etiquetas.

## <a name="creating-a-local-repository"></a>Criar um repositório local

O artigo seguinte lista os passos para configurar o seu próprio servidor do NuGet.

- [NuGet.Server][]

Siga os passos até ao ponto da adição de pacotes. Os passos para [publicando um pacote](#publishing-to-a-local-repository) serão abordadas mais adiante neste artigo.

Para um repositório baseadas em partilha de ficheiros, certifique-se de que os utilizadores têm permissões para aceder à partilha de ficheiros.

## <a name="registering-a-local-repository"></a>Registar um repositório local

Antes de um repositório pode ser utilizado, tem de ser registado com o `Register-PSRepository` comando.
Nos exemplos abaixo, o **InstallationPolicy** está definida como *fidedigna*, no pressuposto de que confia seu próprio repositório.

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

Tome nota da diferença entre a forma como os dois comandos processam **ScriptSourceLocation**. Para repositórios baseadas em partilha de ficheiros, o **SourceLocation** e **ScriptSourceLocation** tem de corresponder. Para um repositório baseada na web, têm de ser diferentes, por isso, neste exemplo, à direita "/" é adicionado para o **SourceLocation**.

Se pretender que o PSRepository recentemente criado para ser o repositório de predefinido, tem de anular o registo todos os outros PSRepositories. Por exemplo:

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> O nome do repositório 'PSGallery' está reservado para utilização da galeria do PowerShell. Pode anular o registo PSGallery, mas não é possível reutilizar o nome PSGallery para qualquer outro repositório.

Se tiver de restaurar o PSGallery, execute o seguinte comando:

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>Publicação de um repositório local

Assim que tiver registado a PSRepository local, pode publicar a sua PSRepository local. Existem dois cenários de publicação principais: publicar o seu próprio módulo e publicação de um módulo do PSGallery.

### <a name="publishing-a-module-you-authored"></a>Publicação de um módulo que criado

Uso `Publish-Module` e `Publish-Script` para publicar seu módulo para seu local PSRepository da mesma forma que para a galeria do PowerShell.

- Especifique a localização para o seu código
- Fornecer uma chave de API
- Especifique o nome do repositório. Por exemplo, `-PSRepository LocalPSRepo`

> [!NOTE]
> Tem de criar uma conta no servidor do NuGet, e inicie sessão gerar e salvar a chave de API.
> Para uma partilha de ficheiros, utilize qualquer cadeia não vazia para o valor de NuGetApiKey.

Exemplos:

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Para garantir a segurança, as chaves de API não devem ser codificada em scripts. Utilize um sistema de gestão de chaves segura.

### <a name="publishing-a-module-from-the-psgallery"></a>Publicação de um módulo do PSGallery

Para publicar um módulo do PSGallery para sua PSRepository local, pode utilizar o cmdlet Save-Package.

- Especifique o nome do pacote
- Especificar 'NuGet' como o fornecedor
- Especificar a localização de PSGallery como o (de origem https://www.powershellgallery.com/api/v2)
- Especifique o caminho para o seu repositório local

Exemplo:

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

Se sua PSRepository local é baseada na web, requer um passo adicional que utiliza nuget.exe para publicar.

Consulte a documentação para usar [nuget.exe][].

## <a name="installing-powershellget-on-a-disconnected-system"></a>Instalar o PowerShellGet num sistema desligado

Implantar o PowerShellGet é difícil em ambientes que necessitam de sistemas para ser desligado da internet. O PowerShellGet tem um processo de arranque que instala a versão mais recente na primeira vez que é utilizado. O módulo de OfflinePowerShellGetDeploy na galeria do PowerShell fornece cmdlets que oferecem suporte a esse processo de arranque de configuração.

Para inicializar uma implantação offline, terá de:

- Transferir e instalar o sistema de OfflinePowerShellGetDeploy sua ligação à internet e de seus sistemas desligados
- Baixe o PowerShellGet e suas dependências no sistema de ligação à internet com o `Save-PowerShellGetForOffline` cmdlet
- Copie o PowerShellGet e as respetivas dependências do sistema de ligação à internet para o sistema desligado
- Utilize o `Install-PowerShellGetOffline` no sistema desligado para colocar o PowerShellGet e as respetivas dependências para as pastas apropriadas

Os seguintes comandos utilização `Save-PowerShellGetForOffline` para colocar todos os componentes numa pasta `f:\OfflinePowerShellGet`

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Neste momento, tem de tornar o conteúdo do `F:\OfflinePowerShellGet` disponível para seus sistemas desconectados. Execute o `Install-PowerShellGetOffline` cmdlet para instalar o PowerShellGet no sistema desligado.

> [!NOTE]
> É importante que não execute o PowerShellGet na sessão do PowerShell antes de executar estes comandos. Uma vez PowerShellGet é carregado para a sessão, não não possível atualizar os componentes. Se iniciar o PowerShellGet por engano, sair e reiniciar o PowerShell.

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Depois de executar estes comandos, está pronto para publicar o PowerShellGet ao seu repositório local.

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Para garantir a segurança, as chaves de API não devem ser codificada em scripts. Utilize um sistema de gestão de chaves segura.

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
