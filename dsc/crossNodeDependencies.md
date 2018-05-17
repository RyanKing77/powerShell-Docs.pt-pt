---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Especificar dependências entre nós
ms.openlocfilehash: c1802d6baa1f2b3449603e0374a83e213abf598e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="specifying-cross-node-dependencies"></a>Especificar dependências entre nós

> Aplica-se a: O Windows PowerShell 5.0

O DSC fornece recursos especiais, **WaitForAll**, **WaitForAny**, e **WaitForSome** que podem ser utilizados em configurações para especificar dependências em configurações de si nós. O comportamento destes recursos é o seguinte:

* **WaitForAll**: for bem sucedida se o recurso especificado está no estado pretendido em todos os nós de destino definido no **NodeName** propriedade.
* **WaitForAny**: for bem sucedida se o recurso especificado está no estado pretendido, pelo menos, um de nós de destino definidos no **NodeName** propriedade.
* **WaitForSome**: Especifica um **NodeCount** propriedade além um **NodeName** propriedade. O recurso for bem sucedida se o recurso está no estado pretendido de um número mínimo de nós (especificada por **NodeCount**) definidos pelo **NodeName** propriedade.

## <a name="using-waitforxxxx-resources"></a>Utilizar recursos WaitForXXXX

Para utilizar o **WaitForXXXX** recursos, cria um bloco de recursos desse tipo de recurso que especifica os recursos de DSC e nós de aguardar. Em seguida, utilize o **DependsOn** bloqueia a propriedade de quaisquer outros recursos na sua configuração de aguardar que as condições especificadas no **WaitForXXXX** nó seja bem sucedida.

Por exemplo, a configuração seguinte, o nó de destino está a aguardar o **xADDomain** recursos para concluir no **Meucd** nó com o número máximo de 30 repete, em intervalos de 15 segundo, antes de nó de destino pode associar ao domínio.

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

>**Nota:** por predefinição o WaitForXXX recursos tente uma vez e, em seguida, falhar. Embora não seja necessário, normalmente, irá querer Especifique um intervalo entre tentativas e uma contagem.

## <a name="see-also"></a>Consulte Também
* [Configurações de DSC](configurations.md)
* [Recursos de DSC](resources.md)
* [Configurar o Gestor de configuração Local](metaConfig.md)