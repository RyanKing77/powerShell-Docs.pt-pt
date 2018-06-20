---
ms.date: 06/12/2017
contributor: JKeithB
keywords: cmdlet do powershell do galeria, psgallery
title: Sintaxe de pesquisa de galeria
ms.openlocfilehash: 52fca21a00bcc6e3789bceb331acf5bc771bb0f2
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188416"
---
# <a name="gallery-search-syntax"></a>Sintaxe de pesquisa de galeria

Galeria do PowerShell oferece um searchbox de texto em que pode utilizar palavras, expressões e expressões de palavra-chave para restringir os resultados da pesquisa.

## <a name="search-by-keywords"></a>Procura por palavras-chave

    dsc azure sql

Pesquisa fazer o seu melhor esforço para localizar documentos relevantes que contém as 3 todas as palavras-chave e devolver documentos correspondentes.

## <a name="search-using-phrases-and-keywords"></a>A procura utilizando expressões e palavras-chave

    "azure sql" deployment

Introduzir uma frase de acesso entre aspas ("") altere a procura para procurar o frase específica em vez de palavras-chave separadas.
Correspondência de documentos, normalmente, deve conter o frase exato "sql do azure", incluindo variações no maiúsculas/minúsculas por exemplo "SQL do azure" e também normalmente contém a palavra 'implementação'.

## <a name="filtering-on-fields"></a>Nos campos de filtragem

Pode procurar um ID de item específico (ou 'Id' ou 'id') ou alguns outros campos por lhe o prefixo procurar termos com o nome do campo.

Atualmente os campos pesquisáveis são 'Id', 'Version', 'Etiquetas', 'Autor', 'Proprietário', 'Funções', 'Cmdlets', 'DscResources' e 'PowerShellVersion'.

[O que é a diferença entre ID e título? O ID é o nome que utiliza na consola do. Título é o que é apresentado na parte superior da página item nos resultados da pesquisa.]

## <a name="examples"></a>Exemplos

    ID:"PSReadline"
    id:"AzureRM.Profile"

Localiza itens com "PSReadline" ou "AzureRM.Profile" no respetivo campo de ID, respetivamente.

    Id:"AzureRM.Profile"

é outra forma para localizar itens com "AzureRM.Profile" no respetivo campo de ID.

O filtro 'Id' é uma subcadeia corresponderem, por isso se procurar o seguinte:

    Id:"azure"

Irá obter resultados como 'AzureRM.Profile' e 'Azure.Storage'.

Poderá também pesquisar por várias palavras-chave num campo único. Ou combinar e misturar campos.

    id:azure tags:intellisense
    id:azure id:storage

E pode efetuar pesquisas de expressão:

    id:"azure.storage"


Para procurar todos os itens com a etiqueta de DSC.

    Tags:"DSC"

Para procurar todos os itens com a função especificada.

    Functions:"Update-AzureRM"

Para procurar todos os itens com o cmdlet especificado.

    Cmdlets:"Get-AzureRmEnvironment"

Para procurar todos os itens com o nome de recursos de DSC especificado.

    DscResources:"xArchive"

Para procurar todos os itens com o PowerShellVersion especificado

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


Por fim, se utilizar um campo que não é suportada, como 'comandos', vamos apenas ignorá-lo e todos os campos de pesquisa. Por isso, a seguinte consulta

    commands:blobs storage

É interpretado exatamente o mesmo que esta consulta:

    blobs storage