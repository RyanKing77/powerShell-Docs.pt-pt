---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: Remover itens da lista
ms.openlocfilehash: 35dcd283ddace5aec62d692b0ede12ae0bada765
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/10/2018
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