---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: A eliminação de pacotes
ms.openlocfilehash: ca5e68fcad52e4c7561d2c2b3858228652f22e0b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084169"
---
# <a name="deleting-packages"></a>Deleting Packages (Eliminar Pacotes)

A galeria do PowerShell não suporta a eliminação permanente de pacotes, porque isso quebraria qualquer pessoa que está dependendo de ele restantes disponíveis.

Em vez disso, a galeria do PowerShell suporta uma forma de "unlist' um pacote, o que pode ser feito na página pacote de gestão no web site.
Quando um pacote é não listado, ele já não aparece na pesquisa e, em qualquer pacote de listagem, ambos na galeria do PowerShell e utilizar comandos do PowerShellGet.
No entanto, permanece disponível para download, especificando sua versão exata, que é o que permite que os scripts automatizados continuar a trabalhar.

Caso se depare com uma situação excecional onde acha que um dos seus pacotes têm de ser eliminado, isso pode ser manipulado manualmente pela equipe de galeria do PowerShell.
Por exemplo, se houver um problema de infração de direitos autorais ou conteúdo potencialmente nocivo, que pode ser um motivo válido para eliminá-lo.
Deve submeter um pedido de suporte através de [galeria do PowerShell](http://www.PowerShellGallery.com) nesse caso.
