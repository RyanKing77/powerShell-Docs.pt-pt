---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Configurações de DSC
ms.openlocfilehash: 6af27f442de3080facd65892c713c989d0e388c5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080180"
---
# <a name="dsc-configurations"></a><span data-ttu-id="d8e14-103">Configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="d8e14-103">DSC Configurations</span></span>

> <span data-ttu-id="d8e14-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d8e14-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="d8e14-105">As configurações de DSC são scripts do PowerShell que definem um tipo especial de função.</span><span class="sxs-lookup"><span data-stu-id="d8e14-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="d8e14-106">Para definir uma configuração, use a palavra-chave do PowerShell **configuração**.</span><span class="sxs-lookup"><span data-stu-id="d8e14-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

<span data-ttu-id="d8e14-107">Guarde o script como um `.ps1` ficheiro.</span><span class="sxs-lookup"><span data-stu-id="d8e14-107">Save the script as a `.ps1` file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="d8e14-108">Sintaxe de configuração</span><span class="sxs-lookup"><span data-stu-id="d8e14-108">Configuration syntax</span></span>

<span data-ttu-id="d8e14-109">Um script de configuração consiste nas seguintes partes:</span><span class="sxs-lookup"><span data-stu-id="d8e14-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="d8e14-110">O **configuração** bloco.</span><span class="sxs-lookup"><span data-stu-id="d8e14-110">The **Configuration** block.</span></span> <span data-ttu-id="d8e14-111">Este é o bloco de scripts mais externo.</span><span class="sxs-lookup"><span data-stu-id="d8e14-111">This is the outermost script block.</span></span> <span data-ttu-id="d8e14-112">Defini-lo utilizando o **configuração** palavra-chave e fornecer um nome.</span><span class="sxs-lookup"><span data-stu-id="d8e14-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="d8e14-113">Neste caso, o nome da configuração é "MyDscConfiguration".</span><span class="sxs-lookup"><span data-stu-id="d8e14-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="d8e14-114">Um ou mais **nó** blocos.</span><span class="sxs-lookup"><span data-stu-id="d8e14-114">One or more **Node** blocks.</span></span> <span data-ttu-id="d8e14-115">Elas definem os nós (VMs ou computadores) que está a configurar.</span><span class="sxs-lookup"><span data-stu-id="d8e14-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="d8e14-116">Na configuração acima, há um **nó** bloco que se destina a um computador com o nome "TEST-PC1".</span><span class="sxs-lookup"><span data-stu-id="d8e14-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span> <span data-ttu-id="d8e14-117">O bloco de nó pode aceitar vários nomes de computador.</span><span class="sxs-lookup"><span data-stu-id="d8e14-117">The Node block can accept multiple computer names.</span></span>
- <span data-ttu-id="d8e14-118">Um ou mais blocos de recursos.</span><span class="sxs-lookup"><span data-stu-id="d8e14-118">One or more resource blocks.</span></span> <span data-ttu-id="d8e14-119">Trata-se em que a configuração define as propriedades dos recursos de que está a configurar.</span><span class="sxs-lookup"><span data-stu-id="d8e14-119">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="d8e14-120">Neste caso, existem dois blocos de recursos, cada um dos quais chamar o recurso de "WindowsFeature".</span><span class="sxs-lookup"><span data-stu-id="d8e14-120">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="d8e14-121">Dentro de um **configuração** bloco, pode fazer tudo o que poderia normalmente numa função do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d8e14-121">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="d8e14-122">Por exemplo, no exemplo anterior, se não quisesse duro codificar o nome do computador de destino na configuração, poderia adicionar um parâmetro para o nome do nó:</span><span class="sxs-lookup"><span data-stu-id="d8e14-122">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

<span data-ttu-id="d8e14-123">Neste exemplo, especificar o nome do nó, passando-o como o **ComputerName** parâmetro quando compilar a configuração.</span><span class="sxs-lookup"><span data-stu-id="d8e14-123">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="d8e14-124">O nome padrão é "localhost".</span><span class="sxs-lookup"><span data-stu-id="d8e14-124">The name defaults to "localhost".</span></span>

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

