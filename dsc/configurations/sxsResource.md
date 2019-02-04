---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Importar uma versão específica de um recurso instalado
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683885"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a><span data-ttu-id="c8201-103">Importar uma versão específica de um recurso instalado</span><span class="sxs-lookup"><span data-stu-id="c8201-103">Import a specific version of an installed resource</span></span>

> <span data-ttu-id="c8201-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c8201-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="c8201-105">No PowerShell 5.0, as versões separadas de recursos de DSC podem ser instaladas num computador lado a lado.</span><span class="sxs-lookup"><span data-stu-id="c8201-105">In PowerShell 5.0, separate versions of DSC resources can be installed on a computer side by side.</span></span> <span data-ttu-id="c8201-106">Um módulo de recursos pode armazenar separadas versões de um recurso na versão pastas nomeada.</span><span class="sxs-lookup"><span data-stu-id="c8201-106">A resource module can store separate versions of a resource in version named folders.</span></span>

## <a name="installing-separate-resource-versions-side-by-side"></a><span data-ttu-id="c8201-107">Instalação de recursos separado versões lado a lado</span><span class="sxs-lookup"><span data-stu-id="c8201-107">Installing separate resource versions side by side</span></span>

<span data-ttu-id="c8201-108">Pode utilizar o **MinimumVersion**, **MaximumVersion**, e **RequiredVersion** parâmetros do [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet para especificar qual é a versão de um módulo para instalar.</span><span class="sxs-lookup"><span data-stu-id="c8201-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="c8201-109">A invocar **Install-Module** sem especificar uma versão instala a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="c8201-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="c8201-110">Por exemplo, há várias versões dos **xFailOverCluster** módulo, cada um contendo uma **xCluster** recursos.</span><span class="sxs-lookup"><span data-stu-id="c8201-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resource.</span></span> <span data-ttu-id="c8201-111">A invocar **Install-Module** sem especificar a versão número instala a versão mais recente do módulo.</span><span class="sxs-lookup"><span data-stu-id="c8201-111">Calling **Install-Module** without specifying the version number installs the most recent version of the module.</span></span>

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="c8201-112">Para instalar uma versão específica de um módulo, especificar um **RequiredVersion** de 1.1.0.0.</span><span class="sxs-lookup"><span data-stu-id="c8201-112">To install a specific version of a module, specify a **RequiredVersion** of 1.1.0.0.</span></span> <span data-ttu-id="c8201-113">Esta ação instala a versão especificada lado a lado com a versão instalada.</span><span class="sxs-lookup"><span data-stu-id="c8201-113">This installs the specified version side by side with the installed version.</span></span>

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

<span data-ttu-id="c8201-114">Agora, vê a versão do módulo listados quando utiliza `Get-DSCResource`.</span><span class="sxs-lookup"><span data-stu-id="c8201-114">Now, you see both version of the module listed when you use `Get-DSCResource`.</span></span>

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="c8201-115">Especificar uma versão do recurso numa configuração</span><span class="sxs-lookup"><span data-stu-id="c8201-115">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="c8201-116">Se tiver versões de recursos separado instaladas num computador, tem de especificar a versão desse recurso quando usá-lo numa configuração.</span><span class="sxs-lookup"><span data-stu-id="c8201-116">If you have separate resource versions installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="c8201-117">Fazê-lo ao especificar os **ModuleVersion** parâmetro do **Import-DscResource** palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="c8201-117">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="c8201-118">Se não especificar a versão de um módulo de recursos de um recurso que tem mais de uma versão instalada, a configuração gera um erro.</span><span class="sxs-lookup"><span data-stu-id="c8201-118">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="c8201-119">A configuração seguinte mostra como especificar a versão do recurso para chamar:</span><span class="sxs-lookup"><span data-stu-id="c8201-119">The following configuration shows how to specify the version of the resource to call:</span></span>

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

><span data-ttu-id="c8201-120">Nota: O parâmetro de ModuleVersion do Import-DscResource não está disponível no PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="c8201-120">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="c8201-121">No PowerShell 4.0, pode especificar uma versão do módulo, passando um objeto de especificação do módulo para o parâmetro ModuleName Import-DscResource.</span><span class="sxs-lookup"><span data-stu-id="c8201-121">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="c8201-122">Um objeto de especificação do módulo é uma tabela de hash que contém as chaves de ModuleName e RequiredVersion.</span><span class="sxs-lookup"><span data-stu-id="c8201-122">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="c8201-123">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c8201-123">For example:</span></span>

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

<span data-ttu-id="c8201-124">Isso também funciona no PowerShell 5.0, mas é recomendado que utilize o **ModuleVersion** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c8201-124">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8201-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8201-125">See also</span></span>

- [<span data-ttu-id="c8201-126">Configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="c8201-126">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="c8201-127">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="c8201-127">DSC Resources</span></span>](../resources/resources.md)
