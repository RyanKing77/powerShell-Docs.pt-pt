---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Criação avançada de DSC para Composição e Colaboração
ms.openlocfilehash: 3e40ba94de0a53c1c9663553c4ec443b5e0df3fd
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405319"
---
# <a name="advanced-dsc-authoring-for-composition-and-collaboration"></a><span data-ttu-id="90aa8-103">Criação avançada de DSC para Composição e Colaboração</span><span class="sxs-lookup"><span data-stu-id="90aa8-103">Advanced DSC Authoring for Composition and Collaboration</span></span>

<span data-ttu-id="90aa8-104">Este artigo descreve os tipos de abordagens disponíveis para a combinação de recursos e configurações.</span><span class="sxs-lookup"><span data-stu-id="90aa8-104">This article describes the types of approaches available for combining configurations and resources.</span></span>
<span data-ttu-id="90aa8-105">O objetivo de cada cenário é o mesmo, para reduzir a complexidade quando várias configurações preferidas para atingir um servidor de estado de ponto de implantação.</span><span class="sxs-lookup"><span data-stu-id="90aa8-105">The goal for each scenario is the same, to reduce complexity when multiple configurations are preferred to reach a server deployment end state.</span></span>
<span data-ttu-id="90aa8-106">Um exemplo disso seria várias equipes que contribuem para o resultado de uma implementação de servidor, como um proprietário da aplicação mantém o estado da aplicação e a uma equipa central lançar as alterações às linhas de base de segurança.</span><span class="sxs-lookup"><span data-stu-id="90aa8-106">An example of this would be multiple teams contributing to the outcome of a server deployment, such as an application owner maintaining the application state and a central team releasing changes to security baselines.</span></span>
<span data-ttu-id="90aa8-107">As nuances de cada abordagem, incluindo os benefícios e riscos são descritas aqui.</span><span class="sxs-lookup"><span data-stu-id="90aa8-107">The nuances of each approach including the benefits and risks are detailed here.</span></span>

