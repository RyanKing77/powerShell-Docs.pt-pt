---
ms.date: 10/13/2017
keywords: DSC, powershell, configuração, a configuração
title: Descrição Geral do Desired State Configuration para Engenheiros
ms.openlocfilehash: 0e599c2218cd2df29dbd0529006be5e1ef17ce5f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079987"
---
# <a name="desired-state-configuration-overview-for-engineers"></a><span data-ttu-id="a7971-103">Descrição Geral do Desired State Configuration para Engenheiros</span><span class="sxs-lookup"><span data-stu-id="a7971-103">Desired State Configuration Overview for Engineers</span></span>

<span data-ttu-id="a7971-104">Este documento destina-se para as equipas de programação e operações compreender os benefícios do PowerShell Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="a7971-104">This document is intended for developer and operations teams to understand the benefits of PowerShell Desired State Configuration (DSC).</span></span>
<span data-ttu-id="a7971-105">Para uma vista de nível superior do valor DSC fornece, veja [Desired State Configuration descrição geral para tomadores de decisões](decisionMaker.md)</span><span class="sxs-lookup"><span data-stu-id="a7971-105">For a higher level view of the value DSC provides, please see [Desired State Configuration Overview for Decision Makers](decisionMaker.md)</span></span>

## <a name="benefits-of-desired-state-configuration"></a><span data-ttu-id="a7971-106">Benefícios do Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="a7971-106">Benefits of Desired State Configuration</span></span>

<span data-ttu-id="a7971-107">DSC existe para:</span><span class="sxs-lookup"><span data-stu-id="a7971-107">DSC exists to:</span></span>

- <span data-ttu-id="a7971-108">Diminuir a complexidade do processamento de scripts no Windows</span><span class="sxs-lookup"><span data-stu-id="a7971-108">Decrease the complexity of scripting in Windows</span></span>
- <span data-ttu-id="a7971-109">Aumentar a velocidade de iteração</span><span class="sxs-lookup"><span data-stu-id="a7971-109">Increase the speed of iteration</span></span>

<span data-ttu-id="a7971-110">O conceito de "implementação contínua" está se tornando mais importante.</span><span class="sxs-lookup"><span data-stu-id="a7971-110">The concept of "continuous deployment" is becoming more important.</span></span>
<span data-ttu-id="a7971-111">Implementação contínua significa que a capacidade de implementar com frequência, potencialmente, muitas vezes por dia.</span><span class="sxs-lookup"><span data-stu-id="a7971-111">Continuous deployment means the ability to deploy frequently, potentially many times per day.</span></span>
<span data-ttu-id="a7971-112">A finalidade destas implementações são não para corrigir algo, mas para obter algo publicados de forma rápida.</span><span class="sxs-lookup"><span data-stu-id="a7971-112">The purpose of these deployments are not to fix something but to get something published quickly.</span></span>
<span data-ttu-id="a7971-113">Obtendo novos recursos por meio do desenvolvimento em operação tão suave e de forma fiável do possível, reduza tempo / valor da nova lógica de negócios.</span><span class="sxs-lookup"><span data-stu-id="a7971-113">By getting new features through development into operation as smoothly and reliably as possible, you reduce time-to-value of new business logic.</span></span>

<span data-ttu-id="a7971-114">O movimento na direção de implica uma solução de implementação que utiliza um modelo de modelo "declarativa", em que um ambiente de estado final é declarado como texto e publicado um mecanismo de implementação de informática na cloud.</span><span class="sxs-lookup"><span data-stu-id="a7971-114">The move towards cloud computing implies a deployment solution that utilizes a "declarative" template model, where an end state environment is declared as text and published to a deployment engine.</span></span>
<span data-ttu-id="a7971-115">Essa técnica de implantação permite alterações rápidas, à escala, com resiliência contra ameaças de falha porque a qualquer momento a implementação pode ser repetida consistentemente para garantir um estado final.</span><span class="sxs-lookup"><span data-stu-id="a7971-115">This deployment technique allows for rapid change, at scale, with resilience against threat of failure because at any time the deployment can be consistently repeated to guarantee an end state.</span></span>
<span data-ttu-id="a7971-116">A criação de ferramentas e serviços que oferecem suporte a esse estilo de operações por meio de automação é uma resposta a essas mudanças.</span><span class="sxs-lookup"><span data-stu-id="a7971-116">The creation of tools and services that support this style of operations through automation is a response to these changes.</span></span>

