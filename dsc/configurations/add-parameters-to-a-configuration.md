---
ms.date: 12/12/2018
keywords: DSC, PowerShell, recurso, Galeria, instalação
title: Adicionar Parâmetros a uma Configuração
ms.openlocfilehash: 72e6c15593d11ed39d7fe8ea79f794089f410cf8
ms.sourcegitcommit: d1ba596f9e0d4df9565601a70687a126d535c917
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/05/2019
ms.locfileid: "70386320"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="f0a45-103">Adicionar Parâmetros a uma Configuração</span><span class="sxs-lookup"><span data-stu-id="f0a45-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="f0a45-104">Como as funções, [as configurações](configurations.md) podem ser parametrizadas para permitir mais configurações dinâmicas com base na entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="f0a45-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="f0a45-105">As etapas são semelhantes às descritas em [funções com parâmetros](/powershell/module/microsoft.powershell.core/about/about_functions).</span><span class="sxs-lookup"><span data-stu-id="f0a45-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="f0a45-106">Este exemplo começa com uma configuração básica que configura o serviço de "spooler" como "em execução".</span><span class="sxs-lookup"><span data-stu-id="f0a45-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to explicitly import any required resources or modules.
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

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="f0a45-107">Parâmetros de configuração internos</span><span class="sxs-lookup"><span data-stu-id="f0a45-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="f0a45-108">No entanto, ao contrário de uma função, o atributo [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) não adiciona nenhuma funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="f0a45-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="f0a45-109">Além dos [parâmetros comuns](/powershell/module/microsoft.powershell.core/about/about_commonparameters), as configurações também podem usar os seguintes parâmetros internos, sem exigir que você os defina.</span><span class="sxs-lookup"><span data-stu-id="f0a45-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="f0a45-110">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f0a45-110">Parameter</span></span>  |<span data-ttu-id="f0a45-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f0a45-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="f0a45-112">Usado na definição de [configurações compostas](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="f0a45-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="f0a45-113">Usado na definição de [configurações compostas](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="f0a45-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="f0a45-114">Usado na definição de [configurações compostas](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="f0a45-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="f0a45-115">Usado para passar dados de [configuração](configData.md) estruturados para uso na configuração.</span><span class="sxs-lookup"><span data-stu-id="f0a45-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="f0a45-116">Usado para especificar onde o arquivo\<"\>ComputerName. mof" será compilado</span><span class="sxs-lookup"><span data-stu-id="f0a45-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="f0a45-117">Adicionando seus próprios parâmetros às configurações</span><span class="sxs-lookup"><span data-stu-id="f0a45-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="f0a45-118">Além dos parâmetros internos, você também pode adicionar seus próprios parâmetros às suas configurações.</span><span class="sxs-lookup"><span data-stu-id="f0a45-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="f0a45-119">O bloco de parâmetro fica diretamente dentro da declaração de configuração, assim como uma função.</span><span class="sxs-lookup"><span data-stu-id="f0a45-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="f0a45-120">Um bloco de parâmetro de configuração deve estar fora de qualquer declaração de **nó** e acima de qualquer instrução de *importação* .</span><span class="sxs-lookup"><span data-stu-id="f0a45-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="f0a45-121">Ao adicionar parâmetros, você pode tornar suas configurações mais robustas e dinâmicas.</span><span class="sxs-lookup"><span data-stu-id="f0a45-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="f0a45-122">Adicionar um parâmetro ComputerName</span><span class="sxs-lookup"><span data-stu-id="f0a45-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="f0a45-123">O primeiro parâmetro que você pode adicionar é `-Computername` um parâmetro para que você possa compilar dinamicamente um arquivo ". mof" `-Computername` para qualquer passagem para sua configuração.</span><span class="sxs-lookup"><span data-stu-id="f0a45-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="f0a45-124">Como as funções, você também pode definir um valor padrão, caso o usuário não passe um valor para`-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="f0a45-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="f0a45-125">Em sua configuração, você pode especificar o `-ComputerName` parâmetro ao definir o bloco de nó.</span><span class="sxs-lookup"><span data-stu-id="f0a45-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="f0a45-126">Chamando sua configuração com parâmetros</span><span class="sxs-lookup"><span data-stu-id="f0a45-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="f0a45-127">Depois de adicionar parâmetros à sua configuração, você pode usá-los exatamente como faria com um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f0a45-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="f0a45-128">Compilando vários arquivos. mof</span><span class="sxs-lookup"><span data-stu-id="f0a45-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="f0a45-129">O bloco de nó também pode aceitar uma lista separada por vírgulas de nomes de computador e gerará arquivos ". mof" para cada um.</span><span class="sxs-lookup"><span data-stu-id="f0a45-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="f0a45-130">Você pode executar o exemplo a seguir para gerar arquivos ". mof" para todos os computadores passados para o `-ComputerName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f0a45-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
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

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="f0a45-131">Parâmetros avançados em configurações</span><span class="sxs-lookup"><span data-stu-id="f0a45-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="f0a45-132">Além de um `-ComputerName` parâmetro, podemos adicionar parâmetros para o nome do serviço e o estado.</span><span class="sxs-lookup"><span data-stu-id="f0a45-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="f0a45-133">O exemplo a seguir adiciona um bloco de parâmetro `-ServiceName` com um parâmetro e o usa para definir dinamicamente o bloco de recursos de **serviço** .</span><span class="sxs-lookup"><span data-stu-id="f0a45-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="f0a45-134">Ele também adiciona um `-State` parâmetro para definir dinamicamente o **estado** no bloco de recursos de **serviço** .</span><span class="sxs-lookup"><span data-stu-id="f0a45-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

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

    # It is best practice to explicitly import any required resources or modules.
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
> <span data-ttu-id="f0a45-135">Em cenários mais Advacned, pode fazer mais sentido mover seus dados dinâmicos para [dados de configuração](configData.md)estruturados.</span><span class="sxs-lookup"><span data-stu-id="f0a45-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="f0a45-136">A configuração de exemplo agora usa um `$ServiceName`dinâmico, mas se um não for especificado, a compilação resultará em um erro.</span><span class="sxs-lookup"><span data-stu-id="f0a45-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="f0a45-137">Você pode adicionar um valor padrão como este exemplo.</span><span class="sxs-lookup"><span data-stu-id="f0a45-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="f0a45-138">No entanto, nesse caso, faz mais sentido simplesmente forçar o usuário a especificar um valor para o `$ServiceName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f0a45-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="f0a45-139">O `parameter` atributo permite que você adicione validação adicional e suporte a pipeline aos parâmetros da configuração.</span><span class="sxs-lookup"><span data-stu-id="f0a45-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="f0a45-140">Acima de qualquer declaração de parâmetro, `parameter` adicione o bloco de atributo como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f0a45-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="f0a45-141">Você pode especificar argumentos para cada `parameter` atributo, para controlar aspectos do parâmetro definido.</span><span class="sxs-lookup"><span data-stu-id="f0a45-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="f0a45-142">O exemplo a seguir cria `$ServiceName` um parâmetro **obrigatório** .</span><span class="sxs-lookup"><span data-stu-id="f0a45-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="f0a45-143">Para o `$State` parâmetro, gostaríamos de impedir que o usuário especifique valores fora de um conjunto predefinido (como em execução, parado) `ValidationSet*`o atributo impediria que o usuário especificasse valores fora de um conjunto predefinido (como em execução, Parado).</span><span class="sxs-lookup"><span data-stu-id="f0a45-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="f0a45-144">O exemplo a seguir adiciona `ValidationSet` o atributo `$State` ao parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f0a45-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="f0a45-145">Como não queremos tornar o `$State` parâmetro **obrigatório**, precisaremos adicionar um valor padrão para ele.</span><span class="sxs-lookup"><span data-stu-id="f0a45-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="f0a45-146">Você não precisa especificar um `parameter` atributo ao usar um `validation` atributo.</span><span class="sxs-lookup"><span data-stu-id="f0a45-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="f0a45-147">Você pode ler mais sobre os `parameter` atributos de validação e em [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span><span class="sxs-lookup"><span data-stu-id="f0a45-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="f0a45-148">Configuração totalmente parametrizada</span><span class="sxs-lookup"><span data-stu-id="f0a45-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="f0a45-149">Agora temos uma configuração com parâmetros que força o usuário a especificar um `-InstanceName`, `-ServiceName`e valida o `-State` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f0a45-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

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

    # It is best practice to explicitly import any required resources or modules.
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

## <a name="see-also"></a><span data-ttu-id="f0a45-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0a45-150">See also</span></span>

- [<span data-ttu-id="f0a45-151">Escrever ajuda para configurações DSC</span><span class="sxs-lookup"><span data-stu-id="f0a45-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="f0a45-152">Configurações dinâmicas</span><span class="sxs-lookup"><span data-stu-id="f0a45-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="f0a45-153">Usar dados de configuração em suas configurações</span><span class="sxs-lookup"><span data-stu-id="f0a45-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="f0a45-154">Dados de configuração e de ambiente separados</span><span class="sxs-lookup"><span data-stu-id="f0a45-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
