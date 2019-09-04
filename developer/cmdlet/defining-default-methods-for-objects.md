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
# <a name="defining-default-methods-for-objects"></a>Defining Default Methods for Objects (Predefinir Métodos para Objetos)

Ao estender .NET Framework objetos, você pode adicionar métodos de código e métodos de script aos objetos.
O XML que é usado para definir esses métodos é descrito nas seções a seguir.

> [!NOTE]
> Os exemplos nas seções a seguir são do `Types.ps1xml` arquivo de tipos no diretório de instalação do Windows PowerShell (`$PSHOME`). Para obter mais informações, consulte [sobre tipos. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).

## <a name="code-methods"></a>Métodos de código

Um método de código faz referência a um método estático de um objeto .NET Framework.

No exemplo a seguir, o método **ToString** é adicionado ao tipo [System. xml. XMLNode](/dotnet/api/System.Xml.XmlNode) . O elemento [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) define o método estendido como um método de código. O elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) especifica o nome do método estendido. E, o elemento [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) especifica o método estático. Você também pode adicionar o elemento [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) aos membros do elemento [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .

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

## <a name="script-methods"></a>Métodos de script

Um método de script define um método cujo valor é a saída de um script. No exemplo a seguir, o método **ConvertToDateTime** é adicionado ao tipo [System. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) . O elemento [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) define o método estendido como um método de script. O elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) especifica o nome do método estendido. E o elemento [script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) especifica o script que gera o valor do método. Você também pode adicionar o elemento [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) aos membros do elemento [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .

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

## <a name="see-also"></a>Consulte também

[Escrevendo um cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
