---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 1595a3e817fd711c35128f06927fd57df7a63fb8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218251"
---
# <a name="authoring-improvements-using-powershell-ise"></a>Melhorias na Criação com o ISE do PowerShell

Criação de configurações de DSC no ISE do Windows PowerShell é muito mais fácil, obrigado para os seguintes melhoramentos:

- Listar todos os recursos de DSC dentro de um **configuração** bloco ou **nó** bloco introduzindo **Ctrl + espaço** numa linha em branco dentro da mesma.
- A conclusão automática no recurso as propriedades do **enumeração** tipo.
- A conclusão automática no **DependsOn** propriedade dos recursos de DSC, com base nas outras instâncias de recurso na configuração.
- Conclusão de separador melhor dos valores de propriedade de recurso.

**Nota:** tem de ter uma cadeia vazia para valores de propriedade de recurso antes de poder utilizar Ctrl + espaço para listar as opções. Premir **separador** percorre opções.
