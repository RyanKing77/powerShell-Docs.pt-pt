---
title: Aliases de cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849967"
---
# <a name="cmdlet-aliases"></a>Cmdlet Aliases (Aliases de Cmdlets)

Pode utilizar o cmdlet aliases para melhorar a experiência de utilizador do cmdlet. Pode adicionar aliases para cmdlets usados com freqüência para reduzir a digitação e para facilitar a concluir as tarefas rapidamente. Pode incluir aliases incorporados nos seus cmdlets ou os utilizadores possam definir seus próprios aliases personalizados.

Por exemplo, o [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet tem um incorporado `gcm` alias. Também pode usar aliases para adicionar nomes de comandos a partir de outras linguagens, para que os usuários não precisam aprender novos comandos.

## <a name="alias-guidelines"></a>Diretrizes de alias

Ao criar aliases incorporadas para os cmdlets, siga estas diretrizes:

- Antes de atribuir aliases, inicie o Windows PowerShell e, em seguida, execute o [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet para ver os aliases que já estão a ser utilizados.

- Inclua um prefixo de alias que referencia o verbo do nome do cmdlet e um sufixo de alias que referencia o substantivo do nome do cmdlet. Por exemplo, o alias para o `Import-Module` cmdlet é "ipmo". Para obter uma lista de todos os verbos e seus aliases, consulte [verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

- Para cmdlets que têm o mesmo verbo, incluem o mesmo prefixo de alias. Por exemplo, os aliases para todos os cmdlets do Windows PowerShell que têm o verbo "Get" no respetivo nome utilizam o prefixo "g".

- Para cmdlets que têm o mesmo substantivo, incluem o mesmo sufixo de alias. Por exemplo, os aliases para todos os cmdlets do Windows PowerShell que tenham o substantivo "Session" no respetivo nome utilizam o sufixo "sn".

- Para cmdlets que são equivalentes aos comandos em outros idiomas, utilize o nome do comando.

- Em geral, verifique aliases o mais curtos possível. Certifique-se de que o alias tem pelo menos um caráter distinto para o verbo e um caráter de distinto para o substantivo. Adicione mais carateres, conforme necessário para que o alias exclusivo.

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
