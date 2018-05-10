---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Recolher Informações sobre os Computadores
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: ca92474eaf6fa546c3d6450f5a282e45157018a8
ms.sourcegitcommit: 4a841ebda3339ae2477e0f5f5be8c01740221232
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/07/2018
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="3be11-103">Recolher Informações sobre os Computadores</span><span class="sxs-lookup"><span data-stu-id="3be11-103">Collecting Information About Computers</span></span>

<span data-ttu-id="3be11-104">Os cmdlets da **CimCmdlets** módulo são os cmdlets mais importantes para tarefas de gestão de sistema geral.</span><span class="sxs-lookup"><span data-stu-id="3be11-104">Cmdlets from **CimCmdlets** module are the most important cmdlets for general system management tasks.</span></span>
<span data-ttu-id="3be11-105">Todas as definições de subsistema críticas são expostas através do WMI.</span><span class="sxs-lookup"><span data-stu-id="3be11-105">All critical subsystem settings are exposed through WMI.</span></span>
<span data-ttu-id="3be11-106">Além disso, o WMI trata dados como objetos que estão em coleções de um ou mais itens.</span><span class="sxs-lookup"><span data-stu-id="3be11-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span>
<span data-ttu-id="3be11-107">Porque o Windows PowerShell também funciona com objetos e tem um pipeline que permite-lhe tratar único ou vários objetos da mesma forma, o acesso WMI genérico permite-lhe efetuar algumas tarefas avançadas com pouco trabalho.</span><span class="sxs-lookup"><span data-stu-id="3be11-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

<span data-ttu-id="3be11-108">Os exemplos seguintes demonstram como recolher informações específicas, utilizando `Get-CimInstance` contra um computador arbitrário.</span><span class="sxs-lookup"><span data-stu-id="3be11-108">The following examples demonstrate how to collect specific information by using `Get-CimInstance` against an arbitrary computer.</span></span>
<span data-ttu-id="3be11-109">Especificamos o **ComputerName** parâmetro com o valor de ponto (**.**), que representa o computador local.</span><span class="sxs-lookup"><span data-stu-id="3be11-109">We specify the **ComputerName** parameter with the dot value (**.**), which represents the local computer.</span></span>
<span data-ttu-id="3be11-110">Pode especificar um nome ou endereço IP associado a qualquer computador que pode aceder através do WMI.</span><span class="sxs-lookup"><span data-stu-id="3be11-110">You can specify a name or IP address associated with any computer you can reach through WMI.</span></span>
<span data-ttu-id="3be11-111">Para obter informações sobre o computador local, pode omitir o **ComputerName** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3be11-111">To retrieve information about the local computer, you could omit the **ComputerName** parameter.</span></span>

### <a name="listing-desktop-settings"></a><span data-ttu-id="3be11-112">Definições de ambiente de trabalho de listagem</span><span class="sxs-lookup"><span data-stu-id="3be11-112">Listing Desktop Settings</span></span>

<span data-ttu-id="3be11-113">Iremos irá começar com um comando que recolhe informações sobre os ambientes de trabalho no computador local.</span><span class="sxs-lookup"><span data-stu-id="3be11-113">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

