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
# <a name="managing-services"></a><span data-ttu-id="6c8c0-103">Gerir Serviços</span><span class="sxs-lookup"><span data-stu-id="6c8c0-103">Managing Services</span></span>

<span data-ttu-id="6c8c0-104">Existem oito cmdlets do serviço de núcleo, concebido para uma ampla variedade de tarefas do serviço.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-104">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="6c8c0-105">Veremos apenas listagem e alteração de estado para os serviços de execução, mas pode obter uma lista de cmdlets de serviço usando `Get-Help \*-Service`, e pode encontrar informações sobre cada cmdlet de serviço, utilizando `Get-Help <Cmdlet-Name>`, tal como `Get-Help New-Service`.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-105">We will look only at listing and changing running state for services, but you can get a list of Service cmdlets by using `Get-Help \*-Service`, and you can find information about each Service cmdlet by using `Get-Help <Cmdlet-Name>`, such as `Get-Help New-Service`.</span></span>

## <a name="getting-services"></a><span data-ttu-id="6c8c0-106">Obter serviços</span><span class="sxs-lookup"><span data-stu-id="6c8c0-106">Getting Services</span></span>

<span data-ttu-id="6c8c0-107">Pode obter os serviços num computador local ou remoto usando a `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-107">You can get the services on a local or remote computer by using the `Get-Service` cmdlet.</span></span> <span data-ttu-id="6c8c0-108">Tal como acontece com `Get-Process`, utilizando o `Get-Service` comando sem parâmetros devolve todos os serviços.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-108">As with `Get-Process`, using the `Get-Service` command without parameters returns all services.</span></span> <span data-ttu-id="6c8c0-109">Pode filtrar por nome, até mesmo com um asterisco como caráter universal:</span><span class="sxs-lookup"><span data-stu-id="6c8c0-109">You can filter by name, even using an asterisk as a wildcard:</span></span>

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="6c8c0-110">Uma vez que nem sempre é óbvio qual é o nome real para o serviço, talvez que precisa localizar serviços por nome a apresentar.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-110">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="6c8c0-111">Pode fazer isso por nome específico, utilizando carateres universais, ou usando uma lista de nomes a apresentar:</span><span class="sxs-lookup"><span data-stu-id="6c8c0-111">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

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

<span data-ttu-id="6c8c0-112">Pode utilizar o parâmetro ComputerName do cmdlet Get-Service para obter os serviços em computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-112">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="6c8c0-113">O parâmetro ComputerName aceita vários valores e caracteres curinga, para que possa obter os serviços em vários computadores com um único comando.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-113">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="6c8c0-114">Por exemplo, o comando seguinte obtém os serviços no computador remoto servidor01.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-114">For example, the following command gets the services on the Server01 remote computer.</span></span>

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="6c8c0-115">Introdução necessários e serviços dependentes</span><span class="sxs-lookup"><span data-stu-id="6c8c0-115">Getting Required and Dependent Services</span></span>

<span data-ttu-id="6c8c0-116">O cmdlet Get-Service tem dois parâmetros que são muito úteis na administração de serviço.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-116">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="6c8c0-117">O parâmetro DependentServices obtém os serviços que dependem do serviço.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-117">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="6c8c0-118">O parâmetro RequiredServices obtém serviços sobre a qual depende este serviço.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-118">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="6c8c0-119">Estes parâmetros apresentam apenas os valores dos DependentServices e ServicesDependedOn (alias = RequiredServices) propriedades do objeto System.ServiceProcess.ServiceController que devolve de Get-Service, mas eles simplificam os comandos e faça a introdução Estas informações muito mais simples.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-119">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="6c8c0-120">O comando seguinte obtém os serviços que o serviço LanmanWorkstation requer.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-120">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="6c8c0-121">O comando seguinte obtém os serviços que requerem o serviço LanmanWorkstation.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-121">The following command gets the services that require the LanmanWorkstation service.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="6c8c0-122">Pode até mesmo obter todos os serviços que têm dependências.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-122">You can even get all services that have dependencies.</span></span> <span data-ttu-id="6c8c0-123">O seguinte comando faz exatamente isso e, em seguida, utiliza o cmdlet Format-Table para apresentar as propriedades de estado, nome, RequiredServices e DependentServices dos serviços no computador.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-123">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="6c8c0-124">A parar, iniciar, suspender e reiniciar serviços</span><span class="sxs-lookup"><span data-stu-id="6c8c0-124">Stopping, Starting, Suspending, and Restarting Services</span></span>

<span data-ttu-id="6c8c0-125">Os cmdlets de serviço todos têm o mesmo formulário geral.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-125">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="6c8c0-126">Os serviços podem ser especificados por nome comum ou o nome a apresentar e listas e caracteres curinga como valores.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-126">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="6c8c0-127">Para parar o spooler de impressão, utilize:</span><span class="sxs-lookup"><span data-stu-id="6c8c0-127">To stop the print spooler, use:</span></span>

```powershell
Stop-Service -Name spooler
```

<span data-ttu-id="6c8c0-128">Para iniciar o spooler de impressão após a está parado, utilize:</span><span class="sxs-lookup"><span data-stu-id="6c8c0-128">To start the print spooler after it is stopped, use:</span></span>

```powershell
Start-Service -Name spooler
```

<span data-ttu-id="6c8c0-129">Para suspender o spooler de impressão, utilize:</span><span class="sxs-lookup"><span data-stu-id="6c8c0-129">To suspend the print spooler, use:</span></span>

```powershell
Suspend-Service -Name spooler
```

<span data-ttu-id="6c8c0-130">O `Restart-Service` cmdlet funciona da mesma forma como os outros cmdlets do serviço, mas vamos mostrar alguns exemplos mais complexos para o mesmo.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-130">The `Restart-Service` cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="6c8c0-131">O uso mais simples, especifique o nome do serviço:</span><span class="sxs-lookup"><span data-stu-id="6c8c0-131">In the simplest use, you specify the name of the service:</span></span>

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="6c8c0-132">Observará que obtém uma mensagem de aviso repetido sobre o Spooler de impressão a partir de cópia de segurança.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-132">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="6c8c0-133">Ao efetuar uma operação de serviço que demora algum tempo, o Windows PowerShell notificará que ainda é tentar executar a tarefa.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-133">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="6c8c0-134">Se pretender reiniciar vários serviços, pode obter uma lista de serviços, filtrá-los e, em seguida, efetuar o reinício:</span><span class="sxs-lookup"><span data-stu-id="6c8c0-134">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

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

<span data-ttu-id="6c8c0-135">Estes cmdlets de serviço não tem um parâmetro ComputerName, mas pode executá-las num computador remoto utilizando o cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-135">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="6c8c0-136">Por exemplo, o seguinte comando reinicia o serviço de Spooler no computador remoto servidor01.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-136">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="6c8c0-137">Propriedades de definição de serviço</span><span class="sxs-lookup"><span data-stu-id="6c8c0-137">Setting Service Properties</span></span>

<span data-ttu-id="6c8c0-138">O `Set-Service` cmdlet altera as propriedades de um serviço num computador local ou remoto.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-138">The `Set-Service` cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="6c8c0-139">Como o estado do serviço é uma propriedade, pode utilizar este cmdlet para iniciar, parar e suspender um serviço.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-139">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span>
<span data-ttu-id="6c8c0-140">O cmdlet Set-Service também tem um parâmetro de Statuptype que lhe permite alterar o tipo de arranque do serviço.</span><span class="sxs-lookup"><span data-stu-id="6c8c0-140">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="6c8c0-141">Para utilizar `Set-Service` no Windows Vista e versões posteriores do Windows, abra o Windows PowerShell com a opção "Executar como administrador".</span><span class="sxs-lookup"><span data-stu-id="6c8c0-141">To use `Set-Service` on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="6c8c0-142">Para obter mais informações, consulte [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="6c8c0-142">For more information, see [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>

## <a name="see-also"></a><span data-ttu-id="6c8c0-143">Veja Também</span><span class="sxs-lookup"><span data-stu-id="6c8c0-143">See Also</span></span>

- <span data-ttu-id="6c8c0-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span><span class="sxs-lookup"><span data-stu-id="6c8c0-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span></span>
- <span data-ttu-id="6c8c0-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="6c8c0-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>
- <span data-ttu-id="6c8c0-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span><span class="sxs-lookup"><span data-stu-id="6c8c0-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span></span>
- <span data-ttu-id="6c8c0-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span><span class="sxs-lookup"><span data-stu-id="6c8c0-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span></span>
