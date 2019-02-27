---
title: Declaração de atributo de cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlet attribute, described
- attributes, Cmdlet
- Cmdlet attribute
ms.assetid: 1d323332-f773-4c0e-8a69-2aada765afb2
caps.latest.revision: 12
ms.openlocfilehash: 2bc03aaade1f18d48f65ecf5f9ee437ffaf07f92
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56852011"
---
# <a name="cmdlet-attribute-declaration"></a>Cmdlet Attribute Declaration (Declaração do Atributo Cmdlet)

O atributo de Cmdlet identifica uma classe de Microsoft .NET Framework como um cmdlet e especifica o verbo e substantivo usado para invocar o cmdlet.

## <a name="syntax"></a>Sintaxe

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>Parâmetros

`VerbName` ([System. String](/dotnet/api/System.String)) necessária. Especifica o verbo do cmdlet. Esse verbo especifica a ação tomada pelo cmdlet. Para obter mais informações sobre verbos aprovados cmdlet, consulte [nomes de verbo do Cmdlet](./approved-verbs-for-windows-powershell-commands.md) e [diretrizes de desenvolvimento necessário](./required-development-guidelines.md).

`NounName` ([System. String](/dotnet/api/System.String)) necessária. Especifica o substantivo do cmdlet. Este substantivo Especifica os recursos que o cmdlet age sobre. Para obter mais informações sobre nomes de cmdlet, consulte [declaração de Cmdlet](./cmdlet-class-declaration.md) e [incentivada diretrizes de desenvolvimento altamente](./strongly-encouraged-development-guidelines.md).

`SupportsShouldProcess` ([Boolean](/dotnet/api/System.Boolean)) opcional chamado de parameter. `True` indica que o cmdlet oferece suporte a chamadas para o [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método, que permite ao cmdlet uma forma de solicitar ao utilizador antes de realizar uma ação que o sistema é executada. `False`, o valor predefinido, indica que o cmdlet não oferece suporte a chamadas para o [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método. Para obter mais informações sobre pedidos de confirmação, consulte [pedir confirmação](./requesting-confirmation-from-cmdlets.md).

`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) opcional chamado de parameter. Especifica quando a ação do cmdlet deve ser confirmada por uma chamada para o [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método. [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) só pode ser chamado quando o valor de ConfirmImpact do cmdlet (por predefinição, médio) é igual ou superior ao valor da `$ConfirmPreference` variável. Este parâmetro deve ser especificado apenas quando o `SupportsShouldProcess` parâmetro for especificado.

`DefaultParameterSetName` ([System. String](/dotnet/api/System.String)) opcional chamado de parameter. Especifica que o parâmetro predefinido definida que o tempo de execução do Windows PowerShell tenta utilizar quando ele não é possível determinar qual parâmetro definido para utilizar. Tenha em atenção que esta situação pode ser eliminada, tornando o parâmetro exclusivo de cada parâmetro definido um parâmetro obrigatório.

Há um caso onde o Windows PowerShell não é possível utilizar o parâmetro de padrão definido, mesmo se for especificado um nome de conjunto de parâmetro padrão. O tempo de execução do Windows PowerShell não é possível distinguir entre conjuntos de parâmetros com base exclusivamente no tipo de objeto. Por exemplo, se tiver um conjunto de parâmetros que aceita uma cadeia de caracteres como o caminho do ficheiro e outro conjunto que usa um **FileInfo** objeto diretamente, Windows PowerShell não é possível determinar qual parâmetro definido para utilizar com base nos valores passados para o cmdlet, nem usa o conjunto de parâmetros padrão. Neste caso, mesmo que especifique o que nome do conjunto de um parâmetro predefinido, o Windows PowerShell gera uma mensagem de erro do conjunto de parâmetro ambígua.

`SupportsTransactions` ([Boolean](/dotnet/api/System.Boolean)) opcional chamado de parameter. `True` indica que o cmdlet pode ser utilizado dentro de uma transação. Quando `True` for especificado, o tempo de execução do Windows PowerShell adiciona o `UseTransaction` parâmetro para a lista de parâmetros do cmdlet. `False`, o valor predefinido, indica que o cmdlet não pode ser utilizado dentro de uma transação.

## <a name="remarks"></a>Observações

- Juntos, o verbo e substantivo são utilizados para identificar o seu cmdlet registado e invocar o cmdlet dentro de um script.

- Quando o cmdlet é invocado a partir da consola do Windows PowerShell, o comando é parecido com o seguinte comando:

**VerbName-NounName**

- Todos os cmdlets que alteram recursos fora do Windows PowerShell deve incluir o `SupportsShouldProcess` palavra-chave quando for declarado o atributo de Cmdlet, que permite que o cmdlet chame o [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método antes do cmdlet executa a ação. Se o [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamar devolve `false`, a ação não deve ser executada. Para obter mais informações sobre os pedidos de confirmação geradas pela [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamar, consulte [pedir confirmação](./requesting-confirmation-from-cmdlets.md).

O `Confirm` e `WhatIf` parâmetros do cmdlet estão disponíveis apenas para cmdlets que suportam [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamadas.

## <a name="example"></a>Exemplo

A seguinte definição de classe usa o atributo de Cmdlet para identificar a classe do .NET Framework para um **Get-Proc** cmdlet obtém informação sobre os processos em execução no computador local.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Para obter mais informações sobre o **Get-Proc** cmdlet, consulte [GetProc Tutorial](./getproc-tutorial.md).

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
