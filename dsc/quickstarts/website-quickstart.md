---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Início rápido - criar um Web site com o DSC
ms.openlocfilehash: d98607939ccd3cc5e660936d8c0a6d54fce7d65f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079127"
---
> <span data-ttu-id="b0442-103">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b0442-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="quickstart---create-a-website-with-dsc"></a><span data-ttu-id="b0442-104">Início rápido - criar um Web site com o DSC</span><span class="sxs-lookup"><span data-stu-id="b0442-104">Quickstart - Create a website with DSC</span></span>

<span data-ttu-id="b0442-105">Neste exercício explica-criar e aplicar uma configuração do Desired State Configuration (DSC) do início ao fim.</span><span class="sxs-lookup"><span data-stu-id="b0442-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="b0442-106">O exemplo, usaremos garante que tem um servidor do `Web-Server` (IIS) funcionalidade ativada e que o conteúdo para um site de "Hello World" simples está presente no `inetpub\wwwroot` diretório desse servidor.</span><span class="sxs-lookup"><span data-stu-id="b0442-106">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `inetpub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="b0442-107">Para uma descrição geral do que DSC é e como ele funciona, consulte [Desired State Configuration descrição geral para os tomadores de decisão](../overview/decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="b0442-107">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](../overview/decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="b0442-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b0442-108">Requirements</span></span>

<span data-ttu-id="b0442-109">Para executar este exemplo, irá precisar de um computador a executar o Windows Server 2012 ou posterior e o PowerShell 4.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="b0442-109">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="b0442-110">Escrever e colocar o arquivo htm</span><span class="sxs-lookup"><span data-stu-id="b0442-110">Write and place the index.htm file</span></span>

<span data-ttu-id="b0442-111">Em primeiro lugar, vamos criar o arquivo HTML que iremos utilizar como o conteúdo do Web site.</span><span class="sxs-lookup"><span data-stu-id="b0442-111">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="b0442-112">Na sua pasta de raiz, crie uma pasta denominada `test`.</span><span class="sxs-lookup"><span data-stu-id="b0442-112">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="b0442-113">Num editor de texto, escreva o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="b0442-113">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="b0442-114">Guardar como `index.htm` no `test` pasta que criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b0442-114">Save this as `index.htm` in the `test` folder you created earlier.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="b0442-115">Escreva a configuração</span><span class="sxs-lookup"><span data-stu-id="b0442-115">Write the configuration</span></span>

