---
title: GetProc01 (C#) o código de exemplo | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 56ce7080e24cc12de6d43ac607ffd5d3f0a3b17c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847433"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="409c2-102">GetProc01 (C#) Sample Code (Código de Exemplo GetProc01 [C#])</span><span class="sxs-lookup"><span data-stu-id="409c2-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="409c2-103">O código a seguir mostra a implementação do cmdlet de exemplo GetProc01.</span><span class="sxs-lookup"><span data-stu-id="409c2-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="409c2-104">Tenha em atenção que o cmdlet é simplificado, deixando o trabalho real de obtenção de processo para o [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) método.</span><span class="sxs-lookup"><span data-stu-id="409c2-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="409c2-105">Pode transferir o C# ficheiro de origem (getproc01.cs) para este cmdlet de Get-Proc usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="409c2-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="409c2-106">Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="409c2-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="409c2-107">Pode transferir o C# ficheiro de origem (getproc01.cs) para este cmdlet de Get-Proc usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="409c2-107">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="409c2-108">Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="409c2-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="409c2-109">Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.</span><span class="sxs-lookup"><span data-stu-id="409c2-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="409c2-110">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="409c2-110">Code Sample</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="409c2-111">Veja Também</span><span class="sxs-lookup"><span data-stu-id="409c2-111">See Also</span></span>

[<span data-ttu-id="409c2-112">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="409c2-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="409c2-113">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="409c2-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)