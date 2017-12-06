---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Configurar uma máquinas virtuais em cima de arranque inicial através da utilização de DSC"
ms.openlocfilehash: c793e36eb9caa194104f9dda2aa1d335b21b676c
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2017
---
><span data-ttu-id="ea5d9-103">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ea5d9-103">Applies To: Windows PowerShell 5.0</span></span>

><span data-ttu-id="ea5d9-104">**Nota:** o **DSCAutomationHostEnabled** chave de registo descrito neste tópico não está disponível no PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-104">**Note:** The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span>
<span data-ttu-id="ea5d9-105">Para obter informações sobre como configurar novas máquinas virtuais em cima de arranque inicial no PowerShell 4.0, consulte [pretende automaticamente configurar seu máquinas utilizando DSC no arranque inicial de segurança?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span><span class="sxs-lookup"><span data-stu-id="ea5d9-105">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="ea5d9-106">Configurar uma máquinas virtuais em cima de arranque inicial através da utilização de DSC</span><span class="sxs-lookup"><span data-stu-id="ea5d9-106">Configure a virtual machines at initial boot-up by using DSC</span></span>

## <a name="requirements"></a><span data-ttu-id="ea5d9-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ea5d9-107">Requirements</span></span>

<span data-ttu-id="ea5d9-108">Para executar estes exemplos, necessitará de:</span><span class="sxs-lookup"><span data-stu-id="ea5d9-108">To run these examples, you will need:</span></span>

- <span data-ttu-id="ea5d9-109">Um VHD de arranque para trabalhar com.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-109">A bootable VHD to work with.</span></span> <span data-ttu-id="ea5d9-110">Pode transferir uma imagem ISO com uma cópia de avaliação do Windows Server 2016 em [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="ea5d9-110">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span> <span data-ttu-id="ea5d9-111">Pode encontrar instruções sobre como criar um VHD a partir de uma imagem ISO na [criar suportes os discos rígidos virtuais](https://technet.microsoft.com/en-us/library/gg318049.aspx).</span><span class="sxs-lookup"><span data-stu-id="ea5d9-111">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](https://technet.microsoft.com/en-us/library/gg318049.aspx).</span></span>
- <span data-ttu-id="ea5d9-112">Um computador anfitrião que tenha o Hyper-V ativada.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-112">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="ea5d9-113">Para informações, consulte [descrição geral do Hyper-V](https://technet.microsoft.com/library/hh831531.aspx).</span><span class="sxs-lookup"><span data-stu-id="ea5d9-113">For information, see [Hyper-V overview](https://technet.microsoft.com/library/hh831531.aspx).</span></span>

<span data-ttu-id="ea5d9-114">Ao utilizar o DSC, pode automatizar a instalação de software e configuração para um computador em cima de arranque inicial.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-114">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span>
<span data-ttu-id="ea5d9-115">Fazê-lo ao ou inserirem-se um documento MOF de configuração ou uma configuração meta para suportes de dados (por exemplo, um VHD) para que forem executadas durante o processo de arranque de segurança inicial.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-115">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span>
<span data-ttu-id="ea5d9-116">Este comportamento é especificado pelo [chave de registo DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) chave de registo em **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies**.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-116">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies**.</span></span>
<span data-ttu-id="ea5d9-117">Por predefinição, o valor desta chave é 2, que lhe permite DSC executar no momento do arranque.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-117">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

<span data-ttu-id="ea5d9-118">Se não pretender DSC para executar no momento do arranque, defina o valor da [chave de registo DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) chave de registo para 0.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-118">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="ea5d9-119">Inserir um documento MOF de configuração num VHD</span><span class="sxs-lookup"><span data-stu-id="ea5d9-119">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="ea5d9-120">Inserir uma configuração meta do DSC num VHD</span><span class="sxs-lookup"><span data-stu-id="ea5d9-120">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="ea5d9-121">Desativar o DSC no momento do arranque</span><span class="sxs-lookup"><span data-stu-id="ea5d9-121">Disable DSC at boot time</span></span>

><span data-ttu-id="ea5d9-122">**Nota:** pode inserir ambos `Pending.mof` e `MetaConfig.mof` para um computador ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-122">**Note:** You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
<span data-ttu-id="ea5d9-123">Se ambos os ficheiros estiverem presentes, as definições especificadas no `MetaConfig.mof` têm precedência.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-123">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="ea5d9-124">Inserir um documento MOF de configuração num VHD</span><span class="sxs-lookup"><span data-stu-id="ea5d9-124">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="ea5d9-125">Para enact uma configuração de segurança de arranque inicial, pode inserir um documento MOF configuração compilados num VHD como respetivo `Pending.mof` ficheiro.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-125">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span>
<span data-ttu-id="ea5d9-126">Se o **DSCAutomationHostEnabled** chave de registo está definida como 2 (o valor predefinido), DSC será aplicada a configuração definida pelo `Pending.mof` quando o computador arranca para a primeira vez.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-126">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="ea5d9-127">Neste exemplo, utilizamos a seguinte configuração, irá instalar o IIS no novo computador:</span><span class="sxs-lookup"><span data-stu-id="ea5d9-127">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="ea5d9-128">Para inserir o documento de MOF de configuração no VHD</span><span class="sxs-lookup"><span data-stu-id="ea5d9-128">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="ea5d9-129">Montar o VHD para o qual pretende inserir a configuração ao chamar o [montar VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-129">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span></span> <span data-ttu-id="ea5d9-130">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ea5d9-130">For example:</span></span>

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```
2. <span data-ttu-id="ea5d9-131">Num computador com o PowerShell 5.0 ou posterior, guarde a configuração de acima (**SampleIISInstall**) como um ficheiro de script (. ps1) do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-131">On a computer running PowerShell 5.0 or later, save the above configuration (**SampleIISInstall**) as a PowerShell script (.ps1) file.</span></span>

3. <span data-ttu-id="ea5d9-132">Na consola do PowerShell, navegue para a pasta onde guardou o ficheiro. ps1.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-132">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

4. <span data-ttu-id="ea5d9-133">Execute os seguintes comandos do PowerShell para compilar o documento MOF (para obter informações sobre configurações de DSC a compilação, consulte [configurações de DSC](configurations.md):</span><span class="sxs-lookup"><span data-stu-id="ea5d9-133">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](configurations.md):</span></span>

    ```powershell
    . .\SampleIISInstall.ps1
    SampleIISInstall
    ```

5. <span data-ttu-id="ea5d9-134">Esta ação irá criar um `localhost.mof` ficheiros numa pasta nova denominada `SampleIISInstall`.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-134">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span>
<span data-ttu-id="ea5d9-135">Mudar o nome e mover esse ficheiro para a localização correta no VHD como `Pending.mof` utilizando o [Mover Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-135">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span></span> <span data-ttu-id="ea5d9-136">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ea5d9-136">For example:</span></span>

    ```powershell
        Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
    ```
6. <span data-ttu-id="ea5d9-137">Desmontar o VHD ao chamar o [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-137">Dismount the VHD by calling the [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet.</span></span> <span data-ttu-id="ea5d9-138">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ea5d9-138">For example:</span></span>

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

7. <span data-ttu-id="ea5d9-139">Crie uma VM utilizando o VHD onde instalou o documento de DSC MOF.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-139">Create a VM by using the VHD where you installed the DSC MOF document.</span></span> <span data-ttu-id="ea5d9-140">Depois de iniciais existentes de segurança de arranque e instalação do sistema operativo, será instalado o IIS.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-140">After intial boot-up and operating system installation, IIS will be installed.</span></span>
<span data-ttu-id="ea5d9-141">Pode verificar isto ao chamar o [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-141">You can verify this by calling the [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="ea5d9-142">Inserir uma configuração meta do DSC num VHD</span><span class="sxs-lookup"><span data-stu-id="ea5d9-142">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="ea5d9-143">Também pode configurar um computador para solicitar uma configuração no arranque iniciais existentes-se ao inserirem uma configuração meta do (consulte [configurar o Gestor de configuração Local (MMC)](metaConfig.md)) para o VHD como respetivo `MetaConfig.mof` ficheiro.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-143">You can also configure a computer to pull a configuration at intial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span>
<span data-ttu-id="ea5d9-144">Se o **DSCAutomationHostEnabled** chave de registo está definida como 2 (o valor predefinido), DSC será aplicada a configuração meta do definido pelo `MetaConfig.mof` para MMC quando o computador arranca para a primeira vez.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-144">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value),  DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span>
<span data-ttu-id="ea5d9-145">Se a configuração meta Especifica que o MMC deve solicitar a configurações de um servidor de solicitação, o computador irá tentar solicitar uma configuração a partir desse servidor de solicitação em cima de arranque inicial.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-145">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at inital boot-up.</span></span>
<span data-ttu-id="ea5d9-146">Para obter informações sobre como configurar um servidor de solicitação do DSC, consulte [configurar um servidor de solicitação do DSC web](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="ea5d9-146">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span>

<span data-ttu-id="ea5d9-147">Neste exemplo, utilizamos ambas a configuração descrita na secção anterior (**SampleIISInstall**) e a configuração meta do seguinte:</span><span class="sxs-lookup"><span data-stu-id="ea5d9-147">For this example, we will use both the configuration described in the previous section (**SampleIISInstall**), and the following metaconfiguration:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="ea5d9-148">Para inserir o documento MOF configuração meta no VHD</span><span class="sxs-lookup"><span data-stu-id="ea5d9-148">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="ea5d9-149">Montar o VHD para o qual pretende inserir a configuração meta ao chamar o [montar VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-149">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span></span> <span data-ttu-id="ea5d9-150">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ea5d9-150">For example:</span></span>

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. <span data-ttu-id="ea5d9-151">[Configurar um servidor de solicitação do DSC web](pullServer.md)e guarde o **SampleIISInistall** configuração para a pasta adequada.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-151">[Set up a DSC web pull server](pullServer.md), and save the **SampleIISInistall** configuration to the appropriate folder.</span></span>

3. <span data-ttu-id="ea5d9-152">Num computador com o PowerShell 5.0 ou posterior, guarde a configuração meta do acima (**PullClientBootstrap**) como um ficheiro de script (. ps1) do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-152">On a computer running PowerShell 5.0 or later, save the above metaconfiguration (**PullClientBootstrap**) as a PowerShell script (.ps1) file.</span></span>

4. <span data-ttu-id="ea5d9-153">Na consola do PowerShell, navegue para a pasta onde guardou o ficheiro. ps1.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-153">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

5. <span data-ttu-id="ea5d9-154">Execute os seguintes comandos do PowerShell para compilar o documento MOF configuração meta (para obter informações sobre configurações de DSC a compilação, consulte [configurações de DSC](configurations.md):</span><span class="sxs-lookup"><span data-stu-id="ea5d9-154">Run the following PowerShell commands to compile the  metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](configurations.md):</span></span>

    ```powershell
    . .\PullClientBootstrap.ps1
    PullClientBootstrap
    ```

6. <span data-ttu-id="ea5d9-155">Esta ação irá criar um `localhost.meta.mof` ficheiros numa pasta nova denominada `PullClientBootstrap`.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-155">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span>
<span data-ttu-id="ea5d9-156">Mudar o nome e mover esse ficheiro para a localização correta no VHD como `MetaConfig.mof` utilizando o [Mover Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-156">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span></span>

    ```powershell
    Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\Sytem32\Configuration\MetaConfig.mof
    ```

7. <span data-ttu-id="ea5d9-157">Desmontar o VHD ao chamar o [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-157">Dismount the VHD by calling the [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet.</span></span> <span data-ttu-id="ea5d9-158">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ea5d9-158">For example:</span></span>

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

8. <span data-ttu-id="ea5d9-159">Crie uma VM utilizando o VHD onde instalou o documento de DSC MOF.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-159">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>
<span data-ttu-id="ea5d9-160">Depois de iniciais existentes de segurança de arranque e instalação do sistema operativo, DSC irá solicitar a configuração do servidor de solicitação e IIS será instalado.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-160">After intial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span>
<span data-ttu-id="ea5d9-161">Pode verificar isto ao chamar o [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-161">You can verify this by calling the [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="ea5d9-162">Desativar o DSC no momento do arranque</span><span class="sxs-lookup"><span data-stu-id="ea5d9-162">Disable DSC at boot time</span></span>

<span data-ttu-id="ea5d9-163">Por predefinição, o valor da **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled** chave está definida como 2, que permite uma configuração de DSC executar se o computador está pendente ou atual Estado.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-163">By default, the value of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled** key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="ea5d9-164">Se não pretender que uma configuração para ser executada em cima de arranque inicial, por isso, tem de definir o valor desta chave como 0:</span><span class="sxs-lookup"><span data-stu-id="ea5d9-164">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="ea5d9-165">Montar o VHD ao chamar o [montar VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-165">Mount the VHD by calling the [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span></span> <span data-ttu-id="ea5d9-166">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ea5d9-166">For example:</span></span>

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. <span data-ttu-id="ea5d9-167">Carregar o registo **HKLM\Software** subchave do VHD chamando `reg load`.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-167">Load the registry **HKLM\Software** subkey from the VHD by calling `reg load`.</span></span>

    ```
    reg load HKLM\Vhd E:\Windows\System32\Config\Software`
    ```

3. <span data-ttu-id="ea5d9-168">Navegue para o **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\***  utilizando o fornecedor de registo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-168">Navigate to the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*** by using the PowerShell Registry provider.</span></span>

    ```powershell
    Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
    ```

4. <span data-ttu-id="ea5d9-169">Altere o valor de `DSCAutomationHostEnabled` como 0.</span><span class="sxs-lookup"><span data-stu-id="ea5d9-169">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

    ```powershell
    Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
    ```

5. <span data-ttu-id="ea5d9-170">Descarregar o registo executando os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="ea5d9-170">Unload the registry by running the following commands:</span></span>

    ```powershell
    [gc]::Collect()
    reg unload HKLM\Vhd
    ```

## <a name="see-also"></a><span data-ttu-id="ea5d9-171">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="ea5d9-171">See Also</span></span>

- [<span data-ttu-id="ea5d9-172">Configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="ea5d9-172">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="ea5d9-173">Chave de registo DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="ea5d9-173">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)
- [<span data-ttu-id="ea5d9-174">Configurar o Gestor de Configuração Local (LCM)</span><span class="sxs-lookup"><span data-stu-id="ea5d9-174">Configuring the Local Configuration Manager (LCM)</span></span>](metaConfig.md)
- [<span data-ttu-id="ea5d9-175">Configurar um servidor de solicitação do DSC web</span><span class="sxs-lookup"><span data-stu-id="ea5d9-175">Setting up a DSC web pull server</span></span>](pullServer.md)

