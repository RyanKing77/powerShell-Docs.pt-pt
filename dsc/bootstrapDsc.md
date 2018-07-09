---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Configurar uma máquina virtual no arranque inicial através da utilização de DSC
ms.openlocfilehash: 2f228a38379d1e65b31c03594e876f7226474fc3
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893357"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="c1ef3-103">Configurar uma máquina virtual no arranque inicial através da utilização de DSC</span><span class="sxs-lookup"><span data-stu-id="c1ef3-103">Configure a virtual machines at initial boot-up by using DSC</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c1ef3-104">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c1ef3-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="requirements"></a><span data-ttu-id="c1ef3-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c1ef3-105">Requirements</span></span>

> [!NOTE] 
> <span data-ttu-id="c1ef3-106">O **DSCAutomationHostEnabled** chave de registo descrito neste tópico não está disponível no PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-106">The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span>
> <span data-ttu-id="c1ef3-107">Para obter informações sobre como configurar novas máquinas virtuais no arranque inicial no PowerShell 4.0, consulte [pretende automaticamente configurar seu máquinas usando o DSC no inicial arranque?] > (https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span><span class="sxs-lookup"><span data-stu-id="c1ef3-107">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?]> (https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

<span data-ttu-id="c1ef3-108">Para executar estes exemplos, terá de:</span><span class="sxs-lookup"><span data-stu-id="c1ef3-108">To run these examples, you will need:</span></span>

- <span data-ttu-id="c1ef3-109">Um VHD de arranque para trabalhar com.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-109">A bootable VHD to work with.</span></span> <span data-ttu-id="c1ef3-110">Pode baixar uma imagem ISO com uma cópia de avaliação do Windows Server 2016 em [Centro de avaliação TechNet](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="c1ef3-110">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span> <span data-ttu-id="c1ef3-111">Pode encontrar instruções sobre como criar um VHD a partir de uma imagem ISO na [criar suportes discos de rígido virtuais](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="c1ef3-111">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span></span>
- <span data-ttu-id="c1ef3-112">Um computador anfitrião que tenha o Hyper-V ativada.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-112">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="c1ef3-113">Para obter informações, consulte [descrição geral do Hyper-V](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="c1ef3-113">For information, see [Hyper-V overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span></span>

  <span data-ttu-id="c1ef3-114">Ao utilizar o DSC, pode automatizar a instalação de software e configuração para um computador no arranque inicial.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-114">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span>
  <span data-ttu-id="c1ef3-115">Pode fazê-lo por qualquer um dos injetar um documento de MOF de configuração ou um metaconfiguration suportes de dados (por exemplo, um VHD) para que estas são executadas durante o processo de inicialização inicial.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-115">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span>
  <span data-ttu-id="c1ef3-116">Este comportamento é especificado pela [de registo dscautomationhostenabled](DSCAutomationHostEnabled.md) chave de Registro em `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies`.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-116">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies`.</span></span>
  <span data-ttu-id="c1ef3-117">Por predefinição, o valor desta chave é 2, que permite a DSC ser executado no momento da inicialização.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-117">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

  <span data-ttu-id="c1ef3-118">Se não pretender DSC para ser executado no momento da inicialização, defina o valor do [de registo dscautomationhostenabled](DSCAutomationHostEnabled.md) chave de registo para 0.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-118">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="c1ef3-119">Inserir um documento de MOF de configuração num VHD</span><span class="sxs-lookup"><span data-stu-id="c1ef3-119">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="c1ef3-120">Injetar um metaconfiguration DSC num VHD</span><span class="sxs-lookup"><span data-stu-id="c1ef3-120">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="c1ef3-121">Desativar o DSC no momento da inicialização</span><span class="sxs-lookup"><span data-stu-id="c1ef3-121">Disable DSC at boot time</span></span>

> [!NOTE]
> <span data-ttu-id="c1ef3-122">Pode injetar ambos `Pending.mof` e `MetaConfig.mof` num computador ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-122">You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
> <span data-ttu-id="c1ef3-123">Se ambos os ficheiros estiverem presentes, as definições especificadas no `MetaConfig.mof` têm precedência.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-123">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="c1ef3-124">Inserir um documento de MOF de configuração num VHD</span><span class="sxs-lookup"><span data-stu-id="c1ef3-124">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="c1ef3-125">Adotar uma configuração no arranque inicial, pode injetar um documento MOF de configuração compilada no VHD como seu `Pending.mof` ficheiro.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-125">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span>
<span data-ttu-id="c1ef3-126">Se o **DSCAutomationHostEnabled** chave de registo está definida como 2 (o valor predefinido), DSC irá aplicar a configuração definida por `Pending.mof` quando o computador é inicializado na primeira vez.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-126">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="c1ef3-127">Neste exemplo, utilizamos a configuração seguinte, que irá instalar o IIS no novo computador:</span><span class="sxs-lookup"><span data-stu-id="c1ef3-127">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

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

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="c1ef3-128">Para inserir o documento de MOF de configuração no VHD</span><span class="sxs-lookup"><span data-stu-id="c1ef3-128">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="c1ef3-129">Montar o VHD para o qual deseja injetar a configuração ao chamar o [montagem VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-129">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="c1ef3-130">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c1ef3-130">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="c1ef3-131">Num computador com o PowerShell 5.0 ou posterior, guarde a configuração acima (**SampleIISInstall**) como um ficheiro de script (. ps1) do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-131">On a computer running PowerShell 5.0 or later, save the above configuration (**SampleIISInstall**) as a PowerShell script (.ps1) file.</span></span>

3. <span data-ttu-id="c1ef3-132">Na consola do PowerShell, navegue para a pasta onde guardou o ficheiro. ps1.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-132">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

4. <span data-ttu-id="c1ef3-133">Execute os seguintes comandos do PowerShell para compilar o documento MOF (para obter informações sobre como compilar configurações de DSC, veja [configurações de DSC](configurations.md):</span><span class="sxs-lookup"><span data-stu-id="c1ef3-133">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](configurations.md):</span></span>

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. <span data-ttu-id="c1ef3-134">Esta ação irá criar um `localhost.mof` arquivo numa nova pasta chamada `SampleIISInstall`.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-134">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span>
   <span data-ttu-id="c1ef3-135">Mudar o nome e mover esse arquivo para a localização correta no VHD como `Pending.mof` utilizando o [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-135">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span></span> <span data-ttu-id="c1ef3-136">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c1ef3-136">For example:</span></span>

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. <span data-ttu-id="c1ef3-137">Desmonte o VHD ao chamar o [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-137">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="c1ef3-138">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c1ef3-138">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. <span data-ttu-id="c1ef3-139">Crie uma VM com o VHD onde instalou o documento MOF de DSC.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-139">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="c1ef3-140">Depois do de segurança de arranque e instalação do sistema operativo, será instalado o IIS.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-140">After intial boot-up and operating system installation, IIS will be installed.</span></span>
<span data-ttu-id="c1ef3-141">Pode verificar isto ao chamar o [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-141">You can verify this by calling the [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="c1ef3-142">Injetar um metaconfiguration DSC num VHD</span><span class="sxs-lookup"><span data-stu-id="c1ef3-142">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="c1ef3-143">Também pode configurar um computador para solicitar uma configuração no arranque o injetando um metaconfiguration (consulte [configurar o Gestor de configuração Local (LCM)](metaConfig.md)) no VHD como seu `MetaConfig.mof` ficheiro.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-143">You can also configure a computer to pull a configuration at intial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span>
<span data-ttu-id="c1ef3-144">Se o **DSCAutomationHostEnabled** chave de registo é definida como 2 (o valor predefinido), DSC irá aplicar metaconfiguration definido pelo `MetaConfig.mof` para o LCM quando o computador arranca tendo em vista a primeira vez.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-144">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value),  DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span>
<span data-ttu-id="c1ef3-145">Se o metaconfiguration Especifica que o LCM deve solicitar configurações a partir de um servidor de solicitação, o computador irá tentar extrair uma configuração a partir desse servidor de solicitação no arranque inicial.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-145">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at inital boot-up.</span></span>
<span data-ttu-id="c1ef3-146">Para obter informações sobre como configurar um servidor de solicitação de DSC, veja [como configurar um servidor de solicitação do DSC web](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="c1ef3-146">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span>

<span data-ttu-id="c1ef3-147">Neste exemplo, utilizamos os dois a configuração descrita na secção anterior (**SampleIISInstall**) e o metaconfiguration seguinte:</span><span class="sxs-lookup"><span data-stu-id="c1ef3-147">For this example, we will use both the configuration described in the previous section (**SampleIISInstall**), and the following metaconfiguration:</span></span>

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="c1ef3-148">Para inserir o documento MOF metaconfiguration no VHD</span><span class="sxs-lookup"><span data-stu-id="c1ef3-148">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="c1ef3-149">Montar o VHD para o qual deseja injetar o metaconfiguration ao chamar o [montagem VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-149">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="c1ef3-150">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c1ef3-150">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="c1ef3-151">[Configurar um servidor de solicitação da web de DSC](pullServer.md)e guarde o **SampleIISInistall** configuração para a pasta adequada.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-151">[Set up a DSC web pull server](pullServer.md), and save the **SampleIISInistall** configuration to the appropriate folder.</span></span>

3. <span data-ttu-id="c1ef3-152">Num computador com o PowerShell 5.0 ou posterior, guarde o metaconfiguration acima (**PullClientBootstrap**) como um ficheiro de script (. ps1) do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-152">On a computer running PowerShell 5.0 or later, save the above metaconfiguration (**PullClientBootstrap**) as a PowerShell script (.ps1) file.</span></span>

4. <span data-ttu-id="c1ef3-153">Na consola do PowerShell, navegue para a pasta onde guardou o ficheiro. ps1.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-153">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

5. <span data-ttu-id="c1ef3-154">Execute os seguintes comandos do PowerShell para compilar o documento MOF metaconfiguration (para obter informações sobre como compilar configurações de DSC, veja [configurações de DSC](configurations.md):</span><span class="sxs-lookup"><span data-stu-id="c1ef3-154">Run the following PowerShell commands to compile the  metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](configurations.md):</span></span>

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. <span data-ttu-id="c1ef3-155">Esta ação irá criar um `localhost.meta.mof` arquivo numa nova pasta chamada `PullClientBootstrap`.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-155">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span>
   <span data-ttu-id="c1ef3-156">Mudar o nome e mover esse arquivo para a localização correta no VHD como `MetaConfig.mof` utilizando o [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-156">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. <span data-ttu-id="c1ef3-157">Desmonte o VHD ao chamar o [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-157">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="c1ef3-158">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c1ef3-158">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. <span data-ttu-id="c1ef3-159">Crie uma VM com o VHD onde instalou o documento MOF de DSC.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-159">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="c1ef3-160">Depois do de segurança de arranque e instalação do sistema operativo, DSC irá fazer com que a configuração do servidor de solicitação e IIS será instalado.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-160">After intial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span>
<span data-ttu-id="c1ef3-161">Pode verificar isto ao chamar o [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-161">You can verify this by calling the [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="c1ef3-162">Desativar o DSC no momento da inicialização</span><span class="sxs-lookup"><span data-stu-id="c1ef3-162">Disable DSC at boot time</span></span>

<span data-ttu-id="c1ef3-163">Por predefinição, o valor da `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled` chave está definida como 2, que permite uma configuração de DSC para ser executada se o computador está no estado atual ou pendente.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-163">By default, the value of the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled` key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="c1ef3-164">Se não pretender que uma configuração de executar no arranque inicial, por isso, precisa definir o valor desta chave como 0:</span><span class="sxs-lookup"><span data-stu-id="c1ef3-164">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="c1ef3-165">Montar o VHD ao chamar o [montagem VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-165">Mount the VHD by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="c1ef3-166">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c1ef3-166">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="c1ef3-167">Carregar o Registro `HKLM\Software` subchave de VHD chamando `reg load`.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-167">Load the registry `HKLM\Software` subkey from the VHD by calling `reg load`.</span></span>

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. <span data-ttu-id="c1ef3-168">Navegue para o `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*` utilizando o fornecedor de registo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-168">Navigate to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*` by using the PowerShell Registry provider.</span></span>

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
   ```

4. <span data-ttu-id="c1ef3-169">Alterar o valor de `DSCAutomationHostEnabled` como 0.</span><span class="sxs-lookup"><span data-stu-id="c1ef3-169">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. <span data-ttu-id="c1ef3-170">Descarrega o registo ao executar os comandos seguintes:</span><span class="sxs-lookup"><span data-stu-id="c1ef3-170">Unload the registry by running the following commands:</span></span>

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a><span data-ttu-id="c1ef3-171">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="c1ef3-171">See Also</span></span>

[<span data-ttu-id="c1ef3-172">Configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="c1ef3-172">DSC Configurations</span></span>](configurations.md)

[<span data-ttu-id="c1ef3-173">Chave de registo DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="c1ef3-173">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)

[<span data-ttu-id="c1ef3-174">Configurar o Gestor de Configuração Local (LCM)</span><span class="sxs-lookup"><span data-stu-id="c1ef3-174">Configuring the Local Configuration Manager (LCM)</span></span>](metaConfig.md)

[<span data-ttu-id="c1ef3-175">Como configurar um servidor de solicitação da web de DSC</span><span class="sxs-lookup"><span data-stu-id="c1ef3-175">Setting up a DSC web pull server</span></span>](pullServer.md)
