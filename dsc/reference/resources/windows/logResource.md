---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso Log de DSC
ms.openlocfilehash: 1f94a2d847a4ef63f81e2fb83d1a0f76f5677b09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077233"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="1eacf-103">Recurso Log de DSC</span><span class="sxs-lookup"><span data-stu-id="1eacf-103">DSC Log Resource</span></span>

> <span data-ttu-id="1eacf-104">_Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="1eacf-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="1eacf-105">O __Log__ recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para escrever mensagens para o registo de eventos da Microsoft-Windows-Desired State Configuration / analítico.</span><span class="sxs-lookup"><span data-stu-id="1eacf-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="1eacf-106">Por predefinição, apenas os registos operacionais para DSC estão ativados.</span><span class="sxs-lookup"><span data-stu-id="1eacf-106">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="1eacf-107">Antes do registo de análise estar disponível ou visível, tem de estar ativada.</span><span class="sxs-lookup"><span data-stu-id="1eacf-107">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="1eacf-108">Para obter mais informações, consulte [onde estão os registos de eventos de DSC?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="1eacf-108">For more information, see [Where are DSC Event Logs?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="1eacf-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="1eacf-109">Properties</span></span>

| <span data-ttu-id="1eacf-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="1eacf-110">Property</span></span> | <span data-ttu-id="1eacf-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="1eacf-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="1eacf-112">Mensagem</span><span class="sxs-lookup"><span data-stu-id="1eacf-112">Message</span></span>| <span data-ttu-id="1eacf-113">Indica a mensagem que deseja escrever no registo de eventos de configuração de estado de Microsoft-Windows-Desired/analítico.</span><span class="sxs-lookup"><span data-stu-id="1eacf-113">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="1eacf-114">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1eacf-114">DependsOn</span></span> | <span data-ttu-id="1eacf-115">Indica que a configuração de outro recurso deve ser executado antes desta mensagem do registo é criada.</span><span class="sxs-lookup"><span data-stu-id="1eacf-115">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="1eacf-116">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será **ResourceName** e seu tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="1eacf-116">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="1eacf-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1eacf-117">Example</span></span>

<span data-ttu-id="1eacf-118">O exemplo seguinte mostra como incluir uma mensagem no log de eventos de configuração de estado de Microsoft-Windows-Desired/analítico.</span><span class="sxs-lookup"><span data-stu-id="1eacf-118">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="1eacf-119">Se executar [Test-dscconfiguration para](https://technet.microsoft.com/en-us/library/dn407382.aspx) com este recurso configurado, irá devolver sempre **$false**.</span><span class="sxs-lookup"><span data-stu-id="1eacf-119">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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
