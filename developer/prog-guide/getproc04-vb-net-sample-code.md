---
title: GetProc04 código de exemplo (VB.NET) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d22f47b-3679-4587-a559-94454415d2dd
caps.latest.revision: 5
ms.openlocfilehash: 8de99247574de130b91eea78b9af81dafbab48eb
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429623"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="139a6-102">GetProc04 (VB.NET) Sample Code (Código de Exemplo GetProc04 [VB.NET])</span><span class="sxs-lookup"><span data-stu-id="139a6-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="139a6-103">O código a seguir mostra a implementação de um `Get-Process` cmdlet relatórios de erros de não terminação.</span><span class="sxs-lookup"><span data-stu-id="139a6-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="139a6-104">Essa implementação chama o [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método para relatar erros de não terminação.</span><span class="sxs-lookup"><span data-stu-id="139a6-104">This implementation calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="139a6-105">Pode transferir o C# ficheiro de origem (getprov04.cs) para este cmdlet de Get-Proc usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="139a6-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="139a6-106">Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="139a6-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="139a6-107">Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.</span><span class="sxs-lookup"><span data-stu-id="139a6-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="139a6-108">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="139a6-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="139a6-109">Veja Também</span><span class="sxs-lookup"><span data-stu-id="139a6-109">See Also</span></span>

[<span data-ttu-id="139a6-110">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="139a6-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="139a6-111">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="139a6-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)