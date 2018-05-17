---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: DSC de Linux nxEnvironment recursos
ms.openlocfilehash: 3c9f39760e0fba7fac060f29f9e808a3a434401f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>DSC de Linux nxEnvironment recursos

O **nxEnvironment** recursos no PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir as variáveis de ambiente de sistema num nó de Linux.

## <a name="syntax"></a>Sintaxe

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Propriedades

|  Propriedade |  Descrição |
|---|---|
| Nome| Indica o nome da variável de ambiente para o qual pretende garantir um estado específico.|
| Valor| O valor a atribuir à variável de ambiente.|
| Certifique-se| Determina se deve verificar se existe a variável. Defina esta propriedade para "Presente" para garantir que existe a variável. Defina-o para "Ausente", certifique-se de que a variável não existe. O valor predefinido é "Presente".|
| Caminho| Define a variável de ambiente que está a ser configurada. Defina esta propriedade como **$true** se a variável é o **caminho** variável; caso contrário, defina-o como **$false**. A predefinição é **$false**. Se a variável que está a ser configurada é o **caminho** variável, o valor fornecido através de **valor** propriedade será anexada ao valor existente.|
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta a propriedade é `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Informações Adicionais

* Se **caminho** não existe ou defina para **$false**, variáveis de ambiente são geridas na `/etc/environment`. Os programas ou scripts poderão requerer configuração à origem de `/etc/environment` ficheiro para aceder as variáveis de ambiente gerido.
* Se **caminho** está definido como **$true**, a variável de ambiente é gerida no ficheiro `/etc/profile.d/DSCenvironment.sh`. Este ficheiro será criado se não existir. Se **Certifique-se** está definido para "Ausente" e **caminho** está definido como **$true**, uma variável de ambiente existente, apenas será removida do `/etc/profile.d/DSCenvironment.sh` e não a partir de outros ficheiros.

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como utilizar o **nxEnvironment** recursos para garantir que **TestEnvironmentVariable** está presente e tem o valor de "Teste-Value". Se **TestEnvironmentVariable** é não existir, será criado.

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```