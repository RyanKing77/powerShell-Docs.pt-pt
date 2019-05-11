---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Get-Test-Set
ms.openlocfilehash: e4aa7770bb5fc8b916b0c0a6488b1ccc0ef0ade9
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229509"
---
# <a name="get-test-set"></a>Get-Test-Set

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

![Métodos Get, Test e Set](/media/get-test-set.png)

PowerShell Desired State Configuration é construído em torno de um **Obtenha**, **teste**, e **definir** processo. DSC [recursos](resources.md) cada contém métodos para concluir cada uma destas operações. Num [Configuration](../configurations/configurations.md), define blocos de recurso para preencher as chaves que tornam-se de parâmetros para um recurso **obter**, **teste**, e **definir** métodos.

Esta é a sintaxe para uma **serviço** bloco de recursos. O **serviço** recursos configura os serviços do Windows.

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

O **obter**, **teste**, e **definir** métodos para o **serviço** recurso terão os blocos de parâmetro que aceitam estes valores.

```powershell
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [System.String]
        $Name,

        [System.String]
        [ValidateSet("Automatic", "Manual", "Disabled")]
        $StartupType,

        [System.String]
        [ValidateSet("LocalSystem", "LocalService", "NetworkService")]
        $BuiltInAccount,

        [System.Management.Automation.PSCredential]
        [ValidateNotNull()]
        $Credential,

        [System.String]
        [ValidateSet("Running", "Stopped")]
        $State="Running",

        [System.String]
        [ValidateNotNullOrEmpty()]
        $DisplayName,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Description,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Path,

        [System.String[]]
        [ValidateNotNullOrEmpty()]
        $Dependencies,

        [System.String]
        [ValidateSet("Present", "Absent")]
        $Ensure="Present"
    )
```

> [!NOTE]
> O idioma e o método usado para definir o recurso determina como o **Obtenha**, **teste**, e **definir** métodos serão definidos.

Uma vez que o **serviço** recurso tem apenas uma chave necessária (`Name`), um **serviço** bloquear recursos podem ser tão simples como este:

```powershell
Configuration TestConfig
{
    Import-DSCResource -Name Service
    Node localhost
    {
        Service "MyService"
        {
            Name = "Spooler"
        }
    }
}
```

Quando compilar a configuração acima, os valores que especificou para uma chave são armazenados no arquivo ". MOF" que é gerado. Para obter mais informações, consulte [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).

```
instance of MSFT_ServiceResource as $MSFT_ServiceResource1ref
{
SourceInfo = "::5::1::Service";
 ModuleName = "PsDesiredStateConfiguration";
 ResourceID = "[Service]MyService";
 Name = "Spooler";

ModuleVersion = "1.0";

 ConfigurationName = "Test";

};
```

Quando aplicada, o [Gestor de configuração Local](../managing-nodes/metaConfig.md) (LCM) irá ler o valor "Spooler" a partir do ficheiro ". MOF" e passá-lo para o `-Name` parâmetro do **obter**, **teste**, e **definir** métodos para a instância de "MyService" do **serviço** recursos.

## <a name="get"></a>Obter

O **obter** método de um recurso, obtém o estado do recurso, porque esta está configurada no nó de destino. Este estado é retornado como um [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables). As chaves do **hashtable** será o configuráveis valores ou parâmetros, aceita o recurso.

