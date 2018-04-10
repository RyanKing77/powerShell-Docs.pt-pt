---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
contributor: vaibch
title: Falha de cmdlets do Gestor de comutador de rede
ms.openlocfilehash: 626809513e7a8f1aa2c47a48c74e69ca4077f598
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
<span data-ttu-id="978fe-103">Os cmdlets do Gestor de comutador de rede pode ser utilizados para gerir os comutadores de rede através de WSMAN.</span><span class="sxs-lookup"><span data-stu-id="978fe-103">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="978fe-104">Alguns cmdlets deste módulo são capazes de aceitar os valores de pipelines.</span><span class="sxs-lookup"><span data-stu-id="978fe-104">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="978fe-105">Pré-visualização do WMF 5.1, os cmdlets que pode aceitar valor de pipeline falha a executar quando os valores não são transmitidos através de pipelines.</span><span class="sxs-lookup"><span data-stu-id="978fe-105">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="978fe-106">Se não for utilizado o parâmetro de "InputObject", o cmdlet deve continuar a executar sem falhas.</span><span class="sxs-lookup"><span data-stu-id="978fe-106">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="978fe-107">Eis a lista de cmdlets afetados ou seja, estes cmdlets pode aceitar valor para o parâmetro de "InputObject" do pipeline.</span><span class="sxs-lookup"><span data-stu-id="978fe-107">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="978fe-108">Se este valor não é transmitido a partir do pipeline a execução do cmdlet irá falhar.</span><span class="sxs-lookup"><span data-stu-id="978fe-108">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="978fe-109">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="978fe-109">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="978fe-110">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="978fe-110">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="978fe-111">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="978fe-111">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="978fe-112">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="978fe-112">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="978fe-113">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="978fe-113">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="978fe-114">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="978fe-114">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="978fe-115">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="978fe-115">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="978fe-116">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="978fe-116">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="978fe-117">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="978fe-117">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="978fe-118">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="978fe-118">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="978fe-119">Resolução</span><span class="sxs-lookup"><span data-stu-id="978fe-119">Resolution</span></span>
<span data-ttu-id="978fe-120">O trabalho de cmdlets bem quando o valor do parâmetro InputObject são transmitidos para a mesma através do pipeline.</span><span class="sxs-lookup"><span data-stu-id="978fe-120">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="978fe-121">Alguns exemplos que funcionam para os cmdlets acima são:</span><span class="sxs-lookup"><span data-stu-id="978fe-121">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="978fe-122">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="978fe-122">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="978fe-123">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="978fe-123">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="978fe-124">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="978fe-124">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="978fe-125">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="978fe-125">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="978fe-126">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="978fe-126">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="978fe-127">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="978fe-127">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="978fe-128">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="978fe-128">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="978fe-129">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="978fe-129">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```