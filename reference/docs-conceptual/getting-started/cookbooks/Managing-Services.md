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
ms.locfileid: "30951203"
---
# <a name="managing-services"></a><span data-ttu-id="e7cb6-103">Gerir Serviços</span><span class="sxs-lookup"><span data-stu-id="e7cb6-103">Managing Services</span></span>

<span data-ttu-id="e7cb6-104">Existem oito núcleos serviço cmdlets concebidos para uma vasta gama de tarefas de serviço.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-104">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="e7cb6-105">Iremos abordar apenas a listagem e alterar o estado de execução para os serviços, mas pode obter uma lista de cmdlets do serviço utilizando **Get-Help \&#42;-serviço**, e pode encontrar informações sobre cada cmdlet de serviço utilizando **Get-Help < nome do Cmdlet >**, tais como **Get-Help novo serviço**.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-105">We will look only at listing and changing running state for services, but you can get a list Service cmdlets by using **Get-Help \&#42;-Service**, and you can find information about each Service cmdlet by using **Get-Help<Cmdlet-Name>**, such as **Get-Help New-Service**.</span></span>

## <a name="getting-services"></a><span data-ttu-id="e7cb6-106">Obter serviços</span><span class="sxs-lookup"><span data-stu-id="e7cb6-106">Getting Services</span></span>

<span data-ttu-id="e7cb6-107">Pode obter os serviços no computador local ou remoto, utilizando o **Get-Service** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-107">You can get the services on a local or remote computer by using the **Get-Service** cmdlet.</span></span> <span data-ttu-id="e7cb6-108">Tal como com **Get-Process**, utilizando o **Get-Service** comando sem parâmetros devolve todos os serviços.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-108">As with **Get-Process**, using the **Get-Service** command without parameters returns all services.</span></span> <span data-ttu-id="e7cb6-109">Pode filtrar por nome, mesmo com um asterisco como caráter universal:</span><span class="sxs-lookup"><span data-stu-id="e7cb6-109">You can filter by name, even using an asterisk as a wildcard:</span></span>

```
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="e7cb6-110">Porque não é sempre óbvios que é o nome real para o serviço, pode constatar que precisa localizar serviços por nome de apresentação.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-110">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="e7cb6-111">Pode fazê-nome específico, utilizando carateres universais, ou uma lista de nomes a apresentar:</span><span class="sxs-lookup"><span data-stu-id="e7cb6-111">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

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

<span data-ttu-id="e7cb6-112">Pode utilizar o parâmetro ComputerName do cmdlet Get-Service para obter os serviços em computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-112">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="e7cb6-113">O parâmetro ComputerName aceita vários valores e os carateres universais, pelo que pode obter os serviços em vários computadores com um único comando.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-113">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="e7cb6-114">Por exemplo, o seguinte comando obtém os serviços no computador remoto servidor01.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-114">For example, the following command gets the services on the Server01 remote computer.</span></span>

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="e7cb6-115">Introdução ao necessário e serviços dependentes</span><span class="sxs-lookup"><span data-stu-id="e7cb6-115">Getting Required and Dependent Services</span></span>

<span data-ttu-id="e7cb6-116">O cmdlet Get-Service tem dois parâmetros que são muito úteis na administração do serviço.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-116">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="e7cb6-117">O parâmetro DependentServices obtém serviços que dependem do serviço.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-117">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="e7cb6-118">O parâmetro RequiredServices obtém serviços sobre os quais depende este serviço.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-118">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="e7cb6-119">Estes parâmetros apenas apresentam os valores do DependentServices e ServicesDependedOn (alias = RequiredServices) propriedades do objeto System.ServiceProcess.ServiceController que simplificam a devolve Get-Service, mas os comandos e certifique-introdução Estas informações muito mais simples.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-119">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="e7cb6-120">O comando seguinte obtém os serviços que requer que o serviço de LanmanWorkstation.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-120">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="e7cb6-121">O comando seguinte obtém os serviços que requerem o serviço de LanmanWorkstation.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-121">The following command gets the services that require the LanmanWorkstation service.</span></span>

```
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="e7cb6-122">Ainda pode obter todos os serviços que têm dependências.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-122">You can even get all services that have dependencies.</span></span> <span data-ttu-id="e7cb6-123">O seguinte comando não mesmo e, em seguida, utiliza o cmdlet Format-Table para apresentar as propriedades de estado, nome, RequiredServices e DependentServices dos serviços de no computador.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-123">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="e7cb6-124">A parar, iniciar, suspender e reiniciar os serviços</span><span class="sxs-lookup"><span data-stu-id="e7cb6-124">Stopping, Starting, Suspending, and Restarting Services</span></span>
<span data-ttu-id="e7cb6-125">Os cmdlets de serviço todas as ter o mesmo formulário geral.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-125">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="e7cb6-126">Os serviços podem ser especificados pelo nome comum ou o nome a apresentar e coloque listas e os carateres universais como valores.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-126">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="e7cb6-127">Para parar o spooler de impressão, utilize:</span><span class="sxs-lookup"><span data-stu-id="e7cb6-127">To stop the print spooler, use:</span></span>

