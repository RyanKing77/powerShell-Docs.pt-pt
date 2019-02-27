---
title: Criar um fluxo de trabalho com o Windows PowerShell atividades | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 65d04c526ef7aa112da82adb924c0789731f3850
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845039"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="4cb73-102">Creating a Workflow with Windows PowerShell Activities (Criar um Fluxo de Trabalho com Atividades do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="4cb73-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="4cb73-103">Pode criar um fluxo de trabalho do Windows PowerShell ao selecionar a atividades do Visual Studio Toolbox e ao arrastá-los para a janela do estruturador de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4cb73-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="4cb73-104">Para obter informações sobre como adicionar atividades do Windows PowerShell para o Visual Studio Toolbox, consulte [adição de atividades do Windows PowerShell para o Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="4cb73-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="4cb73-105">Os procedimentos seguintes descrevem como criar um fluxo de trabalho que verifica o estado do domínio de um grupo de computadores especificadas pelo utilizador, associa-a um domínio, se já não estão associados e, em seguida, verifica o estado novamente.</span><span class="sxs-lookup"><span data-stu-id="4cb73-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="4cb73-106">Definindo o projeto</span><span class="sxs-lookup"><span data-stu-id="4cb73-106">Setting up the Project</span></span>

1. <span data-ttu-id="4cb73-107">Siga o procedimento descrito [adição de atividades do Windows PowerShell para o Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) para criar um projeto de fluxo de trabalho e adicionar as atividades a [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) e [ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies à caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="4cb73-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="4cb73-108">Adicione System.Management.Automation, Microsoft.PowerShell.Activities, gestão de sistemas, Microsoft.PowerShell.Management.Activities e Microsoft.PowerShell.Commands.Management como para o projeto como assemblies de referência.</span><span class="sxs-lookup"><span data-stu-id="4cb73-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="4cb73-109">Adicionar atividades ao fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4cb73-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="4cb73-110">Adicionar uma **sequência** atividade ao fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4cb73-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="4cb73-111">Criar um argumento com o nome `ComputerName` com um tipo de argumento do `String[]`.</span><span class="sxs-lookup"><span data-stu-id="4cb73-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="4cb73-112">Este argumento representa os nomes dos computadores para verificar e Junte-se.</span><span class="sxs-lookup"><span data-stu-id="4cb73-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="4cb73-113">Criar um argumento com o nome `DomainCred` typu [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="4cb73-113">Create an argument named `DomainCred` of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="4cb73-114">Este argumento representa as credenciais de domínio de uma conta de domínio que está autorizado para associar um computador ao domínio.</span><span class="sxs-lookup"><span data-stu-id="4cb73-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="4cb73-115">Criar um argumento com o nome `MachineCred` typu [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="4cb73-115">Create an argument named `MachineCred` of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="4cb73-116">Este argumento representa as credenciais de administrador nos computadores para verificar e Junte-se.</span><span class="sxs-lookup"><span data-stu-id="4cb73-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="4cb73-117">Adicionar uma **ParallelForEach** atividade dentro do **sequência** atividade.</span><span class="sxs-lookup"><span data-stu-id="4cb73-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="4cb73-118">Introduza `comp` e `ComputerName` em caixas de texto para que o loop faz a iteração pelos elementos do `ComputerName` matriz.</span><span class="sxs-lookup"><span data-stu-id="4cb73-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="4cb73-119">Adicionar uma **sequência** atividade ao corpo dos **ParallelForEach** atividade.</span><span class="sxs-lookup"><span data-stu-id="4cb73-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="4cb73-120">Definir o **DisplayName** propriedade da sequência para `JoinDomain`.</span><span class="sxs-lookup"><span data-stu-id="4cb73-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="4cb73-121">Adicionar uma **GetWmiObject** atividade para o **JoinDomain** sequência.</span><span class="sxs-lookup"><span data-stu-id="4cb73-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="4cb73-122">Editar as propriedades do **GetWmiObject** atividade da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="4cb73-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="4cb73-123">Propriedade</span><span class="sxs-lookup"><span data-stu-id="4cb73-123">Property</span></span>|<span data-ttu-id="4cb73-124">Valor</span><span class="sxs-lookup"><span data-stu-id="4cb73-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="4cb73-125">**Classe**</span><span class="sxs-lookup"><span data-stu-id="4cb73-125">**Class**</span></span>|<span data-ttu-id="4cb73-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="4cb73-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="4cb73-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="4cb73-127">**PSComputerName**</span></span>|<span data-ttu-id="4cb73-128">{comp}</span><span class="sxs-lookup"><span data-stu-id="4cb73-128">{comp}</span></span>|
   |<span data-ttu-id="4cb73-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="4cb73-129">**PSCredential**</span></span>|<span data-ttu-id="4cb73-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="4cb73-130">MachineCred</span></span>|

9. <span data-ttu-id="4cb73-131">Adicionar uma **AddComputer** atividade para o **JoinDomain** sequência após o **GetWmiObject** atividade.</span><span class="sxs-lookup"><span data-stu-id="4cb73-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="4cb73-132">Editar as propriedades do **AddComputer** atividade da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="4cb73-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="4cb73-133">Propriedade</span><span class="sxs-lookup"><span data-stu-id="4cb73-133">Property</span></span>|<span data-ttu-id="4cb73-134">Valor</span><span class="sxs-lookup"><span data-stu-id="4cb73-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="4cb73-135">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="4cb73-135">**ComputerName**</span></span>|<span data-ttu-id="4cb73-136">{comp}</span><span class="sxs-lookup"><span data-stu-id="4cb73-136">{comp}</span></span>|
    |<span data-ttu-id="4cb73-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="4cb73-137">**DomainCredential**</span></span>|<span data-ttu-id="4cb73-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="4cb73-138">DomainCred</span></span>|

11. <span data-ttu-id="4cb73-139">Adicionar uma **RestartComputer** atividade para o **JoinDomain** sequência após o **AddComputer** atividade.</span><span class="sxs-lookup"><span data-stu-id="4cb73-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="4cb73-140">Editar as propriedades do **RestartComputer** atividade da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="4cb73-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="4cb73-141">Propriedade</span><span class="sxs-lookup"><span data-stu-id="4cb73-141">Property</span></span>|<span data-ttu-id="4cb73-142">Valor</span><span class="sxs-lookup"><span data-stu-id="4cb73-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="4cb73-143">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="4cb73-143">**ComputerName**</span></span>|<span data-ttu-id="4cb73-144">{comp}</span><span class="sxs-lookup"><span data-stu-id="4cb73-144">{comp}</span></span>|
    |<span data-ttu-id="4cb73-145">**Credencial**</span><span class="sxs-lookup"><span data-stu-id="4cb73-145">**Credential**</span></span>|<span data-ttu-id="4cb73-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="4cb73-146">MachineCred</span></span>|
    |<span data-ttu-id="4cb73-147">**para**</span><span class="sxs-lookup"><span data-stu-id="4cb73-147">**For**</span></span>|<span data-ttu-id="4cb73-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span><span class="sxs-lookup"><span data-stu-id="4cb73-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="4cb73-149">**Force**</span><span class="sxs-lookup"><span data-stu-id="4cb73-149">**Force**</span></span>|<span data-ttu-id="4cb73-150">True</span><span class="sxs-lookup"><span data-stu-id="4cb73-150">True</span></span>|
    |<span data-ttu-id="4cb73-151">Aguarde</span><span class="sxs-lookup"><span data-stu-id="4cb73-151">Wait</span></span>|<span data-ttu-id="4cb73-152">True</span><span class="sxs-lookup"><span data-stu-id="4cb73-152">True</span></span>|
    |<span data-ttu-id="4cb73-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="4cb73-153">PSComputerName</span></span>|<span data-ttu-id="4cb73-154">{""}</span><span class="sxs-lookup"><span data-stu-id="4cb73-154">{""}</span></span>|

13. <span data-ttu-id="4cb73-155">Adicionar uma **GetWmiObject** atividade para o **JoinDomain** sequência após o **RestartComputer** atividade.</span><span class="sxs-lookup"><span data-stu-id="4cb73-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="4cb73-156">Editar as respetivas propriedades para ser o mesmo que a anterior **GetWmiObject** atividade.</span><span class="sxs-lookup"><span data-stu-id="4cb73-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="4cb73-157">Quando tiver concluído os procedimentos, a janela de design de fluxo de trabalho deve ser assim:</span><span class="sxs-lookup"><span data-stu-id="4cb73-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="4cb73-158">![JoinDomain XAML no designer de fluxo de trabalho](../media/joindomainworkflow.png)
    ![JoinDomain XAML no designer de fluxo de trabalho](../media/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="4cb73-158">![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span></span>