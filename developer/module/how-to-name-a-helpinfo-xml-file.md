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
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794812"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="a35c5-102">How to Name a HelpInfo XML File (Como Atribuir um Nome a um Ficheiro XML HelpInfo)</span><span class="sxs-lookup"><span data-stu-id="a35c5-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="a35c5-103">Este tópico explica o formato de nome necessário para os ficheiros de informações de ajuda Atualizável, comumente conhecido como arquivos HelpInfo XML.</span><span class="sxs-lookup"><span data-stu-id="a35c5-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="a35c5-104">How to Name a HelpInfo XML File (Como Atribuir um Nome a um Ficheiro XML HelpInfo)</span><span class="sxs-lookup"><span data-stu-id="a35c5-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="a35c5-105">Um arquivo XML de HelpInfo tem de ter um nome com o seguinte formato.</span><span class="sxs-lookup"><span data-stu-id="a35c5-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="a35c5-106">Seguem-se os elementos do nome.</span><span class="sxs-lookup"><span data-stu-id="a35c5-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="a35c5-107">ModuleName o valor do **Name** propriedade da **ModuleInfo** de objeto que o [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet devolve.</span><span class="sxs-lookup"><span data-stu-id="a35c5-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="a35c5-108">ModuleGUID o valor do **GUID** chave no manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="a35c5-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="a35c5-109">Por exemplo, se o nome do módulo é "TestModule" e o GUID de módulo é 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, deve ser o nome do ficheiro XML de HelpInfo para o módulo:</span><span class="sxs-lookup"><span data-stu-id="a35c5-109">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`