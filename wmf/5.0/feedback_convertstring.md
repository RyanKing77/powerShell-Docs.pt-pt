---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7730912707bb14e90a9926b387fb3a859d7ca26d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="convert-string"></a><span data-ttu-id="fecc4-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="fecc4-102">Convert-String</span></span>
<span data-ttu-id="fecc4-103">**Converter a cadeia** expõe uma funcionalidade de "Substituir por magic".</span><span class="sxs-lookup"><span data-stu-id="fecc4-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="fecc4-104">Fornecer antes e depois exemplos de como pretende que o texto a procurar, e **converter a cadeia** formata o texto automaticamente.</span><span class="sxs-lookup"><span data-stu-id="fecc4-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="fecc4-105">Eis uma demonstração - demorar alguém primeiro e último nome e a respetiva substituição por seu apelido, uma vírgula, a primeira inicial do seu apelido e um ponto.</span><span class="sxs-lookup"><span data-stu-id="fecc4-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="fecc4-106">Experimente com uma regex e ver o período de tempo que demora a.</span><span class="sxs-lookup"><span data-stu-id="fecc4-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
