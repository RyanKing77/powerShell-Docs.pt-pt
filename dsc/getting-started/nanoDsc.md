---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Utilizar o DSC no Servidor Nano
ms.openlocfilehash: fd81fe56d16100f45d9ee2dfd8fdc303c2a6c17a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404956"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="c955a-103">Utilizar o DSC no Servidor Nano</span><span class="sxs-lookup"><span data-stu-id="c955a-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="c955a-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c955a-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="c955a-105">**DSC no servidor Nano** é um pacote opcional no `NanoServer\Packages` pasta do suporte de dados do Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="c955a-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="c955a-106">O pacote pode ser instalado quando criar um VHD para um servidor Nano, especificando **Microsoft-NanoServer-DSC-Package** como o valor da **pacotes** parâmetro do **New-NanoServerImage**  função.</span><span class="sxs-lookup"><span data-stu-id="c955a-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="c955a-107">Por exemplo, se estiver a criar um VHD para uma máquina virtual, o comando teria o aspeto semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="c955a-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="c955a-108">Para obter informações sobre como instalar e utilizar o servidor Nano, bem como gerir o servidor Nano com a comunicação remota do PowerShell, consulte [introdução ao Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span><span class="sxs-lookup"><span data-stu-id="c955a-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span></span>

## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="c955a-109">Recursos de DSC disponíveis no servidor Nano</span><span class="sxs-lookup"><span data-stu-id="c955a-109">DSC features available on Nano Server</span></span>

<span data-ttu-id="c955a-110">Como o servidor Nano suporta apenas um conjunto limitado de APIs em comparação com uma versão completa do Windows Server, o DSC no servidor Nano não tem paridade completa funcional com DSC em execução em SKUs completos por enquanto.</span><span class="sxs-lookup"><span data-stu-id="c955a-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="c955a-111">DSC no servidor Nano está em fase de desenvolvimento e ainda não está recursos completos.</span><span class="sxs-lookup"><span data-stu-id="c955a-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

<span data-ttu-id="c955a-112">Os seguintes recursos de DSC estão atualmente disponíveis no servidor Nano:</span><span class="sxs-lookup"><span data-stu-id="c955a-112">The following DSC features are currently available on Nano Server:</span></span>

<span data-ttu-id="c955a-113">Modos push e pull</span><span class="sxs-lookup"><span data-stu-id="c955a-113">Both push and pull modes</span></span>

- <span data-ttu-id="c955a-114">Todos os cmdlets de DSC que existe uma versão completa do Windows Server, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c955a-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
- [<span data-ttu-id="c955a-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c955a-115">Get-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [<span data-ttu-id="c955a-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c955a-116">Set-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [<span data-ttu-id="c955a-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="c955a-117">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [<span data-ttu-id="c955a-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="c955a-118">Disable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [<span data-ttu-id="c955a-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="c955a-119">Start-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [<span data-ttu-id="c955a-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="c955a-120">Stop-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [<span data-ttu-id="c955a-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="c955a-121">Get-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [<span data-ttu-id="c955a-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="c955a-122">Test-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [<span data-ttu-id="c955a-123">Publish-DscConfiguraiton</span><span class="sxs-lookup"><span data-stu-id="c955a-123">Publish-DscConfiguraiton</span></span>](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [<span data-ttu-id="c955a-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="c955a-124">Update-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [<span data-ttu-id="c955a-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="c955a-125">Restore-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [<span data-ttu-id="c955a-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="c955a-126">Remove-DscConfigurationDocument</span></span>](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [<span data-ttu-id="c955a-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="c955a-127">Get-DscConfigurationStatus</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [<span data-ttu-id="c955a-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="c955a-128">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [<span data-ttu-id="c955a-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="c955a-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [<span data-ttu-id="c955a-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="c955a-130">Get-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [<span data-ttu-id="c955a-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="c955a-131">New-DscChecksum</span></span>](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- <span data-ttu-id="c955a-132">Compilar configurações (veja [configurações de DSC](../configurations/configurations.md))</span><span class="sxs-lookup"><span data-stu-id="c955a-132">Compiling configurations (see [DSC configurations](../configurations/configurations.md))</span></span>

  <span data-ttu-id="c955a-133">**Problema:** Encriptação de palavra-passe (consulte [proteger o ficheiro MOF](../pull-server/secureMOF.md)) durante a configuração de compilação não funciona.</span><span class="sxs-lookup"><span data-stu-id="c955a-133">**Issue:** Password encryption (see [Securing the MOF File](../pull-server/secureMOF.md)) during configuration compilation doesn't work.</span></span>

- <span data-ttu-id="c955a-134">Compilar metaconfigurations (consulte [configurar o Gestor de configuração Local](../managing-nodes/metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="c955a-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md))</span></span>

- <span data-ttu-id="c955a-135">Executar um recurso no contexto de usuário (consulte [a executar o DSC com as credenciais de utilizador (RunAs)](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="c955a-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](../configurations/runAsUser.md))</span></span>

- <span data-ttu-id="c955a-136">Recursos baseados na classe (consulte [escrever um recurso personalizado do DSC com classes do PowerShell](../resources/authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="c955a-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](../resources/authoringResourceClass.md))</span></span>

- <span data-ttu-id="c955a-137">Depuração de recursos de DSC (consulte [recursos de DSC de depuração](../troubleshooting/debugResource.md))</span><span class="sxs-lookup"><span data-stu-id="c955a-137">Debugging of DSC resources (see [Debugging DSC resources](../troubleshooting/debugResource.md))</span></span>

  <span data-ttu-id="c955a-138">**Problema:** Não funciona se um recurso está a utilizar PsDscRunAsCredential (consulte [a executar o DSC com as credenciais de utilizador](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="c955a-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](../configurations/runAsUser.md))</span></span>

- [<span data-ttu-id="c955a-139">Especificar dependências entre nós</span><span class="sxs-lookup"><span data-stu-id="c955a-139">Specifying cross-node dependencies</span></span>](../configurations/crossNodeDependencies.md)

- [<span data-ttu-id="c955a-140">Controle de versão do recurso</span><span class="sxs-lookup"><span data-stu-id="c955a-140">Resource versioning</span></span>](../configurations/sxsResource.md)

- <span data-ttu-id="c955a-141">Cliente de solicitação (configurações e recursos) (consulte [como configurar um cliente de solicitação através de nomes de configuração](../pull-server/pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="c955a-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](../pull-server/pullClientConfigNames.md))</span></span>

- [<span data-ttu-id="c955a-142">Configurações parciais (pull & push)</span><span class="sxs-lookup"><span data-stu-id="c955a-142">Partial configurations (pull & push)</span></span>](../pull-server/partialConfigs.md)

- [<span data-ttu-id="c955a-143">Relatórios para o servidor de solicitação</span><span class="sxs-lookup"><span data-stu-id="c955a-143">Reporting to pull server</span></span>](../pull-server/reportServer.md)

- <span data-ttu-id="c955a-144">Encriptação do MOF</span><span class="sxs-lookup"><span data-stu-id="c955a-144">MOF encryption</span></span>

- <span data-ttu-id="c955a-145">Registo de eventos</span><span class="sxs-lookup"><span data-stu-id="c955a-145">Event logging</span></span>

- <span data-ttu-id="c955a-146">Relatórios de DSC de automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="c955a-146">Azure Automation DSC reporting</span></span>

- <span data-ttu-id="c955a-147">Recursos que são totalmente funcionais</span><span class="sxs-lookup"><span data-stu-id="c955a-147">Resources that are fully functional</span></span>

- <span data-ttu-id="c955a-148">**Arquivo**</span><span class="sxs-lookup"><span data-stu-id="c955a-148">**Archive**</span></span>
- <span data-ttu-id="c955a-149">**Ambiente**</span><span class="sxs-lookup"><span data-stu-id="c955a-149">**Environment**</span></span>
- <span data-ttu-id="c955a-150">**Ficheiro**</span><span class="sxs-lookup"><span data-stu-id="c955a-150">**File**</span></span>
- <span data-ttu-id="c955a-151">**Registo**</span><span class="sxs-lookup"><span data-stu-id="c955a-151">**Log**</span></span>
- <span data-ttu-id="c955a-152">**ProcessSet**</span><span class="sxs-lookup"><span data-stu-id="c955a-152">**ProcessSet**</span></span>
- <span data-ttu-id="c955a-153">**registo**</span><span class="sxs-lookup"><span data-stu-id="c955a-153">**Registry**</span></span>
- <span data-ttu-id="c955a-154">**Script**</span><span class="sxs-lookup"><span data-stu-id="c955a-154">**Script**</span></span>
- <span data-ttu-id="c955a-155">**WindowsPackageCab**</span><span class="sxs-lookup"><span data-stu-id="c955a-155">**WindowsPackageCab**</span></span>
- <span data-ttu-id="c955a-156">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="c955a-156">**WindowsProcess**</span></span>
- <span data-ttu-id="c955a-157">**WaitForAll** (consulte [especificar dependências entre nós](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="c955a-157">**WaitForAll** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="c955a-158">**WaitForAny** (consulte [especificar dependências entre nós](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="c955a-158">**WaitForAny** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="c955a-159">**WaitForSome** (consulte [especificar dependências entre nós](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="c955a-159">**WaitForSome** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>

- <span data-ttu-id="c955a-160">Recursos que são parcialmente funcionais</span><span class="sxs-lookup"><span data-stu-id="c955a-160">Resources that are partially functional</span></span>
- <span data-ttu-id="c955a-161">**Grupo**</span><span class="sxs-lookup"><span data-stu-id="c955a-161">**Group**</span></span>
- <span data-ttu-id="c955a-162">**GroupSet**</span><span class="sxs-lookup"><span data-stu-id="c955a-162">**GroupSet**</span></span>

  <span data-ttu-id="c955a-163">**Problema:** Acima recursos falhar se a instância específica é chamada duas vezes (a ser executada duas vezes a mesma configuração)</span><span class="sxs-lookup"><span data-stu-id="c955a-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

- <span data-ttu-id="c955a-164">**Serviço**</span><span class="sxs-lookup"><span data-stu-id="c955a-164">**Service**</span></span>
- <span data-ttu-id="c955a-165">**ServiceSet**</span><span class="sxs-lookup"><span data-stu-id="c955a-165">**ServiceSet**</span></span>

  <span data-ttu-id="c955a-166">**Problema:** Só funciona para iniciar/parar serviço (estado).</span><span class="sxs-lookup"><span data-stu-id="c955a-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="c955a-167">Falhar, se um tentar altere os outros atributos de serviço como statuptype, credenciais, descrição etc...</span><span class="sxs-lookup"><span data-stu-id="c955a-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="c955a-168">O erro gerado é semelhante a:</span><span class="sxs-lookup"><span data-stu-id="c955a-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="c955a-169">*Não é possível localizar o tipo [management.managementobject]: Certifique-se de que o assembly que contém este tipo é carregado.*</span><span class="sxs-lookup"><span data-stu-id="c955a-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

- <span data-ttu-id="c955a-170">Recursos que não estão funcionais</span><span class="sxs-lookup"><span data-stu-id="c955a-170">Resources that are not functional</span></span>
- <span data-ttu-id="c955a-171">**Utilizador**</span><span class="sxs-lookup"><span data-stu-id="c955a-171">**User**</span></span>

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="c955a-172">Recursos de DSC não está disponíveis no servidor Nano</span><span class="sxs-lookup"><span data-stu-id="c955a-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="c955a-173">Os seguintes recursos de DSC não estão atualmente disponíveis no servidor Nano:</span><span class="sxs-lookup"><span data-stu-id="c955a-173">The following DSC features are not currently available on Nano Server:</span></span>

- <span data-ttu-id="c955a-174">A desencriptação de documento MOF com incorrectas encriptados</span><span class="sxs-lookup"><span data-stu-id="c955a-174">Decrypting MOF document with encrypted password(s)</span></span>
- <span data-ttu-id="c955a-175">Servidor de solicitação, não pode atualmente configurar um servidor de solicitação no servidor Nano</span><span class="sxs-lookup"><span data-stu-id="c955a-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
- <span data-ttu-id="c955a-176">Tudo o que não está na lista de recurso funciona</span><span class="sxs-lookup"><span data-stu-id="c955a-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="c955a-177">Utilizar recursos de DSC personalizados no servidor Nano</span><span class="sxs-lookup"><span data-stu-id="c955a-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="c955a-178">Devido a um limitado conjuntos de APIs do Windows e bibliotecas CLR disponíveis no servidor Nano, os recursos de DSC que funcionam na versão CLR completa do Windows não necessariamente funcionar no servidor Nano.</span><span class="sxs-lookup"><span data-stu-id="c955a-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="c955a-179">Conclua o teste de ponto-a-ponto antes de implementar quaisquer recursos personalizados de DSC para um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="c955a-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="c955a-180">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="c955a-180">See Also</span></span>

- [<span data-ttu-id="c955a-181">Introdução ao servidor Nano</span><span class="sxs-lookup"><span data-stu-id="c955a-181">Getting Started with Nano Server</span></span>](/windows-server/get-started/getting-started-with-nano-server)
