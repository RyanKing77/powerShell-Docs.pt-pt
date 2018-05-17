---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: jianyunt, quoctruong
title: Melhorias na gestão de pacotes no WMF 5.1
ms.openlocfilehash: 1ebd574bd98a056de634ac688244813c1947618e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="improvements-to-package-management-in-wmf-51"></a>Melhorias na gestão de pacotes no WMF 5.1#

## <a name="improvements-in-packagemanagement"></a>Melhoramentos na PackageManagement ##
Seguem-se as correções efetuadas 5.1 o WMF:

### <a name="version-alias"></a>Alias de versão

**Cenário**: Se tiver a versão 1.0 e 2.0 de um pacote, P1, instalados no seu sistema e pretender desinstalar a versão 1.0, executaria `Uninstall-Package -Name P1 -Version 1.0` e esperam versão 1.0 ser desinstaladas depois de executar o cmdlet. No entanto o resultado é que a versão 2.0 obtém desinstalada.

Isto ocorre porque o `-Version` parâmetro é um alias do `-MinimumVersion` parâmetro. Quando PackageManagement está à procura de um pacote com a versão mínima do 1.0 qualificado, devolve a versão mais recente. Este comportamento é esperado em casos normais porque localizar que a versão mais recente é normalmente o resultado pretendido. No entanto, não deve aplicar ao `Uninstall-Package` maiúsculas e minúsculas.

**Solução**: remover `-Version` alias inteiramente no PackageManagement (a.k.a. OneGet) e PowerShellGet.

### <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a>Vários pedidos para bootstrapping o fornecedor do NuGet

**Cenário**: ao executar `Find-Module` ou `Install-Module` ou outros cmdlets PackageManagement no seu computador pela primeira vez, PackageManagement tenta arranque o fornecedor do NuGet. Fazê-lo porque o fornecedor de PowerShellGet também utiliza o fornecedor do NuGet para transferir os módulos do PowerShell. PackageManagement, em seguida, pede ao utilizador permissão instalar o fornecedor do NuGet. Depois do utilizador seleciona "Sim" para o bootstrapping, será instalada a versão mais recente do fornecedor do NuGet.

No entanto, em alguns casos, quando tem uma versão antiga do fornecedor de NuGet instalada no seu computador, a versão mais antiga do NuGet, por vezes, obtém carregar o primeiro na sessão do PowerShell (que é a condição provável de antecipação no PackageManagement). No entanto PowerShellGet requer a versão posterior do fornecedor do NuGet para funcionar, por isso PowerShellGet pede PackageManagement arranque novamente o fornecedor do NuGet. Isto resulta em vários pedidos para bootstrapping o fornecedor do NuGet.

**Solução**: no WMF5.1, PackageManagement carrega a versão mais recente do fornecedor do NuGet para evitar várias pede bootstrapping o fornecedor do NuGet.

Foi também contornar este problema, eliminando manualmente a antiga versão do fornecedor do NuGet (NuGet-Anycpu.exe) se existe entre a $env: ProgramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies


### <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a>Suporte para PackageManagement em computadores com o acesso apenas à Intranet

**Cenário**: para o cenário da empresa, as pessoas estão a funcionar num ambiente onde exista sem acesso à Internet, Intranet, mas apenas. PackageManagement não suportava neste caso, WMF 5.0.

**Cenário**: WMF 5.0, PackageManagement não suporta computadores que têm apenas Intranet (mas não Internet) acesso.

**Solução**: no WMF 5.1, pode seguir estes passos para permitir que os computadores de Intranet utilizar PackageManagement:

1. Transferir o fornecedor do NuGet através de outro computador que tenha uma ligação à Internet utilizando `Install-PackageProvider -Name NuGet`.

2. Localize o fornecedor do NuGet sob um `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` ou `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.

3. Copiar os binários para uma localização de partilha de rede ou de pasta que o computador de Intranet pode aceder e, em seguida, instale o fornecedor de NuGet com `Install-PackageProvider -Name NuGet -Source <Path to folder>`.


### <a name="event-logging-improvements"></a>Melhoramentos do registo de eventos

Quando instalar pacotes, está a alterar o estado do computador. No WMF 5.1, PackageManagement agora os registos de eventos no registo de eventos do Windows para `Install-Package`, `Uninstall-Package`, e `Save-Package` atividades. O registo de eventos é igual PowerShell, ou seja, `Microsoft-Windows-PowerShell, Operational`.

### <a name="support-for-basic-authentication"></a>Suporte para a autenticação básica

Em WMF 5.1, PackageManagement suporta localizar e instalar pacotes de um repositório de que requer autenticação básica. Pode fornecer as suas credenciais para o `Find-Package` e `Install-Package` cmdlets. Por exemplo:

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
### <a name="support-for-using-packagemanagement-behind-a-proxy"></a>Suporte para utilização PackageManagement atrás de um proxy

No WMF 5.1, PackageManagement demora agora novos parâmetros de proxy `-ProxyCredential` e `-Proxy`. Utilizar estes parâmetros, pode especificar o URL de proxy e as credenciais para PackageManagement cmdlets. Por predefinição, são utilizadas as definições de proxy do sistema. Por exemplo:

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```
