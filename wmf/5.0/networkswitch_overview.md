---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 4868cf657f678ee43a6c92d5ee286e9ddb490964
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="network-switch-management-with-powershell"></a><span data-ttu-id="0f124-102">Gestão de comutador de rede com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f124-102">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="0f124-103">O **Get-NetworkSwitchEthernetPort** cmdlet devolve agora as seguintes informações adicionais com instâncias:</span><span class="sxs-lookup"><span data-stu-id="0f124-103">The **Get-NetworkSwitchEthernetPort** cmdlet now returns the following additional information with instances:</span></span>

- <span data-ttu-id="0f124-104">IPAddress – o endereço IP associado a porta</span><span class="sxs-lookup"><span data-stu-id="0f124-104">IPAddress – the IP address associated with the port</span></span>
- <span data-ttu-id="0f124-105">PortMode – o modo de porta: acesso, rota ou ramal</span><span class="sxs-lookup"><span data-stu-id="0f124-105">PortMode – the port mode: access, route, or trunk</span></span>
- <span data-ttu-id="0f124-106">AccessVLAN – o ID de VLAN associado a esta porta no modo de acesso</span><span class="sxs-lookup"><span data-stu-id="0f124-106">AccessVLAN – the ID of the VLAN associated with this port in access mode</span></span>
- <span data-ttu-id="0f124-107">TrunkedVLANList – de uma lista de IDs de VLAN associadas esta porta no modo de ramal</span><span class="sxs-lookup"><span data-stu-id="0f124-107">TrunkedVLANList – a list of IDs of VLANs associated with this port in trunk mode</span></span>

## <a name="fundamental-network-switch-management-with-windows-powershell"></a><span data-ttu-id="0f124-108">Gestão de comutador de rede fundamentais com o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f124-108">Fundamental network switch management with Windows PowerShell</span></span>

<span data-ttu-id="0f124-109">Os cmdlets de comutador de rede, introduzidos no WMF 5.0, permitem-lhe aplicar comutador, LAN virtual (VLAN) e básica configuração de porta do comutador de rede de camada 2 para comutadores de rede de certificação de logótipo do Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="0f124-109">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="0f124-110">Microsoft permanece consolidada para suportar o [Abstração do Centro de dados](http://technet.microsoft.com/cloud/dal.aspx) visão da camada DAL () e para mostrar o valor para os nossos clientes e parceiros neste espaço.</span><span class="sxs-lookup"><span data-stu-id="0f124-110">Microsoft remains committed to supporting the [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) Layer (DAL) vision, and to show value for our customers and partners in this space.</span></span> <span data-ttu-id="0f124-111">Utilizar estes cmdlets pode efetuar:</span><span class="sxs-lookup"><span data-stu-id="0f124-111">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="0f124-112">Global comutador configuração, tais como:</span><span class="sxs-lookup"><span data-stu-id="0f124-112">Global switch configuration, such as:</span></span>
    - <span data-ttu-id="0f124-113">Nome do conjunto de anfitrião</span><span class="sxs-lookup"><span data-stu-id="0f124-113">Set host name</span></span>
    - <span data-ttu-id="0f124-114">Faixa de comutador de conjunto</span><span class="sxs-lookup"><span data-stu-id="0f124-114">Set switch banner</span></span>
    - <span data-ttu-id="0f124-115">Manter a configuração</span><span class="sxs-lookup"><span data-stu-id="0f124-115">Persist configuration</span></span>
    - <span data-ttu-id="0f124-116">Ativar ou desativar funcionalidades</span><span class="sxs-lookup"><span data-stu-id="0f124-116">Enable or disable feature</span></span>

- <span data-ttu-id="0f124-117">Configuração de VLAN:</span><span class="sxs-lookup"><span data-stu-id="0f124-117">VLAN configuration:</span></span>
    - <span data-ttu-id="0f124-118">Criar ou remover VLAN</span><span class="sxs-lookup"><span data-stu-id="0f124-118">Create or remove VLAN</span></span>
    - <span data-ttu-id="0f124-119">Ativar ou desativar a VLAN</span><span class="sxs-lookup"><span data-stu-id="0f124-119">Enable or disable VLAN</span></span>
    - <span data-ttu-id="0f124-120">Enumerar VLAN</span><span class="sxs-lookup"><span data-stu-id="0f124-120">Enumerate VLAN</span></span>
    - <span data-ttu-id="0f124-121">Definir o nome amigável para uma VLAN</span><span class="sxs-lookup"><span data-stu-id="0f124-121">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="0f124-122">Configuração da porta de camada 2:</span><span class="sxs-lookup"><span data-stu-id="0f124-122">Layer 2 port configuration:</span></span>
    - <span data-ttu-id="0f124-123">Enumerar portas</span><span class="sxs-lookup"><span data-stu-id="0f124-123">Enumerate ports</span></span>
    - <span data-ttu-id="0f124-124">Ativar ou desativar as portas</span><span class="sxs-lookup"><span data-stu-id="0f124-124">Enable or disable ports</span></span>
    - <span data-ttu-id="0f124-125">Propriedades e modos de porta de conjunto</span><span class="sxs-lookup"><span data-stu-id="0f124-125">Set port modes and properties</span></span>
    - <span data-ttu-id="0f124-126">Adicionar ou associar a VLAN de ramal ou acesso na porta</span><span class="sxs-lookup"><span data-stu-id="0f124-126">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="0f124-127">Começar a explorar procurando todos os cmdlets NetworkSwitch!</span><span class="sxs-lookup"><span data-stu-id="0f124-127">Start exploring by looking for all of the NetworkSwitch cmdlets!</span></span>

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

<span data-ttu-id="0f124-128">Estão disponíveis na mensagem de blogue de anúncio de pré-visualização do WMF 5.0 de Jeffrey Snover mais informações: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span><span class="sxs-lookup"><span data-stu-id="0f124-128">More information is available in Jeffrey Snover’s WMF 5.0 Preview announcement blog post: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span></span>

