---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Trabalhar com Chaves do Registo
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: a9d08f2f6b5803980dec45a4e266ad66879c8c8d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951703"
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="17d58-103">Trabalhar com Chaves do Registo</span><span class="sxs-lookup"><span data-stu-id="17d58-103">Working with Registry Keys</span></span>

<span data-ttu-id="17d58-104">Uma vez que as chaves de registo são itens em unidades do Windows PowerShell, trabalhar com eles é muito semelhante para trabalhar com ficheiros e pastas.</span><span class="sxs-lookup"><span data-stu-id="17d58-104">Because registry keys are items on Windows PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="17d58-105">Uma diferença crítica é que todos os itens numa unidade do Windows PowerShell baseada no registo é um contentor, tal como uma pasta numa unidade de sistema de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="17d58-105">One critical difference is that every item on a registry-based Windows PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="17d58-106">No entanto, as entradas de registo e os respetivos valores associados são propriedades dos itens, itens não distintos.</span><span class="sxs-lookup"><span data-stu-id="17d58-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

### <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="17d58-107">Listar todas as subchaves da chave de registo</span><span class="sxs-lookup"><span data-stu-id="17d58-107">Listing All Subkeys of a Registry Key</span></span>

<span data-ttu-id="17d58-108">Pode mostrar todos os itens diretamente dentro de uma chave de registo utilizando **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="17d58-108">You can show all items directly within a registry key by using **Get-ChildItem**.</span></span> <span data-ttu-id="17d58-109">Adicionar o opcional **Force** parâmetro para apresentar ocultada ou itens de sistema.</span><span class="sxs-lookup"><span data-stu-id="17d58-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="17d58-110">Por exemplo, este comando apresenta os itens diretamente na unidade do Windows PowerShell HKCU:, que corresponde ao ramo do registo em HKEY_CURRENT_USER:</span><span class="sxs-lookup"><span data-stu-id="17d58-110">For example, this command displays the items directly within Windows PowerShell drive HKCU:, which corresponds to the HKEY_CURRENT_USER registry hive:</span></span>

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

<span data-ttu-id="17d58-111">Estes são visíveis em HKEY_CURRENT_USER no Editor de registo (Regedit.exe), as chaves de nível superior.</span><span class="sxs-lookup"><span data-stu-id="17d58-111">These are the top-level keys visible under HKEY_CURRENT_USER in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="17d58-112">Também pode especificar este caminho de registo, especificando o nome do fornecedor de registo, seguido de "**::**".</span><span class="sxs-lookup"><span data-stu-id="17d58-112">You can also specify this registry path by specifying the registry provider's name, followed by "**::**".</span></span> <span data-ttu-id="17d58-113">Nome completo do fornecedor de registo for **Microsoft.PowerShell.Core\\registo**, mas isto pode ser shortened para just **registo**.</span><span class="sxs-lookup"><span data-stu-id="17d58-113">The registry provider's full name is **Microsoft.PowerShell.Core\\Registry**, but this can be shortened to just **Registry**.</span></span> <span data-ttu-id="17d58-114">Qualquer um dos seguintes comandos irá listar o conteúdo diretamente em HKCU:</span><span class="sxs-lookup"><span data-stu-id="17d58-114">Any of the following commands will list the contents directly under HKCU:</span></span>

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="17d58-115">Estes comandos listam apenas os itens contidos diretamente, semelhante a utilização do Cmd.exe **DIR** comando ou **ls** na shell de UNIX.</span><span class="sxs-lookup"><span data-stu-id="17d58-115">These commands list only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="17d58-116">Mostrar itens que contêm, tem de especificar o **Recurse** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="17d58-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="17d58-117">Para listar todas as chaves de registo no HKCU, utilize o seguinte comando (esta operação pode demorar uma hora extremamente longa.):</span><span class="sxs-lookup"><span data-stu-id="17d58-117">To list all registry keys in HKCU, use the following command (This operation can take an extremely long time.):</span></span>

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

<span data-ttu-id="17d58-118">**Get-ChildItem** pode efetuar as capacidades de filtragem complexas através do respetivo **caminho**, **filtro**, **incluir**, e **excluir**parâmetros, mas esses parâmetros normalmente baseiam-se apenas no nome.</span><span class="sxs-lookup"><span data-stu-id="17d58-118">**Get-ChildItem** can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="17d58-119">Pode efetuar a filtragem complexas com base nas outras propriedades de itens utilizando o **Where-Object** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="17d58-119">You can perform complex filtering based on other properties of items by using the **Where-Object** cmdlet.</span></span> <span data-ttu-id="17d58-120">O comando seguinte localiza todas as chaves dentro HKCU:\\Software que tenham mais do que uma subchave e também de ter exatamente quatro valores:</span><span class="sxs-lookup"><span data-stu-id="17d58-120">The following command finds all keys within HKCU:\\Software that have no more than one subkey and also have exactly four values:</span></span>

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a><span data-ttu-id="17d58-121">Copiar chaves</span><span class="sxs-lookup"><span data-stu-id="17d58-121">Copying Keys</span></span>

