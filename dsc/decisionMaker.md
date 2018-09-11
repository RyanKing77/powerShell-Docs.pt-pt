---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Descrição Geral do Desired State Configuration para Decisores
ms.openlocfilehash: 7c36aa5fadeab8bcb381f316288d102b5ce402e2
ms.sourcegitcommit: ac20e0faaa37142e9c6e4507a21df2f4a3fdbece
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339842"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a><span data-ttu-id="74705-103">Descrição Geral do Desired State Configuration para Decisores</span><span class="sxs-lookup"><span data-stu-id="74705-103">Desired State Configuration Overview for Decision Makers</span></span>

<span data-ttu-id="74705-104">Este documento descreve os benefícios empresariais da utilização do Windows PowerShell Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="74705-104">This document describes the business benefits of using Windows PowerShell Desired State Configuration (DSC).</span></span> <span data-ttu-id="74705-105">Não é um guia técnico.</span><span class="sxs-lookup"><span data-stu-id="74705-105">It is not a technical guide.</span></span>

## <a name="what-is-desired-state-configuration"></a><span data-ttu-id="74705-106">O que é a Desired State Configuration?</span><span class="sxs-lookup"><span data-stu-id="74705-106">What Is Desired State Configuration?</span></span>

<span data-ttu-id="74705-107">PowerShell Desired State Configuration é uma plataforma de gestão de configuração integrada no Windows com base em padrões abertos.</span><span class="sxs-lookup"><span data-stu-id="74705-107">PowerShell Desired State Configuration is a configuration management platform built into Windows that is based on open standards.</span></span> <span data-ttu-id="74705-108">DSC é flexível o suficiente para funcionar de maneira confiável e consistente em cada fase do ciclo de vida de implementação (desenvolvimento, teste, pré-produção, produção), bem como durante o Escalamento horizontal.</span><span class="sxs-lookup"><span data-stu-id="74705-108">DSC is flexible enough to function reliably and consistently in each stage of the deployment lifecycle (development, test, pre-production, production), as well as during scale-out.</span></span>

