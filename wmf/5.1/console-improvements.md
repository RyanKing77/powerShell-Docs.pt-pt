---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Melhorias de consola no WMF 5.1
ms.openlocfilehash: a8e82e2f973916c2ed5007eba90ee6f2b7a9a769
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085147"
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="32175-103">Melhorias de consola no WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="32175-103">Console Improvements in WMF 5.1</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="32175-104">Melhorias da consola do PowerShell</span><span class="sxs-lookup"><span data-stu-id="32175-104">PowerShell console improvements</span></span>

<span data-ttu-id="32175-105">As seguintes alterações foram feitas para powershell.exe no WMF 5.1 para melhorar a experiência de consola:</span><span class="sxs-lookup"><span data-stu-id="32175-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

### <a name="vt100-support"></a><span data-ttu-id="32175-106">Suporte de VT100</span><span class="sxs-lookup"><span data-stu-id="32175-106">VT100 support</span></span>

<span data-ttu-id="32175-107">Windows 10 foi adicionado suporte para [seqüências de escape VT100](/windows/console/console-virtual-terminal-sequences).</span><span class="sxs-lookup"><span data-stu-id="32175-107">Windows 10 added support for [VT100 escape sequences](/windows/console/console-virtual-terminal-sequences).</span></span>
<span data-ttu-id="32175-108">PowerShell irá ignorar determinadas seqüências de escape formatação VT100 ao calcular larguras de tabela.</span><span class="sxs-lookup"><span data-stu-id="32175-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="32175-109">PowerShell também adicionou uma nova API que pode ser utilizada na formatação de código para determinar se VT100 é suportada.</span><span class="sxs-lookup"><span data-stu-id="32175-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span>
<span data-ttu-id="32175-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="32175-110">For example:</span></span>

```powershell
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

<span data-ttu-id="32175-111">Aqui está uma completa [exemplo](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) que pode ser utilizado para destacar as correspondências de `Select-String`.</span><span class="sxs-lookup"><span data-stu-id="32175-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from `Select-String`.</span></span>
<span data-ttu-id="32175-112">Guarde o exemplo num arquivo chamado `MatchInfo.format.ps1xml`, em seguida, usá-lo, no seu perfil ou noutro local, execute `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="32175-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="32175-113">Tenha em atenção que seqüências de escape VT100 só são suportadas a partir da atualização de aniversário do Windows 10; não são suportadas em sistemas anteriores.</span><span class="sxs-lookup"><span data-stu-id="32175-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update; they are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="32175-114">Suporte de modo VI em PSReadline</span><span class="sxs-lookup"><span data-stu-id="32175-114">Vi mode support in PSReadline</span></span>

<span data-ttu-id="32175-115">[PSReadline](https://github.com/lzybkr/PSReadLine) adiciona suporte para o modo de vi.</span><span class="sxs-lookup"><span data-stu-id="32175-115">[PSReadline](https://github.com/lzybkr/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="32175-116">Para utilizar o modo de vi, executar `Set-PSReadlineOption -EditMode Vi`.</span><span class="sxs-lookup"><span data-stu-id="32175-116">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="32175-117">Redirecionada stdin com entrada interativa</span><span class="sxs-lookup"><span data-stu-id="32175-117">Redirected stdin with interactive input</span></span>

<span data-ttu-id="32175-118">Nas versões anteriores, a partir do PowerShell com `powershell -File -` era necessária quando foi redirecionada stdin e quer introduzir os comandos de forma interativa.</span><span class="sxs-lookup"><span data-stu-id="32175-118">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="32175-119">Com o WMF 5.1, nesse difícil descobrir a opção já não é necessária.</span><span class="sxs-lookup"><span data-stu-id="32175-119">With WMF 5.1, this hard to discover option is no longer necessary.</span></span>
<span data-ttu-id="32175-120">Pode iniciar o PowerShell sem quaisquer opções, por exemplo, `powershell`.</span><span class="sxs-lookup"><span data-stu-id="32175-120">You can start PowerShell without any options, e.g. `powershell`.</span></span>

<span data-ttu-id="32175-121">Tenha em atenção que não suportam atualmente PSReadline redirecionado stdin e a experiência de edição da linha de comandos incorporada com stdin redirecionada é extremamente limitada, por exemplo, as teclas de seta não funcionam.</span><span class="sxs-lookup"><span data-stu-id="32175-121">Note that PSReadline does not currently support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span>
<span data-ttu-id="32175-122">Uma versão futura do PSReadline deve resolver este problema.</span><span class="sxs-lookup"><span data-stu-id="32175-122">A future release of PSReadline should address this issue.</span></span>