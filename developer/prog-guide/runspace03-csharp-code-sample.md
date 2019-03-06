---
title: RunSpace03 (C#) exemplo de código | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 0e80f4d850a7c6dc044526a56b92f16eea4040b5
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429912"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="d6640-102">Runspace03 (C#) Code Sample (Código de Exemplo Runspace03 [C#])</span><span class="sxs-lookup"><span data-stu-id="d6640-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="d6640-103">Aqui está o C# da origem de código da aplicação de consola descrito na [criar uma aplicação de consola execuções para que um Script especificado](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).</span><span class="sxs-lookup"><span data-stu-id="d6640-103">Here is the C# source code for the console application described in [Creating a Console Application That Runs a Specified Script](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).</span></span> <span data-ttu-id="d6640-104">Este exemplo utiliza a [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) classe para executar um script que recupera informações do processo, utilizando a lista de nomes de processo passado para o script.</span><span class="sxs-lookup"><span data-stu-id="d6640-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="d6640-105">Ele mostra como transmitir objetos de entrada para um script e como recuperar objetos de erro, bem como os objetos de saída.</span><span class="sxs-lookup"><span data-stu-id="d6640-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="d6640-106">Pode transferir o C# ficheiro de origem (runspace03.cs) para este exemplo com o Microsoft Windows Software Development Kit para Windows Vista e o Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="d6640-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="d6640-107">Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="d6640-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="d6640-108">Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.</span><span class="sxs-lookup"><span data-stu-id="d6640-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="d6640-109">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="d6640-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="d6640-110">Veja Também</span><span class="sxs-lookup"><span data-stu-id="d6640-110">See Also</span></span>

[<span data-ttu-id="d6640-111">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6640-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="d6640-112">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6640-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)