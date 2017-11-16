---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos do DSC WaitForAny
ms.openlocfilehash: ba1873cc0ecfc4596cbad5b61b4a52b61ea4778a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
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
| resourceName| O nome de recurso a dependem.| 
| nodeName| Os nós de destino do recurso dependem.| 
| RetryIntervalSec| O número de segundos antes de repetir a operação. Mínimo é 1.| 
| retryCount| O número máximo de vezes para tentar novamente.| 
| ThrottleLimit| Número de máquinas para ligar em simultâneo. Predefinição é novo-cimsession predefinido.| 
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|


## <a name="example"></a>Exemplo

Para obter um exemplo de como utilizar este recurso, consulte [especificar dependências entre nós](crossNodeDependencies.md)
