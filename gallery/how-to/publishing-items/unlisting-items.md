---
ms.date: 06/12/2017
contributor: JKeithB
keywords: cmdlet do powershell do galeria, psgallery
title: Remover itens da lista
ms.openlocfilehash: bdcceba0ba18ade6a1d0f94602fd8d0f64af8936
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187543"
---
# <a name="unlisting-items"></a>Remover itens da lista

**Razão pela qual está a remover um item da galeria do PowerShell não exposta como uma opção?**

A galeria do PowerShell não suporta utilizadores eliminados permanentemente os itens.
Isto permite que os outros possam desempenhar as dependências dos itens sem se preocupar quebras possíveis no futuro.
Por exemplo, se o módulo de Pester depende do módulo do Azure e o módulo do Azure é removido do galeria, em seguida, o utilizador pode já não utiliza o módulo de Pester.

Em vez de um item a remover, no entanto, é pode unlist-lo em vez disso.

**O que faz unlisting um item na galeria do PowerShell fazer?**

Unlisting um item como módulo ou script na galeria do PowerShell irá removê-lo no separador itens. Além disso, não listados itens deixarão de estar Detetáveis utilizando a barra de pesquisa.
É a única forma de transferir um item não listado para especificar o nome exato e a versão do item.
Por este motivo, unlisting de um item não irão interromper a outros módulos ou scripts que dependem dele.

Para unlist o item, visite a página de detalhes do item e selecione 'Eliminar Item'. Desmarque a caixa de verificação 'Apresentados' e clique em Guardar.

**Como posso remover um item?**

Se ocorrer um cenário em que a eliminação do item é necessária, contacte os administradores de galeria do PowerShell.
Cenários de eliminação válidos são:
- Problemas de violação de direitos de autor.
- Item contém conteúdo potencialmente prejudicial.
- O item contém dados confidenciais.

Para submeter um eliminar o Item pedido aos administradores de galeria do PowerShell, visite a página de detalhes do item e selecione contacte o suporte.