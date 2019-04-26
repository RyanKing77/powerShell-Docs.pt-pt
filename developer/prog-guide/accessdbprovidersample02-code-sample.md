---
title: Exemplo de código AccessDbProviderSample02 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 67a169bfac0b0fc90e6ccd276d3d3592d1b70bb0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082038"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="82b6c-102">AccessDbProviderSample02 Code Sample (Código de Exemplo AccessDbProviderSample02)</span><span class="sxs-lookup"><span data-stu-id="82b6c-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="82b6c-103">O código a seguir mostra a implementação do fornecedor de Windows PowerShell descrito em [criar um fornecedor de unidade do Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="82b6c-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span> <span data-ttu-id="82b6c-104">Esta implementação cria um caminho, faz uma ligação para uma base de dados do Access e, em seguida, remove a unidade.</span><span class="sxs-lookup"><span data-stu-id="82b6c-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="82b6c-105">Pode transferir o C# ficheiro de origem (AccessDBSampleProvider02.cs) para este fornecedor com o Microsoft Windows Software Development Kit para Windows Vista e o Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="82b6c-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="82b6c-106">Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="82b6c-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="82b6c-107">Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.</span><span class="sxs-lookup"><span data-stu-id="82b6c-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="82b6c-108">Para obter mais informações sobre outras implementações de provedores do Windows PowerShell, consulte [conceber Windows PowerShell Fornecedor_de_e](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="82b6c-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="82b6c-109">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="82b6c-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a><span data-ttu-id="82b6c-110">Veja Também</span><span class="sxs-lookup"><span data-stu-id="82b6c-110">See Also</span></span>

[<span data-ttu-id="82b6c-111">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="82b6c-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="82b6c-112">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="82b6c-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)