---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recursos do DSC WaitForAny
ms.openlocfilehash: d15acb3fb34d571eca56ed496eaa9a04b2551ff0
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726848"
---
# <a name="dsc-waitforany-resource"></a>Recursos do DSC WaitForAny

> Aplica-se a: Windows PowerShell 5.1 e versões posterior

O **WaitForAny** recursos do Desired State Configuration (DSC) podem ser utilizado dentro de um bloco de nó num [configuração de DSC](../../../configurations/configurations.md) para especificar dependências em configurações nos outros nós.

Este recurso é bem-sucedida se o recurso especificado pela **ResourceName** propriedade está no Estado desejado em quaisquer nós de destino definido no **NodeName** propriedade.

> [!NOTE]
> **WaitForAny** recursos utilizam a gestão remota do Windows para verificar o estado de outros nós.
> Para obter mais informações sobre os requisitos de segurança e de porta para o WinRM, consulte [considerações de segurança de comunicação remota do PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).

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

## <a name="properties"></a>properties

|  Propriedade  |  Descrição   |
|---|---|
| ResourceName| O nome de recurso a dependem. Se este recurso pertence a uma configuração diferente, formatar o nome como "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "|
| NodeName| Os nós de destino do recurso a dependem.|
| RetryIntervalSec| O número de segundos antes de tentar novamente. Mínimo é 1.|
| RetryCount| O número máximo de vezes a repetir.|
| ThrottleLimit| Número de máquinas para se conectar simultaneamente. A predefinição é padrão do novo-cimsession.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exemplo

Para obter um exemplo de como usar este recurso, consulte [especificar dependências entre nós](../../../configurations/crossNodeDependencies.md)
