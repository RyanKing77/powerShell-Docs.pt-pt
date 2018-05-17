---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos do DSC WaitForAll
ms.openlocfilehash: 4413220bb0b5eeef5fd1599f794cd551f15a2925
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-waitforall-resource"></a>Recursos do DSC WaitForAll

> Aplica-se a: Windows PowerShell 5.0 e posterior

O **WaitForAll** recurso de configuração de estado pretendido (DSC) pode ser utilizado dentro de um bloco de nó num [configuração DSC](configurations.md) para especificar dependências em configurações nos outros nós.

Este recurso é bem sucedida se se o recurso especificado pelo **ResourceName** se encontra no estado pretendido em todos os nós de destino definido na propriedade o **NodeName** propriedade.


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
| ResourceName| O nome de recurso a dependem. Se este recurso pertence a uma configuração diferente, o nome de formato "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]: [ __ConfigurationName__] "|
| NodeName| Os nós de destino do recurso dependem.|
| RetryIntervalSec| O número de segundos antes de repetir a operação. Mínimo é 1.|
| RetryCount| O número máximo de vezes para tentar novamente.|
| ThrottleLimit| Número de máquinas para ligar em simultâneo. Predefinição é novo-cimsession predefinido.|
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|


## <a name="example"></a>Exemplo

Para obter um exemplo de como utilizar este recurso, consulte [especificar dependências entre nós](crossNodeDependencies.md)