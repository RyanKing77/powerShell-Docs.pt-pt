---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085331"
---
# <a name="new-guid"></a><span data-ttu-id="f8908-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="f8908-102">New-Guid</span></span>
<span data-ttu-id="f8908-103">Muitas vezes, o script (ou talvez escrever um recurso de DSC), tem a necessidade de um identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="f8908-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="f8908-104">GUIDs funcionam bem e é fácil chamar a classe Guid do .NET Framework para geração de um, mas ter um cmdlet torna isso mais detectáveis para os utilizadores finais que já não estiver familiarizados com a classe do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="f8908-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="f8908-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="f8908-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="f8908-106">Guid</span><span class="sxs-lookup"><span data-stu-id="f8908-106">Guid</span></span>

----

<span data-ttu-id="f8908-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="f8908-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
