---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Sintaxe de pesquisa da Galeria
ms.openlocfilehash: 9aadb6771c85845cc3fa05cb56f0194b060d1c1b
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004148"
---
# <a name="gallery-search-syntax"></a>Sintaxe de pesquisa da Galeria

Galeria do PowerShell oferece uma caixa de pesquisa de texto em que pode usar palavras, frases e expressões de palavra-chave para limitar os resultados da pesquisa.

## <a name="search-by-keywords"></a>Procurar por palavras-chave

    dsc azure sql

Pesquisa fará o melhor esforço para encontrar os documentos relevantes que contém todas as palavras-chave de 3 e devolver os documentos correspondentes.

## <a name="search-using-phrases-and-keywords"></a>Utilizar frases e palavras-chave de pesquisa

    "azure sql" deployment

Introduzir uma frase entre aspas ("") altere a procura para procurar a frase específica em vez de palavras-chave separadas.
Documentos correspondentes, normalmente, devem conter a frase exata "sql do azure", incluindo variações na capitalização p. ex. "SQL do azure" e também normalmente contêm a palavra "implementação".

## <a name="filtering-on-fields"></a>Filtrar em campos

Pode pesquisar por um ID de pacote específico (ou "Id" ou "id") ou termos com o nome do campo de pesquisa de determinados outros campos colocando um prefixo.

Atualmente, os campos pesquisáveis são 'Id', 'Versão', "Etiquetas", "Autor", "Owner", "Funções", "Cmdlets", 'DscResources' e 'PowerShellVersion'.

[O que é a diferença entre o ID e o título? O ID é o nome que utiliza na consola do. O título é o que é mostrado na parte superior da página pacote nos resultados da pesquisa.]

## <a name="examples"></a>Exemplos

    ID:"PSReadline"
    id:"AzureRM.Profile"

encontra pacotes com "PSReadline" ou "Azurerm. Profile" no respetivo campo de ID, respetivamente.

    Id:"AzureRM.Profile"

é outra maneira de encontrar os pacotes com "Azurerm. Profile" no respetivo campo de ID.

O filtro de "Id" é uma subcadeia de corresponder, se pesquisar para o seguinte:

    Id:"azure"

Obterá resultados como 'Azurerm. Profile' e 'Azure.Storage'.

Também pode pesquisar por várias palavras-chave num único campo. Ou combinar e corresponder aos campos.

    id:azure tags:intellisense
    id:azure id:storage

E pode efetuar pesquisas de frase:

    id:"azure.storage"


Para pesquisar todos os pacotes com a etiqueta de DSC.

    Tags:"DSC"

Para pesquisar todos os pacotes com a função especificada.

    Functions:"Update-AzureRM"

Para pesquisar todos os pacotes com o cmdlet especificado.

    Cmdlets:"Get-AzureRmEnvironment"

Para pesquisar todos os pacotes com o nome de recurso de DSC especificado.

    DscResources:"xArchive"

Para pesquisar todos os pacotes com o PowerShellVersion especificado

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


Por fim, se usar um campo que não é suportada, por exemplo, 'commands', vou ignorá-lo e todos os campos de pesquisa. Portanto, a seguinte consulta

    commands:blobs storage

É interpretado exatamente o mesmo que esta consulta:

    blobs storage
