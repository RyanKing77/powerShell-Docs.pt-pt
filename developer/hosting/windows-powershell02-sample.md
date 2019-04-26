---
title: Exemplo do Windows PowerShell02 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082520"
---
# <a name="windows-powershell02-sample"></a>Windows PowerShell02 Sample (Exemplo Windows PowerShell02)

Este exemplo mostra como executar comandos de forma assíncrona utilizando os espaços de execução de um conjunto de espaço de execução. O exemplo gera uma lista de comandos e, em seguida, executa esses comandos, enquanto o motor do Windows PowerShell abre um espaço de execução do conjunto, quando for necessário.

## <a name="requirements"></a>Requisitos

- Este exemplo requer o Windows PowerShell 2.0.

## <a name="demonstrates"></a>Demonstra

Este exemplo demonstra o seguinte:

- Criar um objeto de RunspacePool com um número mínimo e máximo de espaços de execução pode ser aberto ao mesmo tempo.

- Criar uma lista de comandos.

- Executar os comandos de forma assíncrona.

- Chamar o [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) método para ver o número de espaços de execução são gratuitos.

- Capturar a saída do comando com o [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) método.

## <a name="example"></a>Exemplo

Este exemplo mostra como abrir os espaços de execução de um conjunto de espaço de execução e como as de forma assíncrona executar comandos esses espaços de execução.

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a>Veja Também

[Escrever um aplicativo de Host de PowerShell do Windows](./writing-a-windows-powershell-host-application.md)