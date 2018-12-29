---
ms.date: 08/27/2018
keywords: PowerShell, o cmdlet
title: Utilizar Nomes de Comandos Familiares
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: c5665f64fd832eb9c807f413a8e879f63db7f8c6
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405602"
---
# <a name="using-familiar-command-names"></a><span data-ttu-id="c942e-103">Utilizar nomes de comandos familiares</span><span class="sxs-lookup"><span data-stu-id="c942e-103">Using familiar command names</span></span>

<span data-ttu-id="c942e-104">PowerShell suporta aliases para fazer referência aos comandos por nomes alternativos.</span><span class="sxs-lookup"><span data-stu-id="c942e-104">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="c942e-105">Aliasing permite aos utilizadores com experiência de outros shells a utilizar nomes de comando comuns que já conhecem para operações semelhantes no PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c942e-105">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="c942e-106">Aliasing associa um novo nome de outro comando.</span><span class="sxs-lookup"><span data-stu-id="c942e-106">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="c942e-107">Por exemplo, o PowerShell tem uma função interna chamada `Clear-Host` que limpa a janela de saída.</span><span class="sxs-lookup"><span data-stu-id="c942e-107">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="c942e-108">Pode digitar um a `cls` ou `clear` alias num prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="c942e-108">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="c942e-109">PowerShell interpreta estes aliases e executa o `Clear-Host` função.</span><span class="sxs-lookup"><span data-stu-id="c942e-109">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="c942e-110">Esta funcionalidade ajuda os utilizadores para aprender o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c942e-110">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="c942e-111">Primeira, a maioria **cmd.exe** e usuários do Unix têm um grande repertório de comandos que já conhece os utilizadores por nome.</span><span class="sxs-lookup"><span data-stu-id="c942e-111">First, most **cmd.exe** and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="c942e-112">Os equivalentes de PowerShell talvez não produzam resultados idênticos.</span><span class="sxs-lookup"><span data-stu-id="c942e-112">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="c942e-113">No entanto, os resultados são fechar suficiente que os utilizadores podem fazer o trabalho sem saber o nome do comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c942e-113">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="c942e-114">"Dedo memória" é outra das principais fontes de frustração quando um novo shell de comando de aprendizado.</span><span class="sxs-lookup"><span data-stu-id="c942e-114">"Finger memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="c942e-115">Se tiver utilizado **cmd.exe** durante anos, forma reflexiva pode digitar o `cls` comando para limpar o ecrã.</span><span class="sxs-lookup"><span data-stu-id="c942e-115">If you have used **cmd.exe** for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="c942e-116">Sem o alias para `Clear-Host`, recebe uma mensagem de erro e não saberá o que fazer para limpar a saída.</span><span class="sxs-lookup"><span data-stu-id="c942e-116">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

