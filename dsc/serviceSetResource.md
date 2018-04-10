---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos do DSC ServiceSet
ms.openlocfilehash: a7516120f0c4bc1c91031adc8aabf6a59b845246
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-serviceset-resource"></a>Recursos do DSC ServiceSet

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0


O **ServiceSet** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir serviços no nó de destino. Este recurso é um [recursos composto](authoringResourceComposite.md) que chama o [Service recursos](serviceResource.md) para cada serviço especificado no `Name` propriedade.

Utilize este recurso quando pretender configurar um número de serviços para o estado do mesmo.

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
| Nome| Indica os nomes de serviço. Tenha em atenção que, por vezes, isto é diferente dos nomes a apresentar. Pode obter uma lista de serviços e o respetivo estado atual com o [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.|
| StartupType| Indica o tipo de arranque para o serviço. Os valores que são permitidos para esta propriedade são: **automática**, **desativado**, e **Manual**|
| BuiltInAccount| Indica a conta de início de sessão a utilizar para os serviços. Os valores que são permitidos para esta propriedade são: **LocalService**, **LocalSystem**, e **NetworkService**.|
| Estado| Indica o estado pretender certificar-se para os serviços: **parado** ou **executar**.|
| Certifique-se| Indica se os serviços de existirem no sistema. Defina esta propriedade como **ausente** para se certificar de que os serviços não existe. Defini-la como **presente** (o valor predefinido) assegura que os serviços de destino existem.|
| credencial| Indica as credenciais para a conta que o recurso de serviço irá ser executado. Esta propriedade e o **BuiltinAccount** propriedade não pode ser utilizada em conjunto.|
| dependsOn| Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é *ResourceName* e o respetivo tipo é *ResourceType*, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|



## <a name="example"></a>Exemplo

A seguinte configuração de inicia os serviços de "Windows áudio" e "Serviços de ambiente de trabalho remoto".

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