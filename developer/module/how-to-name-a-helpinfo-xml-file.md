---
title: Como atribuir um nome um arquivo XML de HelpInfo | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: a3e8ae664d5c0e29d0f84174950bebe6a1da6a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848091"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="22bc2-102">How to Name a HelpInfo XML File (Como Atribuir um Nome a um Ficheiro XML HelpInfo)</span><span class="sxs-lookup"><span data-stu-id="22bc2-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="22bc2-103">Este tópico explica o formato de nome necessário para os ficheiros de informações de ajuda Atualizável, comumente conhecido como arquivos HelpInfo XML.</span><span class="sxs-lookup"><span data-stu-id="22bc2-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="22bc2-104">How to Name a HelpInfo XML File (Como Atribuir um Nome a um Ficheiro XML HelpInfo)</span><span class="sxs-lookup"><span data-stu-id="22bc2-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="22bc2-105">Um arquivo XML de HelpInfo tem de ter um nome com o seguinte formato.</span><span class="sxs-lookup"><span data-stu-id="22bc2-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="22bc2-106">Seguem-se os elementos do nome.</span><span class="sxs-lookup"><span data-stu-id="22bc2-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="22bc2-107">ModuleName o valor do **Name** propriedade da **ModuleInfo** de objeto que o [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet devolve.</span><span class="sxs-lookup"><span data-stu-id="22bc2-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>
<span data-ttu-id="22bc2-108">O valor do **Name** propriedade da **ModuleInfo** de objeto que o [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet devolve.</span><span class="sxs-lookup"><span data-stu-id="22bc2-108">The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="22bc2-109">ModuleGUID o valor do **GUID** chave no manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="22bc2-109">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="22bc2-110">Por exemplo, se o nome do módulo é "TestModule" e o GUID de módulo é 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, deve ser o nome do ficheiro XML de HelpInfo para o módulo:</span><span class="sxs-lookup"><span data-stu-id="22bc2-110">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`