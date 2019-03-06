---
title: Exemplo de código RunSpace10 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5337dc40-c56e-458b-aedc-5f5d401dfd28
caps.latest.revision: 6
ms.openlocfilehash: 77c0675b45bf4ff6f8c6a85ff9a090c13c199c6d
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429589"
---
# <a name="runspace10-code-sample"></a><span data-ttu-id="9f034-102">Runspace10 Code Sample (Código de Exemplo Runspace10)</span><span class="sxs-lookup"><span data-stu-id="9f034-102">RunSpace10 Code Sample</span></span>

<span data-ttu-id="9f034-103">Aqui está o código-fonte para o exemplo de Runspace10.</span><span class="sxs-lookup"><span data-stu-id="9f034-103">Here is the source code for the Runspace10 sample.</span></span> <span data-ttu-id="9f034-104">Este aplicativo de exemplo adiciona um cmdlet para [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) e, em seguida, usa as informações de configuração modificado para criar o espaço de execução.</span><span class="sxs-lookup"><span data-stu-id="9f034-104">This sample application adds a cmdlet to [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) and then uses the modified configuration information to create the runspace.</span></span>

> [!NOTE]
> <span data-ttu-id="9f034-105">Pode transferir o C# ficheiro de origem (runspace10.cs) com o Windows Software Development Kit para Windows Vista e o Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="9f034-105">You can download the C# source file (runspace10.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="9f034-106">Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="9f034-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="9f034-107">Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.</span><span class="sxs-lookup"><span data-stu-id="9f034-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="9f034-108">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="9f034-108">Code Sample</span></span>

[!code-csharp[Runspace10.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace10/Runspace10.cs#L11-L118 "Runspace10.cs")]

## <a name="see-also"></a><span data-ttu-id="9f034-109">Veja Também</span><span class="sxs-lookup"><span data-stu-id="9f034-109">See Also</span></span>

[<span data-ttu-id="9f034-110">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9f034-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="9f034-111">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9f034-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)