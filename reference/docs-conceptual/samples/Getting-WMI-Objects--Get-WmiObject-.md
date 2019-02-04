---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Obter objetos WMI obtém WmiObject
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
ms.openlocfilehash: 522822ac3ea6f08b20fa5af6c9accb48b01035d3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688463"
---
# <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="b0046-103">Obter objetos WMI (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="b0046-103">Getting WMI Objects (Get-WmiObject)</span></span>

## <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="b0046-104">Obter objetos WMI (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="b0046-104">Getting WMI Objects (Get-WmiObject)</span></span>

<span data-ttu-id="b0046-105">Windows Management Instrumentation (WMI) é uma tecnologia de núcleos para a administração de sistema do Windows porque ela expõe uma vasta gama de informações de forma uniforme.</span><span class="sxs-lookup"><span data-stu-id="b0046-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="b0046-106">Devido a quanto o WMI torna possível, o cmdlet do Windows PowerShell para o acesso a objetos WMI **Get-WmiObject**, é um dos mais úteis para fazer o trabalho real.</span><span class="sxs-lookup"><span data-stu-id="b0046-106">Because of how much WMI makes possible, the Windows PowerShell cmdlet for accessing WMI objects, **Get-WmiObject**, is one of the most useful for doing real work.</span></span> <span data-ttu-id="b0046-107">Vamos discutir como usar o Get-WmiObject para acessar objetos do WMI e, em seguida, como utilizar objetos WMI para fazer coisas específicas.</span><span class="sxs-lookup"><span data-stu-id="b0046-107">We are going to discuss how to use Get-WmiObject to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="b0046-108">Listagem Classes WMI</span><span class="sxs-lookup"><span data-stu-id="b0046-108">Listing WMI Classes</span></span>

<span data-ttu-id="b0046-109">O primeiro problema que encontrar a maioria dos usuários WMI está tentando descobrir o que pode ser feito com o WMI.</span><span class="sxs-lookup"><span data-stu-id="b0046-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="b0046-110">WMI classes descrevem os recursos que podem ser geridos.</span><span class="sxs-lookup"><span data-stu-id="b0046-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="b0046-111">Há centenas de classes WMI, alguns dos quais contêm dezenas de propriedades.</span><span class="sxs-lookup"><span data-stu-id="b0046-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="b0046-112">**Get-WmiObject** resolve este problema, tornando o WMI Detetáveis.</span><span class="sxs-lookup"><span data-stu-id="b0046-112">**Get-WmiObject** addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="b0046-113">Pode obter uma lista das classes WMI disponíveis no computador local digitando:</span><span class="sxs-lookup"><span data-stu-id="b0046-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

<span data-ttu-id="b0046-114">Pode recuperar as mesmas informações de um computador remoto utilizando o parâmetro ComputerName, especificando um nome de computador ou endereço IP:</span><span class="sxs-lookup"><span data-stu-id="b0046-114">You can retrieve the same information from a remote computer by using the ComputerName parameter, specifying a computer name or IP address:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

<span data-ttu-id="b0046-115">A listagem de classe devolvida por computadores remotos pode variar por sistema operativo específico, que o computador está em execução e as extensões WMI particulares adicionadas por aplicativos instalados.</span><span class="sxs-lookup"><span data-stu-id="b0046-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="b0046-116">Ao utilizar Get-WmiObject para ligar a um computador remoto, o computador remoto deve estar em execução WMI e, sob a configuração predefinida, a conta que está a utilizar tem de estar no grupo de administradores locais no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="b0046-116">When using Get-WmiObject to connect to a remote computer, the remote computer must be running WMI and, under the default configuration, the account you are using must be in the local administrators group on the remote computer.</span></span> <span data-ttu-id="b0046-117">O sistema remoto não é necessário ter o PowerShell de Windows instalado.</span><span class="sxs-lookup"><span data-stu-id="b0046-117">The remote system does not need to have Windows PowerShell installed.</span></span> <span data-ttu-id="b0046-118">Isso permite que a administração de sistemas operativos que não estejam a executar o Windows PowerShell, mas têm WMI disponível.</span><span class="sxs-lookup"><span data-stu-id="b0046-118">This allows you to administer operating systems that are not running Windows PowerShell, but do have WMI available.</span></span>

<span data-ttu-id="b0046-119">Pode incluir ComputerName ao ligar ao sistema local.</span><span class="sxs-lookup"><span data-stu-id="b0046-119">You can even include the ComputerName when connecting to the local system.</span></span> <span data-ttu-id="b0046-120">Pode utilizar o nome do computador local, o endereço IP (ou o endereço de loopback 127.0.0.1), ou o estilo de WMI "." como o nome do computador.</span><span class="sxs-lookup"><span data-stu-id="b0046-120">You can use the local computer's name, its IP address (or the loopback address 127.0.0.1), or the WMI-style '.' as the computer name.</span></span> <span data-ttu-id="b0046-121">Se estiver a executar o Windows PowerShell num computador denominado Admin01 com o endereço IP 192.168.1.90, os seguintes comandos todos retornará a classe WMI de listagem para esse computador:</span><span class="sxs-lookup"><span data-stu-id="b0046-121">If you are running Windows PowerShell on a computer named Admin01 with IP address 192.168.1.90, the following commands will all return the WMI class listing for that computer:</span></span>

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

