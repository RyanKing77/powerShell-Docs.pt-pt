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
# <a name="update-nodes-from-a-pull-server"></a>Atualizar os nós de um servidor de solicitação

As secções abaixo partem do princípio de que já configurou um servidor de solicitação. Se não tiver configurado o servidor de solicitação, pode utilizar os seguintes guias:

- [Configurar um servidor de solicitação de SMB de DSC](pullServerSmb.md)
- [Configurar um servidor de solicitação de HTTP de DSC](pullServer.md)

Cada nó de destino pode ser configurado para transferir configurações, recursos e até mesmo comunicou o seu estado. Este artigo irá mostrar como carregar recursos para que estejam disponíveis para transferir e configurar os clientes transfiram os recursos automaticamente. Quando o nó recebe uma configuração atribuídos, por meio **extrair** ou **Push** (v5), é transferida automaticamente quaisquer recursos de que a configuração a partir da localização especificada no LCM.

## <a name="using-the-update-dscconfiguration-cmdlet"></a>Com o cmdlet Update-dscconfiguration para

A partir do PowerShell 5.0, o [Update-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet força um nó para atualizar a respetiva configuração do servidor de solicitação, configurado no LCM.

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>Usando o Invoke-CIMMethod

No PowerShell 4.0, pode forçar manualmente um cliente de solicitação para atualizar a respetiva configuração através de [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod). O exemplo seguinte cria uma sessão CIM com as credenciais especificadas, invoca o método apropriado de CIM e remove a sessão.

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>Consulte Também

[PerformRequiredConfigurationChecks](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
