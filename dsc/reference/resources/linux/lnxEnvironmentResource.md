---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: DSC para Linux nxEnvironment recursos
ms.openlocfilehash: 763ec560faa6adaf42aef3c21c9045be95f780bc
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048853"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>DSC para Linux nxEnvironment recursos

O **nxEnvironment** recursos no PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir as variáveis de ambiente de sistema num nó de Linux.

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
| Certifique-se| Determina se deve verificar se a variável existe. Defina esta propriedade para "Presente" para garantir que a variável existe. Defini-lo como "Ausente", certifique-se de que a variável não existe. O valor predefinido é "Presente".|
| Caminho| Define a variável de ambiente que está a ser configurada. Defina esta propriedade como **$true** se a variável é o **caminho** variável; caso contrário, defina-o como **$false**. A predefinição é **$false**. Se a variável a ser configurada é a **caminho** variável, o valor fornecido por meio do **valor** propriedade será anexada ao valor existente.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e seu tipo é **ResourceType**, a sintaxe para usar isso a propriedade é `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Informações Adicionais

* Se **caminho** é não existe ou definido como **$false**, as variáveis de ambiente são gerenciadas no `/etc/environment`. Seus programas ou scripts poderão exigir configuração para origem a `/etc/environment` ficheiros para aceder as variáveis de ambiente gerenciado.
* Se **caminho** está definida como **$true**, a variável de ambiente é gerenciada no ficheiro `/etc/profile.d/DSCenvironment.sh`. Esse arquivo será criado se não existir. Se **Certifique-se** está definido para "Ausente" e **caminho** está definida como **$true**, uma variável de ambiente existente, apenas será removida do `/etc/profile.d/DSCenvironment.sh` e não a partir de outros ficheiros.

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como utilizar o **nxEnvironment** recurso para se certificar de que **TestEnvironmentVariable** está presente e tem o valor "Valor de teste". Se **TestEnvironmentVariable** é não existir, será criada.

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```