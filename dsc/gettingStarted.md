---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Configuração do estado pretendido de introdução do PowerShell
ms.openlocfilehash: a449382c979e680ea311c887c86cb675ba6162b7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="getting-started-with-powershell-desired-state-configuration"></a><span data-ttu-id="8a2dd-103">Configuração do estado pretendido de introdução do PowerShell</span><span class="sxs-lookup"><span data-stu-id="8a2dd-103">Getting Started with PowerShell Desired State Configuration</span></span> #

<span data-ttu-id="8a2dd-104">Este guia descreve como começar a criar documentos de configuração de estado pretendido do PowerShell e aplicá-las nos computadores.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-104">This guide describes how to begin creating PowerShell Desired State Configuration documents and apply them to machines.</span></span> <span data-ttu-id="8a2dd-105">Pressupõe familiaridade básica com cmdlets do PowerShell, módulos e funções.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-105">It assumes basic familiarity with PowerShell cmdlets, modules, and functions.</span></span>


## <a name="create-a-configuration"></a><span data-ttu-id="8a2dd-106">Criar uma configuração</span><span class="sxs-lookup"><span data-stu-id="8a2dd-106">Create a Configuration</span></span> ##

<span data-ttu-id="8a2dd-107">[**Configurações** ](https://msdn.microsoft.com/powershell/dsc/configurations) são documentos que descrevem um ambiente.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-107">[**Configurations**](https://msdn.microsoft.com/powershell/dsc/configurations) are documents that describe an environment.</span></span> <span data-ttu-id="8a2dd-108">Consistem em ambientes "**nós**", que são frequentemente máquinas virtuais ou físicas.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-108">Environments consist of "**nodes**", which are commonly virtual or physical machines.</span></span>

<span data-ttu-id="8a2dd-109">Configurações podem ter uma variedade de formulários.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-109">Configurations can come in a variety of forms.</span></span> <span data-ttu-id="8a2dd-110">É a forma mais fácil de criar uma nova configuração para criar um ficheiro de (script do PowerShell). ps1.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-110">The easiest way to create a new configuration is to create a .ps1 (PowerShell script) file.</span></span> <span data-ttu-id="8a2dd-111">Para tal, abra o editor de eleição.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-111">To do this, open your editor of choice.</span></span> <span data-ttu-id="8a2dd-112">ISE do PowerShell é uma boa opção, uma vez que compreende o DSC nativamente.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-112">The PowerShell ISE is a good choice, since it understands DSC natively.</span></span> <span data-ttu-id="8a2dd-113">Guarde o seguinte como um PS1:</span><span class="sxs-lookup"><span data-stu-id="8a2dd-113">Save the following as a PS1:</span></span>

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }

    }

}
```
## <a name="parts-of-a-configuration"></a><span data-ttu-id="8a2dd-114">Partes de uma configuração</span><span class="sxs-lookup"><span data-stu-id="8a2dd-114">Parts of a Configuration</span></span> ##
<span data-ttu-id="8a2dd-115">**Configuração** é uma palavra-chave que tenha sido adicionada ao PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-115">**Configuration** is a keyword that has been added to PowerShell 4.0.</span></span> <span data-ttu-id="8a2dd-116">-Representa um tipo especial de função de PowerShell utilizados pela configuração de estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-116">It signifies a special kind of PowerShell function used by Desired State Configuration.</span></span> <span data-ttu-id="8a2dd-117">Neste exemplo, a função é denominada myFirstConfiguration.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-117">In this example, the function is named myFirstConfiguration.</span></span>

<span data-ttu-id="8a2dd-118">A linha seguinte é uma instrução de importação, semelhante a importar um módulo.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-118">The next line is an import statement, similar to importing a module.</span></span> <span data-ttu-id="8a2dd-119">Irá ser abordada mais tarde.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-119">It will be discussed later on.</span></span>

<span data-ttu-id="8a2dd-120">"Nó" define o nome da máquina que esta configuração irá atuar.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-120">"Node" defines the machine name this configuration will act on.</span></span> <span data-ttu-id="8a2dd-121">Embora esta configuração é editada localmente, configurações podem aceder a nós remotos e configurá-los.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-121">Although this configuration is edited locally, configurations can reach out to remote nodes and configure them.</span></span>

<span data-ttu-id="8a2dd-122">Nós podem ser nomes de computador ou endereços IP.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-122">Nodes can be machine names or IP addresses.</span></span> <span data-ttu-id="8a2dd-123">Pode ter vários nós de um documento de configuração única.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-123">You can have multiple nodes in a single configuration document.</span></span> <span data-ttu-id="8a2dd-124">Utilizar [dados de configuração](https://msdn.microsoft.com/powershell/dsc/configdata), também pode ter a mesma configuração que se aplicam a vários nós.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-124">Using [configuration data](https://msdn.microsoft.com/powershell/dsc/configdata), you can also have the same configuration apply to multiple nodes.</span></span> <span data-ttu-id="8a2dd-125">Neste caso, o nó é "localhost" - significa que o computador local.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-125">In this case, the node is "localhost" - which means the local computer.</span></span>

<span data-ttu-id="8a2dd-126">O item seguinte é um [ **recursos**](https://msdn.microsoft.com/powershell/dsc/resources).</span><span class="sxs-lookup"><span data-stu-id="8a2dd-126">The next item is a [**resource**](https://msdn.microsoft.com/powershell/dsc/resources).</span></span> <span data-ttu-id="8a2dd-127">Os recursos são os blocos modulares de configurações.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-127">Resources are building blocks of configurations.</span></span> <span data-ttu-id="8a2dd-128">Cada recurso é um módulo que define a lógica de implementação de um único aspeto de uma máquina.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-128">Each resource is a module that defines the implementation logic of a single aspect of a machine.</span></span> <span data-ttu-id="8a2dd-129">Pode ver todos os recursos no seu computador, executando **Get-DscResource** no PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-129">You can view every resource on your machine by running **Get-DscResource** in PowerShell.</span></span> <span data-ttu-id="8a2dd-130">Recursos deve estar presentes no computador local e importado antes de poderem ser utilizados numa configuração com **importação DscResource** que é a segunda linha desta configuração.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-130">Resources must be present on the local machine and imported before they can be used in a configuration with **Import-DscResource** which is on the second line of this configuration.</span></span>

<span data-ttu-id="8a2dd-131">**Enacting uma configuração**</span><span class="sxs-lookup"><span data-stu-id="8a2dd-131">**Enacting a Configuration**</span></span>

<span data-ttu-id="8a2dd-132">Se o script acima é guardado e executado, não será produzida nenhuma saída.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-132">If the script above is saved and run, no output will be produced.</span></span> <span data-ttu-id="8a2dd-133">Esta é uma vez que uma configuração é apenas uma função e o script acima tem a função definida pelo mas ainda não foram executá-la.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-133">This is because a configuration is just a function, and the script above has defined the function but not yet run it.</span></span> <span data-ttu-id="8a2dd-134">Depois da função estiver definida, tem de ser invocado:</span><span class="sxs-lookup"><span data-stu-id="8a2dd-134">After the function is defined, it must be invoked:</span></span>
```powershell
myFirstConfiguration
```

<span data-ttu-id="8a2dd-135">Quando executada, as funções de configuração valide a configuração é válido.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-135">When executed, configuration functions validate the configuration is valid.</span></span> <span data-ttu-id="8a2dd-136">Não deve ter não existem erros de sintaxe, recursos devem ter todos os parâmetros obrigatórios definidos e todos os recursos devem ser importados antes da execução.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-136">It should have no syntax errors, resources should have all mandatory parameters defined, and all resources should be imported before execution.</span></span>

<span data-ttu-id="8a2dd-137">Depois da configuração é executada, cria uma pasta com o nome de configuração que contém um **. Ficheiro MOF** para cada nó na configuração.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-137">Once the configuration is executed, it creates a folder with the name of the configuration containing a **.MOF file** for every node in the configuration.</span></span> <span data-ttu-id="8a2dd-138">O. Ficheiro MOF é um formato de gestão baseada em normas que é utilizado pelo PowerShell DSC para comunicar através da rede.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-138">The .MOF file is a standards-based management format which is used by PowerShell DSC to communicate over the network.</span></span>

<span data-ttu-id="8a2dd-139">Para enact a configuração:</span><span class="sxs-lookup"><span data-stu-id="8a2dd-139">To enact the configuration:</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
<span data-ttu-id="8a2dd-140">Esta ação cria um trabalho do PowerShell que acede a nós na configuração e configura-as.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-140">This creates a PowerShell job that reaches out to the nodes in the configuration and configures them.</span></span> <span data-ttu-id="8a2dd-141">Para ver o resultado da tarefa, utilize o-espera.</span><span class="sxs-lookup"><span data-stu-id="8a2dd-141">To see the output of the job, use -Wait.</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```