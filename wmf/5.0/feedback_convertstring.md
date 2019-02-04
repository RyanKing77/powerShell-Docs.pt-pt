---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 27541d903748738675917941dc6b60bc9acdc3f4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684501"
---
# <a name="convert-string"></a><span data-ttu-id="e0c87-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="e0c87-102">Convert-String</span></span>
<span data-ttu-id="e0c87-103">**Cadeia de caracteres convert** expõe a funcionalidade de "Substituir por mágica".</span><span class="sxs-lookup"><span data-stu-id="e0c87-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="e0c87-104">Fornecer antes e depois de exemplos de como pretende que o texto deve parecer, e **Convert-String** formata automaticamente o seu texto.</span><span class="sxs-lookup"><span data-stu-id="e0c87-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="e0c87-105">Eis uma demonstração - tirar de alguém nome próprio e apelido e substituí-la com o sobrenome, uma vírgula, a primeira inicial do sobrenome e um ponto.</span><span class="sxs-lookup"><span data-stu-id="e0c87-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="e0c87-106">Experimente-o com um regex e ver o quanto ele leva-o.</span><span class="sxs-lookup"><span data-stu-id="e0c87-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
