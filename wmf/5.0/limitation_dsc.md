---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 883f80a5c8c99f2ab9886558a7aebfe1204f3be6
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795152"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="19286-102">Desired State Configuration (DSC) conhecido limitações e problemas</span><span class="sxs-lookup"><span data-stu-id="19286-102">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="19286-103">Alteração de última hora: Certificados utilizados para encriptação/desencriptação palavras-passe em configurações de DSC podem não funcionar após a instalação do WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="19286-103">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="19286-104">Em versões do WMF 4.0 e pré-visualização do WMF 5.0, DSC não permitiria palavras-passe na configuração do comprimento mais de 121 carateres.</span><span class="sxs-lookup"><span data-stu-id="19286-104">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="19286-105">DSC foi forçar a usar senhas curtas, mesmo que a palavra-passe longa e forte foi assim o desejar.</span><span class="sxs-lookup"><span data-stu-id="19286-105">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="19286-106">Esta alteração de última hora permite que as senhas tenham de comprimento arbitrário na configuração do DSC.</span><span class="sxs-lookup"><span data-stu-id="19286-106">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="19286-107">**Resolução:** Voltar a criar o certificado com a utilização de encriptação de dados ou a chave de encriptação de chave e utilização de chave de melhorada de encriptação de documentos (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="19286-107">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="19286-108">Artigo da TechNet <https://technet.microsoft.com/library/dn807171.aspx> tem mais informações.</span><span class="sxs-lookup"><span data-stu-id="19286-108">Technet article <https://technet.microsoft.com/library/dn807171.aspx> has more information.</span></span>

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="19286-109">Cmdlets de DSC pode falhar após a instalação do WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="19286-109">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="19286-110">Start-dscconfiguration para e os outros cmdlets do DSC pode falhar após a instalação do WMF 5.0 RTM com o seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="19286-110">Start-DscConfiguration and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

<span data-ttu-id="19286-111">**Resolução:** Elimine DSCEngineCache.mof ao executar o seguinte comando numa sessão do PowerShell elevada (executar como administrador):</span><span class="sxs-lookup"><span data-stu-id="19286-111">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="19286-112">Cmdlets de DSC poderá não funcionar se WMF 5.0 RTM é instalada sobre o WMF 5.0 produção pré-visualização</span><span class="sxs-lookup"><span data-stu-id="19286-112">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>

<span data-ttu-id="19286-113">**Resolução:** Execute o seguinte comando numa sessão elevada do PowerShell (executar como administrador):</span><span class="sxs-lookup"><span data-stu-id="19286-113">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="19286-114">LCM pode entrar num estado instável, ao utilizar Get-dscconfiguration para no DebugMode</span><span class="sxs-lookup"><span data-stu-id="19286-114">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>

<span data-ttu-id="19286-115">Se for LCM no DebugMode, premir CTRL + C para parar o processamento de Get-dscconfiguration para pode fazer com que o MMC para ir para um estado instável desse tipo que a maioria dos cmdlets de DSC não funcionará.</span><span class="sxs-lookup"><span data-stu-id="19286-115">If LCM is in DebugMode, pressing CTRL+C to stop the processing of Get-DscConfiguration can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="19286-116">**Resolução:** Não, pressione CTRL + C durante a depuração do cmdlet Get-dscconfiguration para.</span><span class="sxs-lookup"><span data-stu-id="19286-116">**Resolution:** Don’t press CTRL+C while debugging Get-DscConfiguration cmdlet.</span></span>

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a><span data-ttu-id="19286-117">Stop-dscconfiguration para poderão não responder no DebugMode</span><span class="sxs-lookup"><span data-stu-id="19286-117">Stop-DscConfiguration may not respond in DebugMode</span></span>

<span data-ttu-id="19286-118">Se for LCM no DebugMode, Stop-dscconfiguration para poderão não responder ao tentar parar uma operação iniciada pelo Get-dscconfiguration para</span><span class="sxs-lookup"><span data-stu-id="19286-118">If LCM is in DebugMode, Stop-DscConfiguration may not respond while trying to stop an operation started by Get-DscConfiguration</span></span>

