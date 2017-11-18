---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Configurações de DSC"
ms.openlocfilehash: b0868a276dbf5cdb566ce1f35a96b3372cf49be1
ms.sourcegitcommit: 60c6f9d8cf316e6d5b285854e6e5641ac7648f3f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/17/2017
---
# <a name="dsc-configurations"></a><span data-ttu-id="eea29-103">Configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="eea29-103">DSC Configurations</span></span>

><span data-ttu-id="eea29-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="eea29-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="eea29-105">Configurações de DSC são scripts do PowerShell que definem um tipo especial de função.</span><span class="sxs-lookup"><span data-stu-id="eea29-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span> <span data-ttu-id="eea29-106">Para definir uma configuração, pode utilizar a palavra-chave do PowerShell **configuração**.</span><span class="sxs-lookup"><span data-stu-id="eea29-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
} 

```

<span data-ttu-id="eea29-107">Guarde o script como um ficheiro. ps1.</span><span class="sxs-lookup"><span data-stu-id="eea29-107">Save the script as a .ps1 file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="eea29-108">Sintaxe de configuração</span><span class="sxs-lookup"><span data-stu-id="eea29-108">Configuration syntax</span></span>

<span data-ttu-id="eea29-109">Um script de configuração consiste dos seguintes partes:</span><span class="sxs-lookup"><span data-stu-id="eea29-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="eea29-110">O **configuração** bloco.</span><span class="sxs-lookup"><span data-stu-id="eea29-110">The **Configuration** block.</span></span> <span data-ttu-id="eea29-111">Este é o bloco de scripts mais exterior.</span><span class="sxs-lookup"><span data-stu-id="eea29-111">This is the outermost script block.</span></span> <span data-ttu-id="eea29-112">Defini-lo utilizando o **configuração** palavra-chave e fornecer um nome.</span><span class="sxs-lookup"><span data-stu-id="eea29-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="eea29-113">Neste caso, o nome da configuração é "MyDscConfiguration".</span><span class="sxs-lookup"><span data-stu-id="eea29-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="eea29-114">Um ou mais **nó** blocos.</span><span class="sxs-lookup"><span data-stu-id="eea29-114">One or more **Node** blocks.</span></span> <span data-ttu-id="eea29-115">Estes definem os nós (computadores ou VMs) que está a configurar.</span><span class="sxs-lookup"><span data-stu-id="eea29-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="eea29-116">Na configuração acima, há um **nó** bloco destina-se um computador com o nome "PC1 de teste".</span><span class="sxs-lookup"><span data-stu-id="eea29-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span>
- <span data-ttu-id="eea29-117">Um ou mais bloqueios de recursos.</span><span class="sxs-lookup"><span data-stu-id="eea29-117">One or more resource blocks.</span></span> <span data-ttu-id="eea29-118">Este é onde a configuração define as propriedades de recursos que está a configurar.</span><span class="sxs-lookup"><span data-stu-id="eea29-118">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="eea29-119">Neste caso, existem dois blocos de recursos, cada um dos quais chamar o recurso "WindowsFeature".</span><span class="sxs-lookup"><span data-stu-id="eea29-119">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="eea29-120">Dentro de um **configuração** bloco, que pode fazer tudo o que lhe foi normalmente de uma função do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eea29-120">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="eea29-121">Por exemplo, no exemplo anterior, se não pretender rígido code o nome do computador de destino na configuração, pode adicionar um parâmetro para o nome de nó:</span><span class="sxs-lookup"><span data-stu-id="eea29-121">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}

```

<span data-ttu-id="eea29-122">Neste exemplo, especifique o nome do nó transferindo-a como o **ComputerName** parâmetro ao compilar o configuraton.</span><span class="sxs-lookup"><span data-stu-id="eea29-122">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuraton.</span></span> <span data-ttu-id="eea29-123">A nome assume a predefinição "localhost".</span><span class="sxs-lookup"><span data-stu-id="eea29-123">The name defaults to "localhost".</span></span>

## <a name="compiling-the-configuration"></a><span data-ttu-id="eea29-124">Compilar a configuração</span><span class="sxs-lookup"><span data-stu-id="eea29-124">Compiling the configuration</span></span>

