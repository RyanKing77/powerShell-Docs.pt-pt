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
# <a name="convert-string"></a>Convert-String
**Converter a cadeia** expõe uma funcionalidade de "Substituir por magic". Fornecer antes e depois exemplos de como pretende que o texto a procurar, e **converter a cadeia** formata o texto automaticamente. Eis uma demonstração - demorar alguém primeiro e último nome e a respetiva substituição por seu apelido, uma vírgula, a primeira inicial do seu apelido e um ponto. Experimente com uma regex e ver o período de tempo que demora a.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```