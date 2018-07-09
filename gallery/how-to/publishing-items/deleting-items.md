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
# <a name="deleting-items"></a><span data-ttu-id="22fa1-103">Eliminar itens</span><span class="sxs-lookup"><span data-stu-id="22fa1-103">Deleting items</span></span>

<span data-ttu-id="22fa1-104">A galeria do PowerShell não suporta a eliminação permanente de itens, porque isso quebraria qualquer pessoa que está dependendo de ele restantes disponíveis.</span><span class="sxs-lookup"><span data-stu-id="22fa1-104">The PowerShell Gallery does not support permanent deletion of items, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="22fa1-105">Em vez disso, a galeria do PowerShell suporta uma forma de "unlist' um item, o que pode ser feito na página de gestão do item no web site.</span><span class="sxs-lookup"><span data-stu-id="22fa1-105">Instead, the PowerShell Gallery supports a way to 'unlist' an item, which can be done in the item management page on the web site.</span></span>
<span data-ttu-id="22fa1-106">Quando um item é não listado, ele já não aparece na pesquisa e, em qualquer item de listagem, ambos na galeria do PowerShell e utilizar comandos do PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="22fa1-106">When an item is unlisted, it no longer shows up in search and in any item listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="22fa1-107">No entanto, permanece disponível para download, especificando sua versão exata, que é o que permite que os scripts automatizados continuar a trabalhar.</span><span class="sxs-lookup"><span data-stu-id="22fa1-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="22fa1-108">Caso se depare com uma situação excecional onde acha que um dos seus itens têm de ser eliminado, isso pode ser manipulado manualmente pela equipe de galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22fa1-108">If you run into an exceptional situation where you think one of your items must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="22fa1-109">Por exemplo, se houver um problema de infração de direitos autorais ou conteúdo potencialmente nocivo, que pode ser um motivo válido para eliminá-lo.</span><span class="sxs-lookup"><span data-stu-id="22fa1-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="22fa1-110">Deve submeter um pedido de suporte através de [galeria do PowerShell](http://www.PowerShellGallery.com) nesse caso.</span><span class="sxs-lookup"><span data-stu-id="22fa1-110">You should submit a support request through [PowerShell Gallery](http://www.PowerShellGallery.com) in that case.</span></span>