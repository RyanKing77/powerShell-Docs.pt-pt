---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Melhores práticas do servidor de solicitação
ms.openlocfilehash: fe483a487f85f2e4edb0928fccfe98746ae11231
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079205"
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="7a4c5-103">Melhores práticas do servidor de solicitação</span><span class="sxs-lookup"><span data-stu-id="7a4c5-103">Pull server best practices</span></span>

<span data-ttu-id="7a4c5-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7a4c5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7a4c5-105">O servidor de solicitação (recurso do Windows *DSC-serviço*) é um componente suportado do Windows Server no entanto, não existem planos para oferecer novas funcionalidades ou capacidades.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="7a4c5-106">É recomendado para começar a fazer a transição geridos os clientes [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação de mensagens em fila no Windows Server) ou uma das soluções da Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="7a4c5-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="7a4c5-107">Resumo: Este documento destina-se para incluir o processo e extensibilidade para ajudar os engenheiros que estiver a preparar para a solução.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-107">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="7a4c5-108">Detalhes devem fornecer melhores práticas, conforme identificado por parte dos clientes e, em seguida, validada pela equipe do produto para garantir que as recomendações são voltado para o futuro e considerado estáveis.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-108">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

| |<span data-ttu-id="7a4c5-109">Informações do documento</span><span class="sxs-lookup"><span data-stu-id="7a4c5-109">Doc Info</span></span>|
|:---|:---|
<span data-ttu-id="7a4c5-110">Autor</span><span class="sxs-lookup"><span data-stu-id="7a4c5-110">Author</span></span> | <span data-ttu-id="7a4c5-111">Michael Greene</span><span class="sxs-lookup"><span data-stu-id="7a4c5-111">Michael Greene</span></span>
<span data-ttu-id="7a4c5-112">Revisores</span><span class="sxs-lookup"><span data-stu-id="7a4c5-112">Reviewers</span></span> | <span data-ttu-id="7a4c5-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="7a4c5-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span>
<span data-ttu-id="7a4c5-114">Publicado</span><span class="sxs-lookup"><span data-stu-id="7a4c5-114">Published</span></span> | <span data-ttu-id="7a4c5-115">Abril de 2015</span><span class="sxs-lookup"><span data-stu-id="7a4c5-115">April, 2015</span></span>

## <a name="abstract"></a><span data-ttu-id="7a4c5-116">Abstrato</span><span class="sxs-lookup"><span data-stu-id="7a4c5-116">Abstract</span></span>

<span data-ttu-id="7a4c5-117">Este documento destina-se para fornecer orientações oficial para qualquer pessoa a planear uma implementação de servidor de solicitação do Windows PowerShell Desired State Configuration.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-117">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="7a4c5-118">Um servidor de solicitação é um serviço simple que deve demorar apenas alguns minutos a implementar.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-118">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="7a4c5-119">Embora este documento oferece orientações técnicas de procedimentos que podem ser utilizada numa implementação, o valor deste documento é como uma referência para as práticas recomendadas e o que pensar antes de implementar.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-119">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span>
<span data-ttu-id="7a4c5-120">Os leitores devem ter familiaridade básica com DSC e os termos utilizados para descrever os componentes que estão incluídas numa implantação de DSC.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-120">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="7a4c5-121">Para obter mais informações, consulte a [Windows PowerShell Desired State Configuration descrição geral](/powershell/dsc/overview) tópico.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-121">For more information, see the [Windows PowerShell Desired State Configuration Overview](/powershell/dsc/overview)  topic.</span></span>
<span data-ttu-id="7a4c5-122">Como o DSC é esperada a evoluir em cadência de cloud, a tecnologia subjacente, incluindo o servidor de solicitação também se espera que a evoluir e introduzir novas capacidades.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-122">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="7a4c5-123">Este documento inclui uma tabela de versão no apêndice que fornece referências para versões anteriores e referências a soluções de aparência futuras para incentivar a designs futuro.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-123">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="7a4c5-124">As duas secções principais deste documento:</span><span class="sxs-lookup"><span data-stu-id="7a4c5-124">The two major sections of this document:</span></span>

- <span data-ttu-id="7a4c5-125">Planejamento da configuração</span><span class="sxs-lookup"><span data-stu-id="7a4c5-125">Configuration Planning</span></span>
- <span data-ttu-id="7a4c5-126">Guia de instalação</span><span class="sxs-lookup"><span data-stu-id="7a4c5-126">Installation Guide</span></span>

### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="7a4c5-127">Versões do Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="7a4c5-127">Versions of the Windows Management Framework</span></span>

<span data-ttu-id="7a4c5-128">As informações neste documento destina-se aplicar ao Windows Management Framework 5.0.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-128">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="7a4c5-129">Embora o WMF 5.0 não seja necessário para implantar e operar um servidor de solicitação, a versão 5.0 é o foco deste documento.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-129">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="7a4c5-130">Windows PowerShell Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="7a4c5-130">Windows PowerShell Desired State Configuration</span></span>

