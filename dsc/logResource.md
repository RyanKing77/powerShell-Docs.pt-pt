---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos de registo DSC
ms.openlocfilehash: 72c9c5a9b8e2a4ed4ce43cfd792572ce95b502b3
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-log-resource"></a>Recursos de registo DSC 

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

O __registo__ recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para escrever mensagens no registo de eventos de configuração de estado Microsoft-Windows-Desired, registos analíticos.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

Nota: Apenas os registos operacionais de DSC são ativados por predefinição.
Antes do registo de análise será visível ou disponível, tem de estar ativada.
Consulte o seguinte artigo.

[Onde estão os registos de eventos do DSC?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a>Propriedades
|  Propriedade  |  Descrição   | 
|---|---| 
| Mensagem| Indica a mensagem que pretende escrever no registo de eventos de configuração de estado Microsoft-Windows-Desired, registos analíticos.| 
| dependsOn | Indica que a configuração de outro recurso tem de executar antes desta mensagem do registo obtém escrita. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como incluir uma mensagem no registo de eventos de configuração de estado Microsoft-Windows-Desired, registos analíticos.

> **Tenha em atenção**: Se executar [teste DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) com este recurso configurado, será sempre devolver **$false**.

```powershell 
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost

    {
        Log LogExample
        {
            Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
        }
    }
}
```

