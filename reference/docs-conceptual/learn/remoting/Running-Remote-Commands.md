---
ms.date: 08/14/2018
keywords: PowerShell, o cmdlet
title: Executar Comandos Remotos
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 2001b5509acde6ec4259bb1442944958a67aa66f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688596"
---
# <a name="running-remote-commands"></a><span data-ttu-id="11870-103">Executar Comandos Remotos</span><span class="sxs-lookup"><span data-stu-id="11870-103">Running Remote Commands</span></span>

<span data-ttu-id="11870-104">Pode executar comandos num ou centenas de computadores com um único comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="11870-104">You can run commands on one or hundreds of computers with a single PowerShell command.</span></span> <span data-ttu-id="11870-105">Windows PowerShell oferece suporte a computação remoto, utilizando várias tecnologias, incluindo WMI, RPC e WS-Management.</span><span class="sxs-lookup"><span data-stu-id="11870-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

<span data-ttu-id="11870-106">O PowerShell Core oferece suporte a WMI, WS-Management e a comunicação remota do SSH.</span><span class="sxs-lookup"><span data-stu-id="11870-106">PowerShell Core supports WMI, WS-Management, and SSH remoting.</span></span> <span data-ttu-id="11870-107">RPC já não é suportada.</span><span class="sxs-lookup"><span data-stu-id="11870-107">RPC is no longer supported.</span></span>

<span data-ttu-id="11870-108">Para obter mais informações sobre a comunicação remota do PowerShell Core, consulte os artigos seguintes:</span><span class="sxs-lookup"><span data-stu-id="11870-108">For more information about remoting in PowerShell Core, see the following articles:</span></span>

