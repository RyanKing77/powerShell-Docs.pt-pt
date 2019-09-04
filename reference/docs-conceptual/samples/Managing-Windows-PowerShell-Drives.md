---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Gerir Unidades do Windows PowerShell
ms.openlocfilehash: 5d1aba459caeaab2542e17e74534da6713b0faa9
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215518"
---
# <a name="managing-windows-powershell-drives"></a><span data-ttu-id="20143-103">Gerir Unidades do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="20143-103">Managing Windows PowerShell Drives</span></span>

<span data-ttu-id="20143-104">Uma *unidade do Windows PowerShell* é um local de armazenamento de dados que você pode acessar como uma unidade do sistema de arquivos no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20143-104">A *Windows PowerShell drive* is a data store location that you can access like a file system drive in Windows PowerShell.</span></span> <span data-ttu-id="20143-105">Os provedores do Windows PowerShell criam algumas unidades para você, como as unidades do sistema de arquivos (incluindo C: e D:), as unidades do registro (HKCU: e HKLM:), e a unidade de certificado (CERT:), e você pode criar suas próprias unidades do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20143-105">The Windows PowerShell providers create some drives for you, such as the file system drives (including C: and D:), the registry drives (HKCU: and HKLM:), and the certificate drive (Cert:), and you can create your own Windows PowerShell drives.</span></span> <span data-ttu-id="20143-106">Essas unidades são muito úteis, mas estão disponíveis apenas no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20143-106">These drives are very useful, but they are available only within Windows PowerShell.</span></span> <span data-ttu-id="20143-107">Você não pode acessá-los usando outras ferramentas do Windows, como o explorador de arquivos ou cmd. exe.</span><span class="sxs-lookup"><span data-stu-id="20143-107">You cannot access them by using other Windows tools, such as File Explorer or Cmd.exe.</span></span>

<span data-ttu-id="20143-108">O Windows PowerShell usa o substantivo, **PSDrive**, para comandos que funcionam com unidades do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20143-108">Windows PowerShell uses the noun, **PSDrive**, for commands that work with Windows PowerShell drives.</span></span> <span data-ttu-id="20143-109">Para obter uma lista das unidades do Windows PowerShell na sua sessão do Windows PowerShell, use o cmdlet **Get-PSDrive** .</span><span class="sxs-lookup"><span data-stu-id="20143-109">For a list of the Windows PowerShell drives in your Windows PowerShell session, use the **Get-PSDrive** cmdlet.</span></span>

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

<span data-ttu-id="20143-110">Embora as unidades na exibição variem de acordo com as unidades no seu sistema, a listagem será semelhante à saída do comando **Get-PSDrive** mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="20143-110">Although the drives in the display vary with the drives on your system, the listing will look similar to the output of the **Get-PSDrive** command shown above.</span></span>

<span data-ttu-id="20143-111">As unidades do sistema de arquivos são um subconjunto das unidades do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20143-111">File system drives are a subset of the Windows PowerShell drives.</span></span> <span data-ttu-id="20143-112">Você pode identificar as unidades do sistema de arquivos pela entrada FileSystem na coluna provedor.</span><span class="sxs-lookup"><span data-stu-id="20143-112">You can identify the file system drives by the FileSystem entry in the Provider column.</span></span> <span data-ttu-id="20143-113">(As unidades do sistema de arquivos no Windows PowerShell são suportadas pelo provedor do sistema de arquivos do Windows PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="20143-113">(The file system drives in Windows PowerShell are supported by the Windows PowerShell FileSystem provider.)</span></span>

<span data-ttu-id="20143-114">Para ver a sintaxe do cmdlet **Get-PSDrive** , digite um comando **Get-Command** com o parâmetro **Syntax** :</span><span class="sxs-lookup"><span data-stu-id="20143-114">To see the syntax of the **Get-PSDrive** cmdlet, type a **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

<span data-ttu-id="20143-115">O parâmetro **PSProvider** permite exibir apenas as unidades do Windows PowerShell com suporte em um provedor específico.</span><span class="sxs-lookup"><span data-stu-id="20143-115">The **PSProvider** parameter lets you display only the Windows PowerShell drives that are supported by a particular provider.</span></span> <span data-ttu-id="20143-116">Por exemplo, para exibir apenas as unidades do Windows PowerShell com suporte no provedor do sistema de arquivos do Windows PowerShell, digite um comando **Get-PSDrive** com o parâmetro **PSProvider** e o valor **FileSystem** :</span><span class="sxs-lookup"><span data-stu-id="20143-116">For example, to display only the Windows PowerShell drives that are supported by the Windows PowerShell FileSystem provider, type a **Get-PSDrive** command with the **PSProvider** parameter and the **FileSystem** value:</span></span>

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

