---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Criar um pipeline de integração contínua e a implementação contínua com DSC
ms.openlocfilehash: faeef5022cbd984cab0620b69db19de8b84cca0e
ms.sourcegitcommit: 68093cc12a7a22c53d11ce7d33c18622921a0dd1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2018
ms.locfileid: "36940349"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a><span data-ttu-id="07661-103">Criar um pipeline de integração contínua e a implementação contínua com DSC</span><span class="sxs-lookup"><span data-stu-id="07661-103">Building a Continuous Integration and Continuous Deployment pipeline with DSC</span></span>

<span data-ttu-id="07661-104">Este exemplo demonstra como criar um pipeline de implementação contínua/integração contínua (CI/CD) utilizando o PowerShell, DSC, Pester e Visual Studio Team Foundation Server (TFS).</span><span class="sxs-lookup"><span data-stu-id="07661-104">This example demonstrates how to build a Continuous Integration/Continuous Deployment (CI/CD) pipeline by using PowerShell, DSC, Pester, and Visual Studio Team Foundation Server (TFS).</span></span>

<span data-ttu-id="07661-105">Depois do pipeline é criado e configurado, pode utilizá-la completamente implementar, configurar e testar um servidor DNS e associados registos de anfitrião.</span><span class="sxs-lookup"><span data-stu-id="07661-105">After the pipeline is built and configured, you can use it to fully deploy, configure and test a DNS server and associated host records.</span></span>
<span data-ttu-id="07661-106">Este processo simula a primeira parte de um pipeline que seria utilizada num ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="07661-106">This process simulates the first part of a pipeline that would be used in a development environment.</span></span>

<span data-ttu-id="07661-107">Um pipeline de CI/CD automatizado ajuda-o a atualização de software mais rápido e mais fiável, garantir que todo o código é testado e de que é uma compilação atual do seu código disponível em todas as vezes.</span><span class="sxs-lookup"><span data-stu-id="07661-107">An automated CI/CD pipeline helps you update software faster and more reliably, ensuring that all code is tested, and that a current build of your code is available at all times.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="07661-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="07661-108">Prerequisites</span></span>

<span data-ttu-id="07661-109">Para utilizar este exemplo, deve estar familiarizado com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="07661-109">To use this example, you should be familiar with the following:</span></span>

