---
title: Exemplos de anfitrião personalizado | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 2d88847e17371c4c04b783569fbd983218b6791b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848644"
---
# <a name="custom-host-samples"></a>Custom Host Samples (Exemplos de Anfitriões Personalizados)

Esta secção inclui código de exemplo para a escrita de um host personalizado. Pode utilizar o Microsoft Visual Studio para criar uma aplicação de consola e, em seguida, copie o código os tópicos nesta secção para seu aplicativo host.

## <a name="in-this-section"></a>Nesta Secção

 [Exemplo de Host01](./host01-sample.md) este exemplo mostra como implementar um aplicativo de host que usa um host personalizado básico.

 [Exemplo de Host02](./host02-sample.md) este exemplo mostra como escrever um aplicativo de host que usa o tempo de execução do Windows PowerShell, juntamente com uma implementação de anfitrião personalizado. O aplicativo host define a cultura de anfitrião para o alemão, execuções a [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet e apresenta os resultados à medida que veria-los usando pwrsh.exe e, em seguida, imprime os dados atuais e a hora em alemão.
Este exemplo mostra como escrever um aplicativo de host que usa o tempo de execução do Windows PowerShell, juntamente com uma implementação de anfitrião personalizado. O aplicativo host define a cultura de anfitrião para o alemão, execuções a [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet e apresenta os resultados à medida que veria-los usando pwrsh.exe e, em seguida, imprime os dados atuais e a hora em alemão.

 [Exemplo de Host03](./host03-sample.md) este exemplo mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console.

 [Exemplo de Host04](./host04-sample.md) este exemplo mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console. Este aplicativo de host também suporta a apresentação de pedidos que permitem ao usuário especificar várias opções.

 [Exemplo de Host05](./host05-sample.md) este exemplo mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console. Este aplicativo de host também oferece suporte a chamadas para computadores remotos utilizando o [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) e [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets este exemplo mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console. Este aplicativo de host também oferece suporte a chamadas para computadores remotos utilizando o [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) e [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets

 [Exemplo de Host06](./host06-sample.md) este exemplo mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console. Além disso, este exemplo utiliza as APIs de atomizador para especificar a cor do texto que é introduzido pelo utilizador.

## <a name="see-also"></a>Consulte Também
