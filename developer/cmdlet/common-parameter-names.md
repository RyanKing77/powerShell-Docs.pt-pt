---
title: Os nomes de parâmetros comuns | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0db9f54c-4014-4450-9e81-c9f5fe562a0e
caps.latest.revision: 12
ms.openlocfilehash: c65deeda6b2ef1b52de55035dc606259a7f2d232
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059665"
---
# <a name="common-parameter-names"></a>Common Parameter Names (Nomes de Parâmetros Comuns)

Os parâmetros descritos neste tópico são denominados *parâmetros comuns de*. Eles são adicionados a cmdlets pelo tempo de execução do Windows PowerShell e não podem ser declarados pelo cmdlet.

> [!NOTE]
> Esses parâmetros também são adicionados aos cmdlets de fornecedor e às funções que são decoradas com o `CmdletBinding` atributo.

## <a name="general-common-parameters"></a>Parâmetros comuns de geral

Os parâmetros seguintes são adicionados a todos os cmdlets e podem ser acedidos sempre que o cmdlet é executado. Esses parâmetros são definidos pelos [System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters) classe.

### <a name="debug-alias-db"></a>Depurar (alias: db)

Tipo de dados: SwitchParameter

Este parâmetro especifica se a depuração de nível de Programador de mensagens que podem ser apresentados na linha de comandos. Essas mensagens destinam-se para a operação do cmdlet de resolução de problemas e são geradas por chamadas para o [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método. Mensagens de depuração não precisam ser localizadas.

### <a name="erroraction-alias-ea"></a>ErrorAction (alias: ea)

Tipo de dados: Enumeração

Este parâmetro especifica a ação que terá lugar quando ocorre um erro. Os valores possíveis para este parâmetro são definidos pelos [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) enumeração.

### <a name="errorvariable-alias-ev"></a>ErrorVariable (alias: ev)

Tipo de dados: Cadeia (de carateres)

Este parâmetro especifica a variável no qual posicionar objetos quando ocorre um erro. Para anexar a essa variável, utilize +*varname* em vez de limpeza e definir a variável.

### <a name="outvariable-alias-ov"></a>OutVariable (alias: ov)

Tipo de dados: Cadeia (de carateres)

Este parâmetro especifica a variável na qual vai colocar todos os resultados objetos gerado pelo cmdlet. Para anexar a essa variável, utilize +*varname* em vez de limpeza e definir a variável.

### <a name="outbuffer-alias-ob"></a>OutBuffer (alias: ob)

Tipo de dados: Int32

Este parâmetro define o número de objetos para armazenar na memória intermédia de saída antes de todos os objetos são passados pelo pipeline. Por predefinição, os objetos são transmitidos imediatamente pelo pipeline.

### <a name="verbose-alias-vb"></a>Verboso (alias: vb)

Tipo de dados: SwitchParameter

Este parâmetro especifica se o cmdlet escreve explicativo mensagens que podem ser apresentadas na linha de comandos. Essas mensagens foram concebidas para fornecer ajuda adicional para o usuário e são geradas por chamadas para o [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método.

### <a name="warningaction-alias-wa"></a>WarningAction (alias: wa)

Tipo de dados: Enumeração

Este parâmetro especifica a ação que deverão ocorrer quando o cmdlet escreve uma mensagem de aviso. Os valores possíveis para este parâmetro são definidos pelos [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) enumeração.

### <a name="warningvariable-alias-wv"></a>WarningVariable (alias: wv)

Tipo de dados: Cadeia (de carateres)

Este parâmetro especifica a variável na qual as mensagens de aviso podem ser guardadas. Para anexar a essa variável, utilize +*varname* em vez de limpeza e definir a variável.

## <a name="risk-mitigation-parameters"></a>Parâmetros de mitigação de riscos

Os parâmetros seguintes são adicionados a cmdlets que pede a confirmação antes de realizar sua ação. Para obter mais informações sobre pedidos de confirmação, consulte [pedir confirmação](./requesting-confirmation-from-cmdlets.md). Esses parâmetros são definidos pelos [System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters) classe.

### <a name="confirm-alias-cf"></a>Confirmar (alias: cf)

Tipo de dados: SwitchParameter

Este parâmetro especifica se o cmdlet apresenta um aviso que pede-lhe se o utilizador é tem a certeza de que pretende continuar.

### <a name="whatif-alias-wi"></a>WhatIf (alias: wi)

Tipo de dados: SwitchParameter

Este parâmetro especifica se o cmdlet escreve uma mensagem que descreve os efeitos de executar o cmdlet sem realmente executar qualquer ação.

## <a name="transaction-parameters"></a>Parâmetros de transação

O parâmetro seguinte é adicionado aos cmdlets que suporte a transações. Esses parâmetros são definidos pelos [System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters) classe.

### <a name="usetransaction-alias-usetx"></a>UseTransaction (alias: usetx)

Tipo de dados: SwitchParameter

Este parâmetro especifica se o cmdlet irá utilizar a transação atual para executar sua ação.

## <a name="see-also"></a>Veja Também

[System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