<span data-ttu-id="c942e-117">A lista seguinte mostra algumas do comum **cmd.exe** e comandos de Unix, que podem ser usados no PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c942e-117">The following list shows a few of the common **cmd.exe** and Unix commands that you can use in PowerShell:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="c942e-118">cat</span><span class="sxs-lookup"><span data-stu-id="c942e-118">cat</span></span>|<span data-ttu-id="c942e-119">dir</span><span class="sxs-lookup"><span data-stu-id="c942e-119">dir</span></span>|<span data-ttu-id="c942e-120">montagem</span><span class="sxs-lookup"><span data-stu-id="c942e-120">mount</span></span>|<span data-ttu-id="c942e-121">RM</span><span class="sxs-lookup"><span data-stu-id="c942e-121">rm</span></span>|
|<span data-ttu-id="c942e-122">CD</span><span class="sxs-lookup"><span data-stu-id="c942e-122">cd</span></span>|<span data-ttu-id="c942e-123">eco</span><span class="sxs-lookup"><span data-stu-id="c942e-123">echo</span></span>|<span data-ttu-id="c942e-124">mover</span><span class="sxs-lookup"><span data-stu-id="c942e-124">move</span></span>|<span data-ttu-id="c942e-125">rmdir</span><span class="sxs-lookup"><span data-stu-id="c942e-125">rmdir</span></span>|
|<span data-ttu-id="c942e-126">chdir</span><span class="sxs-lookup"><span data-stu-id="c942e-126">chdir</span></span>|<span data-ttu-id="c942e-127">Apagar</span><span class="sxs-lookup"><span data-stu-id="c942e-127">erase</span></span>|<span data-ttu-id="c942e-128">popd</span><span class="sxs-lookup"><span data-stu-id="c942e-128">popd</span></span>|<span data-ttu-id="c942e-129">modo de suspensão</span><span class="sxs-lookup"><span data-stu-id="c942e-129">sleep</span></span>|
|<span data-ttu-id="c942e-130">Limpar</span><span class="sxs-lookup"><span data-stu-id="c942e-130">clear</span></span>|<span data-ttu-id="c942e-131">H</span><span class="sxs-lookup"><span data-stu-id="c942e-131">h</span></span>|<span data-ttu-id="c942e-132">PS</span><span class="sxs-lookup"><span data-stu-id="c942e-132">ps</span></span>|<span data-ttu-id="c942e-133">Ordenação</span><span class="sxs-lookup"><span data-stu-id="c942e-133">sort</span></span>|
|<span data-ttu-id="c942e-134">CLS</span><span class="sxs-lookup"><span data-stu-id="c942e-134">cls</span></span>|<span data-ttu-id="c942e-135">histórico</span><span class="sxs-lookup"><span data-stu-id="c942e-135">history</span></span>|<span data-ttu-id="c942e-136">pushd</span><span class="sxs-lookup"><span data-stu-id="c942e-136">pushd</span></span>|<span data-ttu-id="c942e-137">Tee</span><span class="sxs-lookup"><span data-stu-id="c942e-137">tee</span></span>|
|<span data-ttu-id="c942e-138">Cópia</span><span class="sxs-lookup"><span data-stu-id="c942e-138">copy</span></span>|<span data-ttu-id="c942e-139">kill</span><span class="sxs-lookup"><span data-stu-id="c942e-139">kill</span></span>|<span data-ttu-id="c942e-140">pwd</span><span class="sxs-lookup"><span data-stu-id="c942e-140">pwd</span></span>|<span data-ttu-id="c942e-141">tipo</span><span class="sxs-lookup"><span data-stu-id="c942e-141">type</span></span>|
|<span data-ttu-id="c942e-142">del</span><span class="sxs-lookup"><span data-stu-id="c942e-142">del</span></span>|<span data-ttu-id="c942e-143">LP</span><span class="sxs-lookup"><span data-stu-id="c942e-143">lp</span></span>|<span data-ttu-id="c942e-144">r</span><span class="sxs-lookup"><span data-stu-id="c942e-144">r</span></span>|<span data-ttu-id="c942e-145">escrita</span><span class="sxs-lookup"><span data-stu-id="c942e-145">write</span></span>|
|<span data-ttu-id="c942e-146">diff</span><span class="sxs-lookup"><span data-stu-id="c942e-146">diff</span></span>|<span data-ttu-id="c942e-147">Ls</span><span class="sxs-lookup"><span data-stu-id="c942e-147">ls</span></span>|<span data-ttu-id="c942e-148">ren</span><span class="sxs-lookup"><span data-stu-id="c942e-148">ren</span></span>||

<span data-ttu-id="c942e-149">O `Get-Alias` cmdlet mostra-lhe o nome real do comando do PowerShell nativo, associado com um alias.</span><span class="sxs-lookup"><span data-stu-id="c942e-149">The `Get-Alias` cmdlet shows you the real name of the native PowerShell command associated with an alias.</span></span>

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a><span data-ttu-id="c942e-150">Interpretar os aliases padrão</span><span class="sxs-lookup"><span data-stu-id="c942e-150">Interpreting standard aliases</span></span>

<span data-ttu-id="c942e-151">Os aliases que descrevemos anteriores foram projetados para nome de compatibilidade com outros shells de comando.</span><span class="sxs-lookup"><span data-stu-id="c942e-151">The aliases we described previous were designed for name-compatibility with other command shells.</span></span>
<span data-ttu-id="c942e-152">A maioria dos aliases incorporados no PowerShell foram concebidos para fins de brevidade.</span><span class="sxs-lookup"><span data-stu-id="c942e-152">Most aliases built into PowerShell are designed for brevity.</span></span> <span data-ttu-id="c942e-153">Nomes mais curtos são mais fáceis de tipo, mas são difíceis de ler se não sabe o que dizem respeito a.</span><span class="sxs-lookup"><span data-stu-id="c942e-153">Shorter names are easier to type, but are difficult to read if you don't know what they refer to.</span></span>

<span data-ttu-id="c942e-154">Aliases de PowerShell tentam comprometer entre clareza e questões de brevidade.</span><span class="sxs-lookup"><span data-stu-id="c942e-154">PowerShell aliases try to compromise between clarity and brevity.</span></span> <span data-ttu-id="c942e-155">PowerShell utiliza um conjunto padrão de aliases para comum substantivos e verbos.</span><span class="sxs-lookup"><span data-stu-id="c942e-155">PowerShell uses a standard set of aliases for common nouns and verbs.</span></span>

<span data-ttu-id="c942e-156">Abreviações de exemplo:</span><span class="sxs-lookup"><span data-stu-id="c942e-156">Example abbreviations:</span></span>

