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
ms.openlocfilehash: d9109e8d5b69a25ad52b90bcaff9628b01067211
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081026"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="6e139-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="6e139-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="6e139-103">Este exemplo demonstra como substituir os métodos de contentor para oferecer suporte a chamadas para o `Copy-Item`, `Get-ChildItem`, `New-Item`, e `Remove-Item` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="6e139-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="6e139-104">Esses métodos devem ser implementados quando o arquivo de dados contém itens que são contentores.</span><span class="sxs-lookup"><span data-stu-id="6e139-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="6e139-105">Um contentor é um grupo de itens filho num item principal comum.</span><span class="sxs-lookup"><span data-stu-id="6e139-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="6e139-106">A classe de fornecedor neste exemplo deriva do [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="6e139-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="6e139-107">Demonstra</span><span class="sxs-lookup"><span data-stu-id="6e139-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6e139-108">Sua classe de provedor é muito provável que serão derivados do [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span><span class="sxs-lookup"><span data-stu-id="6e139-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="6e139-109">Este exemplo demonstra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6e139-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="6e139-110">Declarando o `CmdletProvider` atributo.</span><span class="sxs-lookup"><span data-stu-id="6e139-110">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="6e139-111">Definir uma classe de provedor que deriva de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="6e139-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

- <span data-ttu-id="6e139-112">Substituir a [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) método para alterar o comportamento do `Copy-Item` cmdlet que permite ao usuário copiar itens de uma localização para outra.</span><span class="sxs-lookup"><span data-stu-id="6e139-112">Overwriting the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="6e139-113">(Este exemplo não mostra como adicionar parâmetros dinâmicos para a `Copy-Item` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="6e139-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>

- <span data-ttu-id="6e139-114">Substituir a [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método para alterar o comportamento do cmdlet Get-ChildItems, que permite ao usuário recuperar os itens subordinados de item principal .</span><span class="sxs-lookup"><span data-stu-id="6e139-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="6e139-115">(Este exemplo não mostra como adicionar parâmetros dinâmicos para o cmdlet Get-ChildItems.)</span><span class="sxs-lookup"><span data-stu-id="6e139-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>

- <span data-ttu-id="6e139-116">Substituir a [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) método para alterar o comportamento do cmdlet Get-ChildItems quando o `Name` é especificado o parâmetro do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6e139-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>

- <span data-ttu-id="6e139-117">Substituir a [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método para alterar o comportamento do `New-Item` cmdlet, que permite ao utilizador adicionar itens ao arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="6e139-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="6e139-118">(Este exemplo não mostra como adicionar parâmetros dinâmicos para a `New-Item` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="6e139-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>

- <span data-ttu-id="6e139-119">Substituir a [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) método para alterar o comportamento do `Remove-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6e139-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="6e139-120">(Este exemplo não mostra como adicionar parâmetros dinâmicos para a `Remove-Item` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="6e139-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="6e139-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6e139-121">Example</span></span>

<span data-ttu-id="6e139-122">Este exemplo mostra como substituir os métodos necessários para copiar, criar e remover itens, bem como métodos para fazer o filho itens de um item principal.</span><span class="sxs-lookup"><span data-stu-id="6e139-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="6e139-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="6e139-123">See Also</span></span>

[<span data-ttu-id="6e139-124">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="6e139-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="6e139-125">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="6e139-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="6e139-126">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="6e139-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="6e139-127">Estruturar o seu fornecedor do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6e139-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)