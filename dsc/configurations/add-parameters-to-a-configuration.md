---
ms.date: 12/12/2018
keywords: DSC, powershell, recurso, galeria, a configuração
title: Adicionar Parâmetros a uma Configuração
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685404"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="6bc58-103">Adicionar Parâmetros a uma Configuração</span><span class="sxs-lookup"><span data-stu-id="6bc58-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="6bc58-104">Como as funções, [configurações](configurations.md) pode ser parametrizada para permitir que as configurações mais dinâmicas com base na entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="6bc58-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="6bc58-105">Os passos são semelhantes às descritas [as funções com parâmetros](/powershell/module/microsoft.powershell.core/about/about_functions).</span><span class="sxs-lookup"><span data-stu-id="6bc58-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="6bc58-106">Este exemplo começa com uma configuração básica que configura o serviço de "Spooler" de "Executar".</span><span class="sxs-lookup"><span data-stu-id="6bc58-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="6bc58-107">Parâmetros de configuração incorporados</span><span class="sxs-lookup"><span data-stu-id="6bc58-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="6bc58-108">Ao contrário de uma função no entanto, o [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) atributo não adiciona nenhuma funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="6bc58-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="6bc58-109">Para além [parâmetros comuns de](/powershell/module/microsoft.powershell.core/about/about_commonparameters), configurações também podem utilizar o seguinte criado nos parâmetros, sem exigir a defini-las.</span><span class="sxs-lookup"><span data-stu-id="6bc58-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="6bc58-110">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="6bc58-110">Parameter</span></span>  |<span data-ttu-id="6bc58-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="6bc58-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="6bc58-112">Utilizadas na definição de [configurações compostos](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="6bc58-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="6bc58-113">Utilizadas na definição de [configurações compostos](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="6bc58-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="6bc58-114">Utilizadas na definição de [configurações compostos](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="6bc58-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="6bc58-115">Usado para transmitir em estruturado [dados de configuração](configData.md) para utilização na configuração.</span><span class="sxs-lookup"><span data-stu-id="6bc58-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="6bc58-116">Utilizado para especificar onde sua "\<computername\>. MOF" ficheiro será compilado</span><span class="sxs-lookup"><span data-stu-id="6bc58-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="6bc58-117">Adicionar os seus parâmetros para configurações</span><span class="sxs-lookup"><span data-stu-id="6bc58-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="6bc58-118">Além dos parâmetros internos, também pode adicionar seus próprios parâmetros para suas configurações.</span><span class="sxs-lookup"><span data-stu-id="6bc58-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="6bc58-119">O bloco de parâmetro vai diretamente dentro da declaração de configuração, assim como uma função.</span><span class="sxs-lookup"><span data-stu-id="6bc58-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="6bc58-120">Um bloco de parâmetro de configuração deve estar fora de qualquer **nó** declarações e acima qualquer *importar* instruções.</span><span class="sxs-lookup"><span data-stu-id="6bc58-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="6bc58-121">Ao adicionar parâmetros, pode fazer suas configurações mais robusto e dinâmico.</span><span class="sxs-lookup"><span data-stu-id="6bc58-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="6bc58-122">Adicione um parâmetro ComputerName</span><span class="sxs-lookup"><span data-stu-id="6bc58-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="6bc58-123">O primeiro parâmetro, pode adicionar é uma `-Computername` parâmetro para que pode compilar dinamicamente um arquivo de ". MOF" para qualquer `-Computername` passar para a configuração.</span><span class="sxs-lookup"><span data-stu-id="6bc58-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="6bc58-124">Como funções, também pode definir um valor predefinido, no caso do utilizador não introduzir um valor para `-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="6bc58-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="6bc58-125">Na sua configuração, em seguida, pode especificar seu `-ComputerName` parâmetro ao definir seu bloco de nó.</span><span class="sxs-lookup"><span data-stu-id="6bc58-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="6bc58-126">Chamar a configuração com parâmetros</span><span class="sxs-lookup"><span data-stu-id="6bc58-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="6bc58-127">Depois de adicionar parâmetros à sua configuração, pode usá-los tal como faria com um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6bc58-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="6bc58-128">Compilação de vários arquivos. MOF</span><span class="sxs-lookup"><span data-stu-id="6bc58-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="6bc58-129">O bloco de nó também pode aceitar uma lista separada por vírgulas de nomes de computador e irá gerar arquivos ". MOF" para cada um.</span><span class="sxs-lookup"><span data-stu-id="6bc58-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="6bc58-130">Pode executar o exemplo a seguir para gerar arquivos de ". MOF" para todos os computadores passados para o `-ComputerName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6bc58-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="6bc58-131">Parâmetros avançados em configurações</span><span class="sxs-lookup"><span data-stu-id="6bc58-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="6bc58-132">Para além um `-ComputerName` parâmetro, podemos adicionar parâmetros para o nome do serviço e o estado.</span><span class="sxs-lookup"><span data-stu-id="6bc58-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="6bc58-133">O exemplo seguinte adiciona um bloco de parâmetro com um `-ServiceName` parâmetro e utiliza-a para definir dinamicamente o **serviço** bloco de recursos.</span><span class="sxs-lookup"><span data-stu-id="6bc58-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="6bc58-134">Também adiciona uma `-State` parâmetro para definir dinamicamente o **estado** no **serviço** bloco de recursos.</span><span class="sxs-lookup"><span data-stu-id="6bc58-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="6bc58-135">Em mais cenários de advacned, pode fazer mais sentido para mover os dados dinâmicos para uma estruturados [dados de configuração](configData.md).</span><span class="sxs-lookup"><span data-stu-id="6bc58-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="6bc58-136">O exemplo de configuração agora demora dinâmico `$ServiceName`, mas se não for especificado, os resultados num erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="6bc58-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="6bc58-137">Poderia adicionar um valor predefinido, como neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="6bc58-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="6bc58-138">Neste caso, faz mais sentido simplesmente forçar o utilizador especifique um valor para o `$ServiceName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6bc58-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="6bc58-139">O `parameter` atributo permite-lhe adicionar suporte a mais de validação e pipeline para parâmetros de sua configuração.</span><span class="sxs-lookup"><span data-stu-id="6bc58-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="6bc58-140">Acima de qualquer declaração de parâmetro, adicione o `parameter` bloco de atributo como no exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="6bc58-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="6bc58-141">Pode especificar argumentos para cada `parameter` atributo, a controlem aspectos do parâmetro definido.</span><span class="sxs-lookup"><span data-stu-id="6bc58-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="6bc58-142">O exemplo a seguir faz com que o `$ServiceName` um **obrigatório** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6bc58-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="6bc58-143">Para o `$State` parâmetro, também gostaria de evitar que o utilizador especificar valores fora de um conjunto predefinido (como em execução, parado) a `ValidationSet*`atributo seria impedir que o utilizador especificar valores fora de um conjunto predefinido (como em execução, Parado).</span><span class="sxs-lookup"><span data-stu-id="6bc58-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="6bc58-144">O exemplo seguinte adiciona o `ValidationSet` atributo para o `$State` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6bc58-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="6bc58-145">Uma vez que não queremos tornar a `$State` parâmetro **obrigatório**, precisamos de adicionar um valor predefinido para o mesmo.</span><span class="sxs-lookup"><span data-stu-id="6bc58-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="6bc58-146">Não é necessário especificar um `parameter` atributo ao utilizar um `validation` atributo.</span><span class="sxs-lookup"><span data-stu-id="6bc58-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="6bc58-147">Pode ler mais sobre o `parameter` e atributos de validação na [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6bc58-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="6bc58-148">Configuração totalmente parametrizada</span><span class="sxs-lookup"><span data-stu-id="6bc58-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="6bc58-149">Agora, temos uma configuração parametrizada que força o utilizador especifique um `-InstanceName`, `-ServiceName`e valida o `-State` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6bc58-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="6bc58-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6bc58-150">See also</span></span>

- [<span data-ttu-id="6bc58-151">Escrever ajuda para configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="6bc58-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="6bc58-152">Configurações dinâmicas</span><span class="sxs-lookup"><span data-stu-id="6bc58-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="6bc58-153">Utilizar dados de configuração nas suas configurações</span><span class="sxs-lookup"><span data-stu-id="6bc58-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="6bc58-154">Dados de configuração e ambiente separado</span><span class="sxs-lookup"><span data-stu-id="6bc58-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
