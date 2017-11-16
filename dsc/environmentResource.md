---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recurso de ambiente de DSC
ms.openlocfilehash: 7c98798fa0e8fc865798ea30530e41ac87b2dadc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
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

