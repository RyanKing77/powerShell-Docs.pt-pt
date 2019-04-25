---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Recolher Informações sobre os Computadores
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: d837684108656e17ebf26189bd4841c5de01051c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058340"
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="1de0e-103">Recolher Informações sobre os Computadores</span><span class="sxs-lookup"><span data-stu-id="1de0e-103">Collecting Information About Computers</span></span>

<span data-ttu-id="1de0e-104">Cmdlets da **CimCmdlets** módulo são os cmdlets mais importantes para tarefas de gestão do sistema geral.</span><span class="sxs-lookup"><span data-stu-id="1de0e-104">Cmdlets from **CimCmdlets** module are the most important cmdlets for general system management tasks.</span></span>
<span data-ttu-id="1de0e-105">Todas as definições de subsistema críticos são expostas por meio de WMI.</span><span class="sxs-lookup"><span data-stu-id="1de0e-105">All critical subsystem settings are exposed through WMI.</span></span>
<span data-ttu-id="1de0e-106">Além disso, o WMI trata dados como objetos que estão em coleções de um ou mais itens.</span><span class="sxs-lookup"><span data-stu-id="1de0e-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span>
<span data-ttu-id="1de0e-107">Como o Windows PowerShell também funciona com objetos e tem um pipeline que permite tratar únicos ou vários objetos da mesma forma, o acesso WMI genérico permite-lhe executar algumas tarefas avançadas com muito pouco de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1de0e-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

<span data-ttu-id="1de0e-108">Os exemplos seguintes demonstram como recolher informações específicas, utilizando `Get-CimInstance` num computador arbitrário.</span><span class="sxs-lookup"><span data-stu-id="1de0e-108">The following examples demonstrate how to collect specific information by using `Get-CimInstance` against an arbitrary computer.</span></span>
<span data-ttu-id="1de0e-109">Especificamos o **nomedocomputador** parâmetro com o valor de ponto (**.**), que representa o computador local.</span><span class="sxs-lookup"><span data-stu-id="1de0e-109">We specify the **ComputerName** parameter with the dot value (**.**), which represents the local computer.</span></span>
<span data-ttu-id="1de0e-110">Pode especificar um nome ou endereço IP associado a qualquer computador que pode aceder através do WMI.</span><span class="sxs-lookup"><span data-stu-id="1de0e-110">You can specify a name or IP address associated with any computer you can reach through WMI.</span></span>
<span data-ttu-id="1de0e-111">Para obter informações sobre o computador local, poderia omitir a **ComputerName** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1de0e-111">To retrieve information about the local computer, you could omit the **ComputerName** parameter.</span></span>

## <a name="listing-desktop-settings"></a><span data-ttu-id="1de0e-112">Listagem das configurações de Desktops</span><span class="sxs-lookup"><span data-stu-id="1de0e-112">Listing Desktop Settings</span></span>

<span data-ttu-id="1de0e-113">Vamos começar com um comando que coleta informações sobre as áreas de trabalho no computador local.</span><span class="sxs-lookup"><span data-stu-id="1de0e-113">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