<span data-ttu-id="3be11-114">Esta ação devolve informações para todos os ambientes de trabalho, quer sejam em utilização ou não.</span><span class="sxs-lookup"><span data-stu-id="3be11-114">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="3be11-115">As informações devolvidas pelo algumas classes WMI podem ser muito detalhada e, muitas vezes, incluir metadados sobre a classe WMI.</span><span class="sxs-lookup"><span data-stu-id="3be11-115">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span>
<span data-ttu-id="3be11-116">Porque a maioria destas propriedades de metadados tem nomes que começam por **Cim**, pode filtrar as propriedades utilizando `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="3be11-116">Because most of these metadata properties have names that begin with **Cim**, you can filter the properties using `Select-Object`.</span></span>
<span data-ttu-id="3be11-117">Especifique o **- ExcludeProperty** parâmetro com "Cim \*" como valor.</span><span class="sxs-lookup"><span data-stu-id="3be11-117">Specify the **-ExcludeProperty** parameter with "Cim\*" as the value.</span></span>
<span data-ttu-id="3be11-118">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="3be11-118">For example:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="3be11-119">Para filtrar os metadados, utilize um operador de pipeline (|) para enviar os resultados do `Get-CimInstance` comando para `Select-Object -ExcludeProperty "CIM*"`.</span><span class="sxs-lookup"><span data-stu-id="3be11-119">To filter out the metadata, use a pipeline operator (|) to send the results of the `Get-CimInstance` command to `Select-Object -ExcludeProperty "CIM*"`.</span></span>

### <a name="listing-bios-information"></a><span data-ttu-id="3be11-120">Listar informações do BIOS</span><span class="sxs-lookup"><span data-stu-id="3be11-120">Listing BIOS Information</span></span>

<span data-ttu-id="3be11-121">O WMI **Win32_BIOS** classe devolve informações bastante compact e completas sobre o BIOS do sistema no computador local:</span><span class="sxs-lookup"><span data-stu-id="3be11-121">The WMI **Win32_BIOS** class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a><span data-ttu-id="3be11-122">Listar as informações do processador</span><span class="sxs-lookup"><span data-stu-id="3be11-122">Listing Processor Information</span></span>

<span data-ttu-id="3be11-123">Pode obter informações do processador geral através do WMI **Win32_Processor** classe, embora irá provavelmente pretender filtrar as informações:</span><span class="sxs-lookup"><span data-stu-id="3be11-123">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="3be11-124">Descrição genérico de uma cadeia a família de processadores, apenas pode devolver o **SystemType** propriedade:</span><span class="sxs-lookup"><span data-stu-id="3be11-124">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="3be11-125">Listar o computador fabricante e modelo</span><span class="sxs-lookup"><span data-stu-id="3be11-125">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="3be11-126">Informações de modelo do computador também estão disponíveis no **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="3be11-126">Computer model information is also available from **Win32_ComputerSystem**.</span></span>
<span data-ttu-id="3be11-127">A saída padrão apresentada não terá qualquer filtragem para fornecer dados OEM:</span><span class="sxs-lookup"><span data-stu-id="3be11-127">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

<span data-ttu-id="3be11-128">A saída de comandos como esta, que devolvem informações diretamente a partir de algum hardware, apenas é como boa como os dados que tem.</span><span class="sxs-lookup"><span data-stu-id="3be11-128">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span>
<span data-ttu-id="3be11-129">Algumas informações não está corretamente configuradas por fabricantes de hardware e podem, por conseguinte, não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="3be11-129">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

### <a name="listing-installed-hotfixes"></a><span data-ttu-id="3be11-130">Listagem instaladas as correções</span><span class="sxs-lookup"><span data-stu-id="3be11-130">Listing Installed Hotfixes</span></span>

<span data-ttu-id="3be11-131">Pode listar correções instaladas todas as utilizando **Win32_QuickFixEngineering**:</span><span class="sxs-lookup"><span data-stu-id="3be11-131">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

<span data-ttu-id="3be11-132">Esta classe devolve uma lista de correções que tem este aspeto:</span><span class="sxs-lookup"><span data-stu-id="3be11-132">This class returns a list of hotfixes that looks like this:</span></span>

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

<span data-ttu-id="3be11-133">Para uma saída mais sucinta, pode pretender excluir algumas propriedades.</span><span class="sxs-lookup"><span data-stu-id="3be11-133">For more succinct output, you may want to exclude some properties.</span></span>
<span data-ttu-id="3be11-134">Apesar de poder utilizar o `Get-CimInstance`do **propriedade** parâmetro escolher apenas o **HotFixID**, fazê-lo, por isso, irão devolver mais informações, porque todos os metadados é apresentado por predefinição:</span><span class="sxs-lookup"><span data-stu-id="3be11-134">Although you can use the `Get-CimInstance`'s **Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixID
```

```output
PSShowComputerName    : True
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4048951
InstalledBy           :
ServicePackInEffect   :
PSComputerName        : .
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

<span data-ttu-id="3be11-135">Os dados adicionais são devolvidos porque o parâmetro de propriedade em `Get-CimInstance` restringe as propriedades devolvidas de instâncias de classe WMI, não o objeto devolvido para o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3be11-135">The additional data is returned, because the Property parameter in `Get-CimInstance` restricts the properties returned from WMI class instances, not the object returned to Windows PowerShell.</span></span>
<span data-ttu-id="3be11-136">Para reduzir a saída, utilize `Select-Object`:</span><span class="sxs-lookup"><span data-stu-id="3be11-136">To reduce the output, use `Select-Object`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

### <a name="listing-operating-system-version-information"></a><span data-ttu-id="3be11-137">Listar as informações de versão do sistema operativo</span><span class="sxs-lookup"><span data-stu-id="3be11-137">Listing Operating System Version Information</span></span>

<span data-ttu-id="3be11-138">O **Win32_OperatingSystem** propriedades de classe incluem informações de pacote de versão e serviço.</span><span class="sxs-lookup"><span data-stu-id="3be11-138">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span>
<span data-ttu-id="3be11-139">Pode selecionar explicitamente só estas propriedades para obter informações de versão um resumo de **Win32_OperatingSystem**:</span><span class="sxs-lookup"><span data-stu-id="3be11-139">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="3be11-140">Também pode utilizar carateres universais com o `Select-Object`do **propriedade** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3be11-140">You can also use wildcards with the `Select-Object`'s **Property** parameter.</span></span>
<span data-ttu-id="3be11-141">Porque todas as propriedades começando com um **criar** ou **ServicePack** são importantes para utilizar aqui, iremos pode abreviar este para o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="3be11-141">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*
```