<span data-ttu-id="eea29-125">Antes de pode enact uma configuração, tem de compilá-la para um documento MOF.</span><span class="sxs-lookup"><span data-stu-id="eea29-125">Before you can enact a configuration, you have to compile it into a MOF document.</span></span> <span data-ttu-id="eea29-126">Fazê-lo ao chamar a configuração como faria com uma função do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eea29-126">You do this by calling the configuration like you would a PowerShell function.</span></span>  
<span data-ttu-id="eea29-127">A última linha do exemplo que contém apenas o nome da configuração, chama a configuração.</span><span class="sxs-lookup"><span data-stu-id="eea29-127">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

><span data-ttu-id="eea29-128">**Nota:** para chamar uma configuração, a função tem de ser no âmbito global (tal como acontece com qualquer outra função do PowerShell).</span><span class="sxs-lookup"><span data-stu-id="eea29-128">**Note:** To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span> 
><span data-ttu-id="eea29-129">Pode efetuar esta acontecer optar por "dot-sourcing" o script, ou ao executar o script de configuração ao utilizar F5 ou clicando no **executar Script** botão no ISE do.</span><span class="sxs-lookup"><span data-stu-id="eea29-129">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span> 
><span data-ttu-id="eea29-130">A origem de ponto de script, execute o comando `. .\myConfig.ps1` onde `myConfig.ps1` é o nome do ficheiro de script que contém a configuração.</span><span class="sxs-lookup"><span data-stu-id="eea29-130">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="eea29-131">Quando chamar a configuração,-lo:</span><span class="sxs-lookup"><span data-stu-id="eea29-131">When you call the configuration, it:</span></span>

- <span data-ttu-id="eea29-132">Resolve todas as variáveis</span><span class="sxs-lookup"><span data-stu-id="eea29-132">Resolves all variables</span></span> 
- <span data-ttu-id="eea29-133">Cria uma pasta no diretório atual com o mesmo nome que a configuração.</span><span class="sxs-lookup"><span data-stu-id="eea29-133">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="eea29-134">Cria um ficheiro denominado _NodeName_. MOF no novo diretório, onde _NodeName_ é o nome do nó de destino da configuração.</span><span class="sxs-lookup"><span data-stu-id="eea29-134">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span> 
    <span data-ttu-id="eea29-135">Se existir mais do que um de nós, será criado um ficheiro MOF para cada nó.</span><span class="sxs-lookup"><span data-stu-id="eea29-135">If there are more than one nodes, a MOF file will be created for each node.</span></span>

><span data-ttu-id="eea29-136">**Tenha em atenção**: ficheiro MOF o contém todas as informações de configuração para o nó de destino.</span><span class="sxs-lookup"><span data-stu-id="eea29-136">**Note**: The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="eea29-137">Por este motivo, é importante manter segura.</span><span class="sxs-lookup"><span data-stu-id="eea29-137">Because of this, it’s important to keep it secure.</span></span> 
><span data-ttu-id="eea29-138">Para obter mais informações, consulte [proteger o ficheiro MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="eea29-138">For more information, see [Securing the MOF file](secureMOF.md).</span></span>

<span data-ttu-id="eea29-139">Compilar a configuração do primeiro acima resultados na estrutura da pasta seguintes:</span><span class="sxs-lookup"><span data-stu-id="eea29-139">Compiling the first configuration above results in the following folder structure:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```  

<span data-ttu-id="eea29-140">Se a configuração utiliza um parâmetro, como no exemplo segundo, que tem de ser fornecido no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="eea29-140">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="eea29-141">Segue-se que seria aspeto:</span><span class="sxs-lookup"><span data-stu-id="eea29-141">Here's how that would look:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```      

## <a name="using-dependson"></a><span data-ttu-id="eea29-142">Utilizar DependsOn</span><span class="sxs-lookup"><span data-stu-id="eea29-142">Using DependsOn</span></span>

<span data-ttu-id="eea29-143">É uma palavra-chave de DSC útil **DependsOn**.</span><span class="sxs-lookup"><span data-stu-id="eea29-143">A useful DSC keyword is **DependsOn**.</span></span> <span data-ttu-id="eea29-144">Normalmente, (embora, não necessariamente sempre), DSC aplica-se os recursos na ordem em que aparecem dentro da configuração.</span><span class="sxs-lookup"><span data-stu-id="eea29-144">Typically (though not necessarily always), DSC applies the resources in the order that they appear within the configuration.</span></span> <span data-ttu-id="eea29-145">No entanto, **DependsOn** Especifica qual a que recursos dependem de outros recursos e o MMC assegura que são aplicadas pela ordem correta, independentemente da ordem pela qual o recurso instâncias são definidas.</span><span class="sxs-lookup"><span data-stu-id="eea29-145">However, **DependsOn** specifies which resources depend on other resources, and the LCM ensures that they are applied in the correct order, regardless of the order in which resource instances are defined.</span></span> <span data-ttu-id="eea29-146">Por exemplo, de uma configuração poderá especificar que uma instância do **utilizador** recursos dependem da existência de um **grupo** instância:</span><span class="sxs-lookup"><span data-stu-id="eea29-146">For example, a configuration might specify that an instance of the **User** resource depends on the existence of a **Group** instance:</span></span>

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}

