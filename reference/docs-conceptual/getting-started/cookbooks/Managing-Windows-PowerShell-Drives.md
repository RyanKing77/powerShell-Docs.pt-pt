---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Gerir Unidades do Windows PowerShell
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
ms.openlocfilehash: cfc5418e9d2efb1a786817e1b941d75e22291742
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951873"
---
# <a name="managing-windows-powershell-drives"></a><span data-ttu-id="3195b-103">Gerir Unidades do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3195b-103">Managing Windows PowerShell Drives</span></span>

<span data-ttu-id="3195b-104">A *unidade do Windows PowerShell* for uma localização de arquivo de dados que pode aceder a como uma unidade de sistema de ficheiros no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3195b-104">A *Windows PowerShell drive* is a data store location that you can access like a file system drive in Windows PowerShell.</span></span> <span data-ttu-id="3195b-105">Os fornecedores do Windows PowerShell criar algumas unidades para si, tais como unidades de sistema de ficheiros (incluindo c e d:), o registo unidades (HKCU: e HKLM:) e a unidade de certificado (Cert:), e pode criar as seus próprios unidades do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3195b-105">The Windows PowerShell providers create some drives for you, such as the file system drives (including C: and D:), the registry drives (HKCU: and HKLM:), and the certificate drive (Cert:), and you can create your own Windows PowerShell drives.</span></span> <span data-ttu-id="3195b-106">Estas unidades são muito úteis, mas estão disponíveis apenas dentro do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3195b-106">These drives are very useful, but they are available only within Windows PowerShell.</span></span> <span data-ttu-id="3195b-107">Não é possível aceder-lhes com outras ferramentas do Windows, tais como o Explorador de ficheiros ou Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="3195b-107">You cannot access them by using other Windows tools, such as File Explorer or Cmd.exe.</span></span>

<span data-ttu-id="3195b-108">O Windows PowerShell utiliza o substantivo **PSDrive**, para comandos que funcionam com o Windows PowerShell unidades.</span><span class="sxs-lookup"><span data-stu-id="3195b-108">Windows PowerShell uses the noun, **PSDrive**, for commands that work with Windows PowerShell drives.</span></span> <span data-ttu-id="3195b-109">Para obter uma lista do Windows PowerShell unidades na sessão do Windows PowerShell, utilize o **Get-PSDrive** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3195b-109">For a list of the Windows PowerShell drives in your Windows PowerShell session, use the **Get-PSDrive** cmdlet.</span></span>

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

<span data-ttu-id="3195b-110">Embora as unidades na apresentação do variar de acordo com as unidades no seu sistema, a listagem terá um aspeto semelhante à saída do **Get-PSDrive** comando mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="3195b-110">Although the drives in the display vary with the drives on your system, the listing will look similar to the output of the **Get-PSDrive** command shown above.</span></span>

<span data-ttu-id="3195b-111">Unidades de sistema de ficheiros são um subconjunto das unidades do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3195b-111">File system drives are a subset of the Windows PowerShell drives.</span></span> <span data-ttu-id="3195b-112">Pode identificar as unidades de sistema de ficheiros pela entrada de sistema de ficheiros na coluna de fornecedor.</span><span class="sxs-lookup"><span data-stu-id="3195b-112">You can identify the file system drives by the FileSystem entry in the Provider column.</span></span> <span data-ttu-id="3195b-113">(As unidades de sistema de ficheiros no Windows PowerShell são suportadas pelo fornecedor de sistema de ficheiros do Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="3195b-113">(The file system drives in Windows PowerShell are supported by the Windows PowerShell FileSystem provider.)</span></span>

<span data-ttu-id="3195b-114">Para ver a sintaxe do **Get-PSDrive** cmdlet, escreva um **Get-Command** comando com o **sintaxe** parâmetro:</span><span class="sxs-lookup"><span data-stu-id="3195b-114">To see the syntax of the **Get-PSDrive** cmdlet, type a **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

<span data-ttu-id="3195b-115">O **PSProvider** permite parâmetro apresentar apenas as unidades do Windows PowerShell que é suportados por um fornecedor específico.</span><span class="sxs-lookup"><span data-stu-id="3195b-115">The **PSProvider** parameter lets you display only the Windows PowerShell drives that are supported by a particular provider.</span></span> <span data-ttu-id="3195b-116">Por exemplo, para visualizar apenas as unidades do Windows PowerShell que são suportadas pelo fornecedor de sistema de ficheiros do Windows PowerShell, digite um **Get-PSDrive** comando com o **PSProvider** parâmetro e o  **Sistema de ficheiros** valor:</span><span class="sxs-lookup"><span data-stu-id="3195b-116">For example, to display only the Windows PowerShell drives that are supported by the Windows PowerShell FileSystem provider, type a **Get-PSDrive** command with the **PSProvider** parameter and the **FileSystem** value:</span></span>

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

