---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Trabalhar com Chaves do Registo
ms.openlocfilehash: 18daeaea2ee8917a709fef421d2b316f46bf7f4c
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030651"
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="d3340-103">Trabalhar com Chaves do Registo</span><span class="sxs-lookup"><span data-stu-id="d3340-103">Working with Registry Keys</span></span>

<span data-ttu-id="d3340-104">Como as chaves de registo são itens em unidades do Windows PowerShell, trabalhar com eles é muito semelhante a trabalhar com ficheiros e pastas.</span><span class="sxs-lookup"><span data-stu-id="d3340-104">Because registry keys are items on Windows PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="d3340-105">Uma diferença fundamental é que todos os itens numa unidade do Windows PowerShell baseada no registo são um contentor, tal como uma pasta numa unidade de sistema de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="d3340-105">One critical difference is that every item on a registry-based Windows PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="d3340-106">No entanto, as entradas do Registro e seus valores associados são propriedades dos itens, itens não distintos.</span><span class="sxs-lookup"><span data-stu-id="d3340-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

## <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="d3340-107">A listagem de todas as subchaves da chave de registo</span><span class="sxs-lookup"><span data-stu-id="d3340-107">Listing All Subkeys of a Registry Key</span></span>

<span data-ttu-id="d3340-108">Pode mostrar todos os itens diretamente dentro de uma chave do Registro usando **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="d3340-108">You can show all items directly within a registry key by using **Get-ChildItem**.</span></span> <span data-ttu-id="d3340-109">Adicionar o opcional **força** parâmetro para apresentar ocultada ou itens de sistema.</span><span class="sxs-lookup"><span data-stu-id="d3340-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="d3340-110">Por exemplo, este comando apresenta os itens diretamente na unidade do Windows PowerShell HKCU:, que corresponde do ramo de registo HKEY_CURRENT_USER:</span><span class="sxs-lookup"><span data-stu-id="d3340-110">For example, this command displays the items directly within Windows PowerShell drive HKCU:, which corresponds to the HKEY_CURRENT_USER registry hive:</span></span>

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

<span data-ttu-id="d3340-111">Estas são as chaves de nível superior visíveis em HKEY_CURRENT_USER no Editor de registo (Regedit.exe).</span><span class="sxs-lookup"><span data-stu-id="d3340-111">These are the top-level keys visible under HKEY_CURRENT_USER in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="d3340-112">Também pode especificar este caminho de registo, especificando o nome do fornecedor de registo, seguido por " **::** ".</span><span class="sxs-lookup"><span data-stu-id="d3340-112">You can also specify this registry path by specifying the registry provider's name, followed by "**::**".</span></span> <span data-ttu-id="d3340-113">O nome completo do fornecedor de registo é **Microsoft.PowerShell.Core\\Registro**, mas isso pode ser baixou para just **registo**.</span><span class="sxs-lookup"><span data-stu-id="d3340-113">The registry provider's full name is **Microsoft.PowerShell.Core\\Registry**, but this can be shortened to just **Registry**.</span></span> <span data-ttu-id="d3340-114">Qualquer um dos seguintes comandos irá listar o conteúdo diretamente em HKCU:</span><span class="sxs-lookup"><span data-stu-id="d3340-114">Any of the following commands will list the contents directly under HKCU:</span></span>

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="d3340-115">Estes comandos listam apenas os itens contidos diretamente, bem similar ao uso do Cmd.exe **DIR** comando ou **ls** numa shell de UNIX.</span><span class="sxs-lookup"><span data-stu-id="d3340-115">These commands list only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="d3340-116">Para mostrar os itens contidos, tem de especificar o **Recurse** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d3340-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="d3340-117">Para listar todas as chaves de Registro em HKCU, utilize o seguinte comando (esta operação pode demorar muito tempo.):</span><span class="sxs-lookup"><span data-stu-id="d3340-117">To list all registry keys in HKCU, use the following command (This operation can take an extremely long time.):</span></span>

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

<span data-ttu-id="d3340-118">**Get-ChildItem** pode efetuar as capacidades de filtragem complexas por meio de seu **caminho**, **filtro**, **Include**, e **excluir**parâmetros, mas esses parâmetros são, normalmente, com base apenas no nome.</span><span class="sxs-lookup"><span data-stu-id="d3340-118">**Get-ChildItem** can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="d3340-119">Pode efetuar uma filtragem complexa com base no outras propriedades de itens com o **Where-Object** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d3340-119">You can perform complex filtering based on other properties of items by using the **Where-Object** cmdlet.</span></span> <span data-ttu-id="d3340-120">O comando seguinte localiza todas as chaves em HKCU:\\Software que não mais do que uma subchave e também de ter exatamente quatro valores:</span><span class="sxs-lookup"><span data-stu-id="d3340-120">The following command finds all keys within HKCU:\\Software that have no more than one subkey and also have exactly four values:</span></span>

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a><span data-ttu-id="d3340-121">Copiar chaves</span><span class="sxs-lookup"><span data-stu-id="d3340-121">Copying Keys</span></span>

