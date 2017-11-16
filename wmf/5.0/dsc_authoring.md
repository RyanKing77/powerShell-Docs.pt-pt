---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 555e01e88647b40717417360fb74bb6554a9c122
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="authoring-improvements-using-powershell-ise"></a>Melhoramentos de criação utilizando o ISE do PowerShell

Criação de configurações de DSC no ISE do Windows PowerShell é muito mais fácil, obrigado para os seguintes melhoramentos:

- Listar todos os recursos de DSC dentro de um **configuração** bloco ou **nó** bloco introduzindo **Ctrl + espaço** numa linha em branco dentro da mesma.
- A conclusão automática no recurso as propriedades do **enumeração** tipo.
- A conclusão automática no **DependsOn** propriedade dos recursos de DSC, com base nas outras instâncias de recurso na configuração.
- Conclusão de separador melhor dos valores de propriedade de recurso.

**Nota:** tem de ter uma cadeia vazia para valores de propriedade de recurso antes de poder utilizar Ctrl + espaço para listar as opções. Premir **separador** percorre opções.

