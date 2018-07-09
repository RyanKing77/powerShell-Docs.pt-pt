---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Eliminar itens
ms.openlocfilehash: 454cd404437bf1c31b9a1b81cd9dd0ac81e6b0f6
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893098"
---
# <a name="deleting-items"></a>Eliminar itens

A galeria do PowerShell não suporta a eliminação permanente de itens, porque isso quebraria qualquer pessoa que está dependendo de ele restantes disponíveis.

Em vez disso, a galeria do PowerShell suporta uma forma de "unlist' um item, o que pode ser feito na página de gestão do item no web site.
Quando um item é não listado, ele já não aparece na pesquisa e, em qualquer item de listagem, ambos na galeria do PowerShell e utilizar comandos do PowerShellGet.
No entanto, permanece disponível para download, especificando sua versão exata, que é o que permite que os scripts automatizados continuar a trabalhar.

Caso se depare com uma situação excecional onde acha que um dos seus itens têm de ser eliminado, isso pode ser manipulado manualmente pela equipe de galeria do PowerShell.
Por exemplo, se houver um problema de infração de direitos autorais ou conteúdo potencialmente nocivo, que pode ser um motivo válido para eliminá-lo.
Deve submeter um pedido de suporte através de [galeria do PowerShell](http://www.PowerShellGallery.com) nesse caso.