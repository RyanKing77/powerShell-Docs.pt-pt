---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Melhorias de consola no WMF 5.1
ms.openlocfilehash: d0dd8e3c31dc0ddebab1bb899468b77a9292954d
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856218"
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="5c058-103">Melhorias de consola no WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="5c058-103">Console Improvements in WMF 5.1</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="5c058-104">Melhorias da consola do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5c058-104">PowerShell console improvements</span></span>

<span data-ttu-id="5c058-105">As seguintes alterações foram feitas para powershell.exe no WMF 5.1 para melhorar a experiência de consola:</span><span class="sxs-lookup"><span data-stu-id="5c058-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

### <a name="vt100-support"></a><span data-ttu-id="5c058-106">Suporte de VT100</span><span class="sxs-lookup"><span data-stu-id="5c058-106">VT100 support</span></span>

<span data-ttu-id="5c058-107">Windows 10 foi adicionado suporte para [seqüências de escape VT100](/windows/console/console-virtual-terminal-sequences).</span><span class="sxs-lookup"><span data-stu-id="5c058-107">Windows 10 added support for [VT100 escape sequences](/windows/console/console-virtual-terminal-sequences).</span></span>
<span data-ttu-id="5c058-108">PowerShell irá ignorar determinadas seqüências de escape formatação VT100 ao calcular larguras de tabela.</span><span class="sxs-lookup"><span data-stu-id="5c058-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="5c058-109">PowerShell também adicionou uma nova API que pode ser utilizada na formatação de código para determinar se VT100 é suportada.</span><span class="sxs-lookup"><span data-stu-id="5c058-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span> <span data-ttu-id="5c058-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5c058-110">For example:</span></span>

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

<span data-ttu-id="5c058-111">Aqui está uma completa [exemplo](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) que pode ser utilizado para destacar as correspondências de `Select-String`.</span><span class="sxs-lookup"><span data-stu-id="5c058-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from `Select-String`.</span></span> <span data-ttu-id="5c058-112">Guarde o exemplo num arquivo chamado `MatchInfo.format.ps1xml`, em seguida, usá-lo, no seu perfil ou noutro local, execute `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="5c058-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="5c058-113">Tenha em atenção que seqüências de escape VT100 só são suportadas a partir da atualização de aniversário do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="5c058-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update.</span></span>
<span data-ttu-id="5c058-114">Não são suportadas em sistemas anteriores.</span><span class="sxs-lookup"><span data-stu-id="5c058-114">They are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="5c058-115">Suporte de modo VI em PSReadline</span><span class="sxs-lookup"><span data-stu-id="5c058-115">Vi mode support in PSReadline</span></span>

<span data-ttu-id="5c058-116">[PSReadline](https://github.com/PowerShell/PSReadLine) adiciona suporte para o modo de vi.</span><span class="sxs-lookup"><span data-stu-id="5c058-116">[PSReadline](https://github.com/PowerShell/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="5c058-117">Para utilizar o modo de vi, executar `Set-PSReadlineOption -EditMode Vi`.</span><span class="sxs-lookup"><span data-stu-id="5c058-117">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="5c058-118">Redirecionada stdin com entrada interativa</span><span class="sxs-lookup"><span data-stu-id="5c058-118">Redirected stdin with interactive input</span></span>

<span data-ttu-id="5c058-119">Nas versões anteriores, a partir do PowerShell com `powershell -File -` era necessária quando foi redirecionada stdin e quer introduzir os comandos de forma interativa.</span><span class="sxs-lookup"><span data-stu-id="5c058-119">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="5c058-120">Com o WMF 5.1, nesse difícil descobrir a opção já não é necessária.</span><span class="sxs-lookup"><span data-stu-id="5c058-120">With WMF 5.1, this hard to discover option is no longer necessary.</span></span> <span data-ttu-id="5c058-121">Pode iniciar o PowerShell sem quaisquer opções.</span><span class="sxs-lookup"><span data-stu-id="5c058-121">You can start PowerShell without any options.</span></span>

<span data-ttu-id="5c058-122">Tenha em atenção que não suporta a PSReadline redirecionado stdin e a experiência de edição da linha de comandos incorporada com stdin redirecionada é extremamente limitada, por exemplo, as teclas de seta não funcionam.</span><span class="sxs-lookup"><span data-stu-id="5c058-122">Note that PSReadline does not support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span> <span data-ttu-id="5c058-123">Uma versão futura do PSReadline deve resolver este problema.</span><span class="sxs-lookup"><span data-stu-id="5c058-123">A future release of PSReadline should address this issue.</span></span>