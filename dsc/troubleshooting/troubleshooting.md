---
ms.date: 10/30/2018
keywords: DSC, powershell, configuração, a configuração
title: Resolução de Problemas de DSC
ms.openlocfilehash: 2a0d2138f30573b9ae6cf52d8b106a05f1193407
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229531"
---
# <a name="troubleshooting-dsc"></a>Resolução de Problemas de DSC

_Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0_

Este tópico descreve formas de resolver problemas de DSC quando surgem problemas.

## <a name="winrm-dependency"></a>Dependência de WinRM

Windows PowerShell Desired State Configuration (DSC) depende de WinRM. WinRM não está ativado por padrão no Windows Server 2008 R2 e Windows 7. Executar `Set-WSManQuickConfig`, no Windows PowerShell elevados sessão, para ativar o WinRM.

## <a name="using-get-dscconfigurationstatus"></a>Usando Get-DscConfigurationStatus

O [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet obtém informações sobre o estado da configuração a partir de um nó de destino. Um objeto avançado for retornado com informações de alto nível sobre se é ou não a execução de configuração foi concluída com êxito ou não. Pode examinar o objeto para detetar informações sobre a configuração executar como:

- Todos os recursos que falharam
- Qualquer recurso que solicitou uma reinicialização
- Executam definições de configuração de meta no momento da configuração
- Etc.

O conjunto de parâmetros seguintes devolve as informações de estado para a última configuração executar:

```
Get-DscConfigurationStatus [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```
O conjunto de parâmetros seguintes devolve as informações de estado para execuções de configuração de todas as anteriores:

```
Get-DscConfigurationStatus -All
                           [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

## <a name="example"></a>Exemplo

```powershell
PS C:\> $Status = Get-DscConfigurationStatus

PS C:\> $Status

Status         StartDate                Type            Mode    RebootRequested        NumberOfResources
------        ---------                ----            ----    ---------------        -----------------
Failure        11/24/2015  3:44:56     Consistency        Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName     :    MyService
DependsOn             :
ModuleName            :    PSDesiredStateConfiguration
ModuleVersion         :    1.1
PsDscRunAsCredential  :
ResourceID            :    [File]ServiceDll
SourceInfo            :    c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds     :    0.19
Error                 :    SourcePath must be accessible for current configuration. The related file/directory is:
                           \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState            :
InDesiredState        :    False
InitialState          :
InstanceName          :    ServiceDll
RebootRequested       :    False
ResourceName          :    File
StartDate             :    11/24/2015  3:44:56
PSComputerName        :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a>Meu script não será executado: Utilizar o DSC registos para diagnosticar erros de script

Como todos os Windows software, DSC registra os erros e eventos no [registos](/windows/desktop/EventLog/about-event-logging) que podem ser visualizados a partir do [Visualizador de eventos](https://support.microsoft.com/hub/4338813/windows-help).
Examinar estes registos pode ajudar a compreender por que motivo uma determinada operação falha e como impedir a falha no futuro. Escrita de scripts de configuração pode ser complicada, por isso facilitar o controlo de erros como autor de, use o recurso de Log de DSC para controlar o progresso da sua configuração no registo de eventos analíticos de DSC.

## <a name="where-are-dsc-event-logs"></a>Onde estão os registos de eventos de DSC?

No Visualizador de eventos, os eventos de DSC são em: **Aplicações e serviços registos/Microsoft/Windows/Desired State Configuration**

O cmdlet do PowerShell correspondente [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent), também pode ser executado para ver os registos de eventos:

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

Conforme mostrado acima, o nome do registo principal do DSC está **Microsoft -> Windows -> DSC** (outros nomes de registo no Windows não são mostrados aqui por questões de brevidade). O nome principal é acrescentado ao nome do canal para criar o nome do registo concluída. O motor de DSC escreve principalmente em três tipos de registos: [Registos de operacional, analítico e depuração](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)). Desde a análise e os registos de depuração estão desativados por predefinição, deve ativá-los no Visualizador de eventos. Para tal, abra o Visualizador de eventos ao escrever Show-registo de eventos do Windows PowerShell; ou, clique nas **começar** botão, clique em **painel de controlo**, clique em **ferramentas administrativas**e, em seguida, clique em **Visualizador de eventos**.
Sobre o **View** menu no Visualizador de eventos, clique em **Mostrar depurar registos analíticos e**. É o nome do registo para o canal analítico **Microsoft-Windows-Dsc/analítico**, e o canal de depuração é **Microsoft-Windows-Dsc/Debug**. Também pode utilizar o [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) utilitário para ativar os registos, conforme mostrado no exemplo seguinte.

```powershell
wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a>O que contêm os registos de DSC?

Registos de DSC são divididos ao longo de três canais de registo com base na importância da mensagem. O registo operacional no DSC contém todas as mensagens de erro e pode ser utilizado para identificar um problema. O registo de análise tem um volume maior de eventos e pode identificar em que ocorreu o erro (s). Este canal também contém as mensagens verbosas (se houver). O registo de depuração contém registos que podem ajudar a compreender como os erros ocorreram. Mensagens de eventos de DSC são estruturadas, de modo a que todas as mensagens de evento começa com um ID de tarefa que representa exclusivamente uma operação de DSC. O exemplo abaixo tenta obter a mensagem do primeiro evento registado para o registo DSC operacional.

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

Eventos de DSC são registados numa estrutura específica que permite ao usuário para agregar eventos a partir de uma tarefa de DSC. A estrutura é o seguinte:

```
Job ID : <Guid>
<Event Message>
```

## <a name="gathering-events-from-a-single-dsc-operation"></a>Recolha de eventos de uma única operação de DSC

Registos de eventos de DSC conter eventos gerados pelo várias operações de DSC. No entanto, normalmente será preocupados com apenas uma determinada operação com os detalhes. Todos os registos de DSC podem ser agrupados pela propriedade de ID de tarefa que é exclusiva para cada operação de DSC. O ID da tarefa é apresentado como o primeiro valor de propriedade em todos os eventos de DSC. Os seguintes passos explicam como a acumular todos os eventos numa estrutura de matriz agrupados.

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>

wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
wevtutil.exe set-log "Microsoft-Windows-Dsc/Debug" /q:True /e:true

<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>

Get-DscLocalConfigurationManager

<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>

$DscEvents=[System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Debug" -Oldest)


<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations = $DscEvents | Group {$_.Properties[0].value}
```

Aqui, a variável `$SeparateDscOperations` com registos agrupados pela tarefa de IDs. Cada elemento de matriz desta variável representa um grupo de eventos registados por uma operação de DSC diferente, permitindo o acesso para obter mais informações sobre os registos.

```
PS C:\> $SeparateDscOperations

Count Name                      Group
----- ----                      -----
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....

PS C:\> $SeparateDscOperations[0].Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
```

Pode extrair os dados na variável `$SeparateDscOperations` usando [Where-Object](/powershell/module/microsoft.powershell.core/where-object). Seguem-se cinco cenários em que pode querer extrair dados para resolução de problemas de DSC:

### <a name="1-operations-failures"></a>1: Falhas de operações

Todos os eventos possuem [níveis de gravidade](/windows/desktop/WES/defining-severity-levels). Estas informações podem ser utilizadas para identificar os eventos de erro:

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}

Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a>2: Detalhes das operações executadas na última meia hora