<span data-ttu-id="a7971-117">DSC é uma plataforma que fornece declarativa e a implantação de (repetível) de idempotentes, a configuração e a conformidade.</span><span class="sxs-lookup"><span data-stu-id="a7971-117">DSC is a platform that provides declarative and idempotent (repeatable) deployment, configuration and conformance.</span></span>
<span data-ttu-id="a7971-118">A plataforma de DSC permite-lhe garantir que os componentes do seu centro de dados tenham a configuração correta, o que evita erros e evita falhas de implementação de alto custo.</span><span class="sxs-lookup"><span data-stu-id="a7971-118">The DSC platform enables you to ensure that the components of your data center have the correct configuration, which avoids errors and prevents costly deployment failures.</span></span>
<span data-ttu-id="a7971-119">Ao tratar as configurações de DSC como parte do código do aplicativo, o DSC permite a implementação contínua.</span><span class="sxs-lookup"><span data-stu-id="a7971-119">By treating DSC configurations as part of application code, DSC enables continuous deployment.</span></span>
<span data-ttu-id="a7971-120">A configuração de DSC deve ser atualizada como parte da aplicação, garantindo que o conhecimento necessário para implementar a aplicação é sempre atualizado e pronto a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="a7971-120">The DSC configuration should be updated as a part of the application, ensuring that the knowledge needed to deploy the application is always up-to-date and ready to be used.</span></span>

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a><span data-ttu-id="a7971-121">"Eu tenho o PowerShell, por que razão necessito de Desired State Configuration?"</span><span class="sxs-lookup"><span data-stu-id="a7971-121">"I have PowerShell, why do I need Desired State Configuration?"</span></span>

<span data-ttu-id="a7971-122">Objetivo de separado de configurações de DSC, ou "o que quero fazer", de execução, ou "como eu quero fazê-lo."</span><span class="sxs-lookup"><span data-stu-id="a7971-122">DSC configurations separate intent, or "what I want to do", from execution, or "how I want to do it."</span></span>
<span data-ttu-id="a7971-123">Isso significa que a lógica de execução está contida nos recursos.</span><span class="sxs-lookup"><span data-stu-id="a7971-123">This means the logic of execution is contained within the resources.</span></span>
<span data-ttu-id="a7971-124">Os utilizadores não têm de saber como implementar ou implantar um recurso quando um recurso de DSC para essa funcionalidade está disponível.</span><span class="sxs-lookup"><span data-stu-id="a7971-124">Users do not have to know how to implement or deploy a feature when a DSC resource for that feature is available.</span></span>
<span data-ttu-id="a7971-125">Isto permite ao utilizador para se concentrar a estrutura da implementação deles.</span><span class="sxs-lookup"><span data-stu-id="a7971-125">This allows the user to focus on the structure of their deployment.</span></span>

<span data-ttu-id="a7971-126">Por exemplo, scripts do PowerShell devem ter um aspeto semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="a7971-126">As an example, PowerShell scripts should look like this:</span></span>
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
<span data-ttu-id="a7971-127">Este script é simples, simples e compreensível.</span><span class="sxs-lookup"><span data-stu-id="a7971-127">This script is simple, comprehensible, and straightforward.</span></span>
<span data-ttu-id="a7971-128">No entanto, se tentar colocar esse script em produção, será executado em vários problemas.</span><span class="sxs-lookup"><span data-stu-id="a7971-128">However, if you try putting that script into production, you will run into several issues.</span></span>
<span data-ttu-id="a7971-129">O que acontece se que o script for executado duas vezes numa linha?</span><span class="sxs-lookup"><span data-stu-id="a7971-129">What happens if that script is run twice in a row?</span></span>
<span data-ttu-id="a7971-130">O que acontece se Bob tinha anteriormente o acesso total à partilha?</span><span class="sxs-lookup"><span data-stu-id="a7971-130">What happens if Bob previously had Full Access to the share?</span></span>

<span data-ttu-id="a7971-131">Para compensar estes problemas, uma versão "real" o script ficará mais de perto para algo como:</span><span class="sxs-lookup"><span data-stu-id="a7971-131">To compensate for these issues, a "real" version of the script will look closer to something like:</span></span>
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

<span data-ttu-id="a7971-132">Este script é mais complexo, com muita lógica e tratamento de erros.</span><span class="sxs-lookup"><span data-stu-id="a7971-132">This script is more complex, with plenty of logic and error handling.</span></span>
<span data-ttu-id="a7971-133">O script é mais complexo porque já não são que diz o que deseja concluído, mas *como fazê-lo*.</span><span class="sxs-lookup"><span data-stu-id="a7971-133">The script is more complex because you are no longer stating what you want done, but *how to do it*.</span></span>

<span data-ttu-id="a7971-134">DSC, pode dizer o que deseja concluído e a lógica subjacente é abstraída.</span><span class="sxs-lookup"><span data-stu-id="a7971-134">DSC allows you to say what you want done, and the underlying logic is abstracted away.</span></span>

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Bob"
          FullAccess  = "Alice"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

