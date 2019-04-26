---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, serviço, configuração
title: Escrever, Compilar e Aplicar uma Configuração
ms.openlocfilehash: 947308efa165543571801c88a922daf44fa88be0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080021"
---
> <span data-ttu-id="a5ed1-103">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a5ed1-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="a5ed1-104">Escrever, Compilar e Aplicar uma Configuração</span><span class="sxs-lookup"><span data-stu-id="a5ed1-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="a5ed1-105">Neste exercício explica-criar e aplicar uma configuração do Desired State Configuration (DSC) do início ao fim.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="a5ed1-106">No exemplo a seguir, aprenderá como escrever e aplicar uma configuração muito simples.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="a5ed1-107">A configuração irá garantir que existe um ficheiro de "HelloWorld.txt" no seu computador local.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="a5ed1-108">Se eliminar o ficheiro, DSC recriará o da próxima vez que ele atualiza.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="a5ed1-109">Para uma descrição geral do que DSC é e como ele funciona, consulte [Desired State Configuration descrição geral para programadores](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="a5ed1-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="a5ed1-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a5ed1-110">Requirements</span></span>

<span data-ttu-id="a5ed1-111">Para executar este exemplo, irá precisar de um computador a executar o PowerShell 4.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="a5ed1-112">Escreva a configuração</span><span class="sxs-lookup"><span data-stu-id="a5ed1-112">Write the configuration</span></span>

<span data-ttu-id="a5ed1-113">Um DSC [configuração](configurations.md) é uma função especial do PowerShell que define a forma como pretende configurar uma ou mais computadores de destino (nós).</span><span class="sxs-lookup"><span data-stu-id="a5ed1-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="a5ed1-114">No ISE do PowerShell ou outro editor de PowerShell, escreva o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a5ed1-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

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

<span data-ttu-id="a5ed1-115">Guarde o ficheiro como "HelloWorld.ps1".</span><span class="sxs-lookup"><span data-stu-id="a5ed1-115">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="a5ed1-116">Definir uma configuração é como definir uma função.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-116">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="a5ed1-117">O **nó** bloco Especifica o nó de destino a ser configurado, neste caso `localhost`.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-117">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="a5ed1-118">A configuração chama uma [recursos](../resources/resources.md), o `File` recursos.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-118">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="a5ed1-119">Recursos de fazem o trabalho de garantir que o nó de destino está no estado definido pela configuração.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-119">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="a5ed1-120">Compilar a configuração</span><span class="sxs-lookup"><span data-stu-id="a5ed1-120">Compile the configuration</span></span>

<span data-ttu-id="a5ed1-121">Para uma configuração de DSC a ser aplicado a um nó, deve primeiro ser compilado num arquivo MOF.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-121">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="a5ed1-122">Executar a configuração, como uma função, irá compilar um arquivo de ". MOF" para cada nó definido pelo `Node` bloco.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-122">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="a5ed1-123">Para executar a configuração, precisa *origem ponto* seu script de "HelloWorld.ps1" no âmbito atual.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-123">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="a5ed1-124">Para obter mais informações, consulte [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="a5ed1-124">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="a5ed1-125">*Origem de dot* seu script de "HelloWorld.ps1" ao escrever no caminho onde armazenou, depois do `. ` (ponto, espaço).</span><span class="sxs-lookup"><span data-stu-id="a5ed1-125">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="a5ed1-126">Pode, em seguida, execute a configuração ao chamá-la como uma função.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-126">You may then, run your configuration by calling it like a Function.</span></span>
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

<span data-ttu-id="a5ed1-127">Isso gera o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="a5ed1-127">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="a5ed1-128">Aplicar a configuração</span><span class="sxs-lookup"><span data-stu-id="a5ed1-128">Apply the configuration</span></span>

<span data-ttu-id="a5ed1-129">Agora que tem o MOF compilado, pode aplicar a configuração para o nó de destino (no caso, o computador local) ao chamar o [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-129">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="a5ed1-130">O `Start-DscConfiguration` cmdlet informa o [Gestor de configuração Local (LCM)](../managing-nodes/metaConfig.md), o motor de DSC, para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-130">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="a5ed1-131">O LCM faz o trabalho de chamar os recursos de DSC para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-131">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="a5ed1-132">Utilize o código abaixo para executar o `Start-DSCConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-132">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="a5ed1-133">Especifique o caminho do diretório onde sua "localhost.mof" são armazenados para o `-Path` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-133">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="a5ed1-134">O `Start-DSCConfiguration` cmdlet examina o diretório especificado para qualquer "\<computername\>. MOF" ficheiros.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-134">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="a5ed1-135">O `Start-DSCConfiguration` cmdlet tenta aplicam-se cada arquivo de ". MOF" encontrar a computername especificado pelo nome de ficheiro ("localhost", "servidor01", "controlador de domínio-02", etc.).</span><span class="sxs-lookup"><span data-stu-id="a5ed1-135">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="a5ed1-136">Se o `-Wait` parâmetro não for especificado, `Start-DSCConfiguration` cria uma tarefa em segundo plano para executar a operação.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-136">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="a5ed1-137">Especificar a `-Verbose` parâmetro permite-lhe ver o **verboso** saída da operação.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-137">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="a5ed1-138">`-Wait`, e `-Verbose` são ambos os parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-138">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="a5ed1-139">Testar a configuração</span><span class="sxs-lookup"><span data-stu-id="a5ed1-139">Test the configuration</span></span>

<span data-ttu-id="a5ed1-140">Uma vez o `Start-DSCConfiguration` cmdlet estiver concluído, deverá ver um ficheiro de "HelloWorld.txt" na localização que especificou.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-140">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="a5ed1-141">Pode verificar o conteúdo com o [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-141">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="a5ed1-142">Também pode *testar* o estado atual com [Test-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="a5ed1-142">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="a5ed1-143">O resultado deve ser "Verdadeiro" se o nó está atualmente em conformidade com a configuração aplicada.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-143">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

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

## <a name="re-applying-the-configuration"></a><span data-ttu-id="a5ed1-144">Voltar a aplicar a configuração</span><span class="sxs-lookup"><span data-stu-id="a5ed1-144">Re-applying the configuration</span></span>

<span data-ttu-id="a5ed1-145">Para ver a configuração são aplicadas novamente, pode remover o arquivo de texto criado pela sua configuração.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-145">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="a5ed1-146">A utilização a `Start-DSCConfiguration` cmdlet com o `-UseExisting` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-146">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="a5ed1-147">O `-UseExisting` instrui o parâmetro `Start-DSCConfiguration` se inscrever novamente o ficheiro de "current.mof", que representa o último com êxito aplicada a configuração.</span><span class="sxs-lookup"><span data-stu-id="a5ed1-147">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="a5ed1-148">Próximos passos</span><span class="sxs-lookup"><span data-stu-id="a5ed1-148">Next steps</span></span>

- <span data-ttu-id="a5ed1-149">Saiba mais sobre as configurações de DSC em [configurações de DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="a5ed1-149">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="a5ed1-150">Veja quais recursos de DSC estão disponíveis e como criar recursos de DSC personalizados em [recursos de DSC](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="a5ed1-150">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="a5ed1-151">Localizar as configurações de DSC e os recursos a [galeria do PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="a5ed1-151">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
