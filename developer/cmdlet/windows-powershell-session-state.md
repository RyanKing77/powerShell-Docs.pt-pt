---
title: Estado de sessão do Windows PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059546"
---
# <a name="windows-powershell-session-state"></a>Windows PowerShell Session State (Estado da Sessão do Windows PowerShell)

Estado da sessão refere-se para a configuração atual de uma sessão do Windows PowerShell ou o módulo. Uma sessão do Windows PowerShell é o ambiente operacional que é utilizado de forma interativa pelo utilizador da linha de comandos ou por meio de programação por um aplicativo host. O estado da sessão para uma sessão é referido como o estado da sessão global.

Da perspectiva do desenvolvedor, refere-se uma sessão do Windows PowerShell para o tempo entre quando um aplicativo host é aberto um espaço de execução do Windows PowerShell e quando ele fecha o espaço de execução. Observado outra forma, a sessão é o tempo de vida de uma instância do motor do PowerShell de Windows que é invocada enquanto o espaço de execução existe.

## <a name="module-session-state"></a>Estado da sessão de módulo

Estados de sessão do módulo são criados sempre que o módulo ou um dos respectivos módulos aninhados é importado para a sessão. Quando um módulo exporta um elemento como um cmdlet, função ou script, uma referência a esse elemento é adicionada para o estado da sessão global da sessão. No entanto, quando o elemento é executado, ele é executado dentro do Estado da sessão do módulo.

## <a name="session-state-data"></a>Dados de estado da sessão

Dados de estado da sessão podem ser público ou privado. Dados públicos estão disponíveis para chamadas a partir de fora o estado da sessão, enquanto os dados privados só estão disponíveis para chamadas a partir do Estado da sessão. Por exemplo, um módulo pode ter uma função privada que pode ser chamada apenas pelo módulo ou apenas internamente por um elemento público que tenha sido exportado. Isso é semelhante para os membros privados e públicos de um tipo de .NET Framework.

Dados de estado da sessão são armazenados por instância atual do motor de execução dentro do contexto da sessão atual do Windows PowerShell. Dados de estado da sessão inclui os seguintes itens:

- Informações de caminho

- Informações da unidade

- Informações do fornecedor de Windows PowerShell

- Informações sobre as referências para os elementos de módulo (por exemplo, cmdlets, funções e scripts) que são exportados pelo módulo e módulos importados. Estas informações e estas referências são para o estado da sessão global apenas.

- Informações de variáveis de estado da sessão

## <a name="accessing-session-state-data-within-cmdlets"></a>Aceder aos dados de estado da sessão dentro de Cmdlets

Cmdlets podem aceder a dados de estado da sessão ou indiretamente através do [System.Management.Automation.PSCmdlet.Sessionstate*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) propriedade da classe cmdlet ou diretamente através do [ System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) classe. O [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) classe fornece propriedades que podem ser utilizadas para investigar os diferentes tipos de dados de estado da sessão.

## <a name="see-also"></a>Veja Também

[System.Management.Automation.PSCmdlet.Sessionstate](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[System.Management.Automation.Sessionstate?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.SessionState)

[Cmdlets do Windows PowerShell](./cmdlet-overview.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Shell do Windows PowerShell SDK](../windows-powershell-reference.md)
