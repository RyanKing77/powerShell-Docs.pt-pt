---
title: AccessDBProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a7e56-7331-4f71-9ecb-7a59b8021c68
caps.latest.revision: 10
ms.openlocfilehash: fd013384a4b588bcdb397d7771425fe5c031c48f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847300"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Este exemplo demonstra como substituir os métodos de contentor para oferecer suporte a chamadas para o `Copy-Item`, `Get-ChildItem`, `New-Item`, e `Remove-Item` cmdlets. Esses métodos devem ser implementados quando o arquivo de dados contém itens que são contentores. Um contentor é um grupo de itens filho num item principal comum. A classe de fornecedor neste exemplo deriva do [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.

## <a name="demonstrates"></a>Demonstra

> [!IMPORTANT]
> Sua classe de provedor é muito provável que serão derivados do [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

Este exemplo demonstra o seguinte:

- Declarando o `CmdletProvider` atributo.

- Definir uma classe de provedor que deriva de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.

- Substituir a [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) método para alterar o comportamento do `Copy-Item` cmdlet que permite ao usuário copiar itens de uma localização para outra. (Este exemplo não mostra como adicionar parâmetros dinâmicos para a `Copy-Item` cmdlet.)

- Substituir a [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método para alterar o comportamento do cmdlet Get-ChildItems, que permite ao usuário recuperar os itens subordinados de item principal . (Este exemplo não mostra como adicionar parâmetros dinâmicos para o cmdlet Get-ChildItems.)

- Substituir a [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) método para alterar o comportamento do cmdlet Get-ChildItems quando o `Name` é especificado o parâmetro do cmdlet.

- Substituir a [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método para alterar o comportamento do `New-Item` cmdlet, que permite ao utilizador adicionar itens ao arquivo de dados. (Este exemplo não mostra como adicionar parâmetros dinâmicos para a `New-Item` cmdlet.)

- Substituir a [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) método para alterar o comportamento do `Remove-Item` cmdlet. (Este exemplo não mostra como adicionar parâmetros dinâmicos para a `Remove-Item` cmdlet.)

## <a name="example"></a>Exemplo

Este exemplo mostra como substituir os métodos necessários para copiar, criar e remover itens, bem como métodos para fazer o filho itens de um item principal.

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Veja Também

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Estruturar o seu fornecedor do Windows PowerShell](./provider-types.md)