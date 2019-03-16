---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recursos do DSC WaitForSome
ms.openlocfilehash: 888da1810f0a9233579bad5eef8d5dd556947c61
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059461"
---
# <a name="dsc-waitforsome-resource"></a>Recursos do DSC WaitForSome

> Aplica-se a: Windows PowerShell 5.0 e posterior

O **WaitForSome** recursos do Desired State Configuration (DSC) podem ser utilizado dentro de um bloco de nó num [configuração de DSC](../../../configurations/configurations.md) para especificar dependências em configurações nos outros nós.

Este recurso é bem-sucedida se o recurso especificado pela **ResourceName** propriedade está no Estado desejado num número mínimo de nós (especificado pelo **NodeCount**) definidos pelo **NodeName**  propriedade.


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
| NodeCount| O número mínimo de nós que tem de estar no estado pretendido para este recurso tenha êxito.|
| NodeName| Os nós de destino do recurso a dependem.|
| ResourceName| O nome de recurso a dependem. Se este recurso pertence a uma configuração diferente, formatar o nome como "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "|
| RetryIntervalSec| O número de segundos antes de tentar novamente. Mínimo é 1.|
| RetryCount| O número máximo de vezes a repetir.|
| ThrottleLimit| Número de máquinas para se conectar simultaneamente. A predefinição é padrão do novo-cimsession.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|
| PsDscRunAsCredential | Consulte [com DSC com as credenciais de utilizador](https://docs.microsoft.com/powershell/dsc/runasuser) |

## <a name="example"></a>Exemplo

Para obter um exemplo de como usar este recurso, consulte [especificar dependências entre nós](../../../configurations/crossNodeDependencies.md)