<span data-ttu-id="7a4c5-131">Desired State Configuration (DSC) é uma plataforma de gestão que permite implementar e gerir dados de configuração utilizando uma sintaxe de setor com o nome de formato MOF (Managed Object Format) para descrever o modelo CIM (Common Information).</span><span class="sxs-lookup"><span data-stu-id="7a4c5-131">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="7a4c5-132">Existe um projeto de código-fonte aberto, o Open Management Infrastructure (OMI), sistemas de operativos de hardware de rede e ainda mais o desenvolvimento desses padrões entre plataformas, incluindo o Linux.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-132">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="7a4c5-133">Para obter mais informações, consulte a [página DMTF vinculando a especificações de MOF](https://www.dmtf.org/standards/cim), e [OMI documentos e origem](https://collaboration.opengroup.org/omi/documents.php).</span><span class="sxs-lookup"><span data-stu-id="7a4c5-133">For more information, see the [DMTF page linking to MOF specifications](https://www.dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="7a4c5-134">Windows PowerShell fornece um conjunto de extensões de linguagem para Desired State Configuration, que pode utilizar para criar e gerir configurações declarativas.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-134">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="7a4c5-135">Função de servidor de solicitação</span><span class="sxs-lookup"><span data-stu-id="7a4c5-135">Pull server role</span></span>

<span data-ttu-id="7a4c5-136">Um servidor de solicitação fornece um serviço centralizado para armazenar as configurações que estarão acessíveis a nós de destino.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-136">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>

<span data-ttu-id="7a4c5-137">A função de servidor de solicitação pode ser implementada como uma instância de servidor Web ou uma partilha de ficheiros SMB.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-137">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="7a4c5-138">A capacidade de servidor web inclui uma interface de OData e, opcionalmente, pode incluir capacidades para nós de destino relatar confirmação de êxito ou falha conforme as configurações são aplicadas.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-138">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="7a4c5-139">Essa funcionalidade é útil em ambientes em que há um grande número de nós de destino.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-139">This functionality is useful in environments where there are a large number of target nodes.</span></span>
<span data-ttu-id="7a4c5-140">Depois de configurar um nó de destino (também referido como um cliente) para apontar para o servidor de solicitação, a configuração mais recente os dados e quaisquer scripts necessários são transferidos e aplicados.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-140">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="7a4c5-141">Isto pode acontecer como uma implementação de uso individual ou como uma tarefa que novamente que também faz com que o servidor de solicitação um ativo importante para o gerenciamento de alterações em escala.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-141">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="7a4c5-142">Para obter mais informações, consulte [Windows PowerShell Desired State Configuration extrair servidores](/powershell/dsc/pullServer) e</span><span class="sxs-lookup"><span data-stu-id="7a4c5-142">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](/powershell/dsc/pullServer) and</span></span>

<span data-ttu-id="7a4c5-143">[Enviar e extrair os modos de configuração](/powershell/dsc/pullServer).</span><span class="sxs-lookup"><span data-stu-id="7a4c5-143">[Push and Pull Configuration Modes](/powershell/dsc/pullServer).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="7a4c5-144">Planejamento da configuração</span><span class="sxs-lookup"><span data-stu-id="7a4c5-144">Configuration planning</span></span>

<span data-ttu-id="7a4c5-145">Para qualquer implementação de software empresarial há informações que podem ser coletadas com antecedência para ajudar a planear para a arquitetura correta e estar preparado para os passos necessários para concluir a implementação.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-145">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="7a4c5-146">As secções seguintes fornecem informações sobre como preparar e as ligações organizacionais que provavelmente terá de acontecer com antecedência.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-146">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="7a4c5-147">Requisitos de software</span><span class="sxs-lookup"><span data-stu-id="7a4c5-147">Software requirements</span></span>

<span data-ttu-id="7a4c5-148">Implementação de um servidor de solicitação requer a funcionalidade de serviço de DSC do Windows Server.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-148">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="7a4c5-149">Esta funcionalidade foi introduzida no Windows Server 2012 e tiver sido atualizada por meio de versões em curso do Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="7a4c5-149">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="7a4c5-150">Downloads de software</span><span class="sxs-lookup"><span data-stu-id="7a4c5-150">Software downloads</span></span>

<span data-ttu-id="7a4c5-151">Para além de instalar o conteúdo mais recente do Windows Update, existem dois downloads consideradas uma prática recomendada para implementar um servidor de solicitação de DSC: A versão mais recente do Windows Management Framework e como um módulo de DSC para automatizar o provisionamento do servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-151">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="7a4c5-152">WMF</span><span class="sxs-lookup"><span data-stu-id="7a4c5-152">WMF</span></span>

