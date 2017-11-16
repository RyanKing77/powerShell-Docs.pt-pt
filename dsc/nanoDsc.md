---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Utilizar o DSC no servidor de Nano
ms.openlocfilehash: 2233106bfd07144132f95ea7957ebfa3248ca219
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="fb367-103">Utilizar o DSC no servidor de Nano</span><span class="sxs-lookup"><span data-stu-id="fb367-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="fb367-104">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fb367-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="fb367-105">**DSC no servidor de Nano** é um pacote opcional no `NanoServer\Packages` pasta do suporte de dados do Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="fb367-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="fb367-106">O pacote pode ser instalado quando criar um VHD para um servidor de nano for apresentado, especificando **Microsoft NanoServer-DSC pacote** como o valor a **pacotes** parâmetro do **NanoServerImage novo**  função.</span><span class="sxs-lookup"><span data-stu-id="fb367-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="fb367-107">Por exemplo, se estiver a criar um VHD para uma máquina virtual, o comando seria o seguinte aspeto:</span><span class="sxs-lookup"><span data-stu-id="fb367-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="fb367-108">Para obter informações sobre como instalar e utilizar o servidor de nano for apresentado, bem como gerir o servidor de Nano com comunicação remota do PowerShell, consulte [introdução ao servidor Nano](https://technet.microsoft.com/en-us/library/mt126167.aspx).</span><span class="sxs-lookup"><span data-stu-id="fb367-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](https://technet.microsoft.com/en-us/library/mt126167.aspx).</span></span>


## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="fb367-109">Funcionalidades de DSC disponíveis no servidor de Nano</span><span class="sxs-lookup"><span data-stu-id="fb367-109">DSC features available on Nano Server</span></span>

 <span data-ttu-id="fb367-110">Porque o servidor de Nano suporta apenas um conjunto limitado de APIs comparado comparadas uma versão completa do Windows Server, DSC no servidor de Nano tem paridade funcional completa com DSC em execução no SKUs completos para o tempo a ser.</span><span class="sxs-lookup"><span data-stu-id="fb367-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="fb367-111">DSC no servidor de Nano está em desenvolvimento Active Directory e não ainda funcionalidade completa.</span><span class="sxs-lookup"><span data-stu-id="fb367-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>
 
 <span data-ttu-id="fb367-112">As seguintes funcionalidades de DSC estão atualmente disponíveis no servidor de Nano:</span><span class="sxs-lookup"><span data-stu-id="fb367-112">The following DSC features are currently available on Nano Server:</span></span> 


* <span data-ttu-id="fb367-113">Modos push e pull</span><span class="sxs-lookup"><span data-stu-id="fb367-113">Both push and pull modes</span></span>

* <span data-ttu-id="fb367-114">Todos os cmdlets de DSC que existe uma versão completa do Windows Server, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="fb367-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span> 
  * [<span data-ttu-id="fb367-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="fb367-115">Get-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/en-us/library/dn407378.aspx)
  * [<span data-ttu-id="fb367-116">Conjunto DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="fb367-116">Set-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/en-us/library/dn521621.aspx)   
  * [<span data-ttu-id="fb367-117">Ativar DscDebug</span><span class="sxs-lookup"><span data-stu-id="fb367-117">Enable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [<span data-ttu-id="fb367-118">Desativar DscDebug</span><span class="sxs-lookup"><span data-stu-id="fb367-118">Disable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517872.aspx)       
  * [<span data-ttu-id="fb367-119">Início DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="fb367-119">Start-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [<span data-ttu-id="fb367-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="fb367-120">Stop-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [<span data-ttu-id="fb367-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="fb367-121">Get-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [<span data-ttu-id="fb367-122">Teste DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="fb367-122">Test-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407382.aspx)      
  * [<span data-ttu-id="fb367-123">DscConfiguraiton publicar</span><span class="sxs-lookup"><span data-stu-id="fb367-123">Publish-DscConfiguraiton</span></span>](https://technet.microsoft.com/en-us/library/mt517875.aspx) 
  * [<span data-ttu-id="fb367-124">Atualização DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="fb367-124">Update-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [<span data-ttu-id="fb367-125">Restauro DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="fb367-125">Restore-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [<span data-ttu-id="fb367-126">Remover DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="fb367-126">Remove-DscConfigurationDocument</span></span>](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [<span data-ttu-id="fb367-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="fb367-127">Get-DscConfigurationStatus</span></span>](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [<span data-ttu-id="fb367-128">DscResource invocar</span><span class="sxs-lookup"><span data-stu-id="fb367-128">Invoke-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [<span data-ttu-id="fb367-129">Localizar DscResource</span><span class="sxs-lookup"><span data-stu-id="fb367-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [<span data-ttu-id="fb367-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="fb367-130">Get-DscResource</span></span>](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [<span data-ttu-id="fb367-131">Novo DscChecksum</span><span class="sxs-lookup"><span data-stu-id="fb367-131">New-DscChecksum</span></span>](https://technet.microsoft.com/en-us/library/dn521622.aspx)    

* <span data-ttu-id="fb367-132">Compilar configurações (consulte [configurações de DSC](configurations.md))</span><span class="sxs-lookup"><span data-stu-id="fb367-132">Compiling configurations (see [DSC configurations](configurations.md))</span></span>

  <span data-ttu-id="fb367-133">**Problema:** encriptação da palavra-passe (consulte [proteger o ficheiro MOF](securemof.md)) durante a configuração de compilação não funciona.</span><span class="sxs-lookup"><span data-stu-id="fb367-133">**Issue:** Password encryption (see [Securing the MOF File](securemof.md)) during configuration compilation doesn't work.</span></span>

* <span data-ttu-id="fb367-134">Compilar metaconfigurations (consulte [configurar o Gestor de configuração Local](metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="fb367-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](metaConfig.md))</span></span>

* <span data-ttu-id="fb367-135">Executar um recurso no contexto de utilizador (consulte [DSC em execução com as credenciais de utilizador (RunAs)](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="fb367-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](runAsUser.md))</span></span>

* <span data-ttu-id="fb367-136">Recursos baseados em classe (consulte [escrever um recurso personalizado de DSC com classes de PowerShell](authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="fb367-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](authoringResourceClass.md))</span></span>

* <span data-ttu-id="fb367-137">A depuração de recursos de DSC (consulte [recursos de DSC depuração](debugresource.md))</span><span class="sxs-lookup"><span data-stu-id="fb367-137">Debugging of DSC resources (see [Debugging DSC resources](debugresource.md))</span></span>
  
  <span data-ttu-id="fb367-138">**Problema:** não funciona se um recurso está a utilizar PsDscRunAsCredential (consulte [DSC em execução com as credenciais de utilizador](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="fb367-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](runAsUser.md))</span></span>

* [<span data-ttu-id="fb367-139">Especificar dependências entre nós</span><span class="sxs-lookup"><span data-stu-id="fb367-139">Specifying cross-node dependencies</span></span>](crossNodeDependencies.md) 

* [<span data-ttu-id="fb367-140">Controlo de versões do recurso</span><span class="sxs-lookup"><span data-stu-id="fb367-140">Resource versioning</span></span>](sxsResource.md)

* <span data-ttu-id="fb367-141">Cliente de extração (configurações e recursos) (consulte [configurar um cliente de solicitação utilizando nomes de configuração](pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="fb367-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](pullClientConfigNames.md))</span></span>

* [<span data-ttu-id="fb367-142">Configurações parciais (extração & push)</span><span class="sxs-lookup"><span data-stu-id="fb367-142">Partial configurations (pull & push)</span></span>](partialConfigs.md)

* [<span data-ttu-id="fb367-143">Reportam ao servidor de solicitação</span><span class="sxs-lookup"><span data-stu-id="fb367-143">Reporting to pull server</span></span>](reportServer.md) 

* <span data-ttu-id="fb367-144">Encriptação de MOF</span><span class="sxs-lookup"><span data-stu-id="fb367-144">MOF encryption</span></span>

* <span data-ttu-id="fb367-145">Registo de eventos</span><span class="sxs-lookup"><span data-stu-id="fb367-145">Event logging</span></span>

* <span data-ttu-id="fb367-146">Relatório de DSC da automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="fb367-146">Azure Automation DSC reporting</span></span>

* <span data-ttu-id="fb367-147">Recursos que são totalmente funcionais</span><span class="sxs-lookup"><span data-stu-id="fb367-147">Resources that are fully functional</span></span>
  * [<span data-ttu-id="fb367-148">Arquivo</span><span class="sxs-lookup"><span data-stu-id="fb367-148">Archive</span></span>](archiveResource.md)
  * [<span data-ttu-id="fb367-149">Ambiente</span><span class="sxs-lookup"><span data-stu-id="fb367-149">Environment</span></span>](environmentResource.md)
  * [<span data-ttu-id="fb367-150">Ficheiro</span><span class="sxs-lookup"><span data-stu-id="fb367-150">File</span></span>](fileResource.md)
  * [<span data-ttu-id="fb367-151">Registo</span><span class="sxs-lookup"><span data-stu-id="fb367-151">Log</span></span>](logResource.md)
  * <span data-ttu-id="fb367-152">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="fb367-152">ProcessSet</span></span>
  * [<span data-ttu-id="fb367-153">Registo</span><span class="sxs-lookup"><span data-stu-id="fb367-153">Registry</span></span>](registryResource.md)
  * [<span data-ttu-id="fb367-154">Script</span><span class="sxs-lookup"><span data-stu-id="fb367-154">Script</span></span>](scriptResource.md)
  * <span data-ttu-id="fb367-155">WindowsPackageCab</span><span class="sxs-lookup"><span data-stu-id="fb367-155">WindowsPackageCab</span></span>
  * [<span data-ttu-id="fb367-156">WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="fb367-156">WindowsProcess</span></span>](windowsProcessResource.md)
  * <span data-ttu-id="fb367-157">WaitForAll (consulte [especificar dependências entre nós](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="fb367-157">WaitForAll (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="fb367-158">WaitForAny (consulte [especificar dependências entre nós](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="fb367-158">WaitForAny (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="fb367-159">WaitForSome (consulte [especificar dependências entre nós](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="fb367-159">WaitForSome (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>

* <span data-ttu-id="fb367-160">Recursos que estão parcialmente funcionais</span><span class="sxs-lookup"><span data-stu-id="fb367-160">Resources that are partially functional</span></span>
  * [<span data-ttu-id="fb367-161">Grupo</span><span class="sxs-lookup"><span data-stu-id="fb367-161">Group</span></span>](groupResource.md)
  * <span data-ttu-id="fb367-162">GroupSet</span><span class="sxs-lookup"><span data-stu-id="fb367-162">GroupSet</span></span>
  
  <span data-ttu-id="fb367-163">**Problema:** acima recursos falhar se a instância específica é chamada duas vezes (com duas vezes a mesma configuração)</span><span class="sxs-lookup"><span data-stu-id="fb367-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>
  
  * [<span data-ttu-id="fb367-164">Serviço</span><span class="sxs-lookup"><span data-stu-id="fb367-164">Service</span></span>](serviceResource.md)
  * <span data-ttu-id="fb367-165">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="fb367-165">ServiceSet</span></span>
  
  <span data-ttu-id="fb367-166">**Problema:** só funciona para iniciar/parar serviço (estado).</span><span class="sxs-lookup"><span data-stu-id="fb367-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="fb367-167">Falhar, se um tentar alterar outros atributos de serviço startuptype, as credenciais, descrição, etc..</span><span class="sxs-lookup"><span data-stu-id="fb367-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="fb367-168">O erro emitido é semelhante a:</span><span class="sxs-lookup"><span data-stu-id="fb367-168">The error thrown is similar to:</span></span>
  
  <span data-ttu-id="fb367-169">*Não é possível localizar o tipo [management.managementobject]: Certifique-se de que a assemblagem que contém este tipo está carregada.*</span><span class="sxs-lookup"><span data-stu-id="fb367-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>
  
* <span data-ttu-id="fb367-170">Recursos que não estão funcionais</span><span class="sxs-lookup"><span data-stu-id="fb367-170">Resources that are not functional</span></span>
  * [<span data-ttu-id="fb367-171">Utilizador</span><span class="sxs-lookup"><span data-stu-id="fb367-171">User</span></span>](userResource.md)
  

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="fb367-172">Funcionalidades de DSC não está disponíveis no servidor de Nano</span><span class="sxs-lookup"><span data-stu-id="fb367-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="fb367-173">As seguintes funcionalidades de DSC não estão atualmente disponíveis no servidor de Nano:</span><span class="sxs-lookup"><span data-stu-id="fb367-173">The following DSC features are not currently available on Nano Server:</span></span>

* <span data-ttu-id="fb367-174">Desencriptar MOF documento com incorrectas encriptados</span><span class="sxs-lookup"><span data-stu-id="fb367-174">Decrypting MOF document with encrypted password(s)</span></span> 
* <span data-ttu-id="fb367-175">Servidor de solicitação – não pode atualmente configurar um servidor de solicitação no servidor de Nano</span><span class="sxs-lookup"><span data-stu-id="fb367-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
* <span data-ttu-id="fb367-176">Tudo o que não se encontra na lista de funcionalidade funciona</span><span class="sxs-lookup"><span data-stu-id="fb367-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="fb367-177">Utilizar recursos de DSC personalizados no servidor de Nano</span><span class="sxs-lookup"><span data-stu-id="fb367-177">Using custom DSC resources on Nano Server</span></span>
 
<span data-ttu-id="fb367-178">Devido a um conjuntos limitado das APIs do Windows e estão disponíveis no Nano servidor de bibliotecas CLR, recursos de DSC funcionam na versão CLR completa do Windows não necessariamente funcionam no servidor de nano for apresentado.</span><span class="sxs-lookup"><span data-stu-id="fb367-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span> <span data-ttu-id="fb367-179">Conclua o teste de ponto-a-ponto antes de implementar quaisquer recursos personalizados do DSC no ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="fb367-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb367-180">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="fb367-180">See Also</span></span>
- [<span data-ttu-id="fb367-181">Introdução ao servidor Nano</span><span class="sxs-lookup"><span data-stu-id="fb367-181">Getting Started with Nano Server</span></span>](https://technet.microsoft.com/en-us/library/mt126167.aspx)

