---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Cmdlets novos e atualizados
ms.openlocfilehash: 9ec31c89c0bc4b111b40e2d4725fa0782a573204
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856246"
---
# <a name="new-and-updated-cmdlets"></a><span data-ttu-id="fe1fa-103">Cmdlets novos e atualizados</span><span class="sxs-lookup"><span data-stu-id="fe1fa-103">New and updated cmdlets</span></span>

<span data-ttu-id="fe1fa-104">Adicionámos novos e atualizados cmdlets existentes com base nos comentários da Comunidade.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-104">We have added new and updated existing cmdlets based on feedback from the community.</span></span>

## <a name="archive-cmdlets"></a><span data-ttu-id="fe1fa-105">Archive cmdlets</span><span class="sxs-lookup"><span data-stu-id="fe1fa-105">Archive cmdlets</span></span>

<span data-ttu-id="fe1fa-106">Dois novos cmdlets `Compress-Archive` e `Expand-Archive`, vou comprimir e expanda arquivos ZIP.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-106">Two new cmdlets, `Compress-Archive` and `Expand-Archive`, let you compress and expand ZIP files.</span></span>

<span data-ttu-id="fe1fa-107">Para obter mais informações, consulte a [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) documentação do módulo.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-107">For more information, see the [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) module documentation.</span></span>

## <a name="catalog-cmdlets"></a><span data-ttu-id="fe1fa-108">Cmdlets Catalog</span><span class="sxs-lookup"><span data-stu-id="fe1fa-108">Catalog Cmdlets</span></span>

<span data-ttu-id="fe1fa-109">Foram adicionados dois novos cmdlets no módulo Microsoft.PowerShell.Security.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-109">Two new cmdlets have been added in the Microsoft.PowerShell.Security module.</span></span>

