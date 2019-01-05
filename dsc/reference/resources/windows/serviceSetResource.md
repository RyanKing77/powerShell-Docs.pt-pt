---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso ServiceSet de DSC
ms.openlocfilehash: 5694c2abc5c0caf0098670b629af464b35125583
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048387"
---
# <a name="dsc-serviceset-resource"></a>Recurso ServiceSet de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O **ServiceSet** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir serviços no nó de destino. Este recurso é um [recursos compostos](../../../resources/authoringResourceComposite.md) que chama o [recursos de serviço](serviceResource.md) para cada serviço especificado no `Name` propriedade.

Utilize este recurso quando pretender configurar um número de serviços para o mesmo Estado.

## <a name="syntax"></a>Sintaxe

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| Nome| Indica os nomes de serviço. Tenha em atenção que, às vezes, isso é diferente dos nomes a apresentar. Pode obter uma lista de serviços e o respetivo estado atual com o [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.|
| Startuptype do| Indica o tipo de arranque para o serviço. Os valores permitidos para esta propriedade são: **Automática**, **desativada**, e **Manual**|
| BuiltInAccount| Indica a conta de início de sessão para utilizar para os serviços. Os valores permitidos para esta propriedade são: **LocalService**, **LocalSystem**, e **NetworkService**.|
| Estado| Indica o estado a que se pretender certificar-se para os serviços: **Parado** ou **em execução**.|
| Certifique-se| Indica se os serviços existem no sistema. Defina esta propriedade como **ausente** para garantir que os serviços não existem. Defini-la como **presente** (o valor predefinido) garante que os serviços de destino existem.|
| Credencial| Indica as credenciais para a conta que o recurso de serviço será executado no. Esta propriedade e o **BuiltinAccount** propriedade não pode ser utilizada em conjunto.|
| DependsOn| Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será *ResourceName* e seu tipo é *ResourceType*, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|



## <a name="example"></a>Exemplo

A seguinte configuração inicia os serviços "Áudio do Windows" e "Serviços de ambiente de trabalho remoto".

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```
