---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Trabalhar com Entradas do Registo
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952380"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="d8387-103">Trabalhar com Entradas do Registo</span><span class="sxs-lookup"><span data-stu-id="d8387-103">Working with Registry Entries</span></span>

<span data-ttu-id="d8387-104">Uma vez que as entradas de registo são propriedades de chaves e, como tal, a não é possível diretamente ser navegadas, precisamos de adotar uma abordagem ligeiramente diferente, ao trabalhar com eles.</span><span class="sxs-lookup"><span data-stu-id="d8387-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

### <a name="listing-registry-entries"></a><span data-ttu-id="d8387-105">Listar as entradas de registo</span><span class="sxs-lookup"><span data-stu-id="d8387-105">Listing Registry Entries</span></span>

<span data-ttu-id="d8387-106">Existem muitas formas diferentes de examinar as entradas de registo.</span><span class="sxs-lookup"><span data-stu-id="d8387-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="d8387-107">É a forma mais simples para obter os nomes de propriedade associados uma chave.</span><span class="sxs-lookup"><span data-stu-id="d8387-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="d8387-108">Por exemplo, para ver os nomes de entradas na chave do registo **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, utilize **Get-Item** .</span><span class="sxs-lookup"><span data-stu-id="d8387-108">For example, to see the names of the entries in the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, use **Get-Item**.</span></span> <span data-ttu-id="d8387-109">As chaves de registo tem uma propriedade com o nome genérico "Property" de que é uma lista de entradas de registo na chave.</span><span class="sxs-lookup"><span data-stu-id="d8387-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span> <span data-ttu-id="d8387-110">O seguinte comando seleciona a propriedade de propriedade e expande os itens de modo a que são apresentadas numa lista:</span><span class="sxs-lookup"><span data-stu-id="d8387-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="d8387-111">Para ver as entradas do registo num formato mais legível, utilize **Get-ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="d8387-111">To view the registry entries in a more readable form, use **Get-ItemProperty**:</span></span>

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

<span data-ttu-id="d8387-112">As propriedades relacionadas com o Windows PowerShell para a chave estão todos o prefixo "PS", tal como **PSPath**, **PSParentPath**, **PSChildName**, e **PSProvider** .</span><span class="sxs-lookup"><span data-stu-id="d8387-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="d8387-113">Pode utilizar o "**.**" notação para referir-se para a localização atual.</span><span class="sxs-lookup"><span data-stu-id="d8387-113">You can use the "**.**" notation for referring to the current location.</span></span> <span data-ttu-id="d8387-114">Pode utilizar **Set-Location** para alterar para o **CurrentVersion** contentor registo primeiro:</span><span class="sxs-lookup"><span data-stu-id="d8387-114">You can use **Set-Location** to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="d8387-115">Em alternativa, pode utilizar o PSDrive HKLM incorporada com **Set-Location**:</span><span class="sxs-lookup"><span data-stu-id="d8387-115">Alternatively, you can use the built-in HKLM PSDrive with **Set-Location**:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="d8387-116">Em seguida, pode utilizar o "**.**" notação para a localização atual ver as propriedades sem especificar um caminho completo:</span><span class="sxs-lookup"><span data-stu-id="d8387-116">You can then use the "**.**" notation for the current location to list the properties without specifying a full path:</span></span>

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="d8387-117">Expansão de caminho funciona da mesma, como sistema de ficheiros, pelo que a partir desta localização pode obter o **ItemProperty** listagem para **HKLM:\\SOFTWARE\\Microsoft\\Windows \\Ajudar** utilizando **Get ItemProperty-caminho... \\Ajudar**.</span><span class="sxs-lookup"><span data-stu-id="d8387-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** by using **Get-ItemProperty -Path ..\\Help**.</span></span>

### <a name="getting-a-single-registry-entry"></a><span data-ttu-id="d8387-118">Obter uma entrada de registo único</span><span class="sxs-lookup"><span data-stu-id="d8387-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="d8387-119">Se pretender obter uma entrada específica uma chave de registo, pode utilizar uma das várias abordagens possíveis.</span><span class="sxs-lookup"><span data-stu-id="d8387-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="d8387-120">Neste exemplo localiza o valor de **DevicePath** no **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="d8387-120">This example finds the value of **DevicePath** in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span>

<span data-ttu-id="d8387-121">Utilizando **Get-ItemProperty**, utilize o **caminho** parâmetro para especificar o nome da chave e o **nome** parâmetro para especificar o nome do **DevicePath** entrada.</span><span class="sxs-lookup"><span data-stu-id="d8387-121">Using **Get-ItemProperty**, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="d8387-122">Este comando devolve as propriedades padrão do Windows PowerShell, bem como o **DevicePath** propriedade.</span><span class="sxs-lookup"><span data-stu-id="d8387-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="d8387-123">Embora **Get-ItemProperty** tem **filtro**, **incluir**, e **excluir** parâmetros, não pode ser utilizados para filtrar por nome de propriedade.</span><span class="sxs-lookup"><span data-stu-id="d8387-123">Although **Get-ItemProperty** has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="d8387-124">Estes parâmetros, consulte a chaves de registo-que são caminhos de item — e não as entradas de registo — que são propriedades do item.</span><span class="sxs-lookup"><span data-stu-id="d8387-124">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="d8387-125">Outra opção consiste em utilizar a ferramenta de linha de comandos Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="d8387-125">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="d8387-126">Para obter ajuda com reg.exe, escreva **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="d8387-126">For help with reg.exe, type **reg.exe /?**</span></span> <span data-ttu-id="d8387-127">numa linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="d8387-127">at a command prompt.</span></span> <span data-ttu-id="d8387-128">Para localizar a entrada de DevicePath, utilize reg.exe conforme mostrado no comando seguinte:</span><span class="sxs-lookup"><span data-stu-id="d8387-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="d8387-129">Também pode utilizar o **WshShell COM** objeto, bem como ao localizar algumas entradas de registo, apesar deste método não funciona com grandes dados binários ou com os nomes de entradas de registo que incluam carateres como "\\").</span><span class="sxs-lookup"><span data-stu-id="d8387-129">You can also use the **WshShell COM** object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="d8387-130">Acrescentar o nome de propriedade para o caminho de item com um \\ separador:</span><span class="sxs-lookup"><span data-stu-id="d8387-130">Append the property name to the item path with a \\ separator:</span></span>

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a><span data-ttu-id="d8387-131">Criar novas entradas de registo</span><span class="sxs-lookup"><span data-stu-id="d8387-131">Creating New Registry Entries</span></span>

