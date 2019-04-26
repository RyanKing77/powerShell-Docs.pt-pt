---
title: Criação de espaços de execução | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082945"
---
# <a name="creating-runspaces"></a><span data-ttu-id="a71cf-102">Creating Runspaces (Criar Espaços de Execução)</span><span class="sxs-lookup"><span data-stu-id="a71cf-102">Creating Runspaces</span></span>

<span data-ttu-id="a71cf-103">Um espaço de execução é o ambiente operacional para os comandos que são invocados por um aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="a71cf-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="a71cf-104">Esse ambiente inclui os comandos e dados que estão atualmente presentes e as restrições de idioma que se aplicam-se atualmente.</span><span class="sxs-lookup"><span data-stu-id="a71cf-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="a71cf-105">Alojar aplicações podem utilizar o espaço de execução padrão fornecido pelo Windows PowerShell, que inclui todos os comandos de núcleos disponíveis, ou criar um espaço de execução personalizado que inclui apenas um subconjunto dos comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a71cf-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="a71cf-106">Para criar um espaço de execução personalizado, crie uma [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) de objeto e atribuí-la ao seu espaço de execução.</span><span class="sxs-lookup"><span data-stu-id="a71cf-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="a71cf-107">Espaço de execução tarefas</span><span class="sxs-lookup"><span data-stu-id="a71cf-107">Runspace tasks</span></span>

1. [<span data-ttu-id="a71cf-108">Criar um InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="a71cf-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="a71cf-109">Criar um espaço de execução restrito</span><span class="sxs-lookup"><span data-stu-id="a71cf-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="a71cf-110">Criação de vários espaços de execução</span><span class="sxs-lookup"><span data-stu-id="a71cf-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="a71cf-111">Veja Também</span><span class="sxs-lookup"><span data-stu-id="a71cf-111">See Also</span></span>
