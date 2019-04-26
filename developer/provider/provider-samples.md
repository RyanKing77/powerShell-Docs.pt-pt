---
title: Exemplos de fornecedor | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4933dad-fec9-4337-a1a9-9dc16ee87cc3
caps.latest.revision: 9
ms.openlocfilehash: 1e7aeb5bcb6bd5a2845648c3327e2245e6c428ba
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080939"
---
# <a name="provider-samples"></a>Provider Samples (Exemplos de Fornecedores)

Esta secção inclui exemplos de fornecedores que acessar um banco de dados do Microsoft Access. As amostras incluem classes de fornecedor que derivam de todas as classes de fornecedor de base.

## <a name="in-this-section"></a>Nesta Secção

Esta seção inclui os seguintes tópicos:

[Exemplo de AccessDBProviderSample01](./accessdbprovidersample01.md) este exemplo mostra como declarar a classe de provedor que deriva diretamente a partir de [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe. Ele é incluído aqui apenas para fornecer uma visão completa.

[AccessDBProviderSample02](./accessdbprovidersample02.md) este exemplo demonstra como substituir o [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [ System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) métodos para oferecer suporte a chamadas para o `New-PSDrive` e `Remove-PSDrive` cmdlets. A classe de fornecedor neste exemplo deriva do [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe.

[AccessDBProviderSample03](./accessdbprovidersample03.md) este exemplo demonstra como substituir o [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) e [ System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) métodos para oferecer suporte a chamadas para o `Get-Item` e `Set-Item` cmdlets. A classe de fornecedor neste exemplo deriva do [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.

[AccessDBProviderSample04](./accessdbprovidersample04.md) este exemplo demonstra como substituir os métodos de contentor para oferecer suporte a chamadas para o `Copy-Item`, `Get-ChildItem`, `New-Item`, e `Remove-Item` cmdlets. Esses métodos devem ser implementados quando o arquivo de dados contém itens que são contentores. Um contentor é um grupo de itens filho num item principal comum. A classe de fornecedor neste exemplo deriva do [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.

[AccessDBProviderSample05](./accessdbprovidersample05.md) este exemplo demonstra como substituir os métodos de contentor para oferecer suporte a chamadas para o `Move-Item` e `Join-Path` cmdlets. Esses métodos devem ser implementados quando o utilizador tem de mover itens dentro de um contêiner e se o arquivo de dados contém contêineres aninhados. A classe de fornecedor neste exemplo deriva do [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.

[AccessDBProviderSample06](./accessdbprovidersample06.md) este exemplo demonstra como substituir os métodos de conteúdo para oferecer suporte a chamadas para o `Clear-Content`, `Get-Content`, e `Set-Content` cmdlets. Esses métodos devem ser implementados quando os utilizadores necessitam gerir o conteúdo dos itens no arquivo de dados. A classe de fornecedor neste exemplo deriva do [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe e ele implementa o [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.

## <a name="see-also"></a>Veja Também

[Escrever um fornecedor do Windows PowerShell](./writing-a-windows-powershell-provider.md)