<span data-ttu-id="19286-119">**Resolução:** Concluir a depuração da operação iniciada pelo Get-dscconfiguration para, conforme descrito na secção '[recursos de DSC de depuração](https://msdn.microsoft.com/powershell/dsc/debugresource)'.</span><span class="sxs-lookup"><span data-stu-id="19286-119">**Resolution:** Finish the debugging of the operation started by Get-DscConfiguration as outlined in section ‘[Debugging DSC resources](https://msdn.microsoft.com/powershell/dsc/debugresource)’.</span></span>

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="19286-120">Nenhuma mensagem de erro detalhado são mostradas na DebugMode</span><span class="sxs-lookup"><span data-stu-id="19286-120">No Verbose Error Messages are shown in DebugMode</span></span>

<span data-ttu-id="19286-121">Se for LCM no DebugMode, nenhuma mensagem de erro detalhado é apresentadas a partir dos recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="19286-121">If LCM is in DebugMode, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="19286-122">**Resolução:** Desativar *DebugMode* para ver as mensagens verbosas de recurso</span><span class="sxs-lookup"><span data-stu-id="19286-122">**Resolution:** Disable *DebugMode* to see verbose messages from the resource</span></span>

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="19286-123">Operações de invocar-DscResource não podem ser obtidas pelo cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="19286-123">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="19286-124">Depois de utilizar o cmdlet Invoke-DscResource diretamente invocar métodos de qualquer recurso, não não possível obter os registos de tal operação por meio de Get-DscConfigurationStatus num momento posterior.</span><span class="sxs-lookup"><span data-stu-id="19286-124">After using Invoke-DscResource cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through Get-DscConfigurationStatus at a later time.</span></span>

<span data-ttu-id="19286-125">**Resolução:** Nenhum.</span><span class="sxs-lookup"><span data-stu-id="19286-125">**Resolution:** None.</span></span>

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="19286-126">Operações de ciclo do Get-DscConfigurationStatus devolve pull como tipo *consistência*</span><span class="sxs-lookup"><span data-stu-id="19286-126">Get-DscConfigurationStatus returns pull cycle operations as type *Consistency*</span></span>

<span data-ttu-id="19286-127">Quando um nó é definido para o modo de atualização de SOLICITAÇÃO, para cada operação de solicitação realizada, o cmdlet Get-DscConfigurationStatus relatórios como o tipo de operação *consistência* em vez de *inicial*</span><span class="sxs-lookup"><span data-stu-id="19286-127">When a node is set to PULL refresh mode, for each pull operation performed, Get-DscConfigurationStatus cmdlet reports the operation type as *Consistency* instead of *Initial*</span></span>

<span data-ttu-id="19286-128">**Resolução:** Nenhum.</span><span class="sxs-lookup"><span data-stu-id="19286-128">**Resolution:** None.</span></span>

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="19286-129">Cmdlet Invoke-DscResource não retorna mensagens na ordem em que foram produzidos</span><span class="sxs-lookup"><span data-stu-id="19286-129">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>

<span data-ttu-id="19286-130">O cmdlet Invoke-DscResource não devolve verboso, aviso, e mensagens de erro na ordem em que foram produzidas pelo LCM ou o recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="19286-130">The Invoke-DscResource cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="19286-131">**Resolução:** Nenhum.</span><span class="sxs-lookup"><span data-stu-id="19286-131">**Resolution:** None.</span></span>

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="19286-132">Recursos de DSC não pode ser depurados facilmente quando utilizado com Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="19286-132">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>

<span data-ttu-id="19286-133">Quando LCM está em execução no modo de depuração (consulte [recursos de DSC de depuração](https://msdn.microsoft.com/powershell/dsc/debugresource) para obter mais detalhes), cmdlet Invoke-DscResource não lhe dá informações sobre o espaço de execução para ligar para depuração.</span><span class="sxs-lookup"><span data-stu-id="19286-133">When LCM is running in debug mode (see [Debugging DSC resources](https://msdn.microsoft.com/powershell/dsc/debugresource) for more details), Invoke-DscResource cmdlet does not give information about runspace to connect to for debugging.</span></span>
<span data-ttu-id="19286-134">**Resolução:** Detetar e anexar ao espaço de execução com os cmdlets **Get-PSHostProcessInfo**, **Enter PSHostProcess** , **Get-Runspace** e **depuração-Runspace** para depurar o recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="19286-134">**Resolution:** Discover and attach to the runspace using cmdlets **Get-PSHostProcessInfo**, **Enter-PSHostProcess** , **Get-Runspace** and **Debug-Runspace** to debug the DSC resource.</span></span>

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell 3932 DefaultAppDomain
powershell_ise 2304 DefaultAppDomain
WmiPrvSE 3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name ComputerName Type State Availability
-- ---- ------------ ---- ----- ------------
2 Runspace2 localhost Local Opened InBreakpoint
5 RemoteHost localhost Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="19286-135">Vários documentos de configuração parcial para o mesmo nó não podem ter nomes de recursos idênticos</span><span class="sxs-lookup"><span data-stu-id="19286-135">Various Partial Configuration documents for same node cannot have identical resource names</span></span>

<span data-ttu-id="19286-136">Para várias parciais configurações que são implementadas num único nó, nomes idênticos de recursos causa executam erro de tempo.</span><span class="sxs-lookup"><span data-stu-id="19286-136">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="19286-137">**Resolução:** Use nomes diferentes para os mesmos até mesmo recursos em diferentes configurações parciais.</span><span class="sxs-lookup"><span data-stu-id="19286-137">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="19286-138">Start-dscconfiguration para – UseExisting não funciona com - de credenciais</span><span class="sxs-lookup"><span data-stu-id="19286-138">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>

<span data-ttu-id="19286-139">Ao utilizar o início-dscconfiguration para com o parâmetro – UseExisting, – Credential parâmetro é ignorado.</span><span class="sxs-lookup"><span data-stu-id="19286-139">When using Start-DscConfiguration with –UseExisting parameter, the –Credential parameter is ignored.</span></span> <span data-ttu-id="19286-140">DSC utiliza a identidade do processo padrão para continuar a operação.</span><span class="sxs-lookup"><span data-stu-id="19286-140">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="19286-141">Isso faz com que o erro quando uma credencial diferente é necessária para continuar no nó remoto.</span><span class="sxs-lookup"><span data-stu-id="19286-141">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="19286-142">**Resolução:** Utilize a sessão CIM para operações remotas do DSC:</span><span class="sxs-lookup"><span data-stu-id="19286-142">**Resolution:** Use CIM session for remote DSC operations:</span></span>
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="19286-143">Endereços IPv6 como nomes de nó em configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="19286-143">IPv6 Addresses as Node Names in DSC configurations</span></span>

<span data-ttu-id="19286-144">Endereços IPv6 como nomes de nó em scripts de configuração de DSC não são suportados nesta versão.</span><span class="sxs-lookup"><span data-stu-id="19286-144">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="19286-145">**Resolução:** Nenhum.</span><span class="sxs-lookup"><span data-stu-id="19286-145">**Resolution:** None.</span></span>

## <a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="19286-146">Depuração de recursos de DSC baseados em classe</span><span class="sxs-lookup"><span data-stu-id="19286-146">Debugging of Class-Based DSC Resources</span></span>

<span data-ttu-id="19286-147">Depuração de recursos de DSC baseados em classe não é suportada nesta versão.</span><span class="sxs-lookup"><span data-stu-id="19286-147">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="19286-148">**Resolução:** Nenhum.</span><span class="sxs-lookup"><span data-stu-id="19286-148">**Resolution:** None.</span></span>

## <a name="variables--functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="19286-149">As variáveis e funções definidas no âmbito de $script no recurso baseado em classes de DSC não são mantidas em várias chamadas para um recurso de DSC</span><span class="sxs-lookup"><span data-stu-id="19286-149">Variables & Functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span>

<span data-ttu-id="19286-150">Várias chamadas consecutivas para Start-dscconfiguration para irão falhar se a configuração está a utilizar qualquer recurso baseado em classes que tem variáveis ou funções definidas no âmbito de $script.</span><span class="sxs-lookup"><span data-stu-id="19286-150">Multiple consecutive calls to Start-DSCConfiguration will fail if configuration is using any class-based resource which has variables or functions defined in $script scope.</span></span>

<span data-ttu-id="19286-151">**Resolução:** Defina todas as variáveis e funções na própria classe de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="19286-151">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="19286-152">Variáveis de âmbito de No $script/funções.</span><span class="sxs-lookup"><span data-stu-id="19286-152">No $script scope variables/functions.</span></span>

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="19286-153">A depuração de recursos de DSC quando um recurso está a utilizar PSDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="19286-153">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>

<span data-ttu-id="19286-154">A depuração de recursos de DSC quando um recurso está a utilizar o *PSDscRunAsCredential* propriedade na configuração não é suportado nesta versão.</span><span class="sxs-lookup"><span data-stu-id="19286-154">DSC Resource debugging when a resource is using the *PSDscRunAsCredential* property in the configuration is not suported in this release.</span></span>

<span data-ttu-id="19286-155">**Resolução:** Nenhum.</span><span class="sxs-lookup"><span data-stu-id="19286-155">**Resolution:** None.</span></span>

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="19286-156">PsDscRunAsCredential não é suportado para recursos compostos de DSC</span><span class="sxs-lookup"><span data-stu-id="19286-156">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>

<span data-ttu-id="19286-157">**Resolução:** Utilize a propriedade de credencial, se estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="19286-157">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="19286-158">Exemplo ServiceSet e WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="19286-158">Example ServiceSet and WindowsFeatureSet</span></span>

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="19286-159">*Get-DscResource-sintaxe* não reflete PsDscRunAsCredential corretamente</span><span class="sxs-lookup"><span data-stu-id="19286-159">*Get-DscResource -Syntax* does not reflect PsDscRunAsCredential correctly</span></span>

<span data-ttu-id="19286-160">Get-DscResource-sintaxe não reflete PsDscRunAsCredential corretamente quando o recurso de marca-o como obrigatórias ou não a suporta.</span><span class="sxs-lookup"><span data-stu-id="19286-160">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="19286-161">**Resolução:** Nenhum.</span><span class="sxs-lookup"><span data-stu-id="19286-161">**Resolution:** None.</span></span> <span data-ttu-id="19286-162">No entanto, a criação de configuração no ISE reflete os metadados corretos sobre PsDscRunAsCredential propriedade ao usar o IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="19286-162">However, authoring configuration in ISE reflects correct metadata about PsDscRunAsCredential property when using IntelliSense.</span></span>

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="19286-163">WindowsOptionalFeature não está disponível no Windows 7</span><span class="sxs-lookup"><span data-stu-id="19286-163">WindowsOptionalFeature is not available in Windows 7</span></span>

<span data-ttu-id="19286-164">O recurso de DSC WindowsOptionalFeature não está disponível no Windows 7.</span><span class="sxs-lookup"><span data-stu-id="19286-164">The WindowsOptionalFeature DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="19286-165">Este recurso requer o módulo DISM e os cmdlets DISM que estão disponíveis a partir do Windows 8 e versões mais recentes do sistema operativo Windows.</span><span class="sxs-lookup"><span data-stu-id="19286-165">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="19286-166">Para os recursos de DSC baseados em classe, Import-DscResource - ModuleVersion poderá não funcionar conforme esperado</span><span class="sxs-lookup"><span data-stu-id="19286-166">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>

<span data-ttu-id="19286-167">Se o nó de compilação tem vários versão do módulo de recursos DSC baseada em classes, `Import-DscResource -ModuleVersion` não escolha a versão especificada e resulta no seguinte erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="19286-167">If the compilation node has multiple version of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="19286-168">**Resolução:** Importar a versão necessária, definindo a *ModuleSpecification* objeto para o `-ModuleName` com `RequiredVersion` chave especificada da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="19286-168">**Resolution:** Import the required version by defining the *ModuleSpecification* object to the `-ModuleName` with `RequiredVersion` key specified as follows:</span></span>

``` PowerShell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="19286-169">Alguns recursos de DSC, como o recurso de registro podem começar a demorar muito tempo a processar o pedido.</span><span class="sxs-lookup"><span data-stu-id="19286-169">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>

<span data-ttu-id="19286-170">**Resolution1:** Crie uma tarefa de agendamento que limpa a seguinte pasta periodicamente.</span><span class="sxs-lookup"><span data-stu-id="19286-170">**Resolution1:** Create a schedule task that cleans up the following folder periodically.</span></span>

``` PowerShell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

<span data-ttu-id="19286-171">**Resolution2:** Alterar a configuração de DSC para limpar os *CommandAnalysis* pasta no final da configuração.</span><span class="sxs-lookup"><span data-stu-id="19286-171">**Resolution2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>

``` PowerShell
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
        DependsOn="[Registry]SetRegisteredOwner"
        getscript="@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
