---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 27541d903748738675917941dc6b60bc9acdc3f4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057796"
---
# <a name="convert-string"></a>Convert-String
**Cadeia de caracteres convert** expõe a funcionalidade de "Substituir por mágica". Fornecer antes e depois de exemplos de como pretende que o texto deve parecer, e **Convert-String** formata automaticamente o seu texto. Eis uma demonstração - tirar de alguém nome próprio e apelido e substituí-la com o sobrenome, uma vírgula, a primeira inicial do sobrenome e um ponto. Experimente-o com um regex e ver o quanto ele leva-o.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
