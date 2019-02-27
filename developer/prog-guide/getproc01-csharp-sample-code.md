---
title: GetProc01 (C#) o código de exemplo | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 56ce7080e24cc12de6d43ac607ffd5d3f0a3b17c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847433"
---
# <a name="getproc01-c-sample-code"></a>GetProc01 (C#) Sample Code (Código de Exemplo GetProc01 [C#])

O código a seguir mostra a implementação do cmdlet de exemplo GetProc01. Tenha em atenção que o cmdlet é simplificado, deixando o trabalho real de obtenção de processo para o [System.Diagnostics.Process.Getprocesses*](/dotnet/api/System.Diagnostics.Process.GetProcesses) método.

> [!NOTE]
> Pode transferir o C# ficheiro de origem (getproc01.cs) para este cmdlet de Get-Proc usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components. Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
> Pode transferir o C# ficheiro de origem (getproc01.cs) para este cmdlet de Get-Proc usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components. Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.

## <a name="code-sample"></a>Exemplo de código

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a>Veja Também

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)