<span data-ttu-id="b0046-122">Get-WmiObject utiliza o espaço de nomes de raiz/cimv2, por predefinição.</span><span class="sxs-lookup"><span data-stu-id="b0046-122">Get-WmiObject uses the root/cimv2 namespace by default.</span></span> <span data-ttu-id="b0046-123">Se pretender especificar outro espaço de nomes WMI, utilize o **espaço de nomes** parâmetro e especificar o caminho de espaço de nomes correspondente:</span><span class="sxs-lookup"><span data-stu-id="b0046-123">If you want to specify another WMI namespace, use the **Namespace** parameter and specify the corresponding namespace path:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="b0046-124">Exibição de detalhes da classe de WMI</span><span class="sxs-lookup"><span data-stu-id="b0046-124">Displaying WMI Class Details</span></span>

<span data-ttu-id="b0046-125">Se já sabe o nome de uma classe WMI, pode usar para obter informações de imediato.</span><span class="sxs-lookup"><span data-stu-id="b0046-125">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="b0046-126">Por exemplo, uma das classes WMI comumente usadas para recuperar informações sobre um computador é **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="b0046-126">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

<span data-ttu-id="b0046-127">Embora estamos mostrando todos os parâmetros, o comando pode ser expresso de forma mais sucinta.</span><span class="sxs-lookup"><span data-stu-id="b0046-127">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span> <span data-ttu-id="b0046-128">O **ComputerName** parâmetro não é necessário quando se liga ao sistema local.</span><span class="sxs-lookup"><span data-stu-id="b0046-128">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="b0046-129">Vamos mostrá-lo para demonstrar o caso mais comum e lembrá-lo sobre o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b0046-129">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="b0046-130">O **espaço de nomes** utiliza por predefinição a raiz/cimv2 e pode ser omitida também.</span><span class="sxs-lookup"><span data-stu-id="b0046-130">The **Namespace** defaults to root/cimv2, and can be omitted as well.</span></span> <span data-ttu-id="b0046-131">Por fim, a maioria dos cmdlets permitem-lhe omitir o nome dos parâmetros comuns.</span><span class="sxs-lookup"><span data-stu-id="b0046-131">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="b0046-132">Com o Get-WmiObject, não se for especificado nenhum nome para o primeiro parâmetro, Windows PowerShell trata-a como o **classe** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b0046-132">With Get-WmiObject, if no name is specified for the first parameter, Windows PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="b0046-133">Isso significa que foram emitido o último comando, digitando:</span><span class="sxs-lookup"><span data-stu-id="b0046-133">This means the last command could have been issued by typing:</span></span>

```powershell
Get-WmiObject Win32_OperatingSystem
```

<span data-ttu-id="b0046-134">O **Win32_OperatingSystem** classe tem muitas propriedades adicionais que são apresentados aqui.</span><span class="sxs-lookup"><span data-stu-id="b0046-134">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="b0046-135">Pode usar o Get-Member para ver todas as propriedades.</span><span class="sxs-lookup"><span data-stu-id="b0046-135">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="b0046-136">As propriedades de uma classe WMI estão automaticamente disponíveis, como de outras propriedades de objeto:</span><span class="sxs-lookup"><span data-stu-id="b0046-136">The properties of a WMI class are automatically available like other object properties:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Get-Member -MemberType Property

   TypeName: System.Management.ManagementObject#root\cimv2\Win32_OperatingSyste
m

Name                                      MemberType Definition
----                                      ---------- ----------
__CLASS                                   Property   System.String __CLASS {...
...
BootDevice                                Property   System.String BootDevic...
BuildNumber                               Property   System.String BuildNumb...
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="b0046-137">Visualizar propriedades de não-padrão com Cmdlets de formato</span><span class="sxs-lookup"><span data-stu-id="b0046-137">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="b0046-138">Se pretender que as informações contidas no **Win32_OperatingSystem** isto é a classe não é apresentado por predefinição, pode apresentá-lo utilizando o **formato** cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b0046-138">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="b0046-139">Por exemplo, se desejar exibir dados de memória disponível, escreva:</span><span class="sxs-lookup"><span data-stu-id="b0046-139">For example, if you want to display available memory data, type:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> <span data-ttu-id="b0046-140">Carateres universais funcionam com nomes de propriedade no **Format-Table**, por isso, o elemento de final pipeline pode ser reduzido a `Format-Table -Property Total,Free`</span><span class="sxs-lookup"><span data-stu-id="b0046-140">Wildcards work with property names in **Format-Table**, so the final pipeline element can be reduced to `Format-Table -Property Total,Free`</span></span>

<span data-ttu-id="b0046-141">Os dados de memória podem ser mais legíveis, se formatar como uma lista ao escrever:</span><span class="sxs-lookup"><span data-stu-id="b0046-141">The memory data might be more readable if you format it as a list by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
