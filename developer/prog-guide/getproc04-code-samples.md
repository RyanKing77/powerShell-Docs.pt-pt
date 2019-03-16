---
title: Exemplos de código GetProc04 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 67081528ebe14fbb082091c1b9500de82069b48f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054650"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="0c7e3-102">GetProc04 Code Samples (Códigos de Exemplo GetProc04)</span><span class="sxs-lookup"><span data-stu-id="0c7e3-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="0c7e3-103">Aqui estão os exemplos de código para o cmdlet de exemplo GetProc04.</span><span class="sxs-lookup"><span data-stu-id="0c7e3-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="0c7e3-104">Este é o `Get-Process` cmdlet de exemplo descrito na [adição de não terminação relatório de erros ao seu Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="0c7e3-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="0c7e3-105">Isso `Get-Process` chamadas de cmdlet do [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método sempre que é emitida uma exceção de operação inválida ao obter as informações de processo.</span><span class="sxs-lookup"><span data-stu-id="0c7e3-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="0c7e3-106">Pode transferir o C# ficheiro de origem (getprov04.cs) para este cmdlet de Get-Proc usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="0c7e3-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="0c7e3-107">Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="0c7e3-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="0c7e3-108">Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.</span><span class="sxs-lookup"><span data-stu-id="0c7e3-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="0c7e3-109">Para o código de exemplo completo, consulte os seguintes tópicos.</span><span class="sxs-lookup"><span data-stu-id="0c7e3-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="0c7e3-110">Idioma</span><span class="sxs-lookup"><span data-stu-id="0c7e3-110">Language</span></span>|<span data-ttu-id="0c7e3-111">Tópico</span><span class="sxs-lookup"><span data-stu-id="0c7e3-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="0c7e3-112">C#</span><span class="sxs-lookup"><span data-stu-id="0c7e3-112">C#</span></span>|[<span data-ttu-id="0c7e3-113">GetProc04 (C#) o código de exemplo</span><span class="sxs-lookup"><span data-stu-id="0c7e3-113">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="0c7e3-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="0c7e3-114">VB.NET</span></span>|[<span data-ttu-id="0c7e3-115">GetProc04 código de exemplo (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="0c7e3-115">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="0c7e3-116">Veja Também</span><span class="sxs-lookup"><span data-stu-id="0c7e3-116">See Also</span></span>

[<span data-ttu-id="0c7e3-117">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c7e3-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="0c7e3-118">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c7e3-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)