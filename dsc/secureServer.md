---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Melhores práticas do servidor de solicitação
ms.openlocfilehash: d8d8667e2fc608e0c5948a0b5046bf92801b49db
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="d34c6-103">Melhores práticas do servidor de solicitação</span><span class="sxs-lookup"><span data-stu-id="d34c6-103">Pull server best practices</span></span>

><span data-ttu-id="d34c6-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d34c6-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d34c6-105">O servidor de solicitação (funcionalidade do Windows *DSC serviço*) é um componente suportado do Windows Server no entanto, são não planos para oferecer novas funcionalidades ou capacidades.</span><span class="sxs-lookup"><span data-stu-id="d34c6-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="d34c6-106">É recomendado para começar a transição geridos os clientes [Automation DSC do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação no Windows Server) ou uma das soluções de Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="d34c6-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="d34c6-107">Resumo: Este documento destina-se para incluir o processo e extensibilidade para ajudá-lo engenheiros estiver a preparar para a solução.</span><span class="sxs-lookup"><span data-stu-id="d34c6-107">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="d34c6-108">Detalhes devem fornecer melhores práticas, conforme identificado por clientes e, em seguida, validar pela equipa do produto para garantir que as recomendações são direcionadas para o futura e considerados estáveis.</span><span class="sxs-lookup"><span data-stu-id="d34c6-108">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

| |<span data-ttu-id="d34c6-109">Informações do documento</span><span class="sxs-lookup"><span data-stu-id="d34c6-109">Doc Info</span></span>|
|:---|:---|
<span data-ttu-id="d34c6-110">autor</span><span class="sxs-lookup"><span data-stu-id="d34c6-110">Author</span></span> | <span data-ttu-id="d34c6-111">Miguel Greene</span><span class="sxs-lookup"><span data-stu-id="d34c6-111">Michael Greene</span></span>
<span data-ttu-id="d34c6-112">Revisores</span><span class="sxs-lookup"><span data-stu-id="d34c6-112">Reviewers</span></span> | <span data-ttu-id="d34c6-113">Bernardo Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="d34c6-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span>
<span data-ttu-id="d34c6-114">Publicado</span><span class="sxs-lookup"><span data-stu-id="d34c6-114">Published</span></span> | <span data-ttu-id="d34c6-115">Abril de 2015</span><span class="sxs-lookup"><span data-stu-id="d34c6-115">April, 2015</span></span>

## <a name="abstract"></a><span data-ttu-id="d34c6-116">Abstrato</span><span class="sxs-lookup"><span data-stu-id="d34c6-116">Abstract</span></span>

