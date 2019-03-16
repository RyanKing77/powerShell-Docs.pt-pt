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
ms.openlocfilehash: f020f023f9a379ff8a610edb7d5dcfe207170394
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055551"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="a236f-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="a236f-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="a236f-103">Este exemplo demonstra como substituir os métodos de conteúdo para oferecer suporte a chamadas para o `Clear-Content`, `Get-Content`, e `Set-Content` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="a236f-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="a236f-104">Esses métodos devem ser implementados quando os utilizadores necessitam gerir o conteúdo dos itens no arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="a236f-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="a236f-105">A classe de fornecedor neste exemplo deriva do [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe e ele implementa o [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span><span class="sxs-lookup"><span data-stu-id="a236f-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="a236f-106">Demonstra</span><span class="sxs-lookup"><span data-stu-id="a236f-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a236f-107">Sua classe de fornecedor será provavelmente derivam de uma das seguintes classes e, possivelmente, implementar outras interfaces de fornecedor:</span><span class="sxs-lookup"><span data-stu-id="a236f-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="a236f-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="a236f-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="a236f-109">Ver [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="a236f-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="a236f-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="a236f-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="a236f-111">Ver [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="a236f-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="a236f-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="a236f-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="a236f-113">Para obter mais informações sobre como escolher a classe de fornecedor que derivar de com base nos recursos de fornecedor, consulte [conceber Windows PowerShell Fornecedor_de_e](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="a236f-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="a236f-114">Este exemplo demonstra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a236f-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="a236f-115">Declarando o `CmdletProvider` atributo.</span><span class="sxs-lookup"><span data-stu-id="a236f-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="a236f-116">Definindo uma classe de provedor que deriva de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe e de que declara o [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span><span class="sxs-lookup"><span data-stu-id="a236f-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

- <span data-ttu-id="a236f-117">Substituir a [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) método para alterar o comportamento do `Clear-Content` cmdlet, permitindo que o usuário remover o conteúdo de um item.</span><span class="sxs-lookup"><span data-stu-id="a236f-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="a236f-118">(Este exemplo não mostra como adicionar parâmetros dinâmicos para a `Clear-Content` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="a236f-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>

- <span data-ttu-id="a236f-119">Substituir a [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) método para alterar o comportamento do `Get-Content` cmdlet, permitindo que o utilizador a obter o conteúdo de um item.</span><span class="sxs-lookup"><span data-stu-id="a236f-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="a236f-120">(Este exemplo não mostra como adicionar parâmetros dinâmicos para a `Get-Content` cmdlet.).</span><span class="sxs-lookup"><span data-stu-id="a236f-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>

- <span data-ttu-id="a236f-121">Substituir a [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) método para alterar o comportamento do `Set-Content` cmdlet, permitindo que o usuário atualizar o conteúdo de um item.</span><span class="sxs-lookup"><span data-stu-id="a236f-121">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="a236f-122">(Este exemplo não mostra como adicionar parâmetros dinâmicos para a `Set-Content` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="a236f-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="a236f-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a236f-123">Example</span></span>

<span data-ttu-id="a236f-124">Este exemplo mostra como substituir os métodos necessários para limpar, obter e definir o conteúdo dos itens numa dados Microsoft Access base.</span><span class="sxs-lookup"><span data-stu-id="a236f-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="a236f-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="a236f-125">See Also</span></span>

[<span data-ttu-id="a236f-126">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a236f-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="a236f-127">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a236f-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="a236f-128">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a236f-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="a236f-129">Estruturar o seu fornecedor do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a236f-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)