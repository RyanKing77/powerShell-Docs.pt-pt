---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 61c5df1b64cb9c54f9c7372a56e77abf319658dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683766"
---
# <a name="network-switch-management-with-powershell"></a>Gestão de Comutador de Rede com o PowerShell

O **Get-NetworkSwitchEthernetPort** agora, o cmdlet retorna as seguintes informações adicionais com instâncias:

- IPAddress – o endereço IP associado a porta
- PortMode – o modo de porta: acesso, rota ou ramal
- AccessVLAN – o ID de VLAN associado esta porta no modo de acesso
- TrunkedVLANList – de uma lista de IDs de VLAN associado a esta porta no modo de ramal

## <a name="fundamental-network-switch-management-with-windows-powershell"></a>Gestão de comutador de rede fundamentais com o Windows PowerShell

Os cmdlets de comutador de rede, introduzidos no WMF 5.0, permitem-lhe aplicar o comutador, LAN virtual (VLAN) e básica configuração de porta do comutador de rede de camada 2 a comutadores de rede com logótipo de certificação do Windows Server 2012 R2. Microsoft mantém seu compromisso de oferecer suporte a [Abstração de centro de dados](http://technet.microsoft.com/cloud/dal.aspx) visão da camada DAL () e para mostrar o valor para os nossos clientes e parceiros neste espaço. Utilizando estes cmdlets pode efetuar:

- Global mudar a configuração, tais como:
    - Nome de anfitrião do conjunto
    - Faixa de comutador de conjunto
    - Manter a configuração
    - Ativar ou desativar funcionalidade

- Configuração de VLAN:
    - Criar ou remover VLAN
    - Ativar ou desativar a VLAN
    - Enumerar VLAN
    - Nome amigável do conjunto a uma VLAN

- Configuração da porta de camada 2:
    - Enumerar portas
    - Ativar ou desativar as portas
    - Modos de porta do conjunto e propriedades
    - Adicionar ou associar a VLAN de ramal ou acesso na porta

Começar a explorar, procurando todos os cmdlets do NetworkSwitch!

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

Mais informações estão disponíveis na mensagem de blogue de anúncio de pré-visualização do WMF 5.0 Jeffrey Snover: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx>
