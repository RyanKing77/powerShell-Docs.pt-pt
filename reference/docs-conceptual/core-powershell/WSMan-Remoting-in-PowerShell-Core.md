# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="371b3-101">Comunicação Remota do WS-Management (WSMan) no PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="371b3-101">WS-Management (WSMan) Remoting in PowerShell Core</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="371b3-102">Instruções para criar um ponto final de gestão remota</span><span class="sxs-lookup"><span data-stu-id="371b3-102">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="371b3-103">O pacote de núcleo do PowerShell para o Windows inclui um plug-in de WinRM (`pwrshplugin.dll`) e um script de instalação (`Install-PowerShellRemoting.ps1`) no `$PSHome`.</span><span class="sxs-lookup"><span data-stu-id="371b3-103">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span>
<span data-ttu-id="371b3-104">Estes ficheiros ativar o PowerShell aceitar ligações remotas de entrada do PowerShell quando o seu ponto final está especificado.</span><span class="sxs-lookup"><span data-stu-id="371b3-104">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="371b3-105">Motivação</span><span class="sxs-lookup"><span data-stu-id="371b3-105">Motivation</span></span>

<span data-ttu-id="371b3-106">Uma instalação do PowerShell pode estabelecer sessões de PowerShell para computadores remotos utilizando `New-PSSession` e `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="371b3-106">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span>
<span data-ttu-id="371b3-107">Para ativá-la para aceitar ligações remotas a receber do PowerShell, o utilizador tem de criar um ponto de final de comunicação remota do WinRM.</span><span class="sxs-lookup"><span data-stu-id="371b3-107">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span>
<span data-ttu-id="371b3-108">Este é um explícito optar ativamente por participar no cenário em que o utilizador executa Install-PowerShellRemoting.ps1 para criar o ponto final do WinRM.</span><span class="sxs-lookup"><span data-stu-id="371b3-108">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span>
<span data-ttu-id="371b3-109">O script de instalação é uma solução de curta duração, até que iremos adicionar funcionalidades adicionais para `Enable-PSRemoting` para efetuar a mesma ação.</span><span class="sxs-lookup"><span data-stu-id="371b3-109">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span>
<span data-ttu-id="371b3-110">Para obter mais detalhes, consulte problema [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span><span class="sxs-lookup"><span data-stu-id="371b3-110">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="371b3-111">Ações de script</span><span class="sxs-lookup"><span data-stu-id="371b3-111">Script Actions</span></span>

<span data-ttu-id="371b3-112">O script</span><span class="sxs-lookup"><span data-stu-id="371b3-112">The script</span></span>

1. <span data-ttu-id="371b3-113">Cria um diretório para o plug-in dentro %windir%\System32\PowerShell</span><span class="sxs-lookup"><span data-stu-id="371b3-113">Creates a directory for the plug-in within %windir%\System32\PowerShell</span></span>
1. <span data-ttu-id="371b3-114">Copia pwrshplugin.dll para essa localização</span><span class="sxs-lookup"><span data-stu-id="371b3-114">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="371b3-115">Gera um ficheiro de configuração</span><span class="sxs-lookup"><span data-stu-id="371b3-115">Generates a configuration file</span></span>
1. <span data-ttu-id="371b3-116">Regista ou plug-in com WinRM</span><span class="sxs-lookup"><span data-stu-id="371b3-116">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="371b3-117">Registo</span><span class="sxs-lookup"><span data-stu-id="371b3-117">Registration</span></span>

<span data-ttu-id="371b3-118">O script tem de ser executado dentro de uma sessão do PowerShell de nível de administrador e é executado em dois modos.</span><span class="sxs-lookup"><span data-stu-id="371b3-118">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="371b3-119">Executado pela instância do PowerShell que serão registados</span><span class="sxs-lookup"><span data-stu-id="371b3-119">Executed by the instance of PowerShell that it will register</span></span>

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="371b3-120">Executado por outra instância do PowerShell em nome de instância que serão registados</span><span class="sxs-lookup"><span data-stu-id="371b3-120">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="371b3-121">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="371b3-121">For Example:</span></span>

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

<span data-ttu-id="371b3-122">**Nota:** o script de registo do sistema de interação remota reiniciará WinRM, pelo que todas as sessões PSRP existentes irão terminar imediatamente após o script é executado.</span><span class="sxs-lookup"><span data-stu-id="371b3-122">**NOTE:** The remoting registration script will restart WinRM, so all existing PSRP sessions will terminate immediately after the script is run.</span></span> <span data-ttu-id="371b3-123">Se executar durante uma sessão remota, isto irá terminar a ligação.</span><span class="sxs-lookup"><span data-stu-id="371b3-123">If run during a remote session, this will terminate the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="371b3-124">Como ligar para o novo ponto final</span><span class="sxs-lookup"><span data-stu-id="371b3-124">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="371b3-125">Criar uma sessão do PowerShell para o novo ponto de final do PowerShell, especificando `-ConfigurationName "some endpoint name"`.</span><span class="sxs-lookup"><span data-stu-id="371b3-125">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="371b3-126">Para ligar à instância do PowerShell de exemplo acima, utilize qualquer um dos seguintes itens:</span><span class="sxs-lookup"><span data-stu-id="371b3-126">To connect to the PowerShell instance from the example above, use either:</span></span>

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="371b3-127">Tenha em atenção que `New-PSSession` e `Enter-PSSession` invocações que não especificam `-ConfigurationName` destina-se o ponto final do PowerShell predefinido, `microsoft.powershell`.</span><span class="sxs-lookup"><span data-stu-id="371b3-127">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>