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
# <a name="how-to-name-a-helpinfo-xml-file"></a>How to Name a HelpInfo XML File (Como Atribuir um Nome a um Ficheiro XML HelpInfo)

Este tópico explica o formato de nome necessário para os ficheiros de informações de ajuda Atualizável, comumente conhecido como arquivos HelpInfo XML.

## <a name="how-to-name-a-helpinfo-xml-file"></a>How to Name a HelpInfo XML File (Como Atribuir um Nome a um Ficheiro XML HelpInfo)

Um arquivo XML de HelpInfo tem de ter um nome com o seguinte formato.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

Seguem-se os elementos do nome.

ModuleName o valor do **Name** propriedade da **ModuleInfo** de objeto que o [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet devolve.
O valor do **Name** propriedade da **ModuleInfo** de objeto que o [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet devolve.

ModuleGUID o valor do **GUID** chave no manifesto do módulo.

Por exemplo, se o nome do módulo é "TestModule" e o GUID de módulo é 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, deve ser o nome do ficheiro XML de HelpInfo para o módulo:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`