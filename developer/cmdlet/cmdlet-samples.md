---
title: Exemplos de cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: 0fa4a5f804586c51ae6a36121f9aab041b0989cc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068457"
---
# <a name="cmdlet-samples"></a>Cmdlet Samples (Exemplos de Cmdlets)

Esta secção descreve o código de exemplo que é fornecido no Windows PowerShell 2.0 SDK. Pode copiar o código dos tópicos nesta secção, ou abra os arquivos de origem instalados com o SDK. O [Windows PowerShell 2.0 Software Development Kit (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560) fornece ficheiros Leia-me, arquivos de origem e arquivos de projeto do Visual Studio para cada exemplo. Com o SDK instalado, pode encontrar exemplos sob o `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` pasta.

## <a name="in-this-section"></a>Nesta Secção

[Exemplo de GetProcessSample01](./getprocesssample01-sample.md) este exemplo mostra como escrever um cmdlet que obtém os processos no computador local.

[Exemplo de GetProcessSample02](./getprocesssample02-sample.md) este exemplo mostra como escrever um cmdlet que obtém os processos no computador local. Ele fornece um parâmetro de nome que pode ser utilizado para especificar os processos a serem obtidas.

[Exemplo de GetProcessSample03](./getprocesssample03-sample.md) este exemplo mostra como escrever um cmdlet que obtém os processos no computador local. Ele fornece um parâmetro de nome que pode aceitar um objeto do pipeline ou um valor de uma propriedade de um objeto cujo nome de propriedade é o mesmo que o nome do parâmetro.

[Exemplo de GetProcessSample04](./getprocesssample04-sample.md) este exemplo mostra como escrever um cmdlet que obtém os processos no computador local. Gera um erro de não terminação se ocorrer um erro ao obter um processo.

[Exemplo de GetProcessSample05](./getprocesssample05-sample.md) este exemplo mostra uma versão completa do cmdlet Get-Proc.

[Exemplo de StopProcessSample01](./stopprocesssample01-sample.md) este exemplo mostra como escrever um cmdlet que solicita tais comentários do usuário antes de ele tenta parar um processo e como implementar um `PassThru` parâmetro que indica que o usuário quer o cmdlet devolver uma objeto.

[Exemplo de StopProcessSample02](./stopprocesssample02-sample.md) este exemplo mostra como escrever um cmdlet que escreve as mensagens de aviso e de depuração, verbosa, ao parar os processos no computador local.

[Exemplo de StopProcessSample03](./stopprocesssample03-sample.md) este exemplo mostra como escrever um cmdlet cujos parâmetros têm aliases e que suporta carateres universais.

[Exemplo de StopProcessSample04](./stopprocesssample04-sample.md) este exemplo mostra como escrever um cmdlet que declara conjuntos de parâmetros, especifica o parâmetro predefinido definido e pode aceitar um objeto de entrada.

[Exemplo de Events01](./events01-sample.md) este exemplo mostra como criar um cmdlet que permite ao utilizador para se registrar para eventos gerados pelo [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher). Com este cmdlet os utilizadores podem, por exemplo, registar uma ação a executar quando é criado um ficheiro num diretório específico. Este exemplo deriva de [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) classe base.

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