- [<span data-ttu-id="fe1fa-110">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="fe1fa-110">New-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [<span data-ttu-id="fe1fa-111">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="fe1fa-111">Test-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

<span data-ttu-id="fe1fa-112">Estes gerarem e validar os arquivos de catálogo do Windows.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-112">These generate and validate Windows catalog files.</span></span>

## <a name="clipboard-cmdlets"></a><span data-ttu-id="fe1fa-113">Cmdlets de área de transferência</span><span class="sxs-lookup"><span data-stu-id="fe1fa-113">Clipboard cmdlets</span></span>

<span data-ttu-id="fe1fa-114">`Get-Clipboard` e `Set-Clipboard` facilitar a transferência de conteúdo de e para uma sessão do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-114">`Get-Clipboard` and `Set-Clipboard` make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="fe1fa-115">Os cmdlets de área de transferência suporta imagens, arquivos de áudio, listas de ficheiro e texto.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-115">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

<span data-ttu-id="fe1fa-116">Para mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="fe1fa-116">For more information, see:</span></span>

- [<span data-ttu-id="fe1fa-117">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="fe1fa-117">Get-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [<span data-ttu-id="fe1fa-118">Área de transferência de conjunto</span><span class="sxs-lookup"><span data-stu-id="fe1fa-118">Set-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="fe1fa-119">Cmdlets de sintaxe de mensagem (CMS) criptográfico</span><span class="sxs-lookup"><span data-stu-id="fe1fa-119">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="fe1fa-120">Os cmdlets de sintaxe de mensagem criptográfica suportam a encriptação e desencriptação de conteúdo utilizando o formato de padrão IETF para proteger criptograficamente mensagens conforme documentado [RFC5652](https://tools.ietf.org/html/rfc5652).</span><span class="sxs-lookup"><span data-stu-id="fe1fa-120">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

<span data-ttu-id="fe1fa-121">A encriptação de CMS padrão implementa a criptografia de chave pública, em que a chave utilizada para encriptar o conteúdo (a *chave pública*) e a chave utilizada para desencriptar o conteúdo (a *chave privada*) estão separados.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-121">The CMS encryption standard implements public key cryptography, where the key used to encrypt content (the *public key*) and the key used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="fe1fa-122">A chave pública pode ser partilhada amplamente e não dados confidenciais.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-122">Your public key can be shared widely and is not sensitive data.</span></span> <span data-ttu-id="fe1fa-123">Só pode ser desencriptado qualquer conteúdo encriptado com a chave pública com a chave privada.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-123">Any content encrypted with the public key can only be decrypted using the private key.</span></span> <span data-ttu-id="fe1fa-124">Para obter mais informações, consulte [criptografia de chave pública](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="fe1fa-124">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="fe1fa-125">Para mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="fe1fa-125">For more information see:</span></span>

- [<span data-ttu-id="fe1fa-126">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="fe1fa-126">Get-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage.md)
- [<span data-ttu-id="fe1fa-127">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="fe1fa-127">Protect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage.md)
- [<span data-ttu-id="fe1fa-128">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="fe1fa-128">Unprotect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/rotect-CmsMessage.md)

<span data-ttu-id="fe1fa-129">Certificados necessitem de um identificador exclusivo de utilização de chave (EKU), como 'Assinatura de código' ou 'Encriptados Mail', para identificá-los como certificados de encriptação de dados no PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-129">Certificates require a unique key usage identifier (EKU), such as 'Code Signing' or 'Encrypted Mail', to identify them as data encryption certificates in PowerShell.</span></span> <span data-ttu-id="fe1fa-130">Para ver os certificados de encriptação de documentos no fornecedor de certificado, pode utilizar o **DocumentEncryptionCert** parâmetro dinâmico de `Get-ChildItem`:</span><span class="sxs-lookup"><span data-stu-id="fe1fa-130">To view document encryption certificates in the certificate provider, you can use the **DocumentEncryptionCert** dynamic parameter of `Get-ChildItem`:</span></span>

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a><span data-ttu-id="fe1fa-131">Extrair e analisar objetos estruturados do conteúdo de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fe1fa-131">Extract and parse structured objects from string content</span></span>

### <a name="convertfrom-string"></a><span data-ttu-id="fe1fa-132">ConvertFrom-String</span><span class="sxs-lookup"><span data-stu-id="fe1fa-132">ConvertFrom-String</span></span>

<span data-ttu-id="fe1fa-133">O novo `ConvertFrom-String` cmdlet oferece suporte a dois modos:</span><span class="sxs-lookup"><span data-stu-id="fe1fa-133">The new `ConvertFrom-String` cmdlet supports two modes:</span></span>

- <span data-ttu-id="fe1fa-134">Basic delimitados por análise</span><span class="sxs-lookup"><span data-stu-id="fe1fa-134">Basic delimited parsing</span></span>
- <span data-ttu-id="fe1fa-135">Gerado automaticamente baseadas no exemplo de análise</span><span class="sxs-lookup"><span data-stu-id="fe1fa-135">Auto generated example-driven parsing</span></span>

<span data-ttu-id="fe1fa-136">Análise delimitados, por predefinição, divide a entrada em espaço em branco e atribui os nomes das propriedades aos grupos resultantes.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-136">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span>

<span data-ttu-id="fe1fa-137">O **UpdateTemplate** parâmetro guarda os resultados do algoritmo de aprendizado num comentário no ficheiro de modelo.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-137">The **UpdateTemplate** parameter saves the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="fe1fa-138">Isso torna o aprendizado processar (a fase mais lenta) um custo único.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-138">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="fe1fa-139">Executar `ConvertFrom-String` com um modelo que contém o algoritmo de aprendizagem codificada agora é quase instantânea.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-139">Running `ConvertFrom-String` with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

<span data-ttu-id="fe1fa-140">Para obter mais informações, consulte [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span><span class="sxs-lookup"><span data-stu-id="fe1fa-140">For more information, see [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span></span>

### <a name="convert-string"></a><span data-ttu-id="fe1fa-141">Convert-String</span><span class="sxs-lookup"><span data-stu-id="fe1fa-141">Convert-String</span></span>

<span data-ttu-id="fe1fa-142">`Convert-String` permite-lhe fornecer antes e depois de exemplos de como pretende que o texto deve parecer.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-142">`Convert-String` allows you to provide before and after examples of how you want text to look.</span></span> <span data-ttu-id="fe1fa-143">O cmdlet formata automaticamente o seu texto.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-143">The cmdlet formats your text automatically.</span></span>

<span data-ttu-id="fe1fa-144">Para obter mais informações, consulte [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span><span class="sxs-lookup"><span data-stu-id="fe1fa-144">For more information, see [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span></span>

## <a name="updates-to-fileinfo-object"></a><span data-ttu-id="fe1fa-145">Atualizações do objeto FileInfo</span><span class="sxs-lookup"><span data-stu-id="fe1fa-145">Updates to FileInfo object</span></span>

<span data-ttu-id="fe1fa-146">Informações de versão do ficheiro podem ser equivocado, especialmente em casos em que o ficheiro foi corrigido.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-146">File version information can be misleading, especially in cases where the file was patched.</span></span> <span data-ttu-id="fe1fa-147">WMF 5.0 adiciona novos **FileVersionRaw** e **ProductVersionRaw** propriedades do script **FileInfo** objetos.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-147">WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to **FileInfo** objects.</span></span>
<span data-ttu-id="fe1fa-148">Aqui estão as propriedades, tal como apresentado para powershell.exe (partindo do princípio de $pid é o ID do processo do PowerShell):</span><span class="sxs-lookup"><span data-stu-id="fe1fa-148">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a><span data-ttu-id="fe1fa-149">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="fe1fa-149">Format-Hex</span></span>

<span data-ttu-id="fe1fa-150">`Format-Hex` permite-lhe ver o texto ou dados binários em formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-150">`Format-Hex` lets you view text or binary data in hexadecimal format.</span></span>

<span data-ttu-id="fe1fa-151">Para obter mais informações, consulte [formato hexadecimal](/powershell/module/microsoft.powershell.utility/format-hex).</span><span class="sxs-lookup"><span data-stu-id="fe1fa-151">For more information, see [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).</span></span>

## <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="fe1fa-152">Tem de GET-ChildItem - parâmetro de profundidade</span><span class="sxs-lookup"><span data-stu-id="fe1fa-152">Get-ChildItem has -Depth parameter</span></span>

<span data-ttu-id="fe1fa-153">`Get-ChildItem` tem agora uma **profundidade** parâmetro para utilização com **Recurse** para limitar a recursão:</span><span class="sxs-lookup"><span data-stu-id="fe1fa-153">`Get-ChildItem` now has a **Depth** parameter for use with **Recurse** to limit the recursion:</span></span>

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="fe1fa-154">Suporte de módulos para a declaração de intervalos de versão (1. \*, etc.)</span><span class="sxs-lookup"><span data-stu-id="fe1fa-154">Modules support for declaring version ranges (1.\*, etc)</span></span>

<span data-ttu-id="fe1fa-155">Agora pode combinar **MinimumVersion** e **MaximumVersion** para importar o módulo dentro do intervalo específico.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-155">You can now combine **MinimumVersion** and **MaximumVersion** to import module within specific range.</span></span> <span data-ttu-id="fe1fa-156">Os parâmetros também suportam carateres universais.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-156">The parameters also support wildcards.</span></span>

```powershell
Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*
```

```Output
VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

## <a name="new-guid"></a><span data-ttu-id="fe1fa-157">New-Guid</span><span class="sxs-lookup"><span data-stu-id="fe1fa-157">New-Guid</span></span>

<span data-ttu-id="fe1fa-158">Há muitos cenários em que youneed para identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-158">There are many scenarios where youneed for unique identifier.</span></span> <span data-ttu-id="fe1fa-159">O `New-GUID` cmdlet fornece uma forma simple de criar um novo GUID.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-159">The `New-GUID` cmdlet provides a simple way to create a new GUID.</span></span>

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a><span data-ttu-id="fe1fa-160">Parâmetro NoNewLine</span><span class="sxs-lookup"><span data-stu-id="fe1fa-160">NoNewLine parameter</span></span>

<span data-ttu-id="fe1fa-161">`Out-File`, `Add-Content`, e `Set-Content` agora tem uma nova **NoNewline** comutador que omite uma nova linha após a saída.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-161">`Out-File`, `Add-Content`, and `Set-Content` now have a new **NoNewline** switch which omits a new line after the output.</span></span> <span data-ttu-id="fe1fa-162">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="fe1fa-162">For example:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt

```Output
This is a single sentence.
```

<span data-ttu-id="fe1fa-163">Sem **NoNewline** especificado, cada fragmento seria numa linha separada:</span><span class="sxs-lookup"><span data-stu-id="fe1fa-163">Without **NoNewline** specified, each fragment would be on a separate line:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt
"a single " | Add-Content -Path Example.txt
"sentence." | Add-Content -Path Example.txt
Get-Content .\Example.txt
```

```Output
This is
a single
sentence.
```

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a><span data-ttu-id="fe1fa-164">Interagir com ligações simbólicas através dos cmdlets de Item melhorados</span><span class="sxs-lookup"><span data-stu-id="fe1fa-164">Interact with Symbolic links using improved Item cmdlets</span></span>

<span data-ttu-id="fe1fa-165">O cmdlet de Item e alguns cmdlets relacionados foram estendidos para oferecer suporte a links simbólicos.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-165">The Item cmdlet and a few related cmdlets have been extended to support symbolic links.</span></span>

### <a name="symbolic-link-files"></a><span data-ttu-id="fe1fa-166">Arquivos de link simbólico</span><span class="sxs-lookup"><span data-stu-id="fe1fa-166">Symbolic link files</span></span>

<span data-ttu-id="fe1fa-167">Neste exemplo, vamos criar um novo ficheiro de ligação simbólica designado MySymLinkFile.txt em C:\Temp que liga à $pshome\profile.ps1.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-167">In this example, we create a new symbolic link file named MySymLinkFile.txt in C:\Temp which links to $pshome\profile.ps1.</span></span> <span data-ttu-id="fe1fa-168">Todos os três exemplos produzem o mesmo resultado.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-168">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a><span data-ttu-id="fe1fa-169">Diretórios de link simbólico</span><span class="sxs-lookup"><span data-stu-id="fe1fa-169">Symbolic link directories</span></span>

<span data-ttu-id="fe1fa-170">Neste exemplo, vamos criar um novo diretório de ligação simbólica MySymLinkDir em C:\Temp, que contém ligações para a pasta de $pshome com o nome.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-170">In this example, we create a new symbolic link directory named MySymLinkDir in C:\Temp which links to the $pshome folder.</span></span> <span data-ttu-id="fe1fa-171">Todos os três exemplos produzem o mesmo resultado.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-171">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a><span data-ttu-id="fe1fa-172">Ligações fixas</span><span class="sxs-lookup"><span data-stu-id="fe1fa-172">Hard links</span></span>

<span data-ttu-id="fe1fa-173">As mesmo combinações de **caminho** e **nome** permitido conforme descrito acima.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-173">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a><span data-ttu-id="fe1fa-174">Junções de diretório</span><span class="sxs-lookup"><span data-stu-id="fe1fa-174">Directory junctions</span></span>

<span data-ttu-id="fe1fa-175">As mesmo combinações de **caminho** e **nome** permitido conforme descrito acima.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-175">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a><span data-ttu-id="fe1fa-176">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="fe1fa-176">Get-ChildItem</span></span>

<span data-ttu-id="fe1fa-177">`Get-ChildItem` apresenta agora um "l" na **modo** propriedade para indicar um link simbólico ficheiro ou diretório.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-177">`Get-ChildItem` now displays an 'l' in the **Mode** property to indicate a symbolic link file or directory.</span></span>

```powershell
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode       LastWriteTime Length Name
----       ------------- ------ ----
-a---- 6/13/2014 3:00 PM     16 File.txt
d----- 6/13/2014 3:00 PM        Directory
-a---l 6/13/2014 3:21 PM      0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM        MySymLinkDir
-a---l 6/13/2014 3:23 PM  23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM        MyJunctionDir
```

### <a name="remove-item"></a><span data-ttu-id="fe1fa-178">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="fe1fa-178">Remove-Item</span></span>

<span data-ttu-id="fe1fa-179">Remover links simbólicos funciona como qualquer outro tipo de item a remover.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-179">Removing symbolic links works like removing any other item type.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

<span data-ttu-id="fe1fa-180">Utilize o **força** parâmetro para remover os ficheiros no diretório de destino e a ligação simbólica.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-180">Use the **Force** parameter to remove the files in the target directory and the symbolic link.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a><span data-ttu-id="fe1fa-181">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="fe1fa-181">New-TemporaryFile</span></span>

<span data-ttu-id="fe1fa-182">Por vezes, nos seus scripts, tem de criar um arquivo temporário.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-182">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="fe1fa-183">Agora pode fazer isso com o `New-TemporaryFile` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="fe1fa-183">You can now do this with the `New-TemporaryFile` cmdlet:</span></span>

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a><span data-ttu-id="fe1fa-184">Gestão de Comutador de Rede com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe1fa-184">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="fe1fa-185">Os cmdlets de comutador de rede, introduzidos no WMF 5.0, permitem-lhe aplicar o comutador, LAN virtual (VLAN) e básica configuração de porta do comutador de rede de camada 2 a comutadores de rede com logótipo de certificação do Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-185">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="fe1fa-186">Utilizando estes cmdlets pode efetuar:</span><span class="sxs-lookup"><span data-stu-id="fe1fa-186">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="fe1fa-187">Global mudar a configuração, tais como:</span><span class="sxs-lookup"><span data-stu-id="fe1fa-187">Global switch configuration, such as:</span></span>
  - <span data-ttu-id="fe1fa-188">Nome de anfitrião do conjunto</span><span class="sxs-lookup"><span data-stu-id="fe1fa-188">Set host name</span></span>
  - <span data-ttu-id="fe1fa-189">Faixa de comutador de conjunto</span><span class="sxs-lookup"><span data-stu-id="fe1fa-189">Set switch banner</span></span>
  - <span data-ttu-id="fe1fa-190">Manter a configuração</span><span class="sxs-lookup"><span data-stu-id="fe1fa-190">Persist configuration</span></span>
  - <span data-ttu-id="fe1fa-191">Ativar ou desativar funcionalidade</span><span class="sxs-lookup"><span data-stu-id="fe1fa-191">Enable or disable feature</span></span>

- <span data-ttu-id="fe1fa-192">Configuração de VLAN:</span><span class="sxs-lookup"><span data-stu-id="fe1fa-192">VLAN configuration:</span></span>
  - <span data-ttu-id="fe1fa-193">Criar ou remover VLAN</span><span class="sxs-lookup"><span data-stu-id="fe1fa-193">Create or remove VLAN</span></span>
  - <span data-ttu-id="fe1fa-194">Ativar ou desativar a VLAN</span><span class="sxs-lookup"><span data-stu-id="fe1fa-194">Enable or disable VLAN</span></span>
  - <span data-ttu-id="fe1fa-195">Enumerar VLAN</span><span class="sxs-lookup"><span data-stu-id="fe1fa-195">Enumerate VLAN</span></span>
  - <span data-ttu-id="fe1fa-196">Nome amigável do conjunto a uma VLAN</span><span class="sxs-lookup"><span data-stu-id="fe1fa-196">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="fe1fa-197">Configuração da porta de camada 2:</span><span class="sxs-lookup"><span data-stu-id="fe1fa-197">Layer 2 port configuration:</span></span>
  - <span data-ttu-id="fe1fa-198">Enumerar portas</span><span class="sxs-lookup"><span data-stu-id="fe1fa-198">Enumerate ports</span></span>
  - <span data-ttu-id="fe1fa-199">Ativar ou desativar as portas</span><span class="sxs-lookup"><span data-stu-id="fe1fa-199">Enable or disable ports</span></span>
  - <span data-ttu-id="fe1fa-200">Modos de porta do conjunto e propriedades</span><span class="sxs-lookup"><span data-stu-id="fe1fa-200">Set port modes and properties</span></span>
  - <span data-ttu-id="fe1fa-201">Adicionar ou associar a VLAN de ramal ou acesso na porta</span><span class="sxs-lookup"><span data-stu-id="fe1fa-201">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="fe1fa-202">Para obter mais informações, consulte a [NetworkSwitchManager](/powershell/module/networkswitchmanager/) documentação.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-202">For more information, see the [NetworkSwitchManager](/powershell/module/networkswitchmanager/) documentation.</span></span>

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="fe1fa-203">Gerar os cmdlets do PowerShell com base num ponto de final de OData com ODataUtils</span><span class="sxs-lookup"><span data-stu-id="fe1fa-203">Generate PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>

<span data-ttu-id="fe1fa-204">O módulo de ODataUtils permite a geração de cmdlets do PowerShell a partir de pontos de extremidade REST que dão suporte a OData.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-204">The ODataUtils module allows generation of PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="fe1fa-205">O módulo de Microsoft.PowerShell.ODataUtils inclui as seguintes funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="fe1fa-205">The Microsoft.PowerShell.ODataUtils module includes the following features:</span></span>

- <span data-ttu-id="fe1fa-206">Canal de informações adicionais do ponto de extremidade do lado do servidor para o lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-206">Channel additional information from server-side endpoint to client side.</span></span>
- <span data-ttu-id="fe1fa-207">Suporte de paginação do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="fe1fa-207">Client-side paging support</span></span>
- <span data-ttu-id="fe1fa-208">Filtragem do lado do servidor utilizando o - parâmetro selecione</span><span class="sxs-lookup"><span data-stu-id="fe1fa-208">Server-side filtering by using the -Select parameter</span></span>
- <span data-ttu-id="fe1fa-209">Suporte para cabeçalhos de solicitação da web</span><span class="sxs-lookup"><span data-stu-id="fe1fa-209">Support for web request headers</span></span>

<span data-ttu-id="fe1fa-210">Os cmdlets do proxy gerados pela `Export-ODataEndPointProxy` cmdlet fornecem informações adicionais do ponto de final de OData do lado do servidor sobre o **informações** stream.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-210">The proxy cmdlets generated by the `Export-ODataEndPointProxy` cmdlet provide additional information from the server-side OData endpoint on the **Information** stream.</span></span>

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

<span data-ttu-id="fe1fa-211">No exemplo a seguir, estamos a obter o produto superior e capturar a saída no `$infoStream` variável.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-211">In the following example, we are retrieving top product and capturing the output in the `$infoStream` variable.</span></span>

<span data-ttu-id="fe1fa-212">Ao especificar **IncludeTotalResponseCount** parâmetro, podemos obter a contagem total de todos os **produto** registos disponíveis no servidor.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-212">By specifying **IncludeTotalResponseCount** parameter, we get the total count of all the **Product** records available on the server.</span></span>

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

<span data-ttu-id="fe1fa-213">Pode obter os registos do servidor em lotes com o suporte de paginação do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-213">You can get the records from the server in batches using client-side paging support.</span></span> <span data-ttu-id="fe1fa-214">Isto é útil quando tem de obter uma grande quantidade de dados do servidor através da rede.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-214">This is useful when you must get a large amount of data from the server over the network.</span></span>

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

<span data-ttu-id="fe1fa-215">Os cmdlets do proxy gerado suportam o **selecione** parâmetro que é utilizado como um filtro para receber apenas as propriedades de registo que o cliente precisa.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-215">The generated proxy cmdlets support the **Select** parameter that is used as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="fe1fa-216">A filtragem ocorre no servidor, o que reduz a quantidade de dados que são transferidos através da rede.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-216">The filtering occurs on the server, which reduces the amount of data that is transferred over the network.</span></span>

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="fe1fa-217">O `Export-ODataEndpointProxy` cmdlet e os cmdlets do proxy gerados por ele, suportam agora o **cabeçalhos** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-217">The `Export-ODataEndpointProxy` cmdlet, and the proxy cmdlets generated by it, now support the **Headers** parameter.</span></span> <span data-ttu-id="fe1fa-218">O cabeçalho pode ser utilizado para obter informações adicionais esperadas pelo ponto de final de OData do channel.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-218">The header can be used to channel additional information expected by the OData endpoint.</span></span>

<span data-ttu-id="fe1fa-219">No exemplo a seguir, uma tabela de hash que contém uma chave de subscrição é fornecida para o **cabeçalhos** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-219">In the following example, a hash table containing a Subscription key is provided to the **Headers** parameter.</span></span> <span data-ttu-id="fe1fa-220">Este é um exemplo típico para serviços que esperam uma chave de subscrição para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="fe1fa-220">This is a typical example for services that are expecting a Subscription key for authentication.</span></span>

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
