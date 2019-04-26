---
title: Exemplo de código RunSpace08 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 1a09cfee3bb317de6c1ca4dde86a87d72a498e6e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081279"
---
# <a name="runspace08-code-sample"></a>Runspace08 Code Sample (Código de Exemplo Runspace08)

Eis o código-fonte para o exemplo de Runspace08 descrito em [criar uma aplicação que adiciona parâmetros da consola a um comando](http://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba). Este aplicativo de exemplo cria um espaço de execução, cria um pipeline, adiciona dois comandos para o pipeline, adiciona dois parâmetros para o segundo comando e, em seguida, executa o pipeline. Os comandos que são adicionados ao pipeline são os `Get-Process` e `Sort-Object` cmdlets.

## <a name="code-sample"></a>Exemplo de código

[!code-csharp[Runspace08.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a>Veja Também

[SDK do Windows PowerShell](../windows-powershell-reference.md)