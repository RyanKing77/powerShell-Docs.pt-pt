---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Utilizar recursos com várias versões"
ms.openlocfilehash: 5ca4eadfe23a4675e1b81b86d4274d7f113228fe
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="using-resources-with-multiple-versions"></a><span data-ttu-id="e0af3-103">Utilizar recursos com várias versões</span><span class="sxs-lookup"><span data-stu-id="e0af3-103">Using resources with multiple versions</span></span>

> <span data-ttu-id="e0af3-104">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e0af3-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="e0af3-105">No PowerShell 5.0, recursos de DSC podem ter várias versões e versões podem ser instaladas num computador do lado do lado a lado.</span><span class="sxs-lookup"><span data-stu-id="e0af3-105">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="e0af3-106">Isto é implementado por ter várias versões de um módulo de recursos que estão contidas na mesma pasta do módulo.</span><span class="sxs-lookup"><span data-stu-id="e0af3-106">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>

## <a name="installing-multiple-resource-versions-side-by-side"></a><span data-ttu-id="e0af3-107">Instalar vários recursos versões do lado do lado a lado</span><span class="sxs-lookup"><span data-stu-id="e0af3-107">Installing multiple resource versions side-by-side</span></span>

<span data-ttu-id="e0af3-108">Pode utilizar o **MinimumVersion**, **MaximumVersion**, e **RequiredVersion** parâmetros a [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet para especificar qual é a versão de um módulo para instalar.</span><span class="sxs-lookup"><span data-stu-id="e0af3-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="e0af3-109">Chamar **Install-Module** sem especificar uma versão instala a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="e0af3-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="e0af3-110">Por exemplo, existem várias versões do **xFailOverCluster** módulo, cada um dos quais contém uma **xCluster** recurso.</span><span class="sxs-lookup"><span data-stu-id="e0af3-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resouce.</span></span> <span data-ttu-id="e0af3-111">O resultado da chamada **Install-Module** sem especificar a versão número é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e0af3-111">The result of calling **Install-Module** without specifying the version number is as follows:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="e0af3-112">Agora, se chamar **Install-Module** novamente, mas Especifica um **RequiredVersion** de 1.1.0.0, o que resulta no seguinte:</span><span class="sxs-lookup"><span data-stu-id="e0af3-112">Now, if you call **Install-Module** again, but specify a **RequiredVersion** of 1.1.0.0, it results in the following:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="e0af3-113">Especificar uma versão do recurso numa configuração</span><span class="sxs-lookup"><span data-stu-id="e0af3-113">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="e0af3-114">Se tiver vários recursos instalados num computador, tem de especificar a versão desse recurso quando utiliza uma configuração.</span><span class="sxs-lookup"><span data-stu-id="e0af3-114">If you have multiple resources installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="e0af3-115">Fazê-lo especificando o **ModuleVersion** parâmetro o **importação DscResource** palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e0af3-115">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="e0af3-116">Se falhar especificar a versão de um módulo de recurso de um recurso de que tem mais do que uma versão instalada, a configuração gera um erro.</span><span class="sxs-lookup"><span data-stu-id="e0af3-116">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="e0af3-117">A configuração seguinte mostra como especificar a versão do recurso para chamar:</span><span class="sxs-lookup"><span data-stu-id="e0af3-117">The following configuration shows how to specify the version of the resource to call:</span></span>

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

><span data-ttu-id="e0af3-118">Nota: O parâmetro ModuleVersion da importação DscResource não está disponível no PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="e0af3-118">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="e0af3-119">No PowerShell 4.0, pode especificar uma versão do módulo através da transmissão de um objeto de especificação do módulo para o parâmetro ModuleName do DscResource de importação.</span><span class="sxs-lookup"><span data-stu-id="e0af3-119">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="e0af3-120">Um objeto de especificação do módulo é uma tabela hash que contém chaves ModuleName e RequiredVersion.</span><span class="sxs-lookup"><span data-stu-id="e0af3-120">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="e0af3-121">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e0af3-121">For example:</span></span>

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

<span data-ttu-id="e0af3-122">Isto também irá funcionar no PowerShell 5.0, mas é recomendado que utilize o **ModuleVersion** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e0af3-122">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0af3-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0af3-123">See also</span></span>
* [<span data-ttu-id="e0af3-124">Configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="e0af3-124">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="e0af3-125">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="e0af3-125">DSC Resources</span></span>](resources.md)

