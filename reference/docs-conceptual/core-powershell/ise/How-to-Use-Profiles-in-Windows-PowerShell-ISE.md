---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Como utilizar perfis no ISE do Windows PowerShell
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: f959aeb91eecc8056c91c56162ea9bff53537be9
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="0c14b-103">Como utilizar perfis no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c14b-103">How to Use Profiles in Windows PowerShell ISE</span></span>
<span data-ttu-id="0c14b-104">Este tópico explica como utilizar perfis no Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="0c14b-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="0c14b-105">Recomendamos que antes de executar as tarefas nesta secção, consulte o artigo [about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630)), ou no painel de consola, tipo, `Get-Help about_Profiles` e prima **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="0c14b-105">We recommend that before performing the tasks in this section, you review [about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630)), or in the Console Pane, type, `Get-Help about_Profiles` and press **ENTER**.</span></span>

<span data-ttu-id="0c14b-106">Um perfil é um script de ISE do Windows PowerShell que é executado automaticamente quando iniciar uma nova sessão.</span><span class="sxs-lookup"><span data-stu-id="0c14b-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>  <span data-ttu-id="0c14b-107">Pode criar um ou mais perfis do Windows PowerShell para o ISE do Windows PowerShell e utilizá-los para adicionar a configurar o ambiente do Windows PowerShell ou o ISE do Windows PowerShell, prepará-lo para utilização, com variáveis, aliases, funções e cor e o tipo de letra preferências que pretende que sejam disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0c14b-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="0c14b-108">Um perfil afeta cada sessão de ISE do Windows PowerShell que pode inicia.</span><span class="sxs-lookup"><span data-stu-id="0c14b-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="0c14b-109">A política de execução do Windows PowerShell determina se pode executar scripts e um perfil de carga.</span><span class="sxs-lookup"><span data-stu-id="0c14b-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span> <span data-ttu-id="0c14b-110">A política de execução da predefinição "Restrito," impedem que todos os scripts sejam executados, incluindo perfis.</span><span class="sxs-lookup"><span data-stu-id="0c14b-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span> <span data-ttu-id="0c14b-111">Se utilizar a política de "Restrito", não é possível carregar o perfil.</span><span class="sxs-lookup"><span data-stu-id="0c14b-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="0c14b-112">Para obter mais informações sobre a política de execução, consulte [about_Execution_Policies [v4]](https://technet.microsoft.com/library/347708dc-1515-4d74-978b-8334603472e6(v=wps.630)).</span><span class="sxs-lookup"><span data-stu-id="0c14b-112">For more information about execution policy, see [about_Execution_Policies [v4]](https://technet.microsoft.com/library/347708dc-1515-4d74-978b-8334603472e6(v=wps.630)).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="0c14b-113">Selecionar um perfil para utilizar no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c14b-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>
<span data-ttu-id="0c14b-114">ISE do Windows PowerShell suporta perfis para o utilizador atual e todos os utilizadores.</span><span class="sxs-lookup"><span data-stu-id="0c14b-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="0c14b-115">Também suporta os perfis do Windows PowerShell que se aplicam a todos os anfitriões.</span><span class="sxs-lookup"><span data-stu-id="0c14b-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="0c14b-116">O perfil que utiliza é determinado pelo como utilizar o Windows PowerShell e o ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c14b-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="0c14b-117">Se utilizar apenas ISE do Windows PowerShell para executar o Windows PowerShell, em seguida, guarde a todos os seus itens dos perfis de ISE específicas, tais como o perfil de CurrentUserCurrentHost para ISE do Windows PowerShell ou o perfil de AllUsersCurrentHost para ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c14b-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the CurrentUserCurrentHost profile for Windows PowerShell ISE or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="0c14b-118">Se utilizar vários programas de anfitrião para executar o Windows PowerShell, guarde a funções, aliases, variáveis e os comandos num perfil que afeta todos os programas de anfitrião, como o CurrentUserAllHosts ou no perfil de AllUsersAllHosts e guardar funcionalidades específicas do ISE, como cor e o tipo de letra personalização no perfil de CurrentUserCurrentHost para perfil do ISE do Windows PowerShell ou o perfil de AllUsersCurrentHost para ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c14b-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the AllUsersAllHosts profile, and save ISE-specific features, like color and font customization in the CurrentUserCurrentHost profile for Windows PowerShell ISE profile or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="0c14b-119">Seguem-se perfis que podem ser criados e utilizados no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c14b-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="0c14b-120">Cada perfil é guardado para a sua própria caminho específico.</span><span class="sxs-lookup"><span data-stu-id="0c14b-120">Each profile is saved to its own specific path.</span></span>

