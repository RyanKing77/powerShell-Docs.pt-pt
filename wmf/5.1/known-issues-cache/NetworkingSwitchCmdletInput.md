---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
contributor: vaibch
title: Falha de cmdlets do Gestor de comutador de rede
ms.openlocfilehash: a0f84c35974b6674faba4b0f19a28bd6e2490a96
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893159"
---
# <a name="network-switch-manager-cmdlets-failure"></a><span data-ttu-id="c2daf-103">Falha de Cmdlets do Gestor de comutador de rede</span><span class="sxs-lookup"><span data-stu-id="c2daf-103">Network Switch Manager Cmdlets Failure</span></span>

<span data-ttu-id="c2daf-104">Os cmdlets do Gestor de comutador de rede pode ser utilizados para gerir comutadores de rede em WSMAN.</span><span class="sxs-lookup"><span data-stu-id="c2daf-104">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="c2daf-105">Alguns cmdlets deste módulo são capazes de aceitação de valores de pipelines.</span><span class="sxs-lookup"><span data-stu-id="c2daf-105">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="c2daf-106">Na pré-visualização do WMF 5.1, os cmdlets que pode aceitar o valor do pipeline de não ser executado quando os valores não forem transmitidos através de pipelines.</span><span class="sxs-lookup"><span data-stu-id="c2daf-106">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="c2daf-107">Se não for utilizado o parâmetro de "InputObject", o cmdlet deve continuam a ser executadas sem falhas.</span><span class="sxs-lookup"><span data-stu-id="c2daf-107">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="c2daf-108">Eis a lista de cmdlets afetados, ou seja, estes cmdlets pode aceitar o valor para o parâmetro de "InputObject" do pipeline.</span><span class="sxs-lookup"><span data-stu-id="c2daf-108">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="c2daf-109">Se este valor não for passado do pipeline de execução do cmdlet irá falhar.</span><span class="sxs-lookup"><span data-stu-id="c2daf-109">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="c2daf-110">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="c2daf-110">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="c2daf-111">Ativar NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="c2daf-111">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="c2daf-112">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="c2daf-112">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="c2daf-113">Conjunto NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="c2daf-113">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="c2daf-114">Conjunto NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="c2daf-114">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="c2daf-115">Conjunto NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="c2daf-115">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="c2daf-116">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="c2daf-116">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="c2daf-117">Ativar NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="c2daf-117">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="c2daf-118">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="c2daf-118">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="c2daf-119">Conjunto NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="c2daf-119">Set-NetworkSwitchVlanProperty</span></span>

## <a name="resolution"></a><span data-ttu-id="c2daf-120">Resolução</span><span class="sxs-lookup"><span data-stu-id="c2daf-120">Resolution</span></span>

<span data-ttu-id="c2daf-121">O trabalho de cmdlets bem quando o valor do parâmetro de InputObject são passadas para o mesmo por meio do pipeline.</span><span class="sxs-lookup"><span data-stu-id="c2daf-121">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="c2daf-122">Alguns exemplos que funcionam para os cmdlets acima são:</span><span class="sxs-lookup"><span data-stu-id="c2daf-122">A few examples that work for the above cmdlets are:</span></span>

- `Disable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Enable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Remove-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $ipAddress = "192.168.10.1"
  $subnetAddress = "255.255.255.0"
  $port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchPortProperty`

  ```powershell
  $portProperties = @{Caption = "New Caption"}
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
  ```

- `Disable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Disable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Enable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Enable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Set-NetworkSwitchVlanProperty`

  ```powershell
  $properties = @{Caption = "New Caption"}
  $vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
  $vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
  ```