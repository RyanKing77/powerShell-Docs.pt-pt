---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Gerir Serviços
ms.openlocfilehash: d9e17b2d91ae01d7d4d6d573348289fa68dc9c56
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030157"
---
# <a name="managing-services"></a>Gerir Serviços

Existem oito cmdlets do serviço de núcleo, concebido para uma ampla variedade de tarefas do serviço. Veremos apenas listagem e alteração de estado para os serviços de execução, mas pode obter uma lista de cmdlets de serviço usando `Get-Help \*-Service`, e pode encontrar informações sobre cada cmdlet de serviço, utilizando `Get-Help <Cmdlet-Name>`, tal como `Get-Help New-Service`.

## <a name="getting-services"></a>Obter serviços

Pode obter os serviços num computador local ou remoto usando a `Get-Service` cmdlet. Tal como acontece com `Get-Process`, utilizando o `Get-Service` comando sem parâmetros devolve todos os serviços. Pode filtrar por nome, até mesmo com um asterisco como caráter universal:

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

Uma vez que nem sempre é óbvio qual é o nome real para o serviço, talvez que precisa localizar serviços por nome a apresentar. Pode fazer isso por nome específico, utilizando carateres universais, ou usando uma lista de nomes a apresentar:

```powershell
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

Pode utilizar o parâmetro ComputerName do cmdlet Get-Service para obter os serviços em computadores remotos. O parâmetro ComputerName aceita vários valores e caracteres curinga, para que possa obter os serviços em vários computadores com um único comando. Por exemplo, o comando seguinte obtém os serviços no computador remoto servidor01.

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a>Introdução necessários e serviços dependentes

O cmdlet Get-Service tem dois parâmetros que são muito úteis na administração de serviço. O parâmetro DependentServices obtém os serviços que dependem do serviço. O parâmetro RequiredServices obtém serviços sobre a qual depende este serviço.

Estes parâmetros apresentam apenas os valores dos DependentServices e ServicesDependedOn (alias = RequiredServices) propriedades do objeto System.ServiceProcess.ServiceController que devolve de Get-Service, mas eles simplificam os comandos e faça a introdução Estas informações muito mais simples.

O comando seguinte obtém os serviços que o serviço LanmanWorkstation requer.

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

O comando seguinte obtém os serviços que requerem o serviço LanmanWorkstation.

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

Pode até mesmo obter todos os serviços que têm dependências. O seguinte comando faz exatamente isso e, em seguida, utiliza o cmdlet Format-Table para apresentar as propriedades de estado, nome, RequiredServices e DependentServices dos serviços no computador.

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a>A parar, iniciar, suspender e reiniciar serviços

Os cmdlets de serviço todos têm o mesmo formulário geral. Os serviços podem ser especificados por nome comum ou o nome a apresentar e listas e caracteres curinga como valores. Para parar o spooler de impressão, utilize:

```powershell
Stop-Service -Name spooler
```

Para iniciar o spooler de impressão após a está parado, utilize:

```powershell
Start-Service -Name spooler
```

Para suspender o spooler de impressão, utilize:

```powershell
Suspend-Service -Name spooler
```

O `Restart-Service` cmdlet funciona da mesma forma como os outros cmdlets do serviço, mas vamos mostrar alguns exemplos mais complexos para o mesmo. O uso mais simples, especifique o nome do serviço:

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

Observará que obtém uma mensagem de aviso repetido sobre o Spooler de impressão a partir de cópia de segurança. Ao efetuar uma operação de serviço que demora algum tempo, o Windows PowerShell notificará que ainda é tentar executar a tarefa.

Se pretender reiniciar vários serviços, pode obter uma lista de serviços, filtrá-los e, em seguida, efetuar o reinício:

```powershell
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

Estes cmdlets de serviço não tem um parâmetro ComputerName, mas pode executá-las num computador remoto utilizando o cmdlet Invoke-Command. Por exemplo, o seguinte comando reinicia o serviço de Spooler no computador remoto servidor01.

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a>Propriedades de definição de serviço

O `Set-Service` cmdlet altera as propriedades de um serviço num computador local ou remoto. Como o estado do serviço é uma propriedade, pode utilizar este cmdlet para iniciar, parar e suspender um serviço.
O cmdlet Set-Service também tem um parâmetro de Statuptype que lhe permite alterar o tipo de arranque do serviço.

Para utilizar `Set-Service` no Windows Vista e versões posteriores do Windows, abra o Windows PowerShell com a opção "Executar como administrador".

Para obter mais informações, consulte [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)

## <a name="see-also"></a>Veja Também

- [Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)
- [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)
- [Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)
- [Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)
