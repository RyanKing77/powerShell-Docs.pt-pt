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
ms.openlocfilehash: 22a7bdf43a294d1e28f78ccf3412173892fdd53e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847272"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="9c8fe-102">AccessDbProviderSample02 Code Sample (Código de Exemplo AccessDbProviderSample02)</span><span class="sxs-lookup"><span data-stu-id="9c8fe-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="9c8fe-103">O código a seguir mostra a implementação do fornecedor de Windows PowerShell descrito em [criar um fornecedor de unidade do Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="9c8fe-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span> <span data-ttu-id="9c8fe-104">Esta implementação cria um caminho, faz uma ligação para uma base de dados do Access e, em seguida, remove a unidade.</span><span class="sxs-lookup"><span data-stu-id="9c8fe-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="9c8fe-105">Pode transferir o C# ficheiro de origem (AccessDBSampleProvider02.cs) para este fornecedor com o Microsoft Windows Software Development Kit para Windows Vista e o Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="9c8fe-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="9c8fe-106">Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="9c8fe-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="9c8fe-107">Pode transferir o C# ficheiro de origem (AccessDBSampleProvider02.cs) para este fornecedor com o Microsoft Windows Software Development Kit para Windows Vista e o Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="9c8fe-107">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="9c8fe-108">Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="9c8fe-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="9c8fe-109">Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.</span><span class="sxs-lookup"><span data-stu-id="9c8fe-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="9c8fe-110">Para obter mais informações sobre outras implementações de provedores do Windows PowerShell, consulte [conceber Windows PowerShell Fornecedor_de_e](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="9c8fe-110">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="9c8fe-111">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="9c8fe-111">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a><span data-ttu-id="9c8fe-112">Veja Também</span><span class="sxs-lookup"><span data-stu-id="9c8fe-112">See Also</span></span>

[<span data-ttu-id="9c8fe-113">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9c8fe-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="9c8fe-114">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9c8fe-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)