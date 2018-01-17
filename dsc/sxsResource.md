---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Utilizar recursos com várias versões"
ms.openlocfilehash: 8bd8b1dab9418c6d8cf64cd682c527a7f039cdb4
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="using-resources-with-multiple-versions"></a>Utilizar recursos com várias versões

> Aplica-se a: O Windows PowerShell 5.0

No PowerShell 5.0, recursos de DSC podem ter várias versões e versões podem ser instaladas num computador do lado do lado a lado. Isto é implementado por ter várias versões de um módulo de recursos que estão contidas na mesma pasta do módulo.

## <a name="installing-multiple-resource-versions-side-by-side"></a>Instalar vários recursos versões do lado do lado a lado

Pode utilizar o **MinimumVersion**, **MaximumVersion**, e **RequiredVersion** parâmetros a [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet para especificar qual é a versão de um módulo para instalar. Chamar **Install-Module** sem especificar uma versão instala a versão mais recente.

Por exemplo, existem várias versões do **xFailOverCluster** módulo, cada um dos quais contém uma **xCluster** recurso. O resultado da chamada **Install-Module** sem especificar a versão número é o seguinte:

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Agora, se chamar **Install-Module** novamente, mas Especifica um **RequiredVersion** de 1.1.0.0, o que resulta no seguinte:

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>Especificar uma versão do recurso numa configuração

Se tiver vários recursos instalados num computador, tem de especificar a versão desse recurso quando utiliza uma configuração. Fazê-lo especificando o **ModuleVersion** parâmetro o **importação DscResource** palavra-chave. Se falhar especificar a versão de um módulo de recurso de um recurso de que tem mais do que uma versão instalada, a configuração gera um erro.

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

>Nota: O parâmetro ModuleVersion da importação DscResource não está disponível no PowerShell 4.0. No PowerShell 4.0, pode especificar uma versão do módulo através da transmissão de um objeto de especificação do módulo para o parâmetro ModuleName do DscResource de importação. Um objeto de especificação do módulo é uma tabela hash que contém chaves ModuleName e RequiredVersion. Por exemplo:

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

Isto também irá funcionar no PowerShell 5.0, mas é recomendado que utilize o **ModuleVersion** parâmetro.

## <a name="see-also"></a>Consulte também
* [Configurações de DSC](configurations.md)
* [Recursos de DSC](resources.md)

