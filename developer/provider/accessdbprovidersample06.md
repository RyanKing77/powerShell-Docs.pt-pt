---
title: AccessDBProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: 59832ed8a4fad3b07a171946bff28fb3e1dbe442
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845872"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

Este exemplo demonstra como substituir os métodos de conteúdo para oferecer suporte a chamadas para o `Clear-Content`, `Get-Content`, e `Set-Content` cmdlets. Esses métodos devem ser implementados quando os utilizadores necessitam gerir o conteúdo dos itens no arquivo de dados. A classe de fornecedor neste exemplo deriva do [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe e ele implementa o [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.

## <a name="demonstrates"></a>Demonstra

> [!IMPORTANT]
> Sua classe de fornecedor será provavelmente derivam de uma das seguintes classes e, possivelmente, implementar outras interfaces de fornecedor:
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe. Ver [AccessDBProviderSample03](./accessdbprovidersample03.md).
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe. Ver [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.
>
> Para obter mais informações sobre como escolher a classe de fornecedor que derivar de com base nos recursos de fornecedor, consulte [conceber Windows PowerShell Fornecedor_de_e](./provider-types.md).

Este exemplo demonstra o seguinte:

- Declarando o `CmdletProvider` atributo.

- Definindo uma classe de provedor que deriva de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe e de que declara o [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.

- Substituir a [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) método para alterar o comportamento do `Clear-Content` cmdlet, permitindo que o usuário remover o conteúdo de um item. (Este exemplo não mostra como adicionar parâmetros dinâmicos para a `Clear-Content` cmdlet.)

- Substituir a [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) método para alterar o comportamento do `Get-Content` cmdlet, permitindo que o utilizador a obter o conteúdo de um item. (Este exemplo não mostra como adicionar parâmetros dinâmicos para a `Get-Content` cmdlet.).

- Substituir a [Microsoft.Powershell.Commands.Filesystemprovider.Getcontentwriter*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) método para alterar o comportamento do `Set-Content` cmdlet, permitindo que o usuário atualizar o conteúdo de um item. (Este exemplo não mostra como adicionar parâmetros dinâmicos para a `Set-Content` cmdlet.)

## <a name="example"></a>Exemplo

Este exemplo mostra como substituir os métodos necessários para limpar, obter e definir o conteúdo dos itens numa dados Microsoft Access base.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Estruturar o seu fornecedor do Windows PowerShell](./provider-types.md)