<span data-ttu-id="d3340-122">A copiar é feita com **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="d3340-122">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="d3340-123">O seguinte comando copia HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion e todas as respetivas propriedades para HKCU:\\, criar uma nova chave denominada "CurrentVersion":</span><span class="sxs-lookup"><span data-stu-id="d3340-123">The following command copies HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion and all of its properties to HKCU:\\, creating a new key named "CurrentVersion":</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

<span data-ttu-id="d3340-124">Se examinar esta chave de novo no editor do Registro ou usando **Get-ChildItem**, irá reparar que não tem cópias das subchaves contidas na nova localização.</span><span class="sxs-lookup"><span data-stu-id="d3340-124">If you examine this new key in the registry editor or by using **Get-ChildItem**, you will notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="d3340-125">Para poder copiar o conteúdo inteiro de um contentor, tem de especificar o **Recurse** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d3340-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="d3340-126">Para tornar a recursiva de comando de cópia anterior, usaria este comando:</span><span class="sxs-lookup"><span data-stu-id="d3340-126">To make the preceding copy command recursive, you would use this command:</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

<span data-ttu-id="d3340-127">Pode continuar a utilizar outras ferramentas que já tem disponível para efetuar cópias de sistema de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="d3340-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="d3340-128">Qualquer registo de ferramentas de edição — incluindo reg.exe regini.exe e regedit.exe—and objetos COM que o suporte à edição de registo (por exemplo, a classe StdRegProv de Wscript. shell e do WMI) pode ser usado no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d3340-128">Any registry editing tools—including reg.exe, regini.exe, and regedit.exe—and COM objects that support registry editing (such as WScript.Shell and WMI's StdRegProv class) can be used from within Windows PowerShell.</span></span>

## <a name="creating-keys"></a><span data-ttu-id="d3340-129">Criação de chaves</span><span class="sxs-lookup"><span data-stu-id="d3340-129">Creating Keys</span></span>

<span data-ttu-id="d3340-130">A criação de novas chaves no Registro é mais simples do que criar um novo item num sistema de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="d3340-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="d3340-131">Uma vez que todas as chaves de registo são contentores, não é necessário especificar o tipo de item; simplesmente fornecer um caminho explícito, tais como:</span><span class="sxs-lookup"><span data-stu-id="d3340-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

<span data-ttu-id="d3340-132">Também pode utilizar um caminho baseado em provedor para especificar uma chave:</span><span class="sxs-lookup"><span data-stu-id="d3340-132">You can also use a provider-based path to specify a key:</span></span>

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

## <a name="deleting-keys"></a><span data-ttu-id="d3340-133">A eliminar chaves</span><span class="sxs-lookup"><span data-stu-id="d3340-133">Deleting Keys</span></span>

<span data-ttu-id="d3340-134">A eliminar itens é essencialmente o mesmo para todos os fornecedores.</span><span class="sxs-lookup"><span data-stu-id="d3340-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="d3340-135">Os seguintes comandos irão automaticamente remover itens:</span><span class="sxs-lookup"><span data-stu-id="d3340-135">The following commands will silently remove items:</span></span>

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="d3340-136">Remover todas as chaves numa chave específica</span><span class="sxs-lookup"><span data-stu-id="d3340-136">Removing All Keys Under a Specific Key</span></span>

<span data-ttu-id="d3340-137">Pode remover itens contidos através de **Remove-Item**, mas será solicitado a confirmar a remoção, se o item contiver qualquer outra coisa.</span><span class="sxs-lookup"><span data-stu-id="d3340-137">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="d3340-138">Por exemplo, se tentar eliminar o HKCU:\\CurrentVersion subchave que criámos, vemos isso:</span><span class="sxs-lookup"><span data-stu-id="d3340-138">For example, if we attempt to delete the HKCU:\\CurrentVersion subkey we created, we see this:</span></span>

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="d3340-139">Para eliminar os itens contidos sem pedir confirmação, especifique a **-Recurse** parâmetro:</span><span class="sxs-lookup"><span data-stu-id="d3340-139">To delete contained items without prompting, specify the **-Recurse** parameter:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="d3340-140">Se quisesse remover todos os itens dentro do HKCU:\\CurrentVersion mas não HKCU:\\CurrentVersion em si, em vez disso, poderia usar:</span><span class="sxs-lookup"><span data-stu-id="d3340-140">If you wanted to remove all items within HKCU:\\CurrentVersion but not HKCU:\\CurrentVersion itself, you could instead use:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
