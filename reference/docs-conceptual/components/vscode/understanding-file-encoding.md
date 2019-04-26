---
title: Compreender a codificação de ficheiros no VSCode e no PowerShell
description: Configurar a codificação do ficheiro no VSCode e no PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: 6a00e45b3700f72f78e2fbcdf6e317f3a17b53c0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058442"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a><span data-ttu-id="4834b-103">Compreender a codificação de ficheiros no VSCode e no PowerShell</span><span class="sxs-lookup"><span data-stu-id="4834b-103">Understanding file encoding in VSCode and PowerShell</span></span>

<span data-ttu-id="4834b-104">Quando utilizar o VS Code para criar e editar scripts do PowerShell, é importante que os ficheiros são guardados com o formato de codificação de caracteres corretas.</span><span class="sxs-lookup"><span data-stu-id="4834b-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="4834b-105">O que é a codificação do ficheiro e por que é importante?</span><span class="sxs-lookup"><span data-stu-id="4834b-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="4834b-106">VSCode gerencia a interface entre um humano cadeias de caracteres de inserção de caracteres num buffer e blocos de leitura/gravação de bytes para o sistema de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="4834b-106">VSCode manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="4834b-107">Quando o VSCode salva um arquivo, ele usa um codificação para fazer isso de texto.</span><span class="sxs-lookup"><span data-stu-id="4834b-107">When VSCode saves a file, it uses a text encoding to do this.</span></span>

<span data-ttu-id="4834b-108">Da mesma forma, quando PowerShell executa um script, tem de converter os bytes num arquivo de carateres para reconstruir o arquivo num programa do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4834b-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="4834b-109">Uma vez que o VSCode escreve o ficheiro e PowerShell lê o arquivo, têm de utilizar o mesmo sistema de codificação.</span><span class="sxs-lookup"><span data-stu-id="4834b-109">Since VSCode writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="4834b-110">Este processo de analisar um script do PowerShell é: *bytes* -> *carateres* -> *tokens*  ->   *árvore de sintaxe abstrata* -> *execução*.</span><span class="sxs-lookup"><span data-stu-id="4834b-110">This process of parsing a PowerShell script goes: *bytes* -> *characters* -> *tokens* -> *abstract syntax tree* -> *execution*.</span></span>

<span data-ttu-id="4834b-111">VSCode e PowerShell são instalados com uma configuração de codificação sensível predefinido.</span><span class="sxs-lookup"><span data-stu-id="4834b-111">Both VSCode and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="4834b-112">No entanto, a codificação padrão utilizado pelo PowerShell mudou com o lançamento do PowerShell Core (v6.x).</span><span class="sxs-lookup"><span data-stu-id="4834b-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="4834b-113">Para garantir que tenha sem problemas com o PowerShell ou a extensão de PowerShell no VSCode, terá de configurar as definições de VSCode e o PowerShell corretamente.</span><span class="sxs-lookup"><span data-stu-id="4834b-113">To ensure you have no problems using PowerShell or the PowerShell extension in VSCode, you need to configure your VSCode and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="4834b-114">Causas comuns de problemas de codificação</span><span class="sxs-lookup"><span data-stu-id="4834b-114">Common causes of encoding issues</span></span>

