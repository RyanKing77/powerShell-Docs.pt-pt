---
title: Como atribuir um nome um ficheiro CAB de ajuda Atualizável | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 23303489372cfe7e036fdea842ae75f7e47503c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850513"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="1bd21-102">How to Name an Updatable Help CAB File (Como Atribuir um Nome a um Ficheiro CAB de Ajuda Atualizável)</span><span class="sxs-lookup"><span data-stu-id="1bd21-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="1bd21-103">Este tópico explica o formato de nome necessário para o ficheiro de ajuda Atualizável cab (. Ficheiros CAB).</span><span class="sxs-lookup"><span data-stu-id="1bd21-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="1bd21-104">How to Name an Updatable Help CAB File (Como Atribuir um Nome a um Ficheiro CAB de Ajuda Atualizável)</span><span class="sxs-lookup"><span data-stu-id="1bd21-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="1bd21-105">Atualizável é um ficheiro CAB (. Arquivo CAB) tem de ter um nome com o seguinte formato.</span><span class="sxs-lookup"><span data-stu-id="1bd21-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="1bd21-106">Seguem-se os elementos do nome.</span><span class="sxs-lookup"><span data-stu-id="1bd21-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="1bd21-107">ModuleName o valor do **Name** propriedade da **ModuleInfo** de objeto que o [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet devolve.</span><span class="sxs-lookup"><span data-stu-id="1bd21-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>
<span data-ttu-id="1bd21-108">O valor do **Name** propriedade da **ModuleInfo** de objeto que o [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet devolve.</span><span class="sxs-lookup"><span data-stu-id="1bd21-108">The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="1bd21-109">ModuleGUID o valor do **GUID** chave no manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="1bd21-109">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="1bd21-110">Cultura de UICulture o da interface do Usuário de arquivos de ajuda no ficheiro CAB.</span><span class="sxs-lookup"><span data-stu-id="1bd21-110">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="1bd21-111">Este valor tem de corresponder ao valor de um da **UICulture** elementos no arquivo XML de HelpInfo para o módulo.</span><span class="sxs-lookup"><span data-stu-id="1bd21-111">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="1bd21-112">Por exemplo, se o nome do módulo "TestModule", o GUID de módulo é 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 e a cultura da interface do Usuário é "en-US", o nome do ficheiro CAB seria:</span><span class="sxs-lookup"><span data-stu-id="1bd21-112">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`