- <span data-ttu-id="07661-110">Conceitos do CD de CI.</span><span class="sxs-lookup"><span data-stu-id="07661-110">CI-CD concepts.</span></span> <span data-ttu-id="07661-111">É possível localizar uma referência de boa [o modelo de Pipeline de versão](http://aka.ms/thereleasepipelinemodelpdf).</span><span class="sxs-lookup"><span data-stu-id="07661-111">A good reference can be found at [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf).</span></span>
- <span data-ttu-id="07661-112">[Git](https://git-scm.com/) controlo de origem</span><span class="sxs-lookup"><span data-stu-id="07661-112">[Git](https://git-scm.com/) source control</span></span>
- <span data-ttu-id="07661-113">O [Pester](https://github.com/pester/Pester) testar framework</span><span class="sxs-lookup"><span data-stu-id="07661-113">The [Pester](https://github.com/pester/Pester) testing framework</span></span>
- [<span data-ttu-id="07661-114">Do Team Foundation Server</span><span class="sxs-lookup"><span data-stu-id="07661-114">Team Foundation Server</span></span>](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a><span data-ttu-id="07661-115">O que precisa</span><span class="sxs-lookup"><span data-stu-id="07661-115">What you will need</span></span>

<span data-ttu-id="07661-116">Para compilar e executar este exemplo, terá um ambiente com vários computadores e/ou máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="07661-116">To build and run this example, you will need an environment with several computers and/or virtual machines.</span></span>

### <a name="client"></a><span data-ttu-id="07661-117">Cliente</span><span class="sxs-lookup"><span data-stu-id="07661-117">Client</span></span>

<span data-ttu-id="07661-118">Este é o computador onde irá fazer todo o trabalho configurar e executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="07661-118">This is the computer where you'll do all of the work setting up and running the example.</span></span>

<span data-ttu-id="07661-119">O computador cliente tem de ser um computador Windows com o seguinte instalado:</span><span class="sxs-lookup"><span data-stu-id="07661-119">The client computer must be a Windows computer with the following installed:</span></span>

- [<span data-ttu-id="07661-120">Git</span><span class="sxs-lookup"><span data-stu-id="07661-120">Git</span></span>](https://git-scm.com/)
- <span data-ttu-id="07661-121">um repositório de local git clonado a partir do https://github.com/PowerShell/Demo_CI</span><span class="sxs-lookup"><span data-stu-id="07661-121">a local git repo cloned from https://github.com/PowerShell/Demo_CI</span></span>
- <span data-ttu-id="07661-122">editor de texto, tal como [Visual Studio Code](https://code.visualstudio.com/)</span><span class="sxs-lookup"><span data-stu-id="07661-122">a text editor, such as [Visual Studio Code](https://code.visualstudio.com/)</span></span>

### <a name="tfssrv1"></a><span data-ttu-id="07661-123">TFSSrv1</span><span class="sxs-lookup"><span data-stu-id="07661-123">TFSSrv1</span></span>

<span data-ttu-id="07661-124">O computador que aloja o servidor TFS onde vai definir a compilação e versão.</span><span class="sxs-lookup"><span data-stu-id="07661-124">The computer that hosts the TFS server where you will define your build and release.</span></span>
<span data-ttu-id="07661-125">Este computador tem de ter [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) instalado.</span><span class="sxs-lookup"><span data-stu-id="07661-125">This computer must have [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installed.</span></span>

### <a name="buildagent"></a><span data-ttu-id="07661-126">BuildAgent</span><span class="sxs-lookup"><span data-stu-id="07661-126">BuildAgent</span></span>

<span data-ttu-id="07661-127">O computador que executa o Windows criar agente que cria o projeto.</span><span class="sxs-lookup"><span data-stu-id="07661-127">The computer that runs the Windows build agent that builds the project.</span></span>
<span data-ttu-id="07661-128">Este computador tem de ter um Windows criar o agente instalado e em execução.</span><span class="sxs-lookup"><span data-stu-id="07661-128">This computer must have a Windows build agent installed and running.</span></span>
<span data-ttu-id="07661-129">Consulte [implementar um agente no Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) para obter instruções sobre como instalar e executar o Windows criar agente.</span><span class="sxs-lookup"><span data-stu-id="07661-129">See [Deploy an agent on Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) for instructions on how to install and run a Windows build agent.</span></span>

<span data-ttu-id="07661-130">Também tem de instalar ambas as `xDnsServer` e `xNetworking` módulos de DSC neste computador.</span><span class="sxs-lookup"><span data-stu-id="07661-130">You also need to install both the `xDnsServer` and `xNetworking` DSC modules on this computer.</span></span>

### <a name="testagent1"></a><span data-ttu-id="07661-131">TestAgent1</span><span class="sxs-lookup"><span data-stu-id="07661-131">TestAgent1</span></span>

<span data-ttu-id="07661-132">Este é o computador que está configurado como um servidor DNS na configuração de DSC neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="07661-132">This is the computer that is configured as a DNS server by the DSC configuration in this example.</span></span>
<span data-ttu-id="07661-133">O computador tem de estar em execução [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="07661-133">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

### <a name="testagent2"></a><span data-ttu-id="07661-134">TestAgent2</span><span class="sxs-lookup"><span data-stu-id="07661-134">TestAgent2</span></span>

<span data-ttu-id="07661-135">Este é o computador que aloja o site que este exemplo configura.</span><span class="sxs-lookup"><span data-stu-id="07661-135">This is the computer that hosts the website this example configures.</span></span>
<span data-ttu-id="07661-136">O computador tem de estar em execução [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="07661-136">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

## <a name="add-the-code-to-tfs"></a><span data-ttu-id="07661-137">Adicione o código para o TFS</span><span class="sxs-lookup"><span data-stu-id="07661-137">Add the code to TFS</span></span>

<span data-ttu-id="07661-138">Iremos começar ao criar um repositório de Git no TFS e importar o código do seu repositório local no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="07661-138">We'll start out by creating a Git repository in TFS, and importing the code from your local repository on the client computer.</span></span>
<span data-ttu-id="07661-139">Se já não clonar o repositório de Demo_CI para o seu computador cliente, fazê-lo agora, por isso, executando o seguinte comando do git:</span><span class="sxs-lookup"><span data-stu-id="07661-139">If you have not already cloned the Demo_CI repository to your client computer, do so now by running the following git command:</span></span>

`git clone https://github.com/PowerShell/Demo_CI`

1. <span data-ttu-id="07661-140">No computador cliente, navegue para o servidor TFS num web browser.</span><span class="sxs-lookup"><span data-stu-id="07661-140">On your client computer, navigate to your TFS server in a web browser.</span></span>
1. <span data-ttu-id="07661-141">No TFS, [criar um novo projeto de equipa](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) denominado Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="07661-141">In TFS, [Create a new team project](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) named Demo_CI.</span></span>

   <span data-ttu-id="07661-142">Certifique-se de que **controlo de versão** está definido como **Git**.</span><span class="sxs-lookup"><span data-stu-id="07661-142">Make sure that **Version control** is set to **Git**.</span></span>
1. <span data-ttu-id="07661-143">No computador cliente, adicione um remoto para o repositório que acabou de criar no TFS com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="07661-143">On your client computer, add a remote to the repository you just created in TFS with the following command:</span></span>

   `git remote add tfs <YourTFSRepoURL>`

   <span data-ttu-id="07661-144">Onde `<YourTFSRepoURL>` é o URL do clone para o repositório do TFS que criou no passo anterior.</span><span class="sxs-lookup"><span data-stu-id="07661-144">Where `<YourTFSRepoURL>` is the clone URL to the TFS repository you created in the previous step.</span></span>

   <span data-ttu-id="07661-145">Se não souber onde encontrar este URL, consulte [clonar um repositório de Git existente](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).</span><span class="sxs-lookup"><span data-stu-id="07661-145">If you don't know where to find this URL, see [Clone an existing Git repo](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).</span></span>
1. <span data-ttu-id="07661-146">Emitir o código do seu repositório local para o seu repositório TFS com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="07661-146">Push the code from your local repository to your TFS repository with the following command:</span></span>

   `git push tfs --all`
1. <span data-ttu-id="07661-147">O repositório TFS será preenchido com o código de Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="07661-147">The TFS repository will be populated with the Demo_CI code.</span></span>

> [!NOTE]
> <span data-ttu-id="07661-148">Este exemplo utiliza o código de `ci-cd-example` ramo do repositório de Git.</span><span class="sxs-lookup"><span data-stu-id="07661-148">This example uses the code in the `ci-cd-example` branch of the Git repo.</span></span>
> <span data-ttu-id="07661-149">Lembre-se de que especifique este ramo como o ramo predefinido no seu projeto do TFS e para os acionadores de CI/CD que cria.</span><span class="sxs-lookup"><span data-stu-id="07661-149">Be sure to specify this branch as the default branch in your TFS project, and for the CI/CD triggers you create.</span></span>

## <a name="understanding-the-code"></a><span data-ttu-id="07661-150">Noções sobre o código</span><span class="sxs-lookup"><span data-stu-id="07661-150">Understanding the code</span></span>

<span data-ttu-id="07661-151">Antes de iremos criar pipelines de compilação e implementação, vamos ver alguns do código para compreender o que está a suceder.</span><span class="sxs-lookup"><span data-stu-id="07661-151">Before we create the build and deployment pipelines, let's look at some of the code to understand what is going on.</span></span>
<span data-ttu-id="07661-152">No computador cliente, abra o editor de texto favorito e navegue para a raiz do repositório de Demo_CI Git.</span><span class="sxs-lookup"><span data-stu-id="07661-152">On your client computer, open your favorite text editor and navigate to the root of your Demo_CI Git repository.</span></span>

### <a name="the-dsc-configuration"></a><span data-ttu-id="07661-153">A configuração DSC</span><span class="sxs-lookup"><span data-stu-id="07661-153">The DSC configuration</span></span>

<span data-ttu-id="07661-154">Abra o ficheiro `DNSServer.ps1` (de raiz do repositório Demo_CI local, `./InfraDNS/Configs/DNSServer.ps1`).</span><span class="sxs-lookup"><span data-stu-id="07661-154">Open the file `DNSServer.ps1` (from the root of the local Demo_CI repository, `./InfraDNS/Configs/DNSServer.ps1`).</span></span>

<span data-ttu-id="07661-155">Este ficheiro contém a configuração de DSC que configura o servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="07661-155">This file contains the DSC configuration that sets up the DNS server.</span></span> <span data-ttu-id="07661-156">Segue-se na íntegra:</span><span class="sxs-lookup"><span data-stu-id="07661-156">Here it is in its entirety:</span></span>

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

<span data-ttu-id="07661-157">Tenha em atenção o `Node` instrução:</span><span class="sxs-lookup"><span data-stu-id="07661-157">Notice the `Node` statement:</span></span>

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

<span data-ttu-id="07661-158">Isto localiza quaisquer nós que foram definidos como tendo uma função de `DNSServer` no [dados de configuração](configData.md), que é criado pelo `DevEnv.ps1` script.</span><span class="sxs-lookup"><span data-stu-id="07661-158">This finds any nodes that were defined as having a role of `DNSServer` in the [configuration data](configData.md), which is created by the `DevEnv.ps1` script.</span></span>

<span data-ttu-id="07661-159">Pode ler mais sobre o `Where` método [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="07661-159">You can read more about the `Where` method in [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)</span></span>

<span data-ttu-id="07661-160">É importante utilizar dados de configuração para definir nós ao efetuar CI porque as informações do nó, provavelmente, serão alterado entre ambientes e utilização de dados de configuração permite-lhe facilmente efetuar alterações às informações do nó, sem alterar o código de configuração.</span><span class="sxs-lookup"><span data-stu-id="07661-160">Using configuration data to define nodes is important when doing CI because node information will likely change between environments, and using configuration data allows you to easily make changes to node information without changing the configuration code.</span></span>

<span data-ttu-id="07661-161">No primeiro bloco de recursos, a configuração chama o [WindowsFeature](windowsFeatureResource.md) para se certificar de que a funcionalidade DNS está ativada.</span><span class="sxs-lookup"><span data-stu-id="07661-161">In the first resource block, the configuration calls the [WindowsFeature](windowsFeatureResource.md) to ensure that the DNS feature is enabled.</span></span>
<span data-ttu-id="07661-162">Os blocos de recursos que se seguem recursos chamada a partir de [xDnsServer](https://github.com/PowerShell/xDnsServer) módulo para configurar a zona primária e registos DNS.</span><span class="sxs-lookup"><span data-stu-id="07661-162">The resource blocks that follow call resources from the [xDnsServer](https://github.com/PowerShell/xDnsServer) module to configure the primary zone and DNS records.</span></span>

<span data-ttu-id="07661-163">Tenha em atenção que as duas `xDnsRecord` blocos são moldados numa `foreach` ciclos iterar através de matrizes de dados de configuração.</span><span class="sxs-lookup"><span data-stu-id="07661-163">Notice that the two `xDnsRecord` blocks are wrapped in `foreach` loops that iterate through arrays in the configuration data.</span></span>
<span data-ttu-id="07661-164">Novamente, os dados de configuração são criados pelo `DevEnv.ps1` script, que vamos ver seguinte.</span><span class="sxs-lookup"><span data-stu-id="07661-164">Again, the configuration data is created by the `DevEnv.ps1` script, which we'll look at next.</span></span>

### <a name="configuration-data"></a><span data-ttu-id="07661-165">Dados de configuração</span><span class="sxs-lookup"><span data-stu-id="07661-165">Configuration data</span></span>

<span data-ttu-id="07661-166">O `DevEnv.ps1` ficheiro (de raiz do repositório Demo_CI local, `./InfraDNS/DevEnv.ps1`) Especifica os dados de configuração específicas do ambiente de uma tabela hash e, em seguida, transmite essa tabela hash para uma chamada para o `New-DscConfigurationDataDocument` função, o que está definida na `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span><span class="sxs-lookup"><span data-stu-id="07661-166">The `DevEnv.ps1` file (from the root of the local Demo_CI repository, `./InfraDNS/DevEnv.ps1`) specifies the environment-specific configuration data in a hashtable, and then passes that hashtable to a call to the `New-DscConfigurationDataDocument` function, which is defined in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span></span>

<span data-ttu-id="07661-167">O `DevEnv.ps1` ficheiro:</span><span class="sxs-lookup"><span data-stu-id="07661-167">The `DevEnv.ps1` file:</span></span>

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

<span data-ttu-id="07661-168">O `New-DscConfigurationDataDocument` função (definido no `\Assets\DscPipelineTools\DscPipelineTools.psm1`) através de programação cria um documento de dados de configuração a partir da tabela hash (dados do nó) e a matriz (dados do nó não) que são transmitidos como o `RawEnvData` e `OtherEnvData` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="07661-168">The `New-DscConfigurationDataDocument` function (defined in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmatically creates a configuration data document from the hashtable (node data) and array (non-node data) that are passed as the `RawEnvData` and `OtherEnvData` parameters.</span></span>

<span data-ttu-id="07661-169">No nosso caso, apenas o `RawEnvData` parâmetro é utilizado.</span><span class="sxs-lookup"><span data-stu-id="07661-169">In our case, only the `RawEnvData` parameter is used.</span></span>

### <a name="the-psake-build-script"></a><span data-ttu-id="07661-170">O script de compilação psake</span><span class="sxs-lookup"><span data-stu-id="07661-170">The psake build script</span></span>

<span data-ttu-id="07661-171">O [psake](https://github.com/psake/psake) compilar o script definido no `Build.ps1` (de raiz do repositório Demo_CI, `./InfraDNS/Build.ps1`) define as tarefas que façam parte de compilação.</span><span class="sxs-lookup"><span data-stu-id="07661-171">The [psake](https://github.com/psake/psake) build script defined in `Build.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Build.ps1`) defines tasks that are part of the build.</span></span>
<span data-ttu-id="07661-172">Também define as tarefas que cada tarefa depende.</span><span class="sxs-lookup"><span data-stu-id="07661-172">It also defines which other tasks each task depends on.</span></span>
<span data-ttu-id="07661-173">Quando foi invocado, o script de psake garante que a tarefa especificada (ou a tarefa com o nome `Default` se não for especificado nenhum) é executado e que também executam todas as dependências (isto é recursiva, para que as dependências de dependências de executam, e assim sucessivamente).</span><span class="sxs-lookup"><span data-stu-id="07661-173">When invoked, the psake script ensures that the specified task (or the task named `Default` if none is specified) runs, and that all dependencies also run (this is recursive, so that dependencies of dependencies run, and so on).</span></span>

<span data-ttu-id="07661-174">Neste exemplo, o `Default` tarefas está definida como:</span><span class="sxs-lookup"><span data-stu-id="07661-174">In this example, the `Default` task is defined as:</span></span>

```powershell
Task Default -depends UnitTests
```

<span data-ttu-id="07661-175">O `Default` tarefa não tem qualquer implementação próprio, mas tem uma dependência `CompileConfigs` tarefas.</span><span class="sxs-lookup"><span data-stu-id="07661-175">The `Default` task has no implementation itself, but has a dependency on the `CompileConfigs` task.</span></span>
<span data-ttu-id="07661-176">A cadeia de dependências de tarefas resultante assegura que todas as tarefas no script de compilação são executadas.</span><span class="sxs-lookup"><span data-stu-id="07661-176">The resulting chain of task dependencies ensures that all tasks in the build script are run.</span></span>

<span data-ttu-id="07661-177">Neste exemplo, o script de psake é invocado por uma chamada para `Invoke-PSake` no `Initiate.ps1` ficheiro (localizado na raiz do repositório Demo_CI):</span><span class="sxs-lookup"><span data-stu-id="07661-177">In this example, the psake script is invoked by a call to `Invoke-PSake` in the `Initiate.ps1` file (located at the root of the Demo_CI repository):</span></span>

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

<span data-ttu-id="07661-178">Quando criamos a definição de compilação para o nosso exemplo no TFS, iremos irá fornecer o nosso ficheiro de script psake como o `fileName` parâmetro para este script.</span><span class="sxs-lookup"><span data-stu-id="07661-178">When we create the build definition for our example in TFS, we will supply our psake script file as the `fileName` parameter for this script.</span></span>

<span data-ttu-id="07661-179">O script de compilação define as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="07661-179">The build script defines the following tasks:</span></span>

#### <a name="generateenvironmentfiles"></a><span data-ttu-id="07661-180">GenerateEnvironmentFiles</span><span class="sxs-lookup"><span data-stu-id="07661-180">GenerateEnvironmentFiles</span></span>

<span data-ttu-id="07661-181">Executa `DevEnv.ps1`, que gera o ficheiro de dados de configuração.</span><span class="sxs-lookup"><span data-stu-id="07661-181">Runs `DevEnv.ps1`, which generates the configuration data file.</span></span>

#### <a name="installmodules"></a><span data-ttu-id="07661-182">InstallModules</span><span class="sxs-lookup"><span data-stu-id="07661-182">InstallModules</span></span>

<span data-ttu-id="07661-183">Instala os módulos necessários na configuração da `DNSServer.ps1`.</span><span class="sxs-lookup"><span data-stu-id="07661-183">Installs the modules required by the configuration `DNSServer.ps1`.</span></span>

#### <a name="scriptanalysis"></a><span data-ttu-id="07661-184">ScriptAnalysis</span><span class="sxs-lookup"><span data-stu-id="07661-184">ScriptAnalysis</span></span>

<span data-ttu-id="07661-185">As chamadas a [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span><span class="sxs-lookup"><span data-stu-id="07661-185">Calls the [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span></span>

#### <a name="unittests"></a><span data-ttu-id="07661-186">UnitTests</span><span class="sxs-lookup"><span data-stu-id="07661-186">UnitTests</span></span>

<span data-ttu-id="07661-187">Executa o [Pester](https://github.com/pester/Pester/wiki) testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="07661-187">Runs the [Pester](https://github.com/pester/Pester/wiki) unit tests.</span></span>

#### <a name="compileconfigs"></a><span data-ttu-id="07661-188">CompileConfigs</span><span class="sxs-lookup"><span data-stu-id="07661-188">CompileConfigs</span></span>

<span data-ttu-id="07661-189">Compila a configuração (`DNSServer.ps1`) para um ficheiro MOF, utilizando os dados de configuração gerados pelo `GenerateEnvironmentFiles` tarefas.</span><span class="sxs-lookup"><span data-stu-id="07661-189">Compiles the configuration (`DNSServer.ps1`) into a MOF file, using the configuration data generated by the `GenerateEnvironmentFiles` task.</span></span>

#### <a name="clean"></a><span data-ttu-id="07661-190">Limpar</span><span class="sxs-lookup"><span data-stu-id="07661-190">Clean</span></span>

<span data-ttu-id="07661-191">Cria as pastas utilizadas para o exemplo e remove quaisquer resultados de teste, ficheiros de dados de configuração e módulos da execução anterior.</span><span class="sxs-lookup"><span data-stu-id="07661-191">Creates the folders used for the example, and removes any test results, configuration data files, and modules from previous runs.</span></span>

### <a name="the-psake-deploy-script"></a><span data-ttu-id="07661-192">O psake implementar script</span><span class="sxs-lookup"><span data-stu-id="07661-192">The psake deploy script</span></span>

<span data-ttu-id="07661-193">O [psake](https://github.com/psake/psake) script de implementação foi definido no `Deploy.ps1` (de raiz do repositório Demo_CI, `./InfraDNS/Deploy.ps1`) define as tarefas que implemente e execute a configuração.</span><span class="sxs-lookup"><span data-stu-id="07661-193">The [psake](https://github.com/psake/psake) deployment script defined in `Deploy.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Deploy.ps1`) defines tasks that deploy and run the configuration.</span></span>

<span data-ttu-id="07661-194">`Deploy.ps1` Define as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="07661-194">`Deploy.ps1` defines the following tasks:</span></span>

#### <a name="deploymodules"></a><span data-ttu-id="07661-195">DeployModules</span><span class="sxs-lookup"><span data-stu-id="07661-195">DeployModules</span></span>

<span data-ttu-id="07661-196">Inicia uma sessão do PowerShell no `TestAgent1` e instala os módulos que contém os recursos de DSC necessários para a configuração.</span><span class="sxs-lookup"><span data-stu-id="07661-196">Starts a PowerShell session on `TestAgent1` and installs the modules containing the DSC resources required for the configuration.</span></span>

#### <a name="deployconfigs"></a><span data-ttu-id="07661-197">DeployConfigs</span><span class="sxs-lookup"><span data-stu-id="07661-197">DeployConfigs</span></span>

<span data-ttu-id="07661-198">As chamadas a [início DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) cmdlet para executar a configuração `TestAgent1`.</span><span class="sxs-lookup"><span data-stu-id="07661-198">Calls the [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) cmdlet to run the configuration on `TestAgent1`.</span></span>

#### <a name="integrationtests"></a><span data-ttu-id="07661-199">IntegrationTests</span><span class="sxs-lookup"><span data-stu-id="07661-199">IntegrationTests</span></span>

<span data-ttu-id="07661-200">Executa o [Pester](https://github.com/pester/Pester/wiki) testes de integração.</span><span class="sxs-lookup"><span data-stu-id="07661-200">Runs the [Pester](https://github.com/pester/Pester/wiki) integration tests.</span></span>

#### <a name="acceptancetests"></a><span data-ttu-id="07661-201">AcceptanceTests</span><span class="sxs-lookup"><span data-stu-id="07661-201">AcceptanceTests</span></span>

<span data-ttu-id="07661-202">Executa o [Pester](https://github.com/pester/Pester/wiki) testes de aceitação.</span><span class="sxs-lookup"><span data-stu-id="07661-202">Runs the [Pester](https://github.com/pester/Pester/wiki) acceptance tests.</span></span>

#### <a name="clean"></a><span data-ttu-id="07661-203">Limpar</span><span class="sxs-lookup"><span data-stu-id="07661-203">Clean</span></span>

<span data-ttu-id="07661-204">Remove quaisquer módulos instalados no executa anterior e assegura que a pasta de resultado do teste existe.</span><span class="sxs-lookup"><span data-stu-id="07661-204">Removes any modules installed in previous runs, and ensures that the test result folder exists.</span></span>

### <a name="test-scripts"></a><span data-ttu-id="07661-205">Testar scripts</span><span class="sxs-lookup"><span data-stu-id="07661-205">Test scripts</span></span>

<span data-ttu-id="07661-206">Testes de aceitação, integração e a unidade são definidos em scripts no `Tests` pasta (de raiz do repositório Demo_CI, `./InfraDNS/Tests`), cada em ficheiros com o nome `DNSServer.tests.ps1` no seus respetivas pastas.</span><span class="sxs-lookup"><span data-stu-id="07661-206">Acceptance, Integration, and Unit tests are defined in scripts in the `Tests` folder (from the root of the Demo_CI repository, `./InfraDNS/Tests`), each in files named `DNSServer.tests.ps1` in their respective folders.</span></span>

<span data-ttu-id="07661-207">O teste de scripts utilize [Pester](https://github.com/pester/Pester/wiki) e [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) sintaxe.</span><span class="sxs-lookup"><span data-stu-id="07661-207">The test scripts use [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="unit-tests"></a><span data-ttu-id="07661-208">Testes de unidade</span><span class="sxs-lookup"><span data-stu-id="07661-208">Unit tests</span></span>

<span data-ttu-id="07661-209">A unidade testes configurações de teste do DSC si próprios para se certificar de que irão fazer as configurações que é esperado quando são executadas.</span><span class="sxs-lookup"><span data-stu-id="07661-209">The unit tests test the DSC configurations themselves to ensure that the configurations will do what is expected when they run.</span></span>
<span data-ttu-id="07661-210">A unidade testar o script utiliza [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="07661-210">The unit test script uses [Pester](https://github.com/pester/Pester/wiki).</span></span>

#### <a name="integration-tests"></a><span data-ttu-id="07661-211">Testes de integração</span><span class="sxs-lookup"><span data-stu-id="07661-211">Integration tests</span></span>

<span data-ttu-id="07661-212">Os testes de integração testar a configuração do sistema para se certificar de que, quando integrado com outros componentes, o sistema está configurado como esperado.</span><span class="sxs-lookup"><span data-stu-id="07661-212">The integration tests test the configuration of the system to ensure that when integrated with other components, the system is configured as expected.</span></span> <span data-ttu-id="07661-213">Estes testes executam no nó de destino depois pois foi configurado com DSC.</span><span class="sxs-lookup"><span data-stu-id="07661-213">These tests run on the target node after it has been configured with DSC.</span></span>
<span data-ttu-id="07661-214">O script de teste de integração utiliza uma combinação de [Pester](https://github.com/pester/Pester/wiki) e [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) sintaxe.</span><span class="sxs-lookup"><span data-stu-id="07661-214">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="acceptance-tests"></a><span data-ttu-id="07661-215">Testes de aceitação</span><span class="sxs-lookup"><span data-stu-id="07661-215">Acceptance tests</span></span>

<span data-ttu-id="07661-216">Testes de aceitação testar o sistema para se certificar de que esta se comporta conforme esperado.</span><span class="sxs-lookup"><span data-stu-id="07661-216">Acceptance tests test the system to ensure that it behaves as expected.</span></span>
<span data-ttu-id="07661-217">Por exemplo, testes para garantir que uma página web devolve as informações corretas quando consultado.</span><span class="sxs-lookup"><span data-stu-id="07661-217">For example, it tests to ensure a web page returns the right information when queried.</span></span>
<span data-ttu-id="07661-218">Estes testes executam remotamente a partir do nó de destino para testar cenários no mundo real.</span><span class="sxs-lookup"><span data-stu-id="07661-218">These tests run remotely from the target node in order to test real world scenarios.</span></span>
<span data-ttu-id="07661-219">O script de teste de integração utiliza uma combinação de [Pester](https://github.com/pester/Pester/wiki) e [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) sintaxe.</span><span class="sxs-lookup"><span data-stu-id="07661-219">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

## <a name="define-the-build"></a><span data-ttu-id="07661-220">Definir a compilação</span><span class="sxs-lookup"><span data-stu-id="07661-220">Define the build</span></span>

<span data-ttu-id="07661-221">Agora que tiver carregado o nosso código para o TFS e consultou o que faz, definamos o nosso compilação.</span><span class="sxs-lookup"><span data-stu-id="07661-221">Now that we've uploaded our code to TFS and looked at what it does, let's define our build.</span></span>

<span data-ttu-id="07661-222">Aqui, iremos abranger apenas os passos de compilação que irá adicionar a compilação.</span><span class="sxs-lookup"><span data-stu-id="07661-222">Here, we'll cover only the build steps that you'll add to the build.</span></span> <span data-ttu-id="07661-223">Para obter instruções sobre como criar uma definição de compilação no TFS, consulte [criar e uma definição de compilação de fila](https://www.visualstudio.com/en-us/docs/build/define/create).</span><span class="sxs-lookup"><span data-stu-id="07661-223">For instructions on how to create a build definition in TFS, see [Create and queue a build definition](https://www.visualstudio.com/en-us/docs/build/define/create).</span></span>

<span data-ttu-id="07661-224">Criar uma nova definição de compilação (selecionar o **vazio** modelo) com o nome "InfraDNS".</span><span class="sxs-lookup"><span data-stu-id="07661-224">Create a new build definition (select the **Empty** template) named "InfraDNS".</span></span>
<span data-ttu-id="07661-225">Adicione que os seguintes passos para a definição de compilação:</span><span class="sxs-lookup"><span data-stu-id="07661-225">Add the following steps to you build definition:</span></span>

- <span data-ttu-id="07661-226">Script do PowerShell</span><span class="sxs-lookup"><span data-stu-id="07661-226">PowerShell Script</span></span>
- <span data-ttu-id="07661-227">Publicar os resultados do teste</span><span class="sxs-lookup"><span data-stu-id="07661-227">Publish Test Results</span></span>
- <span data-ttu-id="07661-228">Copiar ficheiros</span><span class="sxs-lookup"><span data-stu-id="07661-228">Copy Files</span></span>
- <span data-ttu-id="07661-229">Publicar artefactos</span><span class="sxs-lookup"><span data-stu-id="07661-229">Publish Artifact</span></span>

<span data-ttu-id="07661-230">Depois de adicionar estas criar passos, edite as propriedades de cada passo da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="07661-230">After adding these build steps, edit the properties of each step as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="07661-231">Script do PowerShell</span><span class="sxs-lookup"><span data-stu-id="07661-231">PowerShell Script</span></span>

1. <span data-ttu-id="07661-232">Definir o **tipo** propriedade `File Path`.</span><span class="sxs-lookup"><span data-stu-id="07661-232">Set the **Type** property to `File Path`.</span></span>
1. <span data-ttu-id="07661-233">Definir o **caminho do Script** propriedade `initiate.ps1`.</span><span class="sxs-lookup"><span data-stu-id="07661-233">Set the **Script Path** property to `initiate.ps1`.</span></span>
1. <span data-ttu-id="07661-234">Adicionar `-fileName build` para o **argumentos** propriedade.</span><span class="sxs-lookup"><span data-stu-id="07661-234">Add `-fileName build` to the **Arguments** property.</span></span>

<span data-ttu-id="07661-235">Este passo de compilação é executado o `initiate.ps1` ficheiro, que chama o script de compilação psake.</span><span class="sxs-lookup"><span data-stu-id="07661-235">This build step runs the `initiate.ps1` file, which calls the psake build script.</span></span>

### <a name="publish-test-results"></a><span data-ttu-id="07661-236">Publicar os resultados do teste</span><span class="sxs-lookup"><span data-stu-id="07661-236">Publish Test Results</span></span>

1. <span data-ttu-id="07661-237">Definir **testar o formato de resultado** para `NUnit`</span><span class="sxs-lookup"><span data-stu-id="07661-237">Set **Test Result Format** to `NUnit`</span></span>
1. <span data-ttu-id="07661-238">Definir **resultados do teste de ficheiros** para `InfraDNS/Tests/Results/*.xml`</span><span class="sxs-lookup"><span data-stu-id="07661-238">Set **Test Results Files** to `InfraDNS/Tests/Results/*.xml`</span></span>
1. <span data-ttu-id="07661-239">Definir **testar título execução** para `Unit`.</span><span class="sxs-lookup"><span data-stu-id="07661-239">Set **Test Run Title** to `Unit`.</span></span>
1. <span data-ttu-id="07661-240">Certifique-se **opções de controlo** **ativado** e **são sempre executadas** tem ambos os selecionado.</span><span class="sxs-lookup"><span data-stu-id="07661-240">Make sure **Control Options** **Enabled** and **Always run** are both selected.</span></span>

<span data-ttu-id="07661-241">Este passo de compilação executa os testes de unidade no script Pester iremos consultou anteriormente e armazena os resultados no `InfraDNS/Tests/Results/*.xml` pasta.</span><span class="sxs-lookup"><span data-stu-id="07661-241">This build step runs the unit tests in the Pester script we looked at earlier, and stores the results in the `InfraDNS/Tests/Results/*.xml` folder.</span></span>

### <a name="copy-files"></a><span data-ttu-id="07661-242">Copiar ficheiros</span><span class="sxs-lookup"><span data-stu-id="07661-242">Copy Files</span></span>

1. <span data-ttu-id="07661-243">Adicionar cada um dos seguintes linhas ao **conteúdo**:</span><span class="sxs-lookup"><span data-stu-id="07661-243">Add each of the following lines to **Contents**:</span></span>

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. <span data-ttu-id="07661-244">Definir **TargetFolder** para `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="07661-244">Set **TargetFolder** to `$(Build.ArtifactStagingDirectory)\`</span></span>

<span data-ttu-id="07661-245">Este passo copia a compilação e teste de scripts para o diretório de testes para que o possa ser publicada como criar artefactos pelo passo seguinte.</span><span class="sxs-lookup"><span data-stu-id="07661-245">This step copies the build and test scripts to the staging directory so that the can be published as build artifacts by the next step.</span></span>

### <a name="publish-artifact"></a><span data-ttu-id="07661-246">Publicar artefactos</span><span class="sxs-lookup"><span data-stu-id="07661-246">Publish Artifact</span></span>

1. <span data-ttu-id="07661-247">Definir **caminho publicar** para `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="07661-247">Set **Path to Publish** to `$(Build.ArtifactStagingDirectory)\`</span></span>
1. <span data-ttu-id="07661-248">Definir **artefactos nome** para `Deploy`</span><span class="sxs-lookup"><span data-stu-id="07661-248">Set **Artifact Name** to `Deploy`</span></span>
1. <span data-ttu-id="07661-249">Definir **artefactos tipo** para `Server`</span><span class="sxs-lookup"><span data-stu-id="07661-249">Set **Artifact Type** to `Server`</span></span>
1. <span data-ttu-id="07661-250">Selecione `Enabled` no **controlo opções**</span><span class="sxs-lookup"><span data-stu-id="07661-250">Select `Enabled` in **Control Options**</span></span>

## <a name="enable-continuous-integration"></a><span data-ttu-id="07661-251">Ativar a integração contínua</span><span class="sxs-lookup"><span data-stu-id="07661-251">Enable continuous integration</span></span>

<span data-ttu-id="07661-252">Agora iremos definir um acionador que faz com que o projeto para qualquer tempo de compilação uma alteração é verificada para o `ci-cd-example` ramo do repositório de git.</span><span class="sxs-lookup"><span data-stu-id="07661-252">Now we'll set up a trigger that causes the project to build any time a change is checked in to the `ci-cd-example` branch of the git repository.</span></span>

1. <span data-ttu-id="07661-253">No TFS, clique em de **compilar & versão** separador</span><span class="sxs-lookup"><span data-stu-id="07661-253">In TFS, click the **Build & Release** tab</span></span>
1. <span data-ttu-id="07661-254">Selecione o `DNS Infra` Criar definição e clique em **editar**</span><span class="sxs-lookup"><span data-stu-id="07661-254">Select the `DNS Infra` build definition, and click **Edit**</span></span>
1. <span data-ttu-id="07661-255">Clique em de **Acionadores** separador</span><span class="sxs-lookup"><span data-stu-id="07661-255">Click the **Triggers** tab</span></span>
1. <span data-ttu-id="07661-256">Selecione **integração contínua (CI)** e selecione `refs/heads/ci-cd-example` na lista pendente sucursal</span><span class="sxs-lookup"><span data-stu-id="07661-256">Select **Continuous integration (CI)**, and select `refs/heads/ci-cd-example` in the branch drop-down list</span></span>
1. <span data-ttu-id="07661-257">Clique em **guardar** e, em seguida, **OK**</span><span class="sxs-lookup"><span data-stu-id="07661-257">Click **Save** and then **OK**</span></span>

<span data-ttu-id="07661-258">Agora qualquer alteração nos acionadores de repositório de git do TFS uma compilação automatizada.</span><span class="sxs-lookup"><span data-stu-id="07661-258">Now any change in the TFS git repository triggers an automated build.</span></span>

## <a name="create-the-release-definition"></a><span data-ttu-id="07661-259">Criar a definição da versão</span><span class="sxs-lookup"><span data-stu-id="07661-259">Create the release definition</span></span>

<span data-ttu-id="07661-260">Vamos criar uma definição de versão, para que o projeto é implementado no ambiente de desenvolvimento com cada dar entrada no código.</span><span class="sxs-lookup"><span data-stu-id="07661-260">Let's create a release definition so that the project is deployed to the development environment with every code check-in.</span></span>

<span data-ttu-id="07661-261">Para tal, adicione uma nova definição de versão associada a `InfraDNS` Criar definição que criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="07661-261">To do this, add a new release definition associated with the `InfraDNS` build definition you created previously.</span></span>
<span data-ttu-id="07661-262">Lembre-se de que selecione **a implementação contínua** para que uma nova versão será acionada sempre que uma nova compilação for concluída.</span><span class="sxs-lookup"><span data-stu-id="07661-262">Be sure to select **Continuous deployment** so that a new release will be triggered any time a new build is completed.</span></span>
<span data-ttu-id="07661-263">([Como: trabalhar com definições de versão](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) e configurá-lo da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="07661-263">([How to: Work with release definitions](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) and configure it as follows:</span></span>

<span data-ttu-id="07661-264">Adicione os seguintes passos para a definição da versão:</span><span class="sxs-lookup"><span data-stu-id="07661-264">Add the following steps to the release definition:</span></span>

- <span data-ttu-id="07661-265">Script do PowerShell</span><span class="sxs-lookup"><span data-stu-id="07661-265">PowerShell Script</span></span>
- <span data-ttu-id="07661-266">Publicar os resultados do teste</span><span class="sxs-lookup"><span data-stu-id="07661-266">Publish Test Results</span></span>
- <span data-ttu-id="07661-267">Publicar os resultados do teste</span><span class="sxs-lookup"><span data-stu-id="07661-267">Publish Test Results</span></span>

<span data-ttu-id="07661-268">Edite os passos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="07661-268">Edit the steps as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="07661-269">Script do PowerShell</span><span class="sxs-lookup"><span data-stu-id="07661-269">PowerShell Script</span></span>

1. <span data-ttu-id="07661-270">Definir o **caminho do Script** campo para `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span><span class="sxs-lookup"><span data-stu-id="07661-270">Set the **Script Path** field to `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span></span>
1. <span data-ttu-id="07661-271">Definir o **argumentos** campo para `-fileName Deploy`</span><span class="sxs-lookup"><span data-stu-id="07661-271">Set the **Arguments** field to `-fileName Deploy`</span></span>

### <a name="first-publish-test-results"></a><span data-ttu-id="07661-272">Publicar primeiro os resultados do teste</span><span class="sxs-lookup"><span data-stu-id="07661-272">First Publish Test Results</span></span>

1. <span data-ttu-id="07661-273">Selecione `NUnit` para o **formato de resultado do teste** campo</span><span class="sxs-lookup"><span data-stu-id="07661-273">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="07661-274">Definir o **ficheiros de resultado do teste** campo para `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span><span class="sxs-lookup"><span data-stu-id="07661-274">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span></span>
1. <span data-ttu-id="07661-275">Definir o **testar título execução** para `Integration`</span><span class="sxs-lookup"><span data-stu-id="07661-275">Set the **Test Run Title** to `Integration`</span></span>
1. <span data-ttu-id="07661-276">Em **opções de controlo**, verifique **são sempre executadas**</span><span class="sxs-lookup"><span data-stu-id="07661-276">Under **Control Options**, check **Always run**</span></span>

### <a name="second-publish-test-results"></a><span data-ttu-id="07661-277">Segundo publicar os resultados do teste</span><span class="sxs-lookup"><span data-stu-id="07661-277">Second Publish Test Results</span></span>

1. <span data-ttu-id="07661-278">Selecione `NUnit` para o **formato de resultado do teste** campo</span><span class="sxs-lookup"><span data-stu-id="07661-278">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="07661-279">Definir o **ficheiros de resultado do teste** campo para `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span><span class="sxs-lookup"><span data-stu-id="07661-279">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span></span>
1. <span data-ttu-id="07661-280">Definir o **testar título execução** para `Acceptance`</span><span class="sxs-lookup"><span data-stu-id="07661-280">Set the **Test Run Title** to `Acceptance`</span></span>
1. <span data-ttu-id="07661-281">Em **opções de controlo**, verifique **são sempre executadas**</span><span class="sxs-lookup"><span data-stu-id="07661-281">Under **Control Options**, check **Always run**</span></span>

## <a name="verify-your-results"></a><span data-ttu-id="07661-282">Verificar os resultados</span><span class="sxs-lookup"><span data-stu-id="07661-282">Verify your results</span></span>

<span data-ttu-id="07661-283">Agora, sempre que enviar a alterações `ci-cd-example` ramo para o TFS, uma nova compilação será iniciado.</span><span class="sxs-lookup"><span data-stu-id="07661-283">Now, any time you push changes in the `ci-cd-example` branch to TFS, a new build will start.</span></span>
<span data-ttu-id="07661-284">Se a compilação for concluída com êxito, é acionada uma nova implementação.</span><span class="sxs-lookup"><span data-stu-id="07661-284">If the build completes successfully, a new deployment is triggered.</span></span>

<span data-ttu-id="07661-285">Pode verificar o resultado da implementação ao abrir um browser no computador cliente e navegar até `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="07661-285">You can check the result of the deployment by opening a browser on the client machine and navigating to `www.contoso.com`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="07661-286">Próximos passos</span><span class="sxs-lookup"><span data-stu-id="07661-286">Next steps</span></span>

<span data-ttu-id="07661-287">Este exemplo configura o servidor DNS `TestAgent1` para que o URL `www.contoso.com` é resolvido para `TestAgent2`, mas não implementa efetivamente um Web site.</span><span class="sxs-lookup"><span data-stu-id="07661-287">This example configures the DNS server `TestAgent1` so that the URL `www.contoso.com` resolves to `TestAgent2`, but it does not actually deploy a website.</span></span>
<span data-ttu-id="07661-288">A estrutura para fazê-lo é fornecida no repositório sob o `WebApp` pasta.</span><span class="sxs-lookup"><span data-stu-id="07661-288">The skeleton for doing so is provided in the repo under the `WebApp` folder.</span></span>
<span data-ttu-id="07661-289">Pode utilizar os stubs fornecidos para criar psake scripts, Pester testes e configurações de DSC para implementar a sua própria Web site.</span><span class="sxs-lookup"><span data-stu-id="07661-289">You can use the stubs provided to create psake scripts, Pester tests, and DSC configurations to deploy your own website.</span></span>