`TimeCreated`, uma propriedade de todos os eventos do Windows, indica o tempo que o evento foi criado. Comparar essa propriedade com um objeto de data/hora específico pode ser utilizado para filtrar todos os eventos:

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}

Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a>3: Mensagens da operação mais recente

A operação mais recente é armazenada no primeiro índice do grupo de matriz `$SeparateDscOperations`.
Consultas de mensagens do grupo para o índice 0 retorna todas as mensagens para a operação mais recente:

```powershell
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Consistency check completed.
```

### <a name="4-error-messages-logged-for-recent-failed-operations"></a>4: Mensagens de erro registadas para operações com falhas recentes

`$SeparateDscOperations[0].Group` contém um conjunto de eventos para a operação mais recente. Execute o `Where-Object` cmdlet para filtrar os eventos com base nos respetivos nomes a apresentar de nível. Os resultados são armazenados no `$myFailedEvent` variável, que podem ser ainda mais examinadas para obter a mensagem de evento:

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message

Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a>5: Todos os eventos gerados para um ID de tarefa específica.

`$SeparateDscOperations` é uma matriz de grupos, cada um com o nome como o ID exclusivo de tarefa. Ao executar o `Where-Object` cmdlet, pode extrair esses grupos de eventos que tem um ID de tarefa específica:

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
```

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a>Registos de utilização xDscDiagnostics para analisar o DSC

**xDscDiagnostics** é um módulo do PowerShell que consiste em várias funções que podem ajudar a analisar falhas de DSC no seu computador. Estas funções podem ajudar a identificar todos os eventos locais de últimos de DSC de operações ou eventos de DSC em computadores remotos (com credenciais válidas). Aqui, o termo operação DSC é usado para definir uma execução DSC exclusiva única desde seu início para o respetivo fim. Por exemplo, `Test-DscConfiguration` seria uma operação de DSC separada. Da mesma forma, todos os outro cmdlet no DSC (como `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) cada identificado como operações de DSC separadas. As funções são explicadas em [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics). A ajuda está disponível através da execução `Get-Help <cmdlet name>`.

