---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Lista de verificação de criação de recursos
ms.openlocfilehash: 7b1a096bba1b729c096b6689178ee022e12e4634
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405082"
---
# <a name="resource-authoring-checklist"></a><span data-ttu-id="2af79-103">Lista de verificação de criação de recursos</span><span class="sxs-lookup"><span data-stu-id="2af79-103">Resource authoring checklist</span></span>

<span data-ttu-id="2af79-104">Esta lista de verificação é uma lista de melhores práticas durante a criação de um novo recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="2af79-104">This checklist is a list of best practices when authoring a new DSC Resource.</span></span>

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a><span data-ttu-id="2af79-105">Módulo de recursos contém o ficheiro. psd1 e schema.mof para todos os recursos</span><span class="sxs-lookup"><span data-stu-id="2af79-105">Resource module contains .psd1 file and schema.mof for every resource</span></span>

<span data-ttu-id="2af79-106">Verifique se o seu recurso tem a estrutura correta e contém todos os ficheiros necessários.</span><span class="sxs-lookup"><span data-stu-id="2af79-106">Check that your resource has correct structure and contains all required files.</span></span> <span data-ttu-id="2af79-107">Cada módulo de recurso deve conter um ficheiro. psd1 e todos os recursos compostos não devem ter schema.mof ficheiro.</span><span class="sxs-lookup"><span data-stu-id="2af79-107">Every resource module should contain a .psd1 file and every non-composite resource should have schema.mof file.</span></span> <span data-ttu-id="2af79-108">Recursos que contém o esquema não serão listados por `Get-DscResource` e os utilizadores não poderão usar o intellisense ao escrever código contra esses módulos no ISE.</span><span class="sxs-lookup"><span data-stu-id="2af79-108">Resources that do not contain schema will not be listed by `Get-DscResource` and users will not be able to use the intellisense when writing code against those modules in ISE.</span></span>
<span data-ttu-id="2af79-109">A estrutura de diretórios para o recurso de xRemoteFile, que faz parte do [módulo do recurso de xPSDesiredStateConfiguration](https://github.com/PowerShell/xPSDesiredStateConfiguration), seria semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="2af79-109">The directory structure for xRemoteFile resource, which is part of the [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), looks as follows:</span></span>

```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a><span data-ttu-id="2af79-110">Esquema e de recursos estão corretos</span><span class="sxs-lookup"><span data-stu-id="2af79-110">Resource and schema are correct</span></span>

<span data-ttu-id="2af79-111">Verifique se o esquema de recursos (\*. schema.mof) ficheiros.</span><span class="sxs-lookup"><span data-stu-id="2af79-111">Verify the resource schema (\*.schema.mof) file.</span></span> <span data-ttu-id="2af79-112">Pode utilizar o [Designer de recursos de DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) para ajudar a desenvolver e testar o seu esquema.</span><span class="sxs-lookup"><span data-stu-id="2af79-112">You can use the [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to help develop and test your schema.</span></span>
<span data-ttu-id="2af79-113">Certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="2af79-113">Make sure that:</span></span>

- <span data-ttu-id="2af79-114">Tipos de propriedade estão corretos (por exemplo, não utilizar cadeia de caracteres para propriedades que aceitam os valores numéricos, deve usar UInt32 ou outros tipos numéricos em vez disso)</span><span class="sxs-lookup"><span data-stu-id="2af79-114">Property types are correct (e.g. don’t use String for properties which accept numeric values, you should use UInt32 or other numeric types instead)</span></span>
- <span data-ttu-id="2af79-115">Atributos da propriedade estão corretamente especificados como: ([chave], [necessário], [escrever], [ler])</span><span class="sxs-lookup"><span data-stu-id="2af79-115">Property attributes are specified correctly as: ([key], [required], [write], [read])</span></span>
- <span data-ttu-id="2af79-116">Pelo menos um parâmetro no esquema tem de ser marcado como [chave]</span><span class="sxs-lookup"><span data-stu-id="2af79-116">At least one parameter in the schema has to be marked as [key]</span></span>
- <span data-ttu-id="2af79-117">[ler] propriedade não coexistir juntamente com qualquer um dos: [necessário], [a chave], [escrever]</span><span class="sxs-lookup"><span data-stu-id="2af79-117">[read] property does not coexist together with any of: [required], [key], [write]</span></span>
- <span data-ttu-id="2af79-118">Se vários qualificadores forem especificados, exceto [leitura], [a chave] tem precedência</span><span class="sxs-lookup"><span data-stu-id="2af79-118">If multiple qualifiers are specified except [read], then [key] takes precedence</span></span>
- <span data-ttu-id="2af79-119">Se [escrever] e [necessário] são especificados, em seguida, tem precedência de [necessário]</span><span class="sxs-lookup"><span data-stu-id="2af79-119">If [write] and [required] are specified, then [required] takes precedence</span></span>
- <span data-ttu-id="2af79-120">ValueMap é especificada quando apropriado exemplo:</span><span class="sxs-lookup"><span data-stu-id="2af79-120">ValueMap is specified where appropriate Example:</span></span>

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- <span data-ttu-id="2af79-121">Nome amigável é especificado e confirma as convenções de nomenclatura de DSC</span><span class="sxs-lookup"><span data-stu-id="2af79-121">Friendly name is specified and confirms to DSC naming conventions</span></span>

  <span data-ttu-id="2af79-122">Exemplo: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span><span class="sxs-lookup"><span data-stu-id="2af79-122">Example: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span></span>

- <span data-ttu-id="2af79-123">Cada campo tem descrição relevante.</span><span class="sxs-lookup"><span data-stu-id="2af79-123">Every field has meaningful description.</span></span> <span data-ttu-id="2af79-124">O repositório do GitHub do PowerShell possui bons exemplos, como [o. schema.mof para xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span><span class="sxs-lookup"><span data-stu-id="2af79-124">The PowerShell GitHub repository has good examples, such as [the .schema.mof for xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span></span>

<span data-ttu-id="2af79-125">Além disso, deve usar **teste xDscResource** e **teste xDscSchema** cmdlets da [Designer de recursos de DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) para verificar automaticamente o recurso e o esquema:</span><span class="sxs-lookup"><span data-stu-id="2af79-125">Additionally, you should use **Test-xDscResource** and **Test-xDscSchema** cmdlets from [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to automatically verify the resource and schema:</span></span>

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

<span data-ttu-id="2af79-126">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2af79-126">For example:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a><span data-ttu-id="2af79-127">Recurso for carregada sem erros</span><span class="sxs-lookup"><span data-stu-id="2af79-127">Resource loads without errors</span></span>

<span data-ttu-id="2af79-128">Verifique se o módulo de recurso pode ser carregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="2af79-128">Check whether the resource module can be successfully loaded.</span></span>
<span data-ttu-id="2af79-129">Isso pode ser conseguido manualmente, executando `Import-Module <resource_module> -force` e confirmar que nenhum erro ocorreu, ou ao escrever automação de teste.</span><span class="sxs-lookup"><span data-stu-id="2af79-129">This can be achieved manually, by running `Import-Module <resource_module> -force` and confirming that no errors occurred, or by writing test automation.</span></span> <span data-ttu-id="2af79-130">Em caso da última opção, pode seguir esta estrutura no seu caso de teste:</span><span class="sxs-lookup"><span data-stu-id="2af79-130">In case of the latter, you can follow this structure in your test case:</span></span>

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a><span data-ttu-id="2af79-131">Recurso é idempotent no caso positivo</span><span class="sxs-lookup"><span data-stu-id="2af79-131">Resource is idempotent in the positive case</span></span>

<span data-ttu-id="2af79-132">Uma das características fundamentais de recursos de DSC é idempotence.</span><span class="sxs-lookup"><span data-stu-id="2af79-132">One of the fundamental characteristics of DSC resources is idempotence.</span></span> <span data-ttu-id="2af79-133">Isso significa que a aplicação de uma configuração de DSC contendo esse recurso várias vezes será sempre alcançar o mesmo resultado.</span><span class="sxs-lookup"><span data-stu-id="2af79-133">It means that applying a DSC configuration containing that resource multiple times will always achieve the same result.</span></span> <span data-ttu-id="2af79-134">Por exemplo, se criarmos uma configuração que contém o seguinte recurso do ficheiro:</span><span class="sxs-lookup"><span data-stu-id="2af79-134">For example, if we create a configuration which contains the following File resource:</span></span>

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

<span data-ttu-id="2af79-135">Depois de aplicá-lo pela primeira vez, o ficheiro txt deve aparecer na `C:\test` pasta.</span><span class="sxs-lookup"><span data-stu-id="2af79-135">After applying it for the first time, file test.txt should appear in `C:\test` folder.</span></span> <span data-ttu-id="2af79-136">No entanto, as execuções posteriores da configuração do mesmo não devem alterar o estado da máquina (por exemplo, não existem cópias do `test.txt` ficheiro deve ser criado).</span><span class="sxs-lookup"><span data-stu-id="2af79-136">However, subsequent runs of the same configuration should not change the state of the machine (e.g. no copies of the `test.txt` file should be created).</span></span>
<span data-ttu-id="2af79-137">Para garantir que um recurso é idempotente pode chamar repetidamente `Set-TargetResource` quando o recurso de teste diretamente ou chamar `Start-DscConfiguration` várias vezes fazendo quando o teste de ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="2af79-137">To ensure a resource is idempotent you can repeatedly call `Set-TargetResource` when testing the resource directly, or call `Start-DscConfiguration` multiple times when doing end to end testing.</span></span> <span data-ttu-id="2af79-138">O resultado deve ser o mesmo após cada execução.</span><span class="sxs-lookup"><span data-stu-id="2af79-138">The result should be the same after every run.</span></span>

## <a name="test-user-modification-scenario"></a><span data-ttu-id="2af79-139">Cenário de modificação de utilizador de teste</span><span class="sxs-lookup"><span data-stu-id="2af79-139">Test user modification scenario</span></span>

<span data-ttu-id="2af79-140">Ao alterar o estado da máquina e, em seguida, volte a executar a DSC, pode verificar que `Set-TargetResource` e `Test-TargetResource` funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="2af79-140">By changing the state of the machine and then rerunning DSC, you can verify that `Set-TargetResource` and `Test-TargetResource` function properly.</span></span> <span data-ttu-id="2af79-141">Eis os passos que deve tomar:</span><span class="sxs-lookup"><span data-stu-id="2af79-141">Here are steps you should take:</span></span>

1. <span data-ttu-id="2af79-142">Comece com o recurso não no estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="2af79-142">Start with the resource not in the desired state.</span></span>
2. <span data-ttu-id="2af79-143">Configuração de execução com o seu recurso</span><span class="sxs-lookup"><span data-stu-id="2af79-143">Run configuration with your resource</span></span>
3. <span data-ttu-id="2af79-144">Certifique-se de `Test-DscConfiguration` retorna True</span><span class="sxs-lookup"><span data-stu-id="2af79-144">Verify `Test-DscConfiguration` returns True</span></span>
4. <span data-ttu-id="2af79-145">Modificar o item configurado para ser sair do estado pretendido</span><span class="sxs-lookup"><span data-stu-id="2af79-145">Modify the configured item to be out of the desired state</span></span>
5. <span data-ttu-id="2af79-146">Certifique-se de `Test-DscConfiguration` retorna FALSO</span><span class="sxs-lookup"><span data-stu-id="2af79-146">Verify `Test-DscConfiguration` returns false</span></span>

<span data-ttu-id="2af79-147">Eis um exemplo mais concreto usando o recurso de Registro:</span><span class="sxs-lookup"><span data-stu-id="2af79-147">Here’s a more concrete example using Registry resource:</span></span>

1. <span data-ttu-id="2af79-148">Começar com a chave de registo não no estado pretendido</span><span class="sxs-lookup"><span data-stu-id="2af79-148">Start with registry key not in the desired state</span></span>
2. <span data-ttu-id="2af79-149">Executar `Start-DscConfiguration` com uma configuração para colocá-la no estado pretendido e verifique se ele passa.</span><span class="sxs-lookup"><span data-stu-id="2af79-149">Run `Start-DscConfiguration` with a configuration to put it in the desired state and verify it passes.</span></span>
3. <span data-ttu-id="2af79-150">Executar `Test-DscConfiguration` e certifique-se de que ela retorna verdadeiro</span><span class="sxs-lookup"><span data-stu-id="2af79-150">Run `Test-DscConfiguration` and verify it returns true</span></span>
4. <span data-ttu-id="2af79-151">Modifique o valor da chave, para que não esteja no estado pretendido</span><span class="sxs-lookup"><span data-stu-id="2af79-151">Modify the value of the key so that it is not in the desired state</span></span>
5. <span data-ttu-id="2af79-152">Executar `Test-DscConfiguration` e certifique-se de que ele retornará false</span><span class="sxs-lookup"><span data-stu-id="2af79-152">Run `Test-DscConfiguration` and verify it returns false</span></span>
6. <span data-ttu-id="2af79-153">`Get-TargetResource` funcionalidade foi verificada através de `Get-DscConfiguration`</span><span class="sxs-lookup"><span data-stu-id="2af79-153">`Get-TargetResource` functionality was verified using `Get-DscConfiguration`</span></span>

<span data-ttu-id="2af79-154">`Get-TargetResource` deverá devolver os detalhes do estado atual do recurso.</span><span class="sxs-lookup"><span data-stu-id="2af79-154">`Get-TargetResource` should return details of the current state of the resource.</span></span> <span data-ttu-id="2af79-155">Certifique-se de testá-lo chamando `Get-DscConfiguration` depois de aplicar a configuração e verificar que saída corretamente reflete o estado atual da máquina.</span><span class="sxs-lookup"><span data-stu-id="2af79-155">Make sure to test it by calling `Get-DscConfiguration` after you apply the configuration and verifying that output correctly reflects the current state of the machine.</span></span> <span data-ttu-id="2af79-156">É importante testá-lo em separado, uma vez que todos os problemas nessa área não será apresentado ao chamar `Start-DscConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="2af79-156">It's important to test it separately, since any issues in this area won't appear when calling `Start-DscConfiguration`.</span></span>

## <a name="call-getsettest-targetresource-functions-directly"></a><span data-ttu-id="2af79-157">Chamar **Get/Set/teste-TargetResource** diretamente de funções</span><span class="sxs-lookup"><span data-stu-id="2af79-157">Call **Get/Set/Test-TargetResource** functions directly</span></span>

<span data-ttu-id="2af79-158">Certifique-se de que teste o **Get/Set/teste-TargetResource** funções implementadas no seu recurso chamando-las diretamente e verificar que estão a funcionar conforme esperado.</span><span class="sxs-lookup"><span data-stu-id="2af79-158">Make sure you test the **Get/Set/Test-TargetResource** functions implemented in your resource by calling them directly and verifying that they work as expected.</span></span>

## <a name="verify-end-to-end-using-start-dscconfiguration"></a><span data-ttu-id="2af79-159">Certifique-se de que ponto a ponto com **início-dscconfiguration para**</span><span class="sxs-lookup"><span data-stu-id="2af79-159">Verify End to End using **Start-DscConfiguration**</span></span>

<span data-ttu-id="2af79-160">Testes **Get/Set/teste-TargetResource** funções ao chamá-los diretamente é importante, mas nem todos os problemas serão detetados dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="2af79-160">Testing **Get/Set/Test-TargetResource** functions by calling them directly is important, but not all issues will be discovered this way.</span></span> <span data-ttu-id="2af79-161">Deve focar-se uma parte significativa de teste sobre como utilizar `Start-DscConfiguration` ou o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="2af79-161">You should focus significant part of your testing on using `Start-DscConfiguration` or the pull server.</span></span> <span data-ttu-id="2af79-162">Na verdade, isso é como os usuários usarão o recurso, portanto, não subestime a importância desse tipo de testes.</span><span class="sxs-lookup"><span data-stu-id="2af79-162">In fact, this is how users will use the resource, so don’t underestimate the significance of this type of tests.</span></span>
<span data-ttu-id="2af79-163">Possíveis tipos de problemas:</span><span class="sxs-lookup"><span data-stu-id="2af79-163">Possible types of issues:</span></span>

- <span data-ttu-id="2af79-164">Credenciais/sessão pode ter um comportamento diferente porque o agente DSC é executado como um serviço.</span><span class="sxs-lookup"><span data-stu-id="2af79-164">Credential/Session may behave differently because the DSC agent runs as a service.</span></span>  <span data-ttu-id="2af79-165">Certifique-se de que quaisquer funcionalidades aqui de teste ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="2af79-165">Be sure to test any features here end to end.</span></span>
- <span data-ttu-id="2af79-166">Erros de saída por `Start-DscConfiguration` podem ser diferentes dos apresentados ao chamar o `Set-TargetResource` função diretamente.</span><span class="sxs-lookup"><span data-stu-id="2af79-166">Errors output by `Start-DscConfiguration` may be different than those displayed when calling the `Set-TargetResource` function directly.</span></span>

## <a name="test-compatability-on-all-dsc-supported-platforms"></a><span data-ttu-id="2af79-167">Teste de compatibilidade no DSC todas as plataformas suportadas</span><span class="sxs-lookup"><span data-stu-id="2af79-167">Test compatability on all DSC supported platforms</span></span>

<span data-ttu-id="2af79-168">Recurso deverá funcionar em todas as plataformas suportada do DSC (Windows Server 2008 R2 e versões mais recentes).</span><span class="sxs-lookup"><span data-stu-id="2af79-168">Resource should work on all DSC supported platforms (Windows Server 2008 R2 and newer).</span></span> <span data-ttu-id="2af79-169">Instale o WMF mais recente (Windows Management Framework) no seu SO para obter a versão mais recente do DSC.</span><span class="sxs-lookup"><span data-stu-id="2af79-169">Install the latest WMF (Windows Management Framework) on your OS to get the latest version of DSC.</span></span> <span data-ttu-id="2af79-170">Se o recurso não funciona em algumas dessas plataformas por design, uma mensagem de erro específico deve ser devolvida.</span><span class="sxs-lookup"><span data-stu-id="2af79-170">If your resource does not work on some of these platforms by design, a specific error message should be returned.</span></span> <span data-ttu-id="2af79-171">Além disso, certifique-se de que o seu recurso verifica se está a chamar de cmdlets estão presentes na máquina específica.</span><span class="sxs-lookup"><span data-stu-id="2af79-171">Also, make sure your resource checks whether cmdlets you are calling are present on particular machine.</span></span> <span data-ttu-id="2af79-172">Windows Server 2012 adicionados um grande número de novos cmdlets que não estão disponíveis no Windows Server 2008 R2, mesmo com WMF instalado.</span><span class="sxs-lookup"><span data-stu-id="2af79-172">Windows Server 2012 added a large number of new cmdlets that are not available on Windows Server 2008R2, even with WMF installed.</span></span>

## <a name="verify-on-windows-client-if-applicable"></a><span data-ttu-id="2af79-173">Certifique-se no cliente do Windows (se aplicável)</span><span class="sxs-lookup"><span data-stu-id="2af79-173">Verify on Windows Client (if applicable)</span></span>

<span data-ttu-id="2af79-174">Um intervalo de teste muito comum é a verificar o recurso apenas em versões de servidor do Windows.</span><span class="sxs-lookup"><span data-stu-id="2af79-174">One very common test gap is verifying the resource only on server versions of Windows.</span></span> <span data-ttu-id="2af79-175">Muitos recursos também foram concebidos para funcionar em SKUs de cliente, portanto, se isso for verdade no seu caso, não se esqueça de testá-lo nessas plataformas também.</span><span class="sxs-lookup"><span data-stu-id="2af79-175">Many resources are also designed to work on Client SKUs, so if that’s true in your case, don’t forget to test it on those platforms as well.</span></span>

## <a name="get-dscresource-lists-the-resource"></a><span data-ttu-id="2af79-176">O recurso apresenta uma lista de GET-DSCResource</span><span class="sxs-lookup"><span data-stu-id="2af79-176">Get-DSCResource lists the resource</span></span>

<span data-ttu-id="2af79-177">Depois de implementar o módulo, chamar `Get-DscResource` deve listar assim o seu recurso, entre outros.</span><span class="sxs-lookup"><span data-stu-id="2af79-177">After deploying the module, calling `Get-DscResource` should list your resource among others as a result.</span></span> <span data-ttu-id="2af79-178">Se não encontrar o recurso na lista, certifique-se esse arquivo schema.mof esse recurso de existência.</span><span class="sxs-lookup"><span data-stu-id="2af79-178">If you can’t find your resource in the list, make sure that schema.mof file for that resource exists.</span></span>

## <a name="resource-module-contains-examples"></a><span data-ttu-id="2af79-179">Módulo de recursos contém exemplos</span><span class="sxs-lookup"><span data-stu-id="2af79-179">Resource module contains examples</span></span>

<span data-ttu-id="2af79-180">Criar exemplos de qualidade que irão ajudar os outros entenderem como usá-lo.</span><span class="sxs-lookup"><span data-stu-id="2af79-180">Creating quality examples which will help others understand how to use it.</span></span> <span data-ttu-id="2af79-181">Isso é crucial, especialmente, uma vez que muitos usuários tratam o código de exemplo como documentação.</span><span class="sxs-lookup"><span data-stu-id="2af79-181">This is crucial, especially since many users treat sample code as documentation.</span></span>

- <span data-ttu-id="2af79-182">Em primeiro lugar, deve determinar os exemplos que serão incluídos com o módulo – no mínimo, deve abranger os casos de utilização mais importantes para o seu recurso:</span><span class="sxs-lookup"><span data-stu-id="2af79-182">First, you should determine the examples that will be included with the module – at minimum, you should cover most important use cases for your resource:</span></span>
- <span data-ttu-id="2af79-183">Se o seu módulo contém vários recursos que precisam para trabalharem em conjunto para um cenário ponto-a-ponto, o exemplo básico do ponto-a-ponto ideal seria ter primeiro.</span><span class="sxs-lookup"><span data-stu-id="2af79-183">If your module contains several resources that need to work together for an end-to-end scenario, the basic end-to-end example would ideally be first.</span></span>
- <span data-ttu-id="2af79-184">Os exemplos iniciais devem ser muito simples – como começar com os seus recursos em pequenas partes gerenciáveis (por exemplo, criar um novo VHD)</span><span class="sxs-lookup"><span data-stu-id="2af79-184">The initial examples should be very simple -- how to get started with your resources in small manageable chunks (e.g. creating a new VHD)</span></span>
- <span data-ttu-id="2af79-185">Exemplos de subsequentes devem compilar nesses exemplos (por exemplo, criar uma VM a partir de um VHD, remover a VM, VM de modificação) e mostrar funcionalidades avançadas (por exemplo, criar uma VM com a memória dinâmica)</span><span class="sxs-lookup"><span data-stu-id="2af79-185">Subsequent examples should build on those examples (e.g. creating a VM from a VHD, removing VM, modifying VM), and show advanced functionality (e.g. creating a VM with dynamic memory)</span></span>
- <span data-ttu-id="2af79-186">As configurações de exemplo devem ser parametrizadas (todos os valores devem ser passados para a configuração como parâmetros e não deve haver nenhum valores embutidos em código):</span><span class="sxs-lookup"><span data-stu-id="2af79-186">Example configurations should be parameterized (all values should be passed to the configuration as parameters and there should be no hardcoded values):</span></span>

  ```powershell
  configuration Sample_xRemoteFile_DownloadFile
  {
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
  }
  ```

- <span data-ttu-id="2af79-187">É uma boa prática para incluir (comentado horizontalmente) de exemplo de como chamar a configuração com os valores reais no final do script de exemplo.</span><span class="sxs-lookup"><span data-stu-id="2af79-187">It’s a good practice to include (commented out) example of how to call the configuration with the actual values at the end of the example script.</span></span>
  <span data-ttu-id="2af79-188">Por exemplo, na configuração acima não é necessariamente óbvio que é a melhor maneira de especificar UserAgent:</span><span class="sxs-lookup"><span data-stu-id="2af79-188">For example, in the configuration above it isn't necessarily obvious that the best way to specify UserAgent is:</span></span>

  <span data-ttu-id="2af79-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` Caso em que um comentário pode esclarecer a execução pretendida da configuração:</span><span class="sxs-lookup"><span data-stu-id="2af79-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In which case a comment can clarify the intended execution of the configuration:</span></span>

  ```powershell
  <#
  Sample use (parameter values need to be changed according to your scenario):

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
  -userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
  #>
  ```

- <span data-ttu-id="2af79-190">Para cada exemplo, escreva uma descrição breve que explica o que ele faz e o significado dos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="2af79-190">For each example, write a short description which explains what it does, and the meaning of the parameters.</span></span>
- <span data-ttu-id="2af79-191">Certifique-se exemplos abrangem a maioria dos cenários importantes para o seu recurso e se não há nada em falta, certifique-se de que todos são executados e colocar a máquina do estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="2af79-191">Make sure examples cover most the important scenarios for your resource and if there’s nothing missing, verify that they all execute and put machine in the desired state.</span></span>

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a><span data-ttu-id="2af79-192">Mensagens de erro são fáceis de compreender e ajudar os utilizadores a resolver problemas</span><span class="sxs-lookup"><span data-stu-id="2af79-192">Error messages are easy to understand and help users solve problems</span></span>

<span data-ttu-id="2af79-193">Boas mensagens de erro devem ser:</span><span class="sxs-lookup"><span data-stu-id="2af79-193">Good error messages should be:</span></span>

- <span data-ttu-id="2af79-194">Daí: O maior problema com mensagens de erro é que, muitas vezes, não existem, por isso, certifique-se de que eles estão lá.</span><span class="sxs-lookup"><span data-stu-id="2af79-194">There: The biggest problem with error messages is that they often don’t exist, so make sure they are there.</span></span>
- <span data-ttu-id="2af79-195">Fácil de compreender: Códigos de erro de leitura e não obscuro humano</span><span class="sxs-lookup"><span data-stu-id="2af79-195">Easy to understand: Human readable, no obscure error codes</span></span>
- <span data-ttu-id="2af79-196">Preciso: Descrever o que é exatamente o problema</span><span class="sxs-lookup"><span data-stu-id="2af79-196">Precise: Describe what’s exactly the problem</span></span>
- <span data-ttu-id="2af79-197">Construtivos: Conselhos sobre como resolver o problema</span><span class="sxs-lookup"><span data-stu-id="2af79-197">Constructive: Advice how to fix the issue</span></span>
- <span data-ttu-id="2af79-198">Educado: Não o culparia usuário ou torná-los a se aflija</span><span class="sxs-lookup"><span data-stu-id="2af79-198">Polite: Don’t blame user or make them feel bad</span></span>

<span data-ttu-id="2af79-199">Certifique-se de verificar a erros em cenários de ponto a ponto (usando `Start-DscConfiguration`), porque eles podem ser diferentes das devolvido ao executar as funções de recurso diretamente.</span><span class="sxs-lookup"><span data-stu-id="2af79-199">Make sure you verify errors in End to End scenarios (using `Start-DscConfiguration`), because they may differ from those returned when running resource functions directly.</span></span>

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a><span data-ttu-id="2af79-200">Mensagens de registo são fáceis de compreender e informativos (incluindo – verboso, – depuração e os registos ETW)</span><span class="sxs-lookup"><span data-stu-id="2af79-200">Log messages are easy to understand and informative (including –verbose, –debug and ETW logs)</span></span>

<span data-ttu-id="2af79-201">Certifique-se de que registos produzidos pelo recurso são fáceis de compreender e fornecer valor ao utilizador.</span><span class="sxs-lookup"><span data-stu-id="2af79-201">Ensure that logs outputted by the resource are easy to understand and provide value to the user.</span></span> <span data-ttu-id="2af79-202">Recursos devem produzir todas as informações que poderão ser úteis para os utilizadores, mas os registos mais nem sempre é melhor.</span><span class="sxs-lookup"><span data-stu-id="2af79-202">Resources should output all information which might be helpful to the user, but more logs is not always better.</span></span> <span data-ttu-id="2af79-203">Deve evitar redundância e saída de dados que não agregam valor adicional ao – não faça alguém passar por centenas de entradas de registo para encontrar aquilo procura.</span><span class="sxs-lookup"><span data-stu-id="2af79-203">You should avoid redundancy and outputting data which does not provide additional value – don’t make someone go through hundreds of log entries in order to find what they're looking for.</span></span> <span data-ttu-id="2af79-204">É claro, não existem registos não é uma solução aceitável para este problema seja.</span><span class="sxs-lookup"><span data-stu-id="2af79-204">Of course, no logs is not an acceptable solution for this problem either.</span></span>

<span data-ttu-id="2af79-205">Ao testar, também deve analisar verboso e registos de depuração (executando `Start-DscConfiguration` com `–Verbose` e `–Debug` muda adequadamente), bem como os registos ETW.</span><span class="sxs-lookup"><span data-stu-id="2af79-205">When testing, you should also analyze verbose and debug logs (by running `Start-DscConfiguration` with `–Verbose` and `–Debug` switches appropriately), as well as ETW logs.</span></span> <span data-ttu-id="2af79-206">Para ver os registos DSC ETW, vá para o Visualizador de eventos e abra a seguinte pasta: Aplicações e serviços - Microsoft - Windows - Desired State Configuration.</span><span class="sxs-lookup"><span data-stu-id="2af79-206">To see DSC ETW logs, go to Event Viewer and open the following folder: Applications and Services- Microsoft - Windows - Desired State Configuration.</span></span>  <span data-ttu-id="2af79-207">Por predefinição lá irá ser canal operacional, mas certifique-se de ativar a análise e depurar canais antes de executar a configuração.</span><span class="sxs-lookup"><span data-stu-id="2af79-207">By default there will be Operational channel, but make sure you enable Analytic and Debug channels before running the configuration.</span></span>
<span data-ttu-id="2af79-208">Para ativar canais analíticos/depuração, pode executar o script abaixo:</span><span class="sxs-lookup"><span data-stu-id="2af79-208">To enable Analytic/Debug channels, you can execute script below:</span></span>

```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a><span data-ttu-id="2af79-209">Implementação de recursos não contém caminhos codificados</span><span class="sxs-lookup"><span data-stu-id="2af79-209">Resource implementation does not contain hardcoded paths</span></span>

<span data-ttu-id="2af79-210">Certifique-se não há nenhum caminho codificado na implementação de recursos, especialmente se partem do princípio de idioma (en-us), ou quando existem variáveis de sistema que podem ser utilizadas.</span><span class="sxs-lookup"><span data-stu-id="2af79-210">Ensure there are no hardcoded paths in the resource implementation, particularly if they assume language (en-us), or when there are system variables that can be used.</span></span>
<span data-ttu-id="2af79-211">Se precisar do recurso aceder aos caminhos específicos, utilize as variáveis de ambiente em vez de codificar o caminho, porque ele poderá ser diferente em outras máquinas.</span><span class="sxs-lookup"><span data-stu-id="2af79-211">If your resource need to access specific paths, use environment variables instead of hardcoding the path, as it may differ on other machines.</span></span>

<span data-ttu-id="2af79-212">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="2af79-212">Example:</span></span>

<span data-ttu-id="2af79-213">Em vez de:</span><span class="sxs-lookup"><span data-stu-id="2af79-213">Instead of:</span></span>

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

<span data-ttu-id="2af79-214">Pode escrever:</span><span class="sxs-lookup"><span data-stu-id="2af79-214">You can write:</span></span>

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a><span data-ttu-id="2af79-215">Implementação de recursos não contém informações de utilizador</span><span class="sxs-lookup"><span data-stu-id="2af79-215">Resource implementation does not contain user information</span></span>

<span data-ttu-id="2af79-216">Certifique-se de que não são nomes de e-mail, as informações da conta ou nomes de pessoas no código.</span><span class="sxs-lookup"><span data-stu-id="2af79-216">Make sure there are no email names, account information, or names of people in the code.</span></span>

## <a name="resource-was-tested-with-validinvalid-credentials"></a><span data-ttu-id="2af79-217">Recurso foi testado com credenciais válidas/inválido</span><span class="sxs-lookup"><span data-stu-id="2af79-217">Resource was tested with valid/invalid credentials</span></span>

<span data-ttu-id="2af79-218">Se o seu recurso usa uma credencial como parâmetro:</span><span class="sxs-lookup"><span data-stu-id="2af79-218">If your resource takes a credential as parameter:</span></span>

- <span data-ttu-id="2af79-219">Verifique se o recurso funciona quando o sistema Local (ou a conta de computador para recursos remotos) não tem acesso.</span><span class="sxs-lookup"><span data-stu-id="2af79-219">Verify the resource works when Local System (or the computer account for remote resources) does not have access.</span></span>
- <span data-ttu-id="2af79-220">Certifique-se de que a funciona de recursos com uma credencial especificada para obter, definir e teste</span><span class="sxs-lookup"><span data-stu-id="2af79-220">Verify the resource works with a credential specified for Get, Set and Test</span></span>
- <span data-ttu-id="2af79-221">Se o recurso aceder a partilhas, teste todas as variantes que tem de suportar, tais como:</span><span class="sxs-lookup"><span data-stu-id="2af79-221">If your resource accesses shares, test all the variants you need to support, such as:</span></span>
  - <span data-ttu-id="2af79-222">Partilhas de padrão do windows.</span><span class="sxs-lookup"><span data-stu-id="2af79-222">Standard windows shares.</span></span>
  - <span data-ttu-id="2af79-223">Partilhas DFS.</span><span class="sxs-lookup"><span data-stu-id="2af79-223">DFS shares.</span></span>
  - <span data-ttu-id="2af79-224">Partilhas do SAMBA (se quiser suporte Linux.)</span><span class="sxs-lookup"><span data-stu-id="2af79-224">SAMBA shares (if you want to support Linux.)</span></span>

## <a name="resource-does-not-require-interactive-input"></a><span data-ttu-id="2af79-225">Recurso não necessita de entrada interativa</span><span class="sxs-lookup"><span data-stu-id="2af79-225">Resource does not require interactive input</span></span>

<span data-ttu-id="2af79-226">**Get/Set/teste-TargetResource** funções deve ser executadas automaticamente e não terá de aguardar para a entrada do utilizador em qualquer fase de execução (por exemplo, não deve usar `Get-Credential` dentro dessas funções).</span><span class="sxs-lookup"><span data-stu-id="2af79-226">**Get/Set/Test-TargetResource** functions should be executed automatically and must not wait for user’s input at any stage of execution (e.g. you should not use `Get-Credential` inside these functions).</span></span> <span data-ttu-id="2af79-227">Se precisar de fornecer a entrada do usuário, deve passá-lo para a configuração como parâmetro durante a fase de compilação.</span><span class="sxs-lookup"><span data-stu-id="2af79-227">If you need to provide user’s input, you should pass it to the configuration as parameter during the compilation phase.</span></span>

## <a name="resource-functionality-was-thoroughly-tested"></a><span data-ttu-id="2af79-228">Funcionalidade de recursos foi totalmente testada</span><span class="sxs-lookup"><span data-stu-id="2af79-228">Resource functionality was thoroughly tested</span></span>

<span data-ttu-id="2af79-229">Esta lista de verificação contém itens que são importantes a serem testados e/ou muitas vezes seja perdidas.</span><span class="sxs-lookup"><span data-stu-id="2af79-229">This checklist contains items which are important to be tested and/or are often missed.</span></span> <span data-ttu-id="2af79-230">Haverá vários testes, principalmente aqueles funcionais que serão específicos para o recurso estiver a testar e não são mencionadas aqui.</span><span class="sxs-lookup"><span data-stu-id="2af79-230">There will be bunch of tests, mainly functional ones which will be specific to the resource you are testing and are not mentioned here.</span></span> <span data-ttu-id="2af79-231">Não se esqueça de sobre casos de teste negativos.</span><span class="sxs-lookup"><span data-stu-id="2af79-231">Don’t forget about negative test cases.</span></span>

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a><span data-ttu-id="2af79-232">Prática recomendada: Módulo de recursos contém a pasta de testes com ResourceDesignerTests.ps1 script</span><span class="sxs-lookup"><span data-stu-id="2af79-232">Best practice: Resource module contains Tests folder with ResourceDesignerTests.ps1 script</span></span>

<span data-ttu-id="2af79-233">É uma boa prática para criar a pasta "testes" no módulo de recursos, crie `ResourceDesignerTests.ps1` de ficheiros e adicionar testes usando **teste xDscResource** e **teste xDscSchema** para todos os recursos em determinados módulo.</span><span class="sxs-lookup"><span data-stu-id="2af79-233">It’s a good practice to create folder “Tests” inside resource module, create `ResourceDesignerTests.ps1` file and add tests using **Test-xDscResource** and **Test-xDscSchema** for all resources in given module.</span></span>
<span data-ttu-id="2af79-234">Dessa forma pode validar rapidamente esquemas de todos os recursos dos módulos de determinado e fazer uma sanidade verificar antes de publicar.</span><span class="sxs-lookup"><span data-stu-id="2af79-234">This way you can quickly validate schemas of all resources from the given modules and do a sanity check before publishing.</span></span>
<span data-ttu-id="2af79-235">Para xRemoteFile, `ResourceTests.ps1` pode ter um aspeto tão simples como:</span><span class="sxs-lookup"><span data-stu-id="2af79-235">For xRemoteFile, `ResourceTests.ps1` could look as simple as:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a><span data-ttu-id="2af79-236">Prática recomendada: Pasta de recurso contém o script do estruturador de recurso para gerar esquema</span><span class="sxs-lookup"><span data-stu-id="2af79-236">Best practice: Resource folder contains resource designer script for generating schema</span></span>

<span data-ttu-id="2af79-237">Cada recurso deve conter um script de designer de recursos que gera um esquema de mof do recurso.</span><span class="sxs-lookup"><span data-stu-id="2af79-237">Each resource should contain a resource designer script which generates a mof schema of the resource.</span></span> <span data-ttu-id="2af79-238">Este ficheiro deve ser colocado na `<ResourceName>\ResourceDesignerScripts` e ter o nome gerar `<ResourceName>Schema.ps1` para o recurso de xRemoteFile este ficheiro seria chamado `GenerateXRemoteFileSchema.ps1` e conter:</span><span class="sxs-lookup"><span data-stu-id="2af79-238">This file should be placed in `<ResourceName>\ResourceDesignerScripts` and be named Generate `<ResourceName>Schema.ps1` For xRemoteFile resource this file would be called `GenerateXRemoteFileSchema.ps1` and contain:</span></span>

```powershell
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.'
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile
```

## <a name="best-practice-resource-supports--whatif"></a><span data-ttu-id="2af79-239">Prática recomendada: -WhatIf oferece suporte a recursos</span><span class="sxs-lookup"><span data-stu-id="2af79-239">Best practice: Resource supports -WhatIf</span></span>

<span data-ttu-id="2af79-240">Se o recurso está a efetuar operações de "perigosas", é uma boa prática para implementar `-WhatIf` funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="2af79-240">If your resource is performing “dangerous” operations, it’s a good practice to implement `-WhatIf` functionality.</span></span> <span data-ttu-id="2af79-241">Depois de terminar, certifique-se de que `-WhatIf` saída corretamente descreve as operações que acontecem se o comando foi executado sem `-WhatIf` mudar.</span><span class="sxs-lookup"><span data-stu-id="2af79-241">After it’s done, make sure that `-WhatIf` output correctly describes operations which would happen if command was executed without `-WhatIf` switch.</span></span>
<span data-ttu-id="2af79-242">Além disso, certifique-se de que as operações não é executado (não para o estado do nó são feitas alterações) quando `–WhatIf` comutador está presente.</span><span class="sxs-lookup"><span data-stu-id="2af79-242">Also, verify that operations does not execute (no changes to the node’s state are made) when `–WhatIf` switch is present.</span></span>
<span data-ttu-id="2af79-243">Por exemplo, vamos supor que está a testar o recurso de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="2af79-243">For example, let’s assume we are testing File resource.</span></span> <span data-ttu-id="2af79-244">Segue-se configuração simples que cria o ficheiro `test.txt` com conteúdo "teste":</span><span class="sxs-lookup"><span data-stu-id="2af79-244">Below is simple configuration which creates file `test.txt` with contents “test”:</span></span>

```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```

<span data-ttu-id="2af79-245">Se vamos compilar e, em seguida, executar a configuração com o `-WhatIf` comutador, a saída é a indicar exatamente o que aconteceria quando executamos a configuração.</span><span class="sxs-lookup"><span data-stu-id="2af79-245">If we compile and then execute the configuration with the `-WhatIf` switch, the output is telling us exactly what would happen when we run the configuration.</span></span> <span data-ttu-id="2af79-246">A configuração do próprio no entanto não foi executada (`test.txt` ficheiro não foi criado).</span><span class="sxs-lookup"><span data-stu-id="2af79-246">The configuration itself however was not executed (`test.txt` file was not created).</span></span>

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```output
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="2af79-247">Esta lista não é exaustiva, mas abrange vários problemas importantes que podem ser encontrados durante a criação, desenvolvimento e teste de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="2af79-247">This list is not exhaustive, but it covers many important issues which can be encountered while designing, developing and testing DSC resources.</span></span>