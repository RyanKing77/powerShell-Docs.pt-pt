---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Executar comandos remotos
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 5cf9690b8fe4549a99186f172cb6f0de156a4dea
ms.sourcegitcommit: c5251755c4442487f99ff74fadf7e37bbf039089
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/18/2017
---
# <a name="running-remote-commands"></a><span data-ttu-id="bec6b-103">Executar comandos remotos</span><span class="sxs-lookup"><span data-stu-id="bec6b-103">Running Remote Commands</span></span>
<span data-ttu-id="bec6b-104">Pode executar comandos num ou centenas de computadores com um único comando do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bec6b-104">You can run commands on one or hundreds of computers with a single Windows PowerShell command.</span></span> <span data-ttu-id="bec6b-105">O Windows PowerShell suporta informática remoto utilizando várias tecnologias, incluindo WMI, RPC e WS-Management.</span><span class="sxs-lookup"><span data-stu-id="bec6b-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

## <a name="remoting-without-configuration"></a><span data-ttu-id="bec6b-106">Comunicação remota sem configuração</span><span class="sxs-lookup"><span data-stu-id="bec6b-106">Remoting Without Configuration</span></span>
<span data-ttu-id="bec6b-107">Vários cmdlets do Windows PowerShell têm o parâmetro ComputerName que lhe permite recolher dados e alterar as definições num ou mais computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="bec6b-107">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="bec6b-108">Utilizam uma variedade de tecnologias de comunicação e de trabalho muitos em todos os sistemas operativos do Windows que suporta o Windows PowerShell sem qualquer configuração especial.</span><span class="sxs-lookup"><span data-stu-id="bec6b-108">They use a variety of communication technologies and many work on all Windows operating systems that Windows PowerShell supports without any special configuration.</span></span>

