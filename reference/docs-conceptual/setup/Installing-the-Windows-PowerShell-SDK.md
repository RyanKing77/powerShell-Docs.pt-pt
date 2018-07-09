---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Instalar o SKD do Windows PowerShell
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: fa876bac0c1afac24f93d11dd2e7ecfb1165cf5f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893543"
---
# <a name="installing-the-windows-powershell-sdk"></a><span data-ttu-id="f415c-103">Instalar o SKD do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f415c-103">Installing the Windows PowerShell SDK</span></span>

<span data-ttu-id="f415c-104">O tópico seguinte descreve como instalar o SDK do PowerShell em diferentes versões do Windows.</span><span class="sxs-lookup"><span data-stu-id="f415c-104">The following topic describes how to install the PowerShell SDK on different versions of Windows.</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a><span data-ttu-id="f415c-105">Instalar o Windows PowerShell 3.0 SDK para Windows 8 e Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="f415c-105">Installing Windows PowerShell 3.0 SDK for Windows 8 and Windows Server 2012</span></span>

<span data-ttu-id="f415c-106">Windows PowerShell 3.0 é instalado automaticamente com o Windows 8 e Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="f415c-106">Windows PowerShell 3.0 is automatically installed with Windows 8 and Windows Server 2012.</span></span>
<span data-ttu-id="f415c-107">Além disso, pode transferir e instalar os assemblies de referência para o Windows PowerShell 3.0 como parte do SDK do Windows 8.</span><span class="sxs-lookup"><span data-stu-id="f415c-107">In addition, you can download and install the reference assemblies for Windows PowerShell 3.0 as part of the Windows 8 SDK.</span></span>
<span data-ttu-id="f415c-108">Esses assemblies permitem-lhe escrever programas de anfitrião, fornecedores e cmdlets para o Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="f415c-108">These assemblies allow you to write cmdlets, providers, and host programs for Windows PowerShell 3.0.</span></span>
<span data-ttu-id="f415c-109">Ao instalar o Windows SDK para Windows 8, os assemblies do Windows PowerShell são instalados automaticamente na pasta de assemblagem de referência, no `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.</span><span class="sxs-lookup"><span data-stu-id="f415c-109">When you install the Windows SDK for Windows 8, the Windows PowerShell assemblies are automatically installed in the reference assembly folder, in `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.</span></span>
<span data-ttu-id="f415c-110">Para obter mais informações, consulte a [site de download do SDK do Windows 8](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).</span><span class="sxs-lookup"><span data-stu-id="f415c-110">For more information, see the [Windows 8 SDK download site](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).</span></span>
<span data-ttu-id="f415c-111">Exemplos de código do Windows PowerShell também estão disponíveis no Centro de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="f415c-111">Windows PowerShell code samples are also available on the Development Center.</span></span>
<span data-ttu-id="f415c-112">Para obter mais informações, consulte a página de exemplo de código de área de trabalho sobre o [site do Centro de desenvolvimento](https://code.msdn.microsoft.com:443/windowsdesktop/).</span><span class="sxs-lookup"><span data-stu-id="f415c-112">For more information, see the Desktop code sample page on the [Dev center site](https://code.msdn.microsoft.com:443/windowsdesktop/).</span></span>

<span data-ttu-id="f415c-113">Além disso, o Windows PowerShell 3.0 está retroativamente compatível com o SDK do Windows PowerShell 2.0, que inclui um número de amostras de código.</span><span class="sxs-lookup"><span data-stu-id="f415c-113">In addition, Windows PowerShell 3.0 is backwards-compatible with the Windows PowerShell 2.0 SDK, which includes a number of code samples.</span></span>
<span data-ttu-id="f415c-114">Para obter mais informações sobre como transferir o SDK do Windows PowerShell 2.0, veja a seguir.</span><span class="sxs-lookup"><span data-stu-id="f415c-114">For more information on how to download the Windows PowerShell 2.0 SDK, see below.</span></span>
<span data-ttu-id="f415c-115">(Observe que embora os exemplos de 2.0 código são compatíveis com o Windows 8 e Windows PowerShell 3.0, não é possível instalar Windows PowerShell 2.0 numa plataforma Windows 8.)</span><span class="sxs-lookup"><span data-stu-id="f415c-115">(Note that while the 2.0 code samples are compatible with Windows 8 and Windows PowerShell 3.0, you cannot install Windows PowerShell 2.0 on a Windows 8 platform.)</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a><span data-ttu-id="f415c-116">Instalar o Windows PowerShell 3.0 SDK para Windows 7 e Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="f415c-116">Installing Windows PowerShell 3.0 SDK for Windows 7 and Windows Server 2008 R2</span></span>

<span data-ttu-id="f415c-117">Windows 7 e Windows Server 2008 R2 têm automaticamente PowerShell 2.0 instalado.</span><span class="sxs-lookup"><span data-stu-id="f415c-117">Windows 7 and Windows Server 2008 R2 automatically have PowerShell 2.0 installed.</span></span>
<span data-ttu-id="f415c-118">Além disso, pode instalar o PowerShell 3.0 nesses sistemas.</span><span class="sxs-lookup"><span data-stu-id="f415c-118">In addition, you can install PowerShell 3.0 on these systems.</span></span>
<span data-ttu-id="f415c-119">(Para obter mais informações, consulte [instalar o Windows PowerShell](Installing-Windows-PowerShell.md).).</span><span class="sxs-lookup"><span data-stu-id="f415c-119">(For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).).</span></span>
<span data-ttu-id="f415c-120">Conforme descrito acima, também pode instalar o SDK do Windows 8 no Windows 7 e Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="f415c-120">As described above, you can also install the Windows 8 SDK on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a><span data-ttu-id="f415c-121">Instalar o Windows PowerShell 2.0 SDK para Windows 7, Vista, XP, Server 2003 e o Server 2008</span><span class="sxs-lookup"><span data-stu-id="f415c-121">Installing Windows PowerShell 2.0 SDK for Windows 7, Vista, XP, Server 2003, and Server 2008</span></span>

