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
ms.openlocfilehash: be31d03b02394cb1694909cf7b65bbc2a29f6976
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795441"
---
# <a name="extending-properties-for-objects"></a>Extending Properties for Objects (Expandir Propriedades para Objetos)

Quando expande objetos do .NET Framework, pode adicionar alias propriedades, propriedades de código, propriedades de observação, propriedades de script e conjuntos de propriedades para os objetos. O XML que é utilizado para definir essas propriedades é descrito nas seções a seguir.

> [!NOTE]
> Os exemplos nas seções a seguir são a partir do ficheiro de tipos de Types.ps1xml padrão no diretório de instalação do Windows PowerShell (`$pshome`).

## <a name="alias-properties"></a>Propriedades de alias

Uma propriedade de alias define um novo nome para uma propriedade existente.

No exemplo a seguir, o `Count` propriedade é adicionada ao [System. Array? Displayproperty = Fullname](/dotnet/api/System.Array) tipo. O [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) elemento define a propriedade estendida como uma propriedade de alias. O [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento Especifica o novo nome. E, o [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) elemento Especifica a propriedade existente que é referenciada pelo alias. (Também pode adicionar os [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) elemento aos membros do [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)

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

## <a name="code-properties"></a>Propriedades de código

Uma propriedade de código faz referência a uma propriedade estática de um objeto do .NET Framework.

No exemplo a seguir, o `Node` propriedade é adicionada ao [System.IO.Directoryinfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) tipo. O [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) elemento define a propriedade estendida como uma propriedade de código. O [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento Especifica o nome da propriedade expandida. E, o [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) elemento define o método estático que é referenciado pela propriedade expandida. (Também pode adicionar os [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) elemento aos membros do [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)

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

## <a name="note-properties"></a>Propriedades de observação

Uma propriedade de nota define uma propriedade que tem um valor estático.

No exemplo a seguir, o `Status` propriedade (cujo valor é sempre "Êxito") é adicionada ao [System.IO.Directoryinfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) tipo. O [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) elemento define a propriedade estendida como uma propriedade de observação; o [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento Especifica o nome da propriedade expandida; e o [valor](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) elemento Especifica o valor estático da propriedade expandida. (A [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) elemento também pode ser adicionado aos membros do [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)

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

## <a name="script-properties"></a>Propriedades do script

Uma propriedade de script define uma propriedade cujo valor é a saída de um script.

No exemplo a seguir, o `VersionInfo` propriedade é adicionada ao [FILEINFO? Displayproperty = Fullname](/dotnet/api/System.IO.FileInfo) tipo. O [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) elemento define a propriedade estendida como uma propriedade de script. O [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento Especifica o nome da propriedade expandida. E, o [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) elemento Especifica o script que gera o valor da propriedade. (Também pode adicionar os [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) elemento aos membros do [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)

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

## <a name="property-sets"></a>Conjuntos de propriedades

Um conjunto de propriedade define um grupo de propriedades expandidas, que pode ser referenciado pelo nome do conjunto. Por exemplo, o `Property` parâmetro do [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet pode especificar uma propriedade específica, defina a apresentar. Quando é especificado um conjunto de propriedade, são apresentadas apenas as propriedades que pertencem ao conjunto.

Não existe nenhuma restrição no número de conjuntos de propriedades que podem ser definidos para um objeto. No entanto, tem de especificar os conjuntos de propriedade utilizados para definir as propriedades de exibição padrão de um objeto dentro do conjunto de membro PSStandardMembers. No arquivo Types.ps1xml tipos, os nomes de conjunto de propriedades padrão incluem DefaultDisplayProperty DefaultDisplayPropertySet e DefaultKeyPropertySet. Todos os conjuntos de propriedade adicionais que adicionar ao conjunto de membro PSStandardMembers são ignorados.

No exemplo a seguir, o conjunto de propriedade DefaultDisplayPropertySet é adicionado ao conjunto de membro PSStandardMembers do [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) tipo. O [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) elemento define o grupo de propriedades. O [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento Especifica o nome do conjunto de propriedade. E, o [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) elemento Especifica as propriedades do conjunto. (Também pode adicionar os [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) elemento aos membros do [tipo](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) elemento.)

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

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
