---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso de serviço de DSC
ms.openlocfilehash: 09571bd0eaa428e7d0bb7a533d6ad1c0c936e2cf
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048376"
---
# <a name="dsc-service-resource"></a>Recurso de serviço de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0


O **serviço** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir serviços no nó de destino.

## <a name="syntax"></a>Sintaxe

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| Nome| Indica o nome do serviço. Observe que, às vezes, isso é diferente do nome de exibição. Pode obter uma lista de serviços e o respetivo estado atual com o cmdlet Get-Service.|
| BuiltInAccount| Indica a conta de início de sessão para utilizar para o serviço. Os valores permitidos para esta propriedade são: **LocalService**, **LocalSystem**, e **NetworkService**.|
| Credencial| Indica as credenciais para a conta que o serviço será executado em. Esta propriedade e o __BuiltinAccount__ propriedade não pode ser utilizada em conjunto.|
| DependsOn| Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|
| Startuptype do| Indica o tipo de arranque para o serviço. Os valores permitidos para esta propriedade são: **Automática**, **desativada**, e **Manual**|
| Estado| Indica o estado que pretender certificar-se para o serviço.|
| Descrição | Indica a descrição do serviço de destino.|
| NomeaApresentar | Indica o nome a apresentar do serviço de destino.|
| Certifique-se | Indica se o serviço de destino existe no sistema. Defina esta propriedade como **ausente** para se certificar de que o serviço de destino não existe. Defini-la como **presente** (o valor predefinido) garante que o serviço de destino existe.|
| Caminho | Indique o caminho para o ficheiro binário para um novo serviço.|

## <a name="example"></a>Exemplo

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```