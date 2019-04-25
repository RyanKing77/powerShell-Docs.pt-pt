---
title: GetProc03 (C#) o código de exemplo | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 4d921dd62999bc68b80838bafa2a3da8d4df3ebb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081523"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="c4176-102">GetProc03 (C#) Sample Code (Código de Exemplo GetProc03 [C#])</span><span class="sxs-lookup"><span data-stu-id="c4176-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="c4176-103">O código a seguir mostra a implementação de um `Get-Process` pipelined de cmdlet que pode aceitar entrada.</span><span class="sxs-lookup"><span data-stu-id="c4176-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="c4176-104">Essa implementação define um `Name` parâmetro que aceita entrada do pipeline, obtém informações de processo a partir do computador local com base nos nomes fornecidos e, em seguida, utiliza o [System.Management.Automation.Cmdlet.WriteObject% 28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) método como o mecanismo de saída para o envio de objetos para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="c4176-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="c4176-105">Pode transferir o C# ficheiro de origem (getprov03.cs) para este cmdlet de Get-Proc usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="c4176-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="c4176-106">Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="c4176-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="c4176-107">Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.</span><span class="sxs-lookup"><span data-stu-id="c4176-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c4176-108">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="c4176-108">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="c4176-109">Veja Também</span><span class="sxs-lookup"><span data-stu-id="c4176-109">See Also</span></span>

[<span data-ttu-id="c4176-110">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4176-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="c4176-111">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4176-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)