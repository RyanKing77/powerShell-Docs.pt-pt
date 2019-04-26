---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: ec4ae8e4b2ef0ec226cb75607f7aaf34b48f6b76
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085648"
---
# <a name="authoring-improvements-using-powershell-ise"></a>Melhorias na Criação com o ISE do PowerShell

Criação de configurações de DSC no ISE do Windows PowerShell é muito mais fácil, graças aos seguintes melhoramentos:

- Listar todos os recursos de DSC numa **configuration** bloco ou **nó** bloco introduzindo **Ctrl + espaço** numa linha em branco dentro do mesmo.
- Conclusão automática nas propriedades dos recursos que são do **enumeração** tipo.
- Conclusão automática no **DependsOn** propriedade de recursos de DSC, com base em outras instâncias de recurso na configuração.
- Conclusão de tabulação melhor dos valores de propriedade de recurso.

**Nota:** Tem de ter uma cadeia vazia para valores de propriedade do recurso antes de poder utilizar Ctrl + espaço para listar as opções. Premir **separador** ciclos por meio de opções.
