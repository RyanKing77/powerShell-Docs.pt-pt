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
# <a name="how-to-name-a-helpinfo-xml-file"></a>How to Name a HelpInfo XML File (Como Atribuir um Nome a um Ficheiro XML HelpInfo)

Este tópico explica o formato de nome necessário para os ficheiros de informações de ajuda Atualizável, comumente conhecido como arquivos HelpInfo XML.

## <a name="how-to-name-a-helpinfo-xml-file"></a>How to Name a HelpInfo XML File (Como Atribuir um Nome a um Ficheiro XML HelpInfo)

Um arquivo XML de HelpInfo tem de ter um nome com o seguinte formato.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

Seguem-se os elementos do nome.

ModuleName o valor do **Name** propriedade da **ModuleInfo** de objeto que o [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet devolve.

ModuleGUID o valor do **GUID** chave no manifesto do módulo.

Por exemplo, se o nome do módulo é "TestModule" e o GUID de módulo é 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, deve ser o nome do ficheiro XML de HelpInfo para o módulo:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`