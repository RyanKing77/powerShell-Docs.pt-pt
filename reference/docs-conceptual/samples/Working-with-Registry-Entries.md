---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Trabalhar com Entradas do Registo
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405373"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="d4a7e-103">Trabalhar com Entradas do Registo</span><span class="sxs-lookup"><span data-stu-id="d4a7e-103">Working with Registry Entries</span></span>

<span data-ttu-id="d4a7e-104">Uma vez que as entradas do Registro são propriedades de chaves e, assim, a não é possível diretamente ser pesquisadas, é necessário usar uma abordagem ligeiramente diferente ao trabalhar com eles.</span><span class="sxs-lookup"><span data-stu-id="d4a7e-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

### <a name="listing-registry-entries"></a><span data-ttu-id="d4a7e-105">Entradas de registro de listagem</span><span class="sxs-lookup"><span data-stu-id="d4a7e-105">Listing Registry Entries</span></span>

<span data-ttu-id="d4a7e-106">Existem várias formas diferentes de examinar as entradas do Registro.</span><span class="sxs-lookup"><span data-stu-id="d4a7e-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="d4a7e-107">A forma mais simples é obter os nomes de propriedade associados com uma chave.</span><span class="sxs-lookup"><span data-stu-id="d4a7e-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="d4a7e-108">Por exemplo, para ver os nomes das entradas na chave do registo **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, utilize **Get-Item** .</span><span class="sxs-lookup"><span data-stu-id="d4a7e-108">For example, to see the names of the entries in the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, use **Get-Item**.</span></span> <span data-ttu-id="d4a7e-109">Chaves de registo de ter uma propriedade com o nome genérico de "Property", que é uma lista de entradas de registo na chave.</span><span class="sxs-lookup"><span data-stu-id="d4a7e-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span> <span data-ttu-id="d4a7e-110">O seguinte comando seleciona a propriedade de propriedade e expande os itens para que eles são exibidos numa lista:</span><span class="sxs-lookup"><span data-stu-id="d4a7e-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="d4a7e-111">Para ver as entradas de registro num formato mais legível, utilize **Get-ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="d4a7e-111">To view the registry entries in a more readable form, use **Get-ItemProperty**:</span></span>

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

<span data-ttu-id="d4a7e-112">As propriedades relacionadas com o Windows PowerShell para a chave são todas o prefixo "PS", tal como **se PSPath**, **PSParentPath**, **PSChildName**, e **PSProvider** .</span><span class="sxs-lookup"><span data-stu-id="d4a7e-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="d4a7e-113">Pode usar a "**.**" notação que se refere a localização atual.</span><span class="sxs-lookup"><span data-stu-id="d4a7e-113">You can use the "**.**" notation for referring to the current location.</span></span> <span data-ttu-id="d4a7e-114">Pode usar **Set-Location** para alterar para o **CurrentVersion** contentor de registo primeiro:</span><span class="sxs-lookup"><span data-stu-id="d4a7e-114">You can use **Set-Location** to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="d4a7e-115">Em alternativa, pode utilizar o PSDrive HKLM incorporadas com **Set-Location**:</span><span class="sxs-lookup"><span data-stu-id="d4a7e-115">Alternatively, you can use the built-in HKLM PSDrive with **Set-Location**:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="d4a7e-116">Em seguida, pode utilizar o "**.**" notação para a localização atual ver as propriedades sem especificar um caminho completo:</span><span class="sxs-lookup"><span data-stu-id="d4a7e-116">You can then use the "**.**" notation for the current location to list the properties without specifying a full path:</span></span>

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="d4a7e-117">Expansão de caminho funciona da mesma forma que funciona dentro do sistema de arquivos, para que a partir desta localização pode obter o **ItemProperty** para a listagem **HKLM:\\SOFTWARE\\Microsoft\\Windows \\Ajudar** utilizando **Get ItemProperty-caminho.... \\Ajudar**.</span><span class="sxs-lookup"><span data-stu-id="d4a7e-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** by using **Get-ItemProperty -Path ..\\Help**.</span></span>

### <a name="getting-a-single-registry-entry"></a><span data-ttu-id="d4a7e-118">Obter uma entrada de registo único</span><span class="sxs-lookup"><span data-stu-id="d4a7e-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="d4a7e-119">Se quiser obter uma entrada específica numa chave de registo, pode utilizar uma das várias abordagens possíveis.</span><span class="sxs-lookup"><span data-stu-id="d4a7e-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="d4a7e-120">Neste exemplo encontra o valor de **DevicePath** na **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="d4a7e-120">This example finds the value of **DevicePath** in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span>

<span data-ttu-id="d4a7e-121">Usando **Get-ItemProperty**, utilize o **caminho** parâmetro para especificar o nome da chave e o **nome** parâmetro para especificar o nome do **DevicePath** entrada.</span><span class="sxs-lookup"><span data-stu-id="d4a7e-121">Using **Get-ItemProperty**, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

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

<span data-ttu-id="d4a7e-122">Este comando devolve as propriedades padrão do Windows PowerShell, bem como a **DevicePath** propriedade.</span><span class="sxs-lookup"><span data-stu-id="d4a7e-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="d4a7e-123">Embora **Get-ItemProperty** tem **filtro**, **incluir**, e **excluir** parâmetros, não pode ser utilizados para filtrar por nome de propriedade.</span><span class="sxs-lookup"><span data-stu-id="d4a7e-123">Although **Get-ItemProperty** has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="d4a7e-124">Estes parâmetros referir-se para chaves do Registro — que são os caminhos de item — e não as entradas de Registro — que são propriedades do item.</span><span class="sxs-lookup"><span data-stu-id="d4a7e-124">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="d4a7e-125">Outra opção é usar a ferramenta de linha de comandos Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="d4a7e-125">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="d4a7e-126">Para obter ajuda com reg.exe, escreva **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="d4a7e-126">For help with reg.exe, type **reg.exe /?**</span></span> <span data-ttu-id="d4a7e-127">no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="d4a7e-127">at a command prompt.</span></span> <span data-ttu-id="d4a7e-128">Para localizar a entrada de DevicePath, utilize reg.exe, conforme mostrado no comando seguinte:</span><span class="sxs-lookup"><span data-stu-id="d4a7e-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="d4a7e-129">Também pode utilizar o **WshShell COM** objeto também para encontrar algumas entradas no Registro, embora esse método não funciona com dados binários grandes ou com os nomes de entrada do Registro que incluem caracteres como "\\").</span><span class="sxs-lookup"><span data-stu-id="d4a7e-129">You can also use the **WshShell COM** object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="d4a7e-130">Acrescentar o nome de propriedade para o caminho de item com um \\ separador:</span><span class="sxs-lookup"><span data-stu-id="d4a7e-130">Append the property name to the item path with a \\ separator:</span></span>

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a><span data-ttu-id="d4a7e-131">Criar novas entradas de registo</span><span class="sxs-lookup"><span data-stu-id="d4a7e-131">Creating New Registry Entries</span></span>

<span data-ttu-id="d4a7e-132">Para adicionar uma nova entrada com o nome "PowerShellPath" para o **CurrentVersion** chave, use **New-ItemProperty** com o caminho para a chave, o nome de entrada e o valor da entrada.</span><span class="sxs-lookup"><span data-stu-id="d4a7e-132">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use **New-ItemProperty** with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="d4a7e-133">Neste exemplo, vamos o valor da variável do Windows PowerShell **$PSHome**, que armazena o caminho para o diretório de instalação para o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d4a7e-133">For this example, we will take the value of the Windows PowerShell variable **$PSHome**, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="d4a7e-134">Pode adicionar a nova entrada à chave, utilizando o comando seguinte e o comando também retorna informações sobre a nova entrada:</span><span class="sxs-lookup"><span data-stu-id="d4a7e-134">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

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

<span data-ttu-id="d4a7e-135">O **PropertyType** tem de ser o nome de um **Microsoft.Win32.RegistryValueKind** membro da enumeração da tabela seguinte:</span><span class="sxs-lookup"><span data-stu-id="d4a7e-135">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="d4a7e-136">Valor de PropertyType</span><span class="sxs-lookup"><span data-stu-id="d4a7e-136">PropertyType Value</span></span>|<span data-ttu-id="d4a7e-137">Significado</span><span class="sxs-lookup"><span data-stu-id="d4a7e-137">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="d4a7e-138">Binário</span><span class="sxs-lookup"><span data-stu-id="d4a7e-138">Binary</span></span>|<span data-ttu-id="d4a7e-139">Dados binários</span><span class="sxs-lookup"><span data-stu-id="d4a7e-139">Binary data</span></span>|
|<span data-ttu-id="d4a7e-140">DWord</span><span class="sxs-lookup"><span data-stu-id="d4a7e-140">DWord</span></span>|<span data-ttu-id="d4a7e-141">Um número que é um UInt32 válido</span><span class="sxs-lookup"><span data-stu-id="d4a7e-141">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="d4a7e-142">ExpandString</span><span class="sxs-lookup"><span data-stu-id="d4a7e-142">ExpandString</span></span>|<span data-ttu-id="d4a7e-143">Uma cadeia de caracteres que pode conter variáveis de ambiente que são expandidas dinamicamente</span><span class="sxs-lookup"><span data-stu-id="d4a7e-143">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="d4a7e-144">MultiString</span><span class="sxs-lookup"><span data-stu-id="d4a7e-144">MultiString</span></span>|<span data-ttu-id="d4a7e-145">Uma cadeia de caracteres com várias linhas</span><span class="sxs-lookup"><span data-stu-id="d4a7e-145">A multiline string</span></span>|
|<span data-ttu-id="d4a7e-146">Cadeia</span><span class="sxs-lookup"><span data-stu-id="d4a7e-146">String</span></span>|<span data-ttu-id="d4a7e-147">Qualquer valor de cadeia</span><span class="sxs-lookup"><span data-stu-id="d4a7e-147">Any string value</span></span>|
|<span data-ttu-id="d4a7e-148">QWord</span><span class="sxs-lookup"><span data-stu-id="d4a7e-148">QWord</span></span>|<span data-ttu-id="d4a7e-149">8 bytes de dados binários</span><span class="sxs-lookup"><span data-stu-id="d4a7e-149">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="d4a7e-150">Pode adicionar uma entrada de registo em várias localizações, especificando uma matriz de valores para o **caminho** parâmetro:</span><span class="sxs-lookup"><span data-stu-id="d4a7e-150">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

<span data-ttu-id="d4a7e-151">Também pode substituir um valor de entrada de registo já existentes ao adicionar o **força** parâmetro para qualquer **New-ItemProperty** comando.</span><span class="sxs-lookup"><span data-stu-id="d4a7e-151">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any **New-ItemProperty** command.</span></span>

### <a name="renaming-registry-entries"></a><span data-ttu-id="d4a7e-152">Mudar o nome de entradas de registro</span><span class="sxs-lookup"><span data-stu-id="d4a7e-152">Renaming Registry Entries</span></span>

<span data-ttu-id="d4a7e-153">Para mudar o nome a **PowerShellPath** entrada de "PSHome", utilize **Rename-ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="d4a7e-153">To rename the **PowerShellPath** entry to "PSHome," use **Rename-ItemProperty**:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="d4a7e-154">Para apresentar o valor de nome mudado, adicione a **PassThru** parâmetro para o comando.</span><span class="sxs-lookup"><span data-stu-id="d4a7e-154">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a><span data-ttu-id="d4a7e-155">A eliminar entradas de registro</span><span class="sxs-lookup"><span data-stu-id="d4a7e-155">Deleting Registry Entries</span></span>

<span data-ttu-id="d4a7e-156">Para eliminar o PSHome e PowerShellPath entradas de registo, utilize **Remove-ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="d4a7e-156">To delete both the PSHome and PowerShellPath registry entries, use **Remove-ItemProperty**:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```