<span data-ttu-id="d8387-132">Para adicionar uma nova entrada com o nome "PowerShellPath" para o **CurrentVersion** utilização da chave, **New-ItemProperty** com o caminho para a chave, o nome de entrada e o valor da entrada.</span><span class="sxs-lookup"><span data-stu-id="d8387-132">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use **New-ItemProperty** with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="d8387-133">Neste exemplo, iremos irá demorar o valor da variável do Windows PowerShell **$PSHome**, que armazena o caminho para o diretório de instalação para o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d8387-133">For this example, we will take the value of the Windows PowerShell variable **$PSHome**, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="d8387-134">Pode adicionar a nova entrada para a chave, utilizando o seguinte comando e o comando também devolve informações sobre a nova entrada:</span><span class="sxs-lookup"><span data-stu-id="d8387-134">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="d8387-135">O **PropertyType** tem de ser o nome de um **Microsoft.Win32.RegistryValueKind** membro de enumeração da tabela seguinte:</span><span class="sxs-lookup"><span data-stu-id="d8387-135">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="d8387-136">PropertyType valor</span><span class="sxs-lookup"><span data-stu-id="d8387-136">PropertyType Value</span></span>|<span data-ttu-id="d8387-137">Significado</span><span class="sxs-lookup"><span data-stu-id="d8387-137">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="d8387-138">Binário</span><span class="sxs-lookup"><span data-stu-id="d8387-138">Binary</span></span>|<span data-ttu-id="d8387-139">Dados binários</span><span class="sxs-lookup"><span data-stu-id="d8387-139">Binary data</span></span>|
|<span data-ttu-id="d8387-140">DWord</span><span class="sxs-lookup"><span data-stu-id="d8387-140">DWord</span></span>|<span data-ttu-id="d8387-141">Um número que é um UInt32 válido</span><span class="sxs-lookup"><span data-stu-id="d8387-141">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="d8387-142">ExpandString</span><span class="sxs-lookup"><span data-stu-id="d8387-142">ExpandString</span></span>|<span data-ttu-id="d8387-143">Uma cadeia que pode conter variáveis de ambiente que são expandidas dinamicamente</span><span class="sxs-lookup"><span data-stu-id="d8387-143">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="d8387-144">FixedLength</span><span class="sxs-lookup"><span data-stu-id="d8387-144">MultiString</span></span>|<span data-ttu-id="d8387-145">Uma cadeia com várias linhas</span><span class="sxs-lookup"><span data-stu-id="d8387-145">A multiline string</span></span>|
|<span data-ttu-id="d8387-146">Cadeia</span><span class="sxs-lookup"><span data-stu-id="d8387-146">String</span></span>|<span data-ttu-id="d8387-147">Qualquer valor de cadeia</span><span class="sxs-lookup"><span data-stu-id="d8387-147">Any string value</span></span>|
|<span data-ttu-id="d8387-148">QWord</span><span class="sxs-lookup"><span data-stu-id="d8387-148">QWord</span></span>|<span data-ttu-id="d8387-149">8 bytes de dados binários</span><span class="sxs-lookup"><span data-stu-id="d8387-149">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="d8387-150">Pode adicionar uma entrada de registo em várias localizações, especificando uma matriz de valores para o **caminho** parâmetro:</span><span class="sxs-lookup"><span data-stu-id="d8387-150">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

<span data-ttu-id="d8387-151">Também pode substituir um valor de entrada de registo pré-existente adicionando o **Force** parâmetro a qualquer **New-ItemProperty** comando.</span><span class="sxs-lookup"><span data-stu-id="d8387-151">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any **New-ItemProperty** command.</span></span>

### <a name="renaming-registry-entries"></a><span data-ttu-id="d8387-152">Mudar o nome de entradas de registo</span><span class="sxs-lookup"><span data-stu-id="d8387-152">Renaming Registry Entries</span></span>

<span data-ttu-id="d8387-153">Para mudar o nome de **PowerShellPath** entrada para "PSHome", utilize **ItemProperty de mudança de nome**:</span><span class="sxs-lookup"><span data-stu-id="d8387-153">To rename the **PowerShellPath** entry to "PSHome," use **Rename-ItemProperty**:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="d8387-154">Para apresentar o valor cujo nome foi alterado, adicione o **PassThru** parâmetro para o comando.</span><span class="sxs-lookup"><span data-stu-id="d8387-154">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a><span data-ttu-id="d8387-155">Eliminar entradas de registo</span><span class="sxs-lookup"><span data-stu-id="d8387-155">Deleting Registry Entries</span></span>

<span data-ttu-id="d8387-156">Para eliminar as entradas de registo PSHome tanto PowerShellPath, utilize **remover ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="d8387-156">To delete both the PSHome and PowerShellPath registry entries, use **Remove-ItemProperty**:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```