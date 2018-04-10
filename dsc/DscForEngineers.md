---
ms.date: 10/13/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Descrição Geral do Desired State Configuration para Decisores
ms.openlocfilehash: 3d2d4b7e09fb699751151d7af641410bae3b38a4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="desired-state-configuration-overview-for-engineers"></a><span data-ttu-id="35e68-103">Descrição Geral do Desired State Configuration para Engenheiros</span><span class="sxs-lookup"><span data-stu-id="35e68-103">Desired State Configuration Overview for Engineers</span></span>

<span data-ttu-id="35e68-104">Este documento destina-se a equipas de programador as operações de e compreender as vantagens do PowerShell pretendido Estado Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="35e68-104">This document is intended for developer and operations teams to understand the benefits of PowerShell Desired State Configuration (DSC).</span></span>
<span data-ttu-id="35e68-105">Para obter uma vista de nível superior do valor DSC fornece, consulte [Desired Configuration descrição geral do Estado para os decisores](decisionMaker.md)</span><span class="sxs-lookup"><span data-stu-id="35e68-105">For a higher level view of the value DSC provides, please see [Desired State Configuration Overview for Decision Makers](decisionMaker.md)</span></span>

## <a name="benefits-of-desired-state-configuration"></a><span data-ttu-id="35e68-106">Vantagens da configuração do estado pretendido</span><span class="sxs-lookup"><span data-stu-id="35e68-106">Benefits of Desired State Configuration</span></span>

<span data-ttu-id="35e68-107">Não existe DSC para:</span><span class="sxs-lookup"><span data-stu-id="35e68-107">DSC exists to:</span></span>

- <span data-ttu-id="35e68-108">Reduzir a complexidade do processamento de scripts do Windows</span><span class="sxs-lookup"><span data-stu-id="35e68-108">Decrease the complexity of scripting in Windows</span></span>
- <span data-ttu-id="35e68-109">Aumentar a velocidade da iteração</span><span class="sxs-lookup"><span data-stu-id="35e68-109">Increase the speed of iteration</span></span>

<span data-ttu-id="35e68-110">O conceito de "implementação contínua" se está a tornar mais importante.</span><span class="sxs-lookup"><span data-stu-id="35e68-110">The concept of "continuous deployment" is becoming more important.</span></span>
<span data-ttu-id="35e68-111">A implementação contínua significa que a capacidade de implementar com frequência, potencialmente, muitas vezes por dia.</span><span class="sxs-lookup"><span data-stu-id="35e68-111">Continuous deployment means the ability to deploy frequently, potentially many times per day.</span></span>
<span data-ttu-id="35e68-112">O objetivo estas implementações são não para corrigir algo mas obter algo publicados rapidamente.</span><span class="sxs-lookup"><span data-stu-id="35e68-112">The purpose of these deployments are not to fix something but to get something published quickly.</span></span>
<span data-ttu-id="35e68-113">Por obter novas funcionalidades através de programação numa operação como facilmente e fiável quanto possível, reduzir o tempo ao valor de lógica de negócio novas.</span><span class="sxs-lookup"><span data-stu-id="35e68-113">By getting new features through development into operation as smoothly and reliably as possible, you reduce time-to-value of new business logic.</span></span>

<span data-ttu-id="35e68-114">A mudança para implica uma solução de implementação que utiliza um modelo de modelo "declarativa", em que um ambiente de estado de fim é declarado como texto e publicado um motor de implementação de computação na nuvem.</span><span class="sxs-lookup"><span data-stu-id="35e68-114">The move towards cloud computing implies a deployment solution that utilizes a "declarative" template model, where an end state environment is declared as text and published to a deployment engine.</span></span>
<span data-ttu-id="35e68-115">Esta técnica de implementação permite rápida alteração, escala, com resiliência contra ameaças de falha porque em qualquer altura a implementação pode ser repetida consistentemente para garantir um estado final.</span><span class="sxs-lookup"><span data-stu-id="35e68-115">This deployment technique allows for rapid change, at scale, with resilience against threat of failure because at any time the deployment can be consistently repeated to guarantee an end state.</span></span>
<span data-ttu-id="35e68-116">A criação de ferramentas e serviços que suportam este estilo das operações através da automatização é uma resposta a estas alterações.</span><span class="sxs-lookup"><span data-stu-id="35e68-116">The creation of tools and services that support this style of operations through automation is a response to these changes.</span></span>

