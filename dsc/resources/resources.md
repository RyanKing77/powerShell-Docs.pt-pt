---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Recursos de DSC
ms.openlocfilehash: 02e1b9856942cf28e77d83dac89681a08cf6bb74
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012454"
---
# <a name="dsc-resources"></a><span data-ttu-id="1f1d2-103">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="1f1d2-103">DSC Resources</span></span>

><span data-ttu-id="1f1d2-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1f1d2-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="1f1d2-105">Desired State Configuration (DSC) recursos fornecem os blocos de construção para uma configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="1f1d2-106">Um recurso expõe propriedades que podem ser configurada (esquema) e contém as funções de script do PowerShell que o Gestor de configuração Local (LCM) chama de "tornam isso".</span><span class="sxs-lookup"><span data-stu-id="1f1d2-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="1f1d2-107">Um recurso pode modelar algo como genérica como um ficheiro ou o mais específico como uma definição de servidor IIS.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="1f1d2-108">Grupos de como os recursos são combinados em para um módulo de DSC, o que organiza a todos os ficheiros necessários para uma estrutura que é portátil e inclui metadados para identificar a forma como os recursos destinam-se a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="1f1d2-109">Cada recurso tem um \* esquema que determina a sintaxe necessária para utilizar o recurso num [configuração](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="1f1d2-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="1f1d2-110">Esquema de um recurso pode ser definida da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="1f1d2-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="1f1d2-111">**'Schema.Mof'** ficheiro: Definir a maioria dos recursos seus *esquema* num schema.mof de ficheiros, usando [formato de objeto gerenciado](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="1f1d2-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="1f1d2-112">**'\<Nome do recurso\>. schema.psm1'** ficheiro: [Recursos compostos](../configurations/compositeConfigs.md) definir seus *esquema* num '<ResourceName>. schema.psm1' de ficheiros com um [bloco de parâmetro](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="1f1d2-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="1f1d2-113">**'\<Nome do recurso\>psm1 '** ficheiro: Classe de recursos de DSC com base definem seus *esquema* na definição de classe.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="1f1d2-114">Itens de sintaxe estão marcadas como propriedades de classe.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="1f1d2-115">Para obter mais informações, consulte [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span><span class="sxs-lookup"><span data-stu-id="1f1d2-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="1f1d2-116">Para obter a sintaxe de um recurso de DSC, utilize o [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet com o `-Syntax` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="1f1d2-117">Esse uso é semelhante à utilização [Get-Command](/powershell/module/microsoft.powershell.core/get-command) com o `-Syntax` parâmetro para obter a sintaxe de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="1f1d2-118">A saída que vir mostrará o modelo utilizado para um bloco de recursos para o recurso que especificar.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="1f1d2-119">A saída que vir deve ser semelhante à saída abaixo, embora a sintaxe deste recurso foi alterado no futuro.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="1f1d2-120">Como a sintaxe de cmdlet, o *chaves* visto em parênteses Retos, são opcionais.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="1f1d2-121">Os tipos de especificar o tipo de dados que cada chave de espera.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="1f1d2-122">O **Certifique-se** chave é opcional, pois é assumida como predefinição "Presente".</span><span class="sxs-lookup"><span data-stu-id="1f1d2-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

<span data-ttu-id="1f1d2-123">Dentro de uma configuração, um **serviço** bloco de recurso pode ser assim para **Certifique-se** que está a executar o serviço de Spooler.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="1f1d2-124">Antes de utilizar um recurso numa configuração, tem de importá-lo a utilizar [Import-DSCResource](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="1f1d2-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

<span data-ttu-id="1f1d2-125">Configurações podem conter várias instâncias do mesmo tipo de recurso.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="1f1d2-126">Cada instância tem de ser chamada de exclusivamente.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="1f1d2-127">No exemplo a seguir, um segundo **serviço** bloco de recurso é adicionado para configurar o serviço de "DHCP".</span><span class="sxs-lookup"><span data-stu-id="1f1d2-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="1f1d2-128">A partir do PowerShell 5.0, intellisense, foi adicionado para DSC.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="1f1d2-129">Esta nova funcionalidade permite-lhe utilizar \<SEPARADOR\> e \<Ctrl + espaço\> para nomes de chaves de preenchimento automático.</span><span class="sxs-lookup"><span data-stu-id="1f1d2-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![Conclusão de tabulação de recursos](../media/resource-tabcompletion.png)
