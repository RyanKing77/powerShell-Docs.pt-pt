---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Melhorias de consola no WMF 5.1
ms.openlocfilehash: a8e82e2f973916c2ed5007eba90ee6f2b7a9a769
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892931"
---
# <a name="console-improvements-in-wmf-51"></a>Melhorias de consola no WMF 5.1

## <a name="powershell-console-improvements"></a>Melhorias da consola do PowerShell

As seguintes alterações foram feitas para powershell.exe no WMF 5.1 para melhorar a experiência de consola:

### <a name="vt100-support"></a>Suporte de VT100

Windows 10 foi adicionado suporte para [seqüências de escape VT100](/windows/console/console-virtual-terminal-sequences).
PowerShell irá ignorar determinadas seqüências de escape formatação VT100 ao calcular larguras de tabela.

PowerShell também adicionou uma nova API que pode ser utilizada na formatação de código para determinar se VT100 é suportada.
Por exemplo:

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

Aqui está uma completa [exemplo](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) que pode ser utilizado para destacar as correspondências de `Select-String`.
Guarde o exemplo num arquivo chamado `MatchInfo.format.ps1xml`, em seguida, usá-lo, no seu perfil ou noutro local, execute `Update-FormatData -Prepend MatchInfo.format.ps1xml`.

Tenha em atenção que seqüências de escape VT100 só são suportadas a partir da atualização de aniversário do Windows 10; não são suportadas em sistemas anteriores.

### <a name="vi-mode-support-in-psreadline"></a>Suporte de modo VI em PSReadline

[PSReadline](https://github.com/lzybkr/PSReadLine) adiciona suporte para o modo de vi. Para utilizar o modo de vi, executar `Set-PSReadlineOption -EditMode Vi`.

### <a name="redirected-stdin-with-interactive-input"></a>Redirecionada stdin com entrada interativa

Nas versões anteriores, a partir do PowerShell com `powershell -File -` era necessária quando foi redirecionada stdin e quer introduzir os comandos de forma interativa.

Com o WMF 5.1, nesse difícil descobrir a opção já não é necessária.
Pode iniciar o PowerShell sem quaisquer opções, por exemplo, `powershell`.

Tenha em atenção que não suportam atualmente PSReadline redirecionado stdin e a experiência de edição da linha de comandos incorporada com stdin redirecionada é extremamente limitada, por exemplo, as teclas de seta não funcionam.
Uma versão futura do PSReadline deve resolver este problema.