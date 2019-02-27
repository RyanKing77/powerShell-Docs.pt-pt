---
title: Módulos e Snap-ins | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849960"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="d078e-102">Modules and Snap-ins (Módulos e Snap-ins)</span><span class="sxs-lookup"><span data-stu-id="d078e-102">Modules and Snap-ins</span></span>

<span data-ttu-id="d078e-103">Cmdlets podem ser adicionados a uma sessão através de módulos (introduzidos pelo Windows PowerShell 2.0) ou do snap-ins. Assim que o cmdlet é adicionado à sessão que pode ser executado por meio de programação por um aplicativo host ou interativamente na linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="d078e-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="d078e-104">Recomendamos que utilize módulos como o método de entrega para a adição de cmdlets para uma sessão pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="d078e-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="d078e-105">Módulos permitem que adicione cmdlets ao carregar o assembly onde o cmdlet é definido.</span><span class="sxs-lookup"><span data-stu-id="d078e-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="d078e-106">Não é necessário implementar uma classe de snap-in.</span><span class="sxs-lookup"><span data-stu-id="d078e-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="d078e-107">Módulos permitem-lhe adicionar outros recursos, como variáveis, funções, scripts, tipos e formatação ficheiros e muito mais.</span><span class="sxs-lookup"><span data-stu-id="d078e-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="d078e-108">Snap-ins pode ser utilizados apenas para adicionar os cmdlets e provedores à sessão.</span><span class="sxs-lookup"><span data-stu-id="d078e-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="d078e-109">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="d078e-109">See Also</span></span>

[<span data-ttu-id="d078e-110">Escrever um módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d078e-110">Writing a Windows PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

[<span data-ttu-id="d078e-111">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d078e-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
