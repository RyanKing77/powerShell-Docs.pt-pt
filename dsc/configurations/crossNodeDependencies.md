---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Especificar dependências entre nós
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734686"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="43448-103">Especificar dependências entre nós</span><span class="sxs-lookup"><span data-stu-id="43448-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="43448-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="43448-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="43448-105">DSC fornece recursos especiais, **WaitForAll**, **WaitForAny**, e **WaitForSome** que podem ser utilizados em configurações para especificar dependências em configurações de si nós.</span><span class="sxs-lookup"><span data-stu-id="43448-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="43448-106">O comportamento desses recursos é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="43448-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="43448-107">**WaitForAll**: É bem-sucedida se o recurso especificado está no Estado desejado em todos os nós de destino definido no **NodeName** propriedade.</span><span class="sxs-lookup"><span data-stu-id="43448-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="43448-108">**WaitForAny**: É bem-sucedida se o recurso especificado está no Estado desejado em, pelo menos, um de nós de destino definidos no **NodeName** propriedade.</span><span class="sxs-lookup"><span data-stu-id="43448-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="43448-109">**WaitForSome**: Especifica um **NodeCount** propriedade além um **NodeName** propriedade.</span><span class="sxs-lookup"><span data-stu-id="43448-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="43448-110">O recurso é bem-sucedida se o recurso está no Estado desejado num número mínimo de nós (especificado pelo **NodeCount**) definidos pela **NodeName** propriedade.</span><span class="sxs-lookup"><span data-stu-id="43448-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="43448-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43448-111">Syntax</span></span>

<span data-ttu-id="43448-112">O **WaitForAll** e **WaitForAny** recursos compartilham a mesma sintaxe.</span><span class="sxs-lookup"><span data-stu-id="43448-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="43448-113">Substitua \<ResourceType\> no exemplo abaixo com ambos **WaitForAny** ou **WaitForAll**.</span><span class="sxs-lookup"><span data-stu-id="43448-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="43448-114">Como o **DependsOn** palavra-chave, precisará formatar o nome como "ResourceName [ResourceType]".</span><span class="sxs-lookup"><span data-stu-id="43448-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="43448-115">Se o recurso pertence a um separado [Configuration](configurations.md), inclua o **ConfigurationName** na cadeia de caracteres formatada "ResourceName [ResourceType]:: [ConfigurationName]:: [ConfigurationName]".</span><span class="sxs-lookup"><span data-stu-id="43448-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="43448-116">O **NodeName** é o computador ou o nó, no qual o recurso atual deve aguardar.</span><span class="sxs-lookup"><span data-stu-id="43448-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

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

<span data-ttu-id="43448-117">O **WaitForSome** recurso tem uma sintaxe semelhante ao exemplo acima, mas adiciona a **NodeCount** chave.</span><span class="sxs-lookup"><span data-stu-id="43448-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="43448-118">O **NodeCount** indica quantos nós o recurso atual deve aguardar.</span><span class="sxs-lookup"><span data-stu-id="43448-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

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

<span data-ttu-id="43448-119">Todos os **WaitForXXXX** partilhar as seguintes chaves de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="43448-119">All **WaitForXXXX** share the following syntax keys.</span></span>