<span data-ttu-id="4834b-115">Problemas de codificação ocorrerem quando a codificação de VSCode ou o ficheiro de script não coincide com a codificação esperado do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4834b-115">Encoding problems occur when the encoding of VSCode or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="4834b-116">Não é possível para o PowerShell determinar automaticamente a codificação de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="4834b-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="4834b-117">É mais provável ter problemas de codificação quando estiver a utilizar carateres não os [conjunto de carateres ASCII de 7 bits](https://ascii.cl/).</span><span class="sxs-lookup"><span data-stu-id="4834b-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="4834b-118">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4834b-118">For example:</span></span>

- <span data-ttu-id="4834b-119">Accented carateres latinos (`É`, `ü`)</span><span class="sxs-lookup"><span data-stu-id="4834b-119">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="4834b-120">Carateres não latinos, como Cirílico (`Д`, `Ц`)</span><span class="sxs-lookup"><span data-stu-id="4834b-120">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="4834b-121">Chinês Han (`脚`, `本`)</span><span class="sxs-lookup"><span data-stu-id="4834b-121">Han Chinese (`脚`, `本`)</span></span>

<span data-ttu-id="4834b-122">Motivos comuns para problemas de codificação são:</span><span class="sxs-lookup"><span data-stu-id="4834b-122">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="4834b-123">As codificações de VSCode e o PowerShell não tiverem sido alteradas nas predefinições.</span><span class="sxs-lookup"><span data-stu-id="4834b-123">The encodings of VSCode and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="4834b-124">Para PowerShell 5.1 e abaixo, a predefinição de codificação é diferente do VSCode.</span><span class="sxs-lookup"><span data-stu-id="4834b-124">For PowerShell 5.1 and below, the default encoding is different from VSCode's.</span></span>
- <span data-ttu-id="4834b-125">Outro editor abriu e substituir o arquivo numa codificação de novo.</span><span class="sxs-lookup"><span data-stu-id="4834b-125">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="4834b-126">Muitas vezes, isso acontece com o ISE.</span><span class="sxs-lookup"><span data-stu-id="4834b-126">This often happens with the ISE.</span></span>
- <span data-ttu-id="4834b-127">O ficheiro é verificado no controle de fonte numa codificação que é diferente do que VSCode ou PowerShell espera.</span><span class="sxs-lookup"><span data-stu-id="4834b-127">The file is checked into source control in an encoding that is different from what VSCode or PowerShell expects.</span></span> <span data-ttu-id="4834b-128">Isto pode acontecer quando os funcionários utilizam editores com configurações de codificação diferentes.</span><span class="sxs-lookup"><span data-stu-id="4834b-128">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="4834b-129">Como descobrir se tiver problemas de codificação</span><span class="sxs-lookup"><span data-stu-id="4834b-129">How to tell when you have encoding issues</span></span>

<span data-ttu-id="4834b-130">Erros de codificação, muitas vezes, apresentam próprios como analisar erros nos scripts.</span><span class="sxs-lookup"><span data-stu-id="4834b-130">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="4834b-131">Se encontrar seqüências de caracteres estranho em seu script, isso pode ser o problema.</span><span class="sxs-lookup"><span data-stu-id="4834b-131">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="4834b-132">No exemplo abaixo, en-dash (`–`) é apresentado como os caracteres `â€“`:</span><span class="sxs-lookup"><span data-stu-id="4834b-132">In the example below, an en-dash (`–`) appears as the characters `â€“`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="4834b-133">Este problema ocorre porque o VSCode codifica o caráter `–` em UTF-8, como os bytes `0xE2 0x80 0x93`.</span><span class="sxs-lookup"><span data-stu-id="4834b-133">This problem occurs because VSCode encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span>
<span data-ttu-id="4834b-134">Quando esses bytes são descodificados como Windows 1252, eles são interpretados como os caracteres `â€“`.</span><span class="sxs-lookup"><span data-stu-id="4834b-134">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€“`.</span></span>

<span data-ttu-id="4834b-135">Algumas seqüências de caracteres estranho que poderá ver incluem:</span><span class="sxs-lookup"><span data-stu-id="4834b-135">Some strange character sequences that you might see include:</span></span>

<!-- markdownlint-disable MD038 -->
- <span data-ttu-id="4834b-136">`â€“` em vez de `–`</span><span class="sxs-lookup"><span data-stu-id="4834b-136">`â€“` instead of `–`</span></span>
- <span data-ttu-id="4834b-137">`â€”` em vez de `—`</span><span class="sxs-lookup"><span data-stu-id="4834b-137">`â€”` instead of `—`</span></span>
- <span data-ttu-id="4834b-138">`Ã„2` em vez de `Ä`</span><span class="sxs-lookup"><span data-stu-id="4834b-138">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="4834b-139">`Â` em vez de ` ` (um espaço sem quebra)</span><span class="sxs-lookup"><span data-stu-id="4834b-139">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="4834b-140">`Ã©` em vez de `é`</span><span class="sxs-lookup"><span data-stu-id="4834b-140">`Ã©` instead of `é`</span></span>
<!-- markdownlint-enable MD038 -->

<span data-ttu-id="4834b-141">Neste útil [referência](https://www.i18nqa.com/debug/utf8-debug.html) apresenta uma lista de padrões comuns que indicar um problema de codificação UTF-8/Windows-1252.</span><span class="sxs-lookup"><span data-stu-id="4834b-141">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a><span data-ttu-id="4834b-142">Como a extensão de PowerShell no VSCode interage com codificações</span><span class="sxs-lookup"><span data-stu-id="4834b-142">How the PowerShell extension in VSCode interacts with encodings</span></span>

<span data-ttu-id="4834b-143">A extensão de PowerShell interage com os scripts de diversas formas:</span><span class="sxs-lookup"><span data-stu-id="4834b-143">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="4834b-144">Quando os scripts são editados no VSCode, o conteúdo será enviado por VSCode para a extensão.</span><span class="sxs-lookup"><span data-stu-id="4834b-144">When scripts are edited in VSCode, the contents are sent by VSCode to the extension.</span></span> <span data-ttu-id="4834b-145">O [Protocolo de servidor de idioma][] estipula que este conteúdo é transferido em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="4834b-145">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="4834b-146">Por conseguinte, não é possível que a extensão obter a codificação errada.</span><span class="sxs-lookup"><span data-stu-id="4834b-146">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
2. <span data-ttu-id="4834b-147">Quando os scripts são executados diretamente na consola do integrada, eles estão lida no arquivo do PowerShell diretamente.</span><span class="sxs-lookup"><span data-stu-id="4834b-147">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="4834b-148">Se a codificação do PowerShell difere do VSCode, algo pode dar errado aqui.</span><span class="sxs-lookup"><span data-stu-id="4834b-148">If PowerShell's encoding differs from VSCode's, something can go wrong here.</span></span>
3. <span data-ttu-id="4834b-149">Quando um script que está aberto no VSCode faz referência a outro script que não está aberto no VSCode, a extensão é retrocede para carregar o conteúdo desse script do sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="4834b-149">When a script that is open in VSCode references another script that is not open in VSCode, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="4834b-150">A extensão de PowerShell está predefinido para a codificação UTF-8, mas usa [marca de ordem de byte][], ou BOM, deteção seleciona a codificação correta.</span><span class="sxs-lookup"><span data-stu-id="4834b-150">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="4834b-151">O problema ocorre quando partindo do princípio de que a codificação de formatos de BOM sem (como [UTF-8][] com nenhuma BOM e [Windows-1252][]).</span><span class="sxs-lookup"><span data-stu-id="4834b-151">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span>
<span data-ttu-id="4834b-152">A extensão de PowerShell padrão é UTF-8.</span><span class="sxs-lookup"><span data-stu-id="4834b-152">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="4834b-153">A extensão não é possível alterar as definições de codificação do VSCode.</span><span class="sxs-lookup"><span data-stu-id="4834b-153">The extension cannot change VSCode's encoding settings.</span></span>
<span data-ttu-id="4834b-154">Para obter mais informações, consulte [emitir #824](https://github.com/Microsoft/vscode/issues/824).</span><span class="sxs-lookup"><span data-stu-id="4834b-154">For more information, see [issue #824](https://github.com/Microsoft/vscode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="4834b-155">Escolher a codificação correta</span><span class="sxs-lookup"><span data-stu-id="4834b-155">Choosing the right encoding</span></span>

<span data-ttu-id="4834b-156">Aplicativos e sistemas diferentes, podem utilizar diferentes codificações:</span><span class="sxs-lookup"><span data-stu-id="4834b-156">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="4834b-157">No .NET Standard na web e no mundo do Linux, UTF-8 é agora a codificação dominante.</span><span class="sxs-lookup"><span data-stu-id="4834b-157">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="4834b-158">Muitas aplicações de .NET Framework utilizam [UTF-16][].</span><span class="sxs-lookup"><span data-stu-id="4834b-158">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="4834b-159">Por motivos históricos, às vezes, isso é chamado de "Unicode", um termo que agora se refere a uma ampla [padrão](https://en.wikipedia.org/wiki/Unicode) que inclui o UTF-8 e UTF-16.</span><span class="sxs-lookup"><span data-stu-id="4834b-159">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="4834b-160">No Windows, muitos aplicativos nativos que são anteriores às Unicode continuam a utilizar o Windows 1252 por predefinição.</span><span class="sxs-lookup"><span data-stu-id="4834b-160">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="4834b-161">Codificações Unicode também tem o conceito de uma ordem de byte marcar (BOM).</span><span class="sxs-lookup"><span data-stu-id="4834b-161">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="4834b-162">BOMs ocorrerem no início do texto para dizer um Decodificador qual codificação é usando o texto.</span><span class="sxs-lookup"><span data-stu-id="4834b-162">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="4834b-163">Para codificações de multi-bytes, o BOM também indica [ordenação de bits](https://en.wikipedia.org/wiki/Endianness) da codificação.</span><span class="sxs-lookup"><span data-stu-id="4834b-163">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="4834b-164">BOMs destinam-se para ser bytes que ocorrem raramente no texto não-Unicode, permitindo uma estimativa razoável de que o texto é Unicode quando uma BOM está presente.</span><span class="sxs-lookup"><span data-stu-id="4834b-164">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="4834b-165">BOMs são opcionais e adoção não é tão popular do mundo do Linux como uma convenção confiável do UTF-8 é utilizada em qualquer lugar.</span><span class="sxs-lookup"><span data-stu-id="4834b-165">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="4834b-166">A maioria dos aplicativos de Linux presumem que a entrada de texto está codificada em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="4834b-166">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="4834b-167">Embora muitos aplicativos de Linux irão reconhecer e processar corretamente uma BOM, um número não o fizer, levando a artefactos no texto manipulado com esses aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4834b-167">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="4834b-168">**Por conseguinte**:</span><span class="sxs-lookup"><span data-stu-id="4834b-168">**Therefore**:</span></span>

- <span data-ttu-id="4834b-169">Se trabalha principalmente com aplicativos do Windows e Windows PowerShell, deve preferir uma codificação como UTF-8 com BOM ou UTF-16.</span><span class="sxs-lookup"><span data-stu-id="4834b-169">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="4834b-170">Se trabalha em todas as plataformas, deve preferir UTF-8 com BOM.</span><span class="sxs-lookup"><span data-stu-id="4834b-170">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="4834b-171">Se trabalha principalmente em contextos associados ao Linux, deve preferir UTF-8, sem BOM.</span><span class="sxs-lookup"><span data-stu-id="4834b-171">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="4834b-172">Windows 1252 e latin 1 são codificações herdadas, essencialmente, deve evitar se possível.</span><span class="sxs-lookup"><span data-stu-id="4834b-172">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="4834b-173">No entanto, alguns aplicativos mais antigos do Windows poderão depender nos mesmos.</span><span class="sxs-lookup"><span data-stu-id="4834b-173">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="4834b-174">Também vale a pena observar que a assinatura de script é [dependentes da codificação](https://github.com/PowerShell/PowerShell/issues/3466), que significa que uma alteração da codificação num script assinado exigirá resigning.</span><span class="sxs-lookup"><span data-stu-id="4834b-174">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vscode"></a><span data-ttu-id="4834b-175">Configurar o VSCode</span><span class="sxs-lookup"><span data-stu-id="4834b-175">Configuring VSCode</span></span>

<span data-ttu-id="4834b-176">Do VSCode codificação padrão é UTF-8, sem BOM.</span><span class="sxs-lookup"><span data-stu-id="4834b-176">VSCode's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="4834b-177">Para definir [Codificação do VSCode][], aceda às definições VSCode (<kbd>Ctrl</kbd>+<kbd>,</kbd>) e defina o `"files.encoding"` definição:</span><span class="sxs-lookup"><span data-stu-id="4834b-177">To set [VSCode's encoding][], go to the VSCode settings (<kbd>Ctrl</kbd>+<kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="4834b-178">Alguns valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="4834b-178">Some possible values are:</span></span>

- <span data-ttu-id="4834b-179">`utf8`: [UTF-8] sem BOM</span><span class="sxs-lookup"><span data-stu-id="4834b-179">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="4834b-180">`utf8bom`: [UTF-8] com BOM</span><span class="sxs-lookup"><span data-stu-id="4834b-180">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="4834b-181">`utf16le`: Little endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="4834b-181">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="4834b-182">`utf16be`: Big endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="4834b-182">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="4834b-183">`windows1252`: [Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="4834b-183">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="4834b-184">Deve obter uma lista pendente para isso, na vista de GUI ou ver conclusões para ele no JSON.</span><span class="sxs-lookup"><span data-stu-id="4834b-184">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="4834b-185">Também pode adicionar o seguinte para deteção automática de codificação sempre que possível:</span><span class="sxs-lookup"><span data-stu-id="4834b-185">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="4834b-186">Se não pretender que estas definições afetam todos os tipos de ficheiros, VSCode também permite que configurações por idioma.</span><span class="sxs-lookup"><span data-stu-id="4834b-186">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="4834b-187">Criar uma definição de idioma específico ao colocar configurações `[<language-name>]` campo.</span><span class="sxs-lookup"><span data-stu-id="4834b-187">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="4834b-188">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4834b-188">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="4834b-189">Configurar o PowerShell</span><span class="sxs-lookup"><span data-stu-id="4834b-189">Configuring PowerShell</span></span>

<span data-ttu-id="4834b-190">Do PowerShell codificação padrão varia dependendo da versão:</span><span class="sxs-lookup"><span data-stu-id="4834b-190">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="4834b-191">No PowerShell 6 +, a codificação predefinida é UTF-8, sem BOM em todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="4834b-191">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="4834b-192">No Windows PowerShell, a codificação predefinida é normalmente Windows-1252, uma extensão da [latin 1][], também conhecido como ISO 8859-1.</span><span class="sxs-lookup"><span data-stu-id="4834b-192">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="4834b-193">No PowerShell 5 + pode encontrar a codificação padrão com isto:</span><span class="sxs-lookup"><span data-stu-id="4834b-193">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="4834b-194">O seguinte procedimento [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) pode ser utilizado para determinar o que a codificação de sua sessão do PowerShell infere para um script sem um BOM.</span><span class="sxs-lookup"><span data-stu-id="4834b-194">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

<span data-ttu-id="4834b-195">É possível configurar o PowerShell para usar uma codificação de determinado mais normalmente, através de definições de perfil.</span><span class="sxs-lookup"><span data-stu-id="4834b-195">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span> <span data-ttu-id="4834b-196">Consulte os seguintes artigos:</span><span class="sxs-lookup"><span data-stu-id="4834b-196">See the following articles:</span></span>

- <span data-ttu-id="4834b-197">[@mklement0]da [resposta sobre codificação do PowerShell no StackOverflow](https://stackoverflow.com/a/40098904).</span><span class="sxs-lookup"><span data-stu-id="4834b-197">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="4834b-198">[@rkeithhill]da [mensagem de blogue sobre como lidar com entrada de BOM sem UTF-8 no PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span><span class="sxs-lookup"><span data-stu-id="4834b-198">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="4834b-199">Não é possível forçar o PowerShell para utilizar uma codificação específica de entrada.</span><span class="sxs-lookup"><span data-stu-id="4834b-199">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="4834b-200">PowerShell 5.1 e abaixo padrão para Windows-1252 codificação quando não existe nenhum BOM.</span><span class="sxs-lookup"><span data-stu-id="4834b-200">PowerShell 5.1 and below default to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="4834b-201">Por motivos de interoperabilidade, é melhor guardar os scripts num formato Unicode com um BOM.</span><span class="sxs-lookup"><span data-stu-id="4834b-201">For interoperability reasons, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4834b-202">Quaisquer outras ferramentas, tem esse touch PowerShell scripts podem ser afetados pelas suas escolhas de codificação ou codificar seus scripts para outra codificação.</span><span class="sxs-lookup"><span data-stu-id="4834b-202">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="4834b-203">Scripts existentes</span><span class="sxs-lookup"><span data-stu-id="4834b-203">Existing scripts</span></span>

<span data-ttu-id="4834b-204">Scripts já no sistema de ficheiros poderão ter de ser codificada novamente para a codificação escolhida novo.</span><span class="sxs-lookup"><span data-stu-id="4834b-204">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="4834b-205">Na barra de VSCode na parte inferior, verá o rótulo UTF-8.</span><span class="sxs-lookup"><span data-stu-id="4834b-205">In the bottom bar of VSCode, you'll see the label UTF-8.</span></span> <span data-ttu-id="4834b-206">Clique nele para abrir a barra de ação e selecione **guardar com codificação**.</span><span class="sxs-lookup"><span data-stu-id="4834b-206">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="4834b-207">Agora pode selecionar uma nova codificação do ficheiro em questão.</span><span class="sxs-lookup"><span data-stu-id="4834b-207">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="4834b-208">Ver [Codificação do VSCode][] para obter instruções completas.</span><span class="sxs-lookup"><span data-stu-id="4834b-208">See [VSCode's encoding][] for full instructions.</span></span>

<span data-ttu-id="4834b-209">Se precisar de codificar vários ficheiros, pode utilizar o seguinte script:</span><span class="sxs-lookup"><span data-stu-id="4834b-209">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="4834b-210">O PowerShell integrado Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="4834b-210">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="4834b-211">Se também pode editar scripts com o ISE do PowerShell, tem de sincronizar as definições de codificação aqui.</span><span class="sxs-lookup"><span data-stu-id="4834b-211">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="4834b-212">O ISE deve honrar uma BOM, mas também é possível usar a reflexão para [definir a codificação](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span><span class="sxs-lookup"><span data-stu-id="4834b-212">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="4834b-213">Tenha em atenção que isto não sejam persistentes entre as start-UPS.</span><span class="sxs-lookup"><span data-stu-id="4834b-213">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="4834b-214">Software de controlo de origem</span><span class="sxs-lookup"><span data-stu-id="4834b-214">Source control software</span></span>

<span data-ttu-id="4834b-215">Algumas ferramentas de controle de origem, como o git, ignorar codificações; o Git monitoriza apenas os bytes.</span><span class="sxs-lookup"><span data-stu-id="4834b-215">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span>
<span data-ttu-id="4834b-216">Outros, como o Azure DevOps ou Mercurial, podem não ter.</span><span class="sxs-lookup"><span data-stu-id="4834b-216">Others, like Azure DevOps or Mercurial, may not.</span></span> <span data-ttu-id="4834b-217">Até mesmo algumas ferramentas baseada no git contam com a descodificação de texto.</span><span class="sxs-lookup"><span data-stu-id="4834b-217">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="4834b-218">Quando for este o caso, certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="4834b-218">When this is the case, make sure you:</span></span>

- <span data-ttu-id="4834b-219">Configure o em seu controle de origem para corresponder à sua configuração de VSCode de codificação do texto.</span><span class="sxs-lookup"><span data-stu-id="4834b-219">Configure the text encoding in your source control to match your VSCode configuration.</span></span>
- <span data-ttu-id="4834b-220">Certifique-se de que todos os seus ficheiros são verificados no controle de fonte na codificação relevante.</span><span class="sxs-lookup"><span data-stu-id="4834b-220">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="4834b-221">Ter cautela alterações para a codificação recebido por meio do controle de origem.</span><span class="sxs-lookup"><span data-stu-id="4834b-221">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="4834b-222">Um sinal de chave isso é uma diferença que indica as alterações, mas onde nada parece ter alterado (porque têm de bytes, mas não o tiver feito carateres).</span><span class="sxs-lookup"><span data-stu-id="4834b-222">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="4834b-223">Ambientes dos funcionários</span><span class="sxs-lookup"><span data-stu-id="4834b-223">Collaborators' environments</span></span>

<span data-ttu-id="4834b-224">Na parte superior, configurando o controle de origem, certifique-se de que os seus colaboradores em qualquer partilha de ficheiros não têm configurações que substituem a codificação por recodificar ficheiros do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4834b-224">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="4834b-225">Outros programas</span><span class="sxs-lookup"><span data-stu-id="4834b-225">Other programs</span></span>

<span data-ttu-id="4834b-226">Qualquer outro programa que lê ou escreve um script do PowerShell novamente poderá codificá-lo.</span><span class="sxs-lookup"><span data-stu-id="4834b-226">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="4834b-227">Alguns exemplos são:</span><span class="sxs-lookup"><span data-stu-id="4834b-227">Some examples are:</span></span>

- <span data-ttu-id="4834b-228">Usando a área de transferência para copiar e colar um script.</span><span class="sxs-lookup"><span data-stu-id="4834b-228">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="4834b-229">Isso é comum em cenários como:</span><span class="sxs-lookup"><span data-stu-id="4834b-229">This is common in scenarios like:</span></span>
  - <span data-ttu-id="4834b-230">Copiar um script para uma VM</span><span class="sxs-lookup"><span data-stu-id="4834b-230">Copying a script into a VM</span></span>
  - <span data-ttu-id="4834b-231">Copiar um script fora de um e-mail ou a página Web</span><span class="sxs-lookup"><span data-stu-id="4834b-231">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="4834b-232">Copiar um script para dentro ou fora de um documento do Microsoft Word ou PowerPoint</span><span class="sxs-lookup"><span data-stu-id="4834b-232">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="4834b-233">Outros editores de texto, tais como:</span><span class="sxs-lookup"><span data-stu-id="4834b-233">Other text editors, such as:</span></span>
  - <span data-ttu-id="4834b-234">Bloco de notas</span><span class="sxs-lookup"><span data-stu-id="4834b-234">Notepad</span></span>
  - <span data-ttu-id="4834b-235">vim</span><span class="sxs-lookup"><span data-stu-id="4834b-235">vim</span></span>
  - <span data-ttu-id="4834b-236">Qualquer outro editor de script do PowerShell</span><span class="sxs-lookup"><span data-stu-id="4834b-236">Any other PowerShell script editor</span></span>
- <span data-ttu-id="4834b-237">Texto da edição de utilitários, como:</span><span class="sxs-lookup"><span data-stu-id="4834b-237">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="4834b-238">Operadores de redirecionamento do PowerShell, como `>` e `>>`</span><span class="sxs-lookup"><span data-stu-id="4834b-238">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="4834b-239">Transferência de programas, do ficheiro, como:</span><span class="sxs-lookup"><span data-stu-id="4834b-239">File transfer programs, like:</span></span>
  - <span data-ttu-id="4834b-240">Um navegador da web, durante o download de scripts</span><span class="sxs-lookup"><span data-stu-id="4834b-240">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="4834b-241">Uma partilha de ficheiros</span><span class="sxs-lookup"><span data-stu-id="4834b-241">A file share</span></span>

<span data-ttu-id="4834b-242">Algumas dessas ferramentas lidam em bytes, em vez de texto, mas outros oferecem configurações de codificação.</span><span class="sxs-lookup"><span data-stu-id="4834b-242">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="4834b-243">Nesses casos em que terá de configurar uma codificação, terá de fazer o mesmo que o seu editor de codificação para evitar problemas.</span><span class="sxs-lookup"><span data-stu-id="4834b-243">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="4834b-244">Outros recursos na codificação no PowerShell</span><span class="sxs-lookup"><span data-stu-id="4834b-244">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="4834b-245">Existem algumas outras boas postagens sobre codificação e configurar a codificação do PowerShell que vale a pena uma leitura:</span><span class="sxs-lookup"><span data-stu-id="4834b-245">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="4834b-246">[@mklement0]do [resumo de codificação do PowerShell no StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="4834b-246">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="4834b-247">Edições anteriores aberta no vscode-PowerShell para problemas de codificação:</span><span class="sxs-lookup"><span data-stu-id="4834b-247">Previous issues opened on vscode-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="4834b-248">#1308</span><span class="sxs-lookup"><span data-stu-id="4834b-248">#1308</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [<span data-ttu-id="4834b-249">#1628</span><span class="sxs-lookup"><span data-stu-id="4834b-249">#1628</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [<span data-ttu-id="4834b-250">#1680</span><span class="sxs-lookup"><span data-stu-id="4834b-250">#1680</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [<span data-ttu-id="4834b-251">#1744</span><span class="sxs-lookup"><span data-stu-id="4834b-251">#1744</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [<span data-ttu-id="4834b-252">#1751</span><span class="sxs-lookup"><span data-stu-id="4834b-252">#1751</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [<span data-ttu-id="4834b-253">O clássico *Joel on Software* escrever sobre Unicode</span><span class="sxs-lookup"><span data-stu-id="4834b-253">The classic *Joel on Software* write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="4834b-254">Codificação no .NET Standard</span><span class="sxs-lookup"><span data-stu-id="4834b-254">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin 1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[marca de ordem de byte]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Protocolo de servidor de idioma]: https://microsoft.github.io/language-server-protocol/
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[Codificação do VSCode]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VSCode's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
