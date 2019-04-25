---
title: Comunicação Remota do WS-Management (WSMan) no PowerShell Core
description: Comunicação remota do PowerShell Core através de WSMan
ms.date: 08/06/2018
ms.openlocfilehash: e5f00128bc8ebc1b432cc77a5896a9e09d684109
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058884"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="d348f-103">Comunicação Remota do WS-Management (WSMan) no PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="d348f-103">WS-Management (WSMan) Remoting in PowerShell Core</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="d348f-104">Instruções para criar um ponto de extremidade de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="d348f-104">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="d348f-105">O pacote do PowerShell Core para Windows inclui um plug-in de WinRM (`pwrshplugin.dll`) e um script de instalação (`Install-PowerShellRemoting.ps1`) no `$PSHome`.</span><span class="sxs-lookup"><span data-stu-id="d348f-105">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span>
<span data-ttu-id="d348f-106">Estes ficheiros ativar o PowerShell aceitar ligações remotas recebidas do PowerShell quando é especificado o seu ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="d348f-106">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="d348f-107">Motivação</span><span class="sxs-lookup"><span data-stu-id="d348f-107">Motivation</span></span>

<span data-ttu-id="d348f-108">Uma instalação do PowerShell pode estabelecer sessões do PowerShell para computadores remotos utilizando `New-PSSession` e `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="d348f-108">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span>
<span data-ttu-id="d348f-109">Para ativá-la aceitar ligações remotas recebidas do PowerShell, o utilizador tem de criar um ponto de extremidade de comunicação remota do WinRM.</span><span class="sxs-lookup"><span data-stu-id="d348f-109">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span>
<span data-ttu-id="d348f-110">Este é um explícito Inscreva-se no cenário em que o usuário executa Install-PowerShellRemoting.ps1 para criar o ponto de extremidade do WinRM.</span><span class="sxs-lookup"><span data-stu-id="d348f-110">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span>
<span data-ttu-id="d348f-111">O script de instalação é uma solução de curto prazo, até que podemos adicionar funcionalidade adicional para `Enable-PSRemoting` para executar a mesma ação.</span><span class="sxs-lookup"><span data-stu-id="d348f-111">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span>
<span data-ttu-id="d348f-112">Para obter mais detalhes, consulte problema [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span><span class="sxs-lookup"><span data-stu-id="d348f-112">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="d348f-113">Ações de script</span><span class="sxs-lookup"><span data-stu-id="d348f-113">Script Actions</span></span>

<span data-ttu-id="d348f-114">O script</span><span class="sxs-lookup"><span data-stu-id="d348f-114">The script</span></span>

1. <span data-ttu-id="d348f-115">Cria um diretório para o plug-in dentro de `$env:windir\System32\PowerShell`</span><span class="sxs-lookup"><span data-stu-id="d348f-115">Creates a directory for the plug-in within `$env:windir\System32\PowerShell`</span></span>
1. <span data-ttu-id="d348f-116">Copia pwrshplugin.dll para essa localização</span><span class="sxs-lookup"><span data-stu-id="d348f-116">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="d348f-117">Gera um ficheiro de configuração</span><span class="sxs-lookup"><span data-stu-id="d348f-117">Generates a configuration file</span></span>
1. <span data-ttu-id="d348f-118">Registros ou plug-ins do WinRM</span><span class="sxs-lookup"><span data-stu-id="d348f-118">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="d348f-119">Registo</span><span class="sxs-lookup"><span data-stu-id="d348f-119">Registration</span></span>

<span data-ttu-id="d348f-120">O script tem de ser executado dentro de uma sessão do PowerShell de nível de administrador e é executado em dois modos.</span><span class="sxs-lookup"><span data-stu-id="d348f-120">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="d348f-121">Executado pela instância do PowerShell que serão registados</span><span class="sxs-lookup"><span data-stu-id="d348f-121">Executed by the instance of PowerShell that it will register</span></span>

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="d348f-122">Executado por outra instância do PowerShell em nome da instância que serão registados</span><span class="sxs-lookup"><span data-stu-id="d348f-122">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="d348f-123">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d348f-123">For Example:</span></span>

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

<span data-ttu-id="d348f-124">**NOTA:** O script de registro de comunicação remota reiniciará o WinRM, para que todas as sessões PSRP existentes serão encerrado imediatamente após o script é executado.</span><span class="sxs-lookup"><span data-stu-id="d348f-124">**NOTE:** The remoting registration script will restart WinRM, so all existing PSRP sessions will terminate immediately after the script is run.</span></span> <span data-ttu-id="d348f-125">Se executar durante uma sessão remota, isso irá terminar a ligação.</span><span class="sxs-lookup"><span data-stu-id="d348f-125">If run during a remote session, this will terminate the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="d348f-126">Como se pode ligar para o novo ponto final</span><span class="sxs-lookup"><span data-stu-id="d348f-126">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="d348f-127">Criar uma sessão de PowerShell para o novo ponto de final do PowerShell, especificando `-ConfigurationName "some endpoint name"`.</span><span class="sxs-lookup"><span data-stu-id="d348f-127">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="d348f-128">Para ligar à instância do PowerShell do exemplo acima, utilize qualquer um dos seguintes itens:</span><span class="sxs-lookup"><span data-stu-id="d348f-128">To connect to the PowerShell instance from the example above, use either:</span></span>

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="d348f-129">Tenha em atenção que `New-PSSession` e `Enter-PSSession` invocações de que não especificam `-ConfigurationName` destina-se o ponto de final do PowerShell de predefinido, `microsoft.powershell`.</span><span class="sxs-lookup"><span data-stu-id="d348f-129">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>