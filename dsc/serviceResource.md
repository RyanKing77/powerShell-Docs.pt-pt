---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Recurso de serviço de DSC"
ms.openlocfilehash: 611729e5d971ebaf15ac947454cffadc6797927b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-service-resource"></a>Recurso de serviço de DSC

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0


O **serviço** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir serviços no nó de destino.

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
| Nome| Indica o nome do serviço. Tenha em atenção que, por vezes, isto é diferente do nome de apresentação. Pode obter uma lista de serviços e o respetivo estado atual com o cmdlet Get-Service.| 
| BuiltInAccount| Indica a conta de início de sessão a utilizar para o serviço. Os valores que são permitidos para esta propriedade são: **LocalService**, **LocalSystem**, e **NetworkService**.| 
| credencial| Indica as credenciais para a conta que o serviço irá ser executado. Esta propriedade e o __BuiltinAccount__ propriedade não pode ser utilizada em conjunto.| 
| dependsOn| Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.| 
| StartupType| Indica o tipo de arranque para o serviço. Os valores que são permitidos para esta propriedade são: **automática**, **desativado**, e **Manual**| 
| Estado| Indica o estado que pretender certificar-se para o serviço.| 
| Descrição | Indica a descrição do serviço de destino.| 
| NomeaApresentar | Indica o nome a apresentar do serviço de destino.| 
| Certifique-se | Indica se o serviço de destino existe no sistema. Defina esta propriedade como **ausente** para se certificar de que o serviço de destino não existe. Defini-la como **presente** (o valor predefinido) assegura que o serviço de destino existe.|
| Caminho | Indica o caminho para o ficheiro binário para um novo serviço.| 

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

