---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Instalar o SKD do Windows PowerShell
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: 830b054c2cf2b49d935d3d96b79effa7131f6db2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953570"
---
# <a name="installing-the-windows-powershell-sdk"></a><span data-ttu-id="dbec5-103">Instalar o SKD do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dbec5-103">Installing the Windows PowerShell SDK</span></span>

<span data-ttu-id="dbec5-104">O tópico seguinte descreve como instalar o SDK do PowerShell em diferentes versões do Windows.</span><span class="sxs-lookup"><span data-stu-id="dbec5-104">The following topic describes how to install the PowerShell SDK on different versions of Windows.</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a><span data-ttu-id="dbec5-105">Instalar o Windows PowerShell 3.0 SDK para Windows 8 e Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="dbec5-105">Installing Windows PowerShell 3.0 SDK for Windows 8 and Windows Server 2012</span></span>

<span data-ttu-id="dbec5-106">Windows PowerShell 3.0 é instalado automaticamente com o Windows 8 e Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="dbec5-106">Windows PowerShell 3.0 is automatically installed with Windows 8 and Windows Server 2012.</span></span>
<span data-ttu-id="dbec5-107">Além disso, pode transferir e instalar as assemblagens de referência para o Windows PowerShell 3.0 como parte do Windows 8 SDK.</span><span class="sxs-lookup"><span data-stu-id="dbec5-107">In addition, you can download and install the reference assemblies for Windows PowerShell 3.0 as part of the Windows 8 SDK.</span></span>
<span data-ttu-id="dbec5-108">Estas assemblagens permitem-lhe escrever cmdlets, fornecedores e programas de anfitrião para o Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="dbec5-108">These assemblies allow you to write cmdlets, providers, and host programs for Windows PowerShell 3.0.</span></span>
<span data-ttu-id="dbec5-109">Quando instalar o Windows SDK para Windows 8, as assemblagens do Windows PowerShell são instaladas automaticamente na pasta de assemblagem de referência, no \Programas ficheiros (x86) \Reference Assemblies\Microsoft\WindowsPowerShell\3.0.</span><span class="sxs-lookup"><span data-stu-id="dbec5-109">When you install the Windows SDK for Windows 8, the Windows PowerShell assemblies are automatically installed in the reference assembly folder, in \Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0.</span></span>
<span data-ttu-id="dbec5-110">Para obter mais informações, consulte o [site de transferência do SDK do Windows 8](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).</span><span class="sxs-lookup"><span data-stu-id="dbec5-110">For more information, see the [Windows 8 SDK download site](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).</span></span>
<span data-ttu-id="dbec5-111">Exemplos de código do Windows PowerShell também estão disponíveis no Centro de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="dbec5-111">Windows PowerShell code samples are also available on the Development Center.</span></span>
<span data-ttu-id="dbec5-112">Para obter mais informações, consulte a página de códigos de ambiente de trabalho de exemplo no [site do Dev center](http://code.msdn.microsoft.com/windowsdesktop/).</span><span class="sxs-lookup"><span data-stu-id="dbec5-112">For more information, see the Desktop code sample page on the [Dev center site](http://code.msdn.microsoft.com/windowsdesktop/).</span></span>

<span data-ttu-id="dbec5-113">Além disso, o Windows PowerShell 3.0 é efeitos compatível com o Windows PowerShell 2.0 SDK, que inclui um número de amostras de código.</span><span class="sxs-lookup"><span data-stu-id="dbec5-113">In addition, Windows PowerShell 3.0 is backwards-compatible with the Windows PowerShell 2.0 SDK, which includes a number of code samples.</span></span>
<span data-ttu-id="dbec5-114">Para obter mais informações sobre como transferir o SDK do Windows PowerShell 2.0, consulte abaixo.</span><span class="sxs-lookup"><span data-stu-id="dbec5-114">For more information on how to download the Windows PowerShell 2.0 SDK, see below.</span></span>
<span data-ttu-id="dbec5-115">(Tenha em atenção que enquanto os exemplos de 2.0 código são compatíveis com Windows 8 e Windows PowerShell 3.0, não é possível instalar o Windows PowerShell 2.0 numa plataforma Windows 8.)</span><span class="sxs-lookup"><span data-stu-id="dbec5-115">(Note that while the 2.0 code samples are compatible with Windows 8 and Windows PowerShell 3.0, you cannot install Windows PowerShell 2.0 on a Windows 8 platform.)</span></span>

##<a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a><span data-ttu-id="dbec5-116">Instalar o Windows PowerShell 3.0 SDK para Windows 7 e Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="dbec5-116">Installing Windows PowerShell 3.0 SDK for Windows 7 and Windows Server 2008 R2</span></span>

<span data-ttu-id="dbec5-117">Windows 7 e Windows Server 2008 R2 automaticamente a ter o PowerShell 2.0 instalados.</span><span class="sxs-lookup"><span data-stu-id="dbec5-117">Windows 7 and Windows Server 2008 R2 automatically have PowerShell 2.0 installed.</span></span>
<span data-ttu-id="dbec5-118">Além disso, pode instalar o PowerShell 3.0 nestes sistemas.</span><span class="sxs-lookup"><span data-stu-id="dbec5-118">In addition, you can install PowerShell 3.0 on these systems.</span></span>
<span data-ttu-id="dbec5-119">(Para obter mais informações, consulte [instalar o Windows PowerShell](Installing-Windows-PowerShell.md).).</span><span class="sxs-lookup"><span data-stu-id="dbec5-119">(For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).).</span></span>
<span data-ttu-id="dbec5-120">Como descrito acima, também pode instalar o SDK do Windows 8 no Windows 7 e Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="dbec5-120">As described above, you can also install the Windows 8 SDK on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a><span data-ttu-id="dbec5-121">Instalar o Windows PowerShell 2.0 SDK para Windows 7, Vista, XP, Server 2003 e Server 2008</span><span class="sxs-lookup"><span data-stu-id="dbec5-121">Installing Windows PowerShell 2.0 SDK for Windows 7, Vista, XP, Server 2003, and Server 2008</span></span>

