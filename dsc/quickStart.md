---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Configuração do Estado de início rápido de pretendida
ms.openlocfilehash: eb7572f39f7a2710c82f132f42c3502b15c48d0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219050"
---
> <span data-ttu-id="7d8d6-103">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7d8d6-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="desired-state-configuration-quick-start"></a><span data-ttu-id="7d8d6-104">Configuração do Estado de início rápido de pretendida</span><span class="sxs-lookup"><span data-stu-id="7d8d6-104">Desired State Configuration Quick Start</span></span>

<span data-ttu-id="7d8d6-105">Neste exercício explica criar e aplicar uma configuração de configuração de estado pretendido (DSC) do início ao fim.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="7d8d6-106">O exemplo utilizaremos garante que tem um servidor a `Web-Server` ativada a funcionalidade (IIS) e de que o conteúdo para um site de "Olá mundo" simples está presente no `intepub\wwwroot` diretório de que o servidor.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-106">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `intepub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="7d8d6-107">Para obter uma descrição geral de Novidades DSC e como funciona, consulte [Desired Configuration descrição geral do Estado para os decisores](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="7d8d6-107">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="7d8d6-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7d8d6-108">Requirements</span></span>

<span data-ttu-id="7d8d6-109">Para executar este exemplo, terá de um computador a executar o Windows Server 2012 ou posterior e o PowerShell 4.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-109">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="7d8d6-110">Escrever e coloque o ficheiro index.htm</span><span class="sxs-lookup"><span data-stu-id="7d8d6-110">Write and place the index.htm file</span></span>

<span data-ttu-id="7d8d6-111">Em primeiro lugar, vamos criar o ficheiro HTML que iremos utilizar como o conteúdo do Web site.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-111">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="7d8d6-112">Na sua pasta de raiz, crie uma pasta denominada `test`.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-112">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="7d8d6-113">Num editor de texto, escreva o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="7d8d6-113">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="7d8d6-114">Guarde-o como `index.htm` no `test` pasta que criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-114">Save this as `index.htm` in the `test` folder you created earlier.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="7d8d6-115">A configuração de escrita</span><span class="sxs-lookup"><span data-stu-id="7d8d6-115">Write the configuration</span></span>

<span data-ttu-id="7d8d6-116">A [configuração DSC](configurations.md) é uma função de PowerShell especial que define a forma como pretende configurar um ou mais computadores de destino (nós).</span><span class="sxs-lookup"><span data-stu-id="7d8d6-116">A [DSC configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="7d8d6-117">No ISE do PowerShell, escreva o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7d8d6-117">In the PowerShell ISE, type the following:</span></span>

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

<span data-ttu-id="7d8d6-118">Guarde o ficheiro como `WebsiteTest.ps1`.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-118">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="7d8d6-119">Pode ver que se parece com uma função do PowerShell, com a adição da palavra-chave **configuração** utilizado antes do nome da função.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-119">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="7d8d6-120">O **nó** bloco Especifica o nó de destino ser configurada, neste caso `localhost`.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-120">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="7d8d6-121">A configuração chama dois [recursos](resources.md), [WindowsFeature](windowsFeatureResource.md) e [ficheiro](fileResource.md).</span><span class="sxs-lookup"><span data-stu-id="7d8d6-121">The configuration calls two [resources](resources.md), [WindowsFeature](windowsFeatureResource.md) and [File](fileResource.md).</span></span>
<span data-ttu-id="7d8d6-122">Recursos efetuar o trabalho de se certificar de que o nó de destino está no estado definido na configuração.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-122">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="7d8d6-123">A configuração de compilação</span><span class="sxs-lookup"><span data-stu-id="7d8d6-123">Compile the configuration</span></span>

<span data-ttu-id="7d8d6-124">Para uma configuração de DSC a ser aplicado a um nó, deve primeiro ser compilado para um ficheiro MOF.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-124">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="7d8d6-125">Para tal, execute a configuração, como uma função.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-125">To do this, you run the configuration like a function.</span></span>
<span data-ttu-id="7d8d6-126">Na consola do PowerShell, navegue para a mesma pasta onde guardou a configuração e execute os seguintes comandos para compilar a configuração num ficheiro MOF:</span><span class="sxs-lookup"><span data-stu-id="7d8d6-126">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="7d8d6-127">Isto gera o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="7d8d6-127">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="7d8d6-128">A primeira linha faz com que a função de configuração disponíveis na consola.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-128">The first line makes the configuration function available in the console.</span></span>
<span data-ttu-id="7d8d6-129">A segunda linha executa a configuração.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-129">The second line runs the configuration.</span></span>
<span data-ttu-id="7d8d6-130">O resultado é que uma nova pasta designada `WebsiteTest` é criado como uma subpasta da pasta atual.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-130">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span>
<span data-ttu-id="7d8d6-131">O `WebsiteTest` pasta contém um ficheiro denominado `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-131">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span>
<span data-ttu-id="7d8d6-132">É este ficheiro que, em seguida, pode ser aplicado ao nó de destino.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-132">It is this file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="7d8d6-133">Aplicar a configuração</span><span class="sxs-lookup"><span data-stu-id="7d8d6-133">Apply the configuration</span></span>

<span data-ttu-id="7d8d6-134">Agora que tem o MOF compilado, pode aplicar a configuração para o nó de destino (neste caso, o computador local) ao chamar o [início DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-134">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span></span>

<span data-ttu-id="7d8d6-135">O `Start-DscConfiguration` cmdlet informa o [Gestor de configuração Local (MMC)](metaConfig.md), que é o motor do DSC, para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-135">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="7d8d6-136">O MMC efetua o trabalho de chamar os recursos de DSC para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-136">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="7d8d6-137">Na consola do PowerShell, navegue para a mesma pasta onde guardou a configuração e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="7d8d6-137">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="7d8d6-138">Testar a configuração</span><span class="sxs-lookup"><span data-stu-id="7d8d6-138">Test the configuration</span></span>

<span data-ttu-id="7d8d6-139">Pode chamar o [Get-DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet para ver se a configuração foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-139">You can call the [Get-DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet to see whether the configuration succeeded.</span></span>

<span data-ttu-id="7d8d6-140">Pode também testar os resultados diretamente, neste caso, navegando até `http://localhost/` num web browser.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-140">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span>
<span data-ttu-id="7d8d6-141">Deverá ver a página de "Olá mundo" HTML que criou como o primeiro passo neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="7d8d6-141">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7d8d6-142">Próximos passos</span><span class="sxs-lookup"><span data-stu-id="7d8d6-142">Next steps</span></span>

- <span data-ttu-id="7d8d6-143">Saber mais sobre as configurações de DSC na [configurações de DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="7d8d6-143">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="7d8d6-144">Consulte os recursos de DSC estão disponíveis e como criar recursos de DSC personalizados em [recursos de DSC](resources.md).</span><span class="sxs-lookup"><span data-stu-id="7d8d6-144">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](resources.md).</span></span>
- <span data-ttu-id="7d8d6-145">Localizar recursos e configurações de DSC o [galeria do PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="7d8d6-145">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>