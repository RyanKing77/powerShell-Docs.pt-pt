---
title: Definindo métodos padrão para objetos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: 346a194c6b4c81aa61a6331cdb62ae380a17bb1e
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215287"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="987b8-102">Defining Default Methods for Objects (Predefinir Métodos para Objetos)</span><span class="sxs-lookup"><span data-stu-id="987b8-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="987b8-103">Ao estender .NET Framework objetos, você pode adicionar métodos de código e métodos de script aos objetos.</span><span class="sxs-lookup"><span data-stu-id="987b8-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span>
<span data-ttu-id="987b8-104">O XML que é usado para definir esses métodos é descrito nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="987b8-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="987b8-105">Os exemplos nas seções a seguir são do `Types.ps1xml` arquivo de tipos no diretório de instalação do Windows PowerShell (`$PSHOME`).</span><span class="sxs-lookup"><span data-stu-id="987b8-105">The examples in the following sections are from the `Types.ps1xml` types file in the Windows PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="987b8-106">Para obter mais informações, consulte [sobre tipos. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="987b8-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="code-methods"></a><span data-ttu-id="987b8-107">Métodos de código</span><span class="sxs-lookup"><span data-stu-id="987b8-107">Code methods</span></span>

<span data-ttu-id="987b8-108">Um método de código faz referência a um método estático de um objeto .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="987b8-108">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="987b8-109">No exemplo a seguir, o método **ToString** é adicionado ao tipo [System. xml. XMLNode](/dotnet/api/System.Xml.XmlNode) .</span><span class="sxs-lookup"><span data-stu-id="987b8-109">In the following example, the **ToString** method is added to the [System.Xml.XmlNode](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="987b8-110">O elemento [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) define o método estendido como um método de código.</span><span class="sxs-lookup"><span data-stu-id="987b8-110">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="987b8-111">O elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) especifica o nome do método estendido.</span><span class="sxs-lookup"><span data-stu-id="987b8-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="987b8-112">E, o elemento [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) especifica o método estático.</span><span class="sxs-lookup"><span data-stu-id="987b8-112">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="987b8-113">Você também pode adicionar o elemento [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) aos membros do elemento [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .</span><span class="sxs-lookup"><span data-stu-id="987b8-113">You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodeMethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a><span data-ttu-id="987b8-114">Métodos de script</span><span class="sxs-lookup"><span data-stu-id="987b8-114">Script methods</span></span>

<span data-ttu-id="987b8-115">Um método de script define um método cujo valor é a saída de um script.</span><span class="sxs-lookup"><span data-stu-id="987b8-115">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="987b8-116">No exemplo a seguir, o método **ConvertToDateTime** é adicionado ao tipo [System. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) .</span><span class="sxs-lookup"><span data-stu-id="987b8-116">In the following example, the **ConvertToDateTime** method is added to the [System.Management.ManagementObject](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="987b8-117">O elemento [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) define o método estendido como um método de script.</span><span class="sxs-lookup"><span data-stu-id="987b8-117">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="987b8-118">O elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) especifica o nome do método estendido.</span><span class="sxs-lookup"><span data-stu-id="987b8-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="987b8-119">E o elemento [script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) especifica o script que gera o valor do método.</span><span class="sxs-lookup"><span data-stu-id="987b8-119">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="987b8-120">Você também pode adicionar o elemento [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) aos membros do elemento [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .</span><span class="sxs-lookup"><span data-stu-id="987b8-120">You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

```xml
<Type>
  <Name>System.Management.ManagementObject</Name>
  <Members>
    <ScriptMethod>
      <Name>ConvertToDateTime</Name>
      <Script>
        [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
      </Script>
    </ScriptMethod>
  </Members>
</Type>
```

## <a name="see-also"></a><span data-ttu-id="987b8-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="987b8-121">See also</span></span>

[<span data-ttu-id="987b8-122">Escrevendo um cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="987b8-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