![Pipeline](../images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a><span data-ttu-id="90aa8-109">Tipos de técnicas de criação de colaboração</span><span class="sxs-lookup"><span data-stu-id="90aa8-109">Types of Collaborative Authoring Techniques</span></span>

<span data-ttu-id="90aa8-110">Existem duas soluções criadas com base Local o Gestor de configuração para ativar este conceito:</span><span class="sxs-lookup"><span data-stu-id="90aa8-110">There are two solutions built in to Local Configuration Manager to enable this concept:</span></span>

| <span data-ttu-id="90aa8-111">Conceito</span><span class="sxs-lookup"><span data-stu-id="90aa8-111">Concept</span></span> | <span data-ttu-id="90aa8-112">Informações detalhadas</span><span class="sxs-lookup"><span data-stu-id="90aa8-112">Detailed Information</span></span>
|-|-
| <span data-ttu-id="90aa8-113">Configurações Parciais</span><span class="sxs-lookup"><span data-stu-id="90aa8-113">Partial Configurations</span></span> | [<span data-ttu-id="90aa8-114">Documentação</span><span class="sxs-lookup"><span data-stu-id="90aa8-114">Documentation</span></span>](../pull-server/partialConfigs.md)
| <span data-ttu-id="90aa8-115">Recursos compostos</span><span class="sxs-lookup"><span data-stu-id="90aa8-115">Composite Resources</span></span> | [<span data-ttu-id="90aa8-116">Documentação</span><span class="sxs-lookup"><span data-stu-id="90aa8-116">Documentation</span></span>](../resources/authoringResourceComposite.md)

## <a name="understanding-the-impact-of-each-approach"></a><span data-ttu-id="90aa8-117">Compreender o impacto de cada abordagem</span><span class="sxs-lookup"><span data-stu-id="90aa8-117">Understanding The Impact of Each Approach</span></span>

<span data-ttu-id="90aa8-118">Uma destas soluções pode ser utilizada para gerir o resultado de uma implementação de servidor.</span><span class="sxs-lookup"><span data-stu-id="90aa8-118">Either of these solutions can be used to manage the outcome of a server deployment.</span></span>
<span data-ttu-id="90aa8-119">No entanto, há uma diferença significativa no impacto da utilização de cada abordagem.</span><span class="sxs-lookup"><span data-stu-id="90aa8-119">However, there is significant difference in the impact of using each approach.</span></span>

## <a name="partial-configurations"></a><span data-ttu-id="90aa8-120">Configurações Parciais</span><span class="sxs-lookup"><span data-stu-id="90aa8-120">Partial Configurations</span></span>

<span data-ttu-id="90aa8-121">Ao usar configurações parciais, o Gestor de configuração Local está configurado para gerir várias configurações de forma independente.</span><span class="sxs-lookup"><span data-stu-id="90aa8-121">When using Partial Configurations, Local Configuration Manager is configured to manage multiple configurations independently.</span></span>
<span data-ttu-id="90aa8-122">Configurações são compiladas de forma independente e, em seguida, são atribuídas ao nó.</span><span class="sxs-lookup"><span data-stu-id="90aa8-122">Configurations are compiled independently and then assigned to the node.</span></span>
<span data-ttu-id="90aa8-123">Isso requer o MMC para ser configurado com antecedência com o nome de cada configuração.</span><span class="sxs-lookup"><span data-stu-id="90aa8-123">This requires LCM to be configured in advance with the name of each configuration.</span></span>

![PartialConfiguration](../images/PartialConfiguration.jpg)

<span data-ttu-id="90aa8-125">Configurações parciais fornecem dois ou mais, as equipes de controle completo sobre configuração de um servidor, geralmente sem o benefício de comunicação ou colaboração.</span><span class="sxs-lookup"><span data-stu-id="90aa8-125">Partial Configurations provide two, or more, teams complete control over configuration of a server, often without the benefit of communication or collaboration.</span></span>

<span data-ttu-id="90aa8-126">Os clientes forneceram comentários que isso pode levar a conflitos de recursos, as substituições não intencionais e, por fim, perda de controle de configuração verdadeiro do ativo.</span><span class="sxs-lookup"><span data-stu-id="90aa8-126">Customers have provided feedback that this can lead to resource conflicts, unintentional overrides, and ultimately loss of true configuration control of the asset.</span></span>

<span data-ttu-id="90aa8-127">Além disso, os clientes forneceram comentários que ao usar esse modelo, são pouco provável que ser totalmente testado por meio de um pipeline de lançamento, cada controlar alterações de configuração de equipas que leva a resultados inesperados na produção.</span><span class="sxs-lookup"><span data-stu-id="90aa8-127">Additionally, customers have provided feedback that when using this model, each controlling teams configuration changes are unlikely to be fully tested through a release pipeline, leading to unexpected results in production.</span></span>

<span data-ttu-id="90aa8-128">**É fundamental que um único pipeline ser utilizada para avaliar todos os de alterações de versão para servidores.**</span><span class="sxs-lookup"><span data-stu-id="90aa8-128">**It is critical that a single pipeline be used to evaluate all changes release to servers.**</span></span>

<span data-ttu-id="90aa8-129">Na ilustração abaixo, equipe B libera a respetiva configuração parcial para A equipe do Team A. em seguida, executa seus testes em relação a um servidor com ambas as configurações aplicadas.</span><span class="sxs-lookup"><span data-stu-id="90aa8-129">In the illustration below, Team B releases their partial configuration to Team A. Team A then runs their tests against a server with both configurations applied.</span></span>
<span data-ttu-id="90aa8-130">Nesse modelo, apenas uma autoridade tem permissão para fazer alterações na produção.</span><span class="sxs-lookup"><span data-stu-id="90aa8-130">In this model, only one authority has permission to make changes in production.</span></span>

![PartialSinglePipeline](../images/PartialSinglePipeline.jpg)

<span data-ttu-id="90aa8-132">Quando as alterações são necessárias da Equipe B, deve enviar um pedido de solicitação contra o ambiente de controle de origem de equipe do.</span><span class="sxs-lookup"><span data-stu-id="90aa8-132">When changes are required from Team B, they should submit a Pull Request against Team A's source control environment.</span></span>
<span data-ttu-id="90aa8-133">Seria, em seguida, reveja as alterações usando a automação de teste e de versão para produção quando há certeza de que as alterações não causará erros em aplicações ou serviços hospedados pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="90aa8-133">Team A would then review the changes using test automation and release to production when there is confidence that the changes will not cause errors in the applications or services hosted by the server.</span></span>

## <a name="composite-resources"></a><span data-ttu-id="90aa8-134">Recursos compostos</span><span class="sxs-lookup"><span data-stu-id="90aa8-134">Composite Resources</span></span>

<span data-ttu-id="90aa8-135">Um recurso composto é simplesmente uma configuração de DSC empacotado como um recurso.</span><span class="sxs-lookup"><span data-stu-id="90aa8-135">A composite resource is simply a DSC Configuration packaged as a resource.</span></span>
<span data-ttu-id="90aa8-136">Não existem não requisitos especiais para configurar o LCM para aceitar recursos compostos.</span><span class="sxs-lookup"><span data-stu-id="90aa8-136">There are no special requirements for configuring LCM to accept composite resources.</span></span>
<span data-ttu-id="90aa8-137">Os recursos são utilizados dentro de uma nova configuração e uma única compilação resulta num arquivo MOF.</span><span class="sxs-lookup"><span data-stu-id="90aa8-137">The resources are used within a new configuration and a single compilation results in one MOF file.</span></span>

![CompositeResource](../images/CompositeResource.jpg)

<span data-ttu-id="90aa8-139">Existem dois cenários comuns para recursos compostos.</span><span class="sxs-lookup"><span data-stu-id="90aa8-139">There are two common scenarios for composite resources.</span></span>
<span data-ttu-id="90aa8-140">A primeira é reduzir a complexidade e conceitos abstratos de exclusivos.</span><span class="sxs-lookup"><span data-stu-id="90aa8-140">The first is to reduce complexity and abstract unique concepts.</span></span>
<span data-ttu-id="90aa8-141">O segundo é para permitir que as linhas de base a serem empacotados para uma equipe de aplicativos implementar em segurança por meio do seu pipeline de lançamento para a produção depois de todos os testes foram aprovados.</span><span class="sxs-lookup"><span data-stu-id="90aa8-141">The second is to allow baselines to be packaged for an application team to safely deploy through their release pipeline to production after all tests have passed.</span></span>

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

<span data-ttu-id="90aa8-142">Recursos compostos promovem a composição e colaboração com um pipeline de durante a criação de maturidade operacional</span><span class="sxs-lookup"><span data-stu-id="90aa8-142">Composite resources promote both composition and collaboration using a pipeline while building operational maturity</span></span>

<span data-ttu-id="90aa8-143">Pode estar já a utilizar recursos compostos sem perceber.</span><span class="sxs-lookup"><span data-stu-id="90aa8-143">You might be already using composite resources without realizing it.</span></span>
<span data-ttu-id="90aa8-144">Um exemplo é **ServiceSet**.</span><span class="sxs-lookup"><span data-stu-id="90aa8-144">An example is **ServiceSet**.</span></span>
<span data-ttu-id="90aa8-145">Este recurso gere o estado dos vários serviços do Windows sem listagem-los individualmente.</span><span class="sxs-lookup"><span data-stu-id="90aa8-145">This resource manages the state of multiple Windows Services without listing them individually.</span></span>
<span data-ttu-id="90aa8-146">A propriedade Name aceita uma matriz de cadeias de caracteres para fornecer o nome de cada serviço.</span><span class="sxs-lookup"><span data-stu-id="90aa8-146">The Name property accepts an array of strings to provide the name of each service.</span></span>
<span data-ttu-id="90aa8-147">Quando a configuração é compilada, o MOF irá conter uma seção de serviço exclusiva para cada um dos nomes passados para ServiceSet.</span><span class="sxs-lookup"><span data-stu-id="90aa8-147">When the configuration is compiled, the MOF will contain a unique Service section for each of the Names passed to ServiceSet.</span></span>

<span data-ttu-id="90aa8-148">As organizações podem ter "agentes" ou "middleware", que deve ser instalado em cada servidor.</span><span class="sxs-lookup"><span data-stu-id="90aa8-148">Organizations might have "agents" or "middleware" that should be installed on every server.</span></span>
<span data-ttu-id="90aa8-149">Um recurso composto é a melhor resposta para gerir as dependências, instalação e configuração dessas ferramentas e utilitários.</span><span class="sxs-lookup"><span data-stu-id="90aa8-149">A composite resource is the best answer to managing the dependencies, setup, and configuration of any such tools and utilities.</span></span>

<span data-ttu-id="90aa8-150">A pessoa ou equipe responsável por soluções que abrangem vários servidores cria uma configuração que contém os seus requisitos.</span><span class="sxs-lookup"><span data-stu-id="90aa8-150">The person or team responsible for solutions that span multiple servers authors a configuration containing their requirements.</span></span>
<span data-ttu-id="90aa8-151">Em seguida, a configuração deverá ser empacotada como um recurso composto com base nas instruções fornecidas na documentação do recursos compostos.</span><span class="sxs-lookup"><span data-stu-id="90aa8-151">Next, the configuration would be packaged as a composite resource using instructions provided in the composite resource documentation.</span></span>
<span data-ttu-id="90aa8-152">Por fim, o novo recurso composto deve ser publicado para uma localização, como uma partilha de ficheiros ou NuGet feed onde o aplicativo as equipes possam consumi-la em suas configurações.</span><span class="sxs-lookup"><span data-stu-id="90aa8-152">Finally, the new composite resource should be published to a location such as a file share or NuGet feed where application teams can consume it in their configurations.</span></span>

<span data-ttu-id="90aa8-153">Sempre que a equipe de versões uma nova versão, eles seriam incrementar o número de versão no manifesto do módulo para seus recursos compostos.</span><span class="sxs-lookup"><span data-stu-id="90aa8-153">Each time the team releases a new version, they would increment the version number in the module manifest for their composite resource.</span></span>
<span data-ttu-id="90aa8-154">As equipas de aplicações incluem o recurso composto na configuração criam para o gerenciamento de dependências de aplicações.</span><span class="sxs-lookup"><span data-stu-id="90aa8-154">The application teams include the composite resource in the configuration they author for managing application dependencies.</span></span>
<span data-ttu-id="90aa8-155">Quando as equipes de operações/segurança lançar uma nova versão de seus recursos, eles notificam as equipes de aplicação de uma nova alteração.</span><span class="sxs-lookup"><span data-stu-id="90aa8-155">When the Operations/Security teams release a new version of their resource, they notify the application teams of a new change.</span></span>

<span data-ttu-id="90aa8-156">As equipes de aplicativo podem disparar uma versão para produção em que a única alteração é às linhas de base.</span><span class="sxs-lookup"><span data-stu-id="90aa8-156">The application teams might trigger a release to production where the only change is to baselines.</span></span>
<span data-ttu-id="90aa8-157">No entanto, isso fornece uma oportunidade de avaliar o impacto em aplicativos antes de risco de uma indisponibilidade do serviço.</span><span class="sxs-lookup"><span data-stu-id="90aa8-157">However, this provides an opportunity to evaluate impact to applications before risk of a service outage.</span></span>

<span data-ttu-id="90aa8-158">Nota – enviar comentários sobre a utilização de recursos compostos incluiu críticas que efetuar alterações requer compilação e lançamento de um novo MOF.</span><span class="sxs-lookup"><span data-stu-id="90aa8-158">Note - Feedback regarding the use of composite resources has included criticism that making changes requires compiling and releasing a new MOF.</span></span>
<span data-ttu-id="90aa8-159">Isto é propositado.</span><span class="sxs-lookup"><span data-stu-id="90aa8-159">This is by design.</span></span>
<span data-ttu-id="90aa8-160">Cada nova versão de configuração deve incluir uma referência estática numa versão específica de cada recurso e deve ser validada por testes antes de chegar a nós do servidor de produção.</span><span class="sxs-lookup"><span data-stu-id="90aa8-160">Each new configuration release should include a static reference to a specific version of each resource, and should be validated by tests before reaching production server nodes.</span></span>
<span data-ttu-id="90aa8-161">O processo de teste e lançar as alterações no controle da fonte cria um ambiente seguro para liberar a alteração em lotes de pequenas, mas frequentes.</span><span class="sxs-lookup"><span data-stu-id="90aa8-161">The process of testing and releasing changes from source control creates a safe environment for releasing change in small but frequent batches.</span></span>

<span data-ttu-id="90aa8-162">Para obter mais informações sobre a utilização de pipelines de versão para gerir a infraestrutura básica, consulte o White Paper: [O modelo de Pipeline de lançamento](../further-reading/whitepapers.md).</span><span class="sxs-lookup"><span data-stu-id="90aa8-162">For more information about using release pipelines to manage core infrastructure, see the whitepaper: [The Release Pipeline Model](../further-reading/whitepapers.md).</span></span>