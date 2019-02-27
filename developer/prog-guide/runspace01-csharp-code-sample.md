---
title: Runspace01 (C#) exemplo de código | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 2f1839d1ba578cdfe97f60c741c84b0a57f1d8f6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845564"
---
# <a name="runspace01-c-code-sample"></a>Runspace01 (C#) Code Sample (Código de Exemplo Runspace01 [C#])

Seguem-se exemplos de código para o espaço de execução descrito em [criar uma aplicação de consola execuções para que um comando especificado](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e). Para fazer isso, o aplicativo invoca um espaço de execução e, em seguida, invoca um comando. (Tenha em atenção que esta aplicação não especifica informações de configuração de espaço de execução nem -lo explicitamente cria um pipeline). O comando invocado é o `Get-Process` cmdlet.
Seguem-se exemplos de código para o espaço de execução descrito em [criar uma aplicação de consola execuções para que um comando especificado](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e). Para fazer isso, o aplicativo invoca um espaço de execução e, em seguida, invoca um comando. (Tenha em atenção que esta aplicação não especifica informações de configuração de espaço de execução nem -lo explicitamente cria um pipeline). O comando invocado é o `Get-Process` cmdlet.

> [!NOTE]
> Pode transferir o C# ficheiro de origem (runspace01.cs) para este espaço de execução usando o Microsoft Windows Software Development Kit para Windows Vista e o Microsoft .NET Framework 3.0 Runtime Components. Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
> Pode transferir o C# ficheiro de origem (runspace01.cs) para este espaço de execução usando o Microsoft Windows Software Development Kit para Windows Vista e o Microsoft .NET Framework 3.0 Runtime Components. Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.

## <a name="code-sample"></a>Exemplo de código

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a>Veja Também

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)