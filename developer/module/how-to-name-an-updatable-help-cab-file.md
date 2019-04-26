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
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082367"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>How to Name an Updatable Help CAB File (Como Atribuir um Nome a um Ficheiro CAB de Ajuda Atualizável)

Este tópico explica o formato de nome necessário para o ficheiro de ajuda Atualizável cab (. Ficheiros CAB).

## <a name="how-to-name-an-updatable-help-cab-file"></a>How to Name an Updatable Help CAB File (Como Atribuir um Nome a um Ficheiro CAB de Ajuda Atualizável)

Atualizável é um ficheiro CAB (. Arquivo CAB) tem de ter um nome com o seguinte formato.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

Seguem-se os elementos do nome.

ModuleName o valor do **Name** propriedade da **ModuleInfo** de objeto que o [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet devolve.

ModuleGUID o valor do **GUID** chave no manifesto do módulo.

Cultura de UICulture o da interface do Usuário de arquivos de ajuda no ficheiro CAB. Este valor tem de corresponder ao valor de um da **UICulture** elementos no arquivo XML de HelpInfo para o módulo.

Por exemplo, se o nome do módulo "TestModule", o GUID de módulo é 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 e a cultura da interface do Usuário é "en-US", o nome do ficheiro CAB seria:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`