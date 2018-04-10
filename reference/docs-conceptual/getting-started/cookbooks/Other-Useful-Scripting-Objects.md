---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Outros Objetos de Scripting Úteis
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 0e87e9919199e011ab5abec5b07dccc8494ad64a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="other-useful-scripting-objects"></a>Outros Objetos de Scripting Úteis

Os seguintes objetos fornecem funcionalidades adicionais de script no ISE do Windows PowerShell. Não são parte do **$psISE** hierarquia.

## <a name="useful-scripting-objects"></a>Objetos de script útil

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications

Existem algumas limitações na forma como o ISE do Windows PowerShell interage com aplicações de consola. Um comando ou um script de automatização requer intervenção do utilizador poderá não funcionar da forma que funciona a partir da consola do Windows PowerShell. Pode querer bloquear estes comandos ou scripts sejam executadas no painel de comando do Windows PowerShell ISE. O **$psUnsupportedConsoleApplications** objeto mantém uma lista desses comandos. Se tentar executar os comandos nesta lista, receberá uma mensagem que não são suportados. O seguinte script adiciona uma entrada à lista.

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a>$psLocalHelp

Este é um objeto de dicionário que mantém um mapeamento sensíveis ao contexto de entre tópicos de ajuda e as respetivas ligações associadas no ficheiro de ajuda de HTML compilado local. É utilizado para localizar a local a ajuda para um tópico específico. Pode adicionar ou eliminar tópicos desta lista. Exemplo de código seguinte mostra alguns exemplos de pares chave-valor que estão contidas num **$psLocalHelp**.

```powershell
# See the local help map
$psLocalHelp | Format-List
```

### <a name="sample-output"></a>Saída de Exemplo

|||
|-|-|
|Chave: Adicionar-computador|Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm|
|Chave: Adicionar conteúdo|Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm|

O seguinte script adiciona uma entrada à lista.

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp

Este é um objeto de dicionário que mantém um mapeamento sensíveis ao contexto entre os títulos de tópico de tópicos de ajuda e os URLs externos associados. É utilizado para localizar a ajuda para um tópico específico na web. Pode adicionar ou eliminar tópicos desta lista.

```powershell
$psOnlineHelp | Format-List
```

### <a name="sample-output"></a>Saída de Exemplo

|||
|-|-|
|Chave: Adicionar-computador|Value : http://go.microsoft.com/fwlink/p/?LinkID=135194|
|Chave: Adicionar conteúdo|Value : http://go.microsoft.com/fwlink/p/?LinkID=113278|

 O seguinte script adiciona uma entrada à lista.

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Consulte Também

- [Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)