### <a name="getting-details-of-dsc-operations"></a>A obter os detalhes das operações de DSC

O `Get-xDscOperation` função permite-lhe encontrar os resultados das operações de DSC que são executados num ou vários computadores e retorna um objeto que contém a coleção de eventos produzido por cada operação de DSC. Por exemplo, na seguinte saída, três comandos foram executados. Primeiro transmitido e a outra dois falhou. Esses resultados estão resumidos na saída do `Get-xDscOperation`.

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

Também pode especificar que pretende que apenas os resultados para as operações mais recentes, utilizando o `Newest` parâmetro:

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation -Newest 5
ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   2          6/23/2016 4:36:54 PM  Success  5c06402b-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   3          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   4          6/23/2016 4:36:54 PM  Success  5c06402a-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   5          6/23/2016 4:36:51 PM  Success                                        {@{Message=; TimeC...
```

### <a name="getting-details-of-dsc-events"></a>A obter os detalhes de eventos de DSC

O `Trace-xDscOperation` cmdlet devolve um objeto que contém uma coleção de eventos, seus tipos de evento, e a mensagem de saída gerados a partir de uma determinada operação de DSC. Normalmente, quando encontrar uma falha em qualquer uma das operações usando `Get-xDscOperation`, teria de rastreio essa operação para descobrir qual dos eventos provocou uma falha.

Utilize o `SequenceID` parâmetro para obter os eventos para uma operação específica de um computador específico.
Por exemplo, se especificar uma `SequenceID` 9, `Trace-xDscOperaion` obter o rastreio para a operação de DSC que foi 9th da última operação:

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -SequenceID 9

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Running consistency engine.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM The local configuration manager is updating the PSModulePath to WindowsPowerShell\Modules;C:\Prog...
SRV1   OPERATIONAL  6/24/2016 10:51:53 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Operation Consistency Check or Pull completed successfully.
```

Passar o **GUID** atribuído a uma operação específica do DSC (conforme devolvido pelo `Get-xDscOperation` cmdlet) para obter os detalhes do evento para essa operação de DSC:

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -JobID 9e0bfb6b-3a3a-11e6-9165-00155d390509

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Starting consistency engine.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Current.mof.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with resource name [WindowsFeature]DSC...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCServiceFeature] True in 0.3130 sec...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with resource name [xDSCWebService]P...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Ensure
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Port
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Physical Path ...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check State
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Get Full Path for We...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCPullServer] True in 0.0160 seconds.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Consistency check completed.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
```

Tenha em atenção que, uma vez que `Trace-xDscOperation` agrega eventos de análise, depuração e operacional registos, que irá solicitar-lhe ativar estes registos, conforme descrito acima.

Em alternativa, pode recolher informações sobre os eventos ao guardar a saída de `Trace-xDscOperation` numa variável. Pode utilizar os seguintes comandos para apresentar todos os eventos para uma determinada operação de DSC.

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

Esta ação apresenta os mesmos resultados como o `Get-WinEvent` cmdlet, como no resultado abaixo:

```output
   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
6/23/2016 1:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 1:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:07:00 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:07:01 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:36:56 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:06:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:06:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:36:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:06:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:36:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:36:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:36:56 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:36:57 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 8:06:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
```

O ideal é que, primeiro deve ser usada `Get-xDscOperation` para listar o último DSC alguns configuração é executado nas suas máquinas. Ao seguir esta, é possível examinar qualquer operação única (com seu SequenceID ou JobID) com `Trace-xDscOperation` para descobrir o que fiz em segundo plano.

### <a name="getting-events-for-a-remote-computer"></a>Obter eventos para um computador remoto

Utilize o `ComputerName` parâmetro do `Trace-xDscOperation` cmdlet para obter os detalhes do evento num computador remoto. Antes de poder fazer isto, terá de criar uma regra de firewall para permitir a administração remota no computador remoto:

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```

