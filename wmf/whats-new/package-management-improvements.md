---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Melhorias na gestão de pacotes no WMF 5.1
ms.openlocfilehash: 24ff05d6bf5993826106f1a1d2cee6dad363d1e2
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856162"
---
# <a name="improvements-to-package-management-in-wmf-51"></a>Melhorias na gestão de pacotes no WMF 5.1

Seguem-se as correções feitas no WMF 5.1:

## <a name="version-alias"></a>Alias de versão

**Cenário**: Se tiver a versão 1.0 e 2.0 de um pacote, P1, instalada no seu sistema e pretender desinstalar a versão 1.0, executaria `Uninstall-Package -Name P1 -Version 1.0` e esperar que a versão 1.0 para ser desinstaladas depois de executar o cmdlet. No entanto será desinstalada o resultado é que a versão 2.0.

Isto ocorre porque o `-Version` parâmetro é um alias do `-MinimumVersion` parâmetro. Quando PackageManagement está à procura de um pacote qualificado com a versão mínima do 1.0, ele retorna a versão mais recente. Este comportamento é esperado em casos normais, uma vez que encontrar que a versão mais recente é normalmente o resultado desejado. No entanto, não deve aplicar ao `Uninstall-Package` caso.

**Solução**: removido `-Version` alias inteiramente no PackageManagement (também conhecido como OneGet) e o PowerShellGet.

## <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a>Vários pedidos de arranque do sistema do fornecedor NuGet

**Cenário**: Quando executa `Find-Module` ou `Install-Module` ou outros cmdlets PackageManagement no seu computador pela primeira vez, PackageManagement tentar inicializar o fornecedor de NuGet. Ele faz isso porque o fornecedor do PowerShellGet também utiliza o fornecedor de NuGet para transferir os módulos do PowerShell.
PackageManagement, em seguida, pede ao utilizador permissão instalar o fornecedor de NuGet. Depois do usuário selecionar "Sim" para o arranque do sistema, será instalada a versão mais recente do fornecedor NuGet.

No entanto, em alguns casos, quando tem uma versão antiga do fornecedor NuGet instalado no seu computador, a versão mais antiga do NuGet, às vezes, é carregada primeiro para a sessão do PowerShell (ou seja, a condição de corrida em PackageManagement). No entanto o PowerShellGet requer a versão posterior do fornecedor NuGet para trabalhar, para que o PowerShellGet pede PackageManagement para inicializar o fornecedor de NuGet novamente.
Isso resulta em vários pedidos de arranque do sistema do fornecedor NuGet.

**Solução**: No WMF5.1, PackageManagement carrega a versão mais recente do fornecedor NuGet para evitar várias avisos para efetuar o arranque do fornecedor de NuGet.

Poderia também contornar este problema ao eliminar manualmente a versão antiga do fornecedor NuGet (NuGet-Anycpu.exe) se existe entre a $env: ProgramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies

## <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a>Suporte para PackageManagement em computadores com o acesso apenas à Intranet

**Cenário**: Para o cenário da empresa, as pessoas estão a funcionar num ambiente onde há sem acesso à Internet, Intranet, mas apenas. PackageManagement não oferecia suporte esse caso no WMF 5.0.

**Cenário**: No WMF 5.0, PackageManagement não oferecia suporte computadores que têm apenas Intranet (mas não a Internet) acesso.

**Solução**: No WMF 5.1, pode seguir estes passos para permitir que os computadores de Intranet utilizar PackageManagement:

1. Transferir o fornecedor do NuGet com outro computador que tenha uma ligação à Internet através da utilização `Install-PackageProvider -Name NuGet`.

2. Localizar o fornecedor do NuGet em qualquer um `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` ou `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.

3. Copiar os binários para uma localização de partilha de rede ou de pasta que o computador de Intranet pode acessar e, em seguida, instale o fornecedor de NuGet com `Install-PackageProvider -Name NuGet -Source <Path to folder>`.


## <a name="event-logging-improvements"></a>Melhorias de registo de eventos

Ao instalar pacotes, altera o estado do computador. No WMF 5.1, PackageManagement agora regista eventos no registo de eventos do Windows para `Install-Package`, `Uninstall-Package`, e `Save-Package` atividades. O registo de eventos é igual de PowerShell, ou seja, `Microsoft-Windows-PowerShell, Operational`.

## <a name="support-for-basic-authentication"></a>Suporte para a autenticação básica

No WMF 5.1, PackageManagement suporta localizar e instalar pacotes a partir de um repositório que requer a autenticação básica. Pode fornecer as suas credenciais para o `Find-Package` e `Install-Package` cmdlets. Por exemplo:

```powershell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```

## <a name="support-for-using-packagemanagement-behind-a-proxy"></a>Suporte para através do PackageManagement atrás de um proxy

No WMF 5.1, PackageManagement agora demora novos parâmetros de proxy `-ProxyCredential` e `-Proxy`. Usando esses parâmetros, pode especificar o URL de proxy e as credenciais para PackageManagement cmdlets. Por predefinição, são utilizadas as definições de proxy do sistema. Por exemplo:

```powershell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```
