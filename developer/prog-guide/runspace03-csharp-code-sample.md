---
title: Exemplo deC#código RunSpace03 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 9afdb97b8ae2919f091ca5bacccedbe37c2e1584
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848037"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="0f488-102">Runspace03 (C#) Code Sample (Código de Exemplo Runspace03 [C#])</span><span class="sxs-lookup"><span data-stu-id="0f488-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="0f488-103">Este é o C# código-fonte do aplicativo de console descrito em "criando um aplicativo de console que executa um script especificado".</span><span class="sxs-lookup"><span data-stu-id="0f488-103">Here is the C# source code for the console application described in "Creating a Console Application That Runs a Specified Script".</span></span> <span data-ttu-id="0f488-104">Este exemplo usa a classe [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) para executar um script que recupera informações de processo usando a lista de nomes de processo passados para o script.</span><span class="sxs-lookup"><span data-stu-id="0f488-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="0f488-105">Ele mostra como passar objetos de entrada para um script e como recuperar objetos de erro, bem como os objetos de saída.</span><span class="sxs-lookup"><span data-stu-id="0f488-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="0f488-106">Você pode baixar o C# arquivo de origem (runspace03.cs) para este exemplo usando os componentes de tempo de execução do Microsoft Windows Software Development Kit para Windows Vista e Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="0f488-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="0f488-107">Para obter instruções de download, consulte [como instalar o Windows PowerShell e baixar o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="0f488-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="0f488-108">Os arquivos de origem baixados estão disponíveis no diretório de  **\<exemplos do PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="0f488-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="0f488-109">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="0f488-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="0f488-110">Veja Também</span><span class="sxs-lookup"><span data-stu-id="0f488-110">See Also</span></span>

[<span data-ttu-id="0f488-111">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f488-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="0f488-112">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f488-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)