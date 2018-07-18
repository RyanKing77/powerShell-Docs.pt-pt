---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso Log de DSC
ms.openlocfilehash: fade94efd8133ae0172737e4bb1aed89fc0f97d9
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093481"
---
# <a name="dsc-log-resource"></a>Recurso Log de DSC

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

O __Log__ recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para escrever mensagens para o registo de eventos da Microsoft-Windows-Desired State Configuration / analítico.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> Por predefinição, apenas os registos operacionais para DSC estão ativados. Antes do registo de análise estar disponível ou visível, tem de estar ativada. Para obter mais informações, consulte [onde estão os registos de eventos de DSC?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs).

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| Mensagem| Indica a mensagem que deseja escrever no registo de eventos de configuração de estado de Microsoft-Windows-Desired/analítico.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes desta mensagem do registo é criada. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = '[ResourceType]ResourceName'`.|

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como incluir uma mensagem no log de eventos de configuração de estado de Microsoft-Windows-Desired/analítico.

> [!NOTE]
> Se executar [Test-dscconfiguration para](https://technet.microsoft.com/en-us/library/dn407382.aspx) com este recurso configurado, irá devolver sempre **$false**.

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```