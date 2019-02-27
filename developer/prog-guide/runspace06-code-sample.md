---
title: Exemplo de código RunSpace06 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: 2874f9df3f5166fbe14deb5b128674540c0d6701
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845438"
---
# <a name="runspace06-code-sample"></a>Runspace06 Code Sample (Código de Exemplo Runspace06)

Eis o código-fonte para o exemplo de Runspace06 descrito em [configurando um espaço de execução usando um Snap-in do PowerShell Windows](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83). Este aplicativo de exemplo cria um espaço de execução com base num snap-in Windows PowerShell, que, em seguida, é utilizado para executar um pipeline com um único comando. Para fazer isso, o aplicativo cria as informações de configuração de espaço de execução, cria um espaço de execução, cria um pipeline com um único comando e, em seguida, executa o pipeline.

> [!NOTE]
> Pode transferir o C# ficheiro de origem (runspace06.cs) com o Windows Software Development Kit para Windows Vista e o Microsoft .NET Framework 3.0 Runtime Components. Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
> Pode transferir o C# ficheiro de origem (runspace06.cs) com o Windows Software Development Kit para Windows Vista e o Microsoft .NET Framework 3.0 Runtime Components. Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.

## <a name="code-sample"></a>Exemplo de código

[!code-csharp[Runspace06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a>Veja Também

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)