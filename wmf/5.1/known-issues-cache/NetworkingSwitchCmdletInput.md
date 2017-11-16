---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
contributor: vaibch
title: Falha de cmdlets do Gestor de comutador de rede
ms.openlocfilehash: d9fcdedbfc7d0c3f68624ed1db6259e04c3d06d1
ms.sourcegitcommit: fee03bb9802222078c8d5f6c8efb0698024406ed
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/27/2017
---
Os cmdlets do Gestor de comutador de rede pode ser utilizados para gerir os comutadores de rede através de WSMAN. Alguns cmdlets deste módulo são capazes de aceitar os valores de pipelines. Pré-visualização do WMF 5.1, os cmdlets que pode aceitar valor de pipeline falha a executar quando os valores não são transmitidos através de pipelines.

Se não for utilizado o parâmetro de "InputObject", o cmdlet deve continuar a executar sem falhas.

Eis a lista de cmdlets afetados ou seja, estes cmdlets pode aceitar valor para o parâmetro de "InputObject" do pipeline. Se este valor não é transmitido a partir do pipeline a execução do cmdlet irá falhar.

- Desativar NetworkSwitchEthernetPort
- Ativar NetworkSwitchEthernetPort
- Remover NetworkSwitchEthernetPortIPAddress
- Conjunto NetworkSwitchEthernetPortIPAddress
- Conjunto NetworkSwitchPortMode
- Conjunto NetworkSwitchPortProperty
- Desativar NetworkSwitchFeature
- Ativar NetworkSwitchFeature
- Remover NetworkSwitchVlan
- Conjunto NetworkSwitchVlanProperty

### <a name="resolution"></a>Resolução
O trabalho de cmdlets bem quando o valor do parâmetro InputObject são transmitidos para a mesma através do pipeline. Alguns exemplos que funcionam para os cmdlets acima são:

- Desativar NetworkSwitchEthernetPort
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- Ativar NetworkSwitchEthernetPort
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- Remover NetworkSwitchEthernetPortIPAddress
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- Conjunto NetworkSwitchEthernetPortIPAddress
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- Conjunto NetworkSwitchPortProperty
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- Desativar NetworkSwitchFeature
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- Ativar NetworkSwitchFeature
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- Conjunto NetworkSwitchVlanProperty
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```

