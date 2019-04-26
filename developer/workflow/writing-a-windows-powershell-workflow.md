---
title: Escrever um fluxo de trabalho do Windows PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 4f0be193fb5b5c753d040a48e5f49235ece11708
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080327"
---
# <a name="writing-a-windows-powershell-workflow"></a><span data-ttu-id="08955-102">Writing a Windows PowerShell Workflow (Escrever um Fluxo de Trabalho do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="08955-102">Writing a Windows PowerShell Workflow</span></span>

<span data-ttu-id="08955-103">Pode criar um fluxo de trabalho XAML ao adicionar atividades expostas por assemblies do Windows PowerShell para o designer de fluxo de trabalho no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="08955-103">You can create a XAML workflow by adding activities exposed by Windows PowerShell assemblies to the Workflow designer in Visual Studio.</span></span> <span data-ttu-id="08955-104">As assemblagens seguintes do Windows PowerShell expõem atividades habilitados para fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="08955-104">The following Windows PowerShell assemblies expose workflow-enabled activities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="08955-105">Um fluxo de trabalho XAML deve ser empacotado como um módulo, se quiser fornecer ajuda para o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="08955-105">A XAML workflow must be packaged as a module if you want to provide help for the workflow.</span></span> <span data-ttu-id="08955-106">Para obter informações sobre os módulos, consulte [escrever um módulo do Windows PowerShell](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="08955-106">For information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- [<span data-ttu-id="08955-107">Microsoft.Powershell.Activities</span><span class="sxs-lookup"><span data-stu-id="08955-107">Microsoft.Powershell.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Activities)

- [<span data-ttu-id="08955-108">Microsoft.Powershell.Core.Activities</span><span class="sxs-lookup"><span data-stu-id="08955-108">Microsoft.Powershell.Core.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [<span data-ttu-id="08955-109">Microsoft.Powershell.Diagnostics.Activities</span><span class="sxs-lookup"><span data-stu-id="08955-109">Microsoft.Powershell.Diagnostics.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [<span data-ttu-id="08955-110">Microsoft.Powershell.Management.Activities</span><span class="sxs-lookup"><span data-stu-id="08955-110">Microsoft.Powershell.Management.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [<span data-ttu-id="08955-111">Microsoft.Powershell.Security.Activities</span><span class="sxs-lookup"><span data-stu-id="08955-111">Microsoft.Powershell.Security.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [<span data-ttu-id="08955-112">Microsoft.Powershell.Utility.Activities</span><span class="sxs-lookup"><span data-stu-id="08955-112">Microsoft.Powershell.Utility.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  <span data-ttu-id="08955-113">Os tópicos seguintes descrevem como criar um fluxo de trabalho com atividades do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="08955-113">The following topics describe how to create a Workflow by using Windows PowerShell activities.</span></span>

- [<span data-ttu-id="08955-114">Adição de atividades do Windows PowerShell para a caixa de ferramentas do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="08955-114">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [<span data-ttu-id="08955-115">Criar um fluxo de trabalho com atividades do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="08955-115">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)

- [<span data-ttu-id="08955-116">A criação de um fluxo de trabalho usando um Script do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="08955-116">Creating a Workflow by Using a Windows PowerShell Script</span></span>](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [<span data-ttu-id="08955-117">Importar e invocando um fluxo de trabalho do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="08955-117">Importing and Invoking a Windows PowerShell Workflow</span></span>](./importing-and-invoking-a-windows-powershell-workflow.md)

- [<span data-ttu-id="08955-118">Criar uma atividade de fluxo de trabalho a partir de um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="08955-118">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)