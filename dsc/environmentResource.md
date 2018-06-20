---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Recurso de ambiente de DSC
ms.openlocfilehash: 023ecf4cc2e3f553770d9c49a94b6e903e560b01
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187304"
---
# <a name="dsc-environment-resource"></a>Recurso de ambiente de DSC

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

O __ambiente__ recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir as variáveis de ambiente de sistema.

## <a name="syntax"></a>Sintaxe
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| Nome| Indica o nome da variável de ambiente para o qual pretende garantir um estado específico.|
| Certifique-se| Indica se existe uma variável. Defina esta propriedade como __presente__ para criar a variável de ambiente, se não existir ou certifique-se de que corresponde ao respetivo valor que é fornecido através de __valor__ propriedade se a variável já existe. Defina-o como __ausente__ para eliminar a variável, se existir.|
| Caminho| Define a variável de ambiente que está a ser configurada. Defina esta propriedade como __$true__ se a variável é o __caminho__ variável; caso contrário, defina-o como __$false__. A predefinição é __$false__. Se a variável que está a ser configurada é o __caminho__ variável, o valor fornecido através de __valor__ propriedade será anexada ao valor existente.|
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|
| Valor| O valor a atribuir à variável de ambiente.|

## <a name="example"></a>Exemplo

O exemplo seguinte garante que __TestEnvironmentVariable__ está presente e tem o valor __TestValue__. Se não estiver presente, criá-lo.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```