<span data-ttu-id="bec6b-109">Estes cmdlets incluem:</span><span class="sxs-lookup"><span data-stu-id="bec6b-109">These cmdlets include:</span></span>
* [<span data-ttu-id="bec6b-110">Reiniciar o computador</span><span class="sxs-lookup"><span data-stu-id="bec6b-110">Restart-Computer</span></span>](https://go.microsoft.com/fwlink/?LinkId=821625)
* [<span data-ttu-id="bec6b-111">Ligação de teste</span><span class="sxs-lookup"><span data-stu-id="bec6b-111">Test-Connection</span></span>](https://go.microsoft.com/fwlink/?LinkId=821646)
* [<span data-ttu-id="bec6b-112">Desmarque-registo de eventos</span><span class="sxs-lookup"><span data-stu-id="bec6b-112">Clear-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821568)
* [<span data-ttu-id="bec6b-113">Get-registo de eventos</span><span class="sxs-lookup"><span data-stu-id="bec6b-113">Get-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821585)
* [<span data-ttu-id="bec6b-114">Get-correção</span><span class="sxs-lookup"><span data-stu-id="bec6b-114">Get-HotFix</span></span>](https://go.microsoft.com/fwlink/?LinkId=821586)
  - [<span data-ttu-id="bec6b-115">Get-Process</span><span class="sxs-lookup"><span data-stu-id="bec6b-115">Get-Process</span></span>](https://go.microsoft.com/fwlink/?linkid=821590)
* [<span data-ttu-id="bec6b-116">Get-Service</span><span class="sxs-lookup"><span data-stu-id="bec6b-116">Get-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821593)
* [<span data-ttu-id="bec6b-117">Serviço de conjunto</span><span class="sxs-lookup"><span data-stu-id="bec6b-117">Set-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821633)
* [<span data-ttu-id="bec6b-118">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="bec6b-118">Get-WinEvent</span></span>](https://go.microsoft.com/fwlink/?linkid=821529)
* [<span data-ttu-id="bec6b-119">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="bec6b-119">Get-WmiObject</span></span>](https://go.microsoft.com/fwlink/?LinkId=821595)

<span data-ttu-id="bec6b-120">Normalmente, os cmdlets que suportam a gestão remota sem configuração especial ter o parâmetro ComputerName e é necessário o parâmetro de sessão.</span><span class="sxs-lookup"><span data-stu-id="bec6b-120">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and do not have the Session parameter.</span></span> <span data-ttu-id="bec6b-121">Para encontrar estes cmdlets na sua sessão, escreva:</span><span class="sxs-lookup"><span data-stu-id="bec6b-121">To find these cmdlets in your session, type:</span></span>

```
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="bec6b-122">Comunicação remota do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bec6b-122">Windows PowerShell Remoting</span></span>
<span data-ttu-id="bec6b-123">Comunicação remota do Windows PowerShell, que utiliza o protocolo WS-Management, permite-lhe executar qualquer comando do Windows PowerShell num ou vários computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="bec6b-123">Windows PowerShell remoting, which uses the WS-Management protocol, lets you run any Windows PowerShell command on one or many remote computers.</span></span> <span data-ttu-id="bec6b-124">Permite-lhe estabelecer ligações persistentes, iniciar sessões interativas 1:1 e executar scripts em vários computadores.</span><span class="sxs-lookup"><span data-stu-id="bec6b-124">It lets you establish persistent connections, start 1:1 interactive sessions, and run scripts on multiple computers.</span></span>

<span data-ttu-id="bec6b-125">Para utilizar a comunicação remota do Windows PowerShell, o computador remoto tem de ser configurado para a gestão remota.</span><span class="sxs-lookup"><span data-stu-id="bec6b-125">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span> <span data-ttu-id="bec6b-126">Para obter mais informações, incluindo instruções, consulte [sobre requisitos remoto](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span><span class="sxs-lookup"><span data-stu-id="bec6b-126">For more information, including instructions, see [About Remote Requirements](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span></span>

<span data-ttu-id="bec6b-127">Depois de ter configurado a comunicação remota do Windows PowerShell, muitos estratégias de gestão remota estão disponíveis para si.</span><span class="sxs-lookup"><span data-stu-id="bec6b-127">After you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span> <span data-ttu-id="bec6b-128">O resto deste documento apresenta alguns dos mesmos.</span><span class="sxs-lookup"><span data-stu-id="bec6b-128">The remainder of this document lists just a few of them.</span></span> <span data-ttu-id="bec6b-129">Para obter mais informações, consulte [sobre remoto](https://technet.microsoft.com/en-us/library/dd347744.aspx) e [sobre remoto FAQ](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span><span class="sxs-lookup"><span data-stu-id="bec6b-129">For more information, see [About Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx) and [About Remote FAQ](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="bec6b-130">Iniciar uma sessão interativa</span><span class="sxs-lookup"><span data-stu-id="bec6b-130">Start an Interactive Session</span></span>
<span data-ttu-id="bec6b-131">Para iniciar uma sessão interativa com um único computador remoto, utilize o [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bec6b-131">To start an interactive session with a single remote computer, use the [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet.</span></span>
<span data-ttu-id="bec6b-132">Por exemplo, para iniciar uma sessão interativa com o computador remoto servidor01, escreva:</span><span class="sxs-lookup"><span data-stu-id="bec6b-132">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```
Enter-PSSession Server01
```

<span data-ttu-id="bec6b-133">As alterações de linha de comandos para apresentar o nome do computador ao qual estão ligados.</span><span class="sxs-lookup"><span data-stu-id="bec6b-133">The command prompt changes to display the name of the computer to which you are connected.</span></span> <span data-ttu-id="bec6b-134">De ora em diante, execute os comandos que escreva na linha de no computador remoto e os resultados são apresentados no computador local.</span><span class="sxs-lookup"><span data-stu-id="bec6b-134">From then on, any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="bec6b-135">Para terminar a sessão interativa, escreva:</span><span class="sxs-lookup"><span data-stu-id="bec6b-135">To end the interactive session, type:</span></span>

```
Exit-PSSession
```

<span data-ttu-id="bec6b-136">Para obter mais informações sobre os cmdlets Enter-PSSession e de saída-PSSession, consulte [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) e [sair-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span><span class="sxs-lookup"><span data-stu-id="bec6b-136">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) and [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span></span>

### <a name="run-a-remote-command"></a><span data-ttu-id="bec6b-137">Executar um comando remoto</span><span class="sxs-lookup"><span data-stu-id="bec6b-137">Run a Remote Command</span></span>
<span data-ttu-id="bec6b-138">Para executar qualquer comando num ou vários computadores remotos, utilize o [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bec6b-138">To run any command on one or many remote computers, use the [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet.</span></span>
<span data-ttu-id="bec6b-139">Por exemplo, para executar um [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) comando nos servidor01 e Server02 computadores remotos, tipo:</span><span class="sxs-lookup"><span data-stu-id="bec6b-139">For example, to run a [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) command on the Server01 and Server02 remote computers, type:</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="bec6b-140">O resultado é devolvido para o seu computador.</span><span class="sxs-lookup"><span data-stu-id="bec6b-140">The output is returned to your computer.</span></span>

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```
<span data-ttu-id="bec6b-141">Para obter mais informações sobre o cmdlet Invoke-Command, consulte [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="bec6b-141">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="run-a-script"></a><span data-ttu-id="bec6b-142">Executar um Script</span><span class="sxs-lookup"><span data-stu-id="bec6b-142">Run a Script</span></span>
<span data-ttu-id="bec6b-143">Para executar um script num ou vários computadores remotos, utilize o parâmetro de FilePath do cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="bec6b-143">To run a script on one or many remote computers, use the FilePath parameter of the Invoke-Command cmdlet.</span></span> <span data-ttu-id="bec6b-144">O script deve ser igual ou acessível para o seu computador local.</span><span class="sxs-lookup"><span data-stu-id="bec6b-144">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="bec6b-145">Os resultados são devolvidos para o seu computador local.</span><span class="sxs-lookup"><span data-stu-id="bec6b-145">The results are returned to your local computer.</span></span>

<span data-ttu-id="bec6b-146">Por exemplo, o seguinte comando executa o script de DiskCollect.ps1 nos computadores remotos servidor01 e Server02.</span><span class="sxs-lookup"><span data-stu-id="bec6b-146">For example, the following command runs the DiskCollect.ps1 script on the Server01 and Server02 remote computers.</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

<span data-ttu-id="bec6b-147">Para obter mais informações sobre o cmdlet Invoke-Command, consulte [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="bec6b-147">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="bec6b-148">Estabelecer uma ligação persistente</span><span class="sxs-lookup"><span data-stu-id="bec6b-148">Establish a Persistent Connection</span></span>
<span data-ttu-id="bec6b-149">Para executar uma série de comandos relacionados que partilham dados, criar uma sessão no computador remoto e, em seguida, utilize o cmdlet Invoke-Command para executar comandos na sessão que criar.</span><span class="sxs-lookup"><span data-stu-id="bec6b-149">To run a series of related commands that share data, create a session on the remote computer and then use the Invoke-Command cmdlet to run commands in the session that you create.</span></span> <span data-ttu-id="bec6b-150">Para criar uma sessão remota, utilize o cmdlet New-PSSession.</span><span class="sxs-lookup"><span data-stu-id="bec6b-150">To create a remote session, use the New-PSSession cmdlet.</span></span>

<span data-ttu-id="bec6b-151">Por exemplo, o comando seguinte cria uma sessão remota no computador servidor01 e outra sessão remota no computador Server02.</span><span class="sxs-lookup"><span data-stu-id="bec6b-151">For example, the following command creates a remote session on the Server01 computer and another remote session on the Server02 computer.</span></span> <span data-ttu-id="bec6b-152">-Guarda os objetos de sessão na variável $s.</span><span class="sxs-lookup"><span data-stu-id="bec6b-152">It saves the session objects in the $s variable.</span></span>

```
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="bec6b-153">Agora que as sessões são estabelecidas, pode executar qualquer comando nos mesmos.</span><span class="sxs-lookup"><span data-stu-id="bec6b-153">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="bec6b-154">E visto que as sessões são persistentes, pode recolher dados de um comando utilizá-lo num comando subsequente.</span><span class="sxs-lookup"><span data-stu-id="bec6b-154">And because the sessions are persistent, you can collect data in one command and use it in a subsequent command.</span></span>

<span data-ttu-id="bec6b-155">Por exemplo, o comando seguinte executa um comando Get-correção em sessões na variável $s e este guarda os resultados na variável $h.</span><span class="sxs-lookup"><span data-stu-id="bec6b-155">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="bec6b-156">A variável de $h é criada em cada uma das sessões na $s, mas não existe na sessão local.</span><span class="sxs-lookup"><span data-stu-id="bec6b-156">The $h variable is created in each of the sessions in $s, but it does not exist in the local session.</span></span>

```
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="bec6b-157">Agora pode utilizar os dados na variável $h nos comandos subsequentes, tal como o seguinte.</span><span class="sxs-lookup"><span data-stu-id="bec6b-157">Now you can use the data in the $h variable in subsequent commands, such as the following one.</span></span> <span data-ttu-id="bec6b-158">Os resultados são apresentados no computador local.</span><span class="sxs-lookup"><span data-stu-id="bec6b-158">The results are displayed on the local computer.</span></span>

```
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="bec6b-159">Comunicação remota avançada</span><span class="sxs-lookup"><span data-stu-id="bec6b-159">Advanced Remoting</span></span>
<span data-ttu-id="bec6b-160">Gestão remota do Windows PowerShell começa imediatamente aqui.</span><span class="sxs-lookup"><span data-stu-id="bec6b-160">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="bec6b-161">Ao utilizar os cmdlets instalados com o Windows PowerShell, pode estabelecer e configurar remotas sessões de extremidades locais e remotas, criar sessões personalizadas e restritas, permitir que os utilizadores para importar os comandos de uma sessão remota que efetivamente executam implicitamente na sessão remota, configure a segurança de uma sessão remota e muito mais.</span><span class="sxs-lookup"><span data-stu-id="bec6b-161">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="bec6b-162">Para facilitar a configuração remota, o Windows PowerShell inclui um fornecedor de WSMan.</span><span class="sxs-lookup"><span data-stu-id="bec6b-162">To facilitate remote configuration, Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="bec6b-163">WSMAN: a unidade que o fornecedor cria permite-lhe navegar através de uma hierarquia de definições de configuração no computador local e computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="bec6b-163">The WSMAN: drive that the provider creates lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>
<span data-ttu-id="bec6b-164">Para obter mais informações sobre o fornecedor de WSMan, consulte [WSMan fornecedor](https://technet.microsoft.com/en-us/library/dd819476.aspx) e [sobre Cmdlets de WS-Management](https://technet.microsoft.com/en-us/library/dd819481.aspx), ou na consola do Windows PowerShell, escreva "Get-Help wsman".</span><span class="sxs-lookup"><span data-stu-id="bec6b-164">For more information about the WSMan provider, see  [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) and [About WS-Management Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx), or in the Windows PowerShell console, type "Get-Help wsman".</span></span>

<span data-ttu-id="bec6b-165">Para mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="bec6b-165">For more information, see:</span></span>
- [<span data-ttu-id="bec6b-166">Sobre FAQ remoto</span><span class="sxs-lookup"><span data-stu-id="bec6b-166">About Remote FAQ</span></span>](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [<span data-ttu-id="bec6b-167">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bec6b-167">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="bec6b-168">Importar-PSSession</span><span class="sxs-lookup"><span data-stu-id="bec6b-168">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="bec6b-169">Para obter ajuda com erros de sistema de interação remota, consulte [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="bec6b-169">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="bec6b-170">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="bec6b-170">See Also</span></span>
- [<span data-ttu-id="bec6b-171">about_Remote</span><span class="sxs-lookup"><span data-stu-id="bec6b-171">about_Remote</span></span>](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="bec6b-172">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="bec6b-172">about_Remote_FAQ</span></span>](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="bec6b-173">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="bec6b-173">about_Remote_Requirements</span></span>](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="bec6b-174">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="bec6b-174">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="bec6b-175">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="bec6b-175">about_PSSessions</span></span>](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="bec6b-176">about_WS Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="bec6b-176">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="bec6b-177">Invocação de comando</span><span class="sxs-lookup"><span data-stu-id="bec6b-177">Invoke-Command</span></span>](https://go.microsoft.com/fwlink/?LinkId=821493)
- [<span data-ttu-id="bec6b-178">Importar-PSSession</span><span class="sxs-lookup"><span data-stu-id="bec6b-178">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="bec6b-179">Novo-PSSession</span><span class="sxs-lookup"><span data-stu-id="bec6b-179">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="bec6b-180">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bec6b-180">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="bec6b-181">Fornecedor de WSMan</span><span class="sxs-lookup"><span data-stu-id="bec6b-181">WSMan Provider</span></span>](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)
