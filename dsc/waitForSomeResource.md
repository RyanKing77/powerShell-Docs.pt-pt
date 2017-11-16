---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos do DSC WaitForSome
ms.openlocfilehash: 3ea9dc51cbb00cf6158abf114fdb31fd91307df9
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/13/2017
---
# <a name="dsc-waitforsome-resource"></a>Recursos do DSC WaitForSome

> Aplica-se a: Windows PowerShell 5.0 e posterior

O **WaitForAny** recurso de configuração de estado pretendido (DSC) pode ser utilizado dentro de um bloco de nó num [configuração DSC](configurations.md) para especificar dependências em configurações nos outros nós.

Este recurso é bem sucedida se o recurso especificado pelo **ResourceName** propriedade está no estado pretendido num número mínimo de nós (especificada por **NodeCount**) definidos pelo **NodeName**  propriedade. 


## <a name="syntax"></a>Sintaxe

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   | 
|---|---| 
| NodeCount| O número mínimo de nós que têm de estar no estado pretendido para este recurso com êxito.|
| nodeName| Os nós de destino do recurso dependem.| 
| resourceName| O nome de recurso a dependem.| 
| RetryIntervalSec| O número de segundos antes de repetir a operação. Mínimo é 1.| 
| retryCount| O número máximo de vezes para tentar novamente.| 
| ThrottleLimit| Número de máquinas para ligar em simultâneo. Predefinição é novo-cimsession predefinido.| 
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|
| PsDscRunAsCredential | Consulte [através de DSC com credenciais de utilizador](https://docs.microsoft.com/en-us/powershell/dsc/runasuser) |


## <a name="example"></a>Exemplo

Para obter um exemplo de como utilizar este recurso, consulte [especificar dependências entre nós](crossNodeDependencies.md)

