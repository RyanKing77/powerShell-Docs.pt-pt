---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7730912707bb14e90a9926b387fb3a859d7ca26d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219271"
---
# <a name="convert-string"></a>Convert-String
**Converter a cadeia** expõe uma funcionalidade de "Substituir por magic". Fornecer antes e depois exemplos de como pretende que o texto a procurar, e **converter a cadeia** formata o texto automaticamente. Eis uma demonstração - demorar alguém primeiro e último nome e a respetiva substituição por seu apelido, uma vírgula, a primeira inicial do seu apelido e um ponto. Experimente com uma regex e ver o período de tempo que demora a.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