<span data-ttu-id="35e68-117">DSC é uma plataforma que fornece declarativa e implementação (repetíveis) idempotent, configuração e conformidade.</span><span class="sxs-lookup"><span data-stu-id="35e68-117">DSC is a platform that provides declarative and idempotent (repeatable) deployment, configuration and conformance.</span></span>
<span data-ttu-id="35e68-118">A plataforma de DSC permite-lhe garantir que os componentes do seu centro de dados têm a configuração correta, o que evita a erros e impede a falhas de implementação dispendiosos.</span><span class="sxs-lookup"><span data-stu-id="35e68-118">The DSC platform enables you to ensure that the components of your data center have the correct configuration, which avoids errors and prevents costly deployment failures.</span></span>
<span data-ttu-id="35e68-119">Por encará-los configurações de DSC como parte do código da aplicação, DSC permite a implementação contínua.</span><span class="sxs-lookup"><span data-stu-id="35e68-119">By treating DSC configurations as part of application code, DSC enables continuous deployment.</span></span>
<span data-ttu-id="35e68-120">A configuração de DSC deve ser atualizada como parte da aplicação, garantindo o conhecimento necessário para implementar a aplicação é sempre atualizados e pronto a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="35e68-120">The DSC configuration should be updated as a part of the application, ensuring that the knowledge needed to deploy the application is always up-to-date and ready to be used.</span></span>

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a><span data-ttu-id="35e68-121">"Preciso de PowerShell, por que motivo precisa a configuração de estado pretendido?"</span><span class="sxs-lookup"><span data-stu-id="35e68-121">"I have PowerShell, why do I need Desired State Configuration?"</span></span>

<span data-ttu-id="35e68-122">Objetivo separado de configurações de DSC ou "o que pretender fazer", da execução, ou "como pretender fazê-lo."</span><span class="sxs-lookup"><span data-stu-id="35e68-122">DSC configurations separate intent, or "what I want to do", from execution, or "how I want to do it."</span></span>
<span data-ttu-id="35e68-123">Isto significa que a lógica de execução é contida os recursos.</span><span class="sxs-lookup"><span data-stu-id="35e68-123">This means the logic of execution is contained within the resources.</span></span>
<span data-ttu-id="35e68-124">Os utilizadores não é necessário saber como implementar ou implementar uma funcionalidade quando está disponível um recurso de DSC para essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="35e68-124">Users do not have to know how to implement or deploy a feature when a DSC resource for that feature is available.</span></span>
<span data-ttu-id="35e68-125">Isto permite ao utilizador para se focarem na estrutura da implementação deles.</span><span class="sxs-lookup"><span data-stu-id="35e68-125">This allows the user to focus on the structure of their deployment.</span></span>

<span data-ttu-id="35e68-126">Por exemplo, scripts do PowerShell devem ter o seguinte aspeto:</span><span class="sxs-lookup"><span data-stu-id="35e68-126">As an example, PowerShell scripts should look like this:</span></span>
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
<span data-ttu-id="35e68-127">Este script é simples, comprehensible e fácil.</span><span class="sxs-lookup"><span data-stu-id="35e68-127">This script is simple, comprehensible, and straightforward.</span></span>
<span data-ttu-id="35e68-128">No entanto, se tentar colocar nesse script em produção, será executado em vários problemas.</span><span class="sxs-lookup"><span data-stu-id="35e68-128">However, if you try putting that script into production, you will run into several issues.</span></span>
<span data-ttu-id="35e68-129">O que acontece se que o script é executado duas vezes numa linha?</span><span class="sxs-lookup"><span data-stu-id="35e68-129">What happens if that script is run twice in a row?</span></span>
<span data-ttu-id="35e68-130">O que acontece se Bernardo tinha anteriormente acesso total à partilha?</span><span class="sxs-lookup"><span data-stu-id="35e68-130">What happens if Bob previously had Full Access to the share?</span></span>

<span data-ttu-id="35e68-131">Para compensar estes problemas, uma versão do script "real" procurará próximo de algo semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="35e68-131">To compensate for these issues, a "real" version of the script will look closer to something like:</span></span>
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

<span data-ttu-id="35e68-132">Este script é mais complexo, com muitos de lógica e processamento de erros.</span><span class="sxs-lookup"><span data-stu-id="35e68-132">This script is more complex, with plenty of logic and error handling.</span></span>
<span data-ttu-id="35e68-133">O script for mais complexo porque já não são indicar que o que pretende efectuada, mas *como fazê-lo*.</span><span class="sxs-lookup"><span data-stu-id="35e68-133">The script is more complex because you are no longer stating what you want done, but *how to do it*.</span></span>

<span data-ttu-id="35e68-134">DSC permite-lhe dizer o que pretende efectuada e a lógica subjacente é abstracted ausente.</span><span class="sxs-lookup"><span data-stu-id="35e68-134">DSC allows you to say what you want done, and the underlying logic is abstracted away.</span></span>

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
          ReadAccess  = "Alice"
          FullAccess  = "Bob"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

