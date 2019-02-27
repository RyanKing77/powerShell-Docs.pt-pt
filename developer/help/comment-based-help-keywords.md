---
title: Palavras-chave de ajuda baseada no comentário | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab90ec96-77f5-42e3-9c7e-2f4156ec207f
caps.latest.revision: 6
ms.openlocfilehash: dbb6f7c4cbefeaaaec0747511f50192bcf08c20c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851472"
---
# <a name="comment-based-help-keywords"></a>Comment-Based Help Keywords (Palavras-chave de Ajuda Baseada em Comentários)

Este tópico apresenta e descreve as palavras-chave na ajuda baseada no comentário.

## <a name="keywords-in-comment-based-help"></a>Palavras-chave na ajuda baseada no comentário

Seguem-se válido com base em comentários ajuda palavras-chave. Estes são apresentados na ordem em que normalmente aparecem num tópico de ajuda, juntamente com seu uso pretendido. Estas palavras-chave pode aparecer em qualquer ordem na ajuda do baseada no comentário, e não diferenciam maiúsculas de minúsculas.

Tenha em atenção que o `.ExternalHelp` palavra-chave tem precedência sobre todas as outras ajuda baseada no comentário palavras-chave. Quando `.ExternalHelp` estiver presente, o [Microsoft.Powershell.Commands.Get-Help](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) cmdlet não apresenta a ajuda baseada no comentário, mesmo quando não for possível encontrar um arquivo de ajuda que corresponde ao valor da palavra-chave.

`.Synopsis` Uma breve descrição da função ou script. Esta palavra-chave pode ser utilizado apenas uma vez em cada tópico.

`.Description` Uma descrição detalhada da função ou script. Esta palavra-chave pode ser utilizado apenas uma vez em cada tópico.

`.Parameter` *\<Nome do parâmetro >* a descrição de um parâmetro. Pode incluir um `.Parameter` palavra-chave para cada parâmetro na função ou script.

O `.Parameter` palavras-chave podem aparecer em qualquer ordem no bloco de comentário, mas a ordem em que os parâmetros aparecem no `Param` declaração de função ou instrução determina a ordem em que os parâmetros são apresentadas no tópico de ajuda. Para alterar a ordem dos parâmetros no tópico de ajuda, alterar a ordem dos parâmetros a `Param` declaração instrução ou a função.

Também pode especificar uma descrição de parâmetro ao colocar um comentário no `Param` instrução imediatamente antes do nome de variável de parâmetro. Se utilizar ambos um `Param` comentário de instrução e uma `.Parameter` palavra-chave, a descrição associada a `.Parameter` palavra-chave é usada e o `Param` comentário de declaração é ignorado.

`.Example` Um comando de exemplo que utiliza a função ou script, seguido opcionalmente de saída de exemplo e uma descrição. Repita esta palavra-chave para cada exemplo.

`.Inputs` Os tipos de Microsoft .NET Framework de objetos que podem ser encaminhados para a função ou script. Também pode incluir uma descrição dos objetos de entrada.

`.Outputs` O tipo de .NET Framework, os objetos que o cmdlet devolve. Também pode incluir uma descrição dos objetos devolvidos.

`.Notes` Obter informações adicionais sobre a função ou script.

`.Link` O nome do tópico relacionado. Repita esta palavra-chave para cada tópico relacionado. Este conteúdo é apresentada na seção Links relacionados do tópico de ajuda.

O `.Link` conteúdo de palavra-chave também pode incluir um identificador de recurso uniforme (URI) para uma versão online do mesmo tópico de ajuda. A versão online abre quando utiliza o `Online` parâmetro de Get-Help. O URI tem de começar com "http" ou "https".

`.Component` A tecnologia ou funcionalidade que utiliza a função ou script, ou para o qual ele está relacionado. Este conteúdo é apresentado quando o comando Get-Help inclui o `Component` parâmetro de Get-Help.

`.Role` A função de utilizador para o tópico de ajuda. Este conteúdo é apresentado quando o comando Get-Help inclui o `Role` parâmetro de Get-Help.

`.Functionality` O uso pretendido da função. Este conteúdo é apresentado quando o comando Get-Help inclui o `Functionality` parâmetro de Get-Help.

`.ForwardHelpTargetName` `<Command-Name>` Redireciona para o tópico de ajuda para o comando especificado. Pode redirecionar os utilizadores para qualquer tópico de ajuda, incluindo tópicos de ajuda para uma função, o script, o cmdlet ou o fornecedor.

`.ForwardHelpCategory` `<Category>` Especifica a categoria de ajuda do item no ForwardHelpTargetName. Valores válidos são Alias, Cmdlet, HelpFile, função, fornecedor, geral, perguntas frequentes, glossário, ScriptCommand, ExternalScript, filtro ou todos. Utilize esta palavra-chave para evitar conflitos quando há comandos com o mesmo nome.

`.RemoteHelpRunspace` `<PSSession-variable>` Especifica uma sessão que contém o tópico de ajuda. Introduza uma variável que contém uma PSSession. Esta palavra-chave é utilizada pelo `Export-PSSession` cmdlet para encontrar os tópicos de ajuda para os comandos exportados.

`.ExternalHelp` `<XML Help File>` Especifica o caminho de e/ou o nome de um arquivo de ajuda baseados em XML para o script ou função.

O `.ExternalHelp` informa a palavra-chave a [Microsoft.Powershell.Commands.Get-Help](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) cmdlet para obter ajuda para a função ou script num arquivo baseado em XML. O **. ExternalHelp** palavra-chave é necessário quando utilizar um arquivo de ajuda baseados em XML para uma função ou script. Sem ele, `Get-Help` não irá encontrar um arquivo de ajuda para a função ou script.

O `.ExternalHelp` palavra-chave tem precedência sobre todas as outras ajuda baseada no comentário palavras-chave. Quando `.ExternalHelp` estiver presente, o [Microsoft.Powershell.Commands.Get-Help](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) cmdlet não apresenta a ajuda baseada no comentário, mesmo quando não for possível encontrar um arquivo de ajuda que corresponde ao valor da palavra-chave.

Quando a função é exportada por um módulo de script, o valor de `.ExternalHelp` deve ser um nome de ficheiro sem um caminho. `Get-Help` procura o arquivo num subdiretório específico da localidade do diretório de módulo. Existem não requisitos para o nome de ficheiro, mas uma prática recomendada é usar o seguinte formato de nome de ficheiro: `<ScriptModule>.psm1-help.xml`.

Quando a função não está associada um módulo, incluem um nome de ficheiro e caminho no valor do **. ExternalHelp** palavra-chave. Se o caminho especificado para o ficheiro XML contém subdiretórios específicos da cultura da interface do Usuário, `Get-Help` procura recursivamente a subdiretórios para um arquivo XML com o nome do script ou função de acordo com o idioma de fallback normas estabelecidas para Windows, como faz para todos os tópicos de ajuda baseados em XML.

Para obter mais informações sobre o formato de arquivo de ajuda baseados em XML de ajuda do cmdlet, consulte [ajuda do Cmdlet escrita Windows PowerShell](./writing-help-for-windows-powershell-cmdlets.md).