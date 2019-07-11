---
title: Exemplo de código RunSpace09 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: 1a21af4b48a414d9c9fee57871eacb0a39c9ab11
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734907"
---
# <a name="runspace09-code-sample"></a>Runspace09 Code Sample (Código de Exemplo Runspace09)

Eis o código-fonte para o exemplo de Runspace09 descrito em [criação de uma consola de aplicação que invoca um Pipeline de forma assíncrona](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47). Este aplicativo de exemplo cria e abre um espaço de execução, cria e assincronamente invoca um pipeline, e, em seguida, utiliza pipeline de eventos para processar o script de forma assíncrona. O script que é executado por esta aplicação cria números inteiros de 1 a 10 em intervalos de 0,5 segundo (500 ms).

## <a name="code-sample"></a>Exemplo de código

[!code-csharp[Runspace09.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a>Veja Também

[SDK do Windows PowerShell](../windows-powershell-reference.md)