<span data-ttu-id="d8e14-125">O **nó** bloco também pode aceitar vários nomes de computador.</span><span class="sxs-lookup"><span data-stu-id="d8e14-125">The **Node** block can also accept multiple computer names.</span></span> <span data-ttu-id="d8e14-126">No exemplo acima, pode utilizar o `-ComputerName` parâmetro ou pass um separados por vírgulas lista de computadores diretamente para o **nó** bloco.</span><span class="sxs-lookup"><span data-stu-id="d8e14-126">In the above example, you can either use the `-ComputerName` parameter, or pass a comma-separated list of computers directly to the **Node** block.</span></span>

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

<span data-ttu-id="d8e14-127">Quando especificar uma lista de computadores para o **nó** bloco, de dentro de uma configuração, precisa usar notação de matriz.</span><span class="sxs-lookup"><span data-stu-id="d8e14-127">When specifying a list of computers to the **Node** block, from within a Configuration, you need to use array-notation.</span></span>

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a><span data-ttu-id="d8e14-128">Compilar a configuração</span><span class="sxs-lookup"><span data-stu-id="d8e14-128">Compiling the configuration</span></span>

<span data-ttu-id="d8e14-129">Antes de pode aplicá uma configuração, deve compilá-lo num documento do MOF.</span><span class="sxs-lookup"><span data-stu-id="d8e14-129">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="d8e14-130">Pode fazê-lo ao chamar a configuração, como chamaria uma função do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d8e14-130">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="d8e14-131">A última linha do exemplo que contém apenas o nome da configuração, chama a configuração.</span><span class="sxs-lookup"><span data-stu-id="d8e14-131">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="d8e14-132">Para chamar uma configuração, a função deve estar no âmbito global (tal como acontece com qualquer outra função do PowerShell).</span><span class="sxs-lookup"><span data-stu-id="d8e14-132">To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
> <span data-ttu-id="d8e14-133">Pode fazer esta acontecer tanto por "dot sourcing" o script, ou ao executar o script de configuração usando F5 ou clicar no **executar Script** botão no ISE.</span><span class="sxs-lookup"><span data-stu-id="d8e14-133">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
> <span data-ttu-id="d8e14-134">A origem de ponto o script, execute o comando `. .\myConfig.ps1` onde `myConfig.ps1` é o nome do ficheiro de script que contém a configuração.</span><span class="sxs-lookup"><span data-stu-id="d8e14-134">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="d8e14-135">Quando chama a configuração, ele:</span><span class="sxs-lookup"><span data-stu-id="d8e14-135">When you call the configuration, it:</span></span>

- <span data-ttu-id="d8e14-136">Resolve todas as variáveis</span><span class="sxs-lookup"><span data-stu-id="d8e14-136">Resolves all variables</span></span>
- <span data-ttu-id="d8e14-137">Cria uma pasta no diretório atual com o mesmo nome que a configuração.</span><span class="sxs-lookup"><span data-stu-id="d8e14-137">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="d8e14-138">Cria um ficheiro denominado _NodeName_arquivos. MOF no novo diretório, onde _NodeName_ é o nome do nó de destino da configuração.</span><span class="sxs-lookup"><span data-stu-id="d8e14-138">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
  <span data-ttu-id="d8e14-139">Se houver mais de um nó, será criado um ficheiro MOF para cada nó.</span><span class="sxs-lookup"><span data-stu-id="d8e14-139">If there is more than one node, a MOF file will be created for each node.</span></span>

