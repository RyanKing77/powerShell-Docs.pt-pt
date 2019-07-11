---
title: Runspace01 (C#) exemplo de código | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: ab067485d70523a16493eb57170615ab300eaa98
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735050"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="62c87-102">Runspace01 (C#) Code Sample (Código de Exemplo Runspace01 [C#])</span><span class="sxs-lookup"><span data-stu-id="62c87-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="62c87-103">Seguem-se exemplos de código para o espaço de execução descrito em [criar uma aplicação de consola execuções para que um comando especificado](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span><span class="sxs-lookup"><span data-stu-id="62c87-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span> <span data-ttu-id="62c87-104">Para fazer isso, o aplicativo invoca um espaço de execução e, em seguida, invoca um comando.</span><span class="sxs-lookup"><span data-stu-id="62c87-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="62c87-105">(Tenha em atenção que esta aplicação não especifica informações de configuração de espaço de execução nem -lo explicitamente cria um pipeline).</span><span class="sxs-lookup"><span data-stu-id="62c87-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="62c87-106">O comando invocado é o `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="62c87-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="62c87-107">Pode transferir o C# ficheiro de origem (runspace01.cs) para este espaço de execução usando o Microsoft Windows Software Development Kit para Windows Vista e o Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="62c87-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="62c87-108">Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="62c87-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="62c87-109">Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.</span><span class="sxs-lookup"><span data-stu-id="62c87-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="62c87-110">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="62c87-110">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="62c87-111">Veja Também</span><span class="sxs-lookup"><span data-stu-id="62c87-111">See Also</span></span>

[<span data-ttu-id="62c87-112">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="62c87-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="62c87-113">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="62c87-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)