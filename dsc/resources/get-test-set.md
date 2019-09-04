---
ms.date: 12/12/2018
keywords: DSC, PowerShell, configuração, instalação
title: Conjunto de testes Get
ms.openlocfilehash: 68738107cd4a222a13dd4afa158f0370953158ad
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215422"
---
# <a name="get-test-set"></a>Conjunto de testes Get

>Aplica-se a: Windows PowerShell 4,0, Windows PowerShell 5,0

![Métodos Get, Test e Set](../media/get-test-set.png)

A configuração de estado desejado do PowerShell é construída em um processo **Get**, **Test**e **set** . Os [recursos](resources.md) de DSC contêm métodos para concluir cada uma dessas operações. Em uma [configuração](../configurations/configurations.md), você define os blocos de recursos para preencher as chaves que se tornam parâmetros para os métodos **Get**, **Test**e **set** de um recurso.

Esta é a sintaxe para um bloco de recursos de **serviço** . O recurso de **serviço** configura os serviços do Windows.

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

Os métodos **Get**, **Test**e **set** do recurso de **serviço** terão blocos de parâmetro que aceitam esses valores.

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
> O idioma e o método usados para definir o recurso determinam como os métodos **Get**, **Test**e **set** serão definidos.

Como o recurso de **serviço** tem apenas uma chave necessária`Name`(), um recurso de bloco de **serviço** pode ser tão simples quanto isto:

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

Quando você compila a configuração acima, os valores que você especifica para uma chave são armazenados no arquivo ". mof" que é gerado. Para obter mais informações, consulte [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).

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

Quando aplicado, o [Configuration Manager local](../managing-nodes/metaConfig.md) (LCM) lerá o valor "spooler" do arquivo " `-Name` . mof" e o passará para o parâmetro dos métodos **Get**, **Test**e **set** para a instância "MyService" doRecurso de serviço.

## <a name="get"></a>Obter

O método **Get** de um recurso recupera o estado do recurso conforme ele é configurado no nó de destino. Esse estado é retornado como uma [tabela de hash](/powershell/module/microsoft.powershell.core/about/about_hash_tables). As chaves da **tabela de hash** serão os valores configuráveis, ou parâmetros, que o recurso aceita.

O método **Get** mapeia diretamente para o cmdlet [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) . Quando você chama `Get-DSCConfiguration`, o LCM executa o método **Get** de cada recurso na configuração aplicada no momento. O LCM usa os valores de chave armazenados no arquivo ". mof" como parâmetros para cada instância de recurso correspondente.

Essa é uma saída de exemplo de um recurso de **serviço** que configura o serviço de "spooler".

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

A saída mostra as propriedades de valor atual configuráveis pelo recurso de **serviço** .

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

O método de **teste** de um recurso determina se o nó de destino está em conformidade no momento com o *estado desejado*do recurso. O método de teste `$True` retorna `$False` ou apenas para indicar se o nó está em conformidade.
Quando você chama [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), o LCM chama o método de **teste** de cada recurso na configuração aplicada no momento. O LCM usa os valores de chave armazenados no arquivo ". mof" como parâmetros para cada instância de recurso correspondente.

Se o resultado de qualquer **teste** de recurso individual for `$False`, `Test-DSCConfiguration` o `$False` retornará indicando que o nó não está em conformidade. Se os métodos `$True`de **teste** de todos os `Test-DSCConfiguration` recursos `$True` retornarem, o retornará para indicar que o nó está em conformidade.

```powershell
Test-DSCConfiguration
```

```output
True
```

A partir do PowerShell 5,0, `-Detailed` o parâmetro foi adicionado. Especificar `-Detailed` as `Test-DSCConfiguration` causas para retornar um objeto que contém coleções de resultados para recursos em conformidade e sem conformidade.

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

Para obter mais informações, consulte [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)

## <a name="set"></a>Definir

O método **set** de um recurso tenta forçar o nó a ficar em conformidade com o *estado desejado*do recurso. O método **set** deve ser **idempotente**, o que significa que **set** pode ser executado várias vezes e sempre obter o mesmo resultado sem erros.  Quando você executa [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), o LCM percorre cada recurso na configuração aplicada no momento. O LCM recupera valores de chave para a instância de recurso atual do arquivo ". mof" e as usa como parâmetros para o método de **teste** . Se o método de teste `$True`retornar, o nó será compatível com o recurso atual e o método **set** será ignorado. Se o **teste** retornar `$False`, o nó não será compatível.  O LCM passa os valores de chave da instância de recurso como parâmetros para o método **set** do recurso, restaurando o nó para conformidade.

Ao especificar os `-Verbose` parâmetros `-Wait` e, você pode `Start-DSCConfiguration` observar o progresso do cmdlet. Neste exemplo, o nó já está em conformidade. A `Verbose` saída indica que o método **set** foi ignorado.

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

- [Visão geral do Azure DSC de Automação](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Configurando um servidor de pull SMB](../pull-server/pullServerSMB.md)
- [Configurando um cliente de pull](../pull-server/pullClientConfigID.md)