| <span data-ttu-id="c942e-157">Substantivo ou verbo</span><span class="sxs-lookup"><span data-stu-id="c942e-157">Noun or Verb</span></span> | <span data-ttu-id="c942e-158">Abreviatura</span><span class="sxs-lookup"><span data-stu-id="c942e-158">Abbreviation</span></span> |
|--------------|--------------|
| <span data-ttu-id="c942e-159">Obter</span><span class="sxs-lookup"><span data-stu-id="c942e-159">Get</span></span>          | <span data-ttu-id="c942e-160">G</span><span class="sxs-lookup"><span data-stu-id="c942e-160">g</span></span>            |
| <span data-ttu-id="c942e-161">Definir</span><span class="sxs-lookup"><span data-stu-id="c942e-161">Set</span></span>          | <span data-ttu-id="c942e-162">s</span><span class="sxs-lookup"><span data-stu-id="c942e-162">s</span></span>            |
| <span data-ttu-id="c942e-163">Item</span><span class="sxs-lookup"><span data-stu-id="c942e-163">Item</span></span>         | <span data-ttu-id="c942e-164">posso</span><span class="sxs-lookup"><span data-stu-id="c942e-164">i</span></span>            |
| <span data-ttu-id="c942e-165">Localização</span><span class="sxs-lookup"><span data-stu-id="c942e-165">Location</span></span>     | <span data-ttu-id="c942e-166">L</span><span class="sxs-lookup"><span data-stu-id="c942e-166">l</span></span>            |
| <span data-ttu-id="c942e-167">Comando</span><span class="sxs-lookup"><span data-stu-id="c942e-167">Command</span></span>      | <span data-ttu-id="c942e-168">cm</span><span class="sxs-lookup"><span data-stu-id="c942e-168">cm</span></span>           |
| <span data-ttu-id="c942e-169">Alias</span><span class="sxs-lookup"><span data-stu-id="c942e-169">Alias</span></span>        | <span data-ttu-id="c942e-170">Al</span><span class="sxs-lookup"><span data-stu-id="c942e-170">al</span></span>           |

<span data-ttu-id="c942e-171">Estes aliases são compreensíveis quando sabe os nomes abreviados.</span><span class="sxs-lookup"><span data-stu-id="c942e-171">These aliases are understandable when you know the shorthand names.</span></span>

| <span data-ttu-id="c942e-172">Nome do cmdlet</span><span class="sxs-lookup"><span data-stu-id="c942e-172">Cmdlet name</span></span>    | <span data-ttu-id="c942e-173">Alias</span><span class="sxs-lookup"><span data-stu-id="c942e-173">Alias</span></span> |
|----------------|-------|
| `Get-Item `    | <span data-ttu-id="c942e-174">GI</span><span class="sxs-lookup"><span data-stu-id="c942e-174">gi</span></span>    |
| `Set-Item`     | <span data-ttu-id="c942e-175">si</span><span class="sxs-lookup"><span data-stu-id="c942e-175">si</span></span>    |
| `Get-Location` | <span data-ttu-id="c942e-176">GL</span><span class="sxs-lookup"><span data-stu-id="c942e-176">gl</span></span>    |
| `Set-Location` | <span data-ttu-id="c942e-177">SL</span><span class="sxs-lookup"><span data-stu-id="c942e-177">sl</span></span>    |
| `Get-Command`  | <span data-ttu-id="c942e-178">GCM</span><span class="sxs-lookup"><span data-stu-id="c942e-178">gcm</span></span>   |
| `Get-Alias`    | <span data-ttu-id="c942e-179">GAL</span><span class="sxs-lookup"><span data-stu-id="c942e-179">gal</span></span>   |

<span data-ttu-id="c942e-180">Quando estiver familiarizado com o aliasing de PowerShell, é fácil supor que o **sal** alias refere-se ao `Set-Alias`.</span><span class="sxs-lookup"><span data-stu-id="c942e-180">Once you're familiar with PowerShell aliasing, it's easy to guess that the **sal** alias refers to `Set-Alias`.</span></span>

## <a name="creating-new-aliases"></a><span data-ttu-id="c942e-181">Criação de novos aliases</span><span class="sxs-lookup"><span data-stu-id="c942e-181">Creating new aliases</span></span>

<span data-ttu-id="c942e-182">Pode criar seu próprio aliases usando o `Set-Alias` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c942e-182">You can create your own aliases using the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="c942e-183">Por exemplo, as seguintes declarações de criar os aliases de padrão de cmdlet discutidos anteriormente:</span><span class="sxs-lookup"><span data-stu-id="c942e-183">For example, the following statements create the standard cmdlet aliases previously discussed:</span></span>

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

<span data-ttu-id="c942e-184">Internamente, o PowerShell utiliza comandos semelhantes durante o arranque, mas estes aliases não são alteráveis.</span><span class="sxs-lookup"><span data-stu-id="c942e-184">Internally, PowerShell uses similar commands during startup, but these aliases are not changeable.</span></span>
<span data-ttu-id="c942e-185">Se tentar executar um desses comandos, obterá um erro explicando o que o alias não pode ser modificado.</span><span class="sxs-lookup"><span data-stu-id="c942e-185">If you try to execute one of these commands, you get an error explaining that the alias can't be modified.</span></span> <span data-ttu-id="c942e-186">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c942e-186">For example:</span></span>

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```