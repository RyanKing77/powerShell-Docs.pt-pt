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
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="ca284-103">Especificar dependências entre nós</span><span class="sxs-lookup"><span data-stu-id="ca284-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="ca284-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ca284-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="ca284-105">DSC fornece recursos especiais, **WaitForAll**, **WaitForAny**, e **WaitForSome** que podem ser utilizados em configurações para especificar dependências em configurações de si nós.</span><span class="sxs-lookup"><span data-stu-id="ca284-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="ca284-106">O comportamento desses recursos é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ca284-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="ca284-107">**WaitForAll**: É bem-sucedida se o recurso especificado está no Estado desejado em todos os nós de destino definido no **NodeName** propriedade.</span><span class="sxs-lookup"><span data-stu-id="ca284-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="ca284-108">**WaitForAny**: É bem-sucedida se o recurso especificado está no Estado desejado em, pelo menos, um de nós de destino definidos no **NodeName** propriedade.</span><span class="sxs-lookup"><span data-stu-id="ca284-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="ca284-109">**WaitForSome**: Especifica um **NodeCount** propriedade além um **NodeName** propriedade.</span><span class="sxs-lookup"><span data-stu-id="ca284-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="ca284-110">O recurso é bem-sucedida se o recurso está no Estado desejado num número mínimo de nós (especificado pelo **NodeCount**) definidos pela **NodeName** propriedade.</span><span class="sxs-lookup"><span data-stu-id="ca284-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="ca284-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca284-111">Syntax</span></span>

<span data-ttu-id="ca284-112">O **WaitForAll** e **WaitForAny** recursos compartilham a mesma sintaxe.</span><span class="sxs-lookup"><span data-stu-id="ca284-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="ca284-113">Substitua \<ResourceType\> no exemplo abaixo com ambos **WaitForAny** ou **WaitForAll**.</span><span class="sxs-lookup"><span data-stu-id="ca284-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="ca284-114">Como o **DependsOn** palavra-chave, precisará formatar o nome como "ResourceName [ResourceType]".</span><span class="sxs-lookup"><span data-stu-id="ca284-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="ca284-115">Se o recurso pertence a um separado [Configuration](configurations.md), inclua o **ConfigurationName** na cadeia de caracteres formatada "ResourceName [ResourceType]:: [ConfigurationName]:: [ConfigurationName]".</span><span class="sxs-lookup"><span data-stu-id="ca284-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="ca284-116">O **NodeName** é o computador ou o nó, no qual o recurso atual deve aguardar.</span><span class="sxs-lookup"><span data-stu-id="ca284-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

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

<span data-ttu-id="ca284-117">O **WaitForSome** recurso tem uma sintaxe semelhante ao exemplo acima, mas adiciona a **NodeCount** chave.</span><span class="sxs-lookup"><span data-stu-id="ca284-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="ca284-118">O **NodeCount** indica quantos nós o recurso atual deve aguardar.</span><span class="sxs-lookup"><span data-stu-id="ca284-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

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

<span data-ttu-id="ca284-119">Todos os **WaitForXXXX** partilhar as seguintes chaves de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="ca284-119">All **WaitForXXXX** share the following syntax keys.</span></span>

<span data-ttu-id="ca284-120">|  Propriedade |  Descrição | | RetryIntervalSec | O número de segundos antes de tentar novamente.</span><span class="sxs-lookup"><span data-stu-id="ca284-120">|  Property  |  Description   | | RetryIntervalSec| The number of seconds before retrying.</span></span> <span data-ttu-id="ca284-121">Mínimo é 1. | | RetryCount | O número máximo de vezes a repetir. | | ThrottleLimit | Número de máquinas para se conectar simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="ca284-121">Minimum is 1.| | RetryCount| The maximum number of times to retry.| | ThrottleLimit| Number of machines to connect simultaneously.</span></span> <span data-ttu-id="ca284-122">A predefinição é `New-CimSession` predefinido. | | DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="ca284-122">Default is `New-CimSession` default.| | DependsOn | Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ca284-123">Para obter mais informações, consulte [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | Consulte [com DSC com as credenciais de utilizador](./runAsUser.md) |</span><span class="sxs-lookup"><span data-stu-id="ca284-123">For more information, see [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | See [Using DSC with User Credentials](./runAsUser.md) |</span></span>


## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="ca284-124">Usando os recursos de WaitForXXXX</span><span class="sxs-lookup"><span data-stu-id="ca284-124">Using WaitForXXXX resources</span></span>

<span data-ttu-id="ca284-125">Cada **WaitForXXXX** recurso aguarda para que os recursos especificados concluir no nó especificado.</span><span class="sxs-lookup"><span data-stu-id="ca284-125">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span> <span data-ttu-id="ca284-126">Outros recursos na mesma configuração podem então *dependem* a **WaitForXXXX** usando o recurso a **DependsOn** chave.</span><span class="sxs-lookup"><span data-stu-id="ca284-126">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="ca284-127">Por exemplo, a configuração seguinte, o nó de destino está a aguardar a **xADDomain** seja concluído dentro do **Meucd** nó com o número máximo de 30 repete, em intervalos de 15 segundos, antes de nó de destino pode ingressar no domínio.</span><span class="sxs-lookup"><span data-stu-id="ca284-127">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

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

<span data-ttu-id="ca284-128">Quando compilar a configuração, são gerados dois arquivos ". MOF".</span><span class="sxs-lookup"><span data-stu-id="ca284-128">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="ca284-129">Aplicam-se ambos os ficheiros de ". MOF" para os nós de destino com o [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span><span class="sxs-lookup"><span data-stu-id="ca284-129">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

><span data-ttu-id="ca284-130">**Nota:** Por predefinição o WaitForXXX recursos tente uma vez e, em seguida, falharem.</span><span class="sxs-lookup"><span data-stu-id="ca284-130">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="ca284-131">Embora não seja necessário, normalmente, deverá especificar um **RetryCount** e **RetryIntervalSec**.</span><span class="sxs-lookup"><span data-stu-id="ca284-131">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca284-132">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="ca284-132">See Also</span></span>

- [<span data-ttu-id="ca284-133">Configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="ca284-133">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="ca284-134">Utilizar as dependências de recursos</span><span class="sxs-lookup"><span data-stu-id="ca284-134">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="ca284-135">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="ca284-135">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="ca284-136">Configurar o Gestor de configuração Local</span><span class="sxs-lookup"><span data-stu-id="ca284-136">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