```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="eea29-147">Utilização de novos recursos na sua configuração</span><span class="sxs-lookup"><span data-stu-id="eea29-147">Using new resources in Your configuration</span></span>

<span data-ttu-id="eea29-148">Se tiver executado os exemplos anteriores, poderá ter reparado que foram avisado que estava a utilizar um recurso sem explicitamente importá-lo.</span><span class="sxs-lookup"><span data-stu-id="eea29-148">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="eea29-149">Hoje em dia, DSC é fornecido com 12 recursos como parte do módulo PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="eea29-149">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span> <span data-ttu-id="eea29-150">Outros recursos em módulos externos tem de ser colocados numa `$env:PSModulePath` para poder ser reconhecido pelo MMC.</span><span class="sxs-lookup"><span data-stu-id="eea29-150">Other resources in external modules must be placed in `$env:PSModulePath` in order to be recognized by the LCM.</span></span> <span data-ttu-id="eea29-151">Um novo cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), pode ser utilizado para determinar os recursos que estão instalados no sistema e disponível para utilização pelo MMC.</span><span class="sxs-lookup"><span data-stu-id="eea29-151">A new cmdlet, [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span> <span data-ttu-id="eea29-152">Depois destes módulos foram colocados no `$env:PSModulePath` e corretamente são reconhecidos pelo [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), têm de ser carregado dentro da sua configuração.</span><span class="sxs-lookup"><span data-stu-id="eea29-152">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), they still need to be loaded within your configuration.</span></span> 
<span data-ttu-id="eea29-153">**Importar DscResource** é uma palavra-chave dinâmica que só pode ser reconhecida dentro de um **configuração** blocos (ou seja, não é um cmdlet).</span><span class="sxs-lookup"><span data-stu-id="eea29-153">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block (i.e. it is not a cmdlet).</span></span> 
<span data-ttu-id="eea29-154">**Importar DscResource** suporta dois parâmetros:</span><span class="sxs-lookup"><span data-stu-id="eea29-154">**Import-DscResource** supports two parameters:</span></span>
- <span data-ttu-id="eea29-155">**ModuleName** é a forma recomendada de utilização **importação DscResource**.</span><span class="sxs-lookup"><span data-stu-id="eea29-155">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="eea29-156">Aceita o nome do módulo que contém os recursos a serem importados (bem como uma matriz de cadeia de nomes de módulo).</span><span class="sxs-lookup"><span data-stu-id="eea29-156">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span> 
- <span data-ttu-id="eea29-157">**Nome** é o nome do recurso para importar.</span><span class="sxs-lookup"><span data-stu-id="eea29-157">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="eea29-158">Não é o nome amigável devolvido como "Name" por [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), mas o nome de classe utilizado quando definir o esquema de recursos (devolvido como **ResourceType** por [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)).</span><span class="sxs-lookup"><span data-stu-id="eea29-158">This is not the friendly name returned as "Name" by [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)).</span></span> 

## <a name="see-also"></a><span data-ttu-id="eea29-159">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="eea29-159">See Also</span></span>
* [<span data-ttu-id="eea29-160">Descrição geral da configuração do estado pretendido do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eea29-160">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="eea29-161">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="eea29-161">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="eea29-162">Configurar o Gestor de configuração Local</span><span class="sxs-lookup"><span data-stu-id="eea29-162">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