<span data-ttu-id="35e68-135">Este script está corretamente formatado e simples para leitura.</span><span class="sxs-lookup"><span data-stu-id="35e68-135">This script is cleanly formatted and straightforward to read.</span></span>
<span data-ttu-id="35e68-136">Os caminhos lógicos e processamento de erros são continuam presentes no [recursos](resources.md) implementação, mas invisíveis ao autor do script.</span><span class="sxs-lookup"><span data-stu-id="35e68-136">The logic paths and error handling are still present in the [resource](resources.md) implementation, but invisible to the script author.</span></span>

## <a name="separating-environment-from-structure"></a><span data-ttu-id="35e68-137">Separação de ambiente de estrutura</span><span class="sxs-lookup"><span data-stu-id="35e68-137">Separating Environment from Structure</span></span>

<span data-ttu-id="35e68-138">Um padrão comum no DevOps consiste em vários ambientes para implementação.</span><span class="sxs-lookup"><span data-stu-id="35e68-138">A common pattern in DevOps is to have multiple environments for deployment.</span></span>
<span data-ttu-id="35e68-139">Por exemplo, poderá ser um ambiente de "dev" utilizado para rapidamente criar protótipos novo código.</span><span class="sxs-lookup"><span data-stu-id="35e68-139">For example, there might be a "dev" environment used to quickly prototype new code.</span></span>
<span data-ttu-id="35e68-140">O código do ambiente de "dev" entra no ambiente de "teste", em que outras pessoas Certifique-se a nova funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="35e68-140">The code from the "dev" environment goes into a "test" environment, where other people verify the new functionality.</span></span>
<span data-ttu-id="35e68-141">Por fim, o código entra "prod" ou o ambiente de produção do site em direto.</span><span class="sxs-lookup"><span data-stu-id="35e68-141">Finally, the code goes into "prod", or the live site production environment.</span></span>

<span data-ttu-id="35e68-142">Configurações de DSC acomodar este pipeline de teste-dev-prod através da utilização de [dados de configuração](configData.md).</span><span class="sxs-lookup"><span data-stu-id="35e68-142">DSC configurations accommodate this dev-test-prod pipeline through the use of [configuration data](configData.md).</span></span>
<span data-ttu-id="35e68-143">Isto deduz ainda mais a diferença entre a estrutura da configuração de nós geridos.</span><span class="sxs-lookup"><span data-stu-id="35e68-143">This further abstracts the difference between the structure of the configuration from the nodes that are managed.</span></span>
<span data-ttu-id="35e68-144">Por exemplo, pode definir uma configuração que requer um SQL server, um servidor IIS e um servidor de camada média.</span><span class="sxs-lookup"><span data-stu-id="35e68-144">For example, you can define a configuration that requires a SQL server, an IIS server, and a middle-tier server.</span></span>
<span data-ttu-id="35e68-145">Independentemente da que nós recebem as diferentes partes desta configuração, essas três elementos sempre estará presentes.</span><span class="sxs-lookup"><span data-stu-id="35e68-145">Regardless of what nodes receive the different pieces of this configuration, those three elements will always be present.</span></span>
<span data-ttu-id="35e68-146">Pode utilizar dados de configuração para apontar três todos os elementos para a mesma máquina para um ambiente de desenvolvimento, separado saída três elementos para três máquinas diferentes para um ambiente de teste e, finalmente, para todos os servidores de produção para o ambiente de prod.</span><span class="sxs-lookup"><span data-stu-id="35e68-146">You can use configuration data to point all three elements towards the same machine for a dev environment, separate out the three elements to three different machines for a test environment, and finally towards all your production servers for the prod environment.</span></span>
<span data-ttu-id="35e68-147">Para implementar os ambientes diferentes, pode invocar **início DscConfiguration** com os dados de configuração correto para o ambiente de destino.</span><span class="sxs-lookup"><span data-stu-id="35e68-147">To deploy to the different environments, you can invoke **Start-DscConfiguration** with the correct configuration data for the environment you want to target.</span></span>

## <a name="see-also"></a><span data-ttu-id="35e68-148">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="35e68-148">See Also</span></span>

[<span data-ttu-id="35e68-149">Configurações</span><span class="sxs-lookup"><span data-stu-id="35e68-149">Configurations</span></span>](configurations.md)

[<span data-ttu-id="35e68-150">Dados de configuração</span><span class="sxs-lookup"><span data-stu-id="35e68-150">Configuration Data</span></span>](configData.md)

[<span data-ttu-id="35e68-151">Recursos</span><span class="sxs-lookup"><span data-stu-id="35e68-151">Resources</span></span>](resources.md)