```powershell
Stop-Service -Name spooler
```

<span data-ttu-id="e7cb6-128">Para iniciar o spooler de impressão após for parado, utilize:</span><span class="sxs-lookup"><span data-stu-id="e7cb6-128">To start the print spooler after it is stopped, use:</span></span>

```powershell
Start-Service -Name spooler
```

<span data-ttu-id="e7cb6-129">Para suspender o spooler de impressão, utilize:</span><span class="sxs-lookup"><span data-stu-id="e7cb6-129">To suspend the print spooler, use:</span></span>

```powershell
Suspend-Service -Name spooler
```

<span data-ttu-id="e7cb6-130">O **Reiniciar serviço** cmdlet funciona da mesma forma que outros cmdlets do serviço, mas vamos mostrar alguns exemplos mais complexos para o mesmo.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-130">The **Restart-Service** cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="e7cb6-131">Na utilização mais simples, especifique o nome do serviço:</span><span class="sxs-lookup"><span data-stu-id="e7cb6-131">In the simplest use, you specify the name of the service:</span></span>

```
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="e7cb6-132">Vai notar que obtém uma mensagem de aviso repetido sobre o Spooler de impressão que configurar.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-132">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="e7cb6-133">Quando efetuar uma operação de serviço demora algum tempo, o Windows PowerShell notificará que ainda é tentar executar a tarefa.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-133">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="e7cb6-134">Se pretender reiniciar múltiplos serviços, pode obter uma lista de serviços, filtrá-los e, em seguida, execute o reinício:</span><span class="sxs-lookup"><span data-stu-id="e7cb6-134">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

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

<span data-ttu-id="e7cb6-135">Estes cmdlets de serviço não tem um parâmetro ComputerName, mas pode executá-los num computador remoto utilizando o cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-135">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="e7cb6-136">Por exemplo, o seguinte comando reinicia o serviço Spooler no computador remoto servidor01.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-136">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="e7cb6-137">Propriedades do serviço de definição</span><span class="sxs-lookup"><span data-stu-id="e7cb6-137">Setting Service Properties</span></span>

<span data-ttu-id="e7cb6-138">O cmdlet Set-Service é alterado as propriedades de um serviço num computador local ou remoto.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-138">The Set-Service cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="e7cb6-139">Porque o estado do serviço é uma propriedade, pode utilizar este cmdlet para iniciar, parar e suspender um serviço.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-139">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span> <span data-ttu-id="e7cb6-140">O cmdlet Set-Service também tem um parâmetro de StartupType que lhe permite alterar o tipo de arranque do serviço.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-140">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="e7cb6-141">Para utilizar o serviço do conjunto no Windows Vista e versões posteriores do Windows, abra o Windows PowerShell com a opção "Executar como administrador".</span><span class="sxs-lookup"><span data-stu-id="e7cb6-141">To use Set-Service on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="e7cb6-142">Para obter mais informações, consulte [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="e7cb6-142">For more information, see [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>

## <a name="see-also"></a><span data-ttu-id="e7cb6-143">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="e7cb6-143">See Also</span></span>

- <span data-ttu-id="e7cb6-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span><span class="sxs-lookup"><span data-stu-id="e7cb6-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span></span>
- <span data-ttu-id="e7cb6-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="e7cb6-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>
- <span data-ttu-id="e7cb6-146">[Reinicie o serviço [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span><span class="sxs-lookup"><span data-stu-id="e7cb6-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span></span>
- <span data-ttu-id="e7cb6-147">[Suspender-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span><span class="sxs-lookup"><span data-stu-id="e7cb6-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span></span>