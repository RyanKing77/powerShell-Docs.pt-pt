---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Utilizar a Expansão por Tabulação
ms.openlocfilehash: d96cbf848f464aff29a7bed9b70d0b6a000aa808
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031021"
---
# <a name="using-tab-expansion"></a>Utilizar a Expansão por Tabulação

Shells de linha de comandos, muitas vezes, proporcionam uma forma para concluir os nomes de ficheiros de longos ou comandos automaticamente, acelerar a entrada de comando e o fornecimento de sugestões. PowerShell permite-lhe o preenchimento nos nomes de ficheiros e nomes de cmdlet ao premir o <kbd>separador</kbd> chave.

> [!NOTE]
> Expansão da tabulação é controlado pela função interna TabExpansion ou TabExpansion2. Uma vez que esta função pode ser modificada ou substituída, essa discussão é um guia para o comportamento da configuração predefinida do PowerShell.

Para preencher automaticamente um nome de ficheiro ou caminho as opções disponíveis, escreva parte do nome e prima a <kbd>separador</kbd> chave. PowerShell expandirá automaticamente o nome para a primeira correspondência que encontra. Premir a <kbd>separador</kbd> chave repetidamente passará por todas as opções disponíveis.

A expansão da tabulação de nomes de cmdlet é ligeiramente diferente. Para utilizar a expansão da tabulação no nome de um cmdlet, escreva a primeira parte inteira do nome (o verbo) e o hífen que o sucede. Pode preencher mais o nome de uma correspondência parcial. Por exemplo, se digitar `get-co` e, em seguida, prima a <kbd>separador</kbd> chave, PowerShell irá automaticamente expandir esta opção para o `Get-Command` cmdlet (Observe que ele também altera o caso de letras para o formato padrão). Se pressionar <kbd>separador</kbd> chave novamente, PowerShell substitui isso com o apenas outro cmdlet nome correspondente, `Get-Content`.

Pode usar repetidamente expansão da tabulação na mesma linha. Por exemplo, pode utilizar a expansão da tabulação no nome do `Get-Content` cmdlet ao introduzir:

```
PS> Get-Con<Tab>
```

Quando pressiona o <kbd>separador</kbd> chave, o comando se expande para:

```
PS> Get-Content
```

Pode, em seguida, parcialmente especifique o caminho para o ficheiro de registo de configuração do Active Directory e utilizar a expansão da tabulação novamente:

```
PS> Get-Content c:\windows\acts<Tab>
```

Quando pressiona o <kbd>separador</kbd> chave, o comando se expande para:

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> Uma limitação do processo de expansão do separador é que os separadores sempre são interpretados como tentativas para concluir uma palavra. Se copiar e colar exemplos de comandos para a consola do PowerShell, certifique-se de que o exemplo não contém separadores; Se existir, os resultados imprevisíveis e certamente não será o que pretendia.