```output
BuildNumber             : 16299
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a><span data-ttu-id="3be11-142">Listar utilizadores locais e proprietário</span><span class="sxs-lookup"><span data-stu-id="3be11-142">Listing Local Users and Owner</span></span>

<span data-ttu-id="3be11-143">Informações gerais de utilizadores local — número de utilizadores licenciados, o número atual de utilizadores e o nome do proprietário — pode ser encontrado com uma seleção de **Win32_OperatingSystem** propriedades dos classe.</span><span class="sxs-lookup"><span data-stu-id="3be11-143">Local general user information — number of licensed users, current number of users, and owner name — can be found with a selection of **Win32_OperatingSystem** class' properties.</span></span>
<span data-ttu-id="3be11-144">Pode selecionar explicitamente as propriedades a apresentar como esta:</span><span class="sxs-lookup"><span data-stu-id="3be11-144">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="3be11-145">Uma versão mais sucinta utilizando carateres universais é:</span><span class="sxs-lookup"><span data-stu-id="3be11-145">A more succinct version using wildcards is:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a><span data-ttu-id="3be11-146">Ao obter espaço livre em disco</span><span class="sxs-lookup"><span data-stu-id="3be11-146">Getting Available Disk Space</span></span>

<span data-ttu-id="3be11-147">Para ver o espaço em disco e o espaço livre para unidades locais, pode utilizar a classe Win32_LogicalDisk WMI.</span><span class="sxs-lookup"><span data-stu-id="3be11-147">To see the disk space and free space for local drives, you can use the Win32_LogicalDisk WMI class.</span></span>
<span data-ttu-id="3be11-148">É necessário ver apenas instâncias com um DriveType de 3 — valor utiliza o WMI para discos rígidos de fixo.</span><span class="sxs-lookup"><span data-stu-id="3be11-148">You need to see only instances with a DriveType of 3 — the value WMI uses for fixed hard disks.</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .

Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum

Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

### <a name="getting-logon-session-information"></a><span data-ttu-id="3be11-149">Obter informações de sessão de início de sessão</span><span class="sxs-lookup"><span data-stu-id="3be11-149">Getting Logon Session Information</span></span>

<span data-ttu-id="3be11-150">Pode obter informações gerais sobre sessões de início de sessão associados a utilizadores através de **Win32_LogonSession** classe WMI:</span><span class="sxs-lookup"><span data-stu-id="3be11-150">You can get general information about logon sessions associated with users through the **Win32_LogonSession** WMI class:</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="3be11-151">Obter o utilizador com sessão iniciado num computador</span><span class="sxs-lookup"><span data-stu-id="3be11-151">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="3be11-152">Pode visualizar o utilizador com sessão iniciado num sistema informático específico utilizando Win32_ComputerSystem.</span><span class="sxs-lookup"><span data-stu-id="3be11-152">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span>
<span data-ttu-id="3be11-153">Este comando devolve apenas o utilizador com sessão iniciado no ambiente de trabalho do sistema:</span><span class="sxs-lookup"><span data-stu-id="3be11-153">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="3be11-154">Obter a hora Local do computador</span><span class="sxs-lookup"><span data-stu-id="3be11-154">Getting Local Time from a Computer</span></span>

<span data-ttu-id="3be11-155">Pode obter a hora local atual num computador específico utilizando o **Win32_LocalTime** classe WMI.</span><span class="sxs-lookup"><span data-stu-id="3be11-155">You can retrieve the current local time on a specific computer by using the **Win32_LocalTime** WMI class.</span></span>

```powershell
Get-CimInstance -ClassName Win32_LocalTime -ComputerName .

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2017
PSComputerName : .
```

### <a name="displaying-service-status"></a><span data-ttu-id="3be11-156">Apresentar o estado do serviço</span><span class="sxs-lookup"><span data-stu-id="3be11-156">Displaying Service Status</span></span>

<span data-ttu-id="3be11-157">Para ver o estado de todos os serviços num computador específico, localmente pode utilizar o `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3be11-157">To view the status of all services on a specific computer, you can locally use the `Get-Service` cmdlet.</span></span>
<span data-ttu-id="3be11-158">Para sistemas remotos, pode utilizar o **Win32_Service** classe WMI.</span><span class="sxs-lookup"><span data-stu-id="3be11-158">For remote systems, you can use the **Win32_Service** WMI class.</span></span>
<span data-ttu-id="3be11-159">Se também de utilizar `Select-Object` para filtrar os resultados para **estado**, **nome**, e **DisplayName**, o formato de saída serão praticamente idêntico à `Get-Service`:</span><span class="sxs-lookup"><span data-stu-id="3be11-159">If you also use `Select-Object` to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from `Get-Service`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="3be11-160">Para permitir a apresentação de nomes para os serviços ocasionais com nomes extremamente longos concluída, pode pretender utilizar `Format-Table` com o **AutoSize** e **moldar** parâmetros, para otimizar a largura da coluna e Permita nomes longos moldar em vez de a ser truncado:</span><span class="sxs-lookup"><span data-stu-id="3be11-160">To allow the complete display of names for the occasional services with extremely long names, you may want to use `Format-Table` with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
