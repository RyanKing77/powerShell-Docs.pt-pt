---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 76aa4a372602d78e013b2138eb6409304a4dfb76
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190065"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a>Configuração do estado pretendido (DSC) conhecido problemas e limitações

<a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a>Alteração interrompendo: Os certificados utilizados para encriptar/desencriptar as palavras-passe em configurações de DSC poderão não funcionar após a instalação do WMF 5.0 RTM
--------------------------------------------------------------------------------------------------------------------------------

Em versões do WMF 4.0 e o WMF 5.0 pré-visualização, DSC não permitiria palavras-passe na configuração para ter um comprimento superior 121 carateres. DSC foi forçar a utilizar palavras-passe curtas, mesmo se a palavra-passe forte e demorado foi assim o desejar. Esta alteração inovadora permite palavras-passe para ser de comprimento arbitrário na configuração de DSC.

**Resolução:** voltar a criar o certificado com a utilização de encriptação de dados ou chave cifragem de chaves e a utilização de chave de melhorada de encriptação do documento (1.3.6.1.4.1.311.80.1). Artigo do TechNet <https://technet.microsoft.com/library/dn807171.aspx> tem mais informações.


<a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a>Cmdlets de DSC poderão falhar após a instalação do WMF 5.0 RTM
------------------------------------------------------------------------------------
Início DscConfiguration e outros cmdlets do DSC poderão falhar após a instalação do WMF 5.0 RTM com o seguinte erro:
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

**Resolução:** eliminar DSCEngineCache.mof executando o seguinte comando numa sessão do PowerShell elevada (executar como administrador):

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```


<a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a>Cmdlets de DSC poderão não funcionar se WMF 5.0 RTM é instalado por cima de pré-visualização de produção do WMF 5.0
------------------------------------------------------
**Resolução:** execute o seguinte comando numa sessão do PowerShell elevada (executar como administrador):
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```


<a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a>O MMC pode ir para um estado instável ao utilizar o Get-DscConfiguration DebugMode
-------------------------------------------------------------------------------

Se tiver o MMC DebugMode, premir CTRL + C para parar o processamento de Get-DscConfiguration pode fazer com que o MMC Ir para um estado instável esse que maioria dos cmdlets de DSC não funcionará.

**Resolução:** não prima CTRL + C durante a depuração cmdlet Get-DscConfiguration.


<a name="stop-dscconfiguration-may-hang-in-debugmode"></a>Stop-DscConfiguration poderá bloquear no DebugMode
------------------------------------------------------------------------------------------------------------------------
Se tiver o MMC DebugMode, Stop-DscConfiguration poderá bloquear ao tentar parar uma operação iniciado por Get-DscConfiguration

**Resolução:** concluir a depuração da operação foi iniciada pelo Get-DscConfiguration conforme descrito na secção '[recursos de DSC depuração](https://msdn.microsoft.com/powershell/dsc/debugresource)'.


<a name="no-verbose-error-messages-are-shown-in-debugmode"></a>Não existem mensagens de erro verbosas são apresentadas na DebugMode
-----------------------------------------------------------------------------------
Se tiver o MMC DebugMode, não existem mensagens de erro verbosas são apresentadas a partir dos recursos de DSC.

**Resolução:** desativar *DebugMode* para ver as mensagens verbosas de recurso


<a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a>Não não possível obter DscResource invocar operações pelo cmdlet Get-DscConfigurationStatus
--------------------------------------------------------------------------------------
Depois de utilizar o cmdlet Invoke-DscResource diretamente invocação de métodos de qualquer recurso, os registos de tal operação não não possível obter através de Get-DscConfigurationStatus numa altura posterior.

**Resolução:** None.


<a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a>Operações de ciclo do Get-DscConfigurationStatus devolve solicitação como tipo *consistência*
---------------------------------------------------------------------------------
Quando um nó estiver definido para o modo de atualização de EXTRAÇÃO, para cada operação de solicitação efetuada, o cmdlet Get-DscConfigurationStatus relatórios como o tipo de operação *consistência* em vez de *inicial*

**Resolução:** None.

<a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a>DscResource invocar o cmdlet não devolve mensagem pela ordem que foram produzidos
---------------------------------------------------------------------------------
O cmdlet Invoke-DscResource não devolver verboso, aviso, e mensagens de erro na ordem que foram produzidos por MMC ou o recursos de DSC.

**Resolução:** None.


