---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Desired State Configuration (DSC) conhecido limitações e problemas
ms.openlocfilehash: 6faf24795d14a93f265943029d9f6f1388f32263
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856197"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="6b762-103">Desired State Configuration (DSC) conhecido limitações e problemas</span><span class="sxs-lookup"><span data-stu-id="6b762-103">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="6b762-104">Alteração de última hora: Certificados utilizados para encriptação/desencriptação palavras-passe em configurações de DSC podem não funcionar após a instalação do WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="6b762-104">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="6b762-105">Em versões do WMF 4.0 e pré-visualização do WMF 5.0, DSC não permitiria palavras-passe na configuração do comprimento mais de 121 carateres.</span><span class="sxs-lookup"><span data-stu-id="6b762-105">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="6b762-106">DSC foi forçar a usar senhas curtas, mesmo que a palavra-passe longa e forte foi assim o desejar.</span><span class="sxs-lookup"><span data-stu-id="6b762-106">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="6b762-107">Esta alteração de última hora permite que as senhas tenham de comprimento arbitrário na configuração do DSC.</span><span class="sxs-lookup"><span data-stu-id="6b762-107">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="6b762-108">**Resolução:** Voltar a criar o certificado com a utilização de encriptação de dados ou a chave de encriptação de chave e utilização de chave de melhorada de encriptação de documentos (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="6b762-108">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="6b762-109">Para obter mais informações, consulte [Protect CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span><span class="sxs-lookup"><span data-stu-id="6b762-109">For more information, see [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span></span>

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="6b762-110">Cmdlets de DSC pode falhar após a instalação do WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="6b762-110">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="6b762-111">`Start-DscConfiguration` e outros cmdlets do DSC pode falhar após a instalação do WMF 5.0 RTM com o seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="6b762-111">`Start-DscConfiguration` and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>

```Output
LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
+ CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : MI RESULT 6
+ PSComputerName : localhost
```

<span data-ttu-id="6b762-112">**Resolução:** Elimine DSCEngineCache.mof ao executar o seguinte comando numa sessão do PowerShell elevada (executar como administrador):</span><span class="sxs-lookup"><span data-stu-id="6b762-112">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="6b762-113">Cmdlets de DSC poderá não funcionar se WMF 5.0 RTM é instalada sobre o WMF 5.0 produção pré-visualização</span><span class="sxs-lookup"><span data-stu-id="6b762-113">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>

<span data-ttu-id="6b762-114">**Resolução:** Execute o seguinte comando numa sessão elevada do PowerShell (executar como administrador):</span><span class="sxs-lookup"><span data-stu-id="6b762-114">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>

```powershell
mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="6b762-115">LCM pode entrar num estado instável, ao utilizar Get-dscconfiguration para no DebugMode</span><span class="sxs-lookup"><span data-stu-id="6b762-115">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>

<span data-ttu-id="6b762-116">Se for LCM no DebugMode, premir CTRL + C para parar o processamento de `Get-DscConfiguration` pode fazer com que o MMC para ir para um estado instável desse tipo que a maioria dos cmdlets de DSC não funcionará.</span><span class="sxs-lookup"><span data-stu-id="6b762-116">If LCM is in DebugMode, pressing CTRL+C to stop the processing of `Get-DscConfiguration` can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="6b762-117">**Resolução:** Não prima CTRL + C durante a depuração `Get-DscConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6b762-117">**Resolution:** Don’t press CTRL+C while debugging `Get-DscConfiguration` cmdlet.</span></span>

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a><span data-ttu-id="6b762-118">Stop-dscconfiguration para poderão não responder no DebugMode</span><span class="sxs-lookup"><span data-stu-id="6b762-118">Stop-DscConfiguration may not respond in DebugMode</span></span>

<span data-ttu-id="6b762-119">Se está a LCM DebugMode, `Stop-DscConfiguration` poderão não responder ao tentar parar uma operação iniciada por `Get-DscConfiguration`</span><span class="sxs-lookup"><span data-stu-id="6b762-119">If LCM is in DebugMode, `Stop-DscConfiguration` may not respond while trying to stop an operation started by `Get-DscConfiguration`</span></span>

