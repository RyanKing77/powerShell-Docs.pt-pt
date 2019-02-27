---
title: Exemplos do Windows PowerShell API | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850156"
---
# <a name="windows-powershell-api-samples"></a>Windows PowerShell API Samples (Exemplos de APIs do Windows PowerShell)

Esta secção inclui código de exemplo que mostra como criar espaços de execução que restringem a funcionalidade e como executar assincronamente comandos ao utilizar um conjunto de espaço de execução para fornecer os espaços de execução. Pode utilizar o Microsoft Visual Studio para criar uma aplicação de consola e, em seguida, copie o código os tópicos nesta secção para seu aplicativo host.

## <a name="in-this-section"></a>Nesta Secção

[Exemplo de PowerShell01](./windows-powershell01-sample.md) este exemplo mostra como usar um [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto para limitar a funcionalidade de um espaço de execução. A saída deste exemplo demonstra como restringir o modo de idioma do espaço de execução, como marcar um cmdlet como particular, como adicionar e remover cmdlets e fornecedores, como adicionar um comando de proxy e muito mais.

[Exemplo de PowerShell02](./windows-powershell02-sample.md) este exemplo mostra como executar comandos de forma assíncrona utilizando os espaços de execução de um conjunto de espaço de execução. O exemplo gera uma lista de comandos e, em seguida, executa esses comandos, enquanto o motor do Windows PowerShell abre um espaço de execução do conjunto, quando for necessário.