<span data-ttu-id="1de0e-114">Esta ação devolve informações para todas as áreas de trabalho, quer estejam em utilização ou não.</span><span class="sxs-lookup"><span data-stu-id="1de0e-114">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="1de0e-115">Informações devolvidas por algumas classes WMI podem ser muito detalhada e, muitas vezes, incluir metadados sobre a classe WMI.</span><span class="sxs-lookup"><span data-stu-id="1de0e-115">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span>
<span data-ttu-id="1de0e-116">Uma vez que a maioria dessas propriedades de metadados têm nomes que começam com **Cim**, pode filtrar as propriedades utilizando `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="1de0e-116">Because most of these metadata properties have names that begin with **Cim**, you can filter the properties using `Select-Object`.</span></span>
<span data-ttu-id="1de0e-117">Especifique a **- ExcludeProperty** parâmetro com "Cim \*" como o valor.</span><span class="sxs-lookup"><span data-stu-id="1de0e-117">Specify the **-ExcludeProperty** parameter with "Cim\*" as the value.</span></span>
<span data-ttu-id="1de0e-118">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1de0e-118">For example:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="1de0e-119">Para filtrar os metadados, utilize um operador de pipeline (|) para enviar os resultados do `Get-CimInstance` comando para `Select-Object -ExcludeProperty "CIM*"`.</span><span class="sxs-lookup"><span data-stu-id="1de0e-119">To filter out the metadata, use a pipeline operator (|) to send the results of the `Get-CimInstance` command to `Select-Object -ExcludeProperty "CIM*"`.</span></span>

## <a name="listing-bios-information"></a><span data-ttu-id="1de0e-120">A listagem de informações do BIOS</span><span class="sxs-lookup"><span data-stu-id="1de0e-120">Listing BIOS Information</span></span>

<span data-ttu-id="1de0e-121">O WMI **Win32_BIOS** classe devolve informações bastante compactas e completas sobre o BIOS do sistema no computador local:</span><span class="sxs-lookup"><span data-stu-id="1de0e-121">The WMI **Win32_BIOS** class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

## <a name="listing-processor-information"></a><span data-ttu-id="1de0e-122">A listagem de informações do processador</span><span class="sxs-lookup"><span data-stu-id="1de0e-122">Listing Processor Information</span></span>

<span data-ttu-id="1de0e-123">Pode recuperar as informações do processador geral através do WMI **Win32_Processor** de classe, embora provavelmente desejará filtrar as informações:</span><span class="sxs-lookup"><span data-stu-id="1de0e-123">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="1de0e-124">Para uma cadeia de descrição genérica da família de processadores, pode simplesmente retornar o **SystemType** propriedade:</span><span class="sxs-lookup"><span data-stu-id="1de0e-124">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="1de0e-125">A listagem de fabricante de computador e o modelo</span><span class="sxs-lookup"><span data-stu-id="1de0e-125">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="1de0e-126">Informações do modelo de computador também estão disponíveis a partir **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="1de0e-126">Computer model information is also available from **Win32_ComputerSystem**.</span></span>
<span data-ttu-id="1de0e-127">A saída exibida padrão não terá de filtragem para fornecer dados de OEM:</span><span class="sxs-lookup"><span data-stu-id="1de0e-127">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

<span data-ttu-id="1de0e-128">A saída dos comandos como esta, que devolvem informações diretamente a partir de algum hardware, apenas é tão bom quanto os de dados que tiver.</span><span class="sxs-lookup"><span data-stu-id="1de0e-128">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span>
<span data-ttu-id="1de0e-129">Algumas informações não estão configuradas corretamente por fabricantes de hardware e podem, por conseguinte, ficar indisponíveis.</span><span class="sxs-lookup"><span data-stu-id="1de0e-129">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

## <a name="listing-installed-hotfixes"></a><span data-ttu-id="1de0e-130">Listagem instalados Hotfixes</span><span class="sxs-lookup"><span data-stu-id="1de0e-130">Listing Installed Hotfixes</span></span>

<span data-ttu-id="1de0e-131">Pode listar as correções instaladas tudo usando **Win32_QuickFixEngineering**:</span><span class="sxs-lookup"><span data-stu-id="1de0e-131">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

<span data-ttu-id="1de0e-132">Essa classe retorna uma lista de correções que tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="1de0e-132">This class returns a list of hotfixes that looks like this:</span></span>

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

<span data-ttu-id="1de0e-133">Para mais sucinta saída, pode querer excluir algumas propriedades.</span><span class="sxs-lookup"><span data-stu-id="1de0e-133">For more succinct output, you may want to exclude some properties.</span></span>
<span data-ttu-id="1de0e-134">Apesar de poder utilizar o `Get-CimInstance`da **propriedade** parâmetro escolher apenas a **HotFixID**, ao fazê-lo por isso, na verdade, retornará obter mais informações, uma vez que todos os metadados é apresentado por predefinição:</span><span class="sxs-lookup"><span data-stu-id="1de0e-134">Although you can use the `Get-CimInstance`'s **Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

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

<span data-ttu-id="1de0e-135">Os dados adicionais são retornados, porque o parâmetro de propriedade no `Get-CimInstance` restringe as propriedades retornadas de instâncias de classes do WMI, não o objeto retornado para o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1de0e-135">The additional data is returned, because the Property parameter in `Get-CimInstance` restricts the properties returned from WMI class instances, not the object returned to Windows PowerShell.</span></span>
<span data-ttu-id="1de0e-136">Para reduzir a saída, utilize `Select-Object`:</span><span class="sxs-lookup"><span data-stu-id="1de0e-136">To reduce the output, use `Select-Object`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a><span data-ttu-id="1de0e-137">A listagem de informações de versão do sistema operativo</span><span class="sxs-lookup"><span data-stu-id="1de0e-137">Listing Operating System Version Information</span></span>

<span data-ttu-id="1de0e-138">O **Win32_OperatingSystem** propriedades de classe incluem informações de pacote de versão e o serviço.</span><span class="sxs-lookup"><span data-stu-id="1de0e-138">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span>
<span data-ttu-id="1de0e-139">Pode selecionar apenas essas propriedades para obter informações sobre a versão um resumo de explicitamente **Win32_OperatingSystem**:</span><span class="sxs-lookup"><span data-stu-id="1de0e-139">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="1de0e-140">Também pode utilizar carateres universais com o `Select-Object`da **propriedade** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1de0e-140">You can also use wildcards with the `Select-Object`'s **Property** parameter.</span></span>
<span data-ttu-id="1de0e-141">Uma vez que todas as propriedades de um a partir **crie** ou **Service Pack** são importantes para utilizar aqui, podem reduzir isso para o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="1de0e-141">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

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

## <a name="listing-local-users-and-owner"></a><span data-ttu-id="1de0e-142">A listagem de utilizadores locais e proprietário</span><span class="sxs-lookup"><span data-stu-id="1de0e-142">Listing Local Users and Owner</span></span>

<span data-ttu-id="1de0e-143">Informações gerais de utilizadores local — o número de utilizadores com licenças, número de utilizadores e o nome do proprietário atual — podem ser encontrados com uma seleção de **Win32_OperatingSystem** propriedades de classe.</span><span class="sxs-lookup"><span data-stu-id="1de0e-143">Local general user information — number of licensed users, current number of users, and owner name — can be found with a selection of **Win32_OperatingSystem** class' properties.</span></span>
<span data-ttu-id="1de0e-144">Pode selecionar explicitamente as propriedades para apresentar como este:</span><span class="sxs-lookup"><span data-stu-id="1de0e-144">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="1de0e-145">Uma versão mais sucinta usando caracteres curinga é:</span><span class="sxs-lookup"><span data-stu-id="1de0e-145">A more succinct version using wildcards is:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a><span data-ttu-id="1de0e-146">Obter o espaço em disco disponível</span><span class="sxs-lookup"><span data-stu-id="1de0e-146">Getting Available Disk Space</span></span>

<span data-ttu-id="1de0e-147">Para ver o espaço em disco e o espaço livre para unidades locais, pode usar a classe WMI de Win32_LogicalDisk.</span><span class="sxs-lookup"><span data-stu-id="1de0e-147">To see the disk space and free space for local drives, you can use the Win32_LogicalDisk WMI class.</span></span>
<span data-ttu-id="1de0e-148">É necessário ver apenas instâncias com drivetype igual de 3 – o valor que utiliza o WMI para fixo discos rígidos.</span><span class="sxs-lookup"><span data-stu-id="1de0e-148">You need to see only instances with a DriveType of 3 — the value WMI uses for fixed hard disks.</span></span>

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

## <a name="getting-logon-session-information"></a><span data-ttu-id="1de0e-149">Obter informações de sessão de início de sessão</span><span class="sxs-lookup"><span data-stu-id="1de0e-149">Getting Logon Session Information</span></span>

<span data-ttu-id="1de0e-150">Pode obter informações gerais sobre sessões de início de sessão associados a utilizadores através da **Win32_LogonSession** classe WMI:</span><span class="sxs-lookup"><span data-stu-id="1de0e-150">You can get general information about logon sessions associated with users through the **Win32_LogonSession** WMI class:</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

## <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="1de0e-151">Obter o utilizador com sessão iniciado num computador</span><span class="sxs-lookup"><span data-stu-id="1de0e-151">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="1de0e-152">Pode exibir o usuário conectado a um sistema de computador específico usando Win32_ComputerSystem.</span><span class="sxs-lookup"><span data-stu-id="1de0e-152">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span>
<span data-ttu-id="1de0e-153">Este comando devolve apenas o utilizador com sessão iniciado na área de trabalho do sistema:</span><span class="sxs-lookup"><span data-stu-id="1de0e-153">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

## <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="1de0e-154">Obter a hora Local de um computador</span><span class="sxs-lookup"><span data-stu-id="1de0e-154">Getting Local Time from a Computer</span></span>

<span data-ttu-id="1de0e-155">Pode obter a hora local atual num computador específico utilizando o **Win32_LocalTime** classe WMI.</span><span class="sxs-lookup"><span data-stu-id="1de0e-155">You can retrieve the current local time on a specific computer by using the **Win32_LocalTime** WMI class.</span></span>

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

## <a name="displaying-service-status"></a><span data-ttu-id="1de0e-156">Exibir o Status do serviço</span><span class="sxs-lookup"><span data-stu-id="1de0e-156">Displaying Service Status</span></span>

<span data-ttu-id="1de0e-157">Para ver o estado de todos os serviços num computador específico, pode usar localmente o `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1de0e-157">To view the status of all services on a specific computer, you can locally use the `Get-Service` cmdlet.</span></span>
<span data-ttu-id="1de0e-158">Para sistemas remotos, pode utilizar o **Win32_Service** classe WMI.</span><span class="sxs-lookup"><span data-stu-id="1de0e-158">For remote systems, you can use the **Win32_Service** WMI class.</span></span>
<span data-ttu-id="1de0e-159">Caso também utilize `Select-Object` para filtrar os resultados para **Status**, **nome**, e **DisplayName**, o formato de saída será quase idêntico do `Get-Service`:</span><span class="sxs-lookup"><span data-stu-id="1de0e-159">If you also use `Select-Object` to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from `Get-Service`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="1de0e-160">Para permitir a apresentação completa de nomes para os serviços ocasionais com nomes muito longos, talvez queira usar `Format-Table` com o **AutoSize** e **encapsular** parâmetros, para otimizar a largura da coluna e Permitir nomes longos encapsular em vez de que está a ser truncado:</span><span class="sxs-lookup"><span data-stu-id="1de0e-160">To allow the complete display of names for the occasional services with extremely long names, you may want to use `Format-Table` with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