<span data-ttu-id="6b762-120">**Resolução:** Concluir a depuração da operação iniciada pelo `Get-DscConfiguration` conforme descrito na [recursos de DSC de depuração](/powershell/dsc/troubleshooting/debugResource).</span><span class="sxs-lookup"><span data-stu-id="6b762-120">**Resolution:** Finish the debugging of the operation started by `Get-DscConfiguration` as outlined in [Debugging DSC resources](/powershell/dsc/troubleshooting/debugResource).</span></span>

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="6b762-121">Nenhuma mensagem de erro detalhado são mostradas na DebugMode</span><span class="sxs-lookup"><span data-stu-id="6b762-121">No Verbose Error Messages are shown in DebugMode</span></span>

<span data-ttu-id="6b762-122">Se está a LCM **DebugMode**, nenhuma mensagem de erro detalhado é apresentadas a partir dos recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="6b762-122">If LCM is in **DebugMode**, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="6b762-123">**Resolução:** Desativar **DebugMode** para ver as mensagens verbosas de recurso</span><span class="sxs-lookup"><span data-stu-id="6b762-123">**Resolution:** Disable **DebugMode** to see verbose messages from the resource</span></span>

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="6b762-124">Operações de invocar-DscResource não podem ser obtidas pelo cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="6b762-124">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="6b762-125">Depois de usar `Invoke-DscResource` cmdlet para invocar diretamente os métodos de qualquer recurso, os registos de tal operação não pode ser obtido por meio de `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="6b762-125">After using `Invoke-DscResource` cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through `Get-DscConfigurationStatus`.</span></span>

<span data-ttu-id="6b762-126">**Resolução:** Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6b762-126">**Resolution:** None.</span></span>

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="6b762-127">Operações de ciclo do Get-DscConfigurationStatus devolve pull como tipo **consistência**</span><span class="sxs-lookup"><span data-stu-id="6b762-127">Get-DscConfigurationStatus returns pull cycle operations as type **Consistency**</span></span>

<span data-ttu-id="6b762-128">Quando um nó é definido para o modo de atualização de SOLICITAÇÃO, para cada operação de solicitação realizada, `Get-DscConfigurationStatus` o tipo de operação como relatórios do cmdlet **consistência** em vez de *inicial*</span><span class="sxs-lookup"><span data-stu-id="6b762-128">When a node is set to PULL refresh mode, for each pull operation performed, `Get-DscConfigurationStatus` cmdlet reports the operation type as **Consistency** instead of *Initial*</span></span>

<span data-ttu-id="6b762-129">**Resolução:** Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6b762-129">**Resolution:** None.</span></span>

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="6b762-130">Cmdlet Invoke-DscResource não retorna mensagens na ordem em que foram produzidos</span><span class="sxs-lookup"><span data-stu-id="6b762-130">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>

<span data-ttu-id="6b762-131">O `Invoke-DscResource` cmdlet não devolve verboso, aviso, e mensagens de erro na ordem em que foram produzidas pelo LCM ou o recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="6b762-131">The `Invoke-DscResource` cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="6b762-132">**Resolução:** Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6b762-132">**Resolution:** None.</span></span>

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="6b762-133">Recursos de DSC não pode ser depurados facilmente quando utilizado com Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="6b762-133">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>

<span data-ttu-id="6b762-134">Quando LCM está em execução no modo de depuração, `Invoke-DscResource` cmdlet não lhe dá informações sobre o espaço de execução para ligar para depuração.</span><span class="sxs-lookup"><span data-stu-id="6b762-134">When LCM is running in debug mode, `Invoke-DscResource` cmdlet does not give information about runspace to connect to for debugging.</span></span> <span data-ttu-id="6b762-135">Para obter mais informações, consulte [recursos de DSC de depuração](/powershell/dsc/troubleshooting/debugResource).</span><span class="sxs-lookup"><span data-stu-id="6b762-135">For more information, see [Debugging DSC resources](/powershell/dsc/troubleshooting/debugResource).</span></span>

<span data-ttu-id="6b762-136">**Resolução:** Detetar e anexar ao espaço de execução com os cmdlets `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` e `Debug-Runspace` para depurar o recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="6b762-136">**Resolution:** Discover and attach to the runspace using cmdlets `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` and `Debug-Runspace` to debug the DSC resource.</span></span>

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName    ProcessId AppDomainName
-----------    --------- -------------
powershell          3932 DefaultAppDomain
powershell_ise      2304 DefaultAppDomain
WmiPrvSE            3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name       ComputerName Type  State  Availability
-- ----       ------------ ----  -----  ------------
 2 Runspace2  localhost    Local Opened InBreakpoint
 5 RemoteHost localhost    Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="6b762-137">Vários documentos de configuração parcial para o mesmo nó não podem ter nomes de recursos idênticos</span><span class="sxs-lookup"><span data-stu-id="6b762-137">Various Partial Configuration documents for same node cannot have identical resource names</span></span>

<span data-ttu-id="6b762-138">Para várias parciais configurações que são implementadas num único nó, nomes idênticos de recursos causa executam erro de tempo.</span><span class="sxs-lookup"><span data-stu-id="6b762-138">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="6b762-139">**Resolução:** Use nomes diferentes para os mesmos até mesmo recursos em diferentes configurações parciais.</span><span class="sxs-lookup"><span data-stu-id="6b762-139">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="6b762-140">Start-dscconfiguration para – UseExisting não funciona com - de credenciais</span><span class="sxs-lookup"><span data-stu-id="6b762-140">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>

<span data-ttu-id="6b762-141">Ao usar `Start-DscConfiguration` com **UseExisting** parâmetro, o **credencial** parâmetro é ignorado.</span><span class="sxs-lookup"><span data-stu-id="6b762-141">When using `Start-DscConfiguration` with **UseExisting** parameter, the **Credential** parameter is ignored.</span></span> <span data-ttu-id="6b762-142">DSC utiliza a identidade do processo padrão para continuar a operação.</span><span class="sxs-lookup"><span data-stu-id="6b762-142">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="6b762-143">Isso faz com que o erro quando uma credencial diferente é necessária para continuar no nó remoto.</span><span class="sxs-lookup"><span data-stu-id="6b762-143">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="6b762-144">**Resolução:** Utilize a sessão CIM para operações remotas do DSC:</span><span class="sxs-lookup"><span data-stu-id="6b762-144">**Resolution:** Use CIM session for remote DSC operations:</span></span>

```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="6b762-145">Endereços IPv6 como nomes de nó em configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="6b762-145">IPv6 Addresses as Node Names in DSC configurations</span></span>