<span data-ttu-id="74705-109">DSC centra-se em [configurações](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="74705-109">DSC centers around [configurations](configurations.md).</span></span>
<span data-ttu-id="74705-110">Uma configuração é um documento de fácil leitura que descreve um ambiente composto de computadores ("nós") com características específicas.</span><span class="sxs-lookup"><span data-stu-id="74705-110">A configuration is an easy-to-read document that describes an environment made up of computers ("nodes") with specific characteristics.</span></span>
<span data-ttu-id="74705-111">Essas características podem ser tão simples como garantir que uma funcionalidade específica do Windows está ativado ou tão complexo como implantar o SharePoint.</span><span class="sxs-lookup"><span data-stu-id="74705-111">These characteristics can be as simple as ensuring a specific Windows feature is enabled or as complex as deploying SharePoint.</span></span>

<span data-ttu-id="74705-112">DSC também tem monitorização e relatórios incorporados.</span><span class="sxs-lookup"><span data-stu-id="74705-112">DSC also has monitoring and reporting built in.</span></span>
<span data-ttu-id="74705-113">Se um sistema já não for compatível, DSC pode emitir um alerta e agir para corrigir o sistema.</span><span class="sxs-lookup"><span data-stu-id="74705-113">If a system is no longer compliant, DSC can raise an alert and act to correct the system.</span></span>

## <a name="benefits-of-using-desired-state-configuration"></a><span data-ttu-id="74705-114">Vantagens da utilização do Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="74705-114">Benefits of Using Desired State Configuration</span></span>

<span data-ttu-id="74705-115">Configurações foram concebidas para serem facilmente lidas, armazenados e atualizado.</span><span class="sxs-lookup"><span data-stu-id="74705-115">Configurations are designed to be easily read, stored, and updated.</span></span>
<span data-ttu-id="74705-116">Configurações de declarar que os dispositivos de destino de Estado devem ser, em vez de escrever instruções sobre como colocá-los com esse Estado.</span><span class="sxs-lookup"><span data-stu-id="74705-116">Configurations declare the state target devices should be in, instead of writing instructions for how to put them in that state.</span></span>
<span data-ttu-id="74705-117">Isso torna muito menos dispendiosa saber mais, adotar, implementar e manter a configuração através do DSC.</span><span class="sxs-lookup"><span data-stu-id="74705-117">This makes it much less costly to learn, adopt, implement, and maintain configuration through DSC.</span></span>

<span data-ttu-id="74705-118">Criação de configurações, significa que os passos de implementação complexos são capturados como uma "única fonte de verdade" numa única localização.</span><span class="sxs-lookup"><span data-stu-id="74705-118">Creating configurations means that complex deployment steps are captured as a "single source of truth" in a single location.</span></span>
<span data-ttu-id="74705-119">Isso torna muito menos propenso a erros Implantações repetidas de um conjunto específico de máquinas.</span><span class="sxs-lookup"><span data-stu-id="74705-119">This makes repeated deployments of a specific set of machines much less error-prone.</span></span>
<span data-ttu-id="74705-120">Por sua vez, que torna as Implantações mais rápidas e confiáveis que permite um rápido retorno em implementações complexas.</span><span class="sxs-lookup"><span data-stu-id="74705-120">In turn, making deployments faster and more reliable which enables a quick turnaround on complex deployments.</span></span>

<span data-ttu-id="74705-121">As configurações também são partilhável através da [galeria do PowerShell](https://powershellgallery.com) que significa que cenários comuns e as melhores práticas poderá já existem para o trabalho que precisa ser feito.</span><span class="sxs-lookup"><span data-stu-id="74705-121">Configurations are also shareable via the [PowerShell Gallery](https://powershellgallery.com) meaning common scenarios and best practices might already exist for the work that needs to be done.</span></span>


## <a name="desired-state-configuration-and-devops"></a><span data-ttu-id="74705-122">Desired State Configuration e DevOps</span><span class="sxs-lookup"><span data-stu-id="74705-122">Desired State Configuration and DevOps</span></span>

<span data-ttu-id="74705-123">DSC foi projetado tendo [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) em mente, uma combinação de pessoas, processos e ferramentas que permitem a implementação rápida e de iteração focada no fornecimento de valor para os utilizadores finais se internos ou externos.</span><span class="sxs-lookup"><span data-stu-id="74705-123">DSC was designed with [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) in mind, a combination of people, processes, and tools that allow for rapid deployment and iteration focused on delivering value to end users whether internal or external.</span></span>
<span data-ttu-id="74705-124">Ter uma única configuração definem um meio de ambiente que os desenvolvedores pode codificar seus requisitos numa configuração, verifique que a configuração no controle de fonte e as equipas de operação pode facilmente implementar código sem a necessidade de passar por propenso a erros processos manuais.</span><span class="sxs-lookup"><span data-stu-id="74705-124">Having a single configuration define an environment means that developers can encode their requirements into a configuration, check that configuration into source control, and operation teams can easily deploy code without having to go through error-prone manual processes.</span></span>

<span data-ttu-id="74705-125">As configurações são também [condicionada por dados](configData.md), que torna mais fácil para o ops identificar e alterar os ambientes sem a intervenção do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="74705-125">Configurations are also [data-driven](configData.md), which makes it easier for ops to identify and change environments without developer intervention.</span></span>

## <a name="desired-state-configuration-on--and-off-premises"></a><span data-ttu-id="74705-126">Desired State Configuration em - e fora do local</span><span class="sxs-lookup"><span data-stu-id="74705-126">Desired State Configuration On- and Off-Premises</span></span>

<span data-ttu-id="74705-127">DSC pode ser utilizado para gerir implementações no local e externamente.</span><span class="sxs-lookup"><span data-stu-id="74705-127">DSC can be used to manage both on-premise and off-premise deployments.</span></span>
<span data-ttu-id="74705-128">Para soluções no local, DSC tem um [servidor de solicitação](pullServer.md) que podem ser utilizados para centralizar o gerenciamento de máquinas e gerar relatórios sobre o respetivo estado.</span><span class="sxs-lookup"><span data-stu-id="74705-128">For on-premise solutions, DSC has a [pull server](pullServer.md) that can be used to centralize management of machines and report on their status.</span></span>
<span data-ttu-id="74705-129">Para soluções de nuvem, DSC é-utilizável onde quer que o Windows é utilizável.</span><span class="sxs-lookup"><span data-stu-id="74705-129">For cloud solutions, DSC is usable wherever Windows is usable.</span></span>
<span data-ttu-id="74705-130">Também existem ofertas específicas do Azure criadas numa, Desired State Configuration, tais como [automatização do Azure](https://azure.microsoft.com/en-us/documentation/services/automation/), que centraliza a criação de relatórios de DSC.</span><span class="sxs-lookup"><span data-stu-id="74705-130">There are also specific offerings from Azure built on Desired State Configuration, such as [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), which centralizes reporting of DSC.</span></span>

## <a name="dsc-and-compatibility"></a><span data-ttu-id="74705-131">DSC e compatibilidade</span><span class="sxs-lookup"><span data-stu-id="74705-131">DSC and Compatibility</span></span>

<span data-ttu-id="74705-132">Embora o DSC foi introduzida no Windows Server 2012 R2, está disponível para sistemas de operativos de nível inferior através do pacote do Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="74705-132">Although DSC was introduced in Windows Server 2012 R2, it is available for down-level operating systems via the Windows Management Framework (WMF) package.</span></span>
<span data-ttu-id="74705-133">Podem encontrar mais informações sobre o WMF no [home page do PowerShell](/powershell/).</span><span class="sxs-lookup"><span data-stu-id="74705-133">More information about the WMF can be found on the [PowerShell homepage](/powershell/).</span></span>

<span data-ttu-id="74705-134">DSC também pode ser utilizado para gerir o Linux.</span><span class="sxs-lookup"><span data-stu-id="74705-134">DSC can also be used to manage Linux.</span></span> <span data-ttu-id="74705-135">Para obter mais informações, consulte [introdução ao DSC para Linux](lnxGettingStarted.md).</span><span class="sxs-lookup"><span data-stu-id="74705-135">For more information, see [Getting Started with DSC for Linux](lnxGettingStarted.md).</span></span>