<span data-ttu-id="3195b-117">Para ver as unidades do Windows PowerShell que representam nos ramos de registo, utilize o **PSProvider** parâmetro para visualizar apenas as unidades do Windows PowerShell que são suportados pelo fornecedor de registo do Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="3195b-117">To view the Windows PowerShell drives that represent registry hives, use the **PSProvider** parameter to display only the Windows PowerShell drives that are supported by the Windows PowerShell Registry provider:</span></span>

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

<span data-ttu-id="3195b-118">Também pode utilizar os cmdlets de localização padrão com as unidades do Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="3195b-118">You can also use the standard Location cmdlets with the Windows PowerShell drives:</span></span>

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

### <a name="adding-new-windows-powershell-drives-new-psdrive"></a><span data-ttu-id="3195b-119">Adicionar novo do Windows PowerShell unidades (novo PSDrive)</span><span class="sxs-lookup"><span data-stu-id="3195b-119">Adding New Windows PowerShell Drives (New-PSDrive)</span></span>

<span data-ttu-id="3195b-120">Pode adicionar as seus próprios unidades do Windows PowerShell utilizando o **New-PSDrive** comando.</span><span class="sxs-lookup"><span data-stu-id="3195b-120">You can add your own Windows PowerShell drives by using the **New-PSDrive** command.</span></span> <span data-ttu-id="3195b-121">Para obter a sintaxe para o **New-PSDrive** de comandos, introduza o **Get-Command** comando com o **sintaxe** parâmetro:</span><span class="sxs-lookup"><span data-stu-id="3195b-121">To get the syntax for the **New-PSDrive** command, enter the **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

<span data-ttu-id="3195b-122">Para criar uma nova unidade do Windows PowerShell, tem de fornecer três parâmetros:</span><span class="sxs-lookup"><span data-stu-id="3195b-122">To create a new Windows PowerShell drive, you must supply three parameters:</span></span>