<span data-ttu-id="17d58-122">A copiar é feito com **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="17d58-122">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="17d58-123">O comando seguinte copia HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion e todas as suas propriedades para HKCU:\\, criar uma nova chave com o nome "CurrentVersion":</span><span class="sxs-lookup"><span data-stu-id="17d58-123">The following command copies HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion and all of its properties to HKCU:\\, creating a new key named "CurrentVersion":</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

<span data-ttu-id="17d58-124">Se examinar esta nova chave no editor de registo ou utilizando **Get-ChildItem**, irá reparar que não dispõe de cópias das subchaves contidas na nova localização.</span><span class="sxs-lookup"><span data-stu-id="17d58-124">If you examine this new key in the registry editor or by using **Get-ChildItem**, you will notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="17d58-125">Para copiar todo o conteúdo de um contentor, terá de especificar o **Recurse** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="17d58-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="17d58-126">Para tornar a recursiva de comando de cópia anterior, teria de utilizar este comando:</span><span class="sxs-lookup"><span data-stu-id="17d58-126">To make the preceding copy command recursive, you would use this command:</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

<span data-ttu-id="17d58-127">Pode continuar a utilizar outras ferramentas já tiver disponíveis para efetuar cópias de sistema de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="17d58-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="17d58-128">As ferramentas de edição de registo — incluindo reg.exe, regini.exe e regedit.exe—and objetos COM que suportam a edição de registo (por exemplo, a classe de StdRegProv WScript.Shell e do WMI) pode ser utilizada a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="17d58-128">Any registry editing tools—including reg.exe, regini.exe, and regedit.exe—and COM objects that support registry editing (such as WScript.Shell and WMI's StdRegProv class) can be used from within Windows PowerShell.</span></span>

### <a name="creating-keys"></a><span data-ttu-id="17d58-129">Criação de chaves</span><span class="sxs-lookup"><span data-stu-id="17d58-129">Creating Keys</span></span>

<span data-ttu-id="17d58-130">A criação de chaves novas no registo é mais simples do que criar um novo item no sistema de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="17d58-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="17d58-131">Uma vez que todas as chaves de registo são contentores, não tem de especificar o tipo de item Basta fornecer um caminho explícito, tais como:</span><span class="sxs-lookup"><span data-stu-id="17d58-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

<span data-ttu-id="17d58-132">Também pode utilizar um caminho baseado em fornecedores para especificar uma chave:</span><span class="sxs-lookup"><span data-stu-id="17d58-132">You can also use a provider-based path to specify a key:</span></span>

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a><span data-ttu-id="17d58-133">A eliminação de chaves</span><span class="sxs-lookup"><span data-stu-id="17d58-133">Deleting Keys</span></span>

<span data-ttu-id="17d58-134">Eliminar itens é, essencialmente, igual para todos os fornecedores.</span><span class="sxs-lookup"><span data-stu-id="17d58-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="17d58-135">Os seguintes comandos irão automaticamente remover itens:</span><span class="sxs-lookup"><span data-stu-id="17d58-135">The following commands will silently remove items:</span></span>

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="17d58-136">Remover todas as chaves sob uma chave específica</span><span class="sxs-lookup"><span data-stu-id="17d58-136">Removing All Keys Under a Specific Key</span></span>

<span data-ttu-id="17d58-137">Pode remover os itens que contêm utilizando **Remove-Item**, mas será solicitado para confirmar a remoção, se o item contém tudo o resto.</span><span class="sxs-lookup"><span data-stu-id="17d58-137">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="17d58-138">Por exemplo, se vamos tentar eliminar o HKCU:\\CurrentVersion subchave criámos, vemos isto:</span><span class="sxs-lookup"><span data-stu-id="17d58-138">For example, if we attempt to delete the HKCU:\\CurrentVersion subkey we created, we see this:</span></span>

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="17d58-139">Para eliminar os itens que contêm sem pedir confirmação, especifique o **-Recurse** parâmetro:</span><span class="sxs-lookup"><span data-stu-id="17d58-139">To delete contained items without prompting, specify the **-Recurse** parameter:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="17d58-140">Se pretender remover todos os itens no HKCU:\\CurrentVersion mas não HKCU:\\CurrentVersion próprio, em vez disso, pode utilizar:</span><span class="sxs-lookup"><span data-stu-id="17d58-140">If you wanted to remove all items within HKCU:\\CurrentVersion but not HKCU:\\CurrentVersion itself, you could instead use:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```