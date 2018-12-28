---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Atualizar os nós de um servidor de solicitação
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404647"
---
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="47493-103">Atualizar os nós de um servidor de solicitação</span><span class="sxs-lookup"><span data-stu-id="47493-103">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="47493-104">As secções abaixo partem do princípio de que já configurou um servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="47493-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="47493-105">Se não tiver configurado o servidor de solicitação, pode utilizar os seguintes guias:</span><span class="sxs-lookup"><span data-stu-id="47493-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="47493-106">Configurar um servidor de solicitação de SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="47493-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="47493-107">Configurar um servidor de solicitação de HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="47493-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="47493-108">Cada nó de destino pode ser configurado para transferir configurações, recursos e até mesmo comunicou o seu estado.</span><span class="sxs-lookup"><span data-stu-id="47493-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="47493-109">Este artigo irá mostrar como carregar recursos para que estejam disponíveis para transferir e configurar os clientes transfiram os recursos automaticamente.</span><span class="sxs-lookup"><span data-stu-id="47493-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="47493-110">Quando o nó recebe uma configuração atribuídos, por meio **extrair** ou **Push** (v5), é transferida automaticamente quaisquer recursos de que a configuração a partir da localização especificada no LCM.</span><span class="sxs-lookup"><span data-stu-id="47493-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="47493-111">Com o cmdlet Update-dscconfiguration para</span><span class="sxs-lookup"><span data-stu-id="47493-111">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="47493-112">A partir do PowerShell 5.0, o [Update-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet força um nó para atualizar a respetiva configuração do servidor de solicitação, configurado no LCM.</span><span class="sxs-lookup"><span data-stu-id="47493-112">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="47493-113">Usando o Invoke-CIMMethod</span><span class="sxs-lookup"><span data-stu-id="47493-113">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="47493-114">No PowerShell 4.0, pode forçar manualmente um cliente de solicitação para atualizar a respetiva configuração através de [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span><span class="sxs-lookup"><span data-stu-id="47493-114">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="47493-115">O exemplo seguinte cria uma sessão CIM com as credenciais especificadas, invoca o método apropriado de CIM e remove a sessão.</span><span class="sxs-lookup"><span data-stu-id="47493-115">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="47493-116">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="47493-116">See Also</span></span>

[<span data-ttu-id="47493-117">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="47493-117">PerformRequiredConfigurationChecks</span></span>](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
