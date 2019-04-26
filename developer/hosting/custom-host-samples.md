---
title: Exemplos de anfitrião personalizado | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082928"
---
# <a name="custom-host-samples"></a><span data-ttu-id="d78d1-102">Custom Host Samples (Exemplos de Anfitriões Personalizados)</span><span class="sxs-lookup"><span data-stu-id="d78d1-102">Custom Host Samples</span></span>

<span data-ttu-id="d78d1-103">Esta secção inclui código de exemplo para a escrita de um host personalizado.</span><span class="sxs-lookup"><span data-stu-id="d78d1-103">This section includes sample code for writing a custom host.</span></span> <span data-ttu-id="d78d1-104">Pode utilizar o Microsoft Visual Studio para criar uma aplicação de consola e, em seguida, copie o código os tópicos nesta secção para seu aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="d78d1-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d78d1-105">Nesta Secção</span><span class="sxs-lookup"><span data-stu-id="d78d1-105">In This Section</span></span>

 <span data-ttu-id="d78d1-106">[Exemplo de Host01](./host01-sample.md) este exemplo mostra como implementar um aplicativo de host que usa um host personalizado básico.</span><span class="sxs-lookup"><span data-stu-id="d78d1-106">[Host01 Sample](./host01-sample.md) This sample shows how to implement a host application that uses a basic custom host.</span></span>

 <span data-ttu-id="d78d1-107">[Exemplo de Host02](./host02-sample.md) este exemplo mostra como escrever um aplicativo de host que usa o tempo de execução do Windows PowerShell, juntamente com uma implementação de anfitrião personalizado.</span><span class="sxs-lookup"><span data-stu-id="d78d1-107">[Host02 Sample](./host02-sample.md) This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="d78d1-108">O aplicativo host define a cultura de anfitrião para o alemão, execuções a [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet e apresenta os resultados à medida que veria-los usando pwrsh.exe e, em seguida, imprime os dados atuais e a hora em alemão.</span><span class="sxs-lookup"><span data-stu-id="d78d1-108">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them using pwrsh.exe, and then prints out the current data and time in German.</span></span>

 <span data-ttu-id="d78d1-109">[Exemplo de Host03](./host03-sample.md) este exemplo mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console.</span><span class="sxs-lookup"><span data-stu-id="d78d1-109">[Host03 Sample](./host03-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

 <span data-ttu-id="d78d1-110">[Exemplo de Host04](./host04-sample.md) este exemplo mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console.</span><span class="sxs-lookup"><span data-stu-id="d78d1-110">[Host04 Sample](./host04-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="d78d1-111">Este aplicativo de host também suporta a apresentação de pedidos que permitem ao usuário especificar várias opções.</span><span class="sxs-lookup"><span data-stu-id="d78d1-111">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

 <span data-ttu-id="d78d1-112">[Exemplo de Host05](./host05-sample.md) este exemplo mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console.</span><span class="sxs-lookup"><span data-stu-id="d78d1-112">[Host05 Sample](./host05-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="d78d1-113">Este aplicativo de host também oferece suporte a chamadas para computadores remotos utilizando o [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) e [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span><span class="sxs-lookup"><span data-stu-id="d78d1-113">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span></span>

 <span data-ttu-id="d78d1-114">[Exemplo de Host06](./host06-sample.md) este exemplo mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console.</span><span class="sxs-lookup"><span data-stu-id="d78d1-114">[Host06 Sample](./host06-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="d78d1-115">Além disso, este exemplo utiliza as APIs de atomizador para especificar a cor do texto que é introduzido pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="d78d1-115">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="d78d1-116">Veja Também</span><span class="sxs-lookup"><span data-stu-id="d78d1-116">See Also</span></span>
