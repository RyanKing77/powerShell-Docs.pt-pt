---
ms.date: 06/12/2017
contributor: JKeithB
keywords: cmdlet do powershell do galeria, psgallery
title: Filtrar os resultados de pesquisa
ms.openlocfilehash: eafbc993a37eaee7413102ef9d669a6b07d6ff6e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="filtering-search-results"></a>Filtrar os resultados de pesquisa

O [separador itens](https://www.powershellgallery.com/items) apresenta todos os itens disponíveis na galeria do PowerShell.

Existem várias formas de filtrar, ordenar e os itens de pesquisa.
Para ver mais detalhes sobre um determinado item, clique no item.

## <a name="filter-by"></a>Filtrar por

Na lista pendente em "Filtrar por" permite que os utilizadores filtrar os resultados por:
- Incluir pré-lançamento
- Estável apenas

Para obter informações sobre "Pré-lançamento" e "Estável", consulte [adicionados de controlo de versões de pré-lançamento para PowerShellGet e galeria do PowerShell](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) no blogue de equipa do PowerShell.

As caixas de verificação em pendente permitem aos utilizadores filtrar os resultados por:
- Tipos de itens
  - Módulo
  - Script
- Categorias
  - Cmdlet
  - Recursos de DSC
  - Função
  - Capacidade de função
  - Fluxo de trabalho

Para ver apenas os módulos na galeria do PowerShell, consulte módulo nos tipos de Item.
Da mesma forma, para ver apenas os scripts na galeria do PowerShell, consulte os tipos de Item de Script.

> [!NOTE]
> Os filtros são inclusive.
> Exemplo: Um item que contém os cmdlets e funções será apresentada se o Cmdlet ou função (ou ambos) são verificadas.
> Se não forem selecionadas, o item não serão apresentados.
> Da mesma forma, se forem selecionadas todas as categorias, serão apresentado apenas os itens que contêm uma dessas categorias.
> **Não serão apresentados itens que não pertencem a nenhum nessas categorias.**

## <a name="sort-by"></a>Ordenar por

Ordenar por pendente permite aos utilizadores ordenar os resultados por:
- Popularidade - popularidade é determinada pelo número de transferir
- A-Z - por ordem alfabética pelo nome do item
- Recente - itens são apresentados por ordem da data de publicação

## <a name="search-box"></a>Caixa de pesquisa

Caixa de pesquisa permite aos utilizadores para os itens no palavras-chave de pesquisa.
Para obter mais informações, consulte [sintaxe de pesquisa de galeria](search-syntax.md).