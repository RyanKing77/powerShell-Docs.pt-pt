---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recursos do DSC WaitForAll
ms.openlocfilehash: 367f95caaa71ebec9c8e0a7c31fa5c0f5be27945
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226105"
---
# <a name="dsc-waitforall-resource"></a>Recursos do DSC WaitForAll

> Aplica-se a: PowerShell de Windows 5.0 e posterior

O **WaitForAll** recursos do Desired State Configuration (DSC) podem ser utilizado dentro de um bloco de nó num [configuração de DSC](configurations.md) para especificar dependências em configurações nos outros nós.

Este recurso é bem-sucedida se o recurso especificado pela **ResourceName** propriedade está no Estado desejado em todos os nós de destino definido no **NodeName** propriedade.


## <a name="syntax"></a>Sintaxe

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| ResourceName| O nome de recurso a dependem. Se este recurso pertence a uma configuração diferente, formatar o nome como "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "|
| NodeName| Os nós de destino do recurso a dependem.|
| RetryIntervalSec| O número de segundos antes de tentar novamente. Mínimo é 1.|
| RetryCount| O número máximo de vezes a repetir.|
| ThrottleLimit| Número de máquinas para se conectar simultaneamente. A predefinição é padrão do novo-cimsession.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|


## <a name="example"></a>Exemplo

Para obter um exemplo de como usar este recurso, consulte [especificar dependências entre nós](crossNodeDependencies.md)