---
title: GetProc04 (C#) o código de exemplo | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 439ba3f3-91b1-46a4-8d07-9af6edb71bc4
caps.latest.revision: 5
ms.openlocfilehash: 936fb355be40b98136719ea929cf50b06705b687
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058288"
---
# <a name="getproc04-c-sample-code"></a><span data-ttu-id="5cd94-102">GetProc04 (C#) Sample Code (Código de Exemplo GetProc04 [C#])</span><span class="sxs-lookup"><span data-stu-id="5cd94-102">GetProc04 (C#) Sample Code</span></span>

<span data-ttu-id="5cd94-103">O código a seguir mostra a implementação de um `Get-Process` cmdlet relatórios de erros de não terminação.</span><span class="sxs-lookup"><span data-stu-id="5cd94-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="5cd94-104">Essa implementação chama o [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método para relatar erros de não terminação.</span><span class="sxs-lookup"><span data-stu-id="5cd94-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="5cd94-105">Pode transferir o C# ficheiro de origem (getprov04.cs) para este cmdlet de Get-Proc usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="5cd94-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="5cd94-106">Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="5cd94-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="5cd94-107">Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.</span><span class="sxs-lookup"><span data-stu-id="5cd94-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5cd94-108">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="5cd94-108">Code Sample</span></span>

[!code-csharp[GetProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs#L11-L98 "GetProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="5cd94-109">Veja Também</span><span class="sxs-lookup"><span data-stu-id="5cd94-109">See Also</span></span>

[<span data-ttu-id="5cd94-110">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5cd94-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="5cd94-111">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5cd94-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)