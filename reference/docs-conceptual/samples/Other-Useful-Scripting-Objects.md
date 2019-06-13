---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Outros Objetos de Scripting Úteis
ms.openlocfilehash: 8d1d10b518d1aadd6aec831b512802558f8fc075
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030041"
---
# <a name="other-useful-scripting-objects"></a>Outros Objetos de Scripting Úteis

Os objetos seguintes fornecem funcionalidades adicionais de scripts no ISE do Windows PowerShell. Não são parte dos **$psISE** hierarquia.

## <a name="useful-scripting-objects"></a>Objetos de Scripting úteis

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications

Existem algumas limitações em como o Windows PowerShell ISE interage com aplicativos de console. Um comando ou um script de automatização que requer intervenção do usuário poderá não funcionar da forma funciona a partir da consola do Windows PowerShell. Pode querer bloquear estes comandos ou scripts a partir de em execução no painel de comando do Windows PowerShell ISE. O **$psUnsupportedConsoleApplications** objeto mantém uma lista desses comandos. Se tentar executar os comandos nesta lista, receberá uma mensagem que não são suportados. O script a seguir adiciona uma entrada à lista.

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a>$psLocalHelp

Este é um objeto de dicionário que mantém um mapeamento sensível ao contexto entre tópicos de ajuda e seus links associado no ficheiro de ajuda HTML compilado local. É utilizado para localizar a ajuda local para um tópico específico. Pode adicionar ou eliminar tópicos desta lista. O exemplo de código seguinte mostra alguns exemplos pares chave-valor que estão contidas na `$psLocalHelp`.

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

O script a seguir adiciona uma entrada à lista.

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp

Este é um objeto de dicionário que mantém um mapeamento sensível ao contexto entre os títulos de tópico de tópicos de ajuda e suas URLs externos associados. É utilizado para localizar a ajuda para um determinado tópico na web. Pode adicionar ou eliminar tópicos desta lista.

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : http://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : http://go.microsoft.com/fwlink/p/?LinkID=113278
```

O script a seguir adiciona uma entrada à lista.

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Veja Também

[Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