<span data-ttu-id="f415c-122">O SDK do Windows PowerShell 2.0 fornece os assemblies de referência necessários para escrever cmdlets, fornecedores e alojamento de aplicações e fornece c# código de exemplo que pode ser usado como o ponto de partida, quando começa a escrever código.</span><span class="sxs-lookup"><span data-stu-id="f415c-122">The Windows PowerShell 2.0 SDK provides the reference assemblies needed to write cmdlets, providers, and hosting applications, and it provides C# sample code that can be used as the starting point when you begin writing code.</span></span>

<span data-ttu-id="f415c-123">Para instalar este SDK, consulte [SDK do Windows PowerShell 2.0](http://www.microsoft.com/en-us/download/details.aspx?id=2560).</span><span class="sxs-lookup"><span data-stu-id="f415c-123">To install this SDK, see [Windows PowerShell 2.0 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=2560).</span></span>

## <a name="reference-assemblies"></a><span data-ttu-id="f415c-124">Assemblies de referência</span><span class="sxs-lookup"><span data-stu-id="f415c-124">Reference assemblies</span></span>

<span data-ttu-id="f415c-125">Assemblies de referência são instalados na seguinte localização por predefinição: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span><span class="sxs-lookup"><span data-stu-id="f415c-125">Reference assemblies are installed in the following location by default: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span></span>

> [!NOTE] 
> <span data-ttu-id="f415c-126">Não é possível carregar o código que é compilado contra os assemblies do Windows PowerShell 2.0 em instalações do Windows PowerShell 1.0.</span><span class="sxs-lookup"><span data-stu-id="f415c-126">Code that is compiled against the Windows PowerShell 2.0 assemblies cannot be loaded into Windows PowerShell 1.0 installations.</span></span>
> <span data-ttu-id="f415c-127">No entanto, o código que é compilado contra os assemblies do Windows PowerShell 1.0 pode ser carregado para instalações do Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="f415c-127">However, code that is compiled against the Windows PowerShell 1.0 assemblies can be loaded into Windows PowerShell 2.0 installations.</span></span>

## <a name="samples"></a><span data-ttu-id="f415c-128">Amostras</span><span class="sxs-lookup"><span data-stu-id="f415c-128">Samples</span></span>

<span data-ttu-id="f415c-129">Exemplos de código são instalados na seguinte localização por predefinição: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="f415c-129">Code samples are installed in the following location by default: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span></span>

<span data-ttu-id="f415c-130">As secções seguintes fornecem uma breve descrição do que faz cada exemplo.</span><span class="sxs-lookup"><span data-stu-id="f415c-130">The following sections provide a brief description of what each sample does.</span></span>

## <a name="cmdlet-samples"></a><span data-ttu-id="f415c-131">Exemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="f415c-131">Cmdlet samples</span></span>

### <a name="getprocesssample01"></a><span data-ttu-id="f415c-132">GetProcessSample01</span><span class="sxs-lookup"><span data-stu-id="f415c-132">GetProcessSample01</span></span>

<span data-ttu-id="f415c-133">Mostra como escrever um cmdlet simple que obtém todos os processos no computador local.</span><span class="sxs-lookup"><span data-stu-id="f415c-133">Shows how to write a simple cmdlet that gets all the processes on the local computer.</span></span>

### <a name="getprocesssample02"></a><span data-ttu-id="f415c-134">GetProcessSample02</span><span class="sxs-lookup"><span data-stu-id="f415c-134">GetProcessSample02</span></span>

<span data-ttu-id="f415c-135">Mostra como adicionar parâmetros ao cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f415c-135">Shows how to add parameters to the cmdlet.</span></span>
<span data-ttu-id="f415c-136">O cmdlet assume uma ou mais nomes de processo e retorna os processos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="f415c-136">The cmdlet takes one or more process names and returns the matching processes.</span></span>

### <a name="getprocesssample03"></a><span data-ttu-id="f415c-137">GetProcessSample03</span><span class="sxs-lookup"><span data-stu-id="f415c-137">GetProcessSample03</span></span>

<span data-ttu-id="f415c-138">Mostra como adicionar parâmetros que aceitam entrada do pipeline.</span><span class="sxs-lookup"><span data-stu-id="f415c-138">Shows how to add parameters that accept input from the pipeline.</span></span>

### <a name="getprocesssample04"></a><span data-ttu-id="f415c-139">GetProcessSample04</span><span class="sxs-lookup"><span data-stu-id="f415c-139">GetProcessSample04</span></span>

<span data-ttu-id="f415c-140">Mostra como lidar com erros de não terminação.</span><span class="sxs-lookup"><span data-stu-id="f415c-140">Shows how to handle nonterminating errors.</span></span>

### <a name="getprocesssample05"></a><span data-ttu-id="f415c-141">GetProcessSample05</span><span class="sxs-lookup"><span data-stu-id="f415c-141">GetProcessSample05</span></span>

<span data-ttu-id="f415c-142">Mostra como exibir uma lista de processos.</span><span class="sxs-lookup"><span data-stu-id="f415c-142">Shows how to display a list of specified processes.</span></span>

### <a name="selectobject"></a><span data-ttu-id="f415c-143">SelectObject</span><span class="sxs-lookup"><span data-stu-id="f415c-143">SelectObject</span></span>

<span data-ttu-id="f415c-144">Mostra como escrever um filtro para selecionar apenas a determinados objetos.</span><span class="sxs-lookup"><span data-stu-id="f415c-144">Shows how to write a filter to select only certain objects.</span></span>

### <a name="selectstring"></a><span data-ttu-id="f415c-145">SelectString</span><span class="sxs-lookup"><span data-stu-id="f415c-145">SelectString</span></span>

<span data-ttu-id="f415c-146">Mostra como procurar ficheiros para padrões especificados.</span><span class="sxs-lookup"><span data-stu-id="f415c-146">Shows how to search files for specified patterns.</span></span>

### <a name="stopprocesssample01"></a><span data-ttu-id="f415c-147">StopProcessSample01</span><span class="sxs-lookup"><span data-stu-id="f415c-147">StopProcessSample01</span></span>

<span data-ttu-id="f415c-148">Mostra como implementar um *PassThru* parâmetro e como solicitar comentários do usuário por chamadas para o [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) e [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) métodos.</span><span class="sxs-lookup"><span data-stu-id="f415c-148">Shows how to implement a *PassThru* parameter, and how to request user feedback by calls to the [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) and [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) methods.</span></span>
<span data-ttu-id="f415c-149">Os utilizadores podem especificar a *PassThru* parâmetro quando pretendem forçar o cmdlet para retornar um objeto,</span><span class="sxs-lookup"><span data-stu-id="f415c-149">Users specify the *PassThru* parameter when they want to force the cmdlet to return an object,</span></span>

### <a name="stopprocesssample02"></a><span data-ttu-id="f415c-150">StopProcessSample02</span><span class="sxs-lookup"><span data-stu-id="f415c-150">StopProcessSample02</span></span>

<span data-ttu-id="f415c-151">Mostra como parar um processo específico.</span><span class="sxs-lookup"><span data-stu-id="f415c-151">Shows how to stop a specific process.</span></span>

### <a name="stopprocesssample03"></a><span data-ttu-id="f415c-152">StopProcessSample03</span><span class="sxs-lookup"><span data-stu-id="f415c-152">StopProcessSample03</span></span>

<span data-ttu-id="f415c-153">Mostra como declarar aliases para os parâmetros e como suportam carateres universais.</span><span class="sxs-lookup"><span data-stu-id="f415c-153">Shows how to declare aliases for parameters and how to support wildcards.</span></span>

### <a name="stopprocesssample04"></a><span data-ttu-id="f415c-154">StopProcessSample04</span><span class="sxs-lookup"><span data-stu-id="f415c-154">StopProcessSample04</span></span>

<span data-ttu-id="f415c-155">Mostra como declarar os conjuntos de parâmetros, o objeto que o cmdlet assume como entrada e como especificar o parâmetro predefinido para utilizar.</span><span class="sxs-lookup"><span data-stu-id="f415c-155">Shows how to declare parameter sets, the object that the cmdlet takes as input, and how to specify the default parameter set to use.</span></span>

## <a name="remoting-samples"></a><span data-ttu-id="f415c-156">Exemplos de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="f415c-156">Remoting samples</span></span>

### <a name="remoterunspace01"></a><span data-ttu-id="f415c-157">RemoteRunspace01</span><span class="sxs-lookup"><span data-stu-id="f415c-157">RemoteRunspace01</span></span>

<span data-ttu-id="f415c-158">Mostra como criar um espaço de execução remoto que é utilizado para estabelecer uma ligação remota.</span><span class="sxs-lookup"><span data-stu-id="f415c-158">Shows how to create a remote runspace that is used to establish a remote connection.</span></span>

### <a name="remoterunspacepool01"></a><span data-ttu-id="f415c-159">RemoteRunspacePool01</span><span class="sxs-lookup"><span data-stu-id="f415c-159">RemoteRunspacePool01</span></span>

<span data-ttu-id="f415c-160">Mostra como construir um conjunto de espaço de execução remoto e como executar vários comandos em simultâneo ao utilizar este conjunto.</span><span class="sxs-lookup"><span data-stu-id="f415c-160">Shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

### <a name="serialization01"></a><span data-ttu-id="f415c-161">Serialization01</span><span class="sxs-lookup"><span data-stu-id="f415c-161">Serialization01</span></span>

<span data-ttu-id="f415c-162">Mostra como examinar uma classe .NET existente e certifique-se de que as informações de propriedades públicas selecionadas dessa classe preservadas na serialização/desserialização.</span><span class="sxs-lookup"><span data-stu-id="f415c-162">Shows how to look at an existing .NET class and make sure that information from selected public properties of this class is preserved across serialization/deserialization.</span></span>

### <a name="serialization02"></a><span data-ttu-id="f415c-163">Serialization02</span><span class="sxs-lookup"><span data-stu-id="f415c-163">Serialization02</span></span>

<span data-ttu-id="f415c-164">Mostra como examinar uma classe .NET existente e certifique-se de que as informações de instância desta classe preservadas na serialização/desserialização quando as informações não estão disponíveis nas propriedades públicas da classe.</span><span class="sxs-lookup"><span data-stu-id="f415c-164">Shows how to look at an existing .NET class and make sure that information from instance of this class is preserved across serialization/deserialization when the information is not available in public properties of the class.</span></span>

### <a name="serialization03"></a><span data-ttu-id="f415c-165">Serialization03</span><span class="sxs-lookup"><span data-stu-id="f415c-165">Serialization03</span></span>

<span data-ttu-id="f415c-166">Mostra como examinar uma classe .NET existente e certifique-se de que as instâncias dessa classe e de classes derivadas são desserializadas (reativado) em objetos do .NET em direto.</span><span class="sxs-lookup"><span data-stu-id="f415c-166">Shows how to look at an existing .NET class and make sure that instances of this class and of derived classes are deserialized (rehydrated) into live .NET objects.</span></span>

## <a name="event-samples"></a><span data-ttu-id="f415c-167">Exemplos de evento</span><span class="sxs-lookup"><span data-stu-id="f415c-167">Event samples</span></span>

### <a name="event01"></a><span data-ttu-id="f415c-168">Event01</span><span class="sxs-lookup"><span data-stu-id="f415c-168">Event01</span></span>

<span data-ttu-id="f415c-169">Mostra como criar um cmdlet para o registo de eventos derivando de ObjectEventRegistrationBase.</span><span class="sxs-lookup"><span data-stu-id="f415c-169">Shows how to create a cmdlet for event registration by deriving from ObjectEventRegistrationBase.</span></span>

### <a name="event02"></a><span data-ttu-id="f415c-170">Event02</span><span class="sxs-lookup"><span data-stu-id="f415c-170">Event02</span></span>

<span data-ttu-id="f415c-171">Mostra como mostra a forma receber notificações de eventos do Windows PowerShell que são gerados em computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="f415c-171">Shows how to shows how to receive notifications of Windows PowerShell events that are generated on remote computers.</span></span>
<span data-ttu-id="f415c-172">Ele usa o evento de PSEventReceived exposto por meio da [espaço de execução](/dotnet/api/system.management.automation.runspaces.runspace) classe.</span><span class="sxs-lookup"><span data-stu-id="f415c-172">It uses the PSEventReceived event exposed through the [Runspace](/dotnet/api/system.management.automation.runspaces.runspace) class.</span></span>

## <a name="hosting-application-samples"></a><span data-ttu-id="f415c-173">Exemplos de aplicações de alojamento</span><span class="sxs-lookup"><span data-stu-id="f415c-173">Hosting application samples</span></span>

### <a name="runspace01"></a><span data-ttu-id="f415c-174">Runspace01</span><span class="sxs-lookup"><span data-stu-id="f415c-174">Runspace01</span></span>

<span data-ttu-id="f415c-175">Mostra como utilizar o [PowerShell](/dotnet/api/system.management.automation.powershell) classe para executar o [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="f415c-175">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously.</span></span>
<span data-ttu-id="f415c-176">O [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet devolve [processo](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objetos para cada processo em execução no computador local.</span><span class="sxs-lookup"><span data-stu-id="f415c-176">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer.</span></span>

### <a name="runspace02"></a><span data-ttu-id="f415c-177">Runspace02</span><span class="sxs-lookup"><span data-stu-id="f415c-177">Runspace02</span></span>

<span data-ttu-id="f415c-178">Mostra como utilizar o [PowerShell](/dotnet/api/system.management.automation.powershell) classe para executar o [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) e [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="f415c-178">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span>
<span data-ttu-id="f415c-179">O [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet devolve [processo](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objetos para cada processo em execução no computador local e o `Sort-Object` classifica os objetos com base no respetivo [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) propriedade.</span><span class="sxs-lookup"><span data-stu-id="f415c-179">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) property.</span></span>
<span data-ttu-id="f415c-180">Os resultados desses comandos são apresentadas utilizando um [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) controle.</span><span class="sxs-lookup"><span data-stu-id="f415c-180">The results of these commands is displayed by using a [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) control.</span></span>

### <a name="runspace03"></a><span data-ttu-id="f415c-181">Runspace03</span><span class="sxs-lookup"><span data-stu-id="f415c-181">Runspace03</span></span>

<span data-ttu-id="f415c-182">Mostra como utilizar o [PowerShell](/dotnet/api/system.management.automation.powershell) classe para executar um script de forma síncrona e como lidar com erros de não terminação.</span><span class="sxs-lookup"><span data-stu-id="f415c-182">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run a script synchronously, and how to handle non-terminating errors.</span></span>
<span data-ttu-id="f415c-183">O script recebe uma lista de nomes de processo e, em seguida, obtém esses processos.</span><span class="sxs-lookup"><span data-stu-id="f415c-183">The script receives a list of process names and then retrieves those processes.</span></span>
<span data-ttu-id="f415c-184">Os resultados do script, incluindo quaisquer erros de não terminação de mensagens em fila que foram gerados ao executar o script, são exibidos numa janela de consola.</span><span class="sxs-lookup"><span data-stu-id="f415c-184">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

### <a name="runspace04"></a><span data-ttu-id="f415c-185">Runspace04</span><span class="sxs-lookup"><span data-stu-id="f415c-185">Runspace04</span></span>

<span data-ttu-id="f415c-186">Mostra como utilizar o [PowerShell](/dotnet/api/system.management.automation.powershell) classe para executar comandos e como erros de terminação de catch que forem lançadas. quando executar os comandos.</span><span class="sxs-lookup"><span data-stu-id="f415c-186">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span>
<span data-ttu-id="f415c-187">Dois comandos são executados, e o último comando é passado um argumento de parâmetro que não é válido.</span><span class="sxs-lookup"><span data-stu-id="f415c-187">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span>
<span data-ttu-id="f415c-188">Como resultado, não existem objetos são devolvidos e um erro de terminação é lançado.</span><span class="sxs-lookup"><span data-stu-id="f415c-188">As a result, no objects are returned and a terminating error is thrown.</span></span>

### <a name="runspace05"></a><span data-ttu-id="f415c-189">Runspace05</span><span class="sxs-lookup"><span data-stu-id="f415c-189">Runspace05</span></span>

<span data-ttu-id="f415c-190">Mostra como adicionar um snap-in para uma [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) de objeto para que o cmdlet do snap-in está disponível quando o espaço de execução é aberto.</span><span class="sxs-lookup"><span data-stu-id="f415c-190">Shows how to add a snap-in to an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span>
<span data-ttu-id="f415c-191">O snap-in fornece um cmdlet de Get-Proc (definido pela [exemplo de GetProcessSample01](https://technet.microsoft.com/library/ff602028.aspx)) que é executado de forma síncrona ao utilizar um [PowerShell](/dotnet/api/system.management.automation.powershell) objeto.</span><span class="sxs-lookup"><span data-stu-id="f415c-191">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](https://technet.microsoft.com/library/ff602028.aspx)) that is run synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace06"></a><span data-ttu-id="f415c-192">Runspace06</span><span class="sxs-lookup"><span data-stu-id="f415c-192">Runspace06</span></span>

<span data-ttu-id="f415c-193">Mostra como adicionar um módulo para uma [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) de objeto para que o módulo é carregado quando o espaço de execução é aberto.</span><span class="sxs-lookup"><span data-stu-id="f415c-193">Shows how to add a module to an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object so that the module is loaded when the runspace is opened.</span></span>
<span data-ttu-id="f415c-194">O módulo fornece um cmdlet de Get-Proc (definido pela [exemplo de GetProcessSample02](https://technet.microsoft.com/library/ff602027.aspx)) que é executado de forma síncrona ao utilizar um [PowerShell](/dotnet/api/system.management.automation.powershell) objeto.</span><span class="sxs-lookup"><span data-stu-id="f415c-194">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](https://technet.microsoft.com/library/ff602027.aspx)) that is run synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace07"></a><span data-ttu-id="f415c-195">Runspace07</span><span class="sxs-lookup"><span data-stu-id="f415c-195">Runspace07</span></span>

<span data-ttu-id="f415c-196">Mostra como criar um espaço de execução e, em seguida, utilizar esse espaço de execução para executar dois cmdlets de forma síncrona ao utilizar um [PowerShell](/dotnet/api/system.management.automation.powershell) objeto.</span><span class="sxs-lookup"><span data-stu-id="f415c-196">Shows how to create a runspace, and then use that runspace to run two cmdlets synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace08"></a><span data-ttu-id="f415c-197">Runspace08</span><span class="sxs-lookup"><span data-stu-id="f415c-197">Runspace08</span></span>

<span data-ttu-id="f415c-198">Mostra como adicionar comandos e argumentos para o pipeline de uma [PowerShell](/dotnet/api/system.management.automation.powershell) objeto e como executar os comandos de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="f415c-198">Shows how to add commands and arguments to the pipeline of a [PowerShell](/dotnet/api/system.management.automation.powershell) object and how to run the commands synchronously.</span></span>

### <a name="runspace09"></a><span data-ttu-id="f415c-199">Runspace09</span><span class="sxs-lookup"><span data-stu-id="f415c-199">Runspace09</span></span>

<span data-ttu-id="f415c-200">Mostra como adicionar um script para o pipeline de uma [PowerShell](/dotnet/api/system.management.automation.powershell) objeto e como executar o script de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="f415c-200">Shows how to add a script to the pipeline of a [PowerShell](/dotnet/api/system.management.automation.powershell) object and how to run the script asynchronously.</span></span>
<span data-ttu-id="f415c-201">Eventos são usados para manipular a saída do script.</span><span class="sxs-lookup"><span data-stu-id="f415c-201">Events are used to handle the output of the script.</span></span>

### <a name="runspace10"></a><span data-ttu-id="f415c-202">Runspace10</span><span class="sxs-lookup"><span data-stu-id="f415c-202">Runspace10</span></span>

<span data-ttu-id="f415c-203">Mostra como criar um Estado de sessão inicial padrão, como adicionar um cmdlet para o [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), como criar um espaço de execução que utiliza o estado da sessão inicial e como executar o comando utilizando um [PowerShell](/dotnet/api/system.management.automation.powershell)objeto.</span><span class="sxs-lookup"><span data-stu-id="f415c-203">Shows how to create a default initial session state, how to add a cmdlet to the [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), how to create a runspace that uses the initial session state, and how to run the command by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace11"></a><span data-ttu-id="f415c-204">Runspace11</span><span class="sxs-lookup"><span data-stu-id="f415c-204">Runspace11</span></span>

<span data-ttu-id="f415c-205">Mostra como utilizar o [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) classe para criar um comando de proxy que chama um cmdlet existente, mas restringe o conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f415c-205">Shows how to use the [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span>
<span data-ttu-id="f415c-206">O comando de proxy, em seguida, é adicionado a um Estado de sessão inicial que é utilizado para criar um espaço de execução restrito.</span><span class="sxs-lookup"><span data-stu-id="f415c-206">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span>
<span data-ttu-id="f415c-207">Isso significa que o usuário pode acessar a funcionalidade do cmdlet apenas através do comando de proxy.</span><span class="sxs-lookup"><span data-stu-id="f415c-207">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

### <a name="powershell01"></a><span data-ttu-id="f415c-208">PowerShell01</span><span class="sxs-lookup"><span data-stu-id="f415c-208">PowerShell01</span></span>

<span data-ttu-id="f415c-209">Mostra como criar um espaço de execução restrito, usando uma [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) objeto.</span><span class="sxs-lookup"><span data-stu-id="f415c-209">Shows how to create a constrained runspace using an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object.</span></span>

### <a name="powershell02"></a><span data-ttu-id="f415c-210">PowerShell02</span><span class="sxs-lookup"><span data-stu-id="f415c-210">PowerShell02</span></span>

<span data-ttu-id="f415c-211">Mostra como utilizar um agrupamento de espaço de execução para executar vários comandos em simultâneo.</span><span class="sxs-lookup"><span data-stu-id="f415c-211">Shows how to use a runspace pool to run multiple commands concurrently.</span></span>

## <a name="host-samples"></a><span data-ttu-id="f415c-212">Exemplos de anfitrião</span><span class="sxs-lookup"><span data-stu-id="f415c-212">Host samples</span></span>

### <a name="host01"></a><span data-ttu-id="f415c-213">Host01</span><span class="sxs-lookup"><span data-stu-id="f415c-213">Host01</span></span>

<span data-ttu-id="f415c-214">Mostra como implementar um aplicativo de host que usa um host personalizado.</span><span class="sxs-lookup"><span data-stu-id="f415c-214">Shows how to implement a host application that uses a custom host.</span></span>
<span data-ttu-id="f415c-215">Neste exemplo é criado um espaço de execução que utiliza o host personalizado, e, em seguida, o [PowerShell](/dotnet/api/system.management.automation.powershell) API é utilizada para executar um script que chama de "Sair".</span><span class="sxs-lookup"><span data-stu-id="f415c-215">In this sample a runspace is created that uses the custom host, and then the [PowerShell](/dotnet/api/system.management.automation.powershell) API is used to run a script that calls "exit".</span></span>
<span data-ttu-id="f415c-216">O aplicativo host, em seguida, analisa a saída do script e imprime os resultados.</span><span class="sxs-lookup"><span data-stu-id="f415c-216">The host application then looks at the output of the script and prints out the results.</span></span>

### <a name="host02"></a><span data-ttu-id="f415c-217">Host02</span><span class="sxs-lookup"><span data-stu-id="f415c-217">Host02</span></span>

<span data-ttu-id="f415c-218">Mostra como escrever um aplicativo de host que usa o tempo de execução do Windows PowerShell, juntamente com uma implementação de anfitrião personalizado.</span><span class="sxs-lookup"><span data-stu-id="f415c-218">Shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span>
<span data-ttu-id="f415c-219">O aplicativo host define a cultura de anfitrião para o alemão, execuções a [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet e apresenta os resultados à medida que os veria através da utilização pwrsh.exe e, em seguida, imprime os dados atuais e a hora em alemão.</span><span class="sxs-lookup"><span data-stu-id="f415c-219">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them by using pwrsh.exe, and then prints out the current data and time in German.</span></span>

### <a name="host03"></a><span data-ttu-id="f415c-220">Host03</span><span class="sxs-lookup"><span data-stu-id="f415c-220">Host03</span></span>

<span data-ttu-id="f415c-221">Mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console.</span><span class="sxs-lookup"><span data-stu-id="f415c-221">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

### <a name="host04"></a><span data-ttu-id="f415c-222">Host04</span><span class="sxs-lookup"><span data-stu-id="f415c-222">Host04</span></span>

<span data-ttu-id="f415c-223">Mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console.</span><span class="sxs-lookup"><span data-stu-id="f415c-223">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="f415c-224">Este aplicativo de host também suporta a apresentação de pedidos que permitem ao usuário especificar várias opções.</span><span class="sxs-lookup"><span data-stu-id="f415c-224">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

### <a name="host05"></a><span data-ttu-id="f415c-225">Host05</span><span class="sxs-lookup"><span data-stu-id="f415c-225">Host05</span></span>

<span data-ttu-id="f415c-226">Mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console.</span><span class="sxs-lookup"><span data-stu-id="f415c-226">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="f415c-227">Este aplicativo de host também oferece suporte a chamadas para computadores remotos utilizando o [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) e [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets.</span><span class="sxs-lookup"><span data-stu-id="f415c-227">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets.</span></span>

### <a name="host06"></a><span data-ttu-id="f415c-228">Host06</span><span class="sxs-lookup"><span data-stu-id="f415c-228">Host06</span></span>

<span data-ttu-id="f415c-229">Mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console.</span><span class="sxs-lookup"><span data-stu-id="f415c-229">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="f415c-230">Além disso, este exemplo utiliza as APIs de atomizador para especificar a cor do texto que é introduzido pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="f415c-230">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="provider-samples"></a><span data-ttu-id="f415c-231">Exemplos de fornecedor</span><span class="sxs-lookup"><span data-stu-id="f415c-231">Provider samples</span></span>

### <a name="accessdbprovidersample01"></a><span data-ttu-id="f415c-232">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="f415c-232">AccessDBProviderSample01</span></span>

<span data-ttu-id="f415c-233">Mostra como declarar uma classe de provedor que deriva diretamente a partir da [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) classe.</span><span class="sxs-lookup"><span data-stu-id="f415c-233">Shows how to declare a provider class that derives directly from the [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) class.</span></span>
<span data-ttu-id="f415c-234">Ele é incluído aqui apenas para fornecer uma visão completa.</span><span class="sxs-lookup"><span data-stu-id="f415c-234">It is included here only for completeness.</span></span>

### <a name="accessdbprovidersample02"></a><span data-ttu-id="f415c-235">AccessDBProviderSample02</span><span class="sxs-lookup"><span data-stu-id="f415c-235">AccessDBProviderSample02</span></span>

<span data-ttu-id="f415c-236">Mostra como substituir a [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) e [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) métodos para oferecer suporte a chamadas para o `New-PSDrive` e `Remove-PSDrive` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="f415c-236">Shows how to overwrite the [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) and [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) methods to support calls to the `New-PSDrive` and `Remove-PSDrive` cmdlets.</span></span>
<span data-ttu-id="f415c-237">A classe de fornecedor neste exemplo deriva do [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) classe.</span><span class="sxs-lookup"><span data-stu-id="f415c-237">The provider class in this sample derives from the [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) class.</span></span>

### <a name="accessdbprovidersample03"></a><span data-ttu-id="f415c-238">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="f415c-238">AccessDBProviderSample03</span></span>

<span data-ttu-id="f415c-239">Mostra como substituir a [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) e [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) métodos para oferecer suporte a chamadas para o `Get-Item` e `Set-Item` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="f415c-239">Shows how to overwrite the [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) and [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span>
<span data-ttu-id="f415c-240">A classe de fornecedor neste exemplo deriva do [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) classe.</span><span class="sxs-lookup"><span data-stu-id="f415c-240">The provider class in this sample derives from the [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample04"></a><span data-ttu-id="f415c-241">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="f415c-241">AccessDBProviderSample04</span></span>

<span data-ttu-id="f415c-242">Mostra como substituir os métodos de contentor para oferecer suporte a chamadas para o `Copy-Item`, `Get-ChildItem`, `New-Item`, e `Remove-Item` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="f415c-242">Shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span>
<span data-ttu-id="f415c-243">Esses métodos devem ser implementados quando o arquivo de dados contém itens que são contentores.</span><span class="sxs-lookup"><span data-stu-id="f415c-243">These methods should be implemented when the data store contains items that are containers.</span></span>
<span data-ttu-id="f415c-244">Um contentor é um grupo de itens filho num item principal comum.</span><span class="sxs-lookup"><span data-stu-id="f415c-244">A container is a group of child items under a common parent item.</span></span>
<span data-ttu-id="f415c-245">A classe de fornecedor neste exemplo deriva do [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) classe.</span><span class="sxs-lookup"><span data-stu-id="f415c-245">The provider class in this sample derives from the [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample05"></a><span data-ttu-id="f415c-246">AccessDBProviderSample05</span><span class="sxs-lookup"><span data-stu-id="f415c-246">AccessDBProviderSample05</span></span>

<span data-ttu-id="f415c-247">Mostra como substituir os métodos de contentor para oferecer suporte a chamadas para o `Move-Item` e `Join-Path` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="f415c-247">Shows how to overwrite container methods to support calls to the `Move-Item` and `Join-Path` cmdlets.</span></span>
<span data-ttu-id="f415c-248">Esses métodos devem ser implementados quando o utilizador tem de mover itens dentro de um contêiner e se o arquivo de dados contém contêineres aninhados.</span><span class="sxs-lookup"><span data-stu-id="f415c-248">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span>
<span data-ttu-id="f415c-249">A classe de fornecedor neste exemplo deriva do [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) classe.</span><span class="sxs-lookup"><span data-stu-id="f415c-249">The provider class in this sample derives from the [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample06"></a><span data-ttu-id="f415c-250">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="f415c-250">AccessDBProviderSample06</span></span>

<span data-ttu-id="f415c-251">Mostra como substituir os métodos de conteúdo para oferecer suporte a chamadas para o `Clear-Content`, `Get-Content`, e `Set-Content` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="f415c-251">Shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span>
<span data-ttu-id="f415c-252">Esses métodos devem ser implementados quando os utilizadores necessitam gerir o conteúdo dos itens no arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="f415c-252">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span>
<span data-ttu-id="f415c-253">A classe de fornecedor neste exemplo deriva do [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) classe e ele implementa a [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interface.</span><span class="sxs-lookup"><span data-stu-id="f415c-253">The provider class in this sample derives from the [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) class, and it implements the [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interface.</span></span>