<span data-ttu-id="b0442-116">R [configuração do DSC](../configurations/configurations.md) é uma função especial do PowerShell que define a forma como pretende configurar uma ou mais computadores de destino (nós).</span><span class="sxs-lookup"><span data-stu-id="b0442-116">A [DSC configuration](../configurations/configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="b0442-117">No ISE do PowerShell, escreva o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b0442-117">In the PowerShell ISE, type the following:</span></span>

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

<span data-ttu-id="b0442-118">Guarde o ficheiro como `WebsiteTest.ps1`.</span><span class="sxs-lookup"><span data-stu-id="b0442-118">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="b0442-119">Pode ver que ele se parece com uma função de PowerShell, com a adição da palavra-chave **configuração** utilizado antes do nome da função.</span><span class="sxs-lookup"><span data-stu-id="b0442-119">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="b0442-120">O **nó** bloco Especifica o nó de destino a ser configurado, neste caso `localhost`.</span><span class="sxs-lookup"><span data-stu-id="b0442-120">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="b0442-121">A configuração chama dois [recursos](../resources/resources.md), **WindowsFeature** e **ficheiro**.</span><span class="sxs-lookup"><span data-stu-id="b0442-121">The configuration calls two [resources](../resources/resources.md), **WindowsFeature** and **File**.</span></span>
<span data-ttu-id="b0442-122">Recursos de fazem o trabalho de garantir que o nó de destino está no estado definido pela configuração.</span><span class="sxs-lookup"><span data-stu-id="b0442-122">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="b0442-123">Compilar a configuração</span><span class="sxs-lookup"><span data-stu-id="b0442-123">Compile the configuration</span></span>

<span data-ttu-id="b0442-124">Para uma configuração de DSC a ser aplicado a um nó, deve primeiro ser compilado num arquivo MOF.</span><span class="sxs-lookup"><span data-stu-id="b0442-124">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="b0442-125">Para tal, execute a configuração como uma função.</span><span class="sxs-lookup"><span data-stu-id="b0442-125">To do this, you run the configuration like a function.</span></span>
<span data-ttu-id="b0442-126">Na consola do PowerShell, navegue para a mesma pasta onde guardou a configuração e execute os seguintes comandos para compilar a configuração para um ficheiro MOF:</span><span class="sxs-lookup"><span data-stu-id="b0442-126">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="b0442-127">Isso gera o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="b0442-127">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="b0442-128">A primeira linha faz a função de configuração disponíveis na consola.</span><span class="sxs-lookup"><span data-stu-id="b0442-128">The first line makes the configuration function available in the console.</span></span>
<span data-ttu-id="b0442-129">A segunda linha executa a configuração.</span><span class="sxs-lookup"><span data-stu-id="b0442-129">The second line runs the configuration.</span></span>
<span data-ttu-id="b0442-130">O resultado é que uma nova pasta, com o nome `WebsiteTest` é criado como uma subpasta da pasta atual.</span><span class="sxs-lookup"><span data-stu-id="b0442-130">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span>
<span data-ttu-id="b0442-131">O `WebsiteTest` pasta contém um ficheiro denominado `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="b0442-131">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span>
<span data-ttu-id="b0442-132">É esse arquivo que, em seguida, pode ser aplicado ao nó de destino.</span><span class="sxs-lookup"><span data-stu-id="b0442-132">It is this file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="b0442-133">Aplicar a configuração</span><span class="sxs-lookup"><span data-stu-id="b0442-133">Apply the configuration</span></span>

<span data-ttu-id="b0442-134">Agora que tem o MOF compilado, pode aplicar a configuração para o nó de destino (no caso, o computador local) ao chamar o [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b0442-134">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="b0442-135">O `Start-DscConfiguration` cmdlet informa o [Gestor de configuração Local (LCM)](../managing-nodes/metaConfig.md), que é o motor de DSC, para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="b0442-135">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="b0442-136">O LCM faz o trabalho de chamar os recursos de DSC para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="b0442-136">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="b0442-137">Na consola do PowerShell, navegue para a mesma pasta onde guardou a configuração e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="b0442-137">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="b0442-138">Testar a configuração</span><span class="sxs-lookup"><span data-stu-id="b0442-138">Test the configuration</span></span>

<span data-ttu-id="b0442-139">Pode chamar o [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet para ver se a configuração foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="b0442-139">You can call the [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet to see whether the configuration succeeded.</span></span>

<span data-ttu-id="b0442-140">Também pode testar os resultados diretamente, neste caso, navegando até `http://localhost/` num navegador da web.</span><span class="sxs-lookup"><span data-stu-id="b0442-140">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span>
<span data-ttu-id="b0442-141">Deverá ver a página de "Hello World" HTML que criou como a primeira etapa neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="b0442-141">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b0442-142">Próximos passos</span><span class="sxs-lookup"><span data-stu-id="b0442-142">Next steps</span></span>

- <span data-ttu-id="b0442-143">Saiba mais sobre as configurações de DSC em [configurações de DSC](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="b0442-143">Find out more about DSC configurations at [DSC configurations](../configurations/configurations.md).</span></span>
- <span data-ttu-id="b0442-144">Veja quais recursos de DSC estão disponíveis e como criar recursos de DSC personalizados em [recursos de DSC](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="b0442-144">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="b0442-145">Localizar as configurações de DSC e os recursos a [galeria do PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="b0442-145">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