|<span data-ttu-id="43448-120">Propriedade</span><span class="sxs-lookup"><span data-stu-id="43448-120">Property</span></span>|  <span data-ttu-id="43448-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="43448-121">Description</span></span>   |
|---------|---------------------|
| <span data-ttu-id="43448-122">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="43448-122">RetryIntervalSec</span></span>| <span data-ttu-id="43448-123">O número de segundos antes de tentar novamente.</span><span class="sxs-lookup"><span data-stu-id="43448-123">The number of seconds before retrying.</span></span> <span data-ttu-id="43448-124">Mínimo é 1.</span><span class="sxs-lookup"><span data-stu-id="43448-124">Minimum is 1.</span></span>|
| <span data-ttu-id="43448-125">RetryCount</span><span class="sxs-lookup"><span data-stu-id="43448-125">RetryCount</span></span>| <span data-ttu-id="43448-126">O número máximo de vezes a repetir.</span><span class="sxs-lookup"><span data-stu-id="43448-126">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="43448-127">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="43448-127">ThrottleLimit</span></span>| <span data-ttu-id="43448-128">Número de máquinas para se conectar simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="43448-128">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="43448-129">A predefinição é `New-CimSession` padrão.</span><span class="sxs-lookup"><span data-stu-id="43448-129">Default is `New-CimSession` default.</span></span>|
| <span data-ttu-id="43448-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="43448-130">DependsOn</span></span> | <span data-ttu-id="43448-131">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="43448-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="43448-132">Para obter mais informações, consulte [DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="43448-132">For more information, see [DependsOn](resource-depends-on.md)</span></span>|
| <span data-ttu-id="43448-133">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="43448-133">PsDscRunAsCredential</span></span> | <span data-ttu-id="43448-134">Consulte [com DSC com as credenciais de utilizador](./runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="43448-134">See [Using DSC with User Credentials](./runAsUser.md)</span></span> |

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="43448-135">Usando os recursos de WaitForXXXX</span><span class="sxs-lookup"><span data-stu-id="43448-135">Using WaitForXXXX resources</span></span>

<span data-ttu-id="43448-136">Cada **WaitForXXXX** recurso aguarda para que os recursos especificados concluir no nó especificado.</span><span class="sxs-lookup"><span data-stu-id="43448-136">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span>
<span data-ttu-id="43448-137">Outros recursos na mesma configuração podem então *dependem* a **WaitForXXXX** usando o recurso a **DependsOn** chave.</span><span class="sxs-lookup"><span data-stu-id="43448-137">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="43448-138">Por exemplo, a configuração seguinte, o nó de destino está a aguardar a **xADDomain** seja concluído dentro do **Meucd** nó com o número máximo de 30 repete, em intervalos de 15 segundos, antes de nó de destino pode ingressar no domínio.</span><span class="sxs-lookup"><span data-stu-id="43448-138">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

<span data-ttu-id="43448-139">Por predefinição o **WaitForXXX** recursos tente uma vez e, em seguida, falhar.</span><span class="sxs-lookup"><span data-stu-id="43448-139">By default the **WaitForXXX** resources try one time and then fail.</span></span> <span data-ttu-id="43448-140">Embora não seja necessário, normalmente, deverá especificar um **RetryCount** e **RetryIntervalSec**.</span><span class="sxs-lookup"><span data-stu-id="43448-140">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

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

<span data-ttu-id="43448-141">Quando compilar a configuração, são gerados dois arquivos ". MOF".</span><span class="sxs-lookup"><span data-stu-id="43448-141">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="43448-142">Aplicam-se ambos os ficheiros de ". MOF" para os nós de destino com o [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span><span class="sxs-lookup"><span data-stu-id="43448-142">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

> [!NOTE]
> <span data-ttu-id="43448-143">**WaitForXXX** recursos utilizam a gestão remota do Windows para verificar o estado dos outros nós.</span><span class="sxs-lookup"><span data-stu-id="43448-143">**WaitForXXX** resources use Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="43448-144">Para obter mais informações sobre os requisitos de segurança e de porta para o WinRM, consulte [considerações de segurança de comunicação remota do PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="43448-144">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="see-also"></a><span data-ttu-id="43448-145">Veja Também</span><span class="sxs-lookup"><span data-stu-id="43448-145">See Also</span></span>

- [<span data-ttu-id="43448-146">Configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="43448-146">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="43448-147">Utilizar as dependências de recursos</span><span class="sxs-lookup"><span data-stu-id="43448-147">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="43448-148">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="43448-148">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="43448-149">Configurar o Gestor de configuração Local</span><span class="sxs-lookup"><span data-stu-id="43448-149">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
