---
ms.date: 09/09/2019
keywords: PowerShell, cmdlet
title: Apêndice 1 – Aliases de Compatibilidade
ms.openlocfilehash: 2351fdf23711fe1417f7e3fc3cca5b642d5a59fc
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848174"
---
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="84246-103">Apêndice 1-aliases de compatibilidade</span><span class="sxs-lookup"><span data-stu-id="84246-103">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="84246-104">O PowerShell tem vários aliases que permitem que os usuários do **Unix** e **cmd. exe** usem comandos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="84246-104">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="84246-105">Os comandos e seus cmdlets do PowerShell relacionados e alias do PowerShell são mostrados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="84246-105">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|<span data-ttu-id="84246-106">comando cmd. exe</span><span class="sxs-lookup"><span data-stu-id="84246-106">cmd.exe command</span></span>|<span data-ttu-id="84246-107">Comando UNIX</span><span class="sxs-lookup"><span data-stu-id="84246-107">UNIX command</span></span>|<span data-ttu-id="84246-108">Cmdlet do PowerShell</span><span class="sxs-lookup"><span data-stu-id="84246-108">PowerShell cmdlet</span></span>|<span data-ttu-id="84246-109">Alias do PowerShell</span><span class="sxs-lookup"><span data-stu-id="84246-109">PowerShell alias</span></span>|
|---------------|----------------|--------------|------------|
|<span data-ttu-id="84246-110">**CLS**</span><span class="sxs-lookup"><span data-stu-id="84246-110">**cls**</span></span>|<span data-ttu-id="84246-111">**clear**</span><span class="sxs-lookup"><span data-stu-id="84246-111">**clear**</span></span>|<span data-ttu-id="84246-112">`Clear-Host`funcionamento</span><span class="sxs-lookup"><span data-stu-id="84246-112">`Clear-Host` (function)</span></span>|`cls`|
|<span data-ttu-id="84246-113">**CopiarObjeto**</span><span class="sxs-lookup"><span data-stu-id="84246-113">**copy**</span></span>|<span data-ttu-id="84246-114">**CP**</span><span class="sxs-lookup"><span data-stu-id="84246-114">**cp**</span></span>|`Copy-Item`|`cpi`|
|<span data-ttu-id="84246-115">**comando**</span><span class="sxs-lookup"><span data-stu-id="84246-115">**dir**</span></span>|<span data-ttu-id="84246-116">**ls**</span><span class="sxs-lookup"><span data-stu-id="84246-116">**ls**</span></span>|`Get-ChildItem`|`gci`|
|<span data-ttu-id="84246-117">**type**</span><span class="sxs-lookup"><span data-stu-id="84246-117">**type**</span></span>|<span data-ttu-id="84246-118">**cat**</span><span class="sxs-lookup"><span data-stu-id="84246-118">**cat**</span></span>|`Get-Content`|`gc`|
|<span data-ttu-id="84246-119">**prosseguir**</span><span class="sxs-lookup"><span data-stu-id="84246-119">**move**</span></span>|<span data-ttu-id="84246-120">**MV**</span><span class="sxs-lookup"><span data-stu-id="84246-120">**mv**</span></span>|`Move-Item`|`mi`|
|<span data-ttu-id="84246-121">**MD**</span><span class="sxs-lookup"><span data-stu-id="84246-121">**md**</span></span>|<span data-ttu-id="84246-122">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="84246-122">**mkdir**</span></span>|`New-Item`|`ni`|
|<span data-ttu-id="84246-123">**PUSHD**</span><span class="sxs-lookup"><span data-stu-id="84246-123">**pushd**</span></span>|<span data-ttu-id="84246-124">**PUSHD**</span><span class="sxs-lookup"><span data-stu-id="84246-124">**pushd**</span></span>|`Push-Location`|`pushd`|
|<span data-ttu-id="84246-125">**popd**</span><span class="sxs-lookup"><span data-stu-id="84246-125">**popd**</span></span>|<span data-ttu-id="84246-126">**popd**</span><span class="sxs-lookup"><span data-stu-id="84246-126">**popd**</span></span>|`Pop-Location`|`popd`|
|<span data-ttu-id="84246-127">**del**, **Erase**, **RD**, **rmdir**</span><span class="sxs-lookup"><span data-stu-id="84246-127">**del**, **erase**, **rd**, **rmdir**</span></span>|<span data-ttu-id="84246-128">**RM**</span><span class="sxs-lookup"><span data-stu-id="84246-128">**rm**</span></span>|`Remove-Item`|`ri`|
|<span data-ttu-id="84246-129">**Outlook**</span><span class="sxs-lookup"><span data-stu-id="84246-129">**ren**</span></span>|<span data-ttu-id="84246-130">**MV**</span><span class="sxs-lookup"><span data-stu-id="84246-130">**mv**</span></span>|`Rename-Item`|`rni`|
|<span data-ttu-id="84246-131">**CD**, **chdir**</span><span class="sxs-lookup"><span data-stu-id="84246-131">**cd**, **chdir**</span></span>|<span data-ttu-id="84246-132">**CD**</span><span class="sxs-lookup"><span data-stu-id="84246-132">**cd**</span></span>|`Set-Location`|`sl`|

<span data-ttu-id="84246-133">Para localizar os aliases do PowerShell, use o cmdlet [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) .</span><span class="sxs-lookup"><span data-stu-id="84246-133">To find the PowerShell aliases, use the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet.</span></span> <span data-ttu-id="84246-134">Para exibir os aliases de um cmdlet, use o parâmetro de **definição** e especifique o nome do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="84246-134">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="84246-135">Ou, para localizar o nome do cmdlet de um alias, use o parâmetro **Name** e especifique o alias.</span><span class="sxs-lookup"><span data-stu-id="84246-135">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```
