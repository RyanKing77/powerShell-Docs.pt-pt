---
title: Exemplos de código GetProc03 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad39c7d-2f64-49d1-9be0-d2295e4302b3
caps.latest.revision: 5
ms.openlocfilehash: 8cb02b9f2510b90f405651deaf551e9622f5a298
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847727"
---
# <a name="getproc03-code-samples"></a><span data-ttu-id="2b1db-102">GetProc03 Code Samples (Códigos de Exemplo GetProc03)</span><span class="sxs-lookup"><span data-stu-id="2b1db-102">GetProc03 Code Samples</span></span>

<span data-ttu-id="2b1db-103">Aqui estão os exemplos de código para o cmdlet de exemplo GetProc03.</span><span class="sxs-lookup"><span data-stu-id="2b1db-103">Here are the code samples for the GetProc03 sample cmdlet.</span></span> <span data-ttu-id="2b1db-104">Este é o `Get-Process` cmdlet de exemplo descrito na [adicionando parâmetros de entrada do Pipeline esse processo](../cmdlet/adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="2b1db-104">This is the `Get-Process` cmdlet sample described in [Adding Parameters that Process Pipeline Input](../cmdlet/adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="2b1db-105">Isso `Get-Process` cmdlet utiliza um `Name` parâmetro que aceite entrada de um objeto de pipeline, obtém informações de processo a partir do computador local com base nos nomes fornecidos e, em seguida, apresenta informações sobre os processos na linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="2b1db-105">This `Get-Process` cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="2b1db-106">Pode transferir o C# ficheiro de origem (getprov03.cs) para este cmdlet de Get-Proc usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="2b1db-106">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2b1db-107">Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="2b1db-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="2b1db-108">Pode transferir o C# ficheiro de origem (getprov03.cs) para este cmdlet de Get-Proc usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="2b1db-108">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2b1db-109">Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="2b1db-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="2b1db-110">Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.</span><span class="sxs-lookup"><span data-stu-id="2b1db-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="2b1db-111">Para o código de exemplo completo, consulte os seguintes tópicos.</span><span class="sxs-lookup"><span data-stu-id="2b1db-111">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="2b1db-112">Idioma</span><span class="sxs-lookup"><span data-stu-id="2b1db-112">Language</span></span>|<span data-ttu-id="2b1db-113">Tópico</span><span class="sxs-lookup"><span data-stu-id="2b1db-113">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="2b1db-114">C#</span><span class="sxs-lookup"><span data-stu-id="2b1db-114">C#</span></span>|[<span data-ttu-id="2b1db-115">GetProc03 (C#) o código de exemplo</span><span class="sxs-lookup"><span data-stu-id="2b1db-115">GetProc03 (C#) Sample Code</span></span>](./getproc03-csharp-sample-code.md)|
|<span data-ttu-id="2b1db-116">VB.NET</span><span class="sxs-lookup"><span data-stu-id="2b1db-116">VB.NET</span></span>|[<span data-ttu-id="2b1db-117">GetProc03 código de exemplo (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="2b1db-117">GetProc03 (VB.NET) Sample Code</span></span>](./getproc03-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="2b1db-118">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="2b1db-118">See Also</span></span>

[<span data-ttu-id="2b1db-119">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2b1db-119">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="2b1db-120">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2b1db-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)