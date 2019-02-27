---
title: Escrever um aplicativo de Host de PowerShell do Windows | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81aeafad-dbc3-4712-8bb9-e6a417be260f
caps.latest.revision: 15
ms.openlocfilehash: 2039e181becd1b39fc3d6cf0cdbcf0c20e9fc206
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851836"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="16439-102">Writing a Windows PowerShell Host Application (Escrever uma Aplicação Anfitriã do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="16439-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="16439-103">Pode hospedar o Windows PowerShell em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="16439-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="16439-104">O aplicativo host pode definir o espaço de execução onde os comandos são executados, abra sessões num computador local ou remoto e invocar os comandos de forma síncrona ou assíncrona baseada nas necessidades do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="16439-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="16439-105">Os tópicos seguintes explicam como criar uma aplicação que aloja</span><span class="sxs-lookup"><span data-stu-id="16439-105">The following topics explain how to create an application that hosts</span></span>

## <a name="in-this-section"></a><span data-ttu-id="16439-106">Nesta Secção</span><span class="sxs-lookup"><span data-stu-id="16439-106">In This Section</span></span>

<span data-ttu-id="16439-107">[Início rápido de anfitrião do Windows PowerShell](./windows-powershell-host-quickstart.md) fornece instruções e exemplos de código para ajudá-lo à criação de aplicativos host.</span><span class="sxs-lookup"><span data-stu-id="16439-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="16439-108">[Criação de espaços de execução](./creating-runspaces.md) um conjunto de tópicos que explicam como criar espaços de execução para executar o comando do Windows PowerShell num aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="16439-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="16439-109">[Adicionar e invocar comandos](./adding-and-invoking-commands.md) explica como criar e executar um pipeline de comando na sua aplicação anfitriã....</span><span class="sxs-lookup"><span data-stu-id="16439-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="16439-110">[Criação de espaços de execução remotos](./creating-remote-runspaces.md) Expains como ligar um espaço de execução para um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="16439-110">[Creating remote runspaces](./creating-remote-runspaces.md) Expains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="16439-111">[Criando uma interface do usuário personalizada](./creating-a-custom-user-interface.md) Introduces personalizadas do utilizador interfaces e fornece ligações para exemplos.</span><span class="sxs-lookup"><span data-stu-id="16439-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="16439-112">[Exemplos de aplicações de anfitrião](./host-application-samples.md) esta secção inclui exemplos de aplicativos host completo.</span><span class="sxs-lookup"><span data-stu-id="16439-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="16439-113">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="16439-113">See Also</span></span>

[<span data-ttu-id="16439-114">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="16439-114">Windows PowerShell</span></span>](http://msdn.microsoft.com/en-us/b41a2af3-aec1-402d-8e18-c2c26be461ff)