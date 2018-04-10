---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Gerir Serviços
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
ms.openlocfilehash: f3231d1922568e552534f3d3face3864d1610d65
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="managing-services"></a>Gerir Serviços

Existem oito núcleos serviço cmdlets concebidos para uma vasta gama de tarefas de serviço. Iremos abordar apenas a listagem e alterar o estado de execução para os serviços, mas pode obter uma lista de cmdlets do serviço utilizando **Get-Help \&#42;-serviço**, e pode encontrar informações sobre cada cmdlet de serviço utilizando **Get-Help < nome do Cmdlet >**, tais como **Get-Help novo serviço**.

## <a name="getting-services"></a>Obter serviços

Pode obter os serviços no computador local ou remoto, utilizando o **Get-Service** cmdlet. Tal como com **Get-Process**, utilizando o **Get-Service** comando sem parâmetros devolve todos os serviços. Pode filtrar por nome, mesmo com um asterisco como caráter universal:

```
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

Porque não é sempre óbvios que é o nome real para o serviço, pode constatar que precisa localizar serviços por nome de apresentação. Pode fazê-nome específico, utilizando carateres universais, ou uma lista de nomes a apresentar:

```
PS> Get-Service -DisplayName se*

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center

PS> Get-Service -DisplayName ServiceLayer,Server

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

Pode utilizar o parâmetro ComputerName do cmdlet Get-Service para obter os serviços em computadores remotos. O parâmetro ComputerName aceita vários valores e os carateres universais, pelo que pode obter os serviços em vários computadores com um único comando. Por exemplo, o seguinte comando obtém os serviços no computador remoto servidor01.

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a>Introdução ao necessário e serviços dependentes

O cmdlet Get-Service tem dois parâmetros que são muito úteis na administração do serviço. O parâmetro DependentServices obtém serviços que dependem do serviço. O parâmetro RequiredServices obtém serviços sobre os quais depende este serviço.

Estes parâmetros apenas apresentam os valores do DependentServices e ServicesDependedOn (alias = RequiredServices) propriedades do objeto System.ServiceProcess.ServiceController que simplificam a devolve Get-Service, mas os comandos e certifique-introdução Estas informações muito mais simples.

O comando seguinte obtém os serviços que requer que o serviço de LanmanWorkstation.

```
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

O comando seguinte obtém os serviços que requerem o serviço de LanmanWorkstation.

```
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

Ainda pode obter todos os serviços que têm dependências. O seguinte comando não mesmo e, em seguida, utiliza o cmdlet Format-Table para apresentar as propriedades de estado, nome, RequiredServices e DependentServices dos serviços de no computador.

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a>A parar, iniciar, suspender e reiniciar os serviços
Os cmdlets de serviço todas as ter o mesmo formulário geral. Os serviços podem ser especificados pelo nome comum ou o nome a apresentar e coloque listas e os carateres universais como valores. Para parar o spooler de impressão, utilize:

```powershell
Stop-Service -Name spooler
```

Para iniciar o spooler de impressão após for parado, utilize:

```powershell
Start-Service -Name spooler
```

Para suspender o spooler de impressão, utilize:

```powershell
Suspend-Service -Name spooler
```

O **Reiniciar serviço** cmdlet funciona da mesma forma que outros cmdlets do serviço, mas vamos mostrar alguns exemplos mais complexos para o mesmo. Na utilização mais simples, especifique o nome do serviço:

```
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

Vai notar que obtém uma mensagem de aviso repetido sobre o Spooler de impressão que configurar. Quando efetuar uma operação de serviço demora algum tempo, o Windows PowerShell notificará que ainda é tentar executar a tarefa.

Se pretender reiniciar múltiplos serviços, pode obter uma lista de serviços, filtrá-los e, em seguida, execute o reinício:

```
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service

WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

Estes cmdlets de serviço não tem um parâmetro ComputerName, mas pode executá-los num computador remoto utilizando o cmdlet Invoke-Command. Por exemplo, o seguinte comando reinicia o serviço Spooler no computador remoto servidor01.

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a>Propriedades do serviço de definição

O cmdlet Set-Service é alterado as propriedades de um serviço num computador local ou remoto. Porque o estado do serviço é uma propriedade, pode utilizar este cmdlet para iniciar, parar e suspender um serviço. O cmdlet Set-Service também tem um parâmetro de StartupType que lhe permite alterar o tipo de arranque do serviço.

Para utilizar o serviço do conjunto no Windows Vista e versões posteriores do Windows, abra o Windows PowerShell com a opção "Executar como administrador".

Para obter mais informações, consulte [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)

## <a name="see-also"></a>Consulte Também

- [Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)
- [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)
- [Reinicie o serviço [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)
- [Suspender-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)