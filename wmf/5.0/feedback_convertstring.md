---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 6caff8c06174a1dcb990ed8e5062ccca5848dbb8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="convert-string"></a>Converter a cadeia
**Converter a cadeia** expõe uma funcionalidade de "Substituir por magic". Fornecer antes e depois exemplos de como pretende que o texto a procurar, e **converter a cadeia** formata o texto automaticamente. Eis uma demonstração - demorar alguém primeiro e último nome e a respetiva substituição por seu apelido, uma vírgula, a primeira inicial do seu apelido e um ponto. Experimente com uma regex e ver o período de tempo que demora a.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```

