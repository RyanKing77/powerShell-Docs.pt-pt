---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Importar uma versão específica de um recurso instalado
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404689"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a>Importar uma versão específica de um recurso instalado

> Aplica-se a: Windows PowerShell 5.0

No PowerShell 5.0, as versões separadas de recursos de DSC podem ser instaladas num computador lado a lado. Um módulo de recursos pode armazenar separadas versões de um recurso na versão pastas nomeada.

## <a name="installing-separate-resource-versions-side-by-side"></a>Instalação de recursos separado versões lado a lado

Pode utilizar o **MinimumVersion**, **MaximumVersion**, e **RequiredVersion** parâmetros do [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet para especificar qual é a versão de um módulo para instalar. A invocar **Install-Module** sem especificar uma versão instala a versão mais recente.

Por exemplo, há várias versões dos **xFailOverCluster** módulo, cada um contendo uma **xCluster** recursos. A invocar **Install-Module** sem especificar a versão número instala a versão mais recente do módulo.

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Para instalar uma versão específica de um módulo, especificar um **RequiredVersion** de 1.1.0.0. Esta ação instala a versão especificada lado a lado com a versão instalada.

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

Agora, vê a versão do módulo listados quando utiliza `Get-DSCResource`.

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>Especificar uma versão do recurso numa configuração

Se tiver versões de recursos separado instaladas num computador, tem de especificar a versão desse recurso quando usá-lo numa configuração. Fazê-lo ao especificar os **ModuleVersion** parâmetro do **Import-DscResource** palavra-chave. Se não especificar a versão de um módulo de recursos de um recurso que tem mais de uma versão instalada, a configuração gera um erro.

A configuração seguinte mostra como especificar a versão do recurso para chamar:

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

>Nota: O parâmetro de ModuleVersion do Import-DscResource não está disponível no PowerShell 4.0. No PowerShell 4.0, pode especificar uma versão do módulo, passando um objeto de especificação do módulo para o parâmetro ModuleName Import-DscResource. Um objeto de especificação do módulo é uma tabela de hash que contém as chaves de ModuleName e RequiredVersion. Por exemplo:

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

Isso também funciona no PowerShell 5.0, mas é recomendado que utilize o **ModuleVersion** parâmetro.

## <a name="see-also"></a>Consulte também

- [Configurações de DSC](configurations.md)
- [Recursos de DSC](../resources/resources.md)
