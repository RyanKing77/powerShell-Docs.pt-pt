---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 2d6b4e3045bc8cff90576c345d1ccb97b2487426
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="new-guid"></a><span data-ttu-id="5b1ba-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="5b1ba-102">New-Guid</span></span>
<span data-ttu-id="5b1ba-103">Muitas vezes, o script (ou talvez ao escrever um recurso de DSC), tem a necessidade de um identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="5b1ba-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="5b1ba-104">GUIDs funcionam bem e é fácil chamar a classe de .NET Framework Guid para gerar um, mas com um cmdlet faz com que esta mais detetável para utilizadores finais que já não estiver familiarizados com a classe do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="5b1ba-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="5b1ba-105">PS c:\\ &gt; novo Guid</span><span class="sxs-lookup"><span data-stu-id="5b1ba-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="5b1ba-106">GUID</span><span class="sxs-lookup"><span data-stu-id="5b1ba-106">Guid</span></span>

----

<span data-ttu-id="5b1ba-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="5b1ba-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
