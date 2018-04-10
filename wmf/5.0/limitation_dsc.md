---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 66ceea383b78b2654caa4f1de16a30beea0e7fd3
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="95b36-102">Configuração do estado pretendido (DSC) conhecido problemas e limitações</span><span class="sxs-lookup"><span data-stu-id="95b36-102">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

<a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="95b36-103">Alteração interrompendo: Os certificados utilizados para encriptar/desencriptar as palavras-passe em configurações de DSC poderão não funcionar após a instalação do WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="95b36-103">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>
--------------------------------------------------------------------------------------------------------------------------------

<span data-ttu-id="95b36-104">Em versões do WMF 4.0 e o WMF 5.0 pré-visualização, DSC não permitiria palavras-passe na configuração para ter um comprimento superior 121 carateres.</span><span class="sxs-lookup"><span data-stu-id="95b36-104">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="95b36-105">DSC foi forçar a utilizar palavras-passe curtas, mesmo se a palavra-passe forte e demorado foi assim o desejar.</span><span class="sxs-lookup"><span data-stu-id="95b36-105">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="95b36-106">Esta alteração inovadora permite palavras-passe para ser de comprimento arbitrário na configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="95b36-106">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="95b36-107">**Resolução:** voltar a criar o certificado com a utilização de encriptação de dados ou chave cifragem de chaves e a utilização de chave de melhorada de encriptação do documento (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="95b36-107">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="95b36-108">Artigo do TechNet <https://technet.microsoft.com/library/dn807171.aspx> tem mais informações.</span><span class="sxs-lookup"><span data-stu-id="95b36-108">Technet article <https://technet.microsoft.com/library/dn807171.aspx> has more information.</span></span>


<a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="95b36-109">Cmdlets de DSC poderão falhar após a instalação do WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="95b36-109">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>
------------------------------------------------------------------------------------
<span data-ttu-id="95b36-110">Início DscConfiguration e outros cmdlets do DSC poderão falhar após a instalação do WMF 5.0 RTM com o seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="95b36-110">Start-DscConfiguration and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

<span data-ttu-id="95b36-111">**Resolução:** eliminar DSCEngineCache.mof executando o seguinte comando numa sessão do PowerShell elevada (executar como administrador):</span><span class="sxs-lookup"><span data-stu-id="95b36-111">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```


<a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="95b36-112">Cmdlets de DSC poderão não funcionar se WMF 5.0 RTM é instalado por cima de pré-visualização de produção do WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="95b36-112">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>
------------------------------------------------------
<span data-ttu-id="95b36-113">**Resolução:** execute o seguinte comando numa sessão do PowerShell elevada (executar como administrador):</span><span class="sxs-lookup"><span data-stu-id="95b36-113">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```


<a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="95b36-114">O MMC pode ir para um estado instável ao utilizar o Get-DscConfiguration DebugMode</span><span class="sxs-lookup"><span data-stu-id="95b36-114">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>
-------------------------------------------------------------------------------

<span data-ttu-id="95b36-115">Se tiver o MMC DebugMode, premir CTRL + C para parar o processamento de Get-DscConfiguration pode fazer com que o MMC Ir para um estado instável esse que maioria dos cmdlets de DSC não funcionará.</span><span class="sxs-lookup"><span data-stu-id="95b36-115">If LCM is in DebugMode, pressing CTRL+C to stop the processing of Get-DscConfiguration can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="95b36-116">**Resolução:** não prima CTRL + C durante a depuração cmdlet Get-DscConfiguration.</span><span class="sxs-lookup"><span data-stu-id="95b36-116">**Resolution:** Don’t press CTRL+C while debugging Get-DscConfiguration cmdlet.</span></span>


<a name="stop-dscconfiguration-may-hang-in-debugmode"></a><span data-ttu-id="95b36-117">Stop-DscConfiguration poderá bloquear no DebugMode</span><span class="sxs-lookup"><span data-stu-id="95b36-117">Stop-DscConfiguration may hang in DebugMode</span></span>
------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="95b36-118">Se tiver o MMC DebugMode, Stop-DscConfiguration poderá bloquear ao tentar parar uma operação iniciado por Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="95b36-118">If LCM is in DebugMode, Stop-DscConfiguration may hang while trying to stop an operation started by Get-DscConfiguration</span></span>

<span data-ttu-id="95b36-119">**Resolução:** concluir a depuração da operação foi iniciada pelo Get-DscConfiguration conforme descrito na secção '[recursos de DSC depuração](https://msdn.microsoft.com/powershell/dsc/debugresource)'.</span><span class="sxs-lookup"><span data-stu-id="95b36-119">**Resolution:** Finish the debugging of the operation started by Get-DscConfiguration as outlined in section ‘[Debugging DSC resources](https://msdn.microsoft.com/powershell/dsc/debugresource)’.</span></span>


<a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="95b36-120">Não existem mensagens de erro verbosas são apresentadas na DebugMode</span><span class="sxs-lookup"><span data-stu-id="95b36-120">No Verbose Error Messages are shown in DebugMode</span></span>
-----------------------------------------------------------------------------------
<span data-ttu-id="95b36-121">Se tiver o MMC DebugMode, não existem mensagens de erro verbosas são apresentadas a partir dos recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="95b36-121">If LCM is in DebugMode, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="95b36-122">**Resolução:** desativar *DebugMode* para ver as mensagens verbosas de recurso</span><span class="sxs-lookup"><span data-stu-id="95b36-122">**Resolution:** Disable *DebugMode* to see verbose messages from the resource</span></span>


<a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="95b36-123">Não não possível obter DscResource invocar operações pelo cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="95b36-123">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>
--------------------------------------------------------------------------------------
<span data-ttu-id="95b36-124">Depois de utilizar o cmdlet Invoke-DscResource diretamente invocação de métodos de qualquer recurso, os registos de tal operação não não possível obter através de Get-DscConfigurationStatus numa altura posterior.</span><span class="sxs-lookup"><span data-stu-id="95b36-124">After using Invoke-DscResource cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through Get-DscConfigurationStatus at a later time.</span></span>

<span data-ttu-id="95b36-125">**Resolução:** None.</span><span class="sxs-lookup"><span data-stu-id="95b36-125">**Resolution:** None.</span></span>


<a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="95b36-126">Operações de ciclo do Get-DscConfigurationStatus devolve solicitação como tipo *consistência*</span><span class="sxs-lookup"><span data-stu-id="95b36-126">Get-DscConfigurationStatus returns pull cycle operations as type *Consistency*</span></span>
---------------------------------------------------------------------------------
<span data-ttu-id="95b36-127">Quando um nó estiver definido para o modo de atualização de EXTRAÇÃO, para cada operação de solicitação efetuada, o cmdlet Get-DscConfigurationStatus relatórios como o tipo de operação *consistência* em vez de *inicial*</span><span class="sxs-lookup"><span data-stu-id="95b36-127">When a node is set to PULL refresh mode, for each pull operation performed, Get-DscConfigurationStatus cmdlet reports the operation type as *Consistency* instead of *Initial*</span></span>

<span data-ttu-id="95b36-128">**Resolução:** None.</span><span class="sxs-lookup"><span data-stu-id="95b36-128">**Resolution:** None.</span></span>

<a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="95b36-129">DscResource invocar o cmdlet não devolve mensagem pela ordem que foram produzidos</span><span class="sxs-lookup"><span data-stu-id="95b36-129">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>
---------------------------------------------------------------------------------
<span data-ttu-id="95b36-130">O cmdlet Invoke-DscResource não devolver verboso, aviso, e mensagens de erro na ordem que foram produzidos por MMC ou o recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="95b36-130">The Invoke-DscResource cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="95b36-131">**Resolução:** None.</span><span class="sxs-lookup"><span data-stu-id="95b36-131">**Resolution:** None.</span></span>


<a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="95b36-132">Recursos de DSC não é possível debugged facilmente quando utilizado com Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="95b36-132">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>
-----------------------------------------------------------------------
<span data-ttu-id="95b36-133">Quando o MMC está em execução no modo de depuração (consulte [recursos de DSC depuração](https://msdn.microsoft.com/powershell/dsc/debugresource) para obter mais detalhes), cmdlet Invoke-DscResource não fornecer informações sobre o espaço de execução para ligar para a depuração.</span><span class="sxs-lookup"><span data-stu-id="95b36-133">When LCM is running in debug mode (see [Debugging DSC resources](https://msdn.microsoft.com/powershell/dsc/debugresource) for more details), Invoke-DscResource cmdlet does not give information about runspace to connect to for debugging.</span></span>
<span data-ttu-id="95b36-134">**Resolução:** detetar e ligue a execução com os cmdlets **Get-PSHostProcessInfo**, **Enter PSHostProcess** , **Get-espaço de execução** e **Espaço de execução de depuração** para depurar o recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="95b36-134">**Resolution:** Discover and attach to the runspace using cmdlets **Get-PSHostProcessInfo**, **Enter-PSHostProcess** , **Get-Runspace** and **Debug-Runspace** to debug the DSC resource.</span></span>

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


<a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="95b36-135">Vários documentos configuração parcial para o mesmo nó não podem ter nomes de recursos idênticas</span><span class="sxs-lookup"><span data-stu-id="95b36-135">Various Partial Configuration documents for same node cannot have identical resource names</span></span>
------------------------------------------------------------------------------------------

<span data-ttu-id="95b36-136">Para várias parciais configurações que são implementadas num único nó, nomes idênticos de recursos causa executam o erro de tempo.</span><span class="sxs-lookup"><span data-stu-id="95b36-136">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="95b36-137">**Resolução:** Utilize diferentes nomes para o mesmo mesmos recursos em diferentes configurações parciais.</span><span class="sxs-lookup"><span data-stu-id="95b36-137">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>


<a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="95b36-138">Início DscConfiguration – UseExisting não funciona com - Credential</span><span class="sxs-lookup"><span data-stu-id="95b36-138">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>
------------------------------------------------------------------

<span data-ttu-id="95b36-139">Ao utilizar DscConfiguration início com o parâmetro – UseExisting, – credenciais parâmetro será ignorado.</span><span class="sxs-lookup"><span data-stu-id="95b36-139">When using Start-DscConfiguration with –UseExisting parameter, the –Credential parameter is ignored.</span></span> <span data-ttu-id="95b36-140">DSC utiliza a identidade do processo predefinido para continuar a operação.</span><span class="sxs-lookup"><span data-stu-id="95b36-140">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="95b36-141">Isto faz com que erro quando é necessária uma credencial diferente para continuar no nó remoto.</span><span class="sxs-lookup"><span data-stu-id="95b36-141">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="95b36-142">**Resolução:** utilize CIM sessão para operações de DSC remotas:</span><span class="sxs-lookup"><span data-stu-id="95b36-142">**Resolution:** Use CIM session for remote DSC operations:</span></span>
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```


<a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="95b36-143">Endereços IPv6 como nomes de nó em configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="95b36-143">IPv6 Addresses as Node Names in DSC configurations</span></span>
--------------------------------------------------
<span data-ttu-id="95b36-144">Endereços IPv6 como nomes de nó em scripts de configuração de DSC não são suportados nesta versão.</span><span class="sxs-lookup"><span data-stu-id="95b36-144">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="95b36-145">**Resolução:** None.</span><span class="sxs-lookup"><span data-stu-id="95b36-145">**Resolution:** None.</span></span>


<a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="95b36-146">A depuração de recursos de DSC com base na classe</span><span class="sxs-lookup"><span data-stu-id="95b36-146">Debugging of Class-Based DSC Resources</span></span>
--------------------------------------
<span data-ttu-id="95b36-147">A depuração de recursos de DSC baseados em classe não é suportada nesta versão.</span><span class="sxs-lookup"><span data-stu-id="95b36-147">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="95b36-148">**Resolução:** None.</span><span class="sxs-lookup"><span data-stu-id="95b36-148">**Resolution:** None.</span></span>


<a name="variables--functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="95b36-149">As variáveis de & funções definidas no âmbito de $script no recurso baseado em classes de DSC não são mantidas em várias chamadas a um recurso de DSC</span><span class="sxs-lookup"><span data-stu-id="95b36-149">Variables & Functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span>
-------------------------------------------------------------------------------------------------------------------------------------

<span data-ttu-id="95b36-150">Várias chamadas consecutivas para início DSCConfiguration irão falhar se a configuração está a utilizar qualquer recurso com base na classe que possui variáveis ou funções definidas no âmbito de $script.</span><span class="sxs-lookup"><span data-stu-id="95b36-150">Multiple consecutive calls to Start-DSCConfiguration will fail if configuration is using any class-based resource which has variables or functions defined in $script scope.</span></span>

<span data-ttu-id="95b36-151">**Resolução:** definir todas as funções e as variáveis na própria classe de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="95b36-151">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="95b36-152">As variáveis de âmbito No $script/funções.</span><span class="sxs-lookup"><span data-stu-id="95b36-152">No $script scope variables/functions.</span></span>


<a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="95b36-153">A depuração de recurso DSC quando um recurso está a utilizar PSDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="95b36-153">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>
----------------------------------------------------------------------
<span data-ttu-id="95b36-154">A depuração de recurso DSC quando um recurso está a utilizar o *PSDscRunAsCredential* propriedade na configuração não é suportado nesta versão.</span><span class="sxs-lookup"><span data-stu-id="95b36-154">DSC Resource debugging when a resource is using the *PSDscRunAsCredential* property in the configuration is not suported in this release.</span></span>

<span data-ttu-id="95b36-155">**Resolução:** None.</span><span class="sxs-lookup"><span data-stu-id="95b36-155">**Resolution:** None.</span></span>


<a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="95b36-156">PsDscRunAsCredential não é suportado para recursos de DSC composto</span><span class="sxs-lookup"><span data-stu-id="95b36-156">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>
----------------------------------------------------------------

<span data-ttu-id="95b36-157">**Resolução:** propriedade de credencial de utilização, se disponível.</span><span class="sxs-lookup"><span data-stu-id="95b36-157">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="95b36-158">Exemplo ServiceSet e WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="95b36-158">Example ServiceSet and WindowsFeatureSet</span></span>


<a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="95b36-159">*Get-DscResource-sintaxe* não reflete PsDscRunAsCredential corretamente</span><span class="sxs-lookup"><span data-stu-id="95b36-159">*Get-DscResource -Syntax* does not reflect PsDscRunAsCredential correctly</span></span>
-------------------------------------------------------------------------
<span data-ttu-id="95b36-160">Get-DscResource-sintaxe não reflete PsDscRunAsCredential corretamente quando recurso marca-a como obrigatórios ou não o suporta.</span><span class="sxs-lookup"><span data-stu-id="95b36-160">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="95b36-161">**Resolução:** None.</span><span class="sxs-lookup"><span data-stu-id="95b36-161">**Resolution:** None.</span></span> <span data-ttu-id="95b36-162">No entanto, a criação de configuração no ISE reflete metadados corretos sobre PsDscRunAsCredential propriedade quando utilizar o IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="95b36-162">However, authoring configuration in ISE reflects correct metadata about PsDscRunAsCredential property when using IntelliSense.</span></span>


<a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="95b36-163">WindowsOptionalFeature não está disponível no Windows 7</span><span class="sxs-lookup"><span data-stu-id="95b36-163">WindowsOptionalFeature is not available in Windows 7</span></span>
-----------------------------------------------------

<span data-ttu-id="95b36-164">O recurso de WindowsOptionalFeature DSC não está disponível no Windows 7.</span><span class="sxs-lookup"><span data-stu-id="95b36-164">The WindowsOptionalFeature DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="95b36-165">Este recurso necessita do módulo DISM e os cmdlets DISM que estão disponíveis a partir do Windows 8 e versões mais recentes do sistema operativo Windows.</span><span class="sxs-lookup"><span data-stu-id="95b36-165">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

<a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="95b36-166">Para os recursos de DSC com base na classe, importação DscResource - ModuleVersion poderão não funcionar conforme esperado</span><span class="sxs-lookup"><span data-stu-id="95b36-166">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>
------------------------------------------------------------------------------------------
<span data-ttu-id="95b36-167">Se o nó de compilação tem vários versão do módulo de recurso DSC baseado em classes, `Import-DscResource -ModuleVersion` não escolha a versão especificada e resulta no seguinte erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="95b36-167">If the compilation node has multiple version of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="95b36-168">**Resolução:** importar a versão necessária, definindo o *ModuleSpecification* de objeto para o `-ModuleName` com `RequiredVersion` chave especificada da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="95b36-168">**Resolution:** Import the required version by defining the *ModuleSpecification* object to the `-ModuleName` with `RequiredVersion` key specified as follows:</span></span>
``` PowerShell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

<a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="95b36-169">Alguns recursos de DSC como recursos de registo podem começar a demorar muito tempo a processar o pedido.</span><span class="sxs-lookup"><span data-stu-id="95b36-169">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>
--------------------------------------------------------------------------------------------------------------------------------

<span data-ttu-id="95b36-170">**Resolution1:** criar uma tarefa de agendamento que limpa a seguinte pasta periodicamente.</span><span class="sxs-lookup"><span data-stu-id="95b36-170">**Resolution1:** Create a schedule task that cleans up the following folder periodically.</span></span>
``` PowerShell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

<span data-ttu-id="95b36-171">**Resolution2:** alterar a configuração de DSC para limpar o *CommandAnalysis* pasta no final da configuração.</span><span class="sxs-lookup"><span data-stu-id="95b36-171">**Resolution2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>
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