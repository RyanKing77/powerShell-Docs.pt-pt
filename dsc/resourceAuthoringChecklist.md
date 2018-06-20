---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Lista de verificação de criação de recursos
ms.openlocfilehash: 76d9fecca8618fcc178975465f45cda0d0e04064
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189963"
---
# <a name="resource-authoring-checklist"></a><span data-ttu-id="0cc53-103">Lista de verificação de criação de recursos</span><span class="sxs-lookup"><span data-stu-id="0cc53-103">Resource authoring checklist</span></span>
<span data-ttu-id="0cc53-104">Esta lista de verificação se uma lista de melhores práticas quando criar um novo recurso do DSC.</span><span class="sxs-lookup"><span data-stu-id="0cc53-104">This checklist is a list of best practices when authoring a new DSC Resource.</span></span>
## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a><span data-ttu-id="0cc53-105">Módulo de recursos contém ficheiros. psd1 e schema.mof para cada recurso</span><span class="sxs-lookup"><span data-stu-id="0cc53-105">Resource module contains .psd1 file and schema.mof for every resource</span></span>
<span data-ttu-id="0cc53-106">Certifique-se de que o recurso tem estrutura correta e contém todos os ficheiros necessários.</span><span class="sxs-lookup"><span data-stu-id="0cc53-106">Check that your resource has correct structure and contains all required files.</span></span> <span data-ttu-id="0cc53-107">Cada módulo de recurso deve conter um ficheiro. psd1 e todos os recursos de compostos não devem ter schema.mof ficheiro.</span><span class="sxs-lookup"><span data-stu-id="0cc53-107">Every resource module should contain a .psd1 file and every non-composite resource should have schema.mof file.</span></span> <span data-ttu-id="0cc53-108">Recursos que contém o esquema não serão listados por **Get-DscResource** e os utilizadores não poderão utilizar o intellisense ao escrever código contra os módulos no ISE.</span><span class="sxs-lookup"><span data-stu-id="0cc53-108">Resources that do not contain schema will not be listed by **Get-DscResource** and users will not be able to use the intellisense when writing code against those modules in ISE.</span></span>
<span data-ttu-id="0cc53-109">A estrutura de diretórios para xRemoteFile recurso, o que faz parte do [módulo de recurso xPSDesiredStateConfiguration](https://github.com/PowerShell/xPSDesiredStateConfiguration), procura da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0cc53-109">The directory structure for xRemoteFile resource, which is part of the [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), looks as follows:</span></span>


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

## <a name="resource-and-schema-are-correct"></a><span data-ttu-id="0cc53-110">Recursos e de esquema estão corretos # #</span><span class="sxs-lookup"><span data-stu-id="0cc53-110">Resource and schema are correct##</span></span>
<span data-ttu-id="0cc53-111">Verifique o esquema de recursos (\*. schema.mof) ficheiros.</span><span class="sxs-lookup"><span data-stu-id="0cc53-111">Verify the resource schema (\*.schema.mof) file.</span></span> <span data-ttu-id="0cc53-112">Pode utilizar o [Designer de recursos de DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) para ajudar a desenvolver e testar o esquema.</span><span class="sxs-lookup"><span data-stu-id="0cc53-112">You can use the [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) to help develop and test your schema.</span></span>
<span data-ttu-id="0cc53-113">Certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="0cc53-113">Make sure that:</span></span>
- <span data-ttu-id="0cc53-114">Tipos de propriedade são corretos (por exemplo, não utilize cadeia para propriedades que aceitam valores numéricos, deve utilizar UInt32 ou outros tipos numéricos em vez disso)</span><span class="sxs-lookup"><span data-stu-id="0cc53-114">Property types are correct (e.g. don’t use String for properties which accept numeric values, you should use UInt32 or other numeric types instead)</span></span>
- <span data-ttu-id="0cc53-115">Atributos de propriedade estão corretamente especificados como: ([chave], [necessário], [escrever], [ler])</span><span class="sxs-lookup"><span data-stu-id="0cc53-115">Property attributes are specified correctly as: ([key], [required], [write], [read])</span></span>
- <span data-ttu-id="0cc53-116">Pelo menos um parâmetro no esquema tem de ser marcado como [chave]</span><span class="sxs-lookup"><span data-stu-id="0cc53-116">At least one parameter in the schema has to be marked as [key]</span></span>
- <span data-ttu-id="0cc53-117">[ler] propriedade não coexistir juntamente com qualquer um dos: [necessário], [a chave], [escrever]</span><span class="sxs-lookup"><span data-stu-id="0cc53-117">[read] property does not coexist together with any of: [required], [key], [write]</span></span>
- <span data-ttu-id="0cc53-118">Se forem especificadas várias qualificadores exceto [leitura], [a chave] tem precedência</span><span class="sxs-lookup"><span data-stu-id="0cc53-118">If multiple qualifiers are specified except [read], then [key] takes precedence</span></span>
- <span data-ttu-id="0cc53-119">Se [escrever] e [necessário] especificado, em seguida, tem precedência [necessário]</span><span class="sxs-lookup"><span data-stu-id="0cc53-119">If [write] and [required] are specified, then [required] takes precedence</span></span>
- <span data-ttu-id="0cc53-120">ValueMap especificado apropriado</span><span class="sxs-lookup"><span data-stu-id="0cc53-120">ValueMap is specified where appropriate</span></span>

<span data-ttu-id="0cc53-121">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="0cc53-121">Example:</span></span>
```
[Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
```

- <span data-ttu-id="0cc53-122">Nome amigável for especificado e confirma para as convenções de nomenclatura de DSC</span><span class="sxs-lookup"><span data-stu-id="0cc53-122">Friendly name is specified and confirms to DSC naming conventions</span></span>

<span data-ttu-id="0cc53-123">Exemplo: ```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```</span><span class="sxs-lookup"><span data-stu-id="0cc53-123">Example: ```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```</span></span>

- <span data-ttu-id="0cc53-124">Cada campo tem uma descrição com significado.</span><span class="sxs-lookup"><span data-stu-id="0cc53-124">Every field has meaningful description.</span></span> <span data-ttu-id="0cc53-125">O repositório do PowerShell GitHub tem bons exemplos, tais como [o. schema.mof para xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span><span class="sxs-lookup"><span data-stu-id="0cc53-125">The PowerShell GitHub repository has good examples, such as [the .schema.mof for xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span></span>

<span data-ttu-id="0cc53-126">Além disso, deve utilizar **teste xDscResource** e **teste xDscSchema** os cmdlets da [Designer de recursos de DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) para verificar automaticamente o recurso e o esquema:</span><span class="sxs-lookup"><span data-stu-id="0cc53-126">Additionally, you should use **Test-xDscResource** and **Test-xDscSchema** cmdlets from [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) to automatically verify the resource and schema:</span></span>
```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```
<span data-ttu-id="0cc53-127">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0cc53-127">For example:</span></span>
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a><span data-ttu-id="0cc53-128">Recurso carrega sem erros</span><span class="sxs-lookup"><span data-stu-id="0cc53-128">Resource loads without errors</span></span> ##
<span data-ttu-id="0cc53-129">Verifique se o módulo de recurso pode ser carregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="0cc53-129">Check whether the resource module can be successfully loaded.</span></span>
<span data-ttu-id="0cc53-130">Isto pode ser conseguido manualmente, executando `Import-Module <resource_module> -force ` e confirmar que ocorreram sem erros ou ao escrever a automatização de teste.</span><span class="sxs-lookup"><span data-stu-id="0cc53-130">This can be achieved manually, by running `Import-Module <resource_module> -force ` and confirming that no errors occurred, or by writing test automation.</span></span> <span data-ttu-id="0cc53-131">Em caso desta última opção, pode seguir esta estrutura no seu caso de teste:</span><span class="sxs-lookup"><span data-stu-id="0cc53-131">In case of the latter, you can follow this structure in your test case:</span></span>
```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```
## <a name="resource-is-idempotent-in-the-positive-case"></a><span data-ttu-id="0cc53-132">Recurso é idempotent no caso de positivo</span><span class="sxs-lookup"><span data-stu-id="0cc53-132">Resource is idempotent in the positive case</span></span>
<span data-ttu-id="0cc53-133">Uma das características fundamentais de recursos de DSC está a ser idempotence.</span><span class="sxs-lookup"><span data-stu-id="0cc53-133">One of the fundamental characteristics of DSC resources is be idempotence.</span></span> <span data-ttu-id="0cc53-134">Significa que aplicar uma configuração de DSC que contém esse recurso várias vezes será sempre alcançar o mesmo resultado.</span><span class="sxs-lookup"><span data-stu-id="0cc53-134">It means that applying a DSC configuration containing that resource multiple times will always achieve the same result.</span></span> <span data-ttu-id="0cc53-135">Por exemplo, vamos criar uma configuração que contém o seguinte recurso do ficheiro:</span><span class="sxs-lookup"><span data-stu-id="0cc53-135">For example, if we create a configuration which contains the following File resource:</span></span>
```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```
<span data-ttu-id="0cc53-136">Depois de aplicá-la pela primeira vez, deverá aparecer test.txt de ficheiro na pasta C:\test.</span><span class="sxs-lookup"><span data-stu-id="0cc53-136">After applying it for the first time, file test.txt should appear in C:\test folder.</span></span> <span data-ttu-id="0cc53-137">No entanto, as execuções subsequentes da configuração da mesma não devem alterar o estado da máquina (por exemplo, não existem cópias do ficheiro test.txt devem ser criadas).</span><span class="sxs-lookup"><span data-stu-id="0cc53-137">However, subsequent runs of the same configuration should not change the state of the machine (e.g. no copies of the test.txt file should be created).</span></span>
<span data-ttu-id="0cc53-138">Para garantir a um recurso idempotent repetidamente pode chamar **conjunto TargetResource** quando testar o recurso diretamente ou chamar **início DscConfiguration** várias vezes ao fazer o teste de ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="0cc53-138">To ensure a resource is idempotent you can repeatedly call **Set-TargetResource** when testing the resource directly, or call **Start-DscConfiguration** multiple times when doing end to end testing.</span></span> <span data-ttu-id="0cc53-139">O resultado deve ser o mesmo após cada execução.</span><span class="sxs-lookup"><span data-stu-id="0cc53-139">The result should be the same after every run.</span></span>


## <a name="test-user-modification-scenario"></a><span data-ttu-id="0cc53-140">Cenário de modificação de utilizador de teste</span><span class="sxs-lookup"><span data-stu-id="0cc53-140">Test user modification scenario</span></span> ##
<span data-ttu-id="0cc53-141">Ao alterar o estado da máquina e, em seguida, volte a executar DSC, pode verificar que **conjunto TargetResource** e **teste TargetResource** funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="0cc53-141">By changing the state of the machine and then rerunning DSC, you can verify that **Set-TargetResource** and **Test-TargetResource** function properly.</span></span> <span data-ttu-id="0cc53-142">Seguem-se passos que deve tomar:</span><span class="sxs-lookup"><span data-stu-id="0cc53-142">Here are steps you should take:</span></span>
1.  <span data-ttu-id="0cc53-143">Começar a utilizar o recurso não no estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="0cc53-143">Start with the resource not in the desired state.</span></span>
2.  <span data-ttu-id="0cc53-144">Execute a configuração com o seu recurso</span><span class="sxs-lookup"><span data-stu-id="0cc53-144">Run configuration with your resource</span></span>
3.  <span data-ttu-id="0cc53-145">Certifique-se **teste DscConfiguration** devolve True</span><span class="sxs-lookup"><span data-stu-id="0cc53-145">Verify **Test-DscConfiguration** returns True</span></span>
4.  <span data-ttu-id="0cc53-146">Modificar o item configurado para ser fora do estado pretendido</span><span class="sxs-lookup"><span data-stu-id="0cc53-146">Modify the configured item to be out of the desired state</span></span>
5.  <span data-ttu-id="0cc53-147">Certifique-se **teste DscConfiguration** devolve false Eis um exemplo mais concreto através de recursos de registo:</span><span class="sxs-lookup"><span data-stu-id="0cc53-147">Verify **Test-DscConfiguration** returns false Here’s a more concrete example using Registry resource:</span></span>
1.  <span data-ttu-id="0cc53-148">Começar a utilizar a chave de registo não no estado pretendido</span><span class="sxs-lookup"><span data-stu-id="0cc53-148">Start with registry key not in the desired state</span></span>
2.  <span data-ttu-id="0cc53-149">Executar **início DscConfiguration** com uma configuração para colocá-la no estado pretendido e certifique-se de passa.</span><span class="sxs-lookup"><span data-stu-id="0cc53-149">Run **Start-DscConfiguration** with a configuration to put it in the desired state and verify it passes.</span></span>
3.  <span data-ttu-id="0cc53-150">Executar **teste DscConfiguration** e certifique-se de que devolve true</span><span class="sxs-lookup"><span data-stu-id="0cc53-150">Run **Test-DscConfiguration** and verify it returns true</span></span>
4.  <span data-ttu-id="0cc53-151">Modifique o valor da chave para que não esteja no estado pretendido</span><span class="sxs-lookup"><span data-stu-id="0cc53-151">Modify the value of the key so that it is not in the desired state</span></span>
5.  <span data-ttu-id="0cc53-152">Executar **teste DscConfiguration** e certifique-se de que devolve false</span><span class="sxs-lookup"><span data-stu-id="0cc53-152">Run **Test-DscConfiguration** and verify it returns false</span></span>
6.  <span data-ttu-id="0cc53-153">Funcionalidade de GET-TargetResource foi verificada através de Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="0cc53-153">Get-TargetResource functionality was verified using Get-DscConfiguration</span></span>

<span data-ttu-id="0cc53-154">Detalhes do estado atual do recurso deve ser devolvido por Get-TargetResource.</span><span class="sxs-lookup"><span data-stu-id="0cc53-154">Get-TargetResource should return details of the current state of the resource.</span></span> <span data-ttu-id="0cc53-155">Certifique-se para testá-lo por Get-DscConfiguration ao chamar depois de aplicar a configuração e a verificar que saída corretamente reflete o estado atual da máquina.</span><span class="sxs-lookup"><span data-stu-id="0cc53-155">Make sure to test it by calling Get-DscConfiguration after you apply the configuration and verifying that output correctly reflects the current state of the machine.</span></span> <span data-ttu-id="0cc53-156">É importante para testá-lo em separado, uma vez que os problemas nesta área deixa de aparecer quando chamar DscConfiguration de início.</span><span class="sxs-lookup"><span data-stu-id="0cc53-156">It's important to test it separately, since any issues in this area won't appear when calling Start-DscConfiguration.</span></span>

## <a name="call-getsettest-targetresource-functions-directly"></a><span data-ttu-id="0cc53-157">Chamar **Get/conjunto/teste-TargetResource** funciona diretamente</span><span class="sxs-lookup"><span data-stu-id="0cc53-157">Call **Get/Set/Test-TargetResource** functions directly</span></span> ##

<span data-ttu-id="0cc53-158">Certifique-se de que testa o **Get/conjunto/teste-TargetResource** funções implementadas no seu recurso pelo diretamente ao chamá-los e verificar que estão a funcionar conforme esperado.</span><span class="sxs-lookup"><span data-stu-id="0cc53-158">Make sure you test the **Get/Set/Test-TargetResource** functions implemented in your resource by calling them directly and verifying that they work as expected.</span></span>

## <a name="verify-end-to-end-using-start-dscconfiguration"></a><span data-ttu-id="0cc53-159">Certifique-se através de ponto a ponto **DscConfiguration de início**</span><span class="sxs-lookup"><span data-stu-id="0cc53-159">Verify End to End using **Start-DscConfiguration**</span></span> ##

<span data-ttu-id="0cc53-160">Testar **Get/conjunto/teste-TargetResource** funções chamando-los diretamente é importante, mas não todos os problemas serão detetados desta forma.</span><span class="sxs-lookup"><span data-stu-id="0cc53-160">Testing **Get/Set/Test-TargetResource** functions by calling them directly is important, but not all issues will be discovered this way.</span></span> <span data-ttu-id="0cc53-161">Deve focar-se parte significativo dos testes no utilizando **início DscConfiguration** ou o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="0cc53-161">You should focus significant part of your testing on using **Start-DscConfiguration** or the pull server.</span></span> <span data-ttu-id="0cc53-162">Na verdade, esta é a forma como os utilizadores utilizarão o recurso de, pelo que não underestimate significância deste tipo de testes.</span><span class="sxs-lookup"><span data-stu-id="0cc53-162">In fact, this is how users will use the resource, so don’t underestimate the significance of this type of tests.</span></span>
<span data-ttu-id="0cc53-163">Tipos possíveis problemas:</span><span class="sxs-lookup"><span data-stu-id="0cc53-163">Possible types of issues:</span></span>
- <span data-ttu-id="0cc53-164">Credenciais/sessão pode comportar-se de forma diferente porque o agente de DSC é executado como um serviço.</span><span class="sxs-lookup"><span data-stu-id="0cc53-164">Credential/Session may behave differently because the DSC agent runs as a service.</span></span>  <span data-ttu-id="0cc53-165">Lembre-se de que testar quaisquer funcionalidades aqui ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="0cc53-165">Be sure to test any features here end to end.</span></span>
- <span data-ttu-id="0cc53-166">Erros de saída por **início DscConfiguration** poderão ser diferentes das apresentado ao chamar o **conjunto TargetResource** diretamente a funcionar.</span><span class="sxs-lookup"><span data-stu-id="0cc53-166">Errors output by **Start-DscConfiguration** may be different than those displayed when calling the **Set-TargetResource** function directly.</span></span>

## <a name="test-compatability-on-all-dsc-supported-platforms"></a><span data-ttu-id="0cc53-167">Teste de compatibilidade no DSC todas as plataformas suportadas</span><span class="sxs-lookup"><span data-stu-id="0cc53-167">Test compatability on all DSC supported platforms</span></span> ##
<span data-ttu-id="0cc53-168">Recursos deverão funcionar em todas as plataformas de DSC suportada (Windows Server 2008 R2 e mais recentes).</span><span class="sxs-lookup"><span data-stu-id="0cc53-168">Resource should work on all DSC supported platforms (Windows Server 2008 R2 and newer).</span></span> <span data-ttu-id="0cc53-169">Instale o WMF mais recente (Windows Management Framework) no seu SO para obter a versão mais recente do DSC.</span><span class="sxs-lookup"><span data-stu-id="0cc53-169">Install the latest WMF (Windows Management Framework) on your OS to get the latest version of DSC.</span></span> <span data-ttu-id="0cc53-170">Se o recurso não funciona em algumas destas plataformas por predefinição, uma mensagem de erro específica deve ser devolvida.</span><span class="sxs-lookup"><span data-stu-id="0cc53-170">If your resource does not work on some of these platforms by design, a specific error message should be returned.</span></span> <span data-ttu-id="0cc53-171">Além disso, certifique-se de que o seu recurso verifica se os cmdlets que são chamar são presentes no computador específico.</span><span class="sxs-lookup"><span data-stu-id="0cc53-171">Also, make sure your resource checks whether cmdlets you are calling are present on particular machine.</span></span> <span data-ttu-id="0cc53-172">Windows Server 2012 adicionados um grande número de novos cmdlets que não estão disponíveis no Windows Server 2008 R2 o, mesmo com WMF instalado.</span><span class="sxs-lookup"><span data-stu-id="0cc53-172">Windows Server 2012 added a large number of new cmdlets that are not available on Windows Server 2008R2, even with WMF installed.</span></span>

## <a name="verify-on-windows-client-if-applicable"></a><span data-ttu-id="0cc53-173">Certifique-se num cliente Windows (se aplicável)</span><span class="sxs-lookup"><span data-stu-id="0cc53-173">Verify on Windows Client (if applicable)</span></span> ##
<span data-ttu-id="0cc53-174">Um intervalo de teste muito comum está a verificar o recurso apenas em versões de servidor do Windows.</span><span class="sxs-lookup"><span data-stu-id="0cc53-174">One very common test gap is verifying the resource only on server versions of Windows.</span></span> <span data-ttu-id="0cc53-175">Muitos recursos também foram concebidos para funcionar no SKUs de cliente, para que o se o que acontece no seu caso, não se esqueça de testá-lo no bem essas plataformas.</span><span class="sxs-lookup"><span data-stu-id="0cc53-175">Many resources are also designed to work on Client SKUs, so if that’s true in your case, don’t forget to test it on those platforms as well.</span></span>
## <a name="get-dscresource-lists-the-resource"></a><span data-ttu-id="0cc53-176">Get-DSCResource apresenta uma lista de recursos</span><span class="sxs-lookup"><span data-stu-id="0cc53-176">Get-DSCResource lists the resource</span></span> ##
<span data-ttu-id="0cc53-177">Depois de implementar o módulo, chamar Get-DscResource deve listar o recurso dos restantes como resultado.</span><span class="sxs-lookup"><span data-stu-id="0cc53-177">After deploying the module, calling Get-DscResource should list your resource among others as a result.</span></span> <span data-ttu-id="0cc53-178">Se não é possível localizar o recurso na lista, certifique-se de que o ficheiro schema.mof para esse recurso existe.</span><span class="sxs-lookup"><span data-stu-id="0cc53-178">If you can’t find your resource in the list, make sure that schema.mof file for that resource exists.</span></span>
## <a name="resource-module-contains-examples"></a><span data-ttu-id="0cc53-179">Módulo de recursos contém exemplos</span><span class="sxs-lookup"><span data-stu-id="0cc53-179">Resource module contains examples</span></span> ##
<span data-ttu-id="0cc53-180">Criar exemplos de qualidade que irão ajudar os outros compreender como utilizá-la.</span><span class="sxs-lookup"><span data-stu-id="0cc53-180">Creating quality examples which will help others understand how to use it.</span></span> <span data-ttu-id="0cc53-181">Isto é crucial, especialmente, uma vez que muitos utilizadores tratar código de exemplo como documentação.</span><span class="sxs-lookup"><span data-stu-id="0cc53-181">This is crucial, especially since many users treat sample code as documentation.</span></span>
- <span data-ttu-id="0cc53-182">Em primeiro lugar, deve determinar os exemplos que serão incluídos com o módulo – no mínimo, deve abranger os casos de utilização mais importantes para o seu recurso:</span><span class="sxs-lookup"><span data-stu-id="0cc53-182">First, you should determine the examples that will be included with the module – at minimum, you should cover most important use cases for your resource:</span></span>
- <span data-ttu-id="0cc53-183">Se o módulo contiver vários recursos que necessitam para funcionarem em conjunto para um cenário ponto-a-ponto, o exemplo básico do ponto-a-ponto ideal seria ter primeiro.</span><span class="sxs-lookup"><span data-stu-id="0cc53-183">If your module contains several resources that need to work together for an end-to-end scenario, the basic end-to-end example would ideally be first.</span></span>
- <span data-ttu-id="0cc53-184">Os exemplos iniciais devem ser muito simples – como começar com os recursos em pequenos segmentos geríveis (por exemplo, criar um novo VHD)</span><span class="sxs-lookup"><span data-stu-id="0cc53-184">The initial examples should be very simple -- how to get started with your resources in small manageable chunks (e.g. creating a new VHD)</span></span>
- <span data-ttu-id="0cc53-185">Exemplos subsequentes devem tirar partido dessas exemplos (por exemplo, criar uma VM a partir de um VHD, remover a VM, modificar VM) e mostram a funcionalidade avançada (por exemplo, criar uma VM com memória dinâmica)</span><span class="sxs-lookup"><span data-stu-id="0cc53-185">Subsequent examples should build on those examples (e.g. creating a VM from a VHD, removing VM, modifying VM), and show advanced functionality (e.g. creating a VM with dynamic memory)</span></span>
- <span data-ttu-id="0cc53-186">Configurações de exemplo devem ser parametrizadas (todos os valores devem ser transmitidos para a configuração como parâmetros e não deverá haver nenhum valores codificado):</span><span class="sxs-lookup"><span data-stu-id="0cc53-186">Example configurations should be parameterized (all values should be passed to the configuration as parameters and there should be no hardcoded values):</span></span>
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
- <span data-ttu-id="0cc53-187">É uma boa prática incluir (comentado out) exemplo de como chamar a configuração com os valores reais no final do script de exemplo.</span><span class="sxs-lookup"><span data-stu-id="0cc53-187">It’s a good practice to include (commented out) example of how to call the configuration with the actual values at the end of the example script.</span></span>
<span data-ttu-id="0cc53-188">Por exemplo, na configuração acima não se encontra necessariamente óbvios que é a melhor forma de o especificar UserAgent:</span><span class="sxs-lookup"><span data-stu-id="0cc53-188">For example, in the configuration above it isn't neccessarily obvious that the best way to specify UserAgent is:</span></span>

<span data-ttu-id="0cc53-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` Caso em que um comentário pode clarificar a execução da configuração pretendida:</span><span class="sxs-lookup"><span data-stu-id="0cc53-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In which case a comment can clarify the intended execution of the configuration:</span></span>
```
<#
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>
```
- <span data-ttu-id="0cc53-190">Para cada exemplo, escreva uma breve descrição que explica o que faz e o significado dos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="0cc53-190">For each example, write a short description which explains what it does, and the meaning of the parameters.</span></span>
- <span data-ttu-id="0cc53-191">Certifique-se exemplos abrangem a maioria dos cenários importantes para o seu recurso e se não há nada em falta, certifique-se de que todos os executar e colocar a máquina no estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="0cc53-191">Make sure examples cover most the important scenarios for your resource and if there’s nothing missing, verify that they all execute and put machine in the desired state.</span></span>

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a><span data-ttu-id="0cc53-192">Mensagens de erro são fáceis de compreender e ajudar utilizadores a resolver problemas</span><span class="sxs-lookup"><span data-stu-id="0cc53-192">Error messages are easy to understand and help users solve problems</span></span> ##
<span data-ttu-id="0cc53-193">Mensagens de erro boa devem ser:</span><span class="sxs-lookup"><span data-stu-id="0cc53-193">Good error messages should be:</span></span>
- <span data-ttu-id="0cc53-194">Não existe: O problema maior com mensagens de erro é que não existem muitas vezes, por isso, certifique-se de que existem.</span><span class="sxs-lookup"><span data-stu-id="0cc53-194">There: The biggest problem with error messages is that they often don’t exist, so make sure they are there.</span></span>
- <span data-ttu-id="0cc53-195">Fácil de compreender: códigos de erros humanos legível, não obscura</span><span class="sxs-lookup"><span data-stu-id="0cc53-195">Easy to understand: Human readable, no obscure error codes</span></span>
- <span data-ttu-id="0cc53-196">Preciso: Descrevem o que é exatamente o problema</span><span class="sxs-lookup"><span data-stu-id="0cc53-196">Precise: Describe what’s exactly the problem</span></span>
- <span data-ttu-id="0cc53-197">Constructive: Conselhos saber como corrigir o problema</span><span class="sxs-lookup"><span data-stu-id="0cc53-197">Constructive: Advice how to fix the issue</span></span>
- <span data-ttu-id="0cc53-198">Um: Não blame utilizador ou marca-los sentir incorretos Certifique-se verificar erros em cenários de ponto a ponto (utilizando **início DscConfiguration**), porque diferem das devolvido ao executar diretamente as funções de recursos.</span><span class="sxs-lookup"><span data-stu-id="0cc53-198">Polite: Don’t blame user or make them feel bad Make sure you verify errors in End to End scenarios (using **Start-DscConfiguration**), because they may differ from those returned when running resource functions directly.</span></span>

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a><span data-ttu-id="0cc53-199">Mensagens de registo são fáceis de compreender e informativo (incluindo-verbose,-debug e registos ETW)</span><span class="sxs-lookup"><span data-stu-id="0cc53-199">Log messages are easy to understand and informative (including –verbose, –debug and ETW logs)</span></span> ##
<span data-ttu-id="0cc53-200">Certifique-se de que os registos debitados pelo recurso são fáceis de compreender e forneça o valor ao utilizador.</span><span class="sxs-lookup"><span data-stu-id="0cc53-200">Ensure that logs outputted by the resource are easy to understand and provide value to the user.</span></span> <span data-ttu-id="0cc53-201">Recursos devem saída todas as informações que poderão ser úteis para o utilizador, mas mais registos nem sempre é melhor.</span><span class="sxs-lookup"><span data-stu-id="0cc53-201">Resources should output all information which might be helpful to the user, but more logs is not always better.</span></span> <span data-ttu-id="0cc53-202">Deve evitar redundância e exportar dados que não fornecer valor adicional – não se alguém passar por centenas de entradas de registo para encontrar aquilo procura.</span><span class="sxs-lookup"><span data-stu-id="0cc53-202">You should avoid redundancy and outputting data which does not provide additional value – don’t make someone go through hundreds of log entries in order to find what they're looking for.</span></span> <span data-ttu-id="0cc53-203">Obviamente, não existem registos não é uma solução aceitável para este problema seja.</span><span class="sxs-lookup"><span data-stu-id="0cc53-203">Of course, no logs is not an acceptable solution for this problem either.</span></span>

<span data-ttu-id="0cc53-204">Quando o testar, também deve analisar verboso e registos de depuração (executando **início DscConfiguration** com-verbose e – depurar comutadores adequadamente), bem como registos ETW.</span><span class="sxs-lookup"><span data-stu-id="0cc53-204">When testing, you should also analyze verbose and debug logs (by running **Start-DscConfiguration** with –verbose and –debug switches appropriately), as well as ETW logs.</span></span> <span data-ttu-id="0cc53-205">Para ver registos de DSC ETW, aceda ao Visualizador de eventos e abra a seguinte pasta: aplicações e serviços da Microsoft - Windows - configuração de estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="0cc53-205">To see DSC ETW logs, go to Event Viewer and open the following folder: Applications and Services- Microsoft - Windows - Desired State Configuration.</span></span>  <span data-ttu-id="0cc53-206">Por predefinição existe irá ser canal operacional, mas certifique-se de ativar registos analíticos e de depuração canais antes de executar a configuração.</span><span class="sxs-lookup"><span data-stu-id="0cc53-206">By default there will be Operational channel, but make sure you enable Analytic and Debug channels before running the configuration.</span></span>
<span data-ttu-id="0cc53-207">Para ativar registos analíticos/depuração canais, pode executar o script abaixo:</span><span class="sxs-lookup"><span data-stu-id="0cc53-207">To enable Analytic/Debug channels, you can execute script below:</span></span>
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
## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a><span data-ttu-id="0cc53-208">Implementação de recursos não contém codificado caminhos</span><span class="sxs-lookup"><span data-stu-id="0cc53-208">Resource implementation does not contain hardcoded paths</span></span> ##
<span data-ttu-id="0cc53-209">Certifique-se existem não existem caminhos codificado da implementação de recursos, particularmente se estes partem do princípio de idioma (en-us), ou quando existem variáveis do sistema que podem ser utilizadas.</span><span class="sxs-lookup"><span data-stu-id="0cc53-209">Ensure there are no hardcoded paths in the resource implementation, particularly if they assume language (en-us), or when there are system variables that can be used.</span></span>
<span data-ttu-id="0cc53-210">Se o recurso necessário aceder aos caminhos específicos, utilize as variáveis de ambiente em vez de codificar o caminho, dado que pode divergir nas outras máquinas.</span><span class="sxs-lookup"><span data-stu-id="0cc53-210">If your resource need to access specific paths, use environment variables instead of hardcoding the path, as it may differ on other machines.</span></span>

<span data-ttu-id="0cc53-211">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="0cc53-211">Example:</span></span>

<span data-ttu-id="0cc53-212">Em vez de:</span><span class="sxs-lookup"><span data-stu-id="0cc53-212">Instead of:</span></span>
```
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
 ```
<span data-ttu-id="0cc53-213">Pode escrever:</span><span class="sxs-lookup"><span data-stu-id="0cc53-213">You can write:</span></span>
```
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```
## <a name="resource-implementation-does-not-contain-user-information"></a><span data-ttu-id="0cc53-214">Implementação de recursos não contém informações de utilizador</span><span class="sxs-lookup"><span data-stu-id="0cc53-214">Resource implementation does not contain user information</span></span> ##
<span data-ttu-id="0cc53-215">Certificar-se de que não são nomes de e-mail, as informações da conta ou nomes de pessoas no código.</span><span class="sxs-lookup"><span data-stu-id="0cc53-215">Make sure there are no email names, account information, or names of people in the code.</span></span>
## <a name="resource-was-tested-with-validinvalid-credentials"></a><span data-ttu-id="0cc53-216">Recurso foi testado com credenciais válidas/inválido.</span><span class="sxs-lookup"><span data-stu-id="0cc53-216">Resource was tested with valid/invalid credentials</span></span> ##
<span data-ttu-id="0cc53-217">Se o seu recurso aceita uma credencial como parâmetro:</span><span class="sxs-lookup"><span data-stu-id="0cc53-217">If your resource takes a credential as parameter:</span></span>
- <span data-ttu-id="0cc53-218">Certifique-se o recurso funciona quando o sistema Local (ou a conta de computador para recursos remotos) não tem acesso.</span><span class="sxs-lookup"><span data-stu-id="0cc53-218">Verify the resource works when Local System (or the computer account for remote resources) does not have access.</span></span>
- <span data-ttu-id="0cc53-219">Certifique-se de que funciona a recursos com uma credencial especificada para obter, definir e teste</span><span class="sxs-lookup"><span data-stu-id="0cc53-219">Verify the resource works with a credential specified for Get, Set and Test</span></span>
- <span data-ttu-id="0cc53-220">Se o seu recurso acede partilhas, teste todos os variantes que tem de suportar, tais como:</span><span class="sxs-lookup"><span data-stu-id="0cc53-220">If your resource accesses shares, test all the variants you need to support, such as:</span></span>
  - <span data-ttu-id="0cc53-221">Partilhas de padrão do windows.</span><span class="sxs-lookup"><span data-stu-id="0cc53-221">Standard windows shares.</span></span>
  - <span data-ttu-id="0cc53-222">Partilhas DFS.</span><span class="sxs-lookup"><span data-stu-id="0cc53-222">DFS shares.</span></span>
  - <span data-ttu-id="0cc53-223">Partilhas SAMBA (se pretende suportar Linux.)</span><span class="sxs-lookup"><span data-stu-id="0cc53-223">SAMBA shares (if you want to support Linux.)</span></span>

## <a name="resource-does-not-require-interactive-input"></a><span data-ttu-id="0cc53-224">Recurso não necessita de entrada interativa</span><span class="sxs-lookup"><span data-stu-id="0cc53-224">Resource does not require interactive input</span></span> ##
<span data-ttu-id="0cc53-225">**Get/conjunto/teste-TargetResource** funções deve ser executadas automaticamente e não terá de aguardar para o utilizador de entrada em qualquer fase de execução (por exemplo, não deve utilizar **Get-Credential** dentro estas funções).</span><span class="sxs-lookup"><span data-stu-id="0cc53-225">**Get/Set/Test-TargetResource** functions should be executed automatically and must not wait for user’s input at any stage of execution (e.g. you should not use **Get-Credential** inside these functions).</span></span> <span data-ttu-id="0cc53-226">Se necessitar de intervenção do utilizador, deve transmiti-lo para a configuração como parâmetro durante a fase de compilação.</span><span class="sxs-lookup"><span data-stu-id="0cc53-226">If you need to provide user’s input, you should pass it to the configuration as parameter during the compilation phase.</span></span>
## <a name="resource-functionality-was-thoroughly-tested"></a><span data-ttu-id="0cc53-227">Funcionalidade de recurso foi testada exaustivamente</span><span class="sxs-lookup"><span data-stu-id="0cc53-227">Resource functionality was thoroughly tested</span></span> ##
<span data-ttu-id="0cc53-228">Esta lista de verificação contém itens que são importantes para testar e/ou são frequentemente omitidos.</span><span class="sxs-lookup"><span data-stu-id="0cc53-228">This checklist contains items which are important to be tested and/or are often missed.</span></span> <span data-ttu-id="0cc53-229">Será bunch dos testes, principalmente funcionais aqueles que serão específicos para o recurso estiver a testar e não são aqui mencionados.</span><span class="sxs-lookup"><span data-stu-id="0cc53-229">There will be bunch of tests, mainly functional ones which will be specific to the resource you are testing and are not mentioned here.</span></span> <span data-ttu-id="0cc53-230">Não se esqueça sobre casos de teste negativos.</span><span class="sxs-lookup"><span data-stu-id="0cc53-230">Don’t forget about negative test cases.</span></span>
## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a><span data-ttu-id="0cc53-231">Recomendado: módulo de recursos contém a pasta de testes com script de ResourceDesignerTests.ps1</span><span class="sxs-lookup"><span data-stu-id="0cc53-231">Best practice: Resource module contains Tests folder with ResourceDesignerTests.ps1 script</span></span> ##
<span data-ttu-id="0cc53-232">É uma boa prática para criar a pasta "testes" no interior do módulo de recurso, criar ficheiro de ResourceDesignerTests.ps1 e adicionar testes utilizando **teste xDscResource** e **teste xDscSchema** para todos os recursos em determinados módulo.</span><span class="sxs-lookup"><span data-stu-id="0cc53-232">It’s a good practice to create folder “Tests” inside resource module, create ResourceDesignerTests.ps1 file and add tests using **Test-xDscResource** and **Test-xDscSchema** for all resources in given module.</span></span>
<span data-ttu-id="0cc53-233">Desta forma pode validar rapidamente esquemas de todos os recursos dos módulos indicados e efetue uma sanity verificar antes de publicar.</span><span class="sxs-lookup"><span data-stu-id="0cc53-233">This way you can quickly validate schemas of all resources from the given modules and do a sanity check before publishing.</span></span>
<span data-ttu-id="0cc53-234">Para xRemoteFile, ResourceTests.ps1 pode ter um aspeto tão simples como:</span><span class="sxs-lookup"><span data-stu-id="0cc53-234">For xRemoteFile, ResourceTests.ps1 could look as simple as:</span></span>
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```
##<a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a><span data-ttu-id="0cc53-235">Recomendado: a pasta do recurso contém script estruturador do recurso para gerar o esquema # #</span><span class="sxs-lookup"><span data-stu-id="0cc53-235">Best practice: Resource folder contains resource designer script for generating schema##</span></span>
<span data-ttu-id="0cc53-236">Cada recurso deve conter um script de estruturador do recurso que gera um esquema de mof do recurso.</span><span class="sxs-lookup"><span data-stu-id="0cc53-236">Each resource should contain a resource designer script which generates a mof schema of the resource.</span></span> <span data-ttu-id="0cc53-237">Este ficheiro deve ser colocado na <ResourceName>\ResourceDesignerScripts e será nomeado gerar<ResourceName>Schema.ps1 para o recurso de xRemoteFile este ficheiro deverá ser chamado GenerateXRemoteFileSchema.ps1 e conter:</span><span class="sxs-lookup"><span data-stu-id="0cc53-237">This file should be placed in <ResourceName>\ResourceDesignerScripts and be named Generate<ResourceName>Schema.ps1 For xRemoteFile resource this file would be called GenerateXRemoteFileSchema.ps1 and contain:</span></span>
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
## <a name="best-practice-resource-supports--whatif"></a><span data-ttu-id="0cc53-238">Recomendado: recurso suporta - whatif</span><span class="sxs-lookup"><span data-stu-id="0cc53-238">Best practice: Resource supports -whatif</span></span> ##
<span data-ttu-id="0cc53-239">Se o recurso está a efetuar operações "perigosos", é recomendável implementar - whatif funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="0cc53-239">If your resource is performing “dangerous” operations, it’s a good practice to implement -whatif functionality.</span></span> <span data-ttu-id="0cc53-240">Depois de terminar, certifique-se de que a saída de whatif descreve corretamente operações que aconteceria se o comando foi executado sem whatif comutador.</span><span class="sxs-lookup"><span data-stu-id="0cc53-240">After it’s done, make sure that whatif output correctly describes operations which would happen if command was executed without whatif switch.</span></span>
<span data-ttu-id="0cc53-241">Além disso, certifique-se de que não é executado operações (são efetuadas sem alterações para o estado do nó) quando o comutador – whatif está presente.</span><span class="sxs-lookup"><span data-stu-id="0cc53-241">Also, verify that operations does not execute (no changes to the node’s state are made) when –whatif switch is present.</span></span>
<span data-ttu-id="0cc53-242">Por exemplo, vamos supor que iremos estiver a testar o recurso do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="0cc53-242">For example, let’s assume we are testing File resource.</span></span> <span data-ttu-id="0cc53-243">Segue-se configuração simple que cria o ficheiro "test.txt" com conteúdo "teste":</span><span class="sxs-lookup"><span data-stu-id="0cc53-243">Below is simple configuration which creates file “test.txt” with contents “test”:</span></span>
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
<span data-ttu-id="0cc53-244">Se podemos compilar e, em seguida, executar a configuração com o parâmetro – whatif, o resultado é informar-nos exatamente que acontece quando é executada a configuração.</span><span class="sxs-lookup"><span data-stu-id="0cc53-244">If we compile and then execute the configuration with the –whatif switch, the output is telling us exactly what would happen when we run the configuration.</span></span> <span data-ttu-id="0cc53-245">A configuração do próprio no entanto não foi executada (o ficheiro de test.txt não foi criado).</span><span class="sxs-lookup"><span data-stu-id="0cc53-245">The configuration itself however was not executed (test.txt file was not created).</span></span>
```powershell
Start-DscConfiguration -path .\config -ComputerName localhost -wait -verbose -whatif
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

<span data-ttu-id="0cc53-246">Esta lista não é exaustiva, mas abrange a muitas questões importantes que podem ser encontrados ao conceber, desenvolver e testar a recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="0cc53-246">This list is not exhaustive, but it covers many important issues which can be encountered while designing, developing and testing DSC resources.</span></span>