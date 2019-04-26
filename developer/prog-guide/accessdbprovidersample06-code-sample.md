---
title: Exemplo de código AccessDbProviderSample06 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: baab6a56-c199-48d7-a03e-a904b1bb1baa
caps.latest.revision: 7
ms.openlocfilehash: 6e86318573df92b9ec84056631843e0efa096a3b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081942"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="97783-102">AccessDbProviderSample06 Code Sample (Código de Exemplo AccessDbProviderSample06)</span><span class="sxs-lookup"><span data-stu-id="97783-102">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="97783-103">O código a seguir mostra a implementação do Windows PowerShell fornecedor de conteúdos descrito em [criar um fornecedor de conteúdo do Windows PowerShell](./creating-a-windows-powershell-content-provider.md).</span><span class="sxs-lookup"><span data-stu-id="97783-103">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span> <span data-ttu-id="97783-104">Esse provedor permite que o usuário manipular o conteúdo dos itens de um arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="97783-104">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="97783-105">Pode transferir o C# ficheiro de origem (AccessDBSampleProvider06.cs) para este fornecedor com o Microsoft Windows Software Development Kit para Windows Vista e o Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="97783-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="97783-106">Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="97783-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="97783-107">Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.</span><span class="sxs-lookup"><span data-stu-id="97783-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="97783-108">Para obter mais informações sobre outras implementações de provedores do Windows PowerShell, consulte [conceber Windows PowerShell Fornecedor_de_e](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="97783-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="97783-109">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="97783-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="97783-110">Veja Também</span><span class="sxs-lookup"><span data-stu-id="97783-110">See Also</span></span>

[<span data-ttu-id="97783-111">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="97783-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="97783-112">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="97783-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)