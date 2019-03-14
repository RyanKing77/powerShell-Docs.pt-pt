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
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a>Desired State Configuration (DSC) conhecido limitações e problemas

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a>Alteração de última hora: Certificados utilizados para encriptação/desencriptação palavras-passe em configurações de DSC podem não funcionar após a instalação do WMF 5.0 RTM

Em versões do WMF 4.0 e pré-visualização do WMF 5.0, DSC não permitiria palavras-passe na configuração do comprimento mais de 121 carateres. DSC foi forçar a usar senhas curtas, mesmo que a palavra-passe longa e forte foi assim o desejar. Esta alteração de última hora permite que as senhas tenham de comprimento arbitrário na configuração do DSC.

**Resolução:** Voltar a criar o certificado com a utilização de encriptação de dados ou a chave de encriptação de chave e utilização de chave de melhorada de encriptação de documentos (1.3.6.1.4.1.311.80.1). Artigo da TechNet <https://technet.microsoft.com/library/dn807171.aspx> tem mais informações.

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a>Cmdlets de DSC pode falhar após a instalação do WMF 5.0 RTM

Start-dscconfiguration para e os outros cmdlets do DSC pode falhar após a instalação do WMF 5.0 RTM com o seguinte erro:
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

**Resolução:** Elimine DSCEngineCache.mof ao executar o seguinte comando numa sessão do PowerShell elevada (executar como administrador):

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a>Cmdlets de DSC poderá não funcionar se WMF 5.0 RTM é instalada sobre o WMF 5.0 produção pré-visualização

**Resolução:** Execute o seguinte comando numa sessão elevada do PowerShell (executar como administrador):
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a>LCM pode entrar num estado instável, ao utilizar Get-dscconfiguration para no DebugMode

Se for LCM no DebugMode, premir CTRL + C para parar o processamento de Get-dscconfiguration para pode fazer com que o MMC para ir para um estado instável desse tipo que a maioria dos cmdlets de DSC não funcionará.

**Resolução:** Não, pressione CTRL + C durante a depuração do cmdlet Get-dscconfiguration para.

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a>Stop-dscconfiguration para poderão não responder no DebugMode

Se for LCM no DebugMode, Stop-dscconfiguration para poderão não responder ao tentar parar uma operação iniciada pelo Get-dscconfiguration para

**Resolução:** Concluir a depuração da operação iniciada pelo Get-dscconfiguration para, conforme descrito na secção '[recursos de DSC de depuração](https://msdn.microsoft.com/powershell/dsc/debugresource)'.

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a>Nenhuma mensagem de erro detalhado são mostradas na DebugMode

Se for LCM no DebugMode, nenhuma mensagem de erro detalhado é apresentadas a partir dos recursos de DSC.

**Resolução:** Desativar *DebugMode* para ver as mensagens verbosas de recurso

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a>Operações de invocar-DscResource não podem ser obtidas pelo cmdlet Get-DscConfigurationStatus

Depois de utilizar o cmdlet Invoke-DscResource diretamente invocar métodos de qualquer recurso, não não possível obter os registos de tal operação por meio de Get-DscConfigurationStatus num momento posterior.

**Resolução:** Nenhum.

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a>Operações de ciclo do Get-DscConfigurationStatus devolve pull como tipo *consistência*

Quando um nó é definido para o modo de atualização de SOLICITAÇÃO, para cada operação de solicitação realizada, o cmdlet Get-DscConfigurationStatus relatórios como o tipo de operação *consistência* em vez de *inicial*

**Resolução:** Nenhum.

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a>Cmdlet Invoke-DscResource não retorna mensagens na ordem em que foram produzidos

O cmdlet Invoke-DscResource não devolve verboso, aviso, e mensagens de erro na ordem em que foram produzidas pelo LCM ou o recurso de DSC.

**Resolução:** Nenhum.

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a>Recursos de DSC não pode ser depurados facilmente quando utilizado com Invoke-DscResource