- <span data-ttu-id="11870-109">[SSH comunicação remota no PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="11870-109">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="11870-110">[Comunicação remota do WSMan no PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="11870-110">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="windows-powershell-remoting-without-configuration"></a><span data-ttu-id="11870-111">Comunicação remota do Windows PowerShell sem configuração</span><span class="sxs-lookup"><span data-stu-id="11870-111">Windows PowerShell Remoting Without Configuration</span></span>

<span data-ttu-id="11870-112">Muitos cmdlets do Windows PowerShell tem o parâmetro ComputerName que lhe permite recolher dados e alterar as definições num ou mais computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="11870-112">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="11870-113">Estes cmdlets utilizar diferentes protocolos de comunicação e funciona em todos os sistemas de operativos do Windows sem nenhuma configuração especial.</span><span class="sxs-lookup"><span data-stu-id="11870-113">These cmdlets use varying communication protocols and work on all Windows operating systems without any special configuration.</span></span>

<span data-ttu-id="11870-114">Estes cmdlets incluem:</span><span class="sxs-lookup"><span data-stu-id="11870-114">These cmdlets include:</span></span>

- [<span data-ttu-id="11870-115">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="11870-115">Restart-Computer</span></span>](/powershell/module/microsoft.powershell.management/restart-computer)
- [<span data-ttu-id="11870-116">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="11870-116">Test-Connection</span></span>](/powershell/module/microsoft.powershell.management/test-connection)
- [<span data-ttu-id="11870-117">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="11870-117">Clear-EventLog</span></span>](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [<span data-ttu-id="11870-118">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="11870-118">Get-EventLog</span></span>](/powershell/module/microsoft.powershell.management/get-eventlog)
- [<span data-ttu-id="11870-119">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="11870-119">Get-HotFix</span></span>](/powershell/module/microsoft.powershell.management/get-hotfix)
- [<span data-ttu-id="11870-120">Get-Process</span><span class="sxs-lookup"><span data-stu-id="11870-120">Get-Process</span></span>](/powershell/module/microsoft.powershell.management/get-process)
- [<span data-ttu-id="11870-121">Get-Service</span><span class="sxs-lookup"><span data-stu-id="11870-121">Get-Service</span></span>](/powershell/module/microsoft.powershell.management/get-service)
- [<span data-ttu-id="11870-122">Set-Service</span><span class="sxs-lookup"><span data-stu-id="11870-122">Set-Service</span></span>](/powershell/module/microsoft.powershell.management/set-service)
- [<span data-ttu-id="11870-123">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="11870-123">Get-WinEvent</span></span>](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [<span data-ttu-id="11870-124">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="11870-124">Get-WmiObject</span></span>](/powershell/module/microsoft.powershell.management/get-wmiobject)

<span data-ttu-id="11870-125">Normalmente, os cmdlets que suportam a comunicação remota sem configuração especial tem o parâmetro ComputerName e não tem o parâmetro de sessão.</span><span class="sxs-lookup"><span data-stu-id="11870-125">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and don't have the Session parameter.</span></span> <span data-ttu-id="11870-126">Para localizar estes cmdlets na sua sessão, escreva:</span><span class="sxs-lookup"><span data-stu-id="11870-126">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="11870-127">Comunicação remota do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="11870-127">Windows PowerShell Remoting</span></span>

<span data-ttu-id="11870-128">Utilizar o protocolo WS-Management, comunicação remota do Windows PowerShell permite-lhe executar qualquer comando do Windows PowerShell num ou mais computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="11870-128">Using the WS-Management protocol, Windows PowerShell remoting lets you run any Windows PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="11870-129">Pode estabelecer ligações persistentes, iniciar sessões interativas e executar scripts em computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="11870-129">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

<span data-ttu-id="11870-130">Para utilizar a comunicação remota do Windows PowerShell, o computador remoto tem de ser configurado para a gestão remota.</span><span class="sxs-lookup"><span data-stu-id="11870-130">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="11870-131">Para obter mais informações, incluindo instruções, consulte [sobre os requisitos remoto](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span><span class="sxs-lookup"><span data-stu-id="11870-131">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="11870-132">Assim que tiver configurado a comunicação remota do Windows PowerShell, muitas estratégias de comunicação remota estão disponíveis para.</span><span class="sxs-lookup"><span data-stu-id="11870-132">Once you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span>
<span data-ttu-id="11870-133">Este artigo lista apenas alguns deles.</span><span class="sxs-lookup"><span data-stu-id="11870-133">This article lists just a few of them.</span></span> <span data-ttu-id="11870-134">Para obter mais informações, consulte [sobre o remoto](/powershell/module/microsoft.powershell.core/about/about_remote).</span><span class="sxs-lookup"><span data-stu-id="11870-134">For more information, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="11870-135">Iniciar uma sessão interativa</span><span class="sxs-lookup"><span data-stu-id="11870-135">Start an Interactive Session</span></span>

<span data-ttu-id="11870-136">Para iniciar uma sessão interativa com um único computador remoto, utilize o [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="11870-136">To start an interactive session with a single remote computer, use the [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span></span>
<span data-ttu-id="11870-137">Por exemplo, para iniciar uma sessão interativa com o computador remoto servidor01, escreva:</span><span class="sxs-lookup"><span data-stu-id="11870-137">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="11870-138">As alterações de linha de comandos para exibir o nome do computador remoto.</span><span class="sxs-lookup"><span data-stu-id="11870-138">The command prompt changes to display the name of the remote computer.</span></span> <span data-ttu-id="11870-139">Os comandos de que escreva na linha de comandos executado no computador remoto e os resultados são exibidos no computador local.</span><span class="sxs-lookup"><span data-stu-id="11870-139">Any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="11870-140">Para terminar a sessão interativa, escreva:</span><span class="sxs-lookup"><span data-stu-id="11870-140">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="11870-141">Para obter mais informações sobre os cmdlets de Enter-PSSession e Exit-PSSession, consulte:</span><span class="sxs-lookup"><span data-stu-id="11870-141">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see:</span></span>

- [<span data-ttu-id="11870-142">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="11870-142">Enter-PSSession</span></span>](/powershell/module/microsoft.powershell.core/enter-pssession)
- [<span data-ttu-id="11870-143">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="11870-143">Exit-PSSession</span></span>](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a><span data-ttu-id="11870-144">Executar um comando remoto</span><span class="sxs-lookup"><span data-stu-id="11870-144">Run a Remote Command</span></span>

<span data-ttu-id="11870-145">Para executar um comando num ou mais computadores, utilize o [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="11870-145">To run a command on one or more computers, use the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span> <span data-ttu-id="11870-146">Por exemplo, para executar uma [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) servidor01 e Server02 computadores remotos, tipo de comando:</span><span class="sxs-lookup"><span data-stu-id="11870-146">For example, to run a [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="11870-147">O resultado é devolvido para o seu computador.</span><span class="sxs-lookup"><span data-stu-id="11870-147">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a><span data-ttu-id="11870-148">Executar um Script</span><span class="sxs-lookup"><span data-stu-id="11870-148">Run a Script</span></span>

<span data-ttu-id="11870-149">Para executar um script numa ou mais computadores remotos, utilize o parâmetro de caminho do ficheiro do `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="11870-149">To run a script on one or many remote computers, use the FilePath parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="11870-150">O script deve ser igual ou acessível para o computador local.</span><span class="sxs-lookup"><span data-stu-id="11870-150">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="11870-151">Os resultados são devolvidos para o computador local.</span><span class="sxs-lookup"><span data-stu-id="11870-151">The results are returned to your local computer.</span></span>

<span data-ttu-id="11870-152">Por exemplo, o seguinte comando executa o script de DiskCollect.ps1 nos computadores remotos, servidor01 e Server02.</span><span class="sxs-lookup"><span data-stu-id="11870-152">For example, the following command runs the DiskCollect.ps1 script on the remote computers, Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="11870-153">Estabelecer uma ligação persistente</span><span class="sxs-lookup"><span data-stu-id="11870-153">Establish a Persistent Connection</span></span>

<span data-ttu-id="11870-154">Utilize o `New-PSSession` cmdlet para criar uma sessão persistente num computador remoto.</span><span class="sxs-lookup"><span data-stu-id="11870-154">Use the `New-PSSession` cmdlet to create a persistent session on a remote computer.</span></span> <span data-ttu-id="11870-155">O exemplo seguinte cria sessões remotas em servidor01 e Server02.</span><span class="sxs-lookup"><span data-stu-id="11870-155">The following example creates remote sessions on Server01 and Server02.</span></span> <span data-ttu-id="11870-156">Os objetos de sessão são armazenados no `$s` variável.</span><span class="sxs-lookup"><span data-stu-id="11870-156">The session objects are stored in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="11870-157">Agora que as sessões são estabelecidas, pode executar qualquer comando nos mesmos.</span><span class="sxs-lookup"><span data-stu-id="11870-157">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="11870-158">E como as sessões são persistentes, pode recolher dados de um comando e utilizá-lo em outro comando.</span><span class="sxs-lookup"><span data-stu-id="11870-158">And because the sessions are persistent, you can collect data from one command and use it in another command.</span></span>

<span data-ttu-id="11870-159">Por exemplo, o seguinte comando executa um comando de Get-HotFix em sessões na variável $s e este guarda os resultados na variável $h.</span><span class="sxs-lookup"><span data-stu-id="11870-159">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="11870-160">A variável $h é criada em cada uma das sessões no $s, mas não existir na sessão local.</span><span class="sxs-lookup"><span data-stu-id="11870-160">The $h variable is created in each of the sessions in $s, but it doesn't exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="11870-161">Agora, pode utilizar os dados no `$h` variável com outros comandos na mesma sessão.</span><span class="sxs-lookup"><span data-stu-id="11870-161">Now you can use the data in the `$h` variable with other commands in the same session.</span></span> <span data-ttu-id="11870-162">Os resultados são exibidos no computador local.</span><span class="sxs-lookup"><span data-stu-id="11870-162">The results are displayed on the local computer.</span></span> <span data-ttu-id="11870-163">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="11870-163">For example:</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="11870-164">Comunicação remota avançada</span><span class="sxs-lookup"><span data-stu-id="11870-164">Advanced Remoting</span></span>

<span data-ttu-id="11870-165">Gestão remota do Windows PowerShell apenas começa aqui.</span><span class="sxs-lookup"><span data-stu-id="11870-165">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="11870-166">Ao utilizar os cmdlets instalados com o Windows PowerShell, pode estabelecer e configurar sessões remotas, as duas das extremidades locais e remotas, a criar sessões restritos e personalizadas, permitir que os utilizadores para importar os comandos de uma sessão remota, que, na verdade, executam implicitamente na sessão remota, configure a segurança de uma sessão remota e muito mais.</span><span class="sxs-lookup"><span data-stu-id="11870-166">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="11870-167">Windows PowerShell inclui um provedor de WSMan.</span><span class="sxs-lookup"><span data-stu-id="11870-167">Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="11870-168">O fornecedor de cria um `WSMAN:` unidade que lhe permite navegar através de uma hierarquia de definições de configuração no computador local e computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="11870-168">The provider creates a `WSMAN:` drive that lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>

<span data-ttu-id="11870-169">Para obter mais informações sobre o fornecedor de WSMan, consulte [fornecedor de WSMan](https://technet.microsoft.com/library/dd819476.aspx) e [sobre Cmdlets de WS-Management](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), ou na consola do Windows PowerShell, escreva `Get-Help wsman`.</span><span class="sxs-lookup"><span data-stu-id="11870-169">For more information about the WSMan provider, see [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) and [About WS-Management Cmdlets](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), or in the Windows PowerShell console, type `Get-Help wsman`.</span></span>

<span data-ttu-id="11870-170">Para mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="11870-170">For more information, see:</span></span>

- [<span data-ttu-id="11870-171">Acerca das FAQ remotas</span><span class="sxs-lookup"><span data-stu-id="11870-171">About Remote FAQ</span></span>](https://technet.microsoft.com/library/dd315359.aspx)
- [<span data-ttu-id="11870-172">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="11870-172">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="11870-173">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="11870-173">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="11870-174">Para obter ajuda com erros de comunicação remota, consulte [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="11870-174">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="11870-175">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="11870-175">See Also</span></span>

- [<span data-ttu-id="11870-176">about_Remote</span><span class="sxs-lookup"><span data-stu-id="11870-176">about_Remote</span></span>](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="11870-177">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="11870-177">about_Remote_FAQ</span></span>](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="11870-178">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="11870-178">about_Remote_Requirements</span></span>](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="11870-179">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="11870-179">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="11870-180">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="11870-180">about_PSSessions</span></span>](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="11870-181">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="11870-181">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="11870-182">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="11870-182">Invoke-Command</span></span>](/powershell/module/microsoft.powershell.core/invoke-command)
- [<span data-ttu-id="11870-183">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="11870-183">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="11870-184">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="11870-184">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="11870-185">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="11870-185">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="11870-186">Fornecedor de WSMan</span><span class="sxs-lookup"><span data-stu-id="11870-186">WSMan Provider</span></span>](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md