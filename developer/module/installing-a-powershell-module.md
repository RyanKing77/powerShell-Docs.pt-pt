---
title: Instalar um módulo do PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: 7c2bfca50de4645676eafc01bbf23d9797e8b758
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059784"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="d9531-102">Installing a PowerShell Module (Instalar um Módulo do PowerShell)</span><span class="sxs-lookup"><span data-stu-id="d9531-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="d9531-103">Depois de criar o módulo do PowerShell, provavelmente desejará instalar o módulo num sistema, para que ou outros poderão utilizá-lo.</span><span class="sxs-lookup"><span data-stu-id="d9531-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="d9531-104">Em termos gerais, isso simplesmente consiste em copiar os módulo arquivos (ie, psm1, ou a assemblagem binária, o manifesto de módulo e todos os outros ficheiros associados) num diretório nesse computador.</span><span class="sxs-lookup"><span data-stu-id="d9531-104">Generally speaking, this simply consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="d9531-105">Para um projeto muito pequeno, isso pode ser tão simples quanto copiar e colar os ficheiros com o Explorador do Windows num único computador remoto; No entanto, para soluções maiores poderá querer utilizar um processo de instalação mais sofisticado.</span><span class="sxs-lookup"><span data-stu-id="d9531-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="d9531-106">Independentemente de como obter o seu módulo no sistema, o PowerShell pode usar várias técnicas que permitirá que os usuários a encontrar e utilizar os módulos.</span><span class="sxs-lookup"><span data-stu-id="d9531-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="d9531-107">(Para obter mais informações, consulte [importar um módulo do PowerShell](./importing-a-powershell-module.md).) Por conseguinte, o problema principal para a instalação é garantir que o PowerShell poderá encontrar seu módulo.</span><span class="sxs-lookup"><span data-stu-id="d9531-107">(For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).) Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span>

<span data-ttu-id="d9531-108">Este tópico contém as seguintes secções:</span><span class="sxs-lookup"><span data-stu-id="d9531-108">This topic contains the following sections:</span></span>

- <span data-ttu-id="d9531-109">Regras para a instalação de módulos</span><span class="sxs-lookup"><span data-stu-id="d9531-109">Rules for Installing Modules</span></span>

- <span data-ttu-id="d9531-110">Onde instalar os módulos</span><span class="sxs-lookup"><span data-stu-id="d9531-110">Where to Install Modules</span></span>

- <span data-ttu-id="d9531-111">Instalação de várias versões de um módulo</span><span class="sxs-lookup"><span data-stu-id="d9531-111">Installing Multiple Versions of a Module</span></span>

- <span data-ttu-id="d9531-112">Manipulação de conflitos de nomes de comando</span><span class="sxs-lookup"><span data-stu-id="d9531-112">Handling Command Name Conflicts</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="d9531-113">Regras para a instalação de módulos</span><span class="sxs-lookup"><span data-stu-id="d9531-113">Rules for Installing Modules</span></span>

<span data-ttu-id="d9531-114">As seguintes informações pertence a todos os módulos, incluindo módulos que criar para o seu próprio uso, módulos que obtém a partir de outras entidades e módulos que distribui a outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="d9531-114">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="d9531-115">Instalar os módulos no PSModulePath</span><span class="sxs-lookup"><span data-stu-id="d9531-115">Install Modules in PSModulePath</span></span>

<span data-ttu-id="d9531-116">Sempre que possível, instale todos os módulos num caminho que está listado na **PSModulePath** variável de ambiente ou adicionar o caminho do módulo para o **PSModulePath** valor da variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="d9531-116">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="d9531-117">O **PSModulePath** variável de ambiente ($Env: PSModulePath) contém os locais dos módulos do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d9531-117">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="d9531-118">Cmdlets baseiam-se no valor desta variável de ambiente para localizar os módulos.</span><span class="sxs-lookup"><span data-stu-id="d9531-118">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="d9531-119">Por predefinição, o **PSModulePath** valor da variável de ambiente contém o sistema seguinte e os diretórios de módulo de usuário, mas pode adicionar e editar o valor.</span><span class="sxs-lookup"><span data-stu-id="d9531-119">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="d9531-120">$PSHome\Modules (% Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="d9531-120">$PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="d9531-121">Esta localização é reservada para módulos que acompanham o Windows.</span><span class="sxs-lookup"><span data-stu-id="d9531-121">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="d9531-122">Não instale módulos para esta localização.</span><span class="sxs-lookup"><span data-stu-id="d9531-122">Do not install modules to this location.</span></span>

