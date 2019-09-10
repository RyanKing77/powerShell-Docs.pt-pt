---
title: Exemplo deC#código RunSpace03 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 9afdb97b8ae2919f091ca5bacccedbe37c2e1584
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848037"
---
# <a name="runspace03-c-code-sample"></a>Runspace03 (C#) Code Sample (Código de Exemplo Runspace03 [C#])

Este é o C# código-fonte do aplicativo de console descrito em "criando um aplicativo de console que executa um script especificado". Este exemplo usa a classe [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) para executar um script que recupera informações de processo usando a lista de nomes de processo passados para o script. Ele mostra como passar objetos de entrada para um script e como recuperar objetos de erro, bem como os objetos de saída.

> [!NOTE]
> Você pode baixar o C# arquivo de origem (runspace03.cs) para este exemplo usando os componentes de tempo de execução do Microsoft Windows Software Development Kit para Windows Vista e Microsoft .NET Framework 3,0. Para obter instruções de download, consulte [como instalar o Windows PowerShell e baixar o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
> Os arquivos de origem baixados estão disponíveis no diretório de  **\<exemplos do PowerShell >** .

## <a name="code-sample"></a>Exemplo de código

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a>Veja Também

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)