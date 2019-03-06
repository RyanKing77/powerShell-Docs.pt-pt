---
title: Exemplo de código RunSpace05 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: b16ee45383059c52ce3433699c6b8d2120992431
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429572"
---
# <a name="runspace05-code-sample"></a>Runspace05 Code Sample (Código de Exemplo Runspace05)

Eis o código-fonte para o exemplo de Runspace05 descrita no [configurando RunspaceConfiguration de utilizar um espaço de execução](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2). Este exemplo mostra como criar as informações de configuração de espaço de execução, criar um espaço de execução, criar um pipeline com um único comando e, em seguida, executar o pipeline. O comando executado é o `Get-Process` cmdlet.

> [!NOTE]
> Pode transferir o C# ficheiro de origem (runspace05.cs) com o Microsoft Windows Software Development Kit para Windows Vista e o Microsoft .NET Framework 3.0 Runtime Components. Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.

## <a name="code-sample"></a>Exemplo de código

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a>Veja Também

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)