<span data-ttu-id="dbec5-122">O SDK do Windows PowerShell 2.0 fornece as assemblagens de referência necessárias para escrever cmdlets, fornecedores e alojamento de aplicações e fornece c# código de exemplo que pode ser utilizado como ponto de partida, quando começar a escrever código.</span><span class="sxs-lookup"><span data-stu-id="dbec5-122">The Windows PowerShell 2.0 SDK provides the reference assemblies needed to write cmdlets, providers, and hosting applications, and it provides C# sample code that can be used as the starting point when you begin writing code.</span></span>

<span data-ttu-id="dbec5-123">Para instalar este SDK, consulte [SDK do Windows PowerShell 2.0](http://go.microsoft.com/fwlink/?LinkId=184611).</span><span class="sxs-lookup"><span data-stu-id="dbec5-123">To install this SDK, see [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611).</span></span>

## <a name="reference-assemblies"></a><span data-ttu-id="dbec5-124">Assemblagens de referência</span><span class="sxs-lookup"><span data-stu-id="dbec5-124">Reference assemblies</span></span>

<span data-ttu-id="dbec5-125">As assemblagens de referência são instaladas na seguinte localização por predefinição: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span><span class="sxs-lookup"><span data-stu-id="dbec5-125">Reference assemblies are installed in the following location by default: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span></span>

> <span data-ttu-id="dbec5-126">**Tenha em atenção**: não é possível carregar o código que é compilado contra as assemblagens do Windows PowerShell 2.0 em instalações do Windows PowerShell 1.0.</span><span class="sxs-lookup"><span data-stu-id="dbec5-126">**Note**: Code that is compiled against the Windows PowerShell 2.0 assemblies cannot be loaded into Windows PowerShell 1.0 installations.</span></span>
><span data-ttu-id="dbec5-127">No entanto, o código que é compilado contra as assemblagens do Windows PowerShell 1.0 pode ser carregado para instalações do Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="dbec5-127">However, code that is compiled against the Windows PowerShell 1.0 assemblies can be loaded into Windows PowerShell 2.0 installations.</span></span>

## <a name="samples"></a><span data-ttu-id="dbec5-128">Amostras</span><span class="sxs-lookup"><span data-stu-id="dbec5-128">Samples</span></span>

<span data-ttu-id="dbec5-129">Exemplos de código são instalados na seguinte localização por predefinição: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="dbec5-129">Code samples are installed in the following location by default: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span></span>

<span data-ttu-id="dbec5-130">As secções seguintes fornecem uma breve descrição do que faz cada amostra.</span><span class="sxs-lookup"><span data-stu-id="dbec5-130">The following sections provide a brief description of what each sample does.</span></span>

## <a name="cmdlet-samples"></a><span data-ttu-id="dbec5-131">Exemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="dbec5-131">Cmdlet samples</span></span>
<span data-ttu-id="dbec5-132">**GetProcessSample01**</span><span class="sxs-lookup"><span data-stu-id="dbec5-132">**GetProcessSample01**</span></span>

<span data-ttu-id="dbec5-133">Demonstra como escrever um simple cmdlet que obtém todos os processos no computador local.</span><span class="sxs-lookup"><span data-stu-id="dbec5-133">Shows how to write a simple cmdlet that gets all the processes on the local computer.</span></span>

<span data-ttu-id="dbec5-134">**GetProcessSample02**</span><span class="sxs-lookup"><span data-stu-id="dbec5-134">**GetProcessSample02**</span></span>

<span data-ttu-id="dbec5-135">Mostra como adicionar parâmetros ao cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dbec5-135">Shows how to add parameters to the cmdlet.</span></span>
<span data-ttu-id="dbec5-136">O cmdlet assume um ou mais nomes de processo e devolve os processos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="dbec5-136">The cmdlet takes one or more process names and returns the matching processes.</span></span>

<span data-ttu-id="dbec5-137">**GetProcessSample03**</span><span class="sxs-lookup"><span data-stu-id="dbec5-137">**GetProcessSample03**</span></span>

<span data-ttu-id="dbec5-138">Mostra como adicionar parâmetros que aceitam entrada a partir do pipeline.</span><span class="sxs-lookup"><span data-stu-id="dbec5-138">Shows how to add parameters that accept input from the pipeline.</span></span>

<span data-ttu-id="dbec5-139">**GetProcessSample04**</span><span class="sxs-lookup"><span data-stu-id="dbec5-139">**GetProcessSample04**</span></span>

<span data-ttu-id="dbec5-140">Mostra como processar erros nonterminating.</span><span class="sxs-lookup"><span data-stu-id="dbec5-140">Shows how to handle nonterminating errors.</span></span>

<span data-ttu-id="dbec5-141">**GetProcessSample05**</span><span class="sxs-lookup"><span data-stu-id="dbec5-141">**GetProcessSample05**</span></span>

<span data-ttu-id="dbec5-142">Mostra como apresentar uma lista de processos especificados.</span><span class="sxs-lookup"><span data-stu-id="dbec5-142">Shows how to display a list of specified processes.</span></span>

<span data-ttu-id="dbec5-143">**SelectObject**</span><span class="sxs-lookup"><span data-stu-id="dbec5-143">**SelectObject**</span></span>

<span data-ttu-id="dbec5-144">Demonstra como escrever um filtro para selecionar apenas a determinados objetos.</span><span class="sxs-lookup"><span data-stu-id="dbec5-144">Shows how to write a filter to select only certain objects.</span></span>

<span data-ttu-id="dbec5-145">**SelectString**</span><span class="sxs-lookup"><span data-stu-id="dbec5-145">**SelectString**</span></span>

<span data-ttu-id="dbec5-146">Mostra como procurar ficheiros de padrões especificados.</span><span class="sxs-lookup"><span data-stu-id="dbec5-146">Shows how to search files for specified patterns.</span></span>

<span data-ttu-id="dbec5-147">**StopProcessSample01**</span><span class="sxs-lookup"><span data-stu-id="dbec5-147">**StopProcessSample01**</span></span>

<span data-ttu-id="dbec5-148">Mostra como implementar um *PassThru* parâmetro e como pedir comentários dos utilizadores por chamadas para o [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) e [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx) métodos.</span><span class="sxs-lookup"><span data-stu-id="dbec5-148">Shows how to implement a *PassThru* parameter, and how to request user feedback by calls to the [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) and [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx) methods.</span></span>
<span data-ttu-id="dbec5-149">Os utilizadores especificarem o *PassThru* parâmetro quando pretendem forçar o cmdlet para devolver um objeto</span><span class="sxs-lookup"><span data-stu-id="dbec5-149">Users specify the *PassThru* parameter when they want to force the cmdlet to return an object,</span></span>

<span data-ttu-id="dbec5-150">**StopProcessSample02**</span><span class="sxs-lookup"><span data-stu-id="dbec5-150">**StopProcessSample02**</span></span>

<span data-ttu-id="dbec5-151">Mostra como parar um processo específico.</span><span class="sxs-lookup"><span data-stu-id="dbec5-151">Shows how to stop a specific process.</span></span>

<span data-ttu-id="dbec5-152">**StopProcessSample03**</span><span class="sxs-lookup"><span data-stu-id="dbec5-152">**StopProcessSample03**</span></span>

<span data-ttu-id="dbec5-153">Mostra como declarar aliases para os parâmetros e como suporta carateres universais.</span><span class="sxs-lookup"><span data-stu-id="dbec5-153">Shows how to declare aliases for parameters and how to support wildcards.</span></span>

<span data-ttu-id="dbec5-154">**StopProcessSample04**</span><span class="sxs-lookup"><span data-stu-id="dbec5-154">**StopProcessSample04**</span></span>

<span data-ttu-id="dbec5-155">Mostra como declarar os conjuntos de parâmetros, o objeto que o cmdlet aceita como entrada e de como especificar o parâmetro predefinido configurado para utilizar.</span><span class="sxs-lookup"><span data-stu-id="dbec5-155">Shows how to declare parameter sets, the object that the cmdlet takes as input, and how to specify the default parameter set to use.</span></span>

## <a name="remoting-samples"></a><span data-ttu-id="dbec5-156">Exemplos de gestão remota</span><span class="sxs-lookup"><span data-stu-id="dbec5-156">Remoting samples</span></span>

<span data-ttu-id="dbec5-157">**RemoteRunspace01**</span><span class="sxs-lookup"><span data-stu-id="dbec5-157">**RemoteRunspace01**</span></span>

<span data-ttu-id="dbec5-158">Mostra como criar um espaço de execução remoto que é utilizado para estabelecer uma ligação remota.</span><span class="sxs-lookup"><span data-stu-id="dbec5-158">Shows how to create a remote runspace that is used to establish a remote connection.</span></span>

<span data-ttu-id="dbec5-159">**RemoteRunspacePool01**</span><span class="sxs-lookup"><span data-stu-id="dbec5-159">**RemoteRunspacePool01**</span></span>

<span data-ttu-id="dbec5-160">Mostra como construir um conjunto de espaço de execução remoto e como executar vários comandos em simultâneo utilizando este conjunto.</span><span class="sxs-lookup"><span data-stu-id="dbec5-160">Shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

<span data-ttu-id="dbec5-161">**Serialization01**</span><span class="sxs-lookup"><span data-stu-id="dbec5-161">**Serialization01**</span></span>

<span data-ttu-id="dbec5-162">Mostra como observar uma classe .NET existente e certifique-se de que as informações a partir das propriedades públicas selecionadas desta classe são preservadas em serialização/desserialização.</span><span class="sxs-lookup"><span data-stu-id="dbec5-162">Shows how to look at an existing .NET class and make sure that information from selected public properties of this class is preserved across serialization/deserialization.</span></span>

<span data-ttu-id="dbec5-163">**Serialization02**</span><span class="sxs-lookup"><span data-stu-id="dbec5-163">**Serialization02**</span></span>

<span data-ttu-id="dbec5-164">Mostra como observar uma classe .NET existente e certifique-se de que as informações de instância desta classe são preservadas na serialização/desserialização quando as informações não estão disponíveis nas propriedades públicas da classe.</span><span class="sxs-lookup"><span data-stu-id="dbec5-164">Shows how to look at an existing .NET class and make sure that information from instance of this class is preserved across serialization/deserialization when the information is not available in public properties of the class.</span></span>

<span data-ttu-id="dbec5-165">**Serialization03**</span><span class="sxs-lookup"><span data-stu-id="dbec5-165">**Serialization03**</span></span>

<span data-ttu-id="dbec5-166">Mostra como observar uma classe .NET existente e certifique-se de que as instâncias desta classe e classes derivadas são anular a serialização (rehydrated) em objetos de .NET em direto.</span><span class="sxs-lookup"><span data-stu-id="dbec5-166">Shows how to look at an existing .NET class and make sure that instances of this class and of derived classes are deserialized (rehydrated) into live .NET objects.</span></span>

## <a name="event-samples"></a><span data-ttu-id="dbec5-167">Exemplos de eventos</span><span class="sxs-lookup"><span data-stu-id="dbec5-167">Event samples</span></span>

<span data-ttu-id="dbec5-168">**Event01**</span><span class="sxs-lookup"><span data-stu-id="dbec5-168">**Event01**</span></span>

<span data-ttu-id="dbec5-169">Mostra como criar um cmdlet para o registo de eventos ao efetuar a derivação de ObjectEventRegistrationBase.</span><span class="sxs-lookup"><span data-stu-id="dbec5-169">Shows how to create a cmdlet for event registration by deriving from ObjectEventRegistrationBase.</span></span>

<span data-ttu-id="dbec5-170">**Event02**</span><span class="sxs-lookup"><span data-stu-id="dbec5-170">**Event02**</span></span>

<span data-ttu-id="dbec5-171">Mostra como a mostra como receber notificações de eventos do Windows PowerShell que são gerados em computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="dbec5-171">Shows how to shows how to receive notifications of Windows PowerShell events that are generated on remote computers.</span></span>
<span data-ttu-id="dbec5-172">Utiliza o evento de PSEventReceived exposto através de [espaço de execução](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx) classe.</span><span class="sxs-lookup"><span data-stu-id="dbec5-172">It uses the PSEventReceived event exposed through the [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx) class.</span></span>

## <a name="hosting-application-samples"></a><span data-ttu-id="dbec5-173">Exemplos de aplicações de alojamento</span><span class="sxs-lookup"><span data-stu-id="dbec5-173">Hosting application samples</span></span>

<span data-ttu-id="dbec5-174">**Runspace01**</span><span class="sxs-lookup"><span data-stu-id="dbec5-174">**Runspace01**</span></span>

<span data-ttu-id="dbec5-175">Mostra como utilizar o [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) classe para executar o [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="dbec5-175">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet synchronously.</span></span>
<span data-ttu-id="dbec5-176">O [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet devolve [processo](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objetos para cada processo em execução no computador local.</span><span class="sxs-lookup"><span data-stu-id="dbec5-176">The [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer.</span></span>

<span data-ttu-id="dbec5-177">**Runspace02**</span><span class="sxs-lookup"><span data-stu-id="dbec5-177">**Runspace02**</span></span>

<span data-ttu-id="dbec5-178">Mostra como utilizar o [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) classe para executar o [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) e [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) cmdlets de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="dbec5-178">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) and [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) cmdlets synchronously.</span></span>
<span data-ttu-id="dbec5-179">O [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet devolve [processo](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objetos para cada processam em execução no computador local e o objeto de ordenação ordena os objetos com base no respetivo [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) propriedade.</span><span class="sxs-lookup"><span data-stu-id="dbec5-179">The [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer, and the Sort-Object sorts the objects based on their [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) property.</span></span>
<span data-ttu-id="dbec5-180">Os resultados destes comandos são apresentadas utilizando um [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) controlo.</span><span class="sxs-lookup"><span data-stu-id="dbec5-180">The results of these commands is displayed by using a [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) control.</span></span>

<span data-ttu-id="dbec5-181">**Runspace03**</span><span class="sxs-lookup"><span data-stu-id="dbec5-181">**Runspace03**</span></span>

<span data-ttu-id="dbec5-182">Mostra como utilizar o [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) classe para executar um script de forma síncrona e como processar erros não terminar.</span><span class="sxs-lookup"><span data-stu-id="dbec5-182">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run a script synchronously, and how to handle non-terminating errors.</span></span>
<span data-ttu-id="dbec5-183">O script recebe uma lista de nomes de processo e, em seguida, obtém desses processos.</span><span class="sxs-lookup"><span data-stu-id="dbec5-183">The script receives a list of process names and then retrieves those processes.</span></span>
<span data-ttu-id="dbec5-184">Os resultados do script, incluindo quaisquer erros de não interrupção de mensagens em fila que foram gerados ao executar o script, são apresentados numa janela de consola.</span><span class="sxs-lookup"><span data-stu-id="dbec5-184">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

<span data-ttu-id="dbec5-185">**Runspace04**</span><span class="sxs-lookup"><span data-stu-id="dbec5-185">**Runspace04**</span></span>

<span data-ttu-id="dbec5-186">Mostra como utilizar o [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) classe para executar comandos e como erros de terminação de catch que são emitida ao executar os comandos.</span><span class="sxs-lookup"><span data-stu-id="dbec5-186">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span>
<span data-ttu-id="dbec5-187">Dois comandos são executados e o último comando é passado um argumento de parâmetro que não é válido.</span><span class="sxs-lookup"><span data-stu-id="dbec5-187">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span>
<span data-ttu-id="dbec5-188">Como resultado, não existem objetos são devolvidos e um erro de terminação é emitido.</span><span class="sxs-lookup"><span data-stu-id="dbec5-188">As a result, no objects are returned and a terminating error is thrown.</span></span>

<span data-ttu-id="dbec5-189">**Runspace05**</span><span class="sxs-lookup"><span data-stu-id="dbec5-189">**Runspace05**</span></span>

<span data-ttu-id="dbec5-190">Mostra como adicionar um snap-in para um [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) objeto para que o cmdlet do snap-in está disponível quando o espaço de execução é aberto.</span><span class="sxs-lookup"><span data-stu-id="dbec5-190">Shows how to add a snap-in to an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span>
<span data-ttu-id="dbec5-191">O snap-in fornece um cmdlet Get-Process (definido pelo [GetProcessSample01 exemplo](https://technet.microsoft.com/library/ff602028.aspx)) que é executado de forma síncrona utilizando um [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) objeto.</span><span class="sxs-lookup"><span data-stu-id="dbec5-191">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](https://technet.microsoft.com/library/ff602028.aspx)) that is run synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="dbec5-192">**Runspace06**</span><span class="sxs-lookup"><span data-stu-id="dbec5-192">**Runspace06**</span></span>

<span data-ttu-id="dbec5-193">Mostra como adicionar um módulo para um [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) objeto para que o módulo é carregado quando o espaço de execução é aberto.</span><span class="sxs-lookup"><span data-stu-id="dbec5-193">Shows how to add a module to an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object so that the module is loaded when the runspace is opened.</span></span>
<span data-ttu-id="dbec5-194">O módulo fornece um cmdlet Get-Process (definido pelo [GetProcessSample02 exemplo](https://technet.microsoft.com/library/ff602027.aspx)) que é executado de forma síncrona utilizando um [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) objeto.</span><span class="sxs-lookup"><span data-stu-id="dbec5-194">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](https://technet.microsoft.com/library/ff602027.aspx)) that is run synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="dbec5-195">**Runspace07**</span><span class="sxs-lookup"><span data-stu-id="dbec5-195">**Runspace07**</span></span>

<span data-ttu-id="dbec5-196">Mostra como criar um espaço de execução e, em seguida, utilizar esse espaço de execução para executar dois cmdlets de forma síncrona utilizando um [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) objeto.</span><span class="sxs-lookup"><span data-stu-id="dbec5-196">Shows how to create a runspace, and then use that runspace to run two cmdlets synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="dbec5-197">**Runspace08**</span><span class="sxs-lookup"><span data-stu-id="dbec5-197">**Runspace08**</span></span>

<span data-ttu-id="dbec5-198">Mostra como adicionar comandos e argumentos para o pipeline de um [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) objeto e como executar os comandos de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="dbec5-198">Shows how to add commands and arguments to the pipeline of a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object and how to run the commands synchronously.</span></span>

<span data-ttu-id="dbec5-199">**Runspace09**</span><span class="sxs-lookup"><span data-stu-id="dbec5-199">**Runspace09**</span></span>

<span data-ttu-id="dbec5-200">Mostra como adicionar um script para o pipeline de um [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) objeto e como executar o script de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="dbec5-200">Shows how to add a script to the pipeline of a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object and how to run the script asynchronously.</span></span>
<span data-ttu-id="dbec5-201">Os eventos são utilizados para processar o resultado do script.</span><span class="sxs-lookup"><span data-stu-id="dbec5-201">Events are used to handle the output of the script.</span></span>

<span data-ttu-id="dbec5-202">**Runspace10**</span><span class="sxs-lookup"><span data-stu-id="dbec5-202">**Runspace10**</span></span>

<span data-ttu-id="dbec5-203">Mostra como criar um Estado de sessão inicial predefinido, como adicionar um cmdlet para o [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), como criar um espaço de execução que utiliza o estado da sessão inicial e como executar o comando utilizando um [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx)objeto.</span><span class="sxs-lookup"><span data-stu-id="dbec5-203">Shows how to create a default initial session state, how to add a cmdlet to the [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), how to create a runspace that uses the initial session state, and how to run the command by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="dbec5-204">**Runspace11**</span><span class="sxs-lookup"><span data-stu-id="dbec5-204">**Runspace11**</span></span>

<span data-ttu-id="dbec5-205">Mostra como utilizar o [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) classe para criar um comando de proxy que chama um cmdlet existente, mas que restringe o conjunto de parâmetros disponíveis.</span><span class="sxs-lookup"><span data-stu-id="dbec5-205">Shows how to use the [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span>
<span data-ttu-id="dbec5-206">O comando de proxy, em seguida, é adicionado a um Estado de sessão inicial que é utilizado para criar um espaço de execução restrita.</span><span class="sxs-lookup"><span data-stu-id="dbec5-206">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span>
<span data-ttu-id="dbec5-207">Isto significa que o utilizador pode aceder a funcionalidade do cmdlet apenas através do comando de proxy.</span><span class="sxs-lookup"><span data-stu-id="dbec5-207">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

<span data-ttu-id="dbec5-208">**PowerShell01**</span><span class="sxs-lookup"><span data-stu-id="dbec5-208">**PowerShell01**</span></span>

<span data-ttu-id="dbec5-209">Mostra como criar um espaço de execução restrita, utilizando um [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) objeto.</span><span class="sxs-lookup"><span data-stu-id="dbec5-209">Shows how to create a constrained runspace using an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object.</span></span>

<span data-ttu-id="dbec5-210">**PowerShell02**</span><span class="sxs-lookup"><span data-stu-id="dbec5-210">**PowerShell02**</span></span>

<span data-ttu-id="dbec5-211">Mostra como utilizar um conjunto de espaço de execução para executar vários comandos em simultâneo.</span><span class="sxs-lookup"><span data-stu-id="dbec5-211">Shows how to use a runspace pool to run multiple commands concurrently.</span></span>

## <a name="host-samples"></a><span data-ttu-id="dbec5-212">Exemplos de anfitrião</span><span class="sxs-lookup"><span data-stu-id="dbec5-212">Host samples</span></span>

<span data-ttu-id="dbec5-213">**Host01**</span><span class="sxs-lookup"><span data-stu-id="dbec5-213">**Host01**</span></span>

<span data-ttu-id="dbec5-214">Mostra como implementar uma aplicação de anfitrião que utiliza um anfitrião personalizado.</span><span class="sxs-lookup"><span data-stu-id="dbec5-214">Shows how to implement a host application that uses a custom host.</span></span>
<span data-ttu-id="dbec5-215">Neste exemplo é criado um espaço de execução que utiliza o anfitrião personalizado, e, em seguida, o [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) API é utilizada para executar um script que chama "Sair".</span><span class="sxs-lookup"><span data-stu-id="dbec5-215">In this sample a runspace is created that uses the custom host, and then the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) API is used to run a script that calls "exit".</span></span>
<span data-ttu-id="dbec5-216">Em seguida, a aplicação anfitriã analisa o resultado do script e imprime os resultados.</span><span class="sxs-lookup"><span data-stu-id="dbec5-216">The host application then looks at the output of the script and prints out the results.</span></span>

<span data-ttu-id="dbec5-217">**Host02**</span><span class="sxs-lookup"><span data-stu-id="dbec5-217">**Host02**</span></span>

<span data-ttu-id="dbec5-218">Mostra como escrever uma aplicação de anfitrião que utiliza o tempo de execução do Windows PowerShell, juntamente com uma implementação do anfitrião personalizado.</span><span class="sxs-lookup"><span data-stu-id="dbec5-218">Shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span>
<span data-ttu-id="dbec5-219">A aplicação anfitriã define a cultura de anfitrião para alemão, executa a [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet e apresenta os resultados como seria vê-los utilizando pwrsh.exe e, em seguida, impressões saída de dados atuais e a hora em alemão.</span><span class="sxs-lookup"><span data-stu-id="dbec5-219">The host application sets the host culture to German, runs the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet and displays the results as you would see them by using pwrsh.exe, and then prints out the current data and time in German.</span></span>

<span data-ttu-id="dbec5-220">**Host03**</span><span class="sxs-lookup"><span data-stu-id="dbec5-220">**Host03**</span></span>

<span data-ttu-id="dbec5-221">Mostra como criar uma aplicação interativa anfitrião baseado em consola que lê os comandos na linha de comandos, executa os comandos e, em seguida, apresenta os resultados para a consola.</span><span class="sxs-lookup"><span data-stu-id="dbec5-221">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

<span data-ttu-id="dbec5-222">**Host04**</span><span class="sxs-lookup"><span data-stu-id="dbec5-222">**Host04**</span></span>

<span data-ttu-id="dbec5-223">Mostra como criar uma aplicação interativa anfitrião baseado em consola que lê os comandos na linha de comandos, executa os comandos e, em seguida, apresenta os resultados para a consola.</span><span class="sxs-lookup"><span data-stu-id="dbec5-223">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="dbec5-224">Esta aplicação anfitriã também suporta a apresentação de pedidos que permitem ao utilizador especificar múltiplas escolhas.</span><span class="sxs-lookup"><span data-stu-id="dbec5-224">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

<span data-ttu-id="dbec5-225">**Host05**</span><span class="sxs-lookup"><span data-stu-id="dbec5-225">**Host05**</span></span>

<span data-ttu-id="dbec5-226">Mostra como criar uma aplicação interativa anfitrião baseado em consola que lê os comandos na linha de comandos, executa os comandos e, em seguida, apresenta os resultados para a consola.</span><span class="sxs-lookup"><span data-stu-id="dbec5-226">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="dbec5-227">Esta aplicação de anfitrião que também suporta chamadas para computadores remotos utilizando o [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) e [sair-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212) cmdlets.</span><span class="sxs-lookup"><span data-stu-id="dbec5-227">This host application also supports calls to remote computers by using the [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) and [Exit-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212) cmdlets.</span></span>

<span data-ttu-id="dbec5-228">**Host06**</span><span class="sxs-lookup"><span data-stu-id="dbec5-228">**Host06**</span></span>

<span data-ttu-id="dbec5-229">Mostra como criar uma aplicação interativa anfitrião baseado em consola que lê os comandos na linha de comandos, executa os comandos e, em seguida, apresenta os resultados para a consola.</span><span class="sxs-lookup"><span data-stu-id="dbec5-229">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="dbec5-230">Além disso, este exemplo utiliza os APIs de atomizador para especificar a cor do texto que é introduzido pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="dbec5-230">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="provider-samples"></a><span data-ttu-id="dbec5-231">Exemplos de fornecedor</span><span class="sxs-lookup"><span data-stu-id="dbec5-231">Provider samples</span></span>

<span data-ttu-id="dbec5-232">**AccessDBProviderSample01**</span><span class="sxs-lookup"><span data-stu-id="dbec5-232">**AccessDBProviderSample01**</span></span>

<span data-ttu-id="dbec5-233">Mostra como declarar uma classe de fornecedor que deriva de diretamente o [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx) classe.</span><span class="sxs-lookup"><span data-stu-id="dbec5-233">Shows how to declare a provider class that derives directly from the [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx) class.</span></span>
<span data-ttu-id="dbec5-234">Está incluído aqui apenas por questões de exaustividade.</span><span class="sxs-lookup"><span data-stu-id="dbec5-234">It is included here only for completeness.</span></span>

<span data-ttu-id="dbec5-235">**AccessDBProviderSample02**</span><span class="sxs-lookup"><span data-stu-id="dbec5-235">**AccessDBProviderSample02**</span></span>

<span data-ttu-id="dbec5-236">Mostra como substituir o [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) e [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) métodos para suportar chamadas para os cmdlets New-PSDrive e Remove-PSDrive.</span><span class="sxs-lookup"><span data-stu-id="dbec5-236">Shows how to overwrite the [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) and [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) methods to support calls to the New-PSDrive and Remove-PSDrive cmdlets.</span></span>
<span data-ttu-id="dbec5-237">A classe de fornecedor neste exemplo deriva de [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx) classe.</span><span class="sxs-lookup"><span data-stu-id="dbec5-237">The provider class in this sample derives from the [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx) class.</span></span>

<span data-ttu-id="dbec5-238">**AccessDBProviderSample03**</span><span class="sxs-lookup"><span data-stu-id="dbec5-238">**AccessDBProviderSample03**</span></span>

<span data-ttu-id="dbec5-239">Mostra como substituir o [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) e [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) métodos para suportar chamadas para os cmdlets do Item de Get e Set-Item.</span><span class="sxs-lookup"><span data-stu-id="dbec5-239">Shows how to overwrite the [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) and [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) methods to support calls to the Get-Item and Set-Item cmdlets.</span></span>
<span data-ttu-id="dbec5-240">A classe de fornecedor neste exemplo deriva de [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) classe.</span><span class="sxs-lookup"><span data-stu-id="dbec5-240">The provider class in this sample derives from the [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="dbec5-241">**AccessDBProviderSample04**</span><span class="sxs-lookup"><span data-stu-id="dbec5-241">**AccessDBProviderSample04**</span></span>

<span data-ttu-id="dbec5-242">Mostra como substituir métodos de contentor para suportar chamadas para o Copy-Item, Get-ChildItem Novo Item e Remover Item cmdlets.</span><span class="sxs-lookup"><span data-stu-id="dbec5-242">Shows how to overwrite container methods to support calls to the Copy-Item, Get-ChildItem, New-Item, and Remove-Item cmdlets.</span></span>
<span data-ttu-id="dbec5-243">Estes métodos devem ser implementados quando o arquivo de dados contém itens que são contentores.</span><span class="sxs-lookup"><span data-stu-id="dbec5-243">These methods should be implemented when the data store contains items that are containers.</span></span>
<span data-ttu-id="dbec5-244">Um contentor é um grupo de itens subordinados sob um item principal comum.</span><span class="sxs-lookup"><span data-stu-id="dbec5-244">A container is a group of child items under a common parent item.</span></span>
<span data-ttu-id="dbec5-245">A classe de fornecedor neste exemplo deriva de [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) classe.</span><span class="sxs-lookup"><span data-stu-id="dbec5-245">The provider class in this sample derives from the [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="dbec5-246">**AccessDBProviderSample05**</span><span class="sxs-lookup"><span data-stu-id="dbec5-246">**AccessDBProviderSample05**</span></span>

<span data-ttu-id="dbec5-247">Mostra como substituir métodos de contentor para suportar chamadas para os cmdlets de mover Item e o caminho de associação.</span><span class="sxs-lookup"><span data-stu-id="dbec5-247">Shows how to overwrite container methods to support calls to the Move-Item and Join-Path cmdlets.</span></span>
<span data-ttu-id="dbec5-248">Estes métodos devem ser implementados quando o utilizador tem de mover itens dentro de um contentor e se o arquivo de dados contém contentores aninhadas.</span><span class="sxs-lookup"><span data-stu-id="dbec5-248">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span>
<span data-ttu-id="dbec5-249">A classe de fornecedor neste exemplo deriva de [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) classe.</span><span class="sxs-lookup"><span data-stu-id="dbec5-249">The provider class in this sample derives from the [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="dbec5-250">**AccessDBProviderSample06**</span><span class="sxs-lookup"><span data-stu-id="dbec5-250">**AccessDBProviderSample06**</span></span>

<span data-ttu-id="dbec5-251">Mostra como substituir métodos de conteúdo para suportar chamadas para o conteúdo encriptado, Get-conteúdo e conteúdo do conjunto de cmdlets.</span><span class="sxs-lookup"><span data-stu-id="dbec5-251">Shows how to overwrite content methods to support calls to the Clear-Content, Get-Content, and Set-Content cmdlets.</span></span>
<span data-ttu-id="dbec5-252">Estes métodos devem ser implementados quando o utilizador precisa de gerir o conteúdo dos itens no arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="dbec5-252">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span>
<span data-ttu-id="dbec5-253">A classe de fornecedor neste exemplo deriva de um a [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) classe e implementa o [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx) interface.</span><span class="sxs-lookup"><span data-stu-id="dbec5-253">The provider class in this sample derives from the [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) class, and it implements the [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx) interface.</span></span>