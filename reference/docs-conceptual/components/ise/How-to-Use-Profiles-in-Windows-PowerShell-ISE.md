---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Como Utilizar Perfis no ISE do Windows PowerShell
ms.openlocfilehash: 28354f39aaaa577cec69c1b3f62cfe16ef091218
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030599"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="56a35-103">Como Utilizar Perfis no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="56a35-103">How to Use Profiles in Windows PowerShell ISE</span></span>

<span data-ttu-id="56a35-104">Este tópico explica como utilizar perfis no Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="56a35-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="56a35-105">Recomendamos que antes de executar as tarefas nesta secção, reveja [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), ou no painel da consola, tipo, `Get-Help about_Profiles` e prima **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="56a35-105">We recommend that before performing the tasks in this section, you review [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), or in the Console Pane, type, `Get-Help about_Profiles` and press **ENTER**.</span></span>

<span data-ttu-id="56a35-106">Um perfil é um script do ISE do Windows PowerShell que é executada automaticamente quando iniciar uma sessão de novo.</span><span class="sxs-lookup"><span data-stu-id="56a35-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>  <span data-ttu-id="56a35-107">Pode criar um ou mais perfis do Windows PowerShell para o ISE do Windows PowerShell e utilizá-los para adicionar a configurar o ambiente do Windows PowerShell ou o Windows PowerShell ISE, preparando-o para a sua utilização, com variáveis, aliases, funções e a cor e tipo de letra preferências que quer estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="56a35-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="56a35-108">Um perfil afeta todas as sessões de ISE do Windows PowerShell que começar.</span><span class="sxs-lookup"><span data-stu-id="56a35-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="56a35-109">A política de execução do Windows PowerShell determina se pode executar scripts e um perfil de carga.</span><span class="sxs-lookup"><span data-stu-id="56a35-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span> <span data-ttu-id="56a35-110">A diretiva de execução padrão "Restritas", impede que todos os scripts sejam executados, incluindo perfis.</span><span class="sxs-lookup"><span data-stu-id="56a35-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span> <span data-ttu-id="56a35-111">Se utilizar a política de "Restrito", não é possível carregar o perfil.</span><span class="sxs-lookup"><span data-stu-id="56a35-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="56a35-112">Para obter mais informações sobre a política de execução, consulte [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="56a35-112">For more information about execution policy, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="56a35-113">Selecionar um perfil para utilizar no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="56a35-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>

<span data-ttu-id="56a35-114">ISE do Windows PowerShell suporta perfis para o utilizador atual e todos os utilizadores.</span><span class="sxs-lookup"><span data-stu-id="56a35-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="56a35-115">Também suporta os perfis do Windows PowerShell que se aplicam a todos os anfitriões.</span><span class="sxs-lookup"><span data-stu-id="56a35-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="56a35-116">O perfil que utiliza é determinado pelo como usar o Windows PowerShell e Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="56a35-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="56a35-117">Se utilizar apenas o Windows PowerShell ISE para executar o Windows PowerShell, em seguida, guarde a todos os seus itens em um dos perfis de ISE específicos, como o perfil de CurrentUserCurrentHost para ISE do Windows PowerShell ou o perfil de AllUsersCurrentHost para Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="56a35-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the CurrentUserCurrentHost profile for Windows PowerShell ISE or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="56a35-118">Se utilizar vários programas de anfitrião para executar o Windows PowerShell, salvar seus aliases, funções, variáveis e comandos num perfil que afeta todos os programas de anfitrião, como o CurrentUserAllHosts ou o perfil de AllUsersAllHosts e guardar os recursos específicos do ISE, como cor e tipo de letra personalização no perfil de CurrentUserCurrentHost para o perfil do ISE do Windows PowerShell ou o perfil de AllUsersCurrentHost para Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="56a35-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the AllUsersAllHosts profile, and save ISE-specific features, like color and font customization in the CurrentUserCurrentHost profile for Windows PowerShell ISE profile or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="56a35-119">Seguem-se os perfis podem ser criados e utilizados no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56a35-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="56a35-120">Cada perfil é salvo em seu próprio caminho específico.</span><span class="sxs-lookup"><span data-stu-id="56a35-120">Each profile is saved to its own specific path.</span></span>

| <span data-ttu-id="56a35-121">Tipo de perfil</span><span class="sxs-lookup"><span data-stu-id="56a35-121">Profile Type</span></span> | <span data-ttu-id="56a35-122">Caminho do perfil</span><span class="sxs-lookup"><span data-stu-id="56a35-122">Profile Path</span></span> |
| --- | --- |
| <span data-ttu-id="56a35-123">**Utilizador atual, o ISE do PowerShell**</span><span class="sxs-lookup"><span data-stu-id="56a35-123">**Current user, PowerShell ISE**</span></span>| <span data-ttu-id="56a35-124">`$PROFILE.CurrentUserCurrentHost`, ou `$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="56a35-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="56a35-125">**Todos os utilizadores, o ISE do PowerShell**</span><span class="sxs-lookup"><span data-stu-id="56a35-125">**All users, PowerShell ISE**</span></span>| `$PROFILE.AllUsersCurrentHost` |
| <span data-ttu-id="56a35-126">**Utilizador atual, todos os anfitriões**</span><span class="sxs-lookup"><span data-stu-id="56a35-126">**Current user, All hosts**</span></span>| `$PROFILE.CurrentUserAllHosts` |
| <span data-ttu-id="56a35-127">**Todos os utilizadores, todos os anfitriões**</span><span class="sxs-lookup"><span data-stu-id="56a35-127">**All users, All hosts**</span></span> | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="56a35-128">Para criar um novo perfil</span><span class="sxs-lookup"><span data-stu-id="56a35-128">To create a new profile</span></span>

<span data-ttu-id="56a35-129">Para criar um novo "utilizador atual, a ISE do Windows PowerShell" perfil, execute este comando:</span><span class="sxs-lookup"><span data-stu-id="56a35-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="56a35-130">Para criar um novo "Todos os utilizadores, a ISE do Windows PowerShell" perfil, execute este comando:</span><span class="sxs-lookup"><span data-stu-id="56a35-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="56a35-131">Para criar um novo perfil "utilizador atual, todos os anfitriões", execute este comando:</span><span class="sxs-lookup"><span data-stu-id="56a35-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="56a35-132">Para criar um novo perfil de "todos os utilizadores, todos os anfitriões", escreva:</span><span class="sxs-lookup"><span data-stu-id="56a35-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="56a35-133">Para editar um perfil</span><span class="sxs-lookup"><span data-stu-id="56a35-133">To edit a profile</span></span>

1. <span data-ttu-id="56a35-134">Para abrir o perfil, execute o comando psedit com a variável que especifica o perfil que pretende editar.</span><span class="sxs-lookup"><span data-stu-id="56a35-134">To open the profile, run the command psedit with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="56a35-135">Por exemplo, para abrir o "utilizador atual, a ISE do Windows PowerShell" de perfil, escreva: `psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="56a35-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="56a35-136">Adicione alguns itens ao seu perfil.</span><span class="sxs-lookup"><span data-stu-id="56a35-136">Add some items to your profile.</span></span> <span data-ttu-id="56a35-137">Seguem-se alguns exemplos para começar:</span><span class="sxs-lookup"><span data-stu-id="56a35-137">The following are a few examples to get you started:</span></span>

   - <span data-ttu-id="56a35-138">Para alterar a cor de fundo padrão do painel de consola para azul, no tipo de ficheiro de perfil: `$psISE.Options.OutputPaneBackground = 'blue'` .</span><span class="sxs-lookup"><span data-stu-id="56a35-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="56a35-139">Para obter mais informações sobre a variável $psISE, consulte [referência do modelo de objeto ISE do Windows PowerShell](object-model/The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="56a35-139">For more information about the $psISE variable, see [Windows PowerShell ISE Object Model Reference](object-model/The-ISE-Object-Model-Hierarchy.md).</span></span>

   - <span data-ttu-id="56a35-140">Para alterar o tamanho da fonte para 20, no tipo de ficheiro de perfil: `$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="56a35-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="56a35-141">Para guardar o ficheiro de perfil, diante a **arquivo** menu, clique em **guardar**.</span><span class="sxs-lookup"><span data-stu-id="56a35-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="56a35-142">Próxima vez que abrir o ISE do Windows PowerShell, as personalizações são aplicadas.</span><span class="sxs-lookup"><span data-stu-id="56a35-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="56a35-143">Veja Também</span><span class="sxs-lookup"><span data-stu-id="56a35-143">See Also</span></span>

- [<span data-ttu-id="56a35-144">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="56a35-144">about_Profiles</span></span>](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [<span data-ttu-id="56a35-145">Introdução ao ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="56a35-145">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