> [!NOTE]
> <span data-ttu-id="d8e14-140">O ficheiro MOF contém todas as informações de configuração para o nó de destino.</span><span class="sxs-lookup"><span data-stu-id="d8e14-140">The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="d8e14-141">Por este motivo, é importante para mantê-lo seguro.</span><span class="sxs-lookup"><span data-stu-id="d8e14-141">Because of this, it’s important to keep it secure.</span></span>
> <span data-ttu-id="d8e14-142">Para obter mais informações, consulte [proteger o ficheiro MOF](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="d8e14-142">For more information, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>

<span data-ttu-id="d8e14-143">Compilar a configuração do primeiro acima resultados na estrutura da pasta seguinte:</span><span class="sxs-lookup"><span data-stu-id="d8e14-143">Compiling the first configuration above results in the following folder structure:</span></span>

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

<span data-ttu-id="d8e14-144">Se a configuração assume um parâmetro, como no segundo exemplo, que deve ser fornecida no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="d8e14-144">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="d8e14-145">Aqui está como que teria o aspeto:</span><span class="sxs-lookup"><span data-stu-id="d8e14-145">Here's how that would look:</span></span>

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

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="d8e14-146">Utilizar os novos recursos na sua configuração</span><span class="sxs-lookup"><span data-stu-id="d8e14-146">Using new resources in Your configuration</span></span>

<span data-ttu-id="d8e14-147">Se tiver executado os exemplos anteriores, deve ter observado que foram avisado que estava a utilizar um recurso sem explicitamente importá-lo.</span><span class="sxs-lookup"><span data-stu-id="d8e14-147">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="d8e14-148">Hoje em dia, DSC é fornecido com 12 recursos como parte do módulo PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="d8e14-148">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>

<span data-ttu-id="d8e14-149">O cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), pode ser utilizado para determinar quais recursos estão instalados no sistema e disponível para utilização pelo LCM.</span><span class="sxs-lookup"><span data-stu-id="d8e14-149">The cmdlet, [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="d8e14-150">Depois destes módulos foram colocados num `$env:PSModulePath` e são reconhecidos corretamente pelo [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), ainda precisam ser carregadas na sua configuração.</span><span class="sxs-lookup"><span data-stu-id="d8e14-150">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), they still need to be loaded within your configuration.</span></span>

<span data-ttu-id="d8e14-151">**Import-DscResource** é uma palavra-chave dinâmica que só possa ser reconhecida dentro de um **configuração** bloco, ele não seja um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d8e14-151">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block, it is not a cmdlet.</span></span>
<span data-ttu-id="d8e14-152">**Import-DscResource** suporta dois parâmetros:</span><span class="sxs-lookup"><span data-stu-id="d8e14-152">**Import-DscResource** supports two parameters:</span></span>

- <span data-ttu-id="d8e14-153">**ModuleName** é a forma recomendada de usar **Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="d8e14-153">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="d8e14-154">Ele aceita o nome do módulo que contém os recursos a serem importados (bem como uma matriz de cadeia de caracteres de nomes de módulos).</span><span class="sxs-lookup"><span data-stu-id="d8e14-154">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="d8e14-155">**Nome** é o nome do recurso para importar.</span><span class="sxs-lookup"><span data-stu-id="d8e14-155">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="d8e14-156">Não é o nome amigável retornado como "Name" ao [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), mas o nome da classe usado ao definir o esquema de recursos (retornados como **ResourceType** por [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span><span class="sxs-lookup"><span data-stu-id="d8e14-156">This is not the friendly name returned as "Name" by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span></span>

<span data-ttu-id="d8e14-157">Para obter mais informações sobre como usar `Import-DSCResource`, consulte [Import-DSCResource usando](import-dscresource.md)</span><span class="sxs-lookup"><span data-stu-id="d8e14-157">For more information on using `Import-DSCResource`, see [Using Import-DSCResource](import-dscresource.md)</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="d8e14-158">Diferenças de PowerShell v4 e v5</span><span class="sxs-lookup"><span data-stu-id="d8e14-158">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="d8e14-159">Existem diferenças no onde os recursos de DSC precisam ser armazenada no PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="d8e14-159">There are differences in where DSC resources need to be stored in PowerShell 4.0.</span></span> <span data-ttu-id="d8e14-160">Para obter mais informações, consulte [localização do recurso](import-dscresource.md#resource-location).</span><span class="sxs-lookup"><span data-stu-id="d8e14-160">For more information, see [Resource location](import-dscresource.md#resource-location).</span></span>

## <a name="see-also"></a><span data-ttu-id="d8e14-161">Veja Também</span><span class="sxs-lookup"><span data-stu-id="d8e14-161">See Also</span></span>

- [<span data-ttu-id="d8e14-162">Windows PowerShell Desired State Configuration descrição-geral</span><span class="sxs-lookup"><span data-stu-id="d8e14-162">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="d8e14-163">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="d8e14-163">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="d8e14-164">Configurar o Gestor de configuração Local</span><span class="sxs-lookup"><span data-stu-id="d8e14-164">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
