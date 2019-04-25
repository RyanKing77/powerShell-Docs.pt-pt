---
title: Exemplo de código RunSpace07 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: 064e7d7ea2ee173bbcdd75a9f3a6c12582afe17b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081296"
---
# <a name="runspace07-code-sample"></a>Runspace07 Code Sample (Código de Exemplo Runspace07)

Eis o código-fonte para o exemplo de Runspace07 descrito em [criar uma aplicação que adiciona comandos da consola para um Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e). Este aplicativo de exemplo cria um espaço de execução, cria um pipeline, adiciona dois comandos para o pipeline e, em seguida, executa o pipeline. Os comandos adicionados ao pipeline são os `Get-Process` e `Measure-Object` cmdlets.

> [!NOTE]
> Pode transferir o C# arquivo de origem (runspace07.cs) usando o Microsoft Windows Software Development Kit para Windows Vista e o Microsoft .NET Framework 3.0 Runtime componentes. Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.

## <a name="code-sample"></a>Exemplo de código

[!code-csharp[Runspace07.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a>Veja Também

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)