<span data-ttu-id="7a4c5-153">Windows Server 2012 R2 inclui um recurso com o nome do serviço de DSC.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-153">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="7a4c5-154">O recurso de DSC serviço fornece a funcionalidade de servidor de solicitação, incluindo os binários que suportam o ponto final de OData.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-154">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span>
<span data-ttu-id="7a4c5-155">WMF está incluído no Windows Server e é atualizado a uma cadência agile entre as versões do Windows Server.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-155">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span> <span data-ttu-id="7a4c5-156">[Novas versões do WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616) podem incluir atualizações para a funcionalidade serviço de DSC.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-156">[New versions of WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616)  can include updates to the DSC Service feature.</span></span> <span data-ttu-id="7a4c5-157">Por esse motivo, é uma prática recomendada para transferir a versão mais recente do WMF e para rever as notas de versão para determinar se a versão inclui uma atualização para o recurso de serviço do DSC.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-157">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="7a4c5-158">Também deve consultar a secção das notas de versão que indica se o estado de design para uma atualização ou cenário está listado como estável ou experimentais.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-158">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span>
<span data-ttu-id="7a4c5-159">Para permitir um ciclo de lançamento ágil, funcionalidades individuais podem ser declaradas estáveis, que indica que o recurso está pronta para ser utilizada num ambiente de produção, mesmo quando o WMF é lançado em pré-visualização.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-159">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span>
<span data-ttu-id="7a4c5-160">Outros recursos que tenham sido atualizados historicamente por versões do WMF (consulte as notas de versão do WMF para obter mais detalhes):</span><span class="sxs-lookup"><span data-stu-id="7a4c5-160">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

- <span data-ttu-id="7a4c5-161">Windows PowerShell de Windows PowerShell de script integrado</span><span class="sxs-lookup"><span data-stu-id="7a4c5-161">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
- <span data-ttu-id="7a4c5-162">Serviços da Web de PowerShell Windows Environment (ISE) (gestão de OData</span><span class="sxs-lookup"><span data-stu-id="7a4c5-162">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
- <span data-ttu-id="7a4c5-163">Extensão do IIS) Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="7a4c5-163">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="7a4c5-164">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="7a4c5-164">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="7a4c5-165">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="7a4c5-165">DSC resource</span></span>