<a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a>Recursos de DSC não é possível debugged facilmente quando utilizado com Invoke-DscResource
-----------------------------------------------------------------------
Quando o MMC está em execução no modo de depuração (consulte [recursos de DSC depuração](https://msdn.microsoft.com/powershell/dsc/debugresource) para obter mais detalhes), cmdlet Invoke-DscResource não fornecer informações sobre o espaço de execução para ligar para a depuração.
**Resolução:** detetar e ligue a execução com os cmdlets **Get-PSHostProcessInfo**, **Enter PSHostProcess** , **Get-espaço de execução** e **Espaço de execução de depuração** para depurar o recursos de DSC.

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


<a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a>Vários documentos configuração parcial para o mesmo nó não podem ter nomes de recursos idênticas
------------------------------------------------------------------------------------------

Para várias parciais configurações que são implementadas num único nó, nomes idênticos de recursos causa executam o erro de tempo.

**Resolução:** Utilize diferentes nomes para o mesmo mesmos recursos em diferentes configurações parciais.


<a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a>Início DscConfiguration – UseExisting não funciona com - Credential
------------------------------------------------------------------

Ao utilizar DscConfiguration início com o parâmetro – UseExisting, – credenciais parâmetro será ignorado. DSC utiliza a identidade do processo predefinido para continuar a operação. Isto faz com que erro quando é necessária uma credencial diferente para continuar no nó remoto.

**Resolução:** utilize CIM sessão para operações de DSC remotas:
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```


<a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a>Endereços IPv6 como nomes de nó em configurações de DSC
--------------------------------------------------
Endereços IPv6 como nomes de nó em scripts de configuração de DSC não são suportados nesta versão.

**Resolução:** None.


<a name="debugging-of-class-based-dsc-resources"></a>A depuração de recursos de DSC com base na classe
--------------------------------------
A depuração de recursos de DSC baseados em classe não é suportada nesta versão.

**Resolução:** None.


<a name="variables--functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a>As variáveis de & funções definidas no âmbito de $script no recurso baseado em classes de DSC não são mantidas em várias chamadas a um recurso de DSC
-------------------------------------------------------------------------------------------------------------------------------------

Várias chamadas consecutivas para início DSCConfiguration irão falhar se a configuração está a utilizar qualquer recurso com base na classe que possui variáveis ou funções definidas no âmbito de $script.

**Resolução:** definir todas as funções e as variáveis na própria classe de recursos de DSC. As variáveis de âmbito No $script/funções.


<a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a>A depuração de recurso DSC quando um recurso está a utilizar PSDscRunAsCredential
----------------------------------------------------------------------
A depuração de recurso DSC quando um recurso está a utilizar o *PSDscRunAsCredential* propriedade na configuração não é suportado nesta versão.

**Resolução:** None.


<a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a>PsDscRunAsCredential não é suportado para recursos de DSC composto
----------------------------------------------------------------

**Resolução:** propriedade de credencial de utilização, se disponível. Exemplo ServiceSet e WindowsFeatureSet


<a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a>*Get-DscResource-sintaxe* não reflete PsDscRunAsCredential corretamente
-------------------------------------------------------------------------
Get-DscResource-sintaxe não reflete PsDscRunAsCredential corretamente quando recurso marca-a como obrigatórios ou não o suporta.

**Resolução:** None. No entanto, a criação de configuração no ISE reflete metadados corretos sobre PsDscRunAsCredential propriedade quando utilizar o IntelliSense.


<a name="windowsoptionalfeature-is-not-available-in-windows-7"></a>WindowsOptionalFeature não está disponível no Windows 7
-----------------------------------------------------

O recurso de WindowsOptionalFeature DSC não está disponível no Windows 7. Este recurso necessita do módulo DISM e os cmdlets DISM que estão disponíveis a partir do Windows 8 e versões mais recentes do sistema operativo Windows.

<a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a>Para os recursos de DSC com base na classe, importação DscResource - ModuleVersion poderão não funcionar conforme esperado
------------------------------------------------------------------------------------------
Se o nó de compilação tem vários versão do módulo de recurso DSC baseado em classes, `Import-DscResource -ModuleVersion` não escolha a versão especificada e resulta no seguinte erro de compilação.

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**Resolução:** importar a versão necessária, definindo o *ModuleSpecification* de objeto para o `-ModuleName` com `RequiredVersion` chave especificada da seguinte forma:
``` PowerShell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

<a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a>Alguns recursos de DSC como recursos de registo podem começar a demorar muito tempo a processar o pedido.
--------------------------------------------------------------------------------------------------------------------------------

**Resolution1:** criar uma tarefa de agendamento que limpa a seguinte pasta periodicamente.
``` PowerShell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

**Resolution2:** alterar a configuração de DSC para limpar o *CommandAnalysis* pasta no final da configuração.
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