<span data-ttu-id="a7971-135">Este script está corretamente formatado e fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="a7971-135">This script is cleanly formatted and straightforward to read.</span></span>
<span data-ttu-id="a7971-136">Os caminhos de lógica e o tratamento de erros ainda estão presentes no [recursos](../resources/resources.md) implementação, mas invisível para o autor do script.</span><span class="sxs-lookup"><span data-stu-id="a7971-136">The logic paths and error handling are still present in the [resource](../resources/resources.md) implementation, but invisible to the script author.</span></span>

## <a name="separating-environment-from-structure"></a><span data-ttu-id="a7971-137">Separar o ambiente de estrutura</span><span class="sxs-lookup"><span data-stu-id="a7971-137">Separating Environment from Structure</span></span>

<span data-ttu-id="a7971-138">Um padrão comum em DevOps é ter vários ambientes para a implementação.</span><span class="sxs-lookup"><span data-stu-id="a7971-138">A common pattern in DevOps is to have multiple environments for deployment.</span></span>
<span data-ttu-id="a7971-139">Por exemplo, pode ser um ambiente de "dev" usado para rapidamente código novo do protótipo.</span><span class="sxs-lookup"><span data-stu-id="a7971-139">For example, there might be a "dev" environment used to quickly prototype new code.</span></span>
<span data-ttu-id="a7971-140">O código do ambiente de "dev" vai para um ambiente de "teste", onde outras pessoas verificar a nova funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="a7971-140">The code from the "dev" environment goes into a "test" environment, where other people verify the new functionality.</span></span>
<span data-ttu-id="a7971-141">Por fim, o código entra "prod" ou o ambiente de produção do site em direto.</span><span class="sxs-lookup"><span data-stu-id="a7971-141">Finally, the code goes into "prod", or the live site production environment.</span></span>

<span data-ttu-id="a7971-142">Configurações de DSC acomodar este pipeline de desenvolvimento-teste-prod através da utilização de [dados de configuração](../configurations/configData.md).</span><span class="sxs-lookup"><span data-stu-id="a7971-142">DSC configurations accommodate this dev-test-prod pipeline through the use of [configuration data](../configurations/configData.md).</span></span>
<span data-ttu-id="a7971-143">Isso ainda mais abstrai a diferença entre a estrutura da configuração a partir de nós que são geridos.</span><span class="sxs-lookup"><span data-stu-id="a7971-143">This further abstracts the difference between the structure of the configuration from the nodes that are managed.</span></span>
<span data-ttu-id="a7971-144">Por exemplo, pode definir uma configuração que requer um SQL server, um servidor IIS e um servidor de camada intermediária.</span><span class="sxs-lookup"><span data-stu-id="a7971-144">For example, you can define a configuration that requires a SQL server, an IIS server, and a middle-tier server.</span></span>
<span data-ttu-id="a7971-145">Independentemente do que nós recebem as diferentes partes desta configuração, esses três elementos sempre estará presentes.</span><span class="sxs-lookup"><span data-stu-id="a7971-145">Regardless of what nodes receive the different pieces of this configuration, those three elements will always be present.</span></span>
<span data-ttu-id="a7971-146">Pode utilizar dados de configuração para apontar a todos os três elementos em direção à mesma máquina para um ambiente de desenvolvimento, separado horizontalmente os três elementos para três máquinas diferentes para um ambiente de teste e, finalmente, para todos os servidores de produção para o ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="a7971-146">You can use configuration data to point all three elements towards the same machine for a dev environment, separate out the three elements to three different machines for a test environment, and finally towards all your production servers for the prod environment.</span></span>
<span data-ttu-id="a7971-147">Para implementar em diferentes ambientes, pode invocar **Start-dscconfiguration para** com os dados de configuração correto para o ambiente de destino.</span><span class="sxs-lookup"><span data-stu-id="a7971-147">To deploy to the different environments, you can invoke **Start-DscConfiguration** with the correct configuration data for the environment you want to target.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7971-148">Veja Também</span><span class="sxs-lookup"><span data-stu-id="a7971-148">See Also</span></span>

[<span data-ttu-id="a7971-149">Configurações</span><span class="sxs-lookup"><span data-stu-id="a7971-149">Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="a7971-150">Dados de configuração</span><span class="sxs-lookup"><span data-stu-id="a7971-150">Configuration Data</span></span>](../configurations/configData.md)

[<span data-ttu-id="a7971-151">Recursos</span><span class="sxs-lookup"><span data-stu-id="a7971-151">Resources</span></span>](../resources/resources.md)
