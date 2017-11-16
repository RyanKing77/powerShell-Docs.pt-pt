---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Resolução de problemas de DSC"
ms.openlocfilehash: 9b1266b9c8923474005760ef78b05d570efdde37
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="troubleshooting-dsc"></a>Resolução de problemas de DSC

>Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

Este tópico descreve opções para solucionar DSC quando ocorrerem problemas.

## <a name="winrm-dependency"></a>Dependência de WinRM

Configuração de estado pretendido do Windows PowerShell (DSC) depende do WinRM. WinRM não está ativado por predefinição no Windows Server 2008 R2 e Windows 7. Executar ```Set-WSManQuickConfig```, num Windows PowerShell elevada sessão, para ativar o WinRM.

## <a name="using-get-dscconfigurationstatus"></a>Get-DscConfigurationStatus a utilizar

O [Get-DscConfigurationStatus](https://technet.microsoft.com/en-us/library/mt517868.aspx) cmdlet obtém informações sobre o estado de configuração a partir de um nó de destino. Um objeto avançado é devolvido que inclui informações de alto nível sobre ou não a execução de configuração foi concluída com êxito ou não. Pode aprofundar para o objeto a descobrir detalhes sobre a configuração executar como:

* Todos os recursos que falhou
* Qualquer recurso pedido um reinício
* Definições de configuração de metadados no momento da configuração de executar
* etc.

O conjunto de parâmetros seguinte devolve as informações de estado para a última configuração executar:

```powershell
Get-DscConfigurationStatus  [-CimSession <CimSession[]>] 
                            [-ThrottleLimit <int>] 
                            [-AsJob] 
                            [<CommonParameters>]
```
O conjunto de parâmetros seguinte devolve as informações de estado para todos os anteriores execuções de configuração:

```powershell
Get-DscConfigurationStatus  -All 
                            [-CimSession <CimSession[]>] 
                            [-ThrottleLimit <int>] 
                            [-AsJob] 
                            [<CommonParameters>]
```

## <a name="example"></a>Exemplo

```powershell
PS C:\> $Status = Get-DscConfigurationStatus 

PS C:\> $Status

Status      StartDate               Type            Mode    RebootRequested     NumberOfResources
------      ---------               ----            ----    ---------------     -----------------
Failure     11/24/2015  3:44:56     Consistency     Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName       :   MyService
DependsOn               :   
ModuleName              :   PSDesiredStateConfiguration
ModuleVersion           :   1.1
PsDscRunAsCredential    :   
ResourceID              :   [File]ServiceDll
SourceInfo              :   c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds       :   0.19
Error                   :   SourcePath must be accessible for current configuration. The related file/directory is:
                            \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState              :   
InDesiredState          :   False
InitialState            :   
InstanceName            :   ServiceDll
RebootRequested         :   False
ReosurceName            :   File
StartDate               :   11/24/2015  3:44:56
PSComputerName          :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a>Os meus scripts não são executadas: DSC utilizando os registos para diagnosticar erros de script

Como todos os Windows software, DSC regista erros e eventos [registos](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) que pode ser visualizada a [Visualizador de eventos](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer). Estes registos a examinar pode ajudar a compreender por que falhou uma operação específica e como impedir a falha no futuro. Scripts de configuração de escrita podem ser tricky, por isso facilitar os erros de controlo como autor, utilize o recurso de registo DSC para acompanhar o progresso da sua configuração no registo de eventos de análise de DSC.

## <a name="where-are-dsc-event-logs"></a>Onde estão os registos de eventos do DSC?

No Visualizador de eventos, os eventos de DSC são em: **aplicações e serviços de configuração de estado de registos/Microsoft/Windows/Desired**

O cmdlet do PowerShell correspondente, [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), também pode executar para ver os registos de eventos:

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                                                                                  
-----------                     -- ---------------- -------                                                                                                  
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
```

Conforme mostrado acima, o nome de registo principal do DSC é **Microsoft-Windows > -> DSC** (outros nomes de registo no Windows não são mostrados aqui de uma forma abreviada). O nome principal é acrescentado ao nome do canal para criar o nome do registo concluída. O motor de DSC escreve principalmente em três tipos de registos: [registos operacionais, de registos analíticos e de depuração](https://technet.microsoft.com/library/cc722404.aspx). Desde a análise e os registos de depuração estão desativados por predefinição, deve ativá-los no Visualizador de eventos. Para tal, abra o Visualizador de eventos, escrevendo Mostrar-registo de eventos do Windows PowerShell; ou, clique em de **iniciar** botão, clique em **painel de controlo**, clique em **ferramentas administrativas**e, em seguida, clique em **Visualizador de eventos**. No **vista** menu no Visualizador de eventos, clique em **Mostrar depurar registos analíticos e**. O nome do registo para o canal de análise é **Microsoft-Windows-Dsc/analíticos**, e o canal de depuração está **Microsoft-Windows-Dsc/depuração**. Também pode utilizar o [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) utilitário para ativar os registos, conforme mostrado no exemplo seguinte.

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a>O que contêm os registos de DSC?

Registos de DSC são dividir através de três canais de registo com base na importância da mensagem. O registo operacional no DSC contém todas as mensagens de erro e pode ser utilizado para identificar um problema. O registo de análise tem um volume maior de eventos e pode identificar em que ocorreram. Este canal também contém as mensagens verbosas (se aplicável). O registo de depuração contém registos que podem ajudar a compreender a forma como os erros tiverem ocorrido. Mensagens de eventos de DSC são estruturadas, de modo a que cada mensagem de evento começa com um ID de tarefa exclusivamente representa uma operação de DSC. O exemplo abaixo tenta obter a mensagem a partir do primeiro evento registado no registo de DSC operacional.

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
Consistency engine was run successfully. 
```

Eventos de DSC são registados numa estrutura específica que permite ao utilizador para agregar eventos a partir de uma tarefa de DSC. A estrutura é o seguinte:

**ID da tarefa:<Guid>**
**<Event Message>**

## <a name="gathering-events-from-a-single-dsc-operation"></a>Recolha de eventos de uma única operação de DSC

Registos de eventos do DSC contém eventos gerados pelo várias operações de DSC. No entanto, normalmente, será preocupados com os detalhes apenas uma operação específica. Todos os registos de DSC podem ser agrupados pela propriedade de ID de tarefa que é exclusiva para cada operação de DSC. O ID da tarefa é apresentado como o primeiro valor da propriedade em todos os eventos de DSC. Os passos seguintes explicam como acumular todos os eventos de uma estrutura de matriz agrupada.

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>
 
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
wevtutil.exe set-log “Microsoft-Windows-Dsc/Debug” /q:True /e:true
 
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

Aqui, a variável `$SeparateDscOperations` contém registos agrupados pela tarefa de IDs. Cada elemento de matriz desta variável representa um grupo de eventos registados por uma operação de DSC diferentes, que permite o acesso para obter mais informações sobre os registos.

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

Pode extrair os dados na variável `$SeparateDscOperations` utilizando [Where-Object](https://technet.microsoft.com/library/ee177028.aspx). Seguem-se cinco cenários em que pode querer extrair dados de DSC de resolução de problemas:

### <a name="1-operations-failures"></a>1: falhas de operações

Todos os eventos tenham [níveis de gravidade](https://msdn.microsoft.com/library/dd996917(v=vs.85)). Estas informações podem ser utilizadas para identificar os eventos de erro:

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a>2: executam detalhes das operações na última hora de meio

`TimeCreated`, uma propriedade de todos os eventos do Windows indica a hora do evento foi criado. Esta propriedade com um objeto específico de data/hora de comparação pode ser utilizada para filtrar todos os eventos:

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}   
```

### <a name="3-messages-from-the-latest-operation"></a>3: mensagens da operação mais recente

A operação mais recente é armazenada no primeiro índice de grupo de matriz `$SeparateDscOperations`. Consultas de mensagens do grupo para o índice 0 devolve todas as mensagens para a operação mais recente:

```powershelll
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

### <a name="4-error-messages-logged-for-recent-failed-operations"></a>4: as mensagens de erro registadas recente operações falhadas

`$SeparateDscOperations[0].Group`contém um conjunto de eventos para a operação mais recente. Execute o `Where-Object` cmdlet para filtrar os eventos com base no respetivo nome de apresentação de nível. Os resultados são armazenados no `$myFailedEvent` variável, que pode ser mais dissected para obter a mensagem de evento:

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})
 
PS C:\> $myFailedEvent.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} : 
DSC Engine Error : 
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first. 
Error Code : 1 
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a>5: todos os eventos gerados para um ID de tarefa específica.

`$SeparateDscOperations`é uma matriz de grupos, cada um dos quais tem o nome como o ID de tarefa exclusivo. Ao executar o `Where-Object` cmdlet, pode extrair os grupos de eventos que tenham um ID de tarefa específica:

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

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a>Os registos de utilização xDscDiagnostics para analisar o DSC

**xDscDiagnostics** é um módulo do PowerShell que é composta por várias funções que podem ajudar a analisar as falhas de DSC no seu computador. Estas funções podem ajudar a identificar todos os eventos locais das operações de DSC nos últimos ou eventos de DSC nos computadores remotos (com credenciais válidas). Aqui, o termo operação DSC é utilizado para definir uma execução DSC exclusiva único desde o início para o respetivo fim. Por exemplo, `Test-DscConfiguration` seria uma operação de DSC separada. Da mesma forma, todos os outro cmdlet no DSC (tais como `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) cada identificada como separadas operações de DSC. As funções são explicadas em [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics). Ajuda está disponível através da execução `Get-Help <cmdlet name>`.

### <a name="getting-details-of-dsc-operations"></a>A obter os detalhes das operações de DSC 

O `Get-xDscOperation` função permite-lhe localizar os resultados das operações DSC que são executadas num ou vários computadores e devolve um objeto que contém a coleção de eventos é produzido por cada operação de DSC. Por exemplo, no seguinte resultado, os três comandos foram executados. Primeiro transmitido e outros dois falhou. Estes resultados estão resumidos na saída do `Get-xDscOperation`.

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

O `Trace-xDscOperation` cmdlet devolve um objeto que contém uma coleção de eventos, os tipos de evento, e a mensagem de saída gerado a partir de uma operação de DSC específica. Normalmente, quando localizar uma falha em qualquer uma das operações utilizando `Get-xDscOperation`, teria de rastreio que saber qual dos eventos causou uma falha da operação.

Utilize o `SequenceID` parâmetro para obter os eventos de uma operação de específica de um computador específico. Por exemplo, se especificar um `SequenceID` 9, `Trace-xDscOperaion` obter o rastreio para a operação de DSC foi 9th da última operação:

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

Passar o **GUID** atribuídos a uma operação de DSC específica (tal como devolvido pelo `Get-xDscOperation` cmldet) para obter os detalhes do evento para essa operação DSC:

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

Tenha em atenção que, uma vez que `Trace-xDscOperation` agrega eventos de analíticos, depuração e os registos de operacional, que irá solicitar-lhe ativar estes registos, conforme descrito acima.

Em alternativa, pode reunir informações sobre os eventos ao guardar a saída do `Trace-xDscOperation` numa variável. Pode utilizar os seguintes comandos para apresentar todos os eventos para uma operação de DSC específica.

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

Esta ação apresenta os mesmos resultados que o `Get-WinEvent` cmdlet, como o resultado abaixo:

```powershell
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

Idealmente, deve primeiro utilizar `Get-xDscOperation` para listar os últimos DSC alguns configuração é executado no seu máquinas. Os seguintes, pode examinar qualquer operação única (utilizando o respetivo SequenceID ou JobID) com `Trace-xDscOperation` para descobrir o que era em segundo plano.

### <a name="getting-events-for-a-remote-computer"></a>Ao obter eventos de um computador remoto

Utilize o `ComputerName` parâmetro o `Trace-xDscOperation` cmdlet para obter os detalhes do evento num computador remoto. Pode fazê-lo, terá de criar uma regra de firewall para permitir a administração remota no computador remoto:

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```
Agora pode especificar que o computador na sua chamada para `Trace-xDscOperation`:

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

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a>Não atualizar os meus recursos: como repor a cache

O motor de DSC coloca em cache recursos implementados como um módulo do PowerShell para fins de eficiência. No entanto, isto pode causar problemas quando estiver a criação de um recurso e testá-lo em simultâneo porque DSC carregará a versão em cache até o processo de é reiniciado. A única forma de efetuar DSC carregar a versão mais recente é explicitamente cancelar o processo que aloja o motor de DSC.

Da mesma forma, quando executa `Start-DscConfiguration`, depois de adicionar e modificar um recurso personalizado, a modificação pode não ser executado, a menos que, ou até, o computador for reiniciado. Isto acontece porque o DSC é executado no processo de anfitrião do fornecedor de WMI (WmiPrvSE) e, normalmente, existem várias instâncias de WmiPrvSE em execução em simultâneo. Quando reiniciar o computador, o processo de anfitrião é reiniciado e a cache está desmarcada.

Para reciclar a configuração e limpar a cache sem ser reiniciado com êxito, tem de parar e, em seguida, reinicie o processo de anfitrião. Pode fazê-lo numa base por instância, na qual identificar o processo, pare- e reiniciá-lo. Em alternativa, pode utilizar `DebugMode`, conforme demonstrado abaixo, para recarregar os recursos de DSC do PowerShell.

Para identificar que processo está a alojar o motor de DSC e pare-a numa base por instância, pode listar o ID do processo de WmiPrvSE que está a alojar o motor de DSC. Em seguida, para atualizar o fornecedor, pare o processo de WmiPrvSE utilizando os comandos abaixo e execute **início DscConfiguration** novamente.

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

## <a name="using-debugmode"></a>Utilizar DebugMode

Pode configurar o DSC Local Configuration Manager (MMC) para utilizar `DebugMode` sempre limpar a cache quando o processo de anfitrião for reiniciado. Quando definido como **verdadeiro**, faz com que o motor sempre recarregar os recursos de DSC do PowerShell. Quando tiver terminado a escrever o seu recurso, pode configurá-lo novamente para **falso** e o motor irá reverter para o respetivo comportamento da colocação em cache os módulos.

Segue-se uma demonstração para mostrar como `DebugMode` automaticamente pode atualizar a cache. Em primeiro lugar, vamos ver a configuração predefinida:

```
PS C:\> Get-DscLocalConfigurationManager
 
 
AllowModuleOverwrite           : False
CertificateID                  : 
ConfigurationID                : 
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     : 
DebugMode                      : False
DownloadManagerCustomData      : 
DownloadManagerName            : 
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :  
```

Pode ver que `DebugMode` está definido como **falso**.

Para configurar o `DebugMode` demonstração, utilize o seguinte recurso de PowerShell:

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

Agora, criar uma configuração utilizando o recurso acima chamado `TestProviderDebugMode`:

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

Verá que o conteúdo do ficheiro: "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" é **1**.

Agora, atualize o código de fornecedor utilizando o script seguinte:

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

Este script gera um número aleatório e atualiza o código de fornecedor em conformidade. Com `DebugMode` definido como FALSO, o conteúdo do ficheiro "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" nunca são alterados.

Agora, defina `DebugMode` para **verdadeiro** no seu script de configuração:

```powershell
LocalConfigurationManager
{
    DebugMode = $true
} 
```

Quando executar novamente o script acima, verá que o conteúdo do ficheiro for diferente sempre. (Pode executar `Get-DscConfiguration` registá-lo). Segue-se o resultado da execução adicionais dois (os resultados podem ser diferentes ao executar o script):

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

## <a name="see-also"></a>Consulte Também

### <a name="reference"></a>Referência
* [Recursos de registo DSC](logResource.md)

### <a name="concepts"></a>Conceitos
* [Criar recursos de configuração do estado pretendido do PowerShell de personalizada do Windows](authoringResource.md)

### <a name="other-resources"></a>Outros Recursos
* [Cmdlets de configuração do estado pretendido do Windows PowerShell](https://technet.microsoft.com/en-us/library/dn521624(v=wps.630).aspx)

