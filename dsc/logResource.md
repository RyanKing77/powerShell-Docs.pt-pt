---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos de registo DSC
ms.openlocfilehash: c7e1957540da2fd85a30f739e0f69bdb6975a4d8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219390"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="16041-103">Recursos de registo DSC</span><span class="sxs-lookup"><span data-stu-id="16041-103">DSC Log Resource</span></span>

> <span data-ttu-id="16041-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="16041-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="16041-105">O __registo__ recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para escrever mensagens no registo de eventos de configuração de estado Microsoft-Windows-Desired, registos analíticos.</span><span class="sxs-lookup"><span data-stu-id="16041-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

<span data-ttu-id="16041-106">Nota: Apenas os registos operacionais de DSC são ativados por predefinição.</span><span class="sxs-lookup"><span data-stu-id="16041-106">NOTE: By default only the Operational logs for DSC are enabled.</span></span>
<span data-ttu-id="16041-107">Antes do registo de análise será visível ou disponível, tem de estar ativada.</span><span class="sxs-lookup"><span data-stu-id="16041-107">Before the Analytic log will be available or visible, it must be enabled.</span></span>
<span data-ttu-id="16041-108">Consulte o seguinte artigo.</span><span class="sxs-lookup"><span data-stu-id="16041-108">See the following article.</span></span>

[<span data-ttu-id="16041-109">Onde estão os registos de eventos do DSC?</span><span class="sxs-lookup"><span data-stu-id="16041-109">Where are DSC Event Logs?</span></span>](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a><span data-ttu-id="16041-110">Propriedades</span><span class="sxs-lookup"><span data-stu-id="16041-110">Properties</span></span>
|  <span data-ttu-id="16041-111">Propriedade</span><span class="sxs-lookup"><span data-stu-id="16041-111">Property</span></span>  |  <span data-ttu-id="16041-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="16041-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="16041-113">Mensagem</span><span class="sxs-lookup"><span data-stu-id="16041-113">Message</span></span>| <span data-ttu-id="16041-114">Indica a mensagem que pretende escrever no registo de eventos de configuração de estado Microsoft-Windows-Desired, registos analíticos.</span><span class="sxs-lookup"><span data-stu-id="16041-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="16041-115">dependsOn</span><span class="sxs-lookup"><span data-stu-id="16041-115">DependsOn</span></span> | <span data-ttu-id="16041-116">Indica que a configuração de outro recurso tem de executar antes desta mensagem do registo obtém escrita.</span><span class="sxs-lookup"><span data-stu-id="16041-116">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="16041-117">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="16041-117">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="16041-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="16041-118">Example</span></span>

<span data-ttu-id="16041-119">O exemplo seguinte mostra como incluir uma mensagem no registo de eventos de configuração de estado Microsoft-Windows-Desired, registos analíticos.</span><span class="sxs-lookup"><span data-stu-id="16041-119">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> <span data-ttu-id="16041-120">**Tenha em atenção**: Se executar [teste DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) com este recurso configurado, será sempre devolver **$false**.</span><span class="sxs-lookup"><span data-stu-id="16041-120">**Note**: if you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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