Quando LCM está em execução no modo de depuração (consulte [recursos de DSC de depuração](https://msdn.microsoft.com/powershell/dsc/debugresource) para obter mais detalhes), cmdlet Invoke-DscResource não lhe dá informações sobre o espaço de execução para ligar para depuração.
**Resolução:** Detetar e anexar ao espaço de execução com os cmdlets **Get-PSHostProcessInfo**, **Enter PSHostProcess** , **Get-Runspace** e **depuração-Runspace** para depurar o recurso de DSC.

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

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a>Vários documentos de configuração parcial para o mesmo nó não podem ter nomes de recursos idênticos

Para várias parciais configurações que são implementadas num único nó, nomes idênticos de recursos causa executam erro de tempo.

**Resolução:** Use nomes diferentes para os mesmos até mesmo recursos em diferentes configurações parciais.

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a>Start-dscconfiguration para – UseExisting não funciona com - de credenciais

Ao utilizar o início-dscconfiguration para com o parâmetro – UseExisting, – Credential parâmetro é ignorado. DSC utiliza a identidade do processo padrão para continuar a operação. Isso faz com que o erro quando uma credencial diferente é necessária para continuar no nó remoto.

**Resolução:** Utilize a sessão CIM para operações remotas do DSC:
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a>Endereços IPv6 como nomes de nó em configurações de DSC

Endereços IPv6 como nomes de nó em scripts de configuração de DSC não são suportados nesta versão.

**Resolução:** Nenhum.

## <a name="debugging-of-class-based-dsc-resources"></a>Depuração de recursos de DSC baseados em classe

Depuração de recursos de DSC baseados em classe não é suportada nesta versão.

**Resolução:** Nenhum.

## <a name="variables--functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a>As variáveis e funções definidas no âmbito de $script no recurso baseado em classes de DSC não são mantidas em várias chamadas para um recurso de DSC

Várias chamadas consecutivas para Start-dscconfiguration para irão falhar se a configuração está a utilizar qualquer recurso baseado em classes que tem variáveis ou funções definidas no âmbito de $script.

**Resolução:** Defina todas as variáveis e funções na própria classe de recursos de DSC. Variáveis de âmbito de No $script/funções.

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a>A depuração de recursos de DSC quando um recurso está a utilizar PSDscRunAsCredential

A depuração de recursos de DSC quando um recurso está a utilizar o *PSDscRunAsCredential* propriedade na configuração não é suportado nesta versão.

**Resolução:** Nenhum.

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a>PsDscRunAsCredential não é suportado para recursos compostos de DSC

**Resolução:** Utilize a propriedade de credencial, se estiver disponível. Exemplo ServiceSet e WindowsFeatureSet

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a>*Get-DscResource-sintaxe* não reflete PsDscRunAsCredential corretamente

Get-DscResource-sintaxe não reflete PsDscRunAsCredential corretamente quando o recurso de marca-o como obrigatórias ou não a suporta.

**Resolução:** Nenhum. No entanto, a criação de configuração no ISE reflete os metadados corretos sobre PsDscRunAsCredential propriedade ao usar o IntelliSense.

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a>WindowsOptionalFeature não está disponível no Windows 7

O recurso de DSC WindowsOptionalFeature não está disponível no Windows 7. Este recurso requer o módulo DISM e os cmdlets DISM que estão disponíveis a partir do Windows 8 e versões mais recentes do sistema operativo Windows.

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a>Para os recursos de DSC baseados em classe, Import-DscResource - ModuleVersion poderá não funcionar conforme esperado

Se o nó de compilação tem vários versão do módulo de recursos DSC baseada em classes, `Import-DscResource -ModuleVersion` não escolha a versão especificada e resulta no seguinte erro de compilação.

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**Resolução:** Importar a versão necessária, definindo a *ModuleSpecification* objeto para o `-ModuleName` com `RequiredVersion` chave especificada da seguinte forma:

``` PowerShell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a>Alguns recursos de DSC, como o recurso de registro podem começar a demorar muito tempo a processar o pedido.

**Resolution1:** Crie uma tarefa de agendamento que limpa a seguinte pasta periodicamente.

``` PowerShell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

**Resolution2:** Alterar a configuração de DSC para limpar os *CommandAnalysis* pasta no final da configuração.

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