<span data-ttu-id="6b762-146">Endereços IPv6 como nomes de nó em scripts de configuração de DSC não são suportados nesta versão.</span><span class="sxs-lookup"><span data-stu-id="6b762-146">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="6b762-147">**Resolução:** Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6b762-147">**Resolution:** None.</span></span>

## <a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="6b762-148">Depuração de `Class-Based` recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="6b762-148">Debugging of `Class-Based` DSC Resources</span></span>

<span data-ttu-id="6b762-149">Depuração de recursos de DSC baseados em classe não é suportada nesta versão.</span><span class="sxs-lookup"><span data-stu-id="6b762-149">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="6b762-150">**Resolução:** Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6b762-150">**Resolution:** None.</span></span>

## <a name="variables-and-functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="6b762-151">Variáveis e funções definidas no âmbito de $script no recurso baseado em classes de DSC não são mantidas em várias chamadas para um recurso de DSC</span><span class="sxs-lookup"><span data-stu-id="6b762-151">Variables and functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span>

<span data-ttu-id="6b762-152">Várias chamadas consecutivas para `Start-DSCConfiguration` falha se a configuração está a utilizar qualquer recurso baseado em classes que tem variáveis ou funções definidas no `$script` âmbito.</span><span class="sxs-lookup"><span data-stu-id="6b762-152">Multiple consecutive calls to `Start-DSCConfiguration` fails if the configuration is using any class-based resource which has variables or functions defined in `$script` scope.</span></span>

<span data-ttu-id="6b762-153">**Resolução:** Defina todas as variáveis e funções na própria classe de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="6b762-153">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="6b762-154">Não `$script` definir o âmbito variáveis/funções.</span><span class="sxs-lookup"><span data-stu-id="6b762-154">No `$script` scope variables/functions.</span></span>

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="6b762-155">A depuração de recursos de DSC quando um recurso está a utilizar PSDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="6b762-155">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>

