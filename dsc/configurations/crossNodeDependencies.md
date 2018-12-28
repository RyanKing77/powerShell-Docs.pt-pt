---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Especificar dependências entre nós
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404683"
---
# <a name="specifying-cross-node-dependencies"></a>Especificar dependências entre nós

> Aplica-se a: Windows PowerShell 5.0

DSC fornece recursos especiais, **WaitForAll**, **WaitForAny**, e **WaitForSome** que podem ser utilizados em configurações para especificar dependências em configurações de si nós. O comportamento desses recursos é o seguinte:

- **WaitForAll**: É bem-sucedida se o recurso especificado está no Estado desejado em todos os nós de destino definido no **NodeName** propriedade.
- **WaitForAny**: É bem-sucedida se o recurso especificado está no Estado desejado em, pelo menos, um de nós de destino definidos no **NodeName** propriedade.
- **WaitForSome**: Especifica um **NodeCount** propriedade além um **NodeName** propriedade. O recurso é bem-sucedida se o recurso está no Estado desejado num número mínimo de nós (especificado pelo **NodeCount**) definidos pela **NodeName** propriedade.

## <a name="syntax"></a>Sintaxe

O **WaitForAll** e **WaitForAny** recursos compartilham a mesma sintaxe. Substitua \<ResourceType\> no exemplo abaixo com ambos **WaitForAny** ou **WaitForAll**.
Como o **DependsOn** palavra-chave, precisará formatar o nome como "ResourceName [ResourceType]". Se o recurso pertence a um separado [Configuration](configurations.md), inclua o **ConfigurationName** na cadeia de caracteres formatada "ResourceName [ResourceType]:: [ConfigurationName]:: [ConfigurationName]". O **NodeName** é o computador ou o nó, no qual o recurso atual deve aguardar.

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

O **WaitForSome** recurso tem uma sintaxe semelhante ao exemplo acima, mas adiciona a **NodeCount** chave. O **NodeCount** indica quantos nós o recurso atual deve aguardar.

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

Todos os **WaitForXXXX** partilhar as seguintes chaves de sintaxe.

|  Propriedade |  Descrição | | RetryIntervalSec | O número de segundos antes de tentar novamente. Mínimo é 1. | | RetryCount | O número máximo de vezes a repetir. | | ThrottleLimit | Número de máquinas para se conectar simultaneamente. A predefinição é `New-CimSession` predefinido. | | DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Para obter mais informações, consulte [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | Consulte [com DSC com as credenciais de utilizador](./runAsUser.md) |


## <a name="using-waitforxxxx-resources"></a>Usando os recursos de WaitForXXXX

Cada **WaitForXXXX** recurso aguarda para que os recursos especificados concluir no nó especificado. Outros recursos na mesma configuração podem então *dependem* a **WaitForXXXX** usando o recurso a **DependsOn** chave.

Por exemplo, a configuração seguinte, o nó de destino está a aguardar a **xADDomain** seja concluído dentro do **Meucd** nó com o número máximo de 30 repete, em intervalos de 15 segundos, antes de nó de destino pode ingressar no domínio.

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

Quando compilar a configuração, são gerados dois arquivos ". MOF". Aplicam-se ambos os ficheiros de ". MOF" para os nós de destino com o [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet

>**Nota:** Por predefinição o WaitForXXX recursos tente uma vez e, em seguida, falharem. Embora não seja necessário, normalmente, deverá especificar um **RetryCount** e **RetryIntervalSec**.

## <a name="see-also"></a>Consulte Também

- [Configurações de DSC](configurations.md)
- [Utilizar as dependências de recursos](resource-depends-on.md)
- [Recursos de DSC](../resources/resources.md)
- [Configurar o Gestor de configuração Local](../managing-nodes/metaConfig.md)
