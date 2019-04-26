---
title: Exibindo informações de erro | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068288"
---
# <a name="displaying-error-information"></a><span data-ttu-id="5e2b4-102">Displaying Error Information (Apresentar Informações de Erros)</span><span class="sxs-lookup"><span data-stu-id="5e2b4-102">Displaying Error Information</span></span>

<span data-ttu-id="5e2b4-103">Este tópico aborda as formas em que os utilizadores podem apresentar informações sobre o erro.</span><span class="sxs-lookup"><span data-stu-id="5e2b4-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="5e2b4-104">Quando seu cmdlet encontra um erro, a apresentação das informações de erro será, por predefinição, assemelhar-se a seguinte saída de erro.</span><span class="sxs-lookup"><span data-stu-id="5e2b4-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="5e2b4-105">No entanto, os utilizadores podem ver erros por categoria, definindo a `$ErrorView` variável à `"CategoryView"`.</span><span class="sxs-lookup"><span data-stu-id="5e2b4-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="5e2b4-106">Vista de categoria apresenta informações específicas do registo de erro, em vez de uma descrição de texto livre do erro.</span><span class="sxs-lookup"><span data-stu-id="5e2b4-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="5e2b4-107">Esta vista pode ser útil se tiver uma longa lista de erros para analisar.</span><span class="sxs-lookup"><span data-stu-id="5e2b4-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="5e2b4-108">Na vista de categorias, a mensagem de erro anterior é apresentada da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="5e2b4-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="5e2b4-109">Para obter mais informações sobre as categorias de erro, consulte [registos de erros do Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="5e2b4-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5e2b4-110">Veja Também</span><span class="sxs-lookup"><span data-stu-id="5e2b4-110">See Also</span></span>

[<span data-ttu-id="5e2b4-111">Registos de erro do PowerShell do Windows</span><span class="sxs-lookup"><span data-stu-id="5e2b4-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="5e2b4-112">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e2b4-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