Agora pode especificar esse computador na sua chamada a `Trace-xDscOperation`:

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -ComputerName SRV2 -Credential Get-Credential -SequenceID 5

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 f...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Starting consistency...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Curr...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature,...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCSer...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with re...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCP...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with ...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Consistency check co...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
```

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a>Não atualizar os meus recursos: Como repor a cache

O motor de DSC armazena em cache recursos implementados como um módulo do PowerShell para fins de eficiência.
No entanto, isso pode causar problemas quando estiver a criação de um recurso e testá-lo em simultâneo porque DSC irá carregar a versão em cache até que o processo seja reiniciado. A única forma de tornar o DSC carregar a versão mais recente é explicitamente interromper o processo que hospeda o mecanismo de DSC.

Da mesma forma, quando executa `Start-DscConfiguration`, depois de adicionar e modificar um recurso personalizado, a modificação pode não ser executado, a menos que ou até que, o computador é reiniciado. Isto acontece porque o DSC é executado no processo de anfitrião do fornecedor de WMI (WmiPrvSE) e, normalmente, existem muitas instâncias de WmiPrvSE em execução ao mesmo tempo. Quando reiniciar, o processo de host é reiniciado e a cache está desmarcada.

Para reciclar a configuração e limpar o cache sem reiniciar com êxito, tem de parar e, em seguida, reinicie o processo de anfitrião. Isso pode ser feito numa base por instância, na qual identifique o processo de pará-la e reiniciá-lo. Em alternativa, pode utilizar `DebugMode`, como demonstrado abaixo, para recarregar o recurso de DSC do PowerShell.

Para identificar o processo que está a alojar o motor de DSC e pará-la numa base por instância, pode listar o ID de processo do WmiPrvSE que está a alojar o motor de DSC. Em seguida, para atualizar o fornecedor, pare o processo de WmiPrvSE utilizando os comandos abaixo e execute **Start-dscconfiguration para** novamente.

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers |
Where-Object {$_.provider -like 'dsccore'} |
Select-Object -ExpandProperty HostProcessIdentifier

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## <a name="using-debugmode"></a>Usando DebugMode

Pode configurar o DSC Local Configuration Manager (LCM) para utilizar `DebugMode` sempre limpar a cache quando o processo de host é reiniciado. Quando definido como **TRUE**, ele faz com que o mecanismo sempre recarregar o recurso de DSC do PowerShell. Depois de concluída a escrever o seu recurso, pode configurá-lo para **FALSE** e o mecanismo irá reverter para o seu comportamento de colocação em cache os módulos.

Segue-se uma demonstração para mostrar como `DebugMode` automaticamente pode atualizar a cache. Em primeiro lugar, vamos examinar a configuração predefinida:

```powershell
PS C:\> Get-DscLocalConfigurationManager
```

```output
AllowModuleOverwrite           : False
CertificateID                  :
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     :
DebugMode                      : {None}
DownloadManagerCustomData      :
DownloadManagerName            :
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :
```

Pode ver que `DebugMode` está definido como **"None"**.

Para configurar o `DebugMode` demonstração, utilize o seguinte recurso do PowerShell:

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1" | Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
}
```

Agora, criar uma configuração usando o recurso acima, chamado `TestProviderDebugMode`:

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

Verá que o conteúdo do ficheiro: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` é **1**.

Agora, atualize o código do provedor usando o seguinte script:

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput" | Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

Este script gera um número aleatório e atualiza o código do provedor em conformidade. Com o `DebugMode` definido como FALSO, o conteúdo do ficheiro "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" nunca são alterados.

Agora, defina `DebugMode` para **"ForceModuleImport"** no seu script de configuração:

```powershell
LocalConfigurationManager
{
    DebugMode = "ForceModuleImport"
}
```

Ao executar novamente o script acima, verá que o conteúdo do ficheiro é diferente cada vez. (Pode executar `Get-DscConfiguration` registá-lo). Segue-se o resultado das duas execuções adicionais (os resultados podem ser diferentes quando executar o script):

```powershell
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
20                                      localhost

PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
14                                      localhost
```

## <a name="dsc-returns-unexpected-response-code-internalservererror-when-registering-with-windows-pull-server"></a>DSC devolve "código de resposta inesperado InternalServerError" quando registar o servidor de solicitação do Windows

Ao aplicar um metaconfiguration a um servidor para registá-lo com uma instância do servidor de solicitação do Windows, que poderá encontrar o seguinte erro.

```PowerShell
Registration of the Dsc Agent with the server https://<serverfqdn>:8080/PSDSCPullServer.svc failed. The underlying error is: The attempt to register Dsc Agent with AgentId <ID> with the server 
https://<serverfqdn>:8080/PSDSCPullServer.svc/Nodes(AgentId='<ID>') returned unexpected response code InternalServerError. .
    + CategoryInfo          : InvalidResult: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : RegisterDscAgentUnsuccessful,Microsoft.PowerShell.DesiredStateConfiguration.Commands.RegisterDscAgentCommand
    + PSComputerName        : <computername>
```

Isto pode ocorrer quando o certificado utilizado no servidor para criptografar o tráfego tem um nome comum (CN) que é diferente do nome DNS utilizado por nó para resolver o URL.
Atualize a instância de servidor de solicitação do Windows para utilizar um certificado com um nome corrigido.

## <a name="see-also"></a>Veja Também

### <a name="concepts"></a>Conceitos

- [Criar recursos do Windows personalizados do PowerShell Desired State Configuration](../resources/authoringResource.md)

### <a name="other-resources"></a>Outros Recursos

- [Windows PowerShell Desired State Configuration Cmdlets](/powershell/module/psdesiredstateconfiguration/)