- <span data-ttu-id="3195b-123">Um nome para a unidade (pode utilizar qualquer nome válido do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="3195b-123">A name for the drive (you can use any valid Windows PowerShell name)</span></span>

- <span data-ttu-id="3195b-124">O PSProvider (utilize "Sistema de ficheiros" para as localizações do sistema de ficheiros e "Registo de" para as localizações de registo)</span><span class="sxs-lookup"><span data-stu-id="3195b-124">The PSProvider (use "FileSystem" for file system locations and "Registry" for registry locations)</span></span>

- <span data-ttu-id="3195b-125">A raiz, ou seja, o caminho para a raiz da unidade de novo</span><span class="sxs-lookup"><span data-stu-id="3195b-125">The root, that is, the path to the root of the new drive</span></span>

<span data-ttu-id="3195b-126">Por exemplo, pode criar uma unidade com o nome "Office" que está mapeado para a pasta que contém as aplicações do Microsoft Office no seu computador, tal como **c:\\os ficheiros de programa\\Microsoft Office\\OFFICE11**.</span><span class="sxs-lookup"><span data-stu-id="3195b-126">For example, you can create a drive named "Office" that is mapped to the folder that contains the Microsoft Office applications on your computer, such as **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span></span> <span data-ttu-id="3195b-127">Para criar a unidade, escreva o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="3195b-127">To create the drive, type the following command:</span></span>

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> <span data-ttu-id="3195b-128">Em geral, os caminhos não são maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="3195b-128">In general, paths are not case-sensitive.</span></span>

<span data-ttu-id="3195b-129">Consulte para a nova unidade do Windows PowerShell de forma que todas as unidades do Windows PowerShell – pelo respetivo nome seguido de dois pontos (**:**).</span><span class="sxs-lookup"><span data-stu-id="3195b-129">You refer to the new Windows PowerShell drive as you do all Windows PowerShell drives -- by its name followed by a colon (**:**).</span></span>

<span data-ttu-id="3195b-130">Uma unidade do Windows PowerShell pode efetuar muitas tarefas muito mais simples.</span><span class="sxs-lookup"><span data-stu-id="3195b-130">A Windows PowerShell drive can make many tasks much simpler.</span></span> <span data-ttu-id="3195b-131">Por exemplo, algumas das chaves mais importantes no registo do Windows têm caminhos extremamente longos, torná-los complexa para o acesso e difíceis de lembrar-se.</span><span class="sxs-lookup"><span data-stu-id="3195b-131">For example, some of the most important keys in the Windows registry have extremely long paths, making them cumbersome to access and difficult to remember.</span></span> <span data-ttu-id="3195b-132">Informações de configuração críticas residem em **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="3195b-132">Critical configuration information resides under **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span> <span data-ttu-id="3195b-133">Para ver e alterar os itens na chave do registo CurrentVersion, pode criar uma unidade do Windows PowerShell que é ROOT nessa chave escrevendo:</span><span class="sxs-lookup"><span data-stu-id="3195b-133">To view and change items in the CurrentVersion registry key, you can create a Windows PowerShell drive that is rooted in that key by typing:</span></span>

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

<span data-ttu-id="3195b-134">Em seguida, pode alterar a localização para o **cvkey:** unidade como faria com qualquer outra unidade: '</span><span class="sxs-lookup"><span data-stu-id="3195b-134">You can then change location to the **cvkey:** drive as you would any other drive:``</span></span>

`PS> cd cvkey:`

<span data-ttu-id="3195b-135">ou:</span><span class="sxs-lookup"><span data-stu-id="3195b-135">or:</span></span>

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

<span data-ttu-id="3195b-136">O cmdlet New-PsDrive adiciona a nova unidade, apenas para a sessão atual do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3195b-136">The New-PsDrive cmdlet adds the new drive only to the current Windows PowerShell session.</span></span> <span data-ttu-id="3195b-137">Se fechar a janela do Windows PowerShell, a nova unidade é perdida.</span><span class="sxs-lookup"><span data-stu-id="3195b-137">If you close the Windows PowerShell window, the new drive is lost.</span></span> <span data-ttu-id="3195b-138">Para guardar uma unidade do Windows PowerShell, utilize o cmdlet Export-consola para exportar a sessão atual do Windows PowerShell e, em seguida, utilize o PowerShell.exe **PSConsoleFile** parâmetro importá-la.</span><span class="sxs-lookup"><span data-stu-id="3195b-138">To save a Windows PowerShell drive, use the Export-Console cmdlet to export the current Windows PowerShell session, and then use the PowerShell.exe **PSConsoleFile** parameter to import it.</span></span> <span data-ttu-id="3195b-139">Em alternativa, adicionar a unidade de novo para o seu perfil do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3195b-139">Or, add the new drive to your Windows PowerShell profile.</span></span>

### <a name="deleting-windows-powershell-drives-remove-psdrive"></a><span data-ttu-id="3195b-140">A eliminação do Windows PowerShell unidades (remover-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="3195b-140">Deleting Windows PowerShell Drives (Remove-PSDrive)</span></span>

<span data-ttu-id="3195b-141">Pode eliminar unidades do Windows PowerShell utilizando o **remover PSDrive** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3195b-141">You can delete drives from Windows PowerShell by using the **Remove-PSDrive** cmdlet.</span></span> <span data-ttu-id="3195b-142">O **remover PSDrive** cmdlet é fácil de utilizar; para eliminar a unidade do Windows PowerShell específica, basta fornecer o nome da unidade do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3195b-142">The **Remove-PSDrive** cmdlet is easy to use; to delete a specific Windows PowerShell drive, you just supply the Windows PowerShell drive name.</span></span>

<span data-ttu-id="3195b-143">Por exemplo, se tiver adicionado o **Office:** unidade do Windows PowerShell, conforme mostrado no **New-PSDrive** tópico, que pode eliminá-lo escrevendo:</span><span class="sxs-lookup"><span data-stu-id="3195b-143">For example, if you added the **Office:** Windows PowerShell drive, as shown in the **New-PSDrive** topic, you can delete it by typing:</span></span>

```powershell
Remove-PSDrive -Name Office
```

<span data-ttu-id="3195b-144">Para eliminar o **cvkey:** do Windows PowerShell de unidade, também apresentado no **New-PSDrive** tópico, utilize o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="3195b-144">To delete the **cvkey:** Windows PowerShell drive, also shown in the **New-PSDrive** topic, use the following command:</span></span>

```powershell
Remove-PSDrive -Name cvkey
```

<span data-ttu-id="3195b-145">É mais fácil eliminar uma unidade do Windows PowerShell, mas não é possível eliminar enquanto estiver na unidade.</span><span class="sxs-lookup"><span data-stu-id="3195b-145">It's easy to delete a Windows PowerShell drive, but you can't delete it while you are in the drive.</span></span> <span data-ttu-id="3195b-146">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="3195b-146">For example:</span></span>

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

### <a name="adding-and-removing-drives-outside-windows-powershell"></a><span data-ttu-id="3195b-147">Adicionar e remover unidades fora do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3195b-147">Adding and Removing Drives Outside Windows PowerShell</span></span>

<span data-ttu-id="3195b-148">Windows PowerShell Deteta as unidades do sistema de ficheiros que são adicionadas ou removidas no Windows, incluindo unidades de rede que estão mapeadas, unidades USB ligadas e unidades são eliminadas utilizando o **net utilize** comando ou o  **WScript.NetworkMapNetworkDrive** e **RemoveNetworkDrive** métodos de um script de Script anfitrião para WSH (Windows).</span><span class="sxs-lookup"><span data-stu-id="3195b-148">Windows PowerShell detects file system drives that are added or removed in Windows, including network drives that are mapped, USB drives that are attached, and drives that are deleted by using either the **net use** command or the **WScript.NetworkMapNetworkDrive** and **RemoveNetworkDrive** methods from a Windows Script Host (WSH) script.</span></span>