<span data-ttu-id="6b762-156">A depuração de recursos de DSC quando um recurso está a utilizar o **PSDscRunAsCredential** propriedade na configuração não é suportada nesta versão.</span><span class="sxs-lookup"><span data-stu-id="6b762-156">DSC Resource debugging when a resource is using the **PSDscRunAsCredential** property in the configuration is not supported in this release.</span></span>

<span data-ttu-id="6b762-157">**Resolução:** Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6b762-157">**Resolution:** None.</span></span>

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="6b762-158">PsDscRunAsCredential não é suportado para recursos compostos de DSC</span><span class="sxs-lookup"><span data-stu-id="6b762-158">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>

<span data-ttu-id="6b762-159">**Resolução:** Utilize a propriedade de credencial, se estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="6b762-159">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="6b762-160">Exemplo ServiceSet e WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="6b762-160">Example ServiceSet and WindowsFeatureSet</span></span>

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="6b762-161">Get-DscResource-sintaxe não reflete PsDscRunAsCredential corretamente</span><span class="sxs-lookup"><span data-stu-id="6b762-161">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly</span></span>

<span data-ttu-id="6b762-162">O **sintaxe** parâmetro não reflete **PsDscRunAsCredential** corretamente quando recurso marca-o como obrigatórias ou não a suporta.</span><span class="sxs-lookup"><span data-stu-id="6b762-162">The **Syntax** parameter does not reflect **PsDscRunAsCredential** correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="6b762-163">**Resolução:** Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6b762-163">**Resolution:** None.</span></span> <span data-ttu-id="6b762-164">No entanto, a criação de configuração no ISE reflete metadados corretos sobre **PsDscRunAsCredential** propriedade ao usar o IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="6b762-164">However, authoring configuration in ISE reflects correct metadata about **PsDscRunAsCredential** property when using IntelliSense.</span></span>

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="6b762-165">WindowsOptionalFeature não está disponível no Windows 7</span><span class="sxs-lookup"><span data-stu-id="6b762-165">WindowsOptionalFeature is not available in Windows 7</span></span>

<span data-ttu-id="6b762-166">O **WindowsOptionalFeature** recursos de DSC não estão disponível no Windows 7.</span><span class="sxs-lookup"><span data-stu-id="6b762-166">The **WindowsOptionalFeature** DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="6b762-167">Este recurso requer o módulo DISM e os cmdlets DISM que estão disponíveis a partir do Windows 8 e versões mais recentes do sistema operativo Windows.</span><span class="sxs-lookup"><span data-stu-id="6b762-167">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="6b762-168">Para os recursos de DSC baseados em classe, Import-DscResource - ModuleVersion poderá não funcionar conforme esperado</span><span class="sxs-lookup"><span data-stu-id="6b762-168">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>

<span data-ttu-id="6b762-169">Se o nó de compilação tem várias versões do módulo de recursos DSC baseada em classes, `Import-DscResource -ModuleVersion` não escolha a versão especificada e resulta no seguinte erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="6b762-169">If the compilation node has multiple versions of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```Output
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s):
 "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="6b762-170">**Resolução:** Importar a versão necessária, definindo a **ModuleSpecification** objeto para o **ModuleName** parâmetro com **RequiredVersion** chave especificada da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="6b762-170">**Resolution:** Import the required version by defining the **ModuleSpecification** object to the **ModuleName** parameter with **RequiredVersion** key specified as follows:</span></span>

```powershell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="6b762-171">Alguns recursos de DSC, como o recurso de registro podem começar a demorar muito tempo a processar o pedido.</span><span class="sxs-lookup"><span data-stu-id="6b762-171">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>

<span data-ttu-id="6b762-172">**Resolução 1:** Crie uma tarefa de agendamento que limpa a seguinte pasta periodicamente.</span><span class="sxs-lookup"><span data-stu-id="6b762-172">**Resolution 1:** Create a schedule task that cleans up the following folder periodically.</span></span>

```powershell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

<span data-ttu-id="6b762-173">**Resolução 2:** Alterar a configuração de DSC para limpar os *CommandAnalysis* pasta no final da configuração.</span><span class="sxs-lookup"><span data-stu-id="6b762-173">**Resolution 2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>

```powershell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn = "[Registry]SetRegisteredOwner"
        getscript = "@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
