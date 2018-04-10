---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 3b2c268cd10d7c421b3d1fc73a7bbeaa4714f5fc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="authoring-improvements-using-powershell-ise"></a>Melhorias na Criação com o ISE do PowerShell

Criação de configurações de DSC no ISE do Windows PowerShell é muito mais fácil, obrigado para os seguintes melhoramentos:

- Listar todos os recursos de DSC dentro de um **configuração** bloco ou **nó** bloco introduzindo **Ctrl + espaço** numa linha em branco dentro da mesma.
- A conclusão automática no recurso as propriedades do **enumeração** tipo.
- A conclusão automática no **DependsOn** propriedade dos recursos de DSC, com base nas outras instâncias de recurso na configuração.
- Conclusão de separador melhor dos valores de propriedade de recurso.

**Nota:** tem de ter uma cadeia vazia para valores de propriedade de recurso antes de poder utilizar Ctrl + espaço para listar as opções. Premir **separador** percorre opções.