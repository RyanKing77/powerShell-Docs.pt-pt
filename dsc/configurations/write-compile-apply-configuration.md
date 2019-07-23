---
ms.date: 12/12/2018
keywords: DSC, PowerShell, configuração, serviço, instalação
title: Escrever, Compilar e Aplicar uma Configuração
ms.openlocfilehash: 8bcd55518b0409b9a4b02ca95f027a0a77eb5300
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372172"
---
> <span data-ttu-id="93cfe-103">Aplica-se a: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="93cfe-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="93cfe-104">Escrever, Compilar e Aplicar uma Configuração</span><span class="sxs-lookup"><span data-stu-id="93cfe-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="93cfe-105">Este exercício explica como criar e aplicar uma configuração de DSC (configuração de estado desejado) do início ao fim.</span><span class="sxs-lookup"><span data-stu-id="93cfe-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="93cfe-106">No exemplo a seguir, você aprenderá a escrever e aplicar uma configuração muito simples.</span><span class="sxs-lookup"><span data-stu-id="93cfe-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="93cfe-107">A configuração garantirá que um arquivo "HelloWorld. txt" exista no computador local.</span><span class="sxs-lookup"><span data-stu-id="93cfe-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="93cfe-108">Se você excluir o arquivo, o DSC o recriará na próxima vez em que for atualizado.</span><span class="sxs-lookup"><span data-stu-id="93cfe-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="93cfe-109">Para obter uma visão geral do que é o DSC e como ele funciona, consulte [visão geral da configuração de estado desejado para desenvolvedores](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="93cfe-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="93cfe-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="93cfe-110">Requirements</span></span>

<span data-ttu-id="93cfe-111">Para executar este exemplo, você precisará de um computador executando o PowerShell 4,0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="93cfe-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="93cfe-112">Gravar a configuração</span><span class="sxs-lookup"><span data-stu-id="93cfe-112">Write the configuration</span></span>

<span data-ttu-id="93cfe-113">Uma [configuração](configurations.md) DSC é uma função especial do PowerShell que define como você deseja configurar um ou mais computadores de destino (nós).</span><span class="sxs-lookup"><span data-stu-id="93cfe-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="93cfe-114">No ISE do PowerShell ou em outro editor do PowerShell, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="93cfe-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

> <span data-ttu-id="93cfe-115">! Importante em cenários mais avançados em que vários módulos precisam ser importados para que você possa trabalhar com muitos recursos de DSC na mesma configuração, certifique-se de colocar cada módulo em `Import-DscResource`uma linha separada usando.</span><span class="sxs-lookup"><span data-stu-id="93cfe-115">!Important In more advanced scenarios where multiple modules need to be imported so you can work with many DSC Resources in the same configuration, make sure to put each module in a seperate line using `Import-DscResource`.</span></span>
> <span data-ttu-id="93cfe-116">Isso é mais fácil de manter no controle do código-fonte e é necessário ao trabalhar com a DSC na configuração de estado do Azure.</span><span class="sxs-lookup"><span data-stu-id="93cfe-116">This is easier to maintain in source control and required when working with DSC in Azure State Configuration.</span></span>
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

<span data-ttu-id="93cfe-117">Salve o arquivo como "HelloWorld. ps1".</span><span class="sxs-lookup"><span data-stu-id="93cfe-117">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="93cfe-118">Definir uma configuração é como definir uma função.</span><span class="sxs-lookup"><span data-stu-id="93cfe-118">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="93cfe-119">O bloco de **nó** especifica o nó de destino a ser configurado, nesse `localhost`caso.</span><span class="sxs-lookup"><span data-stu-id="93cfe-119">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="93cfe-120">A configuração chama um [recursos](../resources/resources.md), o `File` recurso.</span><span class="sxs-lookup"><span data-stu-id="93cfe-120">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="93cfe-121">Os recursos fazem o trabalho de garantir que o nó de destino esteja no estado definido pela configuração.</span><span class="sxs-lookup"><span data-stu-id="93cfe-121">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="93cfe-122">Compilar a configuração</span><span class="sxs-lookup"><span data-stu-id="93cfe-122">Compile the configuration</span></span>

<span data-ttu-id="93cfe-123">Para que uma configuração DSC seja aplicada a um nó, ela deve primeiro ser compilada em um arquivo MOF.</span><span class="sxs-lookup"><span data-stu-id="93cfe-123">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="93cfe-124">A execução da configuração, como uma função, irá compilar um arquivo ". mof" para cada nó definido pelo `Node` bloco.</span><span class="sxs-lookup"><span data-stu-id="93cfe-124">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="93cfe-125">Para executar a configuração, você precisa criar o *ponto de origem* do script "HelloWorld. ps1" no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="93cfe-125">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="93cfe-126">Para obter mais informações, consulte [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="93cfe-126">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="93cfe-127">*Dot Source* seu script "HelloWorld. ps1" digitando o caminho onde você o armazenou, após o `. ` (ponto, espaço).</span><span class="sxs-lookup"><span data-stu-id="93cfe-127">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="93cfe-128">Em seguida, você pode executar sua configuração chamando-a como uma função.</span><span class="sxs-lookup"><span data-stu-id="93cfe-128">You may then, run your configuration by calling it like a Function.</span></span>
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

<span data-ttu-id="93cfe-129">Isso gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="93cfe-129">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="93cfe-130">Aplicar a configuração</span><span class="sxs-lookup"><span data-stu-id="93cfe-130">Apply the configuration</span></span>

<span data-ttu-id="93cfe-131">Agora que você tem o MOF compilado, é possível aplicar a configuração ao nó de destino (nesse caso, o computador local) chamando o cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="93cfe-131">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="93cfe-132">O `Start-DscConfiguration` cmdlet informa o [Configuration Manager local (LCM)](../managing-nodes/metaConfig.md), o mecanismo do DSC, para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="93cfe-132">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="93cfe-133">O LCM faz o trabalho de chamar os recursos de DSC para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="93cfe-133">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="93cfe-134">Use o código abaixo para executar o `Start-DSCConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="93cfe-134">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="93cfe-135">Especifique o caminho do diretório em que o "localhost. mof" está armazenado `-Path` no parâmetro.</span><span class="sxs-lookup"><span data-stu-id="93cfe-135">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="93cfe-136">O `Start-DSCConfiguration` cmdlet examina o diretório especificado para todos os arquivos\<"computername\>. mof".</span><span class="sxs-lookup"><span data-stu-id="93cfe-136">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="93cfe-137">O `Start-DSCConfiguration` cmdlet tenta aplicar cada arquivo ". mof" encontrado ao ComputerName especificado pelo nome de arquivo ("localhost", "Server01", "DC-02", etc.).</span><span class="sxs-lookup"><span data-stu-id="93cfe-137">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="93cfe-138">Se o `-Wait` parâmetro não for especificado, `Start-DSCConfiguration` o criará um trabalho em segundo plano para executar a operação.</span><span class="sxs-lookup"><span data-stu-id="93cfe-138">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="93cfe-139">A especificação `-Verbose` do parâmetro permite que você assista à saída **detalhada** da operação.</span><span class="sxs-lookup"><span data-stu-id="93cfe-139">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="93cfe-140">`-Wait`e `-Verbose` são ambos parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="93cfe-140">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="93cfe-141">Testar a configuração</span><span class="sxs-lookup"><span data-stu-id="93cfe-141">Test the configuration</span></span>

<span data-ttu-id="93cfe-142">Depois que `Start-DSCConfiguration` o cmdlet for concluído, você deverá ver um arquivo "HelloWorld. txt" no local especificado.</span><span class="sxs-lookup"><span data-stu-id="93cfe-142">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="93cfe-143">Você pode verificar o conteúdo com o cmdlet [Get-Content](/powershell/module/microsoft.powershell.management/get-content) .</span><span class="sxs-lookup"><span data-stu-id="93cfe-143">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="93cfe-144">Você também pode *testar* o status atual usando [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="93cfe-144">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="93cfe-145">A saída deverá ser "true" se o nó estiver em conformidade no momento com a configuração aplicada.</span><span class="sxs-lookup"><span data-stu-id="93cfe-145">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a><span data-ttu-id="93cfe-146">Reaplicando a configuração</span><span class="sxs-lookup"><span data-stu-id="93cfe-146">Re-applying the configuration</span></span>

<span data-ttu-id="93cfe-147">Para ver sua configuração ser aplicada novamente, você pode remover o arquivo de texto criado pela sua configuração.</span><span class="sxs-lookup"><span data-stu-id="93cfe-147">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="93cfe-148">Use o `Start-DSCConfiguration` cmdlet com o `-UseExisting` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="93cfe-148">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="93cfe-149">O `-UseExisting` parâmetro`Start-DSCConfiguration` instrui a aplicar novamente o arquivo "Current. mof", que representa a configuração aplicada com êxito mais recentemente.</span><span class="sxs-lookup"><span data-stu-id="93cfe-149">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="93cfe-150">Passos Seguintes</span><span class="sxs-lookup"><span data-stu-id="93cfe-150">Next steps</span></span>

- <span data-ttu-id="93cfe-151">Saiba mais sobre as configurações de DSC em [configurações de DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="93cfe-151">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="93cfe-152">Veja quais recursos de DSC estão disponíveis e como criar recursos personalizados de DSC em [recursos de DSC](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="93cfe-152">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="93cfe-153">Localize as configurações e os recursos de DSC no [Galeria do PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="93cfe-153">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
