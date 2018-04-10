---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Melhorias na consola no WMF 5.1
ms.openlocfilehash: 2abc02010c6c1d9f7fc617e9831b2d1243e0a3ee
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="598bd-103">Melhorias na consola no WMF 5.1#</span><span class="sxs-lookup"><span data-stu-id="598bd-103">Console Improvements in WMF 5.1#</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="598bd-104">Melhorias na consola do PowerShell</span><span class="sxs-lookup"><span data-stu-id="598bd-104">PowerShell console improvements</span></span>

<span data-ttu-id="598bd-105">As seguintes alterações foram efetuadas para o powershell.exe no WMF 5.1 para melhorar a experiência de consola:</span><span class="sxs-lookup"><span data-stu-id="598bd-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

###<a name="vt100-support"></a><span data-ttu-id="598bd-106">Suporte de VT100</span><span class="sxs-lookup"><span data-stu-id="598bd-106">VT100 support</span></span>

<span data-ttu-id="598bd-107">Windows 10 suporte adicionado para [sequências de escape VT100](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="598bd-107">Windows 10 added support for [VT100 escape sequences](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).</span></span>
<span data-ttu-id="598bd-108">PowerShell ignorará sequências de escape formatação determinadas VT100 quando se calcular larguras de tabela.</span><span class="sxs-lookup"><span data-stu-id="598bd-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="598bd-109">PowerShell também adicionada uma nova API que pode ser utilizada na formatação código para determinar se VT100 é suportada.</span><span class="sxs-lookup"><span data-stu-id="598bd-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span>
<span data-ttu-id="598bd-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="598bd-110">For example:</span></span>

```
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```
<span data-ttu-id="598bd-111">Eis um concluída [exemplo](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) que podem ser utilizados para realçar correspondências de cadeia de selecione.</span><span class="sxs-lookup"><span data-stu-id="598bd-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from Select-String.</span></span>
<span data-ttu-id="598bd-112">Guardar o exemplo num ficheiro denominado `MatchInfo.format.ps1xml`, em seguida, utilizá-lo, o perfil ou noutro local, execute `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="598bd-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="598bd-113">Tenha em atenção que as sequências de escape VT100 só são suportadas a partir da atualização do Windows 10 Anniversary; não são suportadas em sistemas anteriores.</span><span class="sxs-lookup"><span data-stu-id="598bd-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update; they are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="598bd-114">Suporte do modo de VI no PSReadline</span><span class="sxs-lookup"><span data-stu-id="598bd-114">Vi mode support in PSReadline</span></span>

<span data-ttu-id="598bd-115">[PSReadline](https://github.com/lzybkr/PSReadLine) adiciona suporte para o modo de vi.</span><span class="sxs-lookup"><span data-stu-id="598bd-115">[PSReadline](https://github.com/lzybkr/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="598bd-116">Para utilizar o modo de vi, execute `Set-PSReadlineOption -EditMode Vi`.</span><span class="sxs-lookup"><span data-stu-id="598bd-116">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="598bd-117">Stdin redirecionada com entrada interativa</span><span class="sxs-lookup"><span data-stu-id="598bd-117">Redirected stdin with interactive input</span></span>

<span data-ttu-id="598bd-118">Nas versões anteriores, a partir do PowerShell com `powershell -File -` era necessário quando foi redirecionada stdin e quer introduza comandos interativamente.</span><span class="sxs-lookup"><span data-stu-id="598bd-118">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="598bd-119">Com 5.1 WMF neste disco rígido detetar a opção já não é necessária.</span><span class="sxs-lookup"><span data-stu-id="598bd-119">With WMF 5.1, this hard to discover option is no longer necessary.</span></span>
<span data-ttu-id="598bd-120">Pode iniciar PowerShell sem quaisquer opções, por exemplo, `powershell`.</span><span class="sxs-lookup"><span data-stu-id="598bd-120">You can start PowerShell without any options, e.g. `powershell`.</span></span>

<span data-ttu-id="598bd-121">Tenha em atenção que PSReadline não suporta atualmente redirecionado stdin e a experiência de edição da linha de comandos incorporada com stdin redirecionado é extremamente limitada, por exemplo, as teclas de seta não funcionam.</span><span class="sxs-lookup"><span data-stu-id="598bd-121">Note that PSReadline does not currently support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span>
<span data-ttu-id="598bd-122">Uma versão futura do PSReadline deve resolver este problema.</span><span class="sxs-lookup"><span data-stu-id="598bd-122">A future release of PSReadline should address this issue.</span></span>