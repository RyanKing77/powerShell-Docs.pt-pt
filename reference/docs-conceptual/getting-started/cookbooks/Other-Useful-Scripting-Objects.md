---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "Outros objetos de Scripting útil"
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 8334d0b346e59dea3643a93bf52b780b361d1945
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="other-useful-scripting-objects"></a>Outros objetos de Scripting útil
  Os seguintes objetos fornecem funcionalidades adicionais de script no ISE do Windows PowerShell. Não são parte do **$psISE** hierarquia.

## <a name="useful-scripting-objects"></a>Objetos de script útil

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications
 Existem algumas limitações na forma como o ISE do Windows PowerShell interage com aplicações de consola. Um comando ou um script de automatização requer intervenção do utilizador poderá não funcionar da forma que funciona a partir da consola do Windows PowerShell. Pode querer bloquear estes comandos ou scripts sejam executadas no painel de comando do Windows PowerShell ISE. O **$psUnsupportedConsoleApplications** objeto mantém uma lista desses comandos. Se tentar executar os comandos nesta lista, receberá uma mensagem que não são suportados. O seguinte script adiciona uma entrada à lista.

```
# List the unsupported commands
psUnsupportedConsoleApplications
# Add a command to this list
psUnsupportedConsoleApplications.Add(“Mycommand”)
#Show the augmented list of commands
psUnsupportedConsoleApplications

```

### <a name="pslocalhelp"></a>$psLocalHelp
 Este é um objeto de dicionário que mantém um mapeamento sensíveis ao contexto de entre tópicos de ajuda e as respetivas ligações associadas no ficheiro de ajuda de HTML compilado local. É utilizado para localizar a local a ajuda para um tópico específico. Pode adicionar ou eliminar tópicos desta lista. Exemplo de código seguinte mostra alguns exemplos de pares chave-valor que estão contidas num **$psLocalHelp**.

```
# See the local help map
$psLocalHelp | Format-List

```

### <a name="sample-output"></a>Saída de Exemplo

|||
|-|-|
|Chave: Adicionar-computador|Valor: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm|
|Chave: Adicionar conteúdo|Valor: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm|

 O seguinte script adiciona uma entrada à lista.

```
$psLocalHelp.Add("get-myNoun","c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp
 Este é um objeto de dicionário que mantém um mapeamento sensíveis ao contexto entre os títulos de tópico de tópicos de ajuda e os URLs externos associados. É utilizado para localizar a ajuda para um tópico específico na web. Pode adicionar ou eliminar tópicos desta lista.

```
$psOnlineHelp | Format-List

```

### <a name="sample-output"></a>Saída de Exemplo

|||
|-|-|
|Chave: Adicionar-computador|Valor: http://go.microsoft.com/fwlink/p/?LinkID=135194|
|Chave: Adicionar conteúdo|Valor: http://go.microsoft.com/fwlink/p/?LinkID=113278|

 O seguinte script adiciona uma entrada à lista.

```
$psOnlineHelp.Add("get-myNoun","http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Consulte Também
- [O ISE do Windows PowerShell modelo de objeto de Scripting](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
