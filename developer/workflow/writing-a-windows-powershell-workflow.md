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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847797"
---
# <a name="writing-a-windows-powershell-workflow"></a>Writing a Windows PowerShell Workflow (Escrever um Fluxo de Trabalho do Windows PowerShell)

Pode criar um fluxo de trabalho XAML ao adicionar atividades expostas por assemblies do Windows PowerShell para o designer de fluxo de trabalho no Visual Studio. As assemblagens seguintes do Windows PowerShell expõem atividades habilitados para fluxo de trabalho.

> [!IMPORTANT]
> Um fluxo de trabalho XAML deve ser empacotado como um módulo, se quiser fornecer ajuda para o fluxo de trabalho. Para obter informações sobre os módulos, consulte [escrever um módulo do Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities)

- [Microsoft.Powershell.Core.Activities](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [Microsoft.Powershell.Diagnostics.Activities](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [Microsoft.Powershell.Security.Activities](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [Microsoft.Powershell.Utility.Activities](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  Os tópicos seguintes descrevem como criar um fluxo de trabalho com atividades do Windows PowerShell.

- [Adição de atividades do Windows PowerShell para a caixa de ferramentas do Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [Criar um fluxo de trabalho com atividades do Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md)

- [A criação de um fluxo de trabalho usando um Script do Windows PowerShell](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [Importar e invocando um fluxo de trabalho do Windows PowerShell](./importing-and-invoking-a-windows-powershell-workflow.md)

- [Criar uma atividade de fluxo de trabalho a partir de um Cmdlet do Windows PowerShell](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)