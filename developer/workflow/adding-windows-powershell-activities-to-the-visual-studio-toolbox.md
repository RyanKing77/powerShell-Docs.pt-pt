---
title: Adição de atividades do Windows PowerShell para a caixa de ferramentas do Visual Studio | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56852109"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a><span data-ttu-id="bcd9f-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox (Adicionar Atividades do Windows PowerShell à Caixa de Ferramentas do Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="bcd9f-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>

<span data-ttu-id="bcd9f-103">Antes de criar um fluxo de trabalho do PowerShell usando o Designer de fluxo de trabalho, primeiro tem de adicionar as atividades do PowerShell para a caixa de ferramentas num projeto de aplicativo de console do fluxo de trabalho do Studio visuais.</span><span class="sxs-lookup"><span data-stu-id="bcd9f-103">Before you author a PowerShell Workflow using Workflow Designer, you must first add the PowerShell Activities to the Toolbox in a Visual Studio Workflow console application project.</span></span> <span data-ttu-id="bcd9f-104">O procedimento seguinte mostra como adicionar as atividades do Microsoft.PowerShell.Core.Activities assembly para a caixa de ferramentas do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bcd9f-104">The following procedure shows how to add the activities from the Microsoft.PowerShell.Core.Activities assembly to the Visual Studio toolbox.</span></span>

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a><span data-ttu-id="bcd9f-105">Adição de atividades do Windows PowerShell para a caixa de ferramentas</span><span class="sxs-lookup"><span data-stu-id="bcd9f-105">Adding Windows PowerShell Activities to the Toolbox</span></span>

1. <span data-ttu-id="bcd9f-106">Crie um novo projeto de aplicação de consola do fluxo de trabalho no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bcd9f-106">Create a new Workflow console application project in Visual Studio.</span></span>

2. <span data-ttu-id="bcd9f-107">Sobre o **View** menu, clique em **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="bcd9f-107">On the **View** menu, click **Toolbox**.</span></span>

3. <span data-ttu-id="bcd9f-108">Adicionar uma nova guia na caixa de ferramentas, clicar com o botão direito dentro da caixa de ferramentas e clique em **separador adicionar**e dê um nome, tais como "Atividades de PowerShell" ao novo separador.</span><span class="sxs-lookup"><span data-stu-id="bcd9f-108">Add a new tab in the Toolbox by right-clicking inside the Toolbox and clicking **Add Tab**, and give the new tab a name such as "PowerShell Activities".</span></span>

   <span data-ttu-id="bcd9f-109">Adicionar um separador permite-lhe agrupar as atividades do PowerShell separadas de outras ferramentas na caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="bcd9f-109">Adding a tab allows you to group the PowerShell Activities separate from other tools in the Toolbox.</span></span>

4. <span data-ttu-id="bcd9f-110">No separador da nova caixa de ferramentas, clique em **escolher itens...** . O **escolher itens da caixa de ferramentas** é apresentada a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="bcd9f-110">On the new Toolbox tab, click **Choose Items...**. The **Choose Toolbox Items** dialog appears.</span></span>

5. <span data-ttu-id="bcd9f-111">Na **escolher itens da caixa de ferramentas** caixa de diálogo, clique nas **System.Activities** separador.</span><span class="sxs-lookup"><span data-stu-id="bcd9f-111">In the **Choose Toolbox Items** dialog, click the **System.Activities** tab.</span></span>

6. <span data-ttu-id="bcd9f-112">Clique em **procurar**.</span><span class="sxs-lookup"><span data-stu-id="bcd9f-112">Click **Browse**.</span></span>

7. <span data-ttu-id="bcd9f-113">Navegue para a pasta de %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e e faça duplo clique Microsoft.PowerShell.Core.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="bcd9f-113">Navigate to the %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e folder and double-click Microsoft.PowerShell.Core.Activities.dll.</span></span>

8. <span data-ttu-id="bcd9f-114">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="bcd9f-114">Click **OK**.</span></span> <span data-ttu-id="bcd9f-115">As atividades definidas pelo Microsoft.PowerShell.Core.Activities assembly estão agora disponíveis na caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="bcd9f-115">The activities defined by the Microsoft.PowerShell.Core.Activities assembly are now available in the toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="bcd9f-116">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="bcd9f-116">See Also</span></span>

[<span data-ttu-id="bcd9f-117">Escrever um fluxo de trabalho do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bcd9f-117">Writing a Windows PowerShell Workflow</span></span>](./writing-a-windows-powershell-workflow.md)

[<span data-ttu-id="bcd9f-118">Criar um fluxo de trabalho com atividades do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bcd9f-118">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)