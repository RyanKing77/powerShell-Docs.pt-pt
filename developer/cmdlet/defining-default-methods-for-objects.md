---
title: Definindo os métodos de padrão para objetos | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: af554cde5e888f2a008028010332caa473151622
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733974"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="20a84-102">Defining Default Methods for Objects (Predefinir Métodos para Objetos)</span><span class="sxs-lookup"><span data-stu-id="20a84-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="20a84-103">Quando expande objetos do .NET Framework, pode adicionar métodos de código e de script para os objetos.</span><span class="sxs-lookup"><span data-stu-id="20a84-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="20a84-104">O XML que é utilizado para definir esses métodos é descrito nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="20a84-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="20a84-105">Os exemplos nas seções a seguir são a partir do ficheiro de tipos de Types.ps1xml no diretório de instalação do Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="20a84-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="20a84-106">Métodos de código</span><span class="sxs-lookup"><span data-stu-id="20a84-106">Code Methods</span></span>

<span data-ttu-id="20a84-107">Um método de código faz referência a um método estático de um objeto do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="20a84-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="20a84-108">No exemplo a seguir, o **ConvertLargeIntegerToInt64** método é adicionado ao [System.Xml.Xmlnode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) tipo.</span><span class="sxs-lookup"><span data-stu-id="20a84-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="20a84-109">O [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) elemento define o método expandido como um método de código.</span><span class="sxs-lookup"><span data-stu-id="20a84-109">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="20a84-110">O [nome](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) elemento Especifica o nome do método expandido.</span><span class="sxs-lookup"><span data-stu-id="20a84-110">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="20a84-111">E, o [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) elemento Especifica o método estático.</span><span class="sxs-lookup"><span data-stu-id="20a84-111">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="20a84-112">(Também pode adicionar os [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) elemento aos membros do [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) elemento.)</span><span class="sxs-lookup"><span data-stu-id="20a84-112">(You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodemethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a><span data-ttu-id="20a84-113">Métodos de script</span><span class="sxs-lookup"><span data-stu-id="20a84-113">Script Methods</span></span>

<span data-ttu-id="20a84-114">Um método de script define um método cujo valor é a saída de um script.</span><span class="sxs-lookup"><span data-stu-id="20a84-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="20a84-115">No exemplo a seguir, o **ConvertToDateTime** método é adicionado ao [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) tipo.</span><span class="sxs-lookup"><span data-stu-id="20a84-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="20a84-116">O [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) elemento define o método expandido como um método de script.</span><span class="sxs-lookup"><span data-stu-id="20a84-116">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="20a84-117">O [nome](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) elemento Especifica o nome do método expandido.</span><span class="sxs-lookup"><span data-stu-id="20a84-117">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="20a84-118">E, o [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) elemento Especifica o script que gera o valor do método.</span><span class="sxs-lookup"><span data-stu-id="20a84-118">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="20a84-119">(Também pode adicionar os [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) elemento aos membros do [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) elemento.)</span><span class="sxs-lookup"><span data-stu-id="20a84-119">(You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="20a84-120">Veja Também</span><span class="sxs-lookup"><span data-stu-id="20a84-120">See Also</span></span>

[<span data-ttu-id="20a84-121">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="20a84-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