O **Obtenha** método é mapeado diretamente para o [Get-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet. Quando chama `Get-DSCConfiguration`, as execuções de LCM a **obter** método de cada recurso na configuração atualmente aplicada. O LCM utiliza os valores de chave armazenados no ficheiro ". MOF" como parâmetros para cada instância de recurso correspondente.

Esta é a saída de exemplo de um **serviço** recurso que configura o serviço de "Spooler".

```output
ConfigurationName    : Test
DependsOn            :
ModuleName           : PsDesiredStateConfiguration
ModuleVersion        : 1.1
PsDscRunAsCredential :
ResourceId           : [Service]Spooler
SourceInfo           :
BuiltInAccount       : LocalSystem
Credential           :
Dependencies         : {RPCSS, http}
Description          : This service spools print jobs and handles interaction with the printer.  If you turn off
                       this service, you won’t be able to print or see your printers.
DisplayName          : Print Spooler
Ensure               :
Name                 : Spooler
Path                 : C:\WINDOWS\System32\spoolsv.exe
StartupType          : Automatic
State                : Running
Status               :
PSComputerName       :
CimClassName         : MSFT_ServiceResource
```

O resultado mostra as propriedades do valor atual configurável, o **serviço** recursos.

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

## <a name="test"></a>Teste

O **teste** método de um recurso determina se o nó de destino está atualmente em conformidade com o recurso *pretendido estado*. O **teste** retorno do método `$True` ou `$False` apenas para indicar se o nó está em conformidade.
Quando chama [Test-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), as chamadas de LCM a **teste** método de cada recurso na configuração atualmente aplicada. O LCM utiliza os valores de chave armazenados no ficheiro ". MOF" como parâmetros para cada instância de recurso correspondente.

Se o resultado de qualquer recurso individual **teste** é `$False`, `Test-DSCConfiguration` devolve `$False` que indica que o nó não está em conformidade. Se todos os recursos **teste** métodos retornam `$True`, `Test-DSCConfiguration` devolve `$True` para indicar que o nó está em conformidade.

```powershell
Test-DSCConfiguration
```

```output
True
```

A partir do PowerShell 5.0, o `-Detailed` foi adicionado o parâmetro. Especificar `-Detailed` faz com que `Test-DSCConfiguration` retorne um objeto que contém coleções de resultados para os recursos em conformidade e não conformes.

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

Para obter mais informações, consulte [Test-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)

## <a name="set"></a>Definir

O **definir** método de um recurso tenta forçar o nó para ficarem em conformidade com o recurso *pretendido estado*. O **definir** método destina-se a ser **idempotentes**, que significa que **definir** poderia ser executado múltiplas vezes e obter sempre o mesmo resultado sem erros.  Quando executa [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), os ciclos de LCM por meio de cada recurso na configuração atualmente aplicada. O LCM recupera valores de chave para a instância atual do recurso do ficheiro ". MOF" e utiliza-as como parâmetros para o **teste** método. Se o **teste** retorno do método `$True`, o nó está em conformidade com o recurso atual e o **definir** método é ignorado. Se o **teste** devolve `$False`, o nó está em conformidade.  O LCM passa o recurso de valores de chave da instância como parâmetros para o recurso **definir** método, restaurar o nó para conformidade.

Ao especificar os `-Verbose` e `-Wait` parâmetros, pode ver o progresso do `Start-DSCConfiguration` cmdlet. Neste exemplo, o nó já está em conformidade. O `Verbose` resultado indica que o **definir** método foi ignorado.

```
PS> Start-DSCConfiguration -Verbose -Wait -UseExisting

VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
ApplyConfiguration,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer SERVER01 with user sid
S-1-5-21-124525095-708259637-1543119021-1282804.
VERBOSE: [SERVER01]:                            [] Starting consistency engine.
VERBOSE: [SERVER01]:                            [] Checking consistency for current configuration.
VERBOSE: [SERVER01]:                            [DSCEngine] Importing the module
C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\DscResources\MSFT_ServiceResource\MSFT
_ServiceResource.psm1 in force mode.
VERBOSE: [SERVER01]: LCM:  [ Start  Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ Start  Test     ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [[Service]Spooler] Importing the module MSFT_ServiceResource in
force mode.
VERBOSE: [SERVER01]: LCM:  [ End    Test     ]  [[Service]Spooler]  in 0.2540 seconds.
VERBOSE: [SERVER01]: LCM:  [ Skip   Set      ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ End    Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [] Consistency check completed.
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Time taken for configuration job to complete is 1.379 seconds
```

## <a name="see-also"></a>Consulte também

- [Descrição geral de DSC de automatização do Azure](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Como configurar um servidor de solicitação SMB](../pull-server/pullServerSMB.md)
- [Configurar um cliente de solicitação](../pull-server/pullClientConfigID.md)
