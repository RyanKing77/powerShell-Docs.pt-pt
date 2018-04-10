---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 302a347b0f4c9c322f7701e8d6a721f9ffba9b59
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="convert-string"></a><span data-ttu-id="ce133-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="ce133-102">Convert-String</span></span>
<span data-ttu-id="ce133-103">**Converter a cadeia** expõe uma funcionalidade de "Substituir por magic".</span><span class="sxs-lookup"><span data-stu-id="ce133-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="ce133-104">Fornecer antes e depois exemplos de como pretende que o texto a procurar, e **converter a cadeia** formata o texto automaticamente.</span><span class="sxs-lookup"><span data-stu-id="ce133-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="ce133-105">Eis uma demonstração - demorar alguém primeiro e último nome e a respetiva substituição por seu apelido, uma vírgula, a primeira inicial do seu apelido e um ponto.</span><span class="sxs-lookup"><span data-stu-id="ce133-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="ce133-106">Experimente com uma regex e ver o período de tempo que demora a.</span><span class="sxs-lookup"><span data-stu-id="ce133-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```