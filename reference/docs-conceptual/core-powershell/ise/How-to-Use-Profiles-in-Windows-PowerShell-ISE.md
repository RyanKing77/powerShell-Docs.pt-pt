---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Como Utilizar Perfis no ISE do Windows PowerShell
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: 8789d6283457f790fdea27657abb2612304e10a1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="265e5-103">Como Utilizar Perfis no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="265e5-103">How to Use Profiles in Windows PowerShell ISE</span></span>

<span data-ttu-id="265e5-104">Este tópico explica como utilizar perfis no Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="265e5-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="265e5-105">Recomendamos que antes de executar as tarefas nesta secção, consulte o artigo [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), ou no painel de consola, tipo, `Get-Help about_Profiles` e prima **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="265e5-105">We recommend that before performing the tasks in this section, you review [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), or in the Console Pane, type, `Get-Help about_Profiles` and press **ENTER**.</span></span>

<span data-ttu-id="265e5-106">Um perfil é um script de ISE do Windows PowerShell que é executado automaticamente quando iniciar uma nova sessão.</span><span class="sxs-lookup"><span data-stu-id="265e5-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>  <span data-ttu-id="265e5-107">Pode criar um ou mais perfis do Windows PowerShell para o ISE do Windows PowerShell e utilizá-los para adicionar a configurar o ambiente do Windows PowerShell ou o ISE do Windows PowerShell, prepará-lo para utilização, com variáveis, aliases, funções e cor e o tipo de letra preferências que pretende que sejam disponíveis.</span><span class="sxs-lookup"><span data-stu-id="265e5-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="265e5-108">Um perfil afeta cada sessão de ISE do Windows PowerShell que pode inicia.</span><span class="sxs-lookup"><span data-stu-id="265e5-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="265e5-109">A política de execução do Windows PowerShell determina se pode executar scripts e um perfil de carga.</span><span class="sxs-lookup"><span data-stu-id="265e5-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span> <span data-ttu-id="265e5-110">A política de execução da predefinição "Restrito," impedem que todos os scripts sejam executados, incluindo perfis.</span><span class="sxs-lookup"><span data-stu-id="265e5-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span> <span data-ttu-id="265e5-111">Se utilizar a política de "Restrito", não é possível carregar o perfil.</span><span class="sxs-lookup"><span data-stu-id="265e5-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="265e5-112">Para obter mais informações sobre a política de execução, consulte [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="265e5-112">For more information about execution policy, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="265e5-113">Selecionar um perfil para utilizar no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="265e5-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>

<span data-ttu-id="265e5-114">ISE do Windows PowerShell suporta perfis para o utilizador atual e todos os utilizadores.</span><span class="sxs-lookup"><span data-stu-id="265e5-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="265e5-115">Também suporta os perfis do Windows PowerShell que se aplicam a todos os anfitriões.</span><span class="sxs-lookup"><span data-stu-id="265e5-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="265e5-116">O perfil que utiliza é determinado pelo como utilizar o Windows PowerShell e o ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="265e5-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="265e5-117">Se utilizar apenas ISE do Windows PowerShell para executar o Windows PowerShell, em seguida, guarde a todos os seus itens dos perfis de ISE específicas, tais como o perfil de CurrentUserCurrentHost para ISE do Windows PowerShell ou o perfil de AllUsersCurrentHost para ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="265e5-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the CurrentUserCurrentHost profile for Windows PowerShell ISE or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="265e5-118">Se utilizar vários programas de anfitrião para executar o Windows PowerShell, guarde a funções, aliases, variáveis e os comandos num perfil que afeta todos os programas de anfitrião, como o CurrentUserAllHosts ou no perfil de AllUsersAllHosts e guardar funcionalidades específicas do ISE, como cor e o tipo de letra personalização no perfil de CurrentUserCurrentHost para perfil do ISE do Windows PowerShell ou o perfil de AllUsersCurrentHost para ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="265e5-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the AllUsersAllHosts profile, and save ISE-specific features, like color and font customization in the CurrentUserCurrentHost profile for Windows PowerShell ISE profile or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="265e5-119">Seguem-se perfis que podem ser criados e utilizados no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="265e5-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="265e5-120">Cada perfil é guardado para a sua própria caminho específico.</span><span class="sxs-lookup"><span data-stu-id="265e5-120">Each profile is saved to its own specific path.</span></span>

| <span data-ttu-id="265e5-121">Tipo de perfil</span><span class="sxs-lookup"><span data-stu-id="265e5-121">Profile Type</span></span> | <span data-ttu-id="265e5-122">Caminho do perfil</span><span class="sxs-lookup"><span data-stu-id="265e5-122">Profile Path</span></span> |
| --- | --- |
| <span data-ttu-id="265e5-123">**Utilizador atual, o ISE do PowerShell**</span><span class="sxs-lookup"><span data-stu-id="265e5-123">**Current user, PowerShell ISE**</span></span>| <span data-ttu-id="265e5-124">`$PROFILE.CurrentUserCurrentHost`, ou `$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="265e5-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="265e5-125">**Todos os utilizadores, ISE do PowerShell**</span><span class="sxs-lookup"><span data-stu-id="265e5-125">**All users, PowerShell ISE**</span></span>| `$PROFILE.AllUsersCurrentHost` |
| <span data-ttu-id="265e5-126">**Utilizador atual, todos os anfitriões**</span><span class="sxs-lookup"><span data-stu-id="265e5-126">**Current user, All hosts**</span></span>| `$PROFILE.CurrentUserAllHosts` |
| <span data-ttu-id="265e5-127">**Todos os utilizadores, todos os anfitriões**</span><span class="sxs-lookup"><span data-stu-id="265e5-127">**All users, All hosts**</span></span> | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="265e5-128">Para criar um novo perfil</span><span class="sxs-lookup"><span data-stu-id="265e5-128">To create a new profile</span></span>

<span data-ttu-id="265e5-129">Para criar um nova "utilizador atual, ISE do Windows PowerShell" perfil, execute este comando:</span><span class="sxs-lookup"><span data-stu-id="265e5-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="265e5-130">Para criar uma nova "Todos os utilizadores, ISE do Windows PowerShell" perfil, execute este comando:</span><span class="sxs-lookup"><span data-stu-id="265e5-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="265e5-131">Para criar um novo perfil "utilizador atual, todos os anfitriões", execute este comando:</span><span class="sxs-lookup"><span data-stu-id="265e5-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="265e5-132">Para criar um novo perfil "todos os utilizadores, todos os anfitriões", escreva:</span><span class="sxs-lookup"><span data-stu-id="265e5-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="265e5-133">Para editar um perfil</span><span class="sxs-lookup"><span data-stu-id="265e5-133">To edit a profile</span></span>

1. <span data-ttu-id="265e5-134">Para abrir o perfil, execute o comando psedit com a variável que especifica o perfil que pretende editar.</span><span class="sxs-lookup"><span data-stu-id="265e5-134">To open the profile, run the command psedit with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="265e5-135">Por exemplo, para abrir o "utilizador atual, ISE do Windows PowerShell" perfil, escreva: `psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="265e5-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="265e5-136">Adicione alguns itens para o seu perfil.</span><span class="sxs-lookup"><span data-stu-id="265e5-136">Add some items to your profile.</span></span> <span data-ttu-id="265e5-137">Seguem-se alguns exemplos para ajudar a começar:</span><span class="sxs-lookup"><span data-stu-id="265e5-137">The following are a few examples to get you started:</span></span>

   - <span data-ttu-id="265e5-138">Para alterar a cor de fundo predefinido do painel de consola para azul, no tipo de ficheiro de perfil: `$psISE.Options.OutputPaneBackground = 'blue'` .</span><span class="sxs-lookup"><span data-stu-id="265e5-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="265e5-139">Para mais informações sobre a variável de $psISE, consulte [referência de modelo de objeto do Windows PowerShell ISE](The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="265e5-139">For more information about the $psISE variable, see [Windows PowerShell ISE Object Model Reference](The-ISE-Object-Model-Hierarchy.md).</span></span>

   - <span data-ttu-id="265e5-140">Para alterar o tamanho do tipo de letra para 20, no tipo de ficheiro de perfil: `$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="265e5-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="265e5-141">Para guardar o ficheiro de perfil, no **ficheiro** menu, clique em **guardar**.</span><span class="sxs-lookup"><span data-stu-id="265e5-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="265e5-142">Próxima vez que abrir o ISE do Windows PowerShell, as personalizações são aplicadas.</span><span class="sxs-lookup"><span data-stu-id="265e5-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="265e5-143">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="265e5-143">See Also</span></span>

- [<span data-ttu-id="265e5-144">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="265e5-144">about_Profiles</span></span>](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [<span data-ttu-id="265e5-145">Introdução ao ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="265e5-145">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)