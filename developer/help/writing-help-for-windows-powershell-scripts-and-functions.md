---
title: Escrever ajuda para funções e Scripts do PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: 98a3f61ff4fa2367f69357173d4e8e14288ff429
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083115"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>Escrever ajuda para funções e Scripts do PowerShell

Scripts do PowerShell e as funções devem ser documentadas sempre que são partilhados com outras pessoas.
O `Get-Help` cmdlet apresenta os tópicos de ajuda do script e a função no mesmo formato, como ele apresenta ajuda para cmdlets e todos os `Get-Help` parâmetros funcionam em tópicos de ajuda de script e a função.

Scripts do PowerShell podem incluir um tópico de ajuda sobre o script e tópicos de ajuda sobre as funções de cada no script.
As funções que são partilhadas independentemente dos scripts podem incluir seus próprios tópicos de ajuda.

Este documento explica o formato e a colocação correta dos tópicos de ajuda e sugere diretrizes para o conteúdo.

## <a name="types-of-script-and-function-help"></a>Tipos de Script e ajuda de função

### <a name="comment-based-help"></a>Ajuda baseada no comentário
O tópico de ajuda descreve um script ou função pode ser implementado como um conjunto de comentários dentro do script ou função.
Ao escrever a ajuda baseada no comentário para obter um script e para as funções num script, preste bastante atenção para as regras para colocar a ajuda baseada no comentário.
A colocação determina se o `Get-Help` cmdlet associa o tópico de ajuda com o script ou uma função.
Para obter mais informações sobre como escrever baseada no comentário tópicos de ajuda, consulte [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

### <a name="xml-based-command-help"></a>Ajuda do comando baseado em XML
O tópico de ajuda descreve um script ou função pode ser implementado num arquivo XML que usa o esquema de ajuda do comando.
Para associar o script ou função com o arquivo XML, utilize o `ExternalHelp` comentar a palavra-chave seguido o caminho e nome do arquivo XML.

Quando o `ExternalHelp` comentar a palavra-chave está presente, ele tem precedência sobre Ajuda baseada no comentário, mesmo quando `Get-Help` não é possível localizar um ficheiro de ajuda que corresponde ao valor da `ExternalHelp` palavra-chave.

### <a name="online-help"></a>Ajuda online
Pode postar seus tópicos de ajuda na Internet e, em seguida, direcionar `Get-Help` para abrir os tópicos.
Para obter mais informações sobre como escrever baseada no comentário tópicos de ajuda, consulte [apoio Ajuda Online](../module/supporting-online-help.md).

Não existe nenhum método estabelecido para escrita conceitual ("sobre") tópicos para scripts e funções.
No entanto, pode postar tópicos conceptuais na lista de Internet os tópicos e os URLs na seção Links relacionados de um tópico de ajuda do comando.

## <a name="content-considerations-for-script-and-function-help"></a>Considerações sobre o conteúdo para o Script e a função de ajuda

- Se estiver escrevendo um tópico de ajuda muito breve com apenas algumas das seções de ajuda do comando disponível, certifique-se de que incluem descrições claras dos parâmetros de script ou função. Também inclua um ou dois comandos de exemplo na secção de exemplos, mesmo se optar por omitir as descrições de exemplo.

- Em todas as descrições, consulte o comando como uma função ou script. Estas informações ajudam o utilizador para compreender e gerenciar o comando.

  Por exemplo, a descrição detalhada seguinte Estados que o comando New-tópico é um script. Isto irá relembrá-os utilizadores que necessitam para especificar o caminho e nome completo quando eles o executam.

  > "O script New-tópico cria um tópico conceptual em branco para cada nome de tópico no ficheiro de entrada..."

  Descrição detalhada a seguir indica que `Disable-PSRemoting` é uma função. Estas informações são particularmente úteis aos usuários quando a sessão inclui vários comandos com o mesmo nome, alguns dos quais botão poderá estar ocultado por um comando com precedência.

  > O `Disable-PSRemoting` função desativa todas as configurações de sessão no computador local...

- Um tópico de ajuda do script, explico como usar o script como um todo. Se também estiver a escrever tópicos de ajuda para as funções no script, mencionar as funções no seu tópico de ajuda de script e inclua referências para os tópicos de ajuda de função na seção Links relacionados do tópico de ajuda do script. Por outro lado, quando uma função faz parte de um script, explica o tópico de ajuda de função a função que a função desempenha no script e como ela pode ser usada independentemente. Em seguida, liste o tópico de ajuda do script na seção Links relacionados do tópico de ajuda de função.

- Ao escrever exemplos para um tópico de ajuda do script, certifique-se de que incluir o caminho para o ficheiro de script no comando de exemplo. Isto irá relembrá-os utilizadores que têm de especificar o caminho explicitamente, mesmo quando o script estiver no diretório atual.

- Um tópico de ajuda de função, lembrar aos usuários que a função existe apenas na sessão atual e usá-lo em outras sessões, que precisam para adicioná-lo ou adicioná-lo um perfil do PowerShell.

- `Get-Help` Apresenta o tópico de ajuda para um script ou função apenas quando o ficheiro de script e os ficheiros de tópico de ajuda são salvos nos locais corretos. Por conseguinte, não é útil incluir instruções para instalar o PowerShell, ou salvar ou instalar a função ou script num tópico de ajuda do script ou função. Em vez disso, incluem quaisquer instruções de instalação no documento que utilizar para distribuir o script ou função.

## <a name="see-also"></a>Veja Também

 [Escrever tópicos de ajuda baseados em XML para Scripts e funções](./writing-xml-based-help-topics-for-scripts-and-functions.md)

 [Escrever tópicos de ajuda baseados em XML para comandos](./writing-xml-based-help-topics-for-commands.md)

 [Escrever tópicos de ajuda baseada no comentário](./writing-comment-based-help-topics.md)