- <span data-ttu-id="d9531-123">$Home\Documents\WindowsPowerShell\Modules (%UserProfile%\Documents\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="d9531-123">$Home\Documents\WindowsPowerShell\Modules (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="d9531-124">$Env: ProgramFiles\WindowsPowerShell\Modules (% ProgramFiles%\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="d9531-124">$Env:ProgramFiles\WindowsPowerShell\Modules (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="d9531-125">Para obter o valor do **PSModulePath** variável de ambiente, utilizar qualquer um dos seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="d9531-125">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="d9531-126">Para adicionar um caminho de módulo ao valor do **PSModulePath** variável de ambiente de valor, utilize o seguinte formato de comando.</span><span class="sxs-lookup"><span data-stu-id="d9531-126">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="d9531-127">Este formato utiliza o **SetEnvironmentVariable** método da **System.Environment** classe fazer uma alteração de sessão independente para o **PSModulePath** ambiente variável.</span><span class="sxs-lookup"><span data-stu-id="d9531-127">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell

  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="d9531-128">Depois de adicionar o caminho para **PSModulePath**, deve difundir uma mensagem de ambiente sobre a alteração.</span><span class="sxs-lookup"><span data-stu-id="d9531-128">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="d9531-129">A alteração a difundir permite que os outros aplicativos, como o shell, captará a alteração.</span><span class="sxs-lookup"><span data-stu-id="d9531-129">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="d9531-130">Para a alteração de difusão, ter seu código de instalação do produto enviar um **WM_SETTINGCHANGE** mensagem com `lParam` definido como a cadeia de caracteres "Ambiente".</span><span class="sxs-lookup"><span data-stu-id="d9531-130">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="d9531-131">Certifique-se de que enviar a mensagem depois do seu código de instalação do módulo atualizou **PSModulePath**.</span><span class="sxs-lookup"><span data-stu-id="d9531-131">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="d9531-132">Utilize o nome de diretório de módulo correto</span><span class="sxs-lookup"><span data-stu-id="d9531-132">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="d9531-133">Um módulo "bem formado" é um módulo que esteja armazenado num diretório com o mesmo nome que o nome de base pelo menos um ficheiro no diretório de módulo.</span><span class="sxs-lookup"><span data-stu-id="d9531-133">A "well-formed" module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="d9531-134">Se um módulo não está formado, Windows PowerShell não o reconhece como um módulo.</span><span class="sxs-lookup"><span data-stu-id="d9531-134">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="d9531-135">O "nome de base" de um ficheiro é o nome sem a extensão de nome de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="d9531-135">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="d9531-136">Num módulo bem formado, o nome do diretório que contém os ficheiros de módulo tem de corresponder ao nome de base pelo menos um ficheiro no módulo.</span><span class="sxs-lookup"><span data-stu-id="d9531-136">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="d9531-137">Por exemplo, o módulo da Fabrikam de exemplo, o diretório que contém os ficheiros de módulo com o nome "Fabrikam" e pelo menos um ficheiro com o nome de base de "Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="d9531-137">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="d9531-138">Neste caso, Fabrikam.psd1 e Fabrikam.dll tem o nome de base "Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="d9531-138">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="d9531-139">Efeito da instalação incorreta</span><span class="sxs-lookup"><span data-stu-id="d9531-139">Effect of Incorrect Installation</span></span>

<span data-ttu-id="d9531-140">Se o módulo não está bem formado e a localização não está incluída no valor dos **PSModulePath** variável de ambiente, funcionalidades de deteção básica do Windows PowerShell, como a seguir, não funcionam.</span><span class="sxs-lookup"><span data-stu-id="d9531-140">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="d9531-141">A funcionalidade de carregamento de módulo automática não é possível importar o módulo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d9531-141">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="d9531-142">O `ListAvailable` parâmetro do [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet não é possível localizar o módulo.</span><span class="sxs-lookup"><span data-stu-id="d9531-142">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="d9531-143">O [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet não é possível localizar o módulo.</span><span class="sxs-lookup"><span data-stu-id="d9531-143">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="d9531-144">Para importar o módulo, tem de fornecer o caminho completo para o ficheiro do módulo de raiz ou o ficheiro de manifesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="d9531-144">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="d9531-145">Recursos adicionais, como o seguinte, não funcionam, a menos que o módulo é importado para a sessão.</span><span class="sxs-lookup"><span data-stu-id="d9531-145">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="d9531-146">Em módulos bem formados no **PSModulePath** variável de ambiente, esses recursos funcionam, mesmo quando o módulo não é importado para a sessão.</span><span class="sxs-lookup"><span data-stu-id="d9531-146">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="d9531-147">O [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet não consegue encontrar os comandos no módulo.</span><span class="sxs-lookup"><span data-stu-id="d9531-147">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="d9531-148">O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets não é possível atualizar ou guardar ajuda para o módulo.</span><span class="sxs-lookup"><span data-stu-id="d9531-148">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="d9531-149">O [comando Show](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet não é possível localizar e apresentar os comandos no módulo.</span><span class="sxs-lookup"><span data-stu-id="d9531-149">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="d9531-150">Os comandos no módulo estão em falta o `Show-Command` janela no Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="d9531-150">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="d9531-151">Onde instalar os módulos</span><span class="sxs-lookup"><span data-stu-id="d9531-151">Where to Install Modules</span></span>

<span data-ttu-id="d9531-152">Esta secção explica onde no sistema de ficheiros para instalar os módulos do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d9531-152">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="d9531-153">O local depende de como o módulo é utilizado.</span><span class="sxs-lookup"><span data-stu-id="d9531-153">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="d9531-154">Instalar módulos para um utilizador específico</span><span class="sxs-lookup"><span data-stu-id="d9531-154">Installing Modules for a Specific User</span></span>

<span data-ttu-id="d9531-155">Se criar seu próprio módulo ou obter um módulo de terceiros, como um site da Comunidade do Windows PowerShell, e pretender que o módulo esteja disponível para a sua conta de utilizador apenas, instale o módulo no seu diretório de módulos específicos do usuário.</span><span class="sxs-lookup"><span data-stu-id="d9531-155">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

```
$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

<span data-ttu-id="d9531-156">O diretório de módulos específicos do usuário é adicionado ao valor do **PSModulePath** variável de ambiente, por predefinição.</span><span class="sxs-lookup"><span data-stu-id="d9531-156">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="d9531-157">Instalar módulos para todos os utilizadores em arquivos de programas</span><span class="sxs-lookup"><span data-stu-id="d9531-157">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="d9531-158">Se pretender que um módulo para estar disponível para todas as contas de utilizador no computador, instale o módulo na localização de ficheiros de programa.</span><span class="sxs-lookup"><span data-stu-id="d9531-158">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

```
$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

> [!NOTE]
> <span data-ttu-id="d9531-159">A localização de arquivos de programas é adicionada ao valor da variável de ambiente PSModulePath por predefinição no Windows PowerShell 4.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="d9531-159">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="d9531-160">Para versões anteriores do Windows PowerShell, pode criar os arquivos de programas localização ((%ProgramFiles%\WindowsPowerShell\Modules) e adicionar este caminho à sua variável de ambiente de PSModulePath, conforme descrito acima manualmente.</span><span class="sxs-lookup"><span data-stu-id="d9531-160">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="d9531-161">Instalar módulos num diretório de produtos</span><span class="sxs-lookup"><span data-stu-id="d9531-161">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="d9531-162">Se está a distribuir o módulo a outras partes, utilize a localização de arquivos de programas padrão descrita acima, ou criar seu próprio subdiretório específico da empresa ou específicos de produtos do diretório % ProgramFiles %.</span><span class="sxs-lookup"><span data-stu-id="d9531-162">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="d9531-163">Por exemplo, Fabrikam tecnologias, uma empresa fictícia, está a ser enviado um módulo do Windows PowerShell para o seu produto Fabrikam Manager.</span><span class="sxs-lookup"><span data-stu-id="d9531-163">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="d9531-164">O instalador do módulo cria um subdiretório de módulos no subdiretório de produto do Gestor da Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="d9531-164">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="d9531-165">Para ativar as funcionalidades de deteção de módulo do Windows PowerShell localizar o módulo da Fabrikam, o instalador do módulo de Fabrikam adiciona a localização do módulo para o valor do **PSModulePath** variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="d9531-165">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += "C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="d9531-166">Instalar módulos no diretório de ficheiros comuns</span><span class="sxs-lookup"><span data-stu-id="d9531-166">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="d9531-167">Se um módulo é utilizado por vários componentes de um produto ou por várias versões de um produto, instale o módulo num subdiretório específicos de módulo de subdiretório de Files\Modules %ProgramFiles%\Common.</span><span class="sxs-lookup"><span data-stu-id="d9531-167">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="d9531-168">No exemplo a seguir, o módulo de Fabrikam é instalado num subdiretório de subdiretório de Files\Modules %ProgramFiles%\Common Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="d9531-168">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span> <span data-ttu-id="d9531-169">Tenha em atenção que cada módulo reside no seu próprio subdiretório no subdiretório módulos.</span><span class="sxs-lookup"><span data-stu-id="d9531-169">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)

```

<span data-ttu-id="d9531-170">Em seguida, o instalador assegura o valor do **PSModulePath** variável de ambiente inclui o caminho do subdiretório de módulos de ficheiros comuns.</span><span class="sxs-lookup"><span data-stu-id="d9531-170">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="d9531-171">Instalação de várias versões de um módulo</span><span class="sxs-lookup"><span data-stu-id="d9531-171">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="d9531-172">Para instalar várias versões do mesmo módulo, utilize o procedimento seguinte.</span><span class="sxs-lookup"><span data-stu-id="d9531-172">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="d9531-173">Crie um diretório para cada versão do módulo.</span><span class="sxs-lookup"><span data-stu-id="d9531-173">Create a directory for each version of the module.</span></span> <span data-ttu-id="d9531-174">Inclua o número de versão no nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="d9531-174">Include the version number in the directory name.</span></span>

2. <span data-ttu-id="d9531-175">Crie um manifesto de módulo para cada versão do módulo.</span><span class="sxs-lookup"><span data-stu-id="d9531-175">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="d9531-176">O valor do **ModuleVersion** da chave no manifesto, introduza o número de versão do módulo.</span><span class="sxs-lookup"><span data-stu-id="d9531-176">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="d9531-177">Guarde o ficheiro de manifesto (. psd1) no diretório específico da versão para o módulo.</span><span class="sxs-lookup"><span data-stu-id="d9531-177">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>

3. <span data-ttu-id="d9531-178">Adicionar o caminho de pasta de raiz do módulo para o valor do **PSModulePath** variável de ambiente, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="d9531-178">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="d9531-179">Para importar uma versão específica do módulo, o utilizador final pode utilizar o `MinimumVersion` ou `RequiredVersion` parâmetros do [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d9531-179">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="d9531-180">Por exemplo, se o módulo de Fabrikam está disponível nas versões 8.0 e 9.0, a estrutura de diretório de módulo Fabrikam poderá assemelhar-se ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="d9531-180">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

<span data-ttu-id="d9531-181">O instalador adiciona ambos os caminhos dos módulos para o **PSModulePath** valor da variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="d9531-181">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="d9531-182">Quando estes passos estiverem concluídos, o **ListAvailable** parâmetro do [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet obtém ambos os módulos da Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="d9531-182">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="d9531-183">Para importar um módulo específico, utilize o `MinimumVersion` ou `RequiredVersion` parâmetros do [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d9531-183">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="d9531-184">Se ambos os módulos são importados para a mesma sessão, e os módulos contêm cmdlets com os mesmos nomes, os cmdlets que são importados pela última vez são eficazes na sessão.</span><span class="sxs-lookup"><span data-stu-id="d9531-184">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="d9531-185">Manipulação de conflitos de nomes de comando</span><span class="sxs-lookup"><span data-stu-id="d9531-185">Handling Command Name Conflicts</span></span>

<span data-ttu-id="d9531-186">Quando os comandos que exporta um módulo de tem o mesmo nome como comandos numa sessão do utilizador, podem ocorrer conflitos de nome do comando.</span><span class="sxs-lookup"><span data-stu-id="d9531-186">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="d9531-187">Quando uma sessão contém dois comandos que têm o mesmo nome, o Windows PowerShell é executado com o tipo de comando que tem precedência.</span><span class="sxs-lookup"><span data-stu-id="d9531-187">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="d9531-188">Quando uma sessão contém dois comandos que têm o mesmo nome e o mesmo tipo, o Windows PowerShell executa o comando que foi adicionado à sessão mais recentemente.</span><span class="sxs-lookup"><span data-stu-id="d9531-188">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="d9531-189">Para executar um comando que não é executado por predefinição, os utilizadores podem qualificar o nome do comando com o nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="d9531-189">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="d9531-190">Por exemplo, se a sessão contém um `Get-Date` função e o `Get-Date` cmdlet, o Windows PowerShell executa a função, por predefinição.</span><span class="sxs-lookup"><span data-stu-id="d9531-190">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="d9531-191">Para executar o cmdlet, precede o comando com o nome do módulo, tal como:</span><span class="sxs-lookup"><span data-stu-id="d9531-191">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="d9531-192">Para evitar conflitos de nomes, os autores de módulo podem utilizar o **DefaultCommandPrefix** exportar chave no manifesto do módulo para especificar um prefixo do nome para todos os comandos do módulo.</span><span class="sxs-lookup"><span data-stu-id="d9531-192">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="d9531-193">Os utilizadores podem utilizar o **prefixo** parâmetro do `Import-Module` cmdlet para utilizar um prefixo de alternativo.</span><span class="sxs-lookup"><span data-stu-id="d9531-193">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="d9531-194">O valor do **prefixo** parâmetro terão precedência sobre o valor da **DefaultCommandPrefix** chave.</span><span class="sxs-lookup"><span data-stu-id="d9531-194">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9531-195">Veja Também</span><span class="sxs-lookup"><span data-stu-id="d9531-195">See Also</span></span>

[<span data-ttu-id="d9531-196">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="d9531-196">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="d9531-197">Escrever um módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d9531-197">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
