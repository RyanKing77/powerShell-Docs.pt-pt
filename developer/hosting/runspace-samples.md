---
title: Exemplos de espaço de execução | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c92a6d3d-8d34-4a76-bdc3-dea923d9858e
caps.latest.revision: 17
ms.openlocfilehash: e24d40746da91f60aaf2af655ddcadc88ab6a4db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082741"
---
# <a name="runspace-samples"></a>Runspace Samples (Exemplos de Espaços de Execução)

Esta secção inclui código de exemplo que mostra como utilizar diferentes tipos de espaços de execução para executar comandos de modo síncrono e assíncrono. Pode utilizar o Microsoft Visual Studio para criar uma aplicação de consola e, em seguida, copie o código os tópicos nesta secção para seu aplicativo host.

## <a name="in-this-section"></a>Nesta Secção

> [!NOTE]
> Para exemplos de aplicativos de host que criam interfaces de anfitrião personalizado, consulte [exemplos de anfitrião personalizado](./custom-host-samples.md).

 [Exemplo de Runspace01](./runspace01-sample.md) este exemplo mostra como utilizar o [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe para executar o [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet forma síncrona e Exibe sua saída num console janela.

 [Exemplo de Runspace02](./runspace02-sample.md) este exemplo mostra como utilizar o [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe para executar o [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) e [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) Cmdlets de forma síncrona. Os resultados desses comandos são apresentadas utilizando um [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) controle.

 [Exemplo de Runspace03](./runspace03-sample.md) este exemplo mostra como utilizar o [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe para executar um script de forma síncrona e como lidar com erros de não terminação. O script recebe uma lista de nomes de processo e, em seguida, obtém esses processos. Os resultados do script, incluindo quaisquer erros de não terminação de mensagens em fila que foram gerados ao executar o script, são exibidos numa janela de consola.

 [Exemplo de Runspace04](./runspace04-sample.md) este exemplo mostra como utilizar o [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe para executar comandos e como erros de terminação de catch que forem lançadas. quando executar os comandos. Dois comandos são executados, e o último comando é passado um argumento de parâmetro que não é válido. Como resultado, não existem objetos são devolvidos e um erro de terminação é lançado.

 [Exemplo de Runspace05](./runspace05-sample.md) este exemplo mostra como adicionar um snap-in para uma [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) de objeto para que o cmdlet do snap-in está disponível quando o espaço de execução é aberto. O snap-in fornece um cmdlet de Get-Proc (definido pela [exemplo de GetProcessSample01](../cmdlet/getprocesssample01-sample.md)) que é executado de forma síncrona com um [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.

 [Exemplo de Runspace06](./runspace06-sample.md) este exemplo mostra como adicionar um módulo para uma [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) de objeto para que o módulo é carregado quando o espaço de execução é aberto. O módulo fornece um cmdlet de Get-Proc (definido pela [exemplo GetProcessSample02](../cmdlet/getprocesssample02-sample.md)) que é executado de forma síncrona usando um [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.

 [Exemplo de Runspace07](./runspace07-sample.md) este exemplo mostra como criar um espaço de execução e, em seguida, utilizar esse espaço de execução para executar dois cmdlets de forma síncrona ao utilizar um [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.

 [Exemplo de Runspace08](./runspace08-sample.md) este exemplo mostra como adicionar comandos e argumentos para o pipeline de uma [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto e como executar os comandos de forma síncrona.

 [Exemplo de Runspace09](./runspace09-sample.md) este exemplo mostra como adicionar um script para o pipeline de uma [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto e como executar o script de forma assíncrona. Eventos são usados para manipular a saída do script.

 [Exemplo de Runspace10](./runspace10-sample.md) este exemplo mostra como criar um Estado de sessão inicial padrão, como adicionar um cmdlet para o [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), como criar um espaço de execução que utiliza o Estado de sessão inicial e como executar o comando utilizando um [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.

 [Exemplo de Runspace11](./runspace11-sample.md) isso mostra como utilizar o [System.Management.Automation.Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand) classe para criar um comando de proxy que chama um cmdlet existente, mas restringe o conjunto de parâmetros. O comando de proxy, em seguida, é adicionado a um Estado de sessão inicial que é utilizado para criar um espaço de execução restrito. Isso significa que o usuário pode acessar a funcionalidade do cmdlet apenas através do comando de proxy.

## <a name="see-also"></a>Veja Também