| <span data-ttu-id="0c14b-121">Tipo de perfil</span><span class="sxs-lookup"><span data-stu-id="0c14b-121">Profile Type</span></span> | <span data-ttu-id="0c14b-122">Caminho do perfil</span><span class="sxs-lookup"><span data-stu-id="0c14b-122">Profile Path</span></span> |
| --- | --- |
| <span data-ttu-id="0c14b-123">**Utilizador atual, o ISE do PowerShell**</span><span class="sxs-lookup"><span data-stu-id="0c14b-123">**Current user, PowerShell ISE**</span></span>| <span data-ttu-id="0c14b-124">`$PROFILE.CurrentUserCurrentHost`, ou`$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="0c14b-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="0c14b-125">**Todos os utilizadores, ISE do PowerShell**</span><span class="sxs-lookup"><span data-stu-id="0c14b-125">**All users, PowerShell ISE**</span></span>| `$PROFILE.AllUsersCurrentHost` |
| <span data-ttu-id="0c14b-126">**Utilizador atual, todos os anfitriões**</span><span class="sxs-lookup"><span data-stu-id="0c14b-126">**Current user, All hosts**</span></span>| `$PROFILE.CurrentUserAllHosts` |
| <span data-ttu-id="0c14b-127">**Todos os utilizadores, todos os anfitriões**</span><span class="sxs-lookup"><span data-stu-id="0c14b-127">**All users, All hosts**</span></span> | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="0c14b-128">Para criar um novo perfil</span><span class="sxs-lookup"><span data-stu-id="0c14b-128">To create a new profile</span></span>
<span data-ttu-id="0c14b-129">Para criar um nova "utilizador atual, ISE do Windows PowerShell" perfil, execute este comando:</span><span class="sxs-lookup"><span data-stu-id="0c14b-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE )) 
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="0c14b-130">Para criar uma nova "Todos os utilizadores, ISE do Windows PowerShell" perfil, execute este comando:</span><span class="sxs-lookup"><span data-stu-id="0c14b-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost)) 
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="0c14b-131">Para criar um novo perfil "utilizador atual, todos os anfitriões", execute este comando:</span><span class="sxs-lookup"><span data-stu-id="0c14b-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts)) 
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="0c14b-132">Para criar um novo perfil "todos os utilizadores, todos os anfitriões", escreva:</span><span class="sxs-lookup"><span data-stu-id="0c14b-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts)) 
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="0c14b-133">Para editar um perfil</span><span class="sxs-lookup"><span data-stu-id="0c14b-133">To edit a profile</span></span>

1. <span data-ttu-id="0c14b-134">Para abrir o perfil, execute o comando psedit com a variável que especifica o perfil que pretende editar.</span><span class="sxs-lookup"><span data-stu-id="0c14b-134">To open the profile, run the command psedit with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="0c14b-135">Por exemplo, para abrir o "utilizador atual, ISE do Windows PowerShell" perfil, escreva:`psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="0c14b-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="0c14b-136">Adicione alguns itens para o seu perfil.</span><span class="sxs-lookup"><span data-stu-id="0c14b-136">Add some items to your profile.</span></span> <span data-ttu-id="0c14b-137">Seguem-se alguns exemplos para ajudar a começar:</span><span class="sxs-lookup"><span data-stu-id="0c14b-137">The following are a few examples to get you started:</span></span>

    -   <span data-ttu-id="0c14b-138">Para alterar a cor de fundo predefinido do painel de consola para azul, no tipo de ficheiro de perfil: `$psISE.Options.OutputPaneBackground = 'blue'` .</span><span class="sxs-lookup"><span data-stu-id="0c14b-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="0c14b-139">Para mais informações sobre a variável de $psISE, consulte [referência de modelo de objeto do Windows PowerShell ISE](The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="0c14b-139">For more information about the $psISE variable, see [Windows PowerShell ISE Object Model Reference](The-ISE-Object-Model-Hierarchy.md).</span></span>

    -   <span data-ttu-id="0c14b-140">Para alterar o tamanho do tipo de letra para 20, no tipo de ficheiro de perfil:`$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="0c14b-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="0c14b-141">Para guardar o ficheiro de perfil, no **ficheiro** menu, clique em **guardar**.</span><span class="sxs-lookup"><span data-stu-id="0c14b-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="0c14b-142">Próxima vez que abrir o ISE do Windows PowerShell, as personalizações são aplicadas.</span><span class="sxs-lookup"><span data-stu-id="0c14b-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c14b-143">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="0c14b-143">See Also</span></span>
- <span data-ttu-id="0c14b-144">[about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630))</span><span class="sxs-lookup"><span data-stu-id="0c14b-144">[about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630))</span></span>
- [<span data-ttu-id="0c14b-145">Utilizar o ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c14b-145">Using the Windows PowerShell ISE</span></span>](Using-the-Windows-PowerShell-ISE.md)

