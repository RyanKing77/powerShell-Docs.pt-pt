---
ms.date: 08/15/2019
keywords: DSC, PowerShell, configuração, instalação
title: Introdução à configuração de estado desejado (DSC) para Windows
ms.openlocfilehash: a4f9db481afda65fc4ac5e553230dbba3037ac9a
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988929"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a><span data-ttu-id="169c0-103">Introdução à configuração de estado desejado (DSC) para Windows</span><span class="sxs-lookup"><span data-stu-id="169c0-103">Get started with Desired State Configuration (DSC) for Windows</span></span>

<span data-ttu-id="169c0-104">Este tópico explica como começar a usar a DSC (configuração de estado desejado) do PowerShell para Windows.</span><span class="sxs-lookup"><span data-stu-id="169c0-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Windows.</span></span>
<span data-ttu-id="169c0-105">Para obter informações gerais sobre a DSC, consulte Introdução [à configuração de estado desejado do Windows PowerShell](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="169c0-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-windows-operation-system-versions"></a><span data-ttu-id="169c0-106">Versões do sistema operacional Windows com suporte</span><span class="sxs-lookup"><span data-stu-id="169c0-106">Supported Windows operation system versions</span></span>

<span data-ttu-id="169c0-107">Há suporte para as seguintes versões:</span><span class="sxs-lookup"><span data-stu-id="169c0-107">The following versions are supported:</span></span>

- <span data-ttu-id="169c0-108">Windows Server de 2019</span><span class="sxs-lookup"><span data-stu-id="169c0-108">Windows Server 2019</span></span>
- <span data-ttu-id="169c0-109">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="169c0-109">Windows Server 2016</span></span>
- <span data-ttu-id="169c0-110">Windows Server 2012R2</span><span class="sxs-lookup"><span data-stu-id="169c0-110">Windows Server 2012R2</span></span>
- <span data-ttu-id="169c0-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="169c0-111">Windows Server 2012</span></span>
- <span data-ttu-id="169c0-112">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="169c0-112">Windows Server 2008 R2 SP1</span></span>
- <span data-ttu-id="169c0-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="169c0-113">Windows 10</span></span>
- <span data-ttu-id="169c0-114">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="169c0-114">Windows 8.1</span></span>
- <span data-ttu-id="169c0-115">Windows 7</span><span class="sxs-lookup"><span data-stu-id="169c0-115">Windows 7</span></span>

<span data-ttu-id="169c0-116">O SKU do produto autônomo do [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) não contém uma implementação do estado desejado configuração, portanto, ele não pode ser gerenciado pela configuração do estado da automação do PowerShell ou da DSC do Azure.</span><span class="sxs-lookup"><span data-stu-id="169c0-116">The [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) standalone product sku does not contain an implementation of Desired State Configuraion so it cannot be managed by PowerShell DSC or Azure Automation State Configuration.</span></span>

## <a name="installing-dsc"></a><span data-ttu-id="169c0-117">Instalando DSC</span><span class="sxs-lookup"><span data-stu-id="169c0-117">Installing DSC</span></span>

<span data-ttu-id="169c0-118">A configuração de estado desejado do PowerShell está incluída no Windows e atualizada por meio do Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="169c0-118">PowerShell Desired State Configuration is included in Windows and updated through Windows Management Framework.</span></span>
<span data-ttu-id="169c0-119">A versão mais recente é o [Windows Management Framework 5,1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span><span class="sxs-lookup"><span data-stu-id="169c0-119">The latest version is [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span></span>

> [!NOTE]
> <span data-ttu-id="169c0-120">Você não precisa habilitar o recurso ' DSC-Service ' do Windows Server para gerenciar um computador usando o DSC.</span><span class="sxs-lookup"><span data-stu-id="169c0-120">You do not need to enable the Windows Server feature 'DSC-Service' to manage a machine using DSC.</span></span>
> <span data-ttu-id="169c0-121">Esse recurso só é necessário ao criar uma instância de servidor de pull do Windows.</span><span class="sxs-lookup"><span data-stu-id="169c0-121">That feature is only needed when building a Windows Pull Server instance.</span></span>

## <a name="using-dsc-for-windows"></a><span data-ttu-id="169c0-122">Usando o DSC para Windows</span><span class="sxs-lookup"><span data-stu-id="169c0-122">Using DSC for Windows</span></span>

<span data-ttu-id="169c0-123">As seções a seguir explicam como criar e executar configurações de DSC em computadores Windows.</span><span class="sxs-lookup"><span data-stu-id="169c0-123">The following sections explain how to create and run DSC configurations on Windows computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="169c0-124">Criando um documento MOF de configuração</span><span class="sxs-lookup"><span data-stu-id="169c0-124">Creating a configuration MOF document</span></span>

<span data-ttu-id="169c0-125">A palavra-chave de configuração do Windows PowerShell é usada para criar uma configuração.</span><span class="sxs-lookup"><span data-stu-id="169c0-125">The Windows PowerShell Configuration keyword is used to create a configuration.</span></span>
<span data-ttu-id="169c0-126">As etapas a seguir descrevem a criação de um documento de configuração usando o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="169c0-126">The following steps describe the creation of a configuration document using Windows PowerShell.</span></span>

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a><span data-ttu-id="169c0-127">Defina uma configuração e gere o documento de configuração:</span><span class="sxs-lookup"><span data-stu-id="169c0-127">Define a configuration and generate the configuration document:</span></span>

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```
#### <a name="install-a-module-containing-dsc-resources"></a><span data-ttu-id="169c0-128">Instalar um módulo que contém recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="169c0-128">Install a module containing DSC resources</span></span>

<span data-ttu-id="169c0-129">A configuração de estado desejado do Windows PowerShell inclui módulos internos que contêm recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="169c0-129">Windows PowerShell Desired State Configuration includes built-in modules containing DSC resources.</span></span>
<span data-ttu-id="169c0-130">Você também pode carregar módulos de fontes externas, como o Galeria do PowerShell, usando os cmdlets do PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="169c0-130">You can also load modules from external sources such as the PowerShell Gallery, using the PowerShellGet cmdlets.</span></span>

`Install-Module 'PSDscResources' -Verbose`

#### <a name="apply-the-configuration-to-the-machine"></a><span data-ttu-id="169c0-131">Aplicar a configuração ao computador</span><span class="sxs-lookup"><span data-stu-id="169c0-131">Apply the configuration to the machine</span></span>

<span data-ttu-id="169c0-132">Os documentos de configuração (Arquivos MOF) podem ser aplicados ao computador usando o cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="169c0-132">Configuration documents (MOF files) can be applied to the machine using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

`Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose`

#### <a name="get-the-current-state-of-the-configuration"></a><span data-ttu-id="169c0-133">Obter o estado atual da configuração</span><span class="sxs-lookup"><span data-stu-id="169c0-133">Get the current state of the configuration</span></span>

<span data-ttu-id="169c0-134">O cmdlet [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) consulta o status atual do computador e retorna os valores atuais para a configuração.</span><span class="sxs-lookup"><span data-stu-id="169c0-134">The [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet queries the current status of the machine and returns the current values for the configuration.</span></span>

`Get-DscConfiguration`

<span data-ttu-id="169c0-135">O cmdlet [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) retorna a meta-configuração atual aplicada ao computador.</span><span class="sxs-lookup"><span data-stu-id="169c0-135">The [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet returns the current meta-configuration applied to the machine.</span></span>

`Get-DscLocalConfigurationManager`

#### <a name="remove-the-current-configuration-from-a-machine"></a><span data-ttu-id="169c0-136">Remover a configuração atual de um computador</span><span class="sxs-lookup"><span data-stu-id="169c0-136">Remove the current configuration from a machine</span></span>

<span data-ttu-id="169c0-137">O [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span><span class="sxs-lookup"><span data-stu-id="169c0-137">The [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span></span>

`Remove-DscConfigurationDocument -Stage Current -Verbose`

#### <a name="configure-settings-in-local-configuration-manager"></a><span data-ttu-id="169c0-138">Definir configurações no Configuration Manager local</span><span class="sxs-lookup"><span data-stu-id="169c0-138">Configure settings in Local Configuration Manager</span></span>

<span data-ttu-id="169c0-139">Aplique um arquivo MOF de metaconfiguração ao computador usando o cmdlet [set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) .</span><span class="sxs-lookup"><span data-stu-id="169c0-139">Apply a Meta Configuration MOF file to the machine using the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span>
<span data-ttu-id="169c0-140">Requer o caminho para o MOF de metaconfiguração.</span><span class="sxs-lookup"><span data-stu-id="169c0-140">Requires the path to the Meta Configuration MOF.</span></span>

`Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose`

## <a name="windows-powershell-desired-state-configuration-log-files"></a><span data-ttu-id="169c0-141">Arquivos de log de configuração de estado desejado do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="169c0-141">Windows PowerShell Desired State Configuration log files</span></span>

<span data-ttu-id="169c0-142">Os logs para DSC são gravados no log de eventos do `Microsoft-Windows-Dsc/Operational`Windows no caminho.</span><span class="sxs-lookup"><span data-stu-id="169c0-142">Logs for DSC are written to Windows Event Log in the path `Microsoft-Windows-Dsc/Operational`.</span></span>
<span data-ttu-id="169c0-143">Logs adicionais para fins de depuração podem ser habilitados seguindo as etapas em [onde estão os logs de eventos de DSC](/powershell/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="169c0-143">Additional logs for debugging purposes can be enabled following the steps in [Where Are DSC Event Logs](/powershell/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span></span>
