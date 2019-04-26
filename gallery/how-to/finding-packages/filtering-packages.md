---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Filtrar os resultados da pesquisa
ms.openlocfilehash: 13270a310613a974e1588a9f56d443a936cfebb8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084407"
---
# <a name="filtering-search-results"></a>Filtrar os resultados da pesquisa

O [guia de pacotes](https://www.powershellgallery.com/packages) apresenta todos os pacotes disponíveis na galeria do PowerShell.

Existem várias formas de filtrar, ordenar e pesquisar os pacotes.
Para ver mais detalhes sobre um determinado pacote, clique no pacote.

## <a name="filter-by"></a>Filtrar por

Na lista pendente em "Filtrar por" permite aos utilizadores filtrar os resultados por:
- Incluir pré-lançamento
- Apenas estável

Para obter informações sobre "Prerelease" e "Estável", consulte [versão de pré-lançamento do controle de versão adicionada à PowerShellGet e galeria do PowerShell](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) no Blog da Equipe do PowerShell.

As caixas de seleção na lista pendente permitem aos utilizadores filtrar os resultados por:
- Tipos de pacotes
  - Módulo
  - Script
- Categories
  - Cmdlet
  - Recursos de DSC
  - Função
  - Capacidade de função
  - Fluxo de trabalho

Para ver apenas os módulos na galeria do PowerShell, verifique o módulo os tipos de pacote.
Da mesma forma, para ver apenas os scripts na galeria do PowerShell, verifique o Script os tipos de pacote.

> [!NOTE]
> Os filtros são, inclusivos.
> Exemplo: Um pacote que contém cmdlets e funções será apresentada se o Cmdlet ou função (ou ambos) são verificadas.
> Se não forem selecionados, o pacote não serão apresentados.
> Da mesma forma, se forem selecionadas todas as categorias, serão apresentada apenas os pacotes que contêm uma dessas categorias.
> **Pacotes que não pertencem a qualquer uma dessas categorias não serão apresentados.**

## <a name="sort-by"></a>Ordenar por

Ordenar por pendente permite aos utilizadores ordenar os resultados por:
- Popularidade - popularidade é determinada pela contagem de Download
- A-Z - por ordem alfabética pelo nome do pacote
- Recentes - pacotes são apresentados por ordem da data de publicação

## <a name="search-box"></a>Caixa de pesquisa

Caixa de pesquisa permite que os usuários pesquisem os pacotes em palavras-chave.
Para obter mais informações, consulte [sintaxe de pesquisa da galeria](search-syntax.md).