<span data-ttu-id="7a4c5-166">A implementação de um servidor de solicitação pode ser simplificada ao aprovisionar o serviço usando um script de configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-166">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="7a4c5-167">Este documento inclui scripts de configuração que podem ser utilizados para implementar um nó de servidor pronto de produção.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-167">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="7a4c5-168">Para utilizar os scripts de configuração, um módulo de DSC é necessário ou seja não incluídos no Windows Server.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-168">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="7a4c5-169">É o nome do módulo de necessários **xPSDesiredStateConfiguration**, que inclui o recurso de DSC **xDscWebService**.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-169">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="7a4c5-170">O módulo de xPSDesiredStateConfiguration pode ser transferido [aqui](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span><span class="sxs-lookup"><span data-stu-id="7a4c5-170">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="7a4c5-171">Utilize o `Install-Module` cmdlet a partir de **PowerShellGet** módulo.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-171">Use the `Install-Module` cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="7a4c5-172">O **PowerShellGet** módulo irá transferir o módulo para:</span><span class="sxs-lookup"><span data-stu-id="7a4c5-172">The **PowerShellGet** module will download the module to:</span></span>

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="7a4c5-173">Tarefas de planeamento</span><span class="sxs-lookup"><span data-stu-id="7a4c5-173">Planning task</span></span>|
---|
<span data-ttu-id="7a4c5-174">Tem acesso para os ficheiros de instalação para Windows Server 2012 R2?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-174">Do you have access to the installation files for Windows Server 2012 R2?</span></span>|
<span data-ttu-id="7a4c5-175">O ambiente de implantação terão acesso à Internet para transferir WMF e o módulo a partir da Galeria online?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-175">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>|
<span data-ttu-id="7a4c5-176">Como instalar as atualizações de segurança mais recentes depois de instalar o sistema operativo?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-176">How will you install the latest security updates after installing the operating system?</span></span>|
<span data-ttu-id="7a4c5-177">O ambiente terão acesso à Internet para obter atualizações ou terão um servidor local do Windows Server Update Services (WSUS)?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-177">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>|
<span data-ttu-id="7a4c5-178">Tem acesso aos ficheiros de instalação do Windows Server que já incluem atualizações por meio de injeção offline?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-178">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>|

### <a name="hardware-requirements"></a><span data-ttu-id="7a4c5-179">Requisitos de hardware</span><span class="sxs-lookup"><span data-stu-id="7a4c5-179">Hardware requirements</span></span>

<span data-ttu-id="7a4c5-180">Implementações de servidor de solicitação são suportadas em servidores físicos e virtuais.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-180">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="7a4c5-181">Os requisitos de dimensionamento do servidor de solicitação se alinham com os requisitos para o Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-181">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

<span data-ttu-id="7a4c5-182">CPU: 1,4 processador de bits a GHz 64 memória: Espaço em disco de 512 MB: Rede de 32 GB: Adaptador Ethernet Gigabit</span><span class="sxs-lookup"><span data-stu-id="7a4c5-182">CPU: 1.4 GHz 64-bit processor Memory: 512 MB Disk Space: 32 GB Network: Gigabit Ethernet Adapter</span></span>

<span data-ttu-id="7a4c5-183">Tarefas de planeamento</span><span class="sxs-lookup"><span data-stu-id="7a4c5-183">Planning task</span></span>|
---|
<span data-ttu-id="7a4c5-184">Irá implementar em hardware físico ou numa plataforma de Virtualização?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-184">Will you deploy on physical hardware or on a virtualization platform?</span></span>|
<span data-ttu-id="7a4c5-185">O que é o processo para pedir um novo servidor para o seu ambiente de destino?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-185">What is the process to request a new server for your target environment?</span></span>|
<span data-ttu-id="7a4c5-186">O que é o tempo de resposta médio para um servidor para se tornar disponível?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-186">What is the average turnaround time for a server to become available?</span></span>|
<span data-ttu-id="7a4c5-187">O que servidor de tamanho irá pedir?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-187">What size server will you request?</span></span>|

### <a name="accounts"></a><span data-ttu-id="7a4c5-188">Contas</span><span class="sxs-lookup"><span data-stu-id="7a4c5-188">Accounts</span></span>

<span data-ttu-id="7a4c5-189">Não existem não requisitos de conta de serviço para implementar uma instância de servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-189">There are no service account requirements to deploy a pull server instance.</span></span>
<span data-ttu-id="7a4c5-190">No entanto, existem cenários onde o Web site pode ser executado em contexto de uma conta de utilizador local.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-190">However, there are scenarios where the website could run in the context of a local user account.</span></span>
<span data-ttu-id="7a4c5-191">Por exemplo, se houver a necessidade de acesso à partilha de um armazenamento para o conteúdo do Web site e o Windows Server ou o dispositivo que aloja a partilha de armazenamento não estão associados a um domínio.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-191">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="7a4c5-192">Registos DNS</span><span class="sxs-lookup"><span data-stu-id="7a4c5-192">DNS records</span></span>

<span data-ttu-id="7a4c5-193">Terá um nome de servidor a utilizar quando configurar clientes para trabalhar com um ambiente de servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-193">You will need a server name to use when configuring clients to work with a pull server environment.</span></span>
<span data-ttu-id="7a4c5-194">Em ambientes de teste, normalmente, é utilizado o nome de anfitrião do servidor ou o endereço IP para o servidor pode ser utilizado se a resolução de nomes DNS não está disponível.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-194">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span>
<span data-ttu-id="7a4c5-195">Em ambientes de produção ou num ambiente de laboratório que se destina-se para representar uma implementação de produção, a prática recomendada é criar um registo CNAME no DNS.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-195">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="7a4c5-196">Um CNAME DNS permite-lhe criar um alias para fazer referência ao seu host (A) registo.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-196">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span>
<span data-ttu-id="7a4c5-197">A intenção de registo de nome adicionais é aumentar a flexibilidade devem uma ser necessárias alterações no futuro.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-197">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span>
<span data-ttu-id="7a4c5-198">Um CNAME pode ajudar a isolar a configuração do cliente para que as alterações ao ambiente do servidor, como substituir um servidor de solicitação ou adicionar servidores de solicitação adicionais, não precisará de uma alteração correspondente para a configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-198">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="7a4c5-199">Ao escolher um nome para o registo DNS, manter a arquitetura da solução em mente.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-199">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span>
<span data-ttu-id="7a4c5-200">Se utilizar o balanceamento de carga, o certificado utilizado para proteger o tráfego através de HTTPS precisam de partilhar o mesmo nome que o registo DNS.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-200">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span>

<span data-ttu-id="7a4c5-201">Cenário</span><span class="sxs-lookup"><span data-stu-id="7a4c5-201">Scenario</span></span> |<span data-ttu-id="7a4c5-202">Melhor prática</span><span class="sxs-lookup"><span data-stu-id="7a4c5-202">Best Practice</span></span>
:---|:---
<span data-ttu-id="7a4c5-203">Ambiente de teste</span><span class="sxs-lookup"><span data-stu-id="7a4c5-203">Test Environment</span></span> |<span data-ttu-id="7a4c5-204">Reproduza o ambiente de produção planeada, se possível.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-204">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="7a4c5-205">Um nome de anfitrião do servidor é adequada para configurações simples.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-205">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="7a4c5-206">Se o DNS não estiver disponível, um endereço IP pode ser utilizado em lugar de um nome de anfitrião.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-206">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>|
<span data-ttu-id="7a4c5-207">Implementação de nó único</span><span class="sxs-lookup"><span data-stu-id="7a4c5-207">Single Node Deployment</span></span> |<span data-ttu-id="7a4c5-208">Crie um registo CNAME no DNS que aponta para o nome de anfitrião do servidor.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-208">Create a DNS CNAME record that points to the server hostname.</span></span>|

<span data-ttu-id="7a4c5-209">Para obter mais informações, consulte [configurar o DNS Round Robin no Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="7a4c5-209">For more information, see [Configuring DNS Round Robin in Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span></span>

<span data-ttu-id="7a4c5-210">Tarefas de planeamento</span><span class="sxs-lookup"><span data-stu-id="7a4c5-210">Planning task</span></span>|
---|
<span data-ttu-id="7a4c5-211">Sabe quem entrar em contato para que os registos DNS criados e alterados?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-211">Do you know who to contact to have DNS records created and changed?</span></span>|
<span data-ttu-id="7a4c5-212">O que é a resposta média para um pedido para um registo DNS?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-212">What is the average turnaround for a request for a DNS record?</span></span>|
<span data-ttu-id="7a4c5-213">Precisa pedir os registros de nome de anfitrião (A) estáticos para os servidores?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-213">Do you need to request static Hostname (A) records for servers?</span></span>|
<span data-ttu-id="7a4c5-214">O que irá pedir como um CNAME?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-214">What will you request as a CNAME?</span></span>|
<span data-ttu-id="7a4c5-215">Se for necessário, o tipo de solução de balanceamento de carga que utilizará?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-215">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="7a4c5-216">(consulte a secção intitulada o balanceamento de carga para obter detalhes)</span><span class="sxs-lookup"><span data-stu-id="7a4c5-216">(see section titled Load Balancing for details)</span></span>|

### <a name="public-key-infrastructure"></a><span data-ttu-id="7a4c5-217">Infraestrutura de chaves públicas</span><span class="sxs-lookup"><span data-stu-id="7a4c5-217">Public Key Infrastructure</span></span>

<span data-ttu-id="7a4c5-218">A maioria das organizações de hoje exigem que o tráfego de rede, especialmente o tráfego que inclua esses dados confidenciais, como a forma como servidores estiverem configurados, deve ser validado e/ou encriptado durante o trânsito.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-218">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span>
<span data-ttu-id="7a4c5-219">Embora seja possível implementar um servidor de solicitação através de HTTP que facilita a solicitações do cliente de limpar o texto, é melhor prática para proteger o tráfego através de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-219">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="7a4c5-220">O serviço pode ser configurado para utilizar HTTPS com um conjunto de parâmetros no recurso de DSC **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-220">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="7a4c5-221">Os requisitos de certificado para proteger o tráfego HTTPS para o servidor de solicitação não são diferentes de proteção de qualquer outro site da web HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-221">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="7a4c5-222">O **servidor Web** modelo num servidor Windows Certificate Services coincida com as capacidades necessárias.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-222">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="7a4c5-223">Tarefas de planeamento</span><span class="sxs-lookup"><span data-stu-id="7a4c5-223">Planning task</span></span>|
---|
<span data-ttu-id="7a4c5-224">Se os pedidos de certificado não são automatizados, que será necessário entrar em contacto para pedidos de um certificado?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-224">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>|
<span data-ttu-id="7a4c5-225">O que é a resposta média para o pedido?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-225">What is the average turnaround for the request?</span></span>|
<span data-ttu-id="7a4c5-226">Como será o ficheiro de certificado ser transferido para si?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-226">How will the certificate file be transferred to you?</span></span>|
<span data-ttu-id="7a4c5-227">Como será a chave privada do certificado ser transferida para si?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-227">How will the certificate private key be transferred to you?</span></span>|
<span data-ttu-id="7a4c5-228">Quanto tempo dura a hora de expiração padrão?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-228">How long is the default expiration time?</span></span>|
<span data-ttu-id="7a4c5-229">Definir um nome DNS para o ambiente de servidor de solicitação, o que pode utilizar para o nome do certificado?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-229">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>|

### <a name="choosing-an-architecture"></a><span data-ttu-id="7a4c5-230">Escolher uma arquitetura</span><span class="sxs-lookup"><span data-stu-id="7a4c5-230">Choosing an architecture</span></span>

<span data-ttu-id="7a4c5-231">Um servidor de solicitação pode ser implementado com um serviço de web hospedado no IIS ou uma partilha de ficheiros SMB.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-231">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="7a4c5-232">Na maioria das situações, a opção de serviço da web irá fornecer maior flexibilidade.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-232">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="7a4c5-233">Não é incomum para tráfego HTTPS de percorrer os limites de rede, ao passo que o tráfego SMB é, muitas vezes, filtrado ou bloqueado entre redes.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-233">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="7a4c5-234">O serviço web também oferece a opção de incluir um servidor de conformidade ou Web Reporting Manager (ambos os tópicos abordados numa futura versão deste documento) que fornecem um mecanismo para que os clientes comunicar o estado para um servidor para visibilidade centralizada.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-234">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span>
<span data-ttu-id="7a4c5-235">SMB fornece uma opção para ambientes em que a política de estabelece que não deve ser utilizado um servidor web e outros requisitos ambientais que fazem com que uma função de servidor web indesejáveis.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-235">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span>
<span data-ttu-id="7a4c5-236">Em ambos os casos, lembre-se avaliar os requisitos para assinar e criptografar o tráfego.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-236">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="7a4c5-237">Políticas IPSEC, assinatura SMB e HTTPS são todas as opções que vale a pena considerar.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-237">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="7a4c5-238">Balanceamento de carga</span><span class="sxs-lookup"><span data-stu-id="7a4c5-238">Load balancing</span></span>

<span data-ttu-id="7a4c5-239">Clientes interagindo com o serviço web fazem um pedido para obter informações que são retornados numa única resposta.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-239">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="7a4c5-240">Não existem pedidos sequenciais são necessários, pelo que não é necessário para a plataforma para garantir sessões são mantidos num único servidor em qualquer ponto no tempo de balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-240">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="7a4c5-241">Tarefas de planeamento</span><span class="sxs-lookup"><span data-stu-id="7a4c5-241">Planning task</span></span>|
---|
<span data-ttu-id="7a4c5-242">O que é solução será utilizada para tráfego entre servidores de balanceamento de carga?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-242">What solution will be used for load balancing traffic across servers?</span></span>|
<span data-ttu-id="7a4c5-243">Se utilizar um balanceador de carga de hardware, o que levará um pedido para adicionar uma nova configuração para o dispositivo?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-243">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>|
<span data-ttu-id="7a4c5-244">O que é a resposta média para um pedido configurar uma nova carga balanceada o serviço web?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-244">What is the average turnaround for a request to configure a new load balanced web service?</span></span>|
<span data-ttu-id="7a4c5-245">As informações que serão necessárias para o pedido?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-245">What information will be required for the request?</span></span>|
<span data-ttu-id="7a4c5-246">Precisará solicitar um IP adicional ou será a equipe responsável por balanceamento de carga tratar disso?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-246">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>|
<span data-ttu-id="7a4c5-247">Tem os registros DNS necessários, e isso necessárias para a equipe responsável por configurar a solução de balanceamento de carga?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-247">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>|
<span data-ttu-id="7a4c5-248">A solução de balanceamento de carga requer que a PKI ser processadas pelo dispositivo ou pode-balanceamento de carga de tráfego HTTPS, desde que existem não requisitos de sessão?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-248">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="7a4c5-249">Configurações de teste e os módulos no servidor de solicitação</span><span class="sxs-lookup"><span data-stu-id="7a4c5-249">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="7a4c5-250">Como parte do planeamento de configuração, terá de pensar sobre o DSC módulos e configurações serão alojadas pelo servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-250">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="7a4c5-251">Para fins de planejamento da configuração é importante ter um entendimento básico de como preparar e implementar conteúdo para um servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-251">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span>

<span data-ttu-id="7a4c5-252">No futuro, esta seção será expandida e incluída no guia de operações para o servidor de solicitação do DSC.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-252">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span>  <span data-ttu-id="7a4c5-253">O guia discutirá o processo de dia a dia para a gestão de módulos e configurações ao longo do tempo com a automatização.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-253">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span>

#### <a name="dsc-modules"></a><span data-ttu-id="7a4c5-254">Módulos de DSC</span><span class="sxs-lookup"><span data-stu-id="7a4c5-254">DSC modules</span></span>

<span data-ttu-id="7a4c5-255">Os clientes que pedem uma configuração terão os módulos necessários do DSC.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-255">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="7a4c5-256">É uma funcionalidade do servidor de solicitação automatizar a distribuição a pedido dos módulos de DSC para clientes.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-256">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="7a4c5-257">Se estiver a implementar um servidor de solicitação pela primeira vez, talvez como um laboratório ou de uma prova de conceito, provavelmente vai depender de módulos de DSC que estão disponíveis a partir de repositórios públicos, como a galeria do PowerShell ou de repositórios do GitHub de PowerShell.org para módulos de DSC .</span><span class="sxs-lookup"><span data-stu-id="7a4c5-257">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="7a4c5-258">É essencial lembrar-se de que mesmo para origens online confiáveis, como a galeria do PowerShell, qualquer módulo que é transferido a partir de um repositório público deve ser revisado por alguém com experiência com o PowerShell e o conhecimento do ambiente em que os módulos será utilizado antes de a ser utilizados na produção.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-258">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="7a4c5-259">Ao concluir esta tarefa é um bom momento para verificar a existência de qualquer carga adicional no módulo que pode ser removido, como scripts de exemplo e documentação.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-259">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="7a4c5-260">Isto irá reduzir a largura de banda de rede por cliente na sua primeira solicitação, quando módulos serão transferidos através da rede do servidor ao cliente.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-260">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="7a4c5-261">Cada módulo tem de ser empacotado num formato específico, um ficheiro ZIP com o nome ModuleName_Version.zip que contém a carga de módulo.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-261">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="7a4c5-262">Depois do ficheiro é copiado para o servidor tem de ser criado um ficheiro de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-262">After the file is copied to the server a checksum file must be created.</span></span> <span data-ttu-id="7a4c5-263">Quando os clientes ligam ao servidor, a soma de verificação é usada para verificar que o conteúdo do módulo de DSC não foi alterado, uma vez que foi publicada.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-263">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="7a4c5-264">Tarefas de planeamento</span><span class="sxs-lookup"><span data-stu-id="7a4c5-264">Planning task</span></span>|
---|
<span data-ttu-id="7a4c5-265">Se estiver a planear um ambiente de laboratório ou teste que cenários são fundamentais para validar?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-265">If you are planning a test or lab environment which scenarios are key to validate?</span></span>|
<span data-ttu-id="7a4c5-266">Existem módulos publicamente disponíveis que contêm recursos para cobrir tudo o que precisa, ou precisará de criar seus próprios recursos?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-266">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>|
<span data-ttu-id="7a4c5-267">Seu ambiente terão acesso à Internet para obter os módulos públicos?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-267">Will your environment have Internet access to retrieve public modules?</span></span>|
<span data-ttu-id="7a4c5-268">Quem será responsável pela revisão módulos de DSC?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-268">Who will be responsible for reviewing DSC modules?</span></span>|
<span data-ttu-id="7a4c5-269">Se estiver a planear um ambiente de produção que irá utilizar como um repositório local para armazenar os módulos de DSC?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-269">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>|
<span data-ttu-id="7a4c5-270">Uma equipa central aceitará módulos de DSC das equipas de aplicações?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-270">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="7a4c5-271">Qual será o processo?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-271">What will the process be?</span></span>|
<span data-ttu-id="7a4c5-272">Irá automatizar empacotamento, copiar e criar uma soma de verificação para os módulos de DSC prontos para produção para o servidor, a partir do seu repositório de origem?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-272">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>|
<span data-ttu-id="7a4c5-273">Sua equipe será responsável por gerenciar também a plataforma de automatização?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-273">Will your team be responsible for managing the automation platform as well?</span></span>|

#### <a name="dsc-configurations"></a><span data-ttu-id="7a4c5-274">Configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="7a4c5-274">DSC configurations</span></span>

<span data-ttu-id="7a4c5-275">A finalidade de um servidor de solicitação é fornecer um mecanismo centralizado para distribuição de configurações de DSC por nós de cliente.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-275">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="7a4c5-276">As configurações são armazenadas no servidor, como documentos do MOF.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-276">The configurations are stored on the server as MOF documents.</span></span>
<span data-ttu-id="7a4c5-277">Cada documento será nomeado com um exclusivo **Guid**.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-277">Each document will be named with a unique **Guid**.</span></span> <span data-ttu-id="7a4c5-278">Quando os clientes estão configurados para ligar com um servidor de solicitação, eles também têm o **Guid** para a configuração deve pedir.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-278">When clients are configured to connect with a pull server, they are also given the **Guid** for the configuration they should request.</span></span> <span data-ttu-id="7a4c5-279">Este sistema de referência de configurações por **Guid** garante que é exclusivo global e é flexível, de modo a que pode ser aplicada uma configuração com granularidade por nó, ou como uma configuração de função que abranja vários servidores que devem ter configurações idênticas.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-279">This system of referencing configurations by **Guid** guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="7a4c5-280">GUIDs</span><span class="sxs-lookup"><span data-stu-id="7a4c5-280">Guids</span></span>

<span data-ttu-id="7a4c5-281">Planear a configuração **Guids** vale a pena de atenção adicional ao pensar numa implementação de servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-281">Planning for configuration **Guids** is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="7a4c5-282">Não existe nenhum requisito específico para saber como lidar com **Guids** e o processo é provável que seja exclusivo para cada ambiente.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-282">There is no specific requirement for how to handle **Guids** and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="7a4c5-283">O processo pode variar de simples a complexos: um ficheiro CSV armazenado de forma centralizada, uma tabela SQL simples, um CMDB ou uma solução complexa que requerem integração com outra solução de software ou a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-283">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="7a4c5-284">Existem duas abordagens gerais:</span><span class="sxs-lookup"><span data-stu-id="7a4c5-284">There are two general approaches:</span></span>

- <span data-ttu-id="7a4c5-285">**Atribuir Guids por servidor** — fornece uma medida de garantia de que cada configuração de servidor é controlada individualmente.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-285">**Assigning Guids per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="7a4c5-286">Isso fornece um nível de precisão em torno de atualizações e pode funcionar bem em ambientes com alguns servidores.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-286">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
- <span data-ttu-id="7a4c5-287">**Atribuir Guids por função de servidor** — todos os servidores que executam a mesma função, tais como servidores web, utilizem o mesmo GUID para referenciar os dados de configuração necessárias.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-287">**Assigning Guids per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span>  <span data-ttu-id="7a4c5-288">Lembre-se de que se muitos servidores partilharem o mesmo GUID, todos eles seriam atualizados simultaneamente quando a configuração for alterada.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-288">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

  <span data-ttu-id="7a4c5-289">O GUID é algo que devem ser considerados confidenciais dados uma vez que pode ser aproveitado por alguém com más intenções para obter informações sobre como os servidores são implementados e configurados no seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-289">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="7a4c5-290">Para obter mais informações, consulte [alocar em segurança Guids no PowerShell Desired State Configuration extrair modo](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).</span><span class="sxs-lookup"><span data-stu-id="7a4c5-290">For more information, see [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).</span></span>

<span data-ttu-id="7a4c5-291">Tarefas de planeamento</span><span class="sxs-lookup"><span data-stu-id="7a4c5-291">Planning task</span></span>|
---|
<span data-ttu-id="7a4c5-292">Quem será responsável para copiar as configurações para a pasta de servidor de solicitação quando eles estão prontos?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-292">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>|
<span data-ttu-id="7a4c5-293">Se as configurações são criadas por uma equipe de aplicativos, o que o processo será passá-los?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-293">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>|
<span data-ttu-id="7a4c5-294">Tirar partido um repositório para armazenar configurações, como eles são criados, entre as equipes?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-294">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>|
<span data-ttu-id="7a4c5-295">Irá automatizar o processo de copiar as configurações para o servidor e a criação de uma soma de verificação quando eles estão prontos?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-295">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>|
<span data-ttu-id="7a4c5-296">Como mapeará Guids para servidores ou funções, e onde serão isso armazenados?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-296">How will you map Guids to servers or roles, and where will this be stored?</span></span>|
<span data-ttu-id="7a4c5-297">O que irá utilizar como um processo para configurar computadores cliente e como ele integrar com o seu processo para criar e armazenar os Guids de configuração?</span><span class="sxs-lookup"><span data-stu-id="7a4c5-297">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration Guids?</span></span>|

## <a name="installation-guide"></a><span data-ttu-id="7a4c5-298">Guia de instalação</span><span class="sxs-lookup"><span data-stu-id="7a4c5-298">Installation Guide</span></span>

<span data-ttu-id="7a4c5-299">*Scripts fornecidos neste documento são exemplos estáveis. Reveja sempre scripts cuidadosamente antes da execução num ambiente de produção.*</span><span class="sxs-lookup"><span data-stu-id="7a4c5-299">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="7a4c5-300">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7a4c5-300">Prerequisites</span></span>

<span data-ttu-id="7a4c5-301">Para verificar a versão do PowerShell no seu servidor, utilize o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-301">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="7a4c5-302">Se possível, atualize para a versão mais recente do Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-302">If possible, upgrade to the latest version of Windows Management Framework.</span></span>
<span data-ttu-id="7a4c5-303">Em seguida, transferir o `xPsDesiredStateConfiguration` módulo com o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-303">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="7a4c5-304">O comando solicitará sua aprovação antes de transferir o módulo.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-304">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="7a4c5-305">Scripts de instalação e configuração</span><span class="sxs-lookup"><span data-stu-id="7a4c5-305">Installation and configuration scripts</span></span>

<span data-ttu-id="7a4c5-306">O melhor método para implementar um servidor de solicitação de DSC é usar um script de configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-306">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="7a4c5-307">Este documento vai apresentar scripts incluindo ambas as definições básicas que poderia configurar apenas o serviço da web de DSC e definições que poderia configurar um serviço de web de DSC incluindo do Windows Server-a-ponto avançadas.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-307">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="7a4c5-308">Nota:  Atualmente o `xPSDesiredStateConfiguration` módulo de DSC requer que o servidor para ser localidade EN-US.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-308">Note:  Currently the `xPSDesiredStateConfiguration` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="7a4c5-309">Configuração básica para o Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="7a4c5-309">Basic configuration for Windows Server 2012</span></span>

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

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="7a4c5-310">Configuração avançada do Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="7a4c5-310">Advanced configuration for Windows Server 2012 R2</span></span>

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

### <a name="verify-pull-server-functionality"></a><span data-ttu-id="7a4c5-311">Verificar a funcionalidade de servidor de solicitação</span><span class="sxs-lookup"><span data-stu-id="7a4c5-311">Verify pull server functionality</span></span>

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a><span data-ttu-id="7a4c5-312">Configurar os clientes</span><span class="sxs-lookup"><span data-stu-id="7a4c5-312">Configure clients</span></span>

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

## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="7a4c5-313">Referências adicionais, trechos e exemplos</span><span class="sxs-lookup"><span data-stu-id="7a4c5-313">Additional references, snippets, and examples</span></span>

<span data-ttu-id="7a4c5-314">Este exemplo mostra como iniciar manualmente uma ligação de cliente (requer WMF5) para fins de teste.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-314">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span>

```powershell
Update-DscConfiguration –Wait -Verbose
```

<span data-ttu-id="7a4c5-315">O [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet é utilizado para adicionar um tipo de registo CNAME a uma zona DNS.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-315">The [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet is used to add a type CNAME record to a DNS zone.</span></span>

<span data-ttu-id="7a4c5-316">A função de PowerShell para [criar uma soma de verificação e publicar o MOF de DSC para o servidor de solicitação SMB](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) gera automaticamente a soma de verificação necessária e, em seguida, copia a configuração do MOF e ficheiros de soma de verificação para o servidor de solicitação SMB.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-316">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="7a4c5-317">Apêndice - Noções básicas sobre ODATA tipos de ficheiro de dados do serviço</span><span class="sxs-lookup"><span data-stu-id="7a4c5-317">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="7a4c5-318">Um ficheiro de dados é armazenado para criar informações durante a implementação de um servidor de solicitação que inclui o serviço da web de OData.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-318">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="7a4c5-319">O tipo de ficheiro depende do sistema operativo, conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-319">The type of file depends on the operating system, as described below.</span></span>

- <span data-ttu-id="7a4c5-320">**Windows Server 2012** o tipo de ficheiro será sempre. mdb</span><span class="sxs-lookup"><span data-stu-id="7a4c5-320">**Windows Server 2012** The file type will always be   .mdb</span></span>
- <span data-ttu-id="7a4c5-321">**Windows Server 2012 R2** o tipo de ficheiro usará como padrão. edb, a menos que um. mdb é especificado na configuração do</span><span class="sxs-lookup"><span data-stu-id="7a4c5-321">**Windows Server 2012 R2** The file type will default to .edb unless a .mdb is specified in the configuration</span></span>

<span data-ttu-id="7a4c5-322">Na [avançada de script de exemplo](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) para instalar um servidor de solicitação, também encontrará um exemplo de como automaticamente controlar as definições do ficheiro Web. config para impedir que alguma chance de erros causados por tipo de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="7a4c5-322">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>
