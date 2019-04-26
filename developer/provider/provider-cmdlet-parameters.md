---
title: Parâmetros de cmdlet do fornecedor | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d09eaa-924f-4e2b-adfb-14bb729090dd
caps.latest.revision: 8
ms.openlocfilehash: ad7f9737c646dd5cea5abb14b828236e40feac5a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081143"
---
# <a name="provider-cmdlet-parameters"></a>Provider cmdlet parameters (Parâmetros de cmdlets de fornecedores)

Cmdlets do fornecedor são fornecidos com um conjunto de parâmetros estáticos que estão disponíveis para todos os fornecedores que suportam o cmdlet, bem como dinâmicos parâmetros que são adicionados quando o usuário Especifica um determinado valor para determinados parâmetros estáticos do cmdlet fornecedor.

## <a name="provider-cmdlet-static-parameters"></a>Parâmetros de Cmdlet estática do fornecedor

Parâmetros estáticos são definidos pelo Windows PowerShell. Um grande conjunto destes parâmetros é implementado pelo Windows PowerShell para proporcionar consistência entre todos os fornecedores e para fornecer uma experiência de desenvolvimento mais simples. Exemplos desses parâmetros incluem o `literalPath`, `exclude`, e `include` parâmetros do `Get-Item` cmdlet. Um conjunto menor desses parâmetros pode ser substituído para fornecer ações que são específicas para o seu fornecedor. Exemplos desses parâmetros incluem o `Path` e `Value` parâmetro do `Set-Item` cmdlet. Aqui está uma lista dos parâmetros que podem ser substituídas para os cmdlets do fornecedor.

`Clear-Content` cmdlet, pode definir o modo como o seu fornecedor irá utilizar os valores passados para o `Path` parâmetro do `Clear-Content` cmdlet, implementando o [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)método.

`Clear-Item` cmdlet, pode definir o modo como o seu fornecedor irá utilizar os valores passados para o `Path` parâmetro do `Clear-Item` cmdlet ao implementar a [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) método.

`Clear-ItemProperty` cmdlet, pode definir o modo como o seu fornecedor irá utilizar os valores passados para o `Path` e `Name` parâmetros do `Clear-ItemProperty` cmdlet implementando o [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) método.

`Copy-Item` cmdlet, pode definir o modo como o seu fornecedor irá utilizar os valores passados para o `Path`, `Destination`, e `Recurse` parâmetros do `Copy-Item` cmdlet implementando o [ System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) método.

Cmdlet Get-ChildItems, pode definir o modo como o seu fornecedor irá utilizar os valores passados para o `Path` e `Recurse` parâmetros do `Get-ChildItem` cmdlet implementando o [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) e [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) métodos.

`Get-Content` cmdlet, pode definir o modo como o seu fornecedor irá utilizar os valores passados para o `Path` parâmetro do `Get-Content` cmdlet, implementando o [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) método.

`Get-Item` cmdlet, pode definir o modo como o seu fornecedor irá utilizar os valores passados para o `Path` parâmetro do `Get-Item` cmdlet ao implementar a [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método.

`Get-ItemProperty` cmdlet, pode definir o modo como o seu fornecedor irá utilizar os valores passados para o `Path` e `Name` parâmetros do `Get-ItemProperty` cmdlet implementando o [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) método.

`Invoke-Item` cmdlet, pode definir o modo como o seu fornecedor irá utilizar os valores passados para o `Path` parâmetro do `Invoke-Item` cmdlet, implementando o [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)método.

`Move-Item` cmdlet, pode definir o modo como o seu fornecedor irá utilizar os valores passados para o `Path` e `Destination` parâmetros do `Move-Item` cmdlet implementando o [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) método.

`New-Item` cmdlet, pode definir o modo como o seu fornecedor irá utilizar os valores passados para o `Path`, `ItemType`, e `Value` parâmetros do `New-Item` cmdlet implementando o [ System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método.

`New-ItemProperty` cmdlet, pode definir o modo como o seu fornecedor irá utilizar os valores passados para o `Path`, `Name`, `PropertyType`, e `Value` parâmetros do `New-ItemProperty` cmdlet implementando o [ Microsoft.PowerShell.Commands.Registryprovider.Newproperty*](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) método.

`Remove-Item` Pode definir o modo como o seu fornecedor irá utilizar os valores passados para o `Path` e `Recurse` parâmetros do `Remove-Item` cmdlet implementando o [System.Management.Automation.Provider.Containercmdletprovider.Removeitem* ](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) método.

`Remove-ItemProperty` Pode definir o modo como o seu fornecedor irá utilizar os valores passados para o `Path` e `Name` parâmetros do `Remove-ItemProperty` cmdlet implementando o [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) método.

`Rename-Item` cmdlet, pode definir o modo como o seu fornecedor irá utilizar os valores passados para o `Path` e `NewName` parâmetros do `Rename-Item` cmdlet implementando o [ System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) método.

`Rename-ItemProperty` Pode definir o modo como o seu fornecedor irá utilizar os valores passados para o `Path`, `NewName`, e `Name` parâmetros do `Rename-ItemProperty` cmdlet implementando o [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) método.

`Set-Content` cmdlet, pode definir o modo como o seu fornecedor irá utilizar os valores passados para o `Path` parâmetro do `Set-Content` cmdlet, implementando o [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) método.

`Set-Item` cmdlet, pode definir o modo como o seu fornecedor irá utilizar os valores passados para o `Path` e `Value` parâmetros do `Set-Item` cmdlet implementando o [System.Management.Automation.Provider.Itemcmdletprovider.Setitem* ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) método.

`Set-ItemProperty` cmdlet, pode definir o modo como o seu fornecedor irá utilizar os valores passados para o `Path` e `Value` parâmetros do `Set-Item` cmdlet implementando o [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) método.

`Test-Path` cmdlet, pode definir o modo como o seu fornecedor irá utilizar os valores passados para o `Path` parâmetro do `Test-Path` cmdlet, implementando o [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)método.

Além disso, não é possível especificar as características desses parâmetros, como se eles são opcionais ou necessária, nem pode fornecer estes parâmetros um alias ou especificar qualquer um dos atributos de validação. Por outro lado, pode especificar características de parâmetro nos cmdlets autónomo por meio de atributos, tais como o `Parameters` atributo.

## <a name="provider-cmdlet-dynamic-parameters"></a>Parâmetros de Cmdlet dinâmico do fornecedor

Os parâmetros dinâmicos para fornecedores de cmdlet são semelhantes aos fornecedores de dinâmicos para os cmdlets autónomo. Em ambos os casos, os parâmetros são adicionados ao cmdlet, quando o usuário Especifica um determinado valor de um dos parâmetros predefinidos, tais como o `path` parâmetro. No entanto, nem todos os parâmetros estáticos podem ser utilizados para acionar a adição dos parâmetros dinâmicos. Para obter mais informações sobre parâmetros dinâmicos, consulte [parâmetros dinâmicos do fornecedor de Cmdlet](./provider-cmdlet-dynamic-parameters.md).

## <a name="see-also"></a>Veja Também

[Parâmetros de Cmdlet dinâmico do fornecedor](./provider-cmdlet-dynamic-parameters.md)

[Escrever um fornecedor do Windows PowerShell](./writing-a-windows-powershell-provider.md)