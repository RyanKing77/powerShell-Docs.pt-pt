---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
title: Melhorias na consola no WMF 5.1
ms.openlocfilehash: b0859191ea310c9b73fe9f255d7f256a1cc1af1f
ms.sourcegitcommit: fee03bb9802222078c8d5f6c8efb0698024406ed
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/27/2017
---
# <a name="console-improvements-in-wmf-51"></a>Melhorias na consola no WMF 5.1#

## <a name="powershell-console-improvements"></a>Melhorias na consola do PowerShell

As seguintes alterações foram efetuadas para o powershell.exe no WMF 5.1 para melhorar a experiência de consola:

###<a name="vt100-support"></a>Suporte de VT100

Windows 10 suporte adicionado para [sequências de escape VT100](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).
PowerShell ignorará sequências de escape formatação determinadas VT100 quando se calcular larguras de tabela.

PowerShell também adicionada uma nova API que pode ser utilizada na formatação código para determinar se VT100 é suportada. Por exemplo:

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
Eis um concluída [exemplo](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) que podem ser utilizados para realçar correspondências de cadeia de selecione.
Guardar o exemplo num ficheiro denominado `MatchInfo.format.ps1xml`, em seguida, utilizá-lo, o perfil ou noutro local, execute `Update-FormatData -Prepend MatchInfo.format.ps1xml`.

Tenha em atenção que as sequências de escape VT100 só são suportadas a partir da atualização do Windows 10 Anniversary; não são suportadas em sistemas anteriores.   

### <a name="vi-mode-support-in-psreadline"></a>Suporte do modo de VI no PSReadline

[PSReadline](https://github.com/lzybkr/PSReadLine) adiciona suporte para o modo de vi. Para utilizar o modo de vi, execute `Set-PSReadlineOption -EditMode Vi`.

### <a name="redirected-stdin-with-interactive-input"></a>Stdin redirecionada com entrada interativa 

Nas versões anteriores, a partir do PowerShell com `powershell -File -` era necessário quando foi redirecionada stdin e quer introduza comandos interativamente.

Com 5.1 WMF neste disco rígido detetar a opção já não é necessária. Pode iniciar PowerShell sem quaisquer opções, por exemplo, `powershell`.

Tenha em atenção que PSReadline não suporta atualmente redirecionado stdin e a experiência de edição da linha de comandos incorporada com stdin redirecionado é extremamente limitada, por exemplo, as teclas de seta não funcionam. Uma versão futura do PSReadline deve resolver este problema.   

