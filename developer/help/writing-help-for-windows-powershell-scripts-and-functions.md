---
title: Gravando ajuda para scripts e funções do PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: af989fb2eeba6b68f2e3e6506f3f60d5be6f7d8a
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848095"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>Escrevendo ajuda para funções e scripts do PowerShell

Os scripts e funções do PowerShell devem ser totalmente documentados sempre que forem compartilhados com outras pessoas.
O `Get-Help` cmdlet exibe os tópicos de ajuda de script e função no mesmo formato que exibe ajuda para cmdlets e todos `Get-Help` os parâmetros funcionam nos tópicos de ajuda de script e função.

Os scripts do PowerShell podem incluir um tópico da ajuda sobre o script e tópicos de ajuda sobre cada função no script.
As funções que são compartilhadas independentemente dos scripts podem incluir seus próprios tópicos de ajuda.

Este documento explica o formato e o posicionamento correto dos tópicos da ajuda e sugere diretrizes para o conteúdo.

## <a name="types-of-script-and-function-help"></a>Tipos de ajuda de função e script

### <a name="comment-based-help"></a>Ajuda baseada em comentários
O tópico da ajuda que descreve um script ou uma função pode ser implementado como um conjunto de comentários dentro do script ou da função.
Ao escrever ajuda baseada em comentários para um script e para funções em um script, preste atenção às regras para colocar a ajuda baseada em comentários.
O posicionamento determina se o `Get-Help` cmdlet associa o tópico da ajuda ao script ou a uma função.
Para obter mais informações sobre como escrever tópicos de ajuda baseados em comentários, consulte [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

### <a name="xml-based-command-help"></a>Ajuda de comando baseada em XML
O tópico da ajuda que descreve um script ou uma função pode ser implementado em um arquivo XML que usa o esquema de ajuda de comando.
Para associar o script ou a função ao arquivo XML, use a `ExternalHelp` palavra-chave comment seguida pelo caminho e o nome do arquivo XML.

Quando a `ExternalHelp` palavra-chave comment está presente, ela tem precedência sobre a ajuda baseada em `Get-Help` comentários, mesmo quando não é possível encontrar um arquivo de `ExternalHelp` ajuda que corresponda ao valor da palavra-chave.

### <a name="online-help"></a>Ajuda online
Você pode postar os tópicos da ajuda na Internet e, em `Get-Help` seguida, direcionar para abrir os tópicos.
Para obter mais informações sobre como escrever tópicos de ajuda baseados em comentários, consulte [suporte à ajuda online](../module/supporting-online-help.md).

Não há nenhum método estabelecido para escrever tópicos conceituais ("sobre") para scripts e funções.
No entanto, você pode postar tópicos conceituais na Internet listar os tópicos e suas URLs na seção links relacionados de um tópico da ajuda de comando.

## <a name="content-considerations-for-script-and-function-help"></a>Considerações de conteúdo para ajuda de script e função

- Se você estiver escrevendo um tópico de ajuda muito breve com apenas algumas das seções de ajuda de comando disponíveis, certifique-se de incluir descrições claras do script ou dos parâmetros de função. Inclua também um ou dois comandos de exemplo na seção de exemplos, mesmo se você decidir omitir descrições de exemplo.

- Em todas as descrições, consulte o comando como um script ou uma função. Essas informações ajudam o usuário a entender e gerenciar o comando.

  Por exemplo, a descrição detalhada a seguir informa que o comando New-topic é um script. Isso lembra os usuários de que eles precisam para especificar o caminho e o nome completo quando eles o executam.

  > "O script New-topic cria um tópico conceitual em branco para cada nome de tópico no arquivo de entrada..."

  A descrição detalhada a seguir declara `Disable-PSRemoting` que é uma função. Essas informações são particularmente úteis para os usuários quando a sessão inclui vários comandos com o mesmo nome, alguns dos quais podem estar ocultos por um comando com precedência mais alta.

  > A `Disable-PSRemoting` função desabilita todas as configurações de sessão no computador local...

- Em um tópico de ajuda de script, explique como usar o script como um todo. Se você também estiver escrevendo tópicos de ajuda para funções no script, mencione as funções no tópico da ajuda do script e inclua referências aos tópicos da ajuda da função na seção links relacionados do tópico da ajuda de script. Por outro lado, quando uma função faz parte de um script, explique no tópico da ajuda da função a função que a função desempenha no script e como ela pode ser usada de forma independente. Em seguida, liste o tópico de ajuda de script na seção links relacionados do tópico da ajuda da função.

- Ao escrever exemplos para um tópico de ajuda de script, certifique-se de incluir o caminho para o arquivo de script no comando de exemplo. Isso lembra os usuários de que eles devem especificar o caminho explicitamente, mesmo quando o script está no diretório atual.

- Em um tópico da ajuda da função, lembre os usuários de que a função existe somente na sessão atual e, para usá-la em outras sessões, eles precisam adicioná-la ou adicioná-la a um perfil do PowerShell.

- `Get-Help`exibe o tópico da ajuda para um script ou função somente quando os arquivos de tópico do arquivo de script e da ajuda são salvos nos locais corretos. Portanto, não é útil incluir instruções para instalar o PowerShell ou salvar ou instalar o script ou a função em um tópico de ajuda de script ou função. Em vez disso, inclua as instruções de instalação no documento que você usa para distribuir o script ou a função.

## <a name="see-also"></a>Veja Também

[Escrevendo tópicos de ajuda baseados em comentários](./writing-comment-based-help-topics.md)
