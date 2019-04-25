---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recursos de ambiente de DSC
ms.openlocfilehash: 2bc1600a9df32538d59efa712569b12fa9e3beee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077539"
---
# <a name="dsc-environment-resource"></a>Recursos de ambiente de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O __ambiente__ recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir as variáveis de ambiente de sistema.

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
| Certifique-se| Indica se existe uma variável. Definir esta propriedade para __presente__ para criar a variável de ambiente, se não existir ou para garantir que seu valor corresponde ao que é fornecido por meio do __valor__ propriedade se a variável já existe. Defina-o como __ausente__ para eliminar a variável, se existir.|
| Caminho| Define a variável de ambiente que está a ser configurada. Defina esta propriedade como __$true__ se a variável é o __caminho__ variável; caso contrário, defina-o como __$false__. A predefinição é __$false__. Se a variável a ser configurada é a __caminho__ variável, o valor fornecido por meio do __valor__ propriedade será anexada ao valor existente.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|
| Valor| O valor a atribuir à variável de ambiente.|

## <a name="example"></a>Exemplo

O exemplo seguinte garante que __TestEnvironmentVariable__ está presente e tem o valor __TestValue__. Se não estiver presente, ele o cria.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```