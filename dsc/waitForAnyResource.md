---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos do DSC WaitForAny
ms.openlocfilehash: 3d73c16397d9a18805184e6a5bb8561483144898
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-waitforany-resource"></a>Recursos do DSC WaitForAny

> Aplica-se a: Windows PowerShell 5.1 e posterior

O **WaitForSome** recurso de configuração de estado pretendido (DSC) pode ser utilizado dentro de um bloco de nó num [configuração DSC](configurations.md) para especificar dependências em configurações nos outros nós.

Este recurso é bem sucedida se se o recurso especificado pelo **ResourceName** se encontra no estado pretendido em quaisquer nós de destino definido na propriedade o **NodeName** propriedade.


## <a name="syntax"></a>Sintaxe

```
WaitForAny [string] #ResourceName
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