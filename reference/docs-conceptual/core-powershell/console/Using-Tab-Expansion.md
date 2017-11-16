---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "Utilizando o separador de expansão"
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: 8412bd97a95719f07b16c6671d3b8801bbfab8e3
ms.sourcegitcommit: 4807ab554d55fdee499980835bcc279368b1df68
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/07/2017
---
# <a name="using-tab-expansion"></a>Utilizando o separador de expansão
Shells da linha de comandos, muitas vezes, fornecem uma forma para concluir automaticamente, os nomes dos ficheiros de longos ou comandos acelerar a entrada de comando e fornecer. Windows PowerShell permite-lhe preencher os nomes de ficheiros e nomes de cmdlet, premindo o **separador** chave.

> [!NOTE]
> Separador expansão é controlada pela função interna TabExpansion ou TabExpansion2. Uma vez que esta função pode ser modificada ou substituí-lo, este debate é um guia para o comportamento da configuração predefinida do PowerShell.

Para preencher automaticamente um nome de ficheiro ou caminho as escolhas disponíveis, escreva parte do nome e prima a **separador** chave. PowerShell irá expandir automaticamente o nome para a correspondência primeiro que encontra. Premir o **separador** chave repetidamente irá percorrer todas as escolhas disponíveis.

A expansão de separador de nomes de cmdlet é ligeiramente diferente. Para utilizar a expansão de separador no nome do cmdlet, escreva a parte do primeiro toda o nome de (o verbo) e o hífen seguinte. Pode preencher mais o nome de uma correspondência parcial. Por exemplo, se escrever **get-co** e, em seguida, prima a **separador** chave, PowerShell será automaticamente expandido para o **Get-Command** cmdlet (tenha em atenção que também altera as maiúsculas e minúsculas de letras ao respetivo formulário standard). Se premir **separador** chave novamente, PowerShell substitui isto com o apenas outro cmdlet nome correspondente, **Get-Content**.

Pode utilizar a expansão de separador repetidamente na mesma linha. Por exemplo, pode utilizar a expansão de separador no nome do **Get-Content** cmdlet introduzindo:

```
PS> Get-Con<Tab>
```

Quando prime o **separador** chave, o comando expande para:

```
PS> Get-Content
```

Pode, em seguida, parcialmente especifique o caminho para o ficheiro de registo de configuração do Active Directory e utilizar a expansão de separador novamente:

```
PS> Get-Content c:\windows\acts<Tab>
```

Quando prime o **separador** chave, o comando expande para:

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> Uma limitação do processo de expansão de separador é que os separadores são sempre interpretados como tentativas para concluir uma palavra. Se copiar e colar exemplos de comando para uma consola do PowerShell, certifique-se de que o exemplo contém separadores; Se tiver, os resultados imprevisíveis e quase certamente não serão os esperados.

