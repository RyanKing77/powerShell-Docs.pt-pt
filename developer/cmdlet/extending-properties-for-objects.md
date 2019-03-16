---
title: Estendendo as propriedades de objetos | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 496e363b041194563d46c09eee67a12055bb54b0
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057302"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="549ea-102">Extending Properties for Objects (Expandir Propriedades para Objetos)</span><span class="sxs-lookup"><span data-stu-id="549ea-102">Extending Properties for Objects</span></span>

<span data-ttu-id="549ea-103">Quando expande objetos do .NET Framework, pode adicionar alias propriedades, propriedades de código, propriedades de observação, propriedades de script e conjuntos de propriedades para os objetos.</span><span class="sxs-lookup"><span data-stu-id="549ea-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="549ea-104">O XML que é utilizado para definir essas propriedades é descrito nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="549ea-104">The XML that is used to define these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="549ea-105">Os exemplos nas seções a seguir são a partir do ficheiro de tipos de Types.ps1xml padrão no diretório de instalação do Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="549ea-105">The examples in the following sections are from the default Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="549ea-106">Propriedades de alias</span><span class="sxs-lookup"><span data-stu-id="549ea-106">Alias Properties</span></span>

<span data-ttu-id="549ea-107">Uma propriedade de alias define um novo nome para uma propriedade existente.</span><span class="sxs-lookup"><span data-stu-id="549ea-107">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="549ea-108">No exemplo a seguir, o `Count` propriedade é adicionada ao [System. Array? Displayproperty = Fullname](/dotnet/api/System.Array) tipo.</span><span class="sxs-lookup"><span data-stu-id="549ea-108">In the following example, the `Count` property is added to the [System.Array?Displayproperty=Fullname](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="549ea-109">O [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) elemento define a propriedade estendida como uma propriedade de alias.</span><span class="sxs-lookup"><span data-stu-id="549ea-109">The [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) element defines the extended property as an alias property.</span></span> <span data-ttu-id="549ea-110">O [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento Especifica o novo nome.</span><span class="sxs-lookup"><span data-stu-id="549ea-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the new name.</span></span> <span data-ttu-id="549ea-111">E, o [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) elemento Especifica a propriedade existente que é referenciada pelo alias.</span><span class="sxs-lookup"><span data-stu-id="549ea-111">And, the [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="549ea-112">(Também pode adicionar os [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) elemento aos membros do [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)</span><span class="sxs-lookup"><span data-stu-id="549ea-112">(You can also add the [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

## <a name="code-properties"></a><span data-ttu-id="549ea-113">Propriedades de código</span><span class="sxs-lookup"><span data-stu-id="549ea-113">Code Properties</span></span>

<span data-ttu-id="549ea-114">Uma propriedade de código faz referência a uma propriedade estática de um objeto do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="549ea-114">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="549ea-115">No exemplo a seguir, o `Node` propriedade é adicionada ao [System.IO.Directoryinfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) tipo.</span><span class="sxs-lookup"><span data-stu-id="549ea-115">In the following example, the `Node` property is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="549ea-116">O [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) elemento define a propriedade estendida como uma propriedade de código.</span><span class="sxs-lookup"><span data-stu-id="549ea-116">The [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element defines the extended property as a code property.</span></span> <span data-ttu-id="549ea-117">O [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento Especifica o nome da propriedade expandida.</span><span class="sxs-lookup"><span data-stu-id="549ea-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="549ea-118">E, o [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) elemento define o método estático que é referenciado pela propriedade expandida.</span><span class="sxs-lookup"><span data-stu-id="549ea-118">And, the [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="549ea-119">(Também pode adicionar os [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) elemento aos membros do [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)</span><span class="sxs-lookup"><span data-stu-id="549ea-119">(You can also add the [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>Microsoft.PowerShell.Commands.FileSystemProvider</TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

## <a name="note-properties"></a><span data-ttu-id="549ea-120">Propriedades de observação</span><span class="sxs-lookup"><span data-stu-id="549ea-120">Note Properties</span></span>

<span data-ttu-id="549ea-121">Uma propriedade de nota define uma propriedade que tem um valor estático.</span><span class="sxs-lookup"><span data-stu-id="549ea-121">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="549ea-122">No exemplo a seguir, o `Status` propriedade (cujo valor é sempre "Êxito") é adicionada ao [System.IO.Directoryinfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) tipo.</span><span class="sxs-lookup"><span data-stu-id="549ea-122">In the following example, the `Status` property (whose value is always "Success") is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="549ea-123">O [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) elemento define a propriedade estendida como uma propriedade de observação; o [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento Especifica o nome da propriedade expandida; e o [valor](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) elemento Especifica o valor estático da propriedade expandida.</span><span class="sxs-lookup"><span data-stu-id="549ea-123">The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element defines the extended property as a note property; the [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property; and the [Value](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the static value of the extended property.</span></span> <span data-ttu-id="549ea-124">(A [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) elemento também pode ser adicionado aos membros do [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)</span><span class="sxs-lookup"><span data-stu-id="549ea-124">(The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element can also be added to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

## <a name="script-properties"></a><span data-ttu-id="549ea-125">Propriedades do script</span><span class="sxs-lookup"><span data-stu-id="549ea-125">Script Properties</span></span>

<span data-ttu-id="549ea-126">Uma propriedade de script define uma propriedade cujo valor é a saída de um script.</span><span class="sxs-lookup"><span data-stu-id="549ea-126">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="549ea-127">No exemplo a seguir, o `VersionInfo` propriedade é adicionada ao [FILEINFO? Displayproperty = Fullname](/dotnet/api/System.IO.FileInfo) tipo.</span><span class="sxs-lookup"><span data-stu-id="549ea-127">In the following example, the `VersionInfo` property is added to the [System.IO.FileInfo?Displayproperty=Fullname](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="549ea-128">O [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) elemento define a propriedade estendida como uma propriedade de script.</span><span class="sxs-lookup"><span data-stu-id="549ea-128">The [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element defines the extended property as a script property.</span></span> <span data-ttu-id="549ea-129">O [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento Especifica o nome da propriedade expandida.</span><span class="sxs-lookup"><span data-stu-id="549ea-129">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="549ea-130">E, o [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) elemento Especifica o script que gera o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="549ea-130">And, the [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the script that generates the property value.</span></span> <span data-ttu-id="549ea-131">(Também pode adicionar os [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) elemento aos membros do [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)</span><span class="sxs-lookup"><span data-stu-id="549ea-131">(You can also add the [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
        [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

## <a name="property-sets"></a><span data-ttu-id="549ea-132">Conjuntos de propriedades</span><span class="sxs-lookup"><span data-stu-id="549ea-132">Property Sets</span></span>

<span data-ttu-id="549ea-133">Um conjunto de propriedade define um grupo de propriedades expandidas, que pode ser referenciado pelo nome do conjunto.</span><span class="sxs-lookup"><span data-stu-id="549ea-133">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span> <span data-ttu-id="549ea-134">Por exemplo, o `Property` parâmetro do [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet pode especificar uma propriedade específica, defina a apresentar.</span><span class="sxs-lookup"><span data-stu-id="549ea-134">For example, the `Property` parameter of the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet can specify a specific property set to be displayed.</span></span> <span data-ttu-id="549ea-135">Quando é especificado um conjunto de propriedade, são apresentadas apenas as propriedades que pertencem ao conjunto.</span><span class="sxs-lookup"><span data-stu-id="549ea-135">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="549ea-136">Não existe nenhuma restrição no número de conjuntos de propriedades que podem ser definidos para um objeto.</span><span class="sxs-lookup"><span data-stu-id="549ea-136">There is no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="549ea-137">No entanto, tem de especificar os conjuntos de propriedade utilizados para definir as propriedades de exibição padrão de um objeto dentro do conjunto de membro PSStandardMembers.</span><span class="sxs-lookup"><span data-stu-id="549ea-137">However, the property sets used to define the default display properties of an object must be specified within the PSStandardMembers member set.</span></span> <span data-ttu-id="549ea-138">No arquivo Types.ps1xml tipos, os nomes de conjunto de propriedades padrão incluem DefaultDisplayProperty DefaultDisplayPropertySet e DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="549ea-138">In the Types.ps1xml types file, the default property set names include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="549ea-139">Todos os conjuntos de propriedade adicionais que adicionar ao conjunto de membro PSStandardMembers são ignorados.</span><span class="sxs-lookup"><span data-stu-id="549ea-139">Any additional property sets that you add to the PSStandardMembers member set are ignored.</span></span>

<span data-ttu-id="549ea-140">No exemplo a seguir, o conjunto de propriedade DefaultDisplayPropertySet é adicionado ao conjunto de membro PSStandardMembers do [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) tipo.</span><span class="sxs-lookup"><span data-stu-id="549ea-140">In the following example, the DefaultDisplayPropertySet property set is added to the PSStandardMembers member set of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="549ea-141">O [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) elemento define o grupo de propriedades.</span><span class="sxs-lookup"><span data-stu-id="549ea-141">The [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element defines the group of properties.</span></span> <span data-ttu-id="549ea-142">O [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento Especifica o nome do conjunto de propriedade.</span><span class="sxs-lookup"><span data-stu-id="549ea-142">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the property set.</span></span> <span data-ttu-id="549ea-143">E, o [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) elemento Especifica as propriedades do conjunto.</span><span class="sxs-lookup"><span data-stu-id="549ea-143">And, the [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) element specifies the properties of the set.</span></span> <span data-ttu-id="549ea-144">(Também pode adicionar os [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) elemento aos membros do [tipo](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) elemento.)</span><span class="sxs-lookup"><span data-stu-id="549ea-144">(You can also add the [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element to the members of the [Type](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) element.)</span></span>

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
           <Name>DefaultDisplayPropertySet</Name>
           <ReferencedProperties>
            <Name>Status</Name
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

## <a name="see-also"></a><span data-ttu-id="549ea-145">Veja Também</span><span class="sxs-lookup"><span data-stu-id="549ea-145">See Also</span></span>

[<span data-ttu-id="549ea-146">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="549ea-146">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
