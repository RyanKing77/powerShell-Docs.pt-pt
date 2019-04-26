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
# <a name="deleting-packages"></a><span data-ttu-id="2ca29-103">Deleting Packages (Eliminar Pacotes)</span><span class="sxs-lookup"><span data-stu-id="2ca29-103">Deleting Packages</span></span>

<span data-ttu-id="2ca29-104">A galeria do PowerShell não suporta a eliminação permanente de pacotes, porque isso quebraria qualquer pessoa que está dependendo de ele restantes disponíveis.</span><span class="sxs-lookup"><span data-stu-id="2ca29-104">The PowerShell Gallery does not support permanent deletion of packages, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="2ca29-105">Em vez disso, a galeria do PowerShell suporta uma forma de "unlist' um pacote, o que pode ser feito na página pacote de gestão no web site.</span><span class="sxs-lookup"><span data-stu-id="2ca29-105">Instead, the PowerShell Gallery supports a way to 'unlist' a package, which can be done in the package management page on the web site.</span></span>
<span data-ttu-id="2ca29-106">Quando um pacote é não listado, ele já não aparece na pesquisa e, em qualquer pacote de listagem, ambos na galeria do PowerShell e utilizar comandos do PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="2ca29-106">When a package is unlisted, it no longer shows up in search and in any package listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="2ca29-107">No entanto, permanece disponível para download, especificando sua versão exata, que é o que permite que os scripts automatizados continuar a trabalhar.</span><span class="sxs-lookup"><span data-stu-id="2ca29-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="2ca29-108">Caso se depare com uma situação excecional onde acha que um dos seus pacotes têm de ser eliminado, isso pode ser manipulado manualmente pela equipe de galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ca29-108">If you run into an exceptional situation where you think one of your packages must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="2ca29-109">Por exemplo, se houver um problema de infração de direitos autorais ou conteúdo potencialmente nocivo, que pode ser um motivo válido para eliminá-lo.</span><span class="sxs-lookup"><span data-stu-id="2ca29-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="2ca29-110">Deve submeter um pedido de suporte através de [galeria do PowerShell](http://www.PowerShellGallery.com) nesse caso.</span><span class="sxs-lookup"><span data-stu-id="2ca29-110">You should submit a support request through [PowerShell Gallery](http://www.PowerShellGallery.com) in that case.</span></span>
