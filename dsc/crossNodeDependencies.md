---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Especificar dependências entre nós"
ms.openlocfilehash: f4411161d819d96803f57600646409d5bfe827b9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="0087e-103">Especificar dependências entre nós</span><span class="sxs-lookup"><span data-stu-id="0087e-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="0087e-104">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0087e-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="0087e-105">O DSC fornece recursos especiais, **WaitForAll**, **WaitForAny**, e **WaitForSome** que podem ser utilizados em configurações para especificar dependências em configurações de si nós.</span><span class="sxs-lookup"><span data-stu-id="0087e-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="0087e-106">O comportamento destes recursos é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0087e-106">The behavior of these resources is as follows:</span></span>

* <span data-ttu-id="0087e-107">**WaitForAll**: for bem sucedida se o recurso especificado está no estado pretendido em todos os nós de destino definido no **NodeName** propriedade.</span><span class="sxs-lookup"><span data-stu-id="0087e-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="0087e-108">**WaitForAny**: for bem sucedida se o recurso especificado está no estado pretendido, pelo menos, um de nós de destino definidos no **NodeName** propriedade.</span><span class="sxs-lookup"><span data-stu-id="0087e-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="0087e-109">**WaitForSome**: Especifica um **NodeCount** propriedade além um **NodeName** propriedade.</span><span class="sxs-lookup"><span data-stu-id="0087e-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="0087e-110">O recurso for bem sucedida se o recurso está no estado pretendido de um número mínimo de nós (especificada por **NodeCount**) definidos pelo **NodeName** propriedade.</span><span class="sxs-lookup"><span data-stu-id="0087e-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="0087e-111">Utilizar recursos WaitForXXXX</span><span class="sxs-lookup"><span data-stu-id="0087e-111">Using WaitForXXXX resources</span></span>

<span data-ttu-id="0087e-112">Para utilizar o **WaitForXXXX** recursos, cria um bloco de recursos desse tipo de recurso que especifica os recursos de DSC e nós de aguardar.</span><span class="sxs-lookup"><span data-stu-id="0087e-112">To use the **WaitForXXXX** resources, you create a resource block of that resource type that specifies the DSC resource and node(s) to wait for.</span></span> <span data-ttu-id="0087e-113">Em seguida, utilize o **DependsOn** bloqueia a propriedade de quaisquer outros recursos na sua configuração de aguardar que as condições especificadas no **WaitForXXXX** nó seja bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0087e-113">You then use the **DependsOn** property in any other resource blocks in your configuration to wait for the conditions specified in the **WaitForXXXX** node to succeed.</span></span>

<span data-ttu-id="0087e-114">Por exemplo, a configuração seguinte, o nó de destino está a aguardar o **xADDomain** recursos para concluir no **Meucd** nó com o número máximo de 30 repete, em intervalos de 15 segundo, antes de nó de destino pode associar ao domínio.</span><span class="sxs-lookup"><span data-stu-id="0087e-114">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

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

><span data-ttu-id="0087e-115">**Nota:** por predefinição o WaitForXXX recursos tente uma vez e, em seguida, falhar.</span><span class="sxs-lookup"><span data-stu-id="0087e-115">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="0087e-116">Embora não seja necessário, normalmente, irá querer Especifique um intervalo entre tentativas e uma contagem.</span><span class="sxs-lookup"><span data-stu-id="0087e-116">Although it is not required, you will typically want to specify a retry interval and count.</span></span>

## <a name="see-also"></a><span data-ttu-id="0087e-117">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="0087e-117">See Also</span></span>
* [<span data-ttu-id="0087e-118">Configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="0087e-118">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="0087e-119">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="0087e-119">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="0087e-120">Configurar o Gestor de configuração Local</span><span class="sxs-lookup"><span data-stu-id="0087e-120">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