<span data-ttu-id="20143-117">Para exibir as unidades do Windows PowerShell que representam os hives do registro, use o parâmetro **PSProvider** para exibir apenas as unidades do Windows PowerShell com suporte no provedor de registro do Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="20143-117">To view the Windows PowerShell drives that represent registry hives, use the **PSProvider** parameter to display only the Windows PowerShell drives that are supported by the Windows PowerShell Registry provider:</span></span>

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

<span data-ttu-id="20143-118">Você também pode usar os cmdlets de local padrão com as unidades do Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="20143-118">You can also use the standard Location cmdlets with the Windows PowerShell drives:</span></span>

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a><span data-ttu-id="20143-119">Adicionando novas unidades do Windows PowerShell (New-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="20143-119">Adding New Windows PowerShell Drives (New-PSDrive)</span></span>

<span data-ttu-id="20143-120">Você pode adicionar suas próprias unidades do Windows PowerShell usando o comando **New-PSDrive** .</span><span class="sxs-lookup"><span data-stu-id="20143-120">You can add your own Windows PowerShell drives by using the **New-PSDrive** command.</span></span> <span data-ttu-id="20143-121">Para obter a sintaxe para o comando **New-PSDrive** , insira o comando **Get-Command** com o parâmetro **Syntax** :</span><span class="sxs-lookup"><span data-stu-id="20143-121">To get the syntax for the **New-PSDrive** command, enter the **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

<span data-ttu-id="20143-122">Para criar uma nova unidade do Windows PowerShell, você deve fornecer três parâmetros:</span><span class="sxs-lookup"><span data-stu-id="20143-122">To create a new Windows PowerShell drive, you must supply three parameters:</span></span>

- <span data-ttu-id="20143-123">Um nome para a unidade (você pode usar qualquer nome do Windows PowerShell válido)</span><span class="sxs-lookup"><span data-stu-id="20143-123">A name for the drive (you can use any valid Windows PowerShell name)</span></span>

- <span data-ttu-id="20143-124">O PSProvider (use "FileSystem" para locais de sistema de arquivos e "registro" para locais de registro)</span><span class="sxs-lookup"><span data-stu-id="20143-124">The PSProvider (use "FileSystem" for file system locations and "Registry" for registry locations)</span></span>

- <span data-ttu-id="20143-125">A raiz, ou seja, o caminho para a raiz da nova unidade</span><span class="sxs-lookup"><span data-stu-id="20143-125">The root, that is, the path to the root of the new drive</span></span>

<span data-ttu-id="20143-126">Por exemplo, você pode criar uma unidade chamada "Office" que é mapeada para a pasta que contém os aplicativos Microsoft Office em seu computador, como **C:\\arquivos\\de programas Microsoft Office\\OFFICE11**.</span><span class="sxs-lookup"><span data-stu-id="20143-126">For example, you can create a drive named "Office" that is mapped to the folder that contains the Microsoft Office applications on your computer, such as **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span></span> <span data-ttu-id="20143-127">Para criar a unidade, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="20143-127">To create the drive, type the following command:</span></span>

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Microsoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> <span data-ttu-id="20143-128">Em geral, os caminhos não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="20143-128">In general, paths are not case-sensitive.</span></span>

<span data-ttu-id="20143-129">Você faz referência à nova unidade do Windows PowerShell à medida que todas as unidades do Windows PowerShell, por seu nome, seguido por dois-pontos ( **:** ).</span><span class="sxs-lookup"><span data-stu-id="20143-129">You refer to the new Windows PowerShell drive as you do all Windows PowerShell drives -- by its name followed by a colon (**:**).</span></span>

<span data-ttu-id="20143-130">Uma unidade do Windows PowerShell pode tornar muitas tarefas muito mais simples.</span><span class="sxs-lookup"><span data-stu-id="20143-130">A Windows PowerShell drive can make many tasks much simpler.</span></span> <span data-ttu-id="20143-131">Por exemplo, algumas das chaves mais importantes no registro do Windows têm caminhos extremamente longos, tornando-os difíceis de serem acessados e difíceis de se lembrar.</span><span class="sxs-lookup"><span data-stu-id="20143-131">For example, some of the most important keys in the Windows registry have extremely long paths, making them cumbersome to access and difficult to remember.</span></span> <span data-ttu-id="20143-132">As informações de configuração críticas residem **em\\HKEY_LOCAL_MACHINE\\software\\Microsoft\\Windows CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="20143-132">Critical configuration information resides under **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span> <span data-ttu-id="20143-133">Para exibir e alterar itens na chave do registro CurrentVersion, você pode criar uma unidade do Windows PowerShell com raiz nessa chave digitando:</span><span class="sxs-lookup"><span data-stu-id="20143-133">To view and change items in the CurrentVersion registry key, you can create a Windows PowerShell drive that is rooted in that key by typing:</span></span>

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\Windows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

<span data-ttu-id="20143-134">Em seguida, você pode alterar o local para a unidade **unidade cvkey:** como faria com qualquer outra unidade:</span><span class="sxs-lookup"><span data-stu-id="20143-134">You can then change location to the **cvkey:** drive as you would any other drive:</span></span>

```
PS> cd cvkey:
```

<span data-ttu-id="20143-135">ou:</span><span class="sxs-lookup"><span data-stu-id="20143-135">or:</span></span>

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

<span data-ttu-id="20143-136">O cmdlet New-PsDrive adiciona a nova unidade somente à sessão atual do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20143-136">The New-PsDrive cmdlet adds the new drive only to the current Windows PowerShell session.</span></span> <span data-ttu-id="20143-137">Se você fechar a janela do Windows PowerShell, a nova unidade será perdida.</span><span class="sxs-lookup"><span data-stu-id="20143-137">If you close the Windows PowerShell window, the new drive is lost.</span></span> <span data-ttu-id="20143-138">Para salvar uma unidade do Windows PowerShell, use o cmdlet Export-Console para exportar a sessão atual do Windows PowerShell e, em seguida, use o parâmetro **PSConsoleFile** do PowerShell. exe para importá-la.</span><span class="sxs-lookup"><span data-stu-id="20143-138">To save a Windows PowerShell drive, use the Export-Console cmdlet to export the current Windows PowerShell session, and then use the PowerShell.exe **PSConsoleFile** parameter to import it.</span></span> <span data-ttu-id="20143-139">Ou adicione a nova unidade ao seu perfil do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20143-139">Or, add the new drive to your Windows PowerShell profile.</span></span>

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a><span data-ttu-id="20143-140">Excluindo unidades do Windows PowerShell (Remove-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="20143-140">Deleting Windows PowerShell Drives (Remove-PSDrive)</span></span>

<span data-ttu-id="20143-141">Você pode excluir unidades do Windows PowerShell usando o cmdlet **Remove-PSDrive** .</span><span class="sxs-lookup"><span data-stu-id="20143-141">You can delete drives from Windows PowerShell by using the **Remove-PSDrive** cmdlet.</span></span> <span data-ttu-id="20143-142">O cmdlet **Remove-PSDrive** é fácil de usar; para excluir uma unidade específica do Windows PowerShell, basta fornecer o nome da unidade do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20143-142">The **Remove-PSDrive** cmdlet is easy to use; to delete a specific Windows PowerShell drive, you just supply the Windows PowerShell drive name.</span></span>

<span data-ttu-id="20143-143">Por exemplo, se você adicionou o **escritório:** Unidade do Windows PowerShell, conforme mostrado no tópico **New-PSDrive** , você pode excluí-lo digitando:</span><span class="sxs-lookup"><span data-stu-id="20143-143">For example, if you added the **Office:** Windows PowerShell drive, as shown in the **New-PSDrive** topic, you can delete it by typing:</span></span>

```powershell
Remove-PSDrive -Name Office
```

<span data-ttu-id="20143-144">Para excluir o **unidade cvkey:** Unidade do Windows PowerShell, também mostrada no tópico **New-PSDrive** , use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="20143-144">To delete the **cvkey:** Windows PowerShell drive, also shown in the **New-PSDrive** topic, use the following command:</span></span>

```powershell
Remove-PSDrive -Name cvkey
```

<span data-ttu-id="20143-145">É fácil excluir uma unidade do Windows PowerShell, mas você não pode excluí-la enquanto estiver na unidade.</span><span class="sxs-lookup"><span data-stu-id="20143-145">It's easy to delete a Windows PowerShell drive, but you can't delete it while you are in the drive.</span></span> <span data-ttu-id="20143-146">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="20143-146">For example:</span></span>

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a><span data-ttu-id="20143-147">Adicionando e removendo unidades fora do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="20143-147">Adding and Removing Drives Outside Windows PowerShell</span></span>

<span data-ttu-id="20143-148">O Windows PowerShell detecta unidades de sistema de arquivos que são adicionadas ou removidas no Windows, incluindo unidades de rede mapeadas, unidades USB que são anexadas e unidades que são excluídas usando o comando **net use** ou o  **Métodos WScript. NetworkMapNetworkDrive** e **RemoveNetworkDrive** de um script do WSH (Windows Script Host).</span><span class="sxs-lookup"><span data-stu-id="20143-148">Windows PowerShell detects file system drives that are added or removed in Windows, including network drives that are mapped, USB drives that are attached, and drives that are deleted by using either the **net use** command or the **WScript.NetworkMapNetworkDrive** and **RemoveNetworkDrive** methods from a Windows Script Host (WSH) script.</span></span>
