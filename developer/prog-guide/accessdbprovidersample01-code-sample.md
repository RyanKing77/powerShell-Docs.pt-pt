---
title: Exemplo de código AccessDbProviderSample01 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 01b95e18794501c2aff13d1e51b7400ae6fb8730
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849379"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="4bac7-102">AccessDbProviderSample01 Code Sample (Código de Exemplo AccessDbProviderSample01)</span><span class="sxs-lookup"><span data-stu-id="4bac7-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="4bac7-103">O código a seguir mostra a implementação do fornecedor de Windows PowerShell descrito em [criar um fornecedor de PowerShell básica do Windows](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="4bac7-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="4bac7-104">Esta implementação fornece métodos para iniciar e parar o fornecedor e, embora ele não fornece um meio para aceder a um arquivo de dados ou para obter ou definir os dados no arquivo de dados, ela fornece a funcionalidade básica que sejam necessários para todos os fornecedores.</span><span class="sxs-lookup"><span data-stu-id="4bac7-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="4bac7-105">Pode transferir o C# ficheiro de origem (AccessDBSampleProvider01.cs) para este fornecedor com o Windows Software Development Kit para Windows Vista e o Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="4bac7-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="4bac7-106">Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="4bac7-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="4bac7-107">Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.</span><span class="sxs-lookup"><span data-stu-id="4bac7-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="4bac7-108">Para obter mais informações sobre outras implementações de provedores do Windows PowerShell, consulte [conceber Windows PowerShell Fornecedor_de_e](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="4bac7-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="4bac7-109">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="4bac7-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="4bac7-110">Veja Também</span><span class="sxs-lookup"><span data-stu-id="4bac7-110">See Also</span></span>

[<span data-ttu-id="4bac7-111">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4bac7-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="4bac7-112">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4bac7-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)