<span data-ttu-id="d34c6-117">Este documento foi concebido para fornecer orientações oficial para qualquer pessoa planear uma implementação de servidor de solicitação de configuração de estado pretendido do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d34c6-117">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="d34c6-118">Um servidor de solicitação é um serviço simple que deve demorar apenas minutos a implementar.</span><span class="sxs-lookup"><span data-stu-id="d34c6-118">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="d34c6-119">Embora este documento irá oferecer técnica orientações procedimentos que podem ser utilizada numa implementação, o valor deste documento é como uma referência para as melhores práticas e que tenha em consideração antes de implementar.</span><span class="sxs-lookup"><span data-stu-id="d34c6-119">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span>
<span data-ttu-id="d34c6-120">Os leitores devem ter básica familiaridade com DSC e termos utilizados para descrever os componentes que estão incluídas na implementação de DSC.</span><span class="sxs-lookup"><span data-stu-id="d34c6-120">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="d34c6-121">Para obter mais informações, consulte o [Windows PowerShell Desired Configuration descrição geral do estado](https://technet.microsoft.com/library/dn249912.aspx) tópico.</span><span class="sxs-lookup"><span data-stu-id="d34c6-121">For more information, see the [Windows PowerShell Desired State Configuration Overview](https://technet.microsoft.com/library/dn249912.aspx)  topic.</span></span>
<span data-ttu-id="d34c6-122">Como é esperado DSC evoluir em cadência de nuvem, a tecnologia subjacente, incluindo o servidor de solicitação também é esperada para evoluem e introduzem novas capacidades.</span><span class="sxs-lookup"><span data-stu-id="d34c6-122">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="d34c6-123">Este documento inclui uma tabela de versão no anexo que fornece as referências para futuras soluções procura a encorajar forward-looking estruturas e referências a versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="d34c6-123">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="d34c6-124">As duas secções principais deste documento:</span><span class="sxs-lookup"><span data-stu-id="d34c6-124">The two major sections of this document:</span></span>

 - <span data-ttu-id="d34c6-125">Planear a configuração</span><span class="sxs-lookup"><span data-stu-id="d34c6-125">Configuration Planning</span></span>
 - <span data-ttu-id="d34c6-126">Guia de instalação</span><span class="sxs-lookup"><span data-stu-id="d34c6-126">Installation Guide</span></span>

### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="d34c6-127">Versões do Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="d34c6-127">Versions of the Windows Management Framework</span></span>
<span data-ttu-id="d34c6-128">As informações neste documento destina-se a aplicar ao Windows Management Framework 5.0.</span><span class="sxs-lookup"><span data-stu-id="d34c6-128">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="d34c6-129">Enquanto o WMF 5.0 não é necessário para implementar e operar um servidor de solicitação, versão 5.0 é o objetivo deste documento.</span><span class="sxs-lookup"><span data-stu-id="d34c6-129">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="d34c6-130">Configuração do estado pretendido do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d34c6-130">Windows PowerShell Desired State Configuration</span></span>
<span data-ttu-id="d34c6-131">Pretendido a configuração de estado (DSC) é uma plataforma de gestão que permite que os dados de configuração de implementação e gestão utilizando uma sintaxe de setor com o nome de formato (Managed Object) para descrever o modelo CIM (Common Information).</span><span class="sxs-lookup"><span data-stu-id="d34c6-131">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="d34c6-132">Um projeto de código aberto, abra o Management Infrastructure (OMI), existe ainda mais o desenvolvimento dessas normas entre plataformas, incluindo o Linux e os sistemas operativos de hardware de rede.</span><span class="sxs-lookup"><span data-stu-id="d34c6-132">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="d34c6-133">Para obter mais informações, consulte o [página DMTF a associar ao especificações MOF](http://dmtf.org/standards/cim), e [OMI documentos e origem](https://collaboration.opengroup.org/omi/documents.php).</span><span class="sxs-lookup"><span data-stu-id="d34c6-133">For more information, see the [DMTF page linking to MOF specifications](http://dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="d34c6-134">Windows PowerShell fornece um conjunto de extensões de idioma para configuração de estado pretendido que pode utilizar para criar e gerir configurações declarativas.</span><span class="sxs-lookup"><span data-stu-id="d34c6-134">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="d34c6-135">Função de servidor de solicitação</span><span class="sxs-lookup"><span data-stu-id="d34c6-135">Pull server role</span></span>
<span data-ttu-id="d34c6-136">Um servidor de solicitação fornece um serviço centralizado para armazenar as configurações que estarão acessíveis a nós de destino.</span><span class="sxs-lookup"><span data-stu-id="d34c6-136">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>

<span data-ttu-id="d34c6-137">A função de servidor de solicitação pode ser implementada como uma instância de servidor Web ou uma partilha de ficheiros SMB.</span><span class="sxs-lookup"><span data-stu-id="d34c6-137">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="d34c6-138">A capacidade de servidor web inclui uma interface de OData e, opcionalmente, pode incluir capacidades para nós de destino informar confirmação de êxito ou falha como configurações são aplicadas.</span><span class="sxs-lookup"><span data-stu-id="d34c6-138">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="d34c6-139">Esta funcionalidade é útil em ambientes onde existe um grande número de nós de destino.</span><span class="sxs-lookup"><span data-stu-id="d34c6-139">This functionality is useful in environments where there are a large number of target nodes.</span></span>
<span data-ttu-id="d34c6-140">Depois de configurar um nó de destino (também referido como um cliente) para apontar para o servidor de solicitação a configuração mais recente os dados e quaisquer scripts necessários são transferidos e aplicadas.</span><span class="sxs-lookup"><span data-stu-id="d34c6-140">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="d34c6-141">Isto pode acontecer como uma única implementação ou como uma tarefa novamente occurring que também faz com que o servidor de solicitação um recurso importante para a gestão de alterações à escala.</span><span class="sxs-lookup"><span data-stu-id="d34c6-141">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="d34c6-142">Para obter mais informações, consulte [Windows PowerShell pretendido Estado solicitar a servidores de configuração](https://technet.microsoft.com/library/dn249913.aspx) e [Push e Pull modos de configuração](https://technet.microsoft.com/library/dn249913.aspx).</span><span class="sxs-lookup"><span data-stu-id="d34c6-142">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](https://technet.microsoft.com/library/dn249913.aspx) and [Push and Pull Configuration Modes](https://technet.microsoft.com/library/dn249913.aspx).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="d34c6-143">Planear a configuração</span><span class="sxs-lookup"><span data-stu-id="d34c6-143">Configuration planning</span></span>

<span data-ttu-id="d34c6-144">Para qualquer implementação de software empresarial não há informações que podem ser recolhidas seguinte com antecedência para ajudar a planear para a arquitetura correta e para estar preparado para os passos necessários para concluir a implementação.</span><span class="sxs-lookup"><span data-stu-id="d34c6-144">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="d34c6-145">As secções seguintes fornecem informações sobre como preparar e as ligações organizacionais que, provavelmente, serão necessário acontecer antecipadamente.</span><span class="sxs-lookup"><span data-stu-id="d34c6-145">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="d34c6-146">Requisitos de software</span><span class="sxs-lookup"><span data-stu-id="d34c6-146">Software requirements</span></span>

<span data-ttu-id="d34c6-147">Implementação de um servidor de solicitação necessita da funcionalidade de DSC serviço do Windows Server.</span><span class="sxs-lookup"><span data-stu-id="d34c6-147">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="d34c6-148">Esta funcionalidade foi introduzida no Windows Server 2012 e tiver sido atualizada através da Windows Management Framework (WMF) de versões em curso.</span><span class="sxs-lookup"><span data-stu-id="d34c6-148">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="d34c6-149">Transferências de software</span><span class="sxs-lookup"><span data-stu-id="d34c6-149">Software downloads</span></span>

<span data-ttu-id="d34c6-150">Para além de instalar o conteúdo mais recente do Windows Update, existem dois transferências consideradas a melhor prática para implementar um servidor de solicitação do DSC: A versão mais recente do Windows Management Framework e um módulo de DSC para automatizar o aprovisionamento do servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="d34c6-150">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="d34c6-151">WMF</span><span class="sxs-lookup"><span data-stu-id="d34c6-151">WMF</span></span>

<span data-ttu-id="d34c6-152">Windows Server 2012 R2 inclui uma funcionalidade com o nome do serviço de DSC.</span><span class="sxs-lookup"><span data-stu-id="d34c6-152">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="d34c6-153">A funcionalidade do serviço de DSC fornece a funcionalidade de servidor de solicitação, incluindo os binários que suportam o ponto final de OData.</span><span class="sxs-lookup"><span data-stu-id="d34c6-153">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span>
<span data-ttu-id="d34c6-154">WMF está incluído no Windows Server e é atualizado uma cadência seja ágil entre versões do Windows Server.</span><span class="sxs-lookup"><span data-stu-id="d34c6-154">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span> <span data-ttu-id="d34c6-155">[Novas versões do WMF 5.0](http://aka.ms/wmf5latest) podem incluir atualizações para a funcionalidade serviço de DSC.</span><span class="sxs-lookup"><span data-stu-id="d34c6-155">[New versions of WMF 5.0](http://aka.ms/wmf5latest)  can include updates to the DSC Service feature.</span></span> <span data-ttu-id="d34c6-156">Por este motivo, é melhor prática para transferir a versão mais recente do WMF e para rever as notas de versão para determinar se a versão inclui uma atualização para a funcionalidade de serviço do DSC.</span><span class="sxs-lookup"><span data-stu-id="d34c6-156">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="d34c6-157">Também deve consultar a secção das notas de versão que indica se o estado da estrutura de um cenário de atualização ou está listado como estável ou experimental.</span><span class="sxs-lookup"><span data-stu-id="d34c6-157">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span>
<span data-ttu-id="d34c6-158">Para permitir um ciclo de lançamento seja ágil funcionalidades individuais podem ser declaradas estáveis, que indica que a funcionalidade, está pronto para ser utilizada num ambiente de produção, mesmo enquanto WMF é lançado em pré-visualização.</span><span class="sxs-lookup"><span data-stu-id="d34c6-158">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span>
<span data-ttu-id="d34c6-159">Outras funcionalidades que tenham sido atualizadas historicamente por versões WMF (consulte as notas de versão do WMF para obter mais detalhes):</span><span class="sxs-lookup"><span data-stu-id="d34c6-159">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

 - <span data-ttu-id="d34c6-160">Windows PowerShell Windows PowerShell, integrado Scripting</span><span class="sxs-lookup"><span data-stu-id="d34c6-160">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
 - <span data-ttu-id="d34c6-161">Serviços de ambiente (ISE) Web do Windows PowerShell (gestão OData</span><span class="sxs-lookup"><span data-stu-id="d34c6-161">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
 - <span data-ttu-id="d34c6-162">Extensão IIS) Windows PowerShell estada configuração pretendido (DSC)</span><span class="sxs-lookup"><span data-stu-id="d34c6-162">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
 - <span data-ttu-id="d34c6-163">Windows (WinRM) de gestão remota Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="d34c6-163">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="d34c6-164">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="d34c6-164">DSC resource</span></span>

<span data-ttu-id="d34c6-165">Uma implementação de servidor de solicitação pode ser simplificada pelo aprovisionamento do serviço através de um script de configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="d34c6-165">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="d34c6-166">Este documento inclui scripts de configuração que podem ser utilizados para implementar um nó de servidor preparada de produção.</span><span class="sxs-lookup"><span data-stu-id="d34c6-166">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="d34c6-167">Para utilizar os scripts de configuração, um módulo de DSC esteja necessário que não incluídos no Windows Server.</span><span class="sxs-lookup"><span data-stu-id="d34c6-167">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="d34c6-168">O nome do módulo necessário é **xPSDesiredStateConfiguration**, que inclui os recursos de DSC **xDscWebService**.</span><span class="sxs-lookup"><span data-stu-id="d34c6-168">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="d34c6-169">O módulo de xPSDesiredStateConfiguration pode ser transferido [aqui](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span><span class="sxs-lookup"><span data-stu-id="d34c6-169">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="d34c6-170">Utilize o **Install-Module** cmdlet a partir de **PowerShellGet** módulo.</span><span class="sxs-lookup"><span data-stu-id="d34c6-170">Use the **Install-Module** cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="d34c6-171">O **PowerShellGet** módulo irá transferir o módulo para:</span><span class="sxs-lookup"><span data-stu-id="d34c6-171">The **PowerShellGet** module will download the module to:</span></span>

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="d34c6-172">Tarefas de planeamento</span><span class="sxs-lookup"><span data-stu-id="d34c6-172">Planning task</span></span>|
---|
<span data-ttu-id="d34c6-173">Tem acesso para os ficheiros de instalação para o Windows Server 2012 R2?</span><span class="sxs-lookup"><span data-stu-id="d34c6-173">Do you have access to the installation files for Windows Server 2012 R2?</span></span>|
<span data-ttu-id="d34c6-174">O ambiente de implementação terá acesso à Internet para transferir o WMF e o módulo da galeria do online?</span><span class="sxs-lookup"><span data-stu-id="d34c6-174">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>|
<span data-ttu-id="d34c6-175">Como irá instalar as atualizações de segurança mais recentes depois de instalar o sistema operativo?</span><span class="sxs-lookup"><span data-stu-id="d34c6-175">How will you install the latest security updates after installing the operating system?</span></span>|
<span data-ttu-id="d34c6-176">O ambiente terá acesso à Internet para obter as atualizações ou terão um servidor local do Windows Server Update Services (WSUS)?</span><span class="sxs-lookup"><span data-stu-id="d34c6-176">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>|
<span data-ttu-id="d34c6-177">Tem acesso aos ficheiros de instalação do Windows Server que já incluem atualizações através de injeção offline?</span><span class="sxs-lookup"><span data-stu-id="d34c6-177">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>|

### <a name="hardware-requirements"></a><span data-ttu-id="d34c6-178">Requisitos de hardware</span><span class="sxs-lookup"><span data-stu-id="d34c6-178">Hardware requirements</span></span>

<span data-ttu-id="d34c6-179">Implementações de servidor de solicitação são suportadas em servidores físicos e virtuais.</span><span class="sxs-lookup"><span data-stu-id="d34c6-179">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="d34c6-180">Os requisitos de dimensionamento para o servidor de solicitação alinharem com os requisitos do Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="d34c6-180">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

<span data-ttu-id="d34c6-181">Da CPU: processador de 64 bits GHz 1,4 memória: 512 MB de espaço em disco: 32 GB de rede: adaptador Ethernet Gigabit</span><span class="sxs-lookup"><span data-stu-id="d34c6-181">CPU: 1.4 GHz 64-bit processor Memory: 512 MB Disk Space: 32 GB Network: Gigabit Ethernet Adapter</span></span>

<span data-ttu-id="d34c6-182">Tarefas de planeamento</span><span class="sxs-lookup"><span data-stu-id="d34c6-182">Planning task</span></span>|
---|
<span data-ttu-id="d34c6-183">Irá implementar em hardware físico ou numa plataforma de Virtualização?</span><span class="sxs-lookup"><span data-stu-id="d34c6-183">Will you deploy on physical hardware or on a virtualization platform?</span></span>|
<span data-ttu-id="d34c6-184">O que é o processo para pedir um novo servidor para o seu ambiente de destino?</span><span class="sxs-lookup"><span data-stu-id="d34c6-184">What is the process to request a new server for your target environment?</span></span>|
<span data-ttu-id="d34c6-185">O que é o tempo de resposta médio mais rápida para um servidor fique disponível?</span><span class="sxs-lookup"><span data-stu-id="d34c6-185">What is the average turnaround time for a server to become available?</span></span>|
<span data-ttu-id="d34c6-186">O servidor de tamanho irá solicitar?</span><span class="sxs-lookup"><span data-stu-id="d34c6-186">What size server will you request?</span></span>|

### <a name="accounts"></a><span data-ttu-id="d34c6-187">Contas</span><span class="sxs-lookup"><span data-stu-id="d34c6-187">Accounts</span></span>

<span data-ttu-id="d34c6-188">Não existem não requisitos de conta de serviço para implementar uma instância de servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="d34c6-188">There are no service account requirements to deploy a pull server instance.</span></span>
<span data-ttu-id="d34c6-189">No entanto, existem cenários onde o Web site foi executada no contexto de uma conta de utilizador local.</span><span class="sxs-lookup"><span data-stu-id="d34c6-189">However, there are scenarios where the website could run in the context of a local user account.</span></span>
<span data-ttu-id="d34c6-190">Por exemplo, se for necessário para acesso de armazenamento de partilha de conteúdo do Web site e o Windows Server ou o dispositivo que aloja a partilha de armazenamento não estão associados a um domínio.</span><span class="sxs-lookup"><span data-stu-id="d34c6-190">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="d34c6-191">Registos DNS</span><span class="sxs-lookup"><span data-stu-id="d34c6-191">DNS records</span></span>

<span data-ttu-id="d34c6-192">É necessário um nome de servidor para utilizar quando configurar clientes para trabalhar com um ambiente de servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="d34c6-192">You will need a server name to use when configuring clients to work with a pull server environment.</span></span>
<span data-ttu-id="d34c6-193">Em ambientes de teste, normalmente é utilizado o nome de anfitrião do servidor ou o endereço IP para o servidor pode ser utilizado se a resolução do nome DNS não está disponível.</span><span class="sxs-lookup"><span data-stu-id="d34c6-193">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span>
<span data-ttu-id="d34c6-194">Em ambientes de produção ou num ambiente de laboratório que se destina a representar uma implementação de produção, a melhor prática é criar um registo CNAME no DNS.</span><span class="sxs-lookup"><span data-stu-id="d34c6-194">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="d34c6-195">Um CNAME DNS permite-lhe criar um alias referir-se para o anfitrião (A) registo.</span><span class="sxs-lookup"><span data-stu-id="d34c6-195">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span>
<span data-ttu-id="d34c6-196">A intenção de registo de nome adicionais é aumentar flexibilidade deve uma alteração necessário no futuro.</span><span class="sxs-lookup"><span data-stu-id="d34c6-196">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span>
<span data-ttu-id="d34c6-197">Um CNAME pode ajudar a isolar a configuração do cliente para que as alterações para o ambiente de servidor, tais como substituir um servidor de solicitação ou adicionar servidores de solicitação adicionais, não irão exigir uma alteração à configuração de cliente correspondente.</span><span class="sxs-lookup"><span data-stu-id="d34c6-197">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="d34c6-198">Ao escolher um nome para o registo DNS, mantenha a arquitetura de solução em mente.</span><span class="sxs-lookup"><span data-stu-id="d34c6-198">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span>
<span data-ttu-id="d34c6-199">Se utilizar o balanceamento de carga, o certificado utilizado para proteger o tráfego através de HTTPS terá de partilhar o mesmo nome que o registo DNS.</span><span class="sxs-lookup"><span data-stu-id="d34c6-199">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span>

<span data-ttu-id="d34c6-200">Cenário</span><span class="sxs-lookup"><span data-stu-id="d34c6-200">Scenario</span></span> |<span data-ttu-id="d34c6-201">Melhores práticas</span><span class="sxs-lookup"><span data-stu-id="d34c6-201">Best Practice</span></span>
:---|:---
<span data-ttu-id="d34c6-202">Ambiente de testes</span><span class="sxs-lookup"><span data-stu-id="d34c6-202">Test Environment</span></span> |<span data-ttu-id="d34c6-203">Reproduza o ambiente de produção planeada, se possível.</span><span class="sxs-lookup"><span data-stu-id="d34c6-203">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="d34c6-204">Um nome de anfitrião do servidor é adequado para configurações simples.</span><span class="sxs-lookup"><span data-stu-id="d34c6-204">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="d34c6-205">Se o DNS não estiver disponível, um endereço IP pode ser utilizado in lieu of um nome de anfitrião.</span><span class="sxs-lookup"><span data-stu-id="d34c6-205">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>|
<span data-ttu-id="d34c6-206">Implementação de nó único</span><span class="sxs-lookup"><span data-stu-id="d34c6-206">Single Node Deployment</span></span> |<span data-ttu-id="d34c6-207">Crie um registo CNAME no DNS que aponta para o nome de anfitrião do servidor.</span><span class="sxs-lookup"><span data-stu-id="d34c6-207">Create a DNS CNAME record that points to the server hostname.</span></span>|

<span data-ttu-id="d34c6-208">Para obter mais informações, consulte [configurar o DNS Round Robin no Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="d34c6-208">For more information, see [Configuring DNS Round Robin in Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).</span></span>

<span data-ttu-id="d34c6-209">Tarefas de planeamento</span><span class="sxs-lookup"><span data-stu-id="d34c6-209">Planning task</span></span>|
---|
<span data-ttu-id="d34c6-210">Saber quem entrar em contacto com registos DNS criados e alterados?</span><span class="sxs-lookup"><span data-stu-id="d34c6-210">Do you know who to contact to have DNS records created and changed?</span></span>|
<span data-ttu-id="d34c6-211">O que é a resposta mais rápida média de um pedido para um registo DNS?</span><span class="sxs-lookup"><span data-stu-id="d34c6-211">What is the average turnaround for a request for a DNS record?</span></span>|
<span data-ttu-id="d34c6-212">Precisa de pedir estático registos de nome de anfitrião (A) para servidores?</span><span class="sxs-lookup"><span data-stu-id="d34c6-212">Do you need to request static Hostname (A) records for servers?</span></span>|
<span data-ttu-id="d34c6-213">O que irá solicitar como um CNAME?</span><span class="sxs-lookup"><span data-stu-id="d34c6-213">What will you request as a CNAME?</span></span>|
<span data-ttu-id="d34c6-214">Se for necessário, tipo de solução de balanceamento de carga que irá utilizar?</span><span class="sxs-lookup"><span data-stu-id="d34c6-214">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="d34c6-215">(consulte a secção intitulada balanceamento de carga para obter detalhes)</span><span class="sxs-lookup"><span data-stu-id="d34c6-215">(see section titled Load Balancing for details)</span></span>|

### <a name="public-key-infrastructure"></a><span data-ttu-id="d34c6-216">Infraestrutura de chaves públicas</span><span class="sxs-lookup"><span data-stu-id="d34c6-216">Public Key Infrastructure</span></span>

<span data-ttu-id="d34c6-217">A maioria das organizações hoje necessitam que o tráfego de rede, especialmente tráfego que inclua esses dados confidenciais, como servidores estiverem configurados, deve ser validado e/ou encriptado durante a trânsito.</span><span class="sxs-lookup"><span data-stu-id="d34c6-217">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span>
<span data-ttu-id="d34c6-218">Embora seja possível implementar um servidor de solicitação utilizando HTTP que facilita a pedidos de cliente no apague o texto, é uma melhor prática para o tráfego seguro através de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d34c6-218">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="d34c6-219">O serviço pode ser configurado para utilizar HTTPS utilizando um conjunto de parâmetros no recurso DSC **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="d34c6-219">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="d34c6-220">Os requisitos de certificados para proteger o tráfego HTTPS para o servidor de solicitação não são diferentes proteger outro HTTPS web site.</span><span class="sxs-lookup"><span data-stu-id="d34c6-220">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="d34c6-221">O **servidor Web** modelo nos serviços de certificados de servidor Windows satisfaça as capacidades necessárias.</span><span class="sxs-lookup"><span data-stu-id="d34c6-221">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="d34c6-222">Tarefas de planeamento</span><span class="sxs-lookup"><span data-stu-id="d34c6-222">Planning task</span></span>|
---|
<span data-ttu-id="d34c6-223">Se os pedidos de certificado não são automatizados, que vai precisar de contactar a pedidos de um certificado?</span><span class="sxs-lookup"><span data-stu-id="d34c6-223">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>|
<span data-ttu-id="d34c6-224">O que é a resposta mais rápida média do pedido?</span><span class="sxs-lookup"><span data-stu-id="d34c6-224">What is the average turnaround for the request?</span></span>|
<span data-ttu-id="d34c6-225">Como será o ficheiro de certificado transferido para si?</span><span class="sxs-lookup"><span data-stu-id="d34c6-225">How will the certificate file be transferred to you?</span></span>|
<span data-ttu-id="d34c6-226">Como será a chave privada de certificado transferida para si?</span><span class="sxs-lookup"><span data-stu-id="d34c6-226">How will the certificate private key be transferred to you?</span></span>|
<span data-ttu-id="d34c6-227">Qual é a hora de expiração predefinido?</span><span class="sxs-lookup"><span data-stu-id="d34c6-227">How long is the default expiration time?</span></span>|
<span data-ttu-id="d34c6-228">Ter settled num nome de DNS para o ambiente de servidor de solicitação, o que pode utilizar para o nome do certificado?</span><span class="sxs-lookup"><span data-stu-id="d34c6-228">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>|

### <a name="choosing-an-architecture"></a><span data-ttu-id="d34c6-229">Escolher uma arquitetura</span><span class="sxs-lookup"><span data-stu-id="d34c6-229">Choosing an architecture</span></span>

<span data-ttu-id="d34c6-230">Um servidor de solicitação pode ser implementado utilizando um serviço de web alojado no IIS ou uma partilha de ficheiros SMB.</span><span class="sxs-lookup"><span data-stu-id="d34c6-230">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="d34c6-231">Na maioria das situações, a opção de serviço web irá fornecer maior flexibilidade.</span><span class="sxs-lookup"><span data-stu-id="d34c6-231">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="d34c6-232">Não é invulgar para tráfego HTTPS para percorrer os limites de rede, enquanto que o tráfego SMB é, muitas vezes, filtrado ou bloqueado entre redes.</span><span class="sxs-lookup"><span data-stu-id="d34c6-232">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="d34c6-233">O serviço web também oferece a opção para incluir um servidor de conformidade ou Web Gestor Reporting Services (ambos os tópicos para ser resolvido numa versão futura deste documento) que fornecem um mecanismo para os clientes para comunicar o estado para um servidor de visibilidade centralizada.</span><span class="sxs-lookup"><span data-stu-id="d34c6-233">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span>
<span data-ttu-id="d34c6-234">O SMB fornece uma opção para ambientes onde a política dita que não deve ser utilizado de um servidor web e outros requisitos ambientais que tornam uma função de servidor web indesejável.</span><span class="sxs-lookup"><span data-stu-id="d34c6-234">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span>
<span data-ttu-id="d34c6-235">Em ambos os casos, lembre-se avaliar os requisitos para assinatura e encriptação de tráfego.</span><span class="sxs-lookup"><span data-stu-id="d34c6-235">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="d34c6-236">HTTPS, a assinatura SMB e políticas IPSEC são todas as opções de vale a considerar.</span><span class="sxs-lookup"><span data-stu-id="d34c6-236">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="d34c6-237">Balanceamento de carga</span><span class="sxs-lookup"><span data-stu-id="d34c6-237">Load balancing</span></span>
<span data-ttu-id="d34c6-238">Os clientes a interagir com o serviço web efetuar um pedido com indicação de que é devolvido numa única resposta.</span><span class="sxs-lookup"><span data-stu-id="d34c6-238">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="d34c6-239">Não existem pedidos sequenciais são necessários, pelo que não é necessário para a plataforma para garantir sessões são mantidas num único servidor em qualquer ponto no tempo de balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="d34c6-239">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="d34c6-240">Tarefas de planeamento</span><span class="sxs-lookup"><span data-stu-id="d34c6-240">Planning task</span></span>|
---|
<span data-ttu-id="d34c6-241">Que solução será utilizada para balanceamento de carga tráfego entre servidores?</span><span class="sxs-lookup"><span data-stu-id="d34c6-241">What solution will be used for load balancing traffic across servers?</span></span>|
<span data-ttu-id="d34c6-242">Se utilizar um balanceador de carga de hardware, que irá demorar um pedido para adicionar uma nova configuração para o dispositivo?</span><span class="sxs-lookup"><span data-stu-id="d34c6-242">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>|
<span data-ttu-id="d34c6-243">O que é a resposta mais rápida para um pedido para configurar uma nova carga média com balanceamento de serviço web?</span><span class="sxs-lookup"><span data-stu-id="d34c6-243">What is the average turnaround for a request to configure a new load balanced web service?</span></span>|
<span data-ttu-id="d34c6-244">As informações que será necessárias para o pedido?</span><span class="sxs-lookup"><span data-stu-id="d34c6-244">What information will be required for the request?</span></span>|
<span data-ttu-id="d34c6-245">Vai precisar de pedir um IP adicional ou a equipa responsável pelo balanceamento de carga processará que?</span><span class="sxs-lookup"><span data-stu-id="d34c6-245">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>|
<span data-ttu-id="d34c6-246">Pretende que os registos DNS necessários, e este terão pela equipa responsável pela configuração de solução de balanceamento de carga?</span><span class="sxs-lookup"><span data-stu-id="d34c6-246">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>|
<span data-ttu-id="d34c6-247">A solução de balanceamento de carga requer que a PKI ser processados pelo dispositivo ou pode-o balanceamento de carga tráfego HTTPS, desde que existem não requisitos de sessão?</span><span class="sxs-lookup"><span data-stu-id="d34c6-247">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="d34c6-248">Configurações e os módulos no servidor de solicitação de teste</span><span class="sxs-lookup"><span data-stu-id="d34c6-248">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="d34c6-249">Como parte do planeamento de configuração, terá de pensar sobre o DSC módulos e configurações serão alojadas pelo servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="d34c6-249">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="d34c6-250">Para efeitos de planeamento da configuração é importante ter uma compreensão básica sobre como preparar e implementar conteúdo num servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="d34c6-250">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span>

<span data-ttu-id="d34c6-251">No futuro, esta secção será expandida e incluída no guia de operações do servidor de solicitação do DSC.</span><span class="sxs-lookup"><span data-stu-id="d34c6-251">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span>  <span data-ttu-id="d34c6-252">O guia de abordar o processo de diário para a gestão de módulos e configurações ao longo do tempo com a automatização.</span><span class="sxs-lookup"><span data-stu-id="d34c6-252">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span>

#### <a name="dsc-modules"></a><span data-ttu-id="d34c6-253">Módulos de DSC</span><span class="sxs-lookup"><span data-stu-id="d34c6-253">DSC modules</span></span>
<span data-ttu-id="d34c6-254">Clientes que solicitam uma configuração terá dos módulos necessários do DSC.</span><span class="sxs-lookup"><span data-stu-id="d34c6-254">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="d34c6-255">É uma funcionalidade do servidor de solicitação automatizar a distribuição a pedido dos módulos de DSC nos clientes.</span><span class="sxs-lookup"><span data-stu-id="d34c6-255">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="d34c6-256">Se estiver a implementar um servidor de solicitação pela primeira vez, talvez como um laboratório ou de prova de conceito, provavelmente pretender dependem de módulos de DSC que estão disponíveis de repositórios públicos, como a galeria do PowerShell ou repositórios do PowerShell.org GitHub para módulos de DSC .</span><span class="sxs-lookup"><span data-stu-id="d34c6-256">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="d34c6-257">É essencial Lembre-se de que, mesmo para origens de online fidedignas, tais como a galeria do PowerShell, qualquer módulo que é transferido a partir de um repositório público deve ser revisto por alguém com experiência com o PowerShell e o conhecimento do ambiente onde os módulos será utilizar antes a ser utilizado em produção.</span><span class="sxs-lookup"><span data-stu-id="d34c6-257">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="d34c6-258">Ao concluir esta tarefa é uma boa altura para verificar a existência de quaisquer payload adicional no módulo que possa ser removido como scripts de exemplo e a documentação.</span><span class="sxs-lookup"><span data-stu-id="d34c6-258">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="d34c6-259">Isto irá reduzir a largura de banda de rede por cliente aquando do primeiro pedido, quando os módulos serão transferidos através da rede do servidor ao cliente.</span><span class="sxs-lookup"><span data-stu-id="d34c6-259">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="d34c6-260">Cada módulo tem de ser compactado num formato específico, um ficheiro ZIP com o nome ModuleName_Version.zip que contém o payload de módulo.</span><span class="sxs-lookup"><span data-stu-id="d34c6-260">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="d34c6-261">Depois do ficheiro é copiado para o servidor tem de ser criado um ficheiro de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="d34c6-261">After the file is copied to the server a checksum file must be created.</span></span> <span data-ttu-id="d34c6-262">Quando os clientes ligam ao servidor, a soma de verificação é utilizada para verificar que o conteúdo do módulo do DSC não mudou desde que foi publicada.</span><span class="sxs-lookup"><span data-stu-id="d34c6-262">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscCheckSum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="d34c6-263">Tarefas de planeamento</span><span class="sxs-lookup"><span data-stu-id="d34c6-263">Planning task</span></span>|
---|
<span data-ttu-id="d34c6-264">Se estiver a planear um ambiente de laboratório ou de teste que cenários são fundamentais para validar?</span><span class="sxs-lookup"><span data-stu-id="d34c6-264">If you are planning a test or lab environment which scenarios are key to validate?</span></span>|
<span data-ttu-id="d34c6-265">Existem módulos publicamente disponíveis que contêm os recursos para cobrir tudo o que necessita ou terá de criar os seus próprios recursos?</span><span class="sxs-lookup"><span data-stu-id="d34c6-265">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>|
<span data-ttu-id="d34c6-266">O ambiente terão acesso à Internet para obter os módulos públicos?</span><span class="sxs-lookup"><span data-stu-id="d34c6-266">Will your environment have Internet access to retrieve public modules?</span></span>|
<span data-ttu-id="d34c6-267">Quem será o responsável pela revisão módulos de DSC?</span><span class="sxs-lookup"><span data-stu-id="d34c6-267">Who will be responsible for reviewing DSC modules?</span></span>|
<span data-ttu-id="d34c6-268">Se estiver a planear um ambiente de produção que irá utilizar como um repositório local para armazenar os módulos de DSC?</span><span class="sxs-lookup"><span data-stu-id="d34c6-268">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>|
<span data-ttu-id="d34c6-269">Um agrupamento central aceitará módulos de DSC das equipas de aplicação?</span><span class="sxs-lookup"><span data-stu-id="d34c6-269">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="d34c6-270">O que será o processo?</span><span class="sxs-lookup"><span data-stu-id="d34c6-270">What will the process be?</span></span>|
<span data-ttu-id="d34c6-271">Será automatizar empacotamento, copiar e criar uma soma de verificação para módulos de DSC prontos para produção ao servidor, do seu repositório de origem?</span><span class="sxs-lookup"><span data-stu-id="d34c6-271">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>|
<span data-ttu-id="d34c6-272">A equipa será responsável por gerir a plataforma de automatização?</span><span class="sxs-lookup"><span data-stu-id="d34c6-272">Will your team be responsible for managing the automation platform as well?</span></span>|

#### <a name="dsc-configurations"></a><span data-ttu-id="d34c6-273">Configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="d34c6-273">DSC configurations</span></span>

<span data-ttu-id="d34c6-274">O objetivo de um servidor de solicitação consiste em fornecer um mecanismo centralizado para distribuir as configurações de DSC em nós de cliente.</span><span class="sxs-lookup"><span data-stu-id="d34c6-274">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="d34c6-275">As configurações são armazenadas no servidor como documentos MOF.</span><span class="sxs-lookup"><span data-stu-id="d34c6-275">The configurations are stored on the server as MOF documents.</span></span>
<span data-ttu-id="d34c6-276">Cada documento será nomeado com um GUID exclusivo.</span><span class="sxs-lookup"><span data-stu-id="d34c6-276">Each document will be named with a unique GUID.</span></span> <span data-ttu-id="d34c6-277">Quando os clientes são configurados para estabelecer ligação com um servidor de solicitação, também são fornecidos o GUID para a configuração deve pedir.</span><span class="sxs-lookup"><span data-stu-id="d34c6-277">When clients are configured to connect with a pull server, they are also given the GUID for the configuration they should request.</span></span> <span data-ttu-id="d34c6-278">Este sistema de referência configurações pelo GUID garantias de exclusividade global e é flexível do que uma configuração pode ser aplicada com granularidade por nó, ou como uma configuração de função que abranja vários servidores que devem ter configurações idênticas.</span><span class="sxs-lookup"><span data-stu-id="d34c6-278">This system of referencing configurations by GUID guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="d34c6-279">GUIDs</span><span class="sxs-lookup"><span data-stu-id="d34c6-279">GUIDs</span></span>

<span data-ttu-id="d34c6-280">Planear a configuração GUIDs é, atenção adicional quando pensar através de uma implementação de servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="d34c6-280">Planning for configuration GUIDs is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="d34c6-281">Não é necessário para saber como processar GUIDs específico e o processo é provável que seja exclusivo para cada ambiente.</span><span class="sxs-lookup"><span data-stu-id="d34c6-281">There is no specific requirement for how to handle GUIDs and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="d34c6-282">O processo pode variar desde simples para complexa: um ficheiro CSV centralmente armazenado, uma tabela SQL simple, uma CMDB ou uma solução complexa que requerem integração com outra solução de software ou a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="d34c6-282">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="d34c6-283">Existem duas abordagens gerais:</span><span class="sxs-lookup"><span data-stu-id="d34c6-283">There are two general approaches:</span></span>

 - <span data-ttu-id="d34c6-284">**Atribuir GUIDs por servidor** — fornece uma medida de garantia que cada configuração do servidor é controlada individualmente.</span><span class="sxs-lookup"><span data-stu-id="d34c6-284">**Assigning GUIDs per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="d34c6-285">Isto fornece um nível de precisão à volta de atualizações e pode funcionar bem em ambientes com alguns servidores.</span><span class="sxs-lookup"><span data-stu-id="d34c6-285">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
 - <span data-ttu-id="d34c6-286">**Atribuir GUIDs por função de servidor** — todos os servidores que executam a mesma função, tais como servidores web, utilizam o mesmo GUID para fazer referência os dados de configuração necessárias.</span><span class="sxs-lookup"><span data-stu-id="d34c6-286">**Assigning GUIDs per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span>  <span data-ttu-id="d34c6-287">Lembre-se de que se o número de servidores de partilhar o mesmo GUID, todos eles seriam atualizados em simultâneo quando a configuração for alterada.</span><span class="sxs-lookup"><span data-stu-id="d34c6-287">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

<span data-ttu-id="d34c6-288">O GUID é algo que devem ser consideradas dados confidenciais porque pode ser aproveitado por alguém com intenções maliciosas para obterem intelligence sobre como os servidores são implementados e configurados no seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="d34c6-288">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="d34c6-289">Para obter mais informações, consulte [em segurança alocar GUIDs no PowerShell pretendido estado configuração solicitar modo](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).</span><span class="sxs-lookup"><span data-stu-id="d34c6-289">For more information, see [Securely allocating GUIDs in PowerShell Desired State Configuration Pull Mode](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).</span></span>

<span data-ttu-id="d34c6-290">Tarefas de planeamento</span><span class="sxs-lookup"><span data-stu-id="d34c6-290">Planning task</span></span>|
---|
<span data-ttu-id="d34c6-291">Quem será o responsável pela cópia configurações para a pasta de servidor de solicitação quando estas estão prontas?</span><span class="sxs-lookup"><span data-stu-id="d34c6-291">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>|
<span data-ttu-id="d34c6-292">Se as configurações são criadas por uma equipa de aplicação, o que o processo será entregam-las?</span><span class="sxs-lookup"><span data-stu-id="d34c6-292">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>|
<span data-ttu-id="d34c6-293">Tirar partido um repositório para armazenar as configurações que estes são criados, entre equipas?</span><span class="sxs-lookup"><span data-stu-id="d34c6-293">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>|
<span data-ttu-id="d34c6-294">Será automatizar o processo de copiar as configurações para o servidor e criar uma soma de verificação quando estas estão prontas?</span><span class="sxs-lookup"><span data-stu-id="d34c6-294">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>|
<span data-ttu-id="d34c6-295">Como irá mapear GUIDs para servidores ou funções e isto armazenar?</span><span class="sxs-lookup"><span data-stu-id="d34c6-295">How will you map GUIDs to servers or roles, and where will this be stored?</span></span>|
<span data-ttu-id="d34c6-296">O que irá utilizar como um processo para configurar computadores cliente e como serão-lo a integrar com o processo para criar e armazenar os GUIDs de configuração?</span><span class="sxs-lookup"><span data-stu-id="d34c6-296">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration GUIDs?</span></span>|

## <a name="installation-guide"></a><span data-ttu-id="d34c6-297">Guia de instalação</span><span class="sxs-lookup"><span data-stu-id="d34c6-297">Installation Guide</span></span>

<span data-ttu-id="d34c6-298">*Scripts indicados neste documento são exemplos estáveis. Reveja sempre scripts cuidadosamente antes de executá-los num ambiente de produção.*</span><span class="sxs-lookup"><span data-stu-id="d34c6-298">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="d34c6-299">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d34c6-299">Prerequisites</span></span>

<span data-ttu-id="d34c6-300">Para verificar a versão do PowerShell no seu servidor, utilize o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="d34c6-300">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="d34c6-301">Se for possível, atualize para a versão mais recente do Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="d34c6-301">If possible, upgrade to the latest version of Windows Management Framework.</span></span>
<span data-ttu-id="d34c6-302">Em seguida, transferir o `xPsDesiredStateConfiguration` módulo com o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="d34c6-302">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>


```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="d34c6-303">O comando irá perguntar-sua aprovação antes de transferir o módulo.</span><span class="sxs-lookup"><span data-stu-id="d34c6-303">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="d34c6-304">Scripts de instalação e configuração</span><span class="sxs-lookup"><span data-stu-id="d34c6-304">Installation and configuration scripts</span></span>
-

<span data-ttu-id="d34c6-305">O melhor método para implementar um servidor de solicitação do DSC consiste em utilizar um script de configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="d34c6-305">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="d34c6-306">Este documento apresenta scripts, incluindo as definições básicas que teria de configurar apenas o serviço web do DSC e as definições que teria de configurar um serviço de web de DSC incluindo do Windows Server ponto-a-ponto avançadas.</span><span class="sxs-lookup"><span data-stu-id="d34c6-306">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="d34c6-307">Nota: Atualmente o `xPSDesiredStateConfiguation` módulo DSC requer que o servidor para ser a região EN-US.</span><span class="sxs-lookup"><span data-stu-id="d34c6-307">Note:  Currently the `xPSDesiredStateConfiguation` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="d34c6-308">Configuração básica para o Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="d34c6-308">Basic configuration for Windows Server 2012</span></span>
-------------------------------------------
```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="d34c6-309">Configuração avançada para o Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="d34c6-309">Advanced configuration for Windows Server 2012 R2</span></span>

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }
        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }
        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }
        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }
        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}
$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }
PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```


### <a name="verify-pull-server-functionality"></a><span data-ttu-id="d34c6-310">Verificar a funcionalidade de servidor de solicitação</span><span class="sxs-lookup"><span data-stu-id="d34c6-310">Verify pull server functionality</span></span>

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](invoke-webrequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}
Verify-DSCPullServer 'INSERT SERVER FQDN'

Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a><span data-ttu-id="d34c6-311">Configurar os clientes</span><span class="sxs-lookup"><span data-stu-id="d34c6-311">Configure clients</span></span>

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}
PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```


## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="d34c6-312">Referências adicionais, fragmentos e exemplos</span><span class="sxs-lookup"><span data-stu-id="d34c6-312">Additional references, snippets, and examples</span></span>

<span data-ttu-id="d34c6-313">Este exemplo mostra como iniciar manualmente uma ligação de cliente (requer WMF5) para fins de teste.</span><span class="sxs-lookup"><span data-stu-id="d34c6-313">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span>

```powershell
Update-DSCConfiguration –Wait -Verbose
```

<span data-ttu-id="d34c6-314">O [adicionar DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet é utilizado para adicionar um tipo de registo CNAME para uma zona DNS.</span><span class="sxs-lookup"><span data-stu-id="d34c6-314">The [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet is used to add a type CNAME record to a DNS zone.</span></span>

<span data-ttu-id="d34c6-315">A função de PowerShell para [criar uma soma de verificação e publicar o DSC MOF para o servidor de solicitação do SMB](http://bit.ly/1E46BhI) gera automaticamente a soma de verificação necessária e, em seguida, copia a configuração de MOF e de ficheiros de soma de verificação para o servidor de solicitação SMB.</span><span class="sxs-lookup"><span data-stu-id="d34c6-315">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](http://bit.ly/1E46BhI) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="d34c6-316">Apêndice - compreender ODATA tipos de ficheiros de dados do serviço</span><span class="sxs-lookup"><span data-stu-id="d34c6-316">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="d34c6-317">Um ficheiro de dados é armazenado para criar informações durante a implementação de um servidor de solicitação, que inclui o serviço web de OData.</span><span class="sxs-lookup"><span data-stu-id="d34c6-317">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="d34c6-318">O tipo do ficheiro depende do sistema operativo, conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="d34c6-318">The type of file depends on the operating system, as described below.</span></span>

 - <span data-ttu-id="d34c6-319">**Windows Server 2012** o tipo de ficheiro será sempre. mdb</span><span class="sxs-lookup"><span data-stu-id="d34c6-319">**Windows Server 2012** The file type will always be   .mdb</span></span>
 - <span data-ttu-id="d34c6-320">**Windows Server 2012 R2** o tipo de ficheiro será predefinido para. edb, a menos que um. mdb é especificado na configuração</span><span class="sxs-lookup"><span data-stu-id="d34c6-320">**Windows Server 2012 R2** The file type will default to .edb unless a .mdb is specified in the configuration</span></span>

<span data-ttu-id="d34c6-321">No [avançadas de script de exemplo](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) para instalar um servidor de solicitação, também irá encontrar um exemplo de como controlar automaticamente as definições do ficheiro Web. config para evitar qualquer probabilidade de erro foi causado por tipo de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="d34c6-321">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>