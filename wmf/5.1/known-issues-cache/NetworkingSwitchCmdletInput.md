---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
contributor: vaibch
title: Falha de cmdlets do Gestor de comutador de rede
ms.openlocfilehash: 197a25411a82e5d256a9420706535d5411991f1b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188688"
---
<span data-ttu-id="7a334-103">Os cmdlets do Gestor de comutador de rede pode ser utilizados para gerir os comutadores de rede através de WSMAN.</span><span class="sxs-lookup"><span data-stu-id="7a334-103">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="7a334-104">Alguns cmdlets deste módulo são capazes de aceitar os valores de pipelines.</span><span class="sxs-lookup"><span data-stu-id="7a334-104">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="7a334-105">Pré-visualização do WMF 5.1, os cmdlets que pode aceitar valor de pipeline falha a executar quando os valores não são transmitidos através de pipelines.</span><span class="sxs-lookup"><span data-stu-id="7a334-105">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="7a334-106">Se não for utilizado o parâmetro de "InputObject", o cmdlet deve continuar a executar sem falhas.</span><span class="sxs-lookup"><span data-stu-id="7a334-106">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="7a334-107">Eis a lista de cmdlets afetados ou seja, estes cmdlets pode aceitar valor para o parâmetro de "InputObject" do pipeline.</span><span class="sxs-lookup"><span data-stu-id="7a334-107">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="7a334-108">Se este valor não é transmitido a partir do pipeline a execução do cmdlet irá falhar.</span><span class="sxs-lookup"><span data-stu-id="7a334-108">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="7a334-109">Desativar NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="7a334-109">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="7a334-110">Ativar NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="7a334-110">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="7a334-111">Remover NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="7a334-111">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="7a334-112">Conjunto NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="7a334-112">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="7a334-113">Conjunto NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="7a334-113">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="7a334-114">Conjunto NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="7a334-114">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="7a334-115">Desativar NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="7a334-115">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="7a334-116">Ativar NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="7a334-116">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="7a334-117">Remover NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="7a334-117">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="7a334-118">Conjunto NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="7a334-118">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="7a334-119">Resolução</span><span class="sxs-lookup"><span data-stu-id="7a334-119">Resolution</span></span>
<span data-ttu-id="7a334-120">O trabalho de cmdlets bem quando o valor do parâmetro InputObject são transmitidos para a mesma através do pipeline.</span><span class="sxs-lookup"><span data-stu-id="7a334-120">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="7a334-121">Alguns exemplos que funcionam para os cmdlets acima são:</span><span class="sxs-lookup"><span data-stu-id="7a334-121">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="7a334-122">Desativar NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="7a334-122">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="7a334-123">Ativar NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="7a334-123">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="7a334-124">Remover NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="7a334-124">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="7a334-125">Conjunto NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="7a334-125">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="7a334-126">Conjunto NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="7a334-126">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="7a334-127">Desativar NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="7a334-127">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="7a334-128">Ativar NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="7a334-128">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="7a334-129">Conjunto NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="7a334-129">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```
