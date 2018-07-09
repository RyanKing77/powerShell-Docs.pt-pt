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
# <a name="network-switch-manager-cmdlets-failure"></a>Falha de Cmdlets do Gestor de comutador de rede

Os cmdlets do Gestor de comutador de rede pode ser utilizados para gerir comutadores de rede em WSMAN.
Alguns cmdlets deste módulo são capazes de aceitação de valores de pipelines.
Na pré-visualização do WMF 5.1, os cmdlets que pode aceitar o valor do pipeline de não ser executado quando os valores não forem transmitidos através de pipelines.

Se não for utilizado o parâmetro de "InputObject", o cmdlet deve continuam a ser executadas sem falhas.

Eis a lista de cmdlets afetados, ou seja, estes cmdlets pode aceitar o valor para o parâmetro de "InputObject" do pipeline.
Se este valor não for passado do pipeline de execução do cmdlet irá falhar.

- Disable-NetworkSwitchEthernetPort
- Ativar NetworkSwitchEthernetPort
- Remove-NetworkSwitchEthernetPortIPAddress
- Conjunto NetworkSwitchEthernetPortIPAddress
- Conjunto NetworkSwitchPortMode
- Conjunto NetworkSwitchPortProperty
- Disable-NetworkSwitchFeature
- Ativar NetworkSwitchFeature
- Remove-NetworkSwitchVlan
- Conjunto NetworkSwitchVlanProperty

## <a name="resolution"></a>Resolução

O trabalho de cmdlets bem quando o valor do parâmetro de InputObject são passadas para o mesmo por meio do pipeline. Alguns exemplos que funcionam para os cmdlets acima são:

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