---
title: Exemplo de código AccessDbProviderSample04 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: 43f01b9cd6af3ab6c26f88ee0c1e9269499b2bc3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845137"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="f3a21-102">AccessDbProviderSample04 Code Sample (Código de Exemplo AccessDbProviderSample04)</span><span class="sxs-lookup"><span data-stu-id="f3a21-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="f3a21-103">O código a seguir mostra a implementação do fornecedor de Windows PowerShell descrito em [criar um fornecedor de contentor do Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="f3a21-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span> <span data-ttu-id="f3a21-104">Este fornecedor funciona em arquivos de dados de multi camada.</span><span class="sxs-lookup"><span data-stu-id="f3a21-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="f3a21-105">Para este tipo de arquivo de dados, o nível superior do arquivo contém os itens de raiz e cada nível subseqüente é referido como um nó de itens subordinados.</span><span class="sxs-lookup"><span data-stu-id="f3a21-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="f3a21-106">Ao permitir que o utilizador trabalhar em de nós subordinados, um usuário pode interagir hierarquicamente por meio do arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="f3a21-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f3a21-107">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="f3a21-107">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="f3a21-108">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="f3a21-108">See Also</span></span>

[<span data-ttu-id="f3a21-109">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3a21-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)