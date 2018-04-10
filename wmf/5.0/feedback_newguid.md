---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 91c115c7f0553cd5edf7fecf04e6a5c71c0a1aa2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="new-guid"></a><span data-ttu-id="7429f-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="7429f-102">New-Guid</span></span>
<span data-ttu-id="7429f-103">Muitas vezes, o script (ou talvez ao escrever um recurso de DSC), tem a necessidade de um identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="7429f-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="7429f-104">GUIDs funcionam bem e é fácil chamar a classe de .NET Framework Guid para gerar um, mas com um cmdlet faz com que esta mais detetável para utilizadores finais que já não estiver familiarizados com a classe do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="7429f-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="7429f-105">PS c:\\ &gt; novo Guid</span><span class="sxs-lookup"><span data-stu-id="7429f-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="7429f-106">GUID</span><span class="sxs-lookup"><span data-stu-id="7429f-106">Guid</span></span>

----

<span data-ttu-id="7429f-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="7429f-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>