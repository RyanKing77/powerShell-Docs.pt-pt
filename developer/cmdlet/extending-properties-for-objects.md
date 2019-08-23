---
title: Estendendo propriedades para objetos | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 3b14007384cca0d0cfa35655aee437adf73b1ff0
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986485"
---
# <a name="extending-properties-for-objects"></a>Extending Properties for Objects (Expandir Propriedades para Objetos)

Ao estender .NET Framework objetos, você pode adicionar propriedades de alias, propriedades de código, propriedades de observação, propriedades de script e conjuntos de propriedades aos objetos. O XML que define essas propriedades é descrito nas seções a seguir.

> [!NOTE]
> Os exemplos nas seções a seguir são do arquivo de `Types.ps1xml` tipos padrão no diretório de instalação do PowerShell`$PSHOME`(). Para obter mais informações, consulte [sobre tipos. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).

## <a name="alias-properties"></a>Propriedades do alias

Uma propriedade de alias define um novo nome para uma propriedade existente.

No exemplo a seguir, a propriedade **Count** é adicionada ao tipo [System. array](/dotnet/api/System.Array) . O [](/dotnet/api/system.management.automation.psaliasproperty) elemento AliasProperty define a propriedade estendida como uma propriedade de alias. O elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) especifica o novo nome. E, o elemento [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) especifica a propriedade existente que é referenciada pelo alias. Você também pode adicionar o `AliasProperty` elemento aos membros do elemento [MemberSets](/dotnet/api/system.management.automation.psmemberset) .

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

## <a name="code-properties"></a>Propriedades do código

Uma propriedade de código faz referência a uma propriedade estática de um objeto .NET Framework.

No exemplo a seguir, a propriedade **Mode** é adicionada ao tipo [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) . O elemento [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) define a propriedade estendida como uma propriedade de código. O elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) especifica o nome da propriedade estendida. E, o elemento [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) define o método estático que é referenciado pela propriedade estendida. Você também pode adicionar o `CodeProperty` elemento aos membros do elemento [MemberSets](/dotnet/api/system.management.automation.psmemberset) .

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

## <a name="note-properties"></a>Propriedades da observação

Uma propriedade Note define uma propriedade que tem um valor estático.

No exemplo a seguir, a propriedade **status** , cujo valor é sempre **êxito**, é adicionada ao tipo [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) . O [](/dotnet/api/system.management.automation.psnoteproperty) elemento NoteProperty define a propriedade estendida como uma propriedade de observação. O elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) especifica o nome da propriedade estendida. O elemento [Value](/dotnet/api/system.management.automation.psnoteproperty.value) especifica o valor estático da propriedade estendida. O `NoteProperty` elemento também pode ser adicionado aos membros do elemento [MemberSets](/dotnet/api/system.management.automation.psmemberset) .

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

No exemplo a seguir, a propriedade **VERSIONINFO** é adicionada ao tipo [System. IO. FileInfo](/dotnet/api/System.IO.FileInfo) . O [](/dotnet/api/system.management.automation.psscriptproperty) elemento ScriptProperty define a propriedade estendida como uma propriedade de script. O elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) especifica o nome da propriedade estendida. E, o [](/dotnet/api/system.management.automation.psscriptproperty.getterscript) elemento getscriptblock especifica o script que gera o valor da propriedade. Você também pode adicionar o `ScriptProperty` elemento aos membros do elemento [MemberSets](/dotnet/api/system.management.automation.psmemberset) .

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

Um conjunto de propriedades define um grupo de propriedades estendidas que podem ser referenciadas pelo nome do conjunto.
Por exemplo, o parâmetro de**Propriedade** [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
pode especificar um conjunto de propriedades específico a ser exibido. Quando um conjunto de propriedades é especificado, somente as propriedades que pertencem ao conjunto são exibidas.

Não há restrição quanto ao número de conjuntos de propriedades que podem ser definidos para um objeto. No entanto, os conjuntos de propriedades usados para definir as propriedades de exibição padrão de um objeto devem ser especificados dentro do conjunto de membros **PSStandardMembers** . No arquivoTypes, os nomes do conjunto de propriedades padrão incluem DefaultDisplayProperty, DefaultDisplayPropertySet e DefaultKeyPropertySet. `Types.ps1xml` Todos os conjuntos de propriedades adicionais que você adicionar ao conjunto de membros **PSStandardMembers** serão ignorados.

No exemplo a seguir, o conjunto de propriedades **DefaultDisplayPropertySet** é adicionado ao conjunto de membros **PSStandardMembers** do tipo [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) . O [](/dotnet/api/system.management.automation.pspropertyset) elemento PropertySet define o grupo de propriedades. O elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) especifica o nome do conjunto de propriedades. E, o [](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) elemento referenciaproperties especifica as propriedades do conjunto. Você também pode adicionar o `PropertySet` elemento aos membros do elemento [Type](/dotnet/api/system.management.automation.pstypename) .

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

## <a name="see-also"></a>Consulte também

[Sobre os tipos. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[System. Management. Automation](/dotnet/api/System.Management.Automation)

[Escrevendo um cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
