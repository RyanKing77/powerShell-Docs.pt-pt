---
title: Exemplo de código RunSpace07 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: 3e016b0e98234797afc8f303a55919228eaf8829
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848161"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="c31d6-102">Runspace07 Code Sample (Código de Exemplo Runspace07)</span><span class="sxs-lookup"><span data-stu-id="c31d6-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="c31d6-103">Eis o código-fonte para o exemplo de Runspace07 descrito em [criar uma aplicação que adiciona comandos da consola para um Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span><span class="sxs-lookup"><span data-stu-id="c31d6-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span> <span data-ttu-id="c31d6-104">Este aplicativo de exemplo cria um espaço de execução, cria um pipeline, adiciona dois comandos para o pipeline e, em seguida, executa o pipeline.</span><span class="sxs-lookup"><span data-stu-id="c31d6-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="c31d6-105">Os comandos adicionados ao pipeline são os `Get-Process` e `Measure-Object` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c31d6-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="c31d6-106">Pode transferir o C# arquivo de origem (runspace07.cs) usando o Microsoft Windows Software Development Kit para Windows Vista e o Microsoft .NET Framework 3.0 Runtime componentes.</span><span class="sxs-lookup"><span data-stu-id="c31d6-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="c31d6-107">Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="c31d6-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="c31d6-108">Pode transferir o C# arquivo de origem (runspace07.cs) usando o Microsoft Windows Software Development Kit para Windows Vista e o Microsoft .NET Framework 3.0 Runtime componentes.</span><span class="sxs-lookup"><span data-stu-id="c31d6-108">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="c31d6-109">Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="c31d6-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="c31d6-110">Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.</span><span class="sxs-lookup"><span data-stu-id="c31d6-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c31d6-111">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="c31d6-111">Code Sample</span></span>

[!code-csharp[Runspace07.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a><span data-ttu-id="c31d6-112">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="c31d6-112">See Also</span></span>

[<span data-ttu-id="c31d6-113">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c31d6-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="c31d6-114">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c31d6-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)