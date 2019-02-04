---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Trabalhar com Entradas do Registo
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 8483b6f98739697b24a13055dfffbc7b5bacc2cc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686811"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="c2fe7-103">Trabalhar com Entradas do Registo</span><span class="sxs-lookup"><span data-stu-id="c2fe7-103">Working with Registry Entries</span></span>

<span data-ttu-id="c2fe7-104">Uma vez que as entradas do Registro são propriedades de chaves e, assim, a não é possível diretamente ser pesquisadas, é necessário usar uma abordagem ligeiramente diferente ao trabalhar com eles.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

### <a name="listing-registry-entries"></a><span data-ttu-id="c2fe7-105">Entradas de registro de listagem</span><span class="sxs-lookup"><span data-stu-id="c2fe7-105">Listing Registry Entries</span></span>

<span data-ttu-id="c2fe7-106">Existem várias formas diferentes de examinar as entradas do Registro.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="c2fe7-107">A forma mais simples é obter os nomes de propriedade associados com uma chave.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="c2fe7-108">Por exemplo, para ver os nomes das entradas na chave do registo `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, utilize `Get-Item`.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-108">For example, to see the names of the entries in the registry key `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, use `Get-Item`.</span></span> <span data-ttu-id="c2fe7-109">Chaves de registo de ter uma propriedade com o nome genérico de "Property", que é uma lista de entradas de registo na chave.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span>
<span data-ttu-id="c2fe7-110">O seguinte comando seleciona a propriedade de propriedade e expande os itens para que eles são exibidos numa lista:</span><span class="sxs-lookup"><span data-stu-id="c2fe7-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="c2fe7-111">Para ver as entradas de registro num formato mais legível, utilize `Get-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="c2fe7-111">To view the registry entries in a more readable form, use `Get-ItemProperty`:</span></span>

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
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

<span data-ttu-id="c2fe7-112">As propriedades relacionadas com o Windows PowerShell para a chave são todas o prefixo "PS", tal como **se PSPath**, **PSParentPath**, **PSChildName**, e **PSProvider** .</span><span class="sxs-lookup"><span data-stu-id="c2fe7-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="c2fe7-113">Pode utilizar o `*.*` notação que se refere a localização atual.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-113">You can use the `*.*` notation for referring to the current location.</span></span> <span data-ttu-id="c2fe7-114">Pode usar `Set-Location` para alterar para o **CurrentVersion** contentor de registo primeiro:</span><span class="sxs-lookup"><span data-stu-id="c2fe7-114">You can use `Set-Location` to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="c2fe7-115">Em alternativa, pode utilizar o PSDrive HKLM incorporadas com `Set-Location`:</span><span class="sxs-lookup"><span data-stu-id="c2fe7-115">Alternatively, you can use the built-in HKLM PSDrive with `Set-Location`:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="c2fe7-116">Em seguida, pode utilizar o `*.*` notação para a localização atual ver as propriedades sem especificar um caminho completo:</span><span class="sxs-lookup"><span data-stu-id="c2fe7-116">You can then use the `*.*` notation for the current location to list the properties without specifying a full path:</span></span>

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="c2fe7-117">Expansão de caminho funciona da mesma forma que funciona dentro do sistema de arquivos, para que a partir desta localização pode obter o **ItemProperty** para a listagem `HKLM:\SOFTWARE\Microsoft\Windows\Help` utilizando `Get-ItemProperty -Path ..\Help`.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for `HKLM:\SOFTWARE\Microsoft\Windows\Help` by using `Get-ItemProperty -Path ..\Help`.</span></span>

### <a name="getting-a-single-registry-entry"></a><span data-ttu-id="c2fe7-118">Obter uma entrada de registo único</span><span class="sxs-lookup"><span data-stu-id="c2fe7-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="c2fe7-119">Se quiser obter uma entrada específica numa chave de registo, pode utilizar uma das várias abordagens possíveis.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="c2fe7-120">Neste exemplo encontra o valor de **DevicePath** no `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-120">This example finds the value of **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

<span data-ttu-id="c2fe7-121">Usando `Get-ItemProperty`, utilize o **caminho** parâmetro para especificar o nome da chave e o **nome** parâmetro para especificar o nome da **DevicePath** entrada.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-121">Using `Get-ItemProperty`, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="c2fe7-122">Este comando devolve as propriedades padrão do Windows PowerShell, bem como a **DevicePath** propriedade.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="c2fe7-123">Embora `Get-ItemProperty` tem **filtro**, **incluir**, e **excluir** parâmetros, não pode ser utilizados para filtrar por nome de propriedade.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-123">Although `Get-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="c2fe7-124">Consulte estes parâmetros para chaves de registro, que são os caminhos de item e não as entradas de Registro.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-124">These parameters refer to registry keys, which are item paths and not registry entries.</span></span> <span data-ttu-id="c2fe7-125">Entradas de registo que são propriedades do item.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-125">Registry entries which are item properties.</span></span>

<span data-ttu-id="c2fe7-126">Outra opção é usar a ferramenta de linha de comandos Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-126">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="c2fe7-127">Para obter ajuda com reg.exe, escreva `reg.exe /?` no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-127">For help with reg.exe, type `reg.exe /?` at a command prompt.</span></span> <span data-ttu-id="c2fe7-128">Para localizar a entrada de DevicePath, utilize reg.exe, conforme mostrado no comando seguinte:</span><span class="sxs-lookup"><span data-stu-id="c2fe7-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="c2fe7-129">Também pode utilizar o **WshShell** objeto de COM também encontrar algumas entradas no Registro, embora esse método não funciona com dados binários grandes ou com os nomes de entrada do Registro que incluem caracteres como "\\").</span><span class="sxs-lookup"><span data-stu-id="c2fe7-129">You can also use the **WshShell** COM object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="c2fe7-130">Acrescentar o nome de propriedade para o caminho de item com um \\ separador:</span><span class="sxs-lookup"><span data-stu-id="c2fe7-130">Append the property name to the item path with a \\ separator:</span></span>

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

### <a name="setting-a-single-registry-entry"></a><span data-ttu-id="c2fe7-131">Definir uma entrada de registo único</span><span class="sxs-lookup"><span data-stu-id="c2fe7-131">Setting a Single Registry Entry</span></span>

<span data-ttu-id="c2fe7-132">Se quiser alterar uma entrada específica numa chave de registo, pode utilizar uma das várias abordagens possíveis.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-132">If you want to change a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="c2fe7-133">Neste exemplo modifica os **caminho** entrada sob `HKEY_CURRENT_USER\Environment`.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-133">This example modifies the **Path** entry under `HKEY_CURRENT_USER\Environment`.</span></span> <span data-ttu-id="c2fe7-134">O **caminho** entrada especifica onde encontrar arquivos executáveis.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-134">The **Path** entry specifies where to find executable files.</span></span>

1. <span data-ttu-id="c2fe7-135">Recuperar o valor atual do **caminho** usando entrada `Get-ItemProperty`.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-135">Retrieve the current value of the **Path** entry using `Get-ItemProperty`.</span></span>
2. <span data-ttu-id="c2fe7-136">Adicionar o novo valor, separá-lo com um `;`.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-136">Add the new value, separating it with a `;`.</span></span>
3. <span data-ttu-id="c2fe7-137">Utilize `Set-ItemProperty` com o nome da chave, o nome de entrada e o valor para modificar a entrada de registo.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-137">Use `Set-ItemProperty` with the specified key, entry name, and value to modify the registry entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> <span data-ttu-id="c2fe7-138">Embora `Set-ItemProperty` tem **filtro**, **incluir**, e **excluir** parâmetros, não pode ser utilizados para filtrar por nome de propriedade.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-138">Although `Set-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="c2fe7-139">Estes parâmetros referir-se para chaves do Registro — que são os caminhos de item — e não as entradas de Registro — que são propriedades do item.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-139">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="c2fe7-140">Outra opção é usar a ferramenta de linha de comandos Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-140">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="c2fe7-141">Para obter ajuda com reg.exe, escreva **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="c2fe7-141">For help with reg.exe, type **reg.exe /?**</span></span>
<span data-ttu-id="c2fe7-142">no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-142">at a command prompt.</span></span>

<span data-ttu-id="c2fe7-143">As seguintes alterações de exemplo da **caminho** entrada ao remover o caminho adicionado no exemplo acima.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-143">The following example changes the **Path** entry by removing the path added in the example above.</span></span>
<span data-ttu-id="c2fe7-144">`Get-ItemProperty` ainda é usado para recuperar o valor atual para evitar ter de analisar a cadeia de caracteres retornada de `reg query`.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-144">`Get-ItemProperty` is still used to retrieve the current value to avoid having to parse the string returned from `reg query`.</span></span> <span data-ttu-id="c2fe7-145">O **subcadeia** e **LastIndexOf** métodos são usados para recuperar o caminho do último adicionado para o **caminho** entrada.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-145">The **SubString** and **LastIndexOf** methods are used to retrieve the last path added to the **Path** entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

### <a name="creating-new-registry-entries"></a><span data-ttu-id="c2fe7-146">Criar novas entradas de registo</span><span class="sxs-lookup"><span data-stu-id="c2fe7-146">Creating New Registry Entries</span></span>

<span data-ttu-id="c2fe7-147">Para adicionar uma nova entrada com o nome "PowerShellPath" para o **CurrentVersion** utilização de chaves, `New-ItemProperty` com o caminho para a chave, o nome de entrada e o valor da entrada.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-147">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use `New-ItemProperty` with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="c2fe7-148">Neste exemplo, vamos o valor da variável do Windows PowerShell `$PSHome`, que armazena o caminho para o diretório de instalação para o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-148">For this example, we will take the value of the Windows PowerShell variable `$PSHome`, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="c2fe7-149">Pode adicionar a nova entrada à chave, utilizando o comando seguinte e o comando também retorna informações sobre a nova entrada:</span><span class="sxs-lookup"><span data-stu-id="c2fe7-149">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="c2fe7-150">O **PropertyType** tem de ser o nome de um **Microsoft.Win32.RegistryValueKind** membro da enumeração da tabela seguinte:</span><span class="sxs-lookup"><span data-stu-id="c2fe7-150">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="c2fe7-151">Valor de PropertyType</span><span class="sxs-lookup"><span data-stu-id="c2fe7-151">PropertyType Value</span></span>|<span data-ttu-id="c2fe7-152">Significado</span><span class="sxs-lookup"><span data-stu-id="c2fe7-152">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="c2fe7-153">Binário</span><span class="sxs-lookup"><span data-stu-id="c2fe7-153">Binary</span></span>|<span data-ttu-id="c2fe7-154">Dados binários</span><span class="sxs-lookup"><span data-stu-id="c2fe7-154">Binary data</span></span>|
|<span data-ttu-id="c2fe7-155">DWord</span><span class="sxs-lookup"><span data-stu-id="c2fe7-155">DWord</span></span>|<span data-ttu-id="c2fe7-156">Um número que é um UInt32 válido</span><span class="sxs-lookup"><span data-stu-id="c2fe7-156">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="c2fe7-157">ExpandString</span><span class="sxs-lookup"><span data-stu-id="c2fe7-157">ExpandString</span></span>|<span data-ttu-id="c2fe7-158">Uma cadeia de caracteres que pode conter variáveis de ambiente que são expandidas dinamicamente</span><span class="sxs-lookup"><span data-stu-id="c2fe7-158">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="c2fe7-159">MultiString</span><span class="sxs-lookup"><span data-stu-id="c2fe7-159">MultiString</span></span>|<span data-ttu-id="c2fe7-160">Uma cadeia de caracteres com várias linhas</span><span class="sxs-lookup"><span data-stu-id="c2fe7-160">A multiline string</span></span>|
|<span data-ttu-id="c2fe7-161">Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="c2fe7-161">String</span></span>|<span data-ttu-id="c2fe7-162">Qualquer valor de cadeia</span><span class="sxs-lookup"><span data-stu-id="c2fe7-162">Any string value</span></span>|
|<span data-ttu-id="c2fe7-163">QWord</span><span class="sxs-lookup"><span data-stu-id="c2fe7-163">QWord</span></span>|<span data-ttu-id="c2fe7-164">8 bytes de dados binários</span><span class="sxs-lookup"><span data-stu-id="c2fe7-164">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="c2fe7-165">Pode adicionar uma entrada de registo em várias localizações, especificando uma matriz de valores para o **caminho** parâmetro:</span><span class="sxs-lookup"><span data-stu-id="c2fe7-165">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="c2fe7-166">Também pode substituir um valor de entrada de registo já existentes ao adicionar o **força** parâmetro para qualquer `New-ItemProperty` comando.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-166">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any `New-ItemProperty` command.</span></span>

### <a name="renaming-registry-entries"></a><span data-ttu-id="c2fe7-167">Mudar o nome de entradas de registro</span><span class="sxs-lookup"><span data-stu-id="c2fe7-167">Renaming Registry Entries</span></span>

<span data-ttu-id="c2fe7-168">Para mudar o nome da **PowerShellPath** entrada de "PSHome", utilize `Rename-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="c2fe7-168">To rename the **PowerShellPath** entry to "PSHome," use `Rename-ItemProperty`:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="c2fe7-169">Para apresentar o valor de nome mudado, adicione a **PassThru** parâmetro para o comando.</span><span class="sxs-lookup"><span data-stu-id="c2fe7-169">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a><span data-ttu-id="c2fe7-170">A eliminar entradas de registro</span><span class="sxs-lookup"><span data-stu-id="c2fe7-170">Deleting Registry Entries</span></span>

<span data-ttu-id="c2fe7-171">Para eliminar o PSHome e PowerShellPath entradas de registo, utilize `Remove-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="c2fe7-171">To delete both the PSHome and PowerShellPath registry entries, use `Remove-ItemProperty`:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
