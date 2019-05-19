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
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a>Desired State Configuration (DSC) conhecido limitações e problemas

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a>Alteração de última hora: Certificados utilizados para encriptação/desencriptação palavras-passe em configurações de DSC podem não funcionar após a instalação do WMF 5.0 RTM

Em versões do WMF 4.0 e pré-visualização do WMF 5.0, DSC não permitiria palavras-passe na configuração do comprimento mais de 121 carateres. DSC foi forçar a usar senhas curtas, mesmo que a palavra-passe longa e forte foi assim o desejar. Esta alteração de última hora permite que as senhas tenham de comprimento arbitrário na configuração do DSC.

**Resolução:** Voltar a criar o certificado com a utilização de encriptação de dados ou a chave de encriptação de chave e utilização de chave de melhorada de encriptação de documentos (1.3.6.1.4.1.311.80.1). Para obter mais informações, consulte [Protect CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a>Cmdlets de DSC pode falhar após a instalação do WMF 5.0 RTM

`Start-DscConfiguration` e outros cmdlets do DSC pode falhar após a instalação do WMF 5.0 RTM com o seguinte erro:

```Output
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

Se for LCM no DebugMode, premir CTRL + C para parar o processamento de `Get-DscConfiguration` pode fazer com que o MMC para ir para um estado instável desse tipo que a maioria dos cmdlets de DSC não funcionará.

**Resolução:** Não prima CTRL + C durante a depuração `Get-DscConfiguration` cmdlet.

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a>Stop-dscconfiguration para poderão não responder no DebugMode

Se está a LCM DebugMode, `Stop-DscConfiguration` poderão não responder ao tentar parar uma operação iniciada por `Get-DscConfiguration`

**Resolução:** Concluir a depuração da operação iniciada pelo `Get-DscConfiguration` conforme descrito na [recursos de DSC de depuração](/powershell/dsc/troubleshooting/debugResource).

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a>Nenhuma mensagem de erro detalhado são mostradas na DebugMode

Se está a LCM **DebugMode**, nenhuma mensagem de erro detalhado é apresentadas a partir dos recursos de DSC.

**Resolução:** Desativar **DebugMode** para ver as mensagens verbosas de recurso

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a>Operações de invocar-DscResource não podem ser obtidas pelo cmdlet Get-DscConfigurationStatus

Depois de usar `Invoke-DscResource` cmdlet para invocar diretamente os métodos de qualquer recurso, os registos de tal operação não pode ser obtido por meio de `Get-DscConfigurationStatus`.

**Resolução:** Nenhum.

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a>Operações de ciclo do Get-DscConfigurationStatus devolve pull como tipo **consistência**

Quando um nó é definido para o modo de atualização de SOLICITAÇÃO, para cada operação de solicitação realizada, `Get-DscConfigurationStatus` o tipo de operação como relatórios do cmdlet **consistência** em vez de *inicial*

**Resolução:** Nenhum.

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a>Cmdlet Invoke-DscResource não retorna mensagens na ordem em que foram produzidos

O `Invoke-DscResource` cmdlet não devolve verboso, aviso, e mensagens de erro na ordem em que foram produzidas pelo LCM ou o recurso de DSC.

**Resolução:** Nenhum.

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a>Recursos de DSC não pode ser depurados facilmente quando utilizado com Invoke-DscResource

Quando LCM está em execução no modo de depuração, `Invoke-DscResource` cmdlet não lhe dá informações sobre o espaço de execução para ligar para depuração. Para obter mais informações, consulte [recursos de DSC de depuração](/powershell/dsc/troubleshooting/debugResource).

**Resolução:** Detetar e anexar ao espaço de execução com os cmdlets `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` e `Debug-Runspace` para depurar o recurso de DSC.

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

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a>Vários documentos de configuração parcial para o mesmo nó não podem ter nomes de recursos idênticos

Para várias parciais configurações que são implementadas num único nó, nomes idênticos de recursos causa executam erro de tempo.

**Resolução:** Use nomes diferentes para os mesmos até mesmo recursos em diferentes configurações parciais.

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a>Start-dscconfiguration para – UseExisting não funciona com - de credenciais

Ao usar `Start-DscConfiguration` com **UseExisting** parâmetro, o **credencial** parâmetro é ignorado. DSC utiliza a identidade do processo padrão para continuar a operação. Isso faz com que o erro quando uma credencial diferente é necessária para continuar no nó remoto.

**Resolução:** Utilize a sessão CIM para operações remotas do DSC:

```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a>Endereços IPv6 como nomes de nó em configurações de DSC

Endereços IPv6 como nomes de nó em scripts de configuração de DSC não são suportados nesta versão.

**Resolução:** Nenhum.

## <a name="debugging-of-class-based-dsc-resources"></a>Depuração de `Class-Based` recursos de DSC

Depuração de recursos de DSC baseados em classe não é suportada nesta versão.

**Resolução:** Nenhum.

## <a name="variables-and-functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a>Variáveis e funções definidas no âmbito de $script no recurso baseado em classes de DSC não são mantidas em várias chamadas para um recurso de DSC

Várias chamadas consecutivas para `Start-DSCConfiguration` falha se a configuração está a utilizar qualquer recurso baseado em classes que tem variáveis ou funções definidas no `$script` âmbito.

**Resolução:** Defina todas as variáveis e funções na própria classe de recursos de DSC. Não `$script` definir o âmbito variáveis/funções.

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a>A depuração de recursos de DSC quando um recurso está a utilizar PSDscRunAsCredential

A depuração de recursos de DSC quando um recurso está a utilizar o **PSDscRunAsCredential** propriedade na configuração não é suportada nesta versão.

**Resolução:** Nenhum.

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a>PsDscRunAsCredential não é suportado para recursos compostos de DSC

**Resolução:** Utilize a propriedade de credencial, se estiver disponível. Exemplo ServiceSet e WindowsFeatureSet

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a>Get-DscResource-sintaxe não reflete PsDscRunAsCredential corretamente

O **sintaxe** parâmetro não reflete **PsDscRunAsCredential** corretamente quando recurso marca-o como obrigatórias ou não a suporta.

**Resolução:** Nenhum. No entanto, a criação de configuração no ISE reflete metadados corretos sobre **PsDscRunAsCredential** propriedade ao usar o IntelliSense.

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a>WindowsOptionalFeature não está disponível no Windows 7

O **WindowsOptionalFeature** recursos de DSC não estão disponível no Windows 7. Este recurso requer o módulo DISM e os cmdlets DISM que estão disponíveis a partir do Windows 8 e versões mais recentes do sistema operativo Windows.

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a>Para os recursos de DSC baseados em classe, Import-DscResource - ModuleVersion poderá não funcionar conforme esperado

Se o nó de compilação tem várias versões do módulo de recursos DSC baseada em classes, `Import-DscResource -ModuleVersion` não escolha a versão especificada e resulta no seguinte erro de compilação.

```Output
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s):
 "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**Resolução:** Importar a versão necessária, definindo a **ModuleSpecification** objeto para o **ModuleName** parâmetro com **RequiredVersion** chave especificada da seguinte forma:

```powershell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a>Alguns recursos de DSC, como o recurso de registro podem começar a demorar muito tempo a processar o pedido.

**Resolução 1:** Crie uma tarefa de agendamento que limpa a seguinte pasta periodicamente.

```powershell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

**Resolução 2:** Alterar a configuração de DSC para limpar os *CommandAnalysis* pasta no final da configuração.

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
