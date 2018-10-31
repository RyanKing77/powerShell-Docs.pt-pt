---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Remover pacotes
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004173"
---
# <a name="unlisting-packages"></a>Pacotes unlisting

**Por isso que está a remover um pacote de galeria do PowerShell não é exposto como uma opção?**

A galeria do PowerShell não suporta utilizadores serem eliminados permanentemente a seus pacotes.
Isto permite que outros possam assumir dependências de seus pacotes sem se preocupar sobre quebras de possíveis no futuro.
Por exemplo, se o módulo de Pester depende do módulo do Azure e o módulo do Azure é removido a partir da galeria, em seguida, o utilizador pode já não utiliza o módulo de Pester.

Em vez de remover um pacote, no entanto, pode unlist-lo em vez disso.

**O que faz a remover um pacote na galeria do PowerShell fazer?**

Remover um pacote, como o módulo ou scripts numa galeria do PowerShell irá removê-lo do separador de pacotes. Além disso, os pacotes não listados não será Detetáveis através da barra de pesquisa.
A única forma de transferir um pacote não listado é especificar o nome exato e a versão do pacote.
Por este motivo, a remover de um pacote não irão interromper a outros módulos ou scripts que dependem dele.

Unlist seu pacote, visite a página de detalhes do pacote e selecione 'Eliminar módulo'. Desmarque a caixa de verificação "Apresentados" e clique em Guardar.

**Como posso remover um pacote?**

Se tiver um cenário em que a eliminação do pacote é necessária, contacte os administradores de galeria do PowerShell.
Cenários de eliminação válidos são:
- Problemas de infração de direitos autorais.
- Pacote contém conteúdo potencialmente prejudicial.
- Pacote contém dados confidenciais.

Para submeter um eliminar pedidos de pacote para os administradores de galeria do PowerShell, visite a página de detalhes do seu pacote e selecione contacte o suporte.
