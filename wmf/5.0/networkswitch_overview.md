---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 80852bf750700d549de24e150ffd89ac55b7bf88
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="network-switch-management-with-powershell"></a>Gestão de comutador de rede com o PowerShell

O **Get-NetworkSwitchEthernetPort** cmdlet devolve agora as seguintes informações adicionais com instâncias:

- IPAddress – o endereço IP associado a porta
- PortMode – o modo de porta: acesso, rota ou ramal
- AccessVLAN – o ID de VLAN associado a esta porta no modo de acesso
- TrunkedVLANList – de uma lista de IDs de VLAN associadas esta porta no modo de ramal

## <a name="fundamental-network-switch-management-with-windows-powershell"></a>Gestão de comutador de rede fundamentais com o Windows PowerShell

Os cmdlets de comutador de rede, introduzidos no WMF 5.0, permitem-lhe aplicar comutador, LAN virtual (VLAN) e básica configuração de porta do comutador de rede de camada 2 para comutadores de rede de certificação de logótipo do Windows Server 2012 R2. Microsoft permanece consolidada para suportar o [Abstração do Centro de dados](http://technet.microsoft.com/en-us/cloud/dal.aspx) visão da camada DAL () e para mostrar o valor para os nossos clientes e parceiros neste espaço. Utilizar estes cmdlets pode efetuar:

- Global comutador configuração, tais como:
    - Nome do conjunto de anfitrião
    - Faixa de comutador de conjunto
    - Manter a configuração
    - Ativar ou desativar funcionalidades

- Configuração de VLAN:
    - Criar ou remover VLAN
    - Ativar ou desativar a VLAN
    - Enumerar VLAN
    - Definir o nome amigável para uma VLAN

- Configuração da porta de camada 2:
    - Enumerar portas
    - Ativar ou desativar as portas
    - Propriedades e modos de porta de conjunto
    - Adicionar ou associar a VLAN de ramal ou acesso na porta

Começar a explorar procurando todos os cmdlets NetworkSwitch!

```powershell
PS> Get-Command *-NetworkSwitch*

| CommandType | Name                                      | Source        |
|-------------|-------------------------------------------|---------------|
|             |                                           |               |
| Function    | Disable-NetworkSwitchEthernetPort         | NetworkSwitch |
| Function    | Disable-NetworkSwitchFeature              | NetworkSwitch |
| Function    | Disable-NetworkSwitchVlan                 | NetworkSwitch |
| Function    | Enable-NetworkSwitchEthernetPort          | NetworkSwitch |
| Function    | Enable-NetworkSwitchFeature               | NetworkSwitch |
| Function    | Enable-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Get-NetworkSwitchEthernetPort             | NetworkSwitch |
| Function    | Get-NetworkSwitchFeature                  | NetworkSwitch |
| Function    | Get-NetworkSwitchGlobalData               | NetworkSwitch |
| Function    | Get-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | New-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | Remove-NetworkSwitchEthernetPortIPAddress | NetworkSwitch |
| Function    | Remove-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Restore-NetworkSwitchConfiguration        | NetworkSwitch |
| Function    | Save-NetworkSwitchConfiguration           | NetworkSwitch |
| Function    | Set-NetworkSwitchEthernetPortIPAddress    | NetworkSwitch |
| Function    | Set-NetworkSwitchPortMode                 | NetworkSwitch |
| Function    | Set-NetworkSwitchPortProperty             | NetworkSwitch |
| Function    | Set-NetworkSwitchVlanProperty             | NetworkSwitch |
```

Estão disponíveis na mensagem de blogue de anúncio de pré-visualização do WMF 5.0 de Jeffrey Snover mais informações: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx>
