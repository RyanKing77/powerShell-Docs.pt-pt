---
title: A pedir a confirmação de Cmdlets | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConfirmImpact [PowerShell Programmer's Guide], described
- ShouldContinue [PowerShell Programmer's Guide], described
- user feedback [PowerShell Programmer's Guide], requesting
- ShouldProcess [PowerShell Programmer's Guide], described
- ConfirmPreference [PowerShell Programmer's Guide], described
ms.assetid: 37d6e87f-57b7-40bd-b645-392cf0b6e88e
caps.latest.revision: 13
ms.openlocfilehash: 0c0517ef7fbd5ae6434773a2dfe276f3a8c35f39
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057410"
---
# <a name="requesting-confirmation-from-cmdlets"></a>Requesting Confirmation from Cmdlets (Pedir Confirmação a Partir de Cmdlets)

Cmdlets deve pedir confirmação quando estiverem prestes a fazer uma alteração no sistema que está fora do ambiente do Windows PowerShell. Por exemplo, se um cmdlet está prestes a adicionar uma conta de utilizador ou parar um processo, o cmdlet deve pedir confirmação do usuário antes que ele prossiga. Por outro lado, se um cmdlet está prestes a alterar uma variável do Windows PowerShell, o cmdlet não é necessário pedir confirmação.

Para fazer um pedido de confirmação, o cmdlet tem de indicar que ele oferece suporte a pedidos de confirmação, e ela deve chamar o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos (opcionais) para exibir uma mensagem de pedido de confirmação.

## <a name="supporting-confirmation-requests"></a>Pedidos de confirmação de suporte

Para suportar pedidos de confirmação, o cmdlet tem de definir o `SupportsShouldProcess` parâmetro do atributo Cmdlet para `true`. Isto permite que o `Confirm` e `WhatIf` parâmetros de cmdlet que são fornecidos pelo Windows PowerShell. O `Confirm` parâmetro permite que o utilizador controle se o pedido de confirmação é apresentado. O `WhatIf` parâmetro permite que o utilizador determinar se o cmdlet deve exibir uma mensagem ou executar sua ação. Não adicione manualmente os `Confirm` e `WhatIf` parâmetros para um cmdlet.

O exemplo seguinte mostra uma declaração de atributo do Cmdlet que suporta pedidos de confirmação.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>Chamar os métodos de pedido de confirmação

No código de cmdlet, chamar o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método antes da operação que altera o sistema é executada. O cmdlet de design, de modo que, se a chamada retorna um valor de `false`, não é possível efetuar a operação e o cmdlet processa a operação seguinte.

## <a name="calling-the-shouldcontinue-method"></a>Chamando o método de ShouldContinue

A maioria dos cmdlets pedir a confirmação usando apenas o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método. No entanto, alguns casos poderão requerer confirmação adicional. Nesses casos, complementar o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamar com uma chamada para o [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método. Isso permite que o cmdlet ou o fornecedor mais lhe controlar o âmbito do **Sim para todos** resposta ao pedido de confirmação.

Se um cmdlet chama o [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método, o cmdlet também tem de fornecer um `Force` mudar o parâmetro. Se o utilizador Especifica `Force` quando o usuário invoca o cmdlet, o cmdlet ainda deve chamar [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess), mas ele deve ignorar a chamada para [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) lançará uma exceção quando é chamado de um ambiente de não-interativa em que o utilizador não pode ser pedido. Adicionar um `Force` parâmetro garante que o comando ainda pode ser executado quando é invocado num ambiente de não-interativa.

O exemplo seguinte mostra como chamar [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

O comportamento de um [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamada pode variar dependendo do ambiente em que o cmdlet é invocado. Utilizando as diretrizes anteriores ajudará a garantir que o cmdlet se comporta de forma consistente com outros cmdlets, independentemente do ambiente de host.

Para obter um exemplo de chamar o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método, consulte [como pedir confirmações](./how-to-request-confirmations.md).

## <a name="specify-the-impact-level"></a>Especifique o nível de impacto

Quando cria o cmdlet, especifique o nível de impacto (a gravidade) da alteração. Para tal, defina o valor da `ConfirmImpact` parâmetro do atributo Cmdlet para alta, média ou baixa. Pode especificar um valor para `ConfirmImpact` apenas se também especificar o `SupportsShouldProcess` parâmetro para o cmdlet.

Para a maioria dos cmdlets, não é necessário especificar explicitamente `ConfirmImpact`.  Em alternativa, utilize a predefinição do parâmetro, que é médio. Se definir `ConfirmImpact` para alta, a operação será confirmada por predefinição. Reserve esta definição para ações altamente problemáticos, como reformatar um volume de disco rígido.

## <a name="calling-non-confirmation-methods"></a>Chamando métodos de não confirmação

Se o cmdlet ou o fornecedor deve enviar uma mensagem, mas não solicitar confirmação, pode chamar os três métodos seguintes. Evite utilizar o [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método para enviar mensagens de um desses tipos porque [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) saída é interligada com a saída normal do seu cmdlet ou o fornecedor, que dificulta a escrita de script.

- Caution o usuário e continuar com a operação, o cmdlet ou o fornecedor pode chamar o [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método.

- Para fornecer informações adicionais que o utilizador pode obter utilizando o `Verbose` parâmetro, o cmdlet ou o fornecedor pode chamar o [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método.

- Para fornecer detalhes no nível de depuração para outros desenvolvedores ou para o suporte do produto, o cmdlet ou o fornecedor pode chamar o [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método. O utilizador pode obter esta informação utilizando o `Debug` parâmetro.

Cmdlets e provedores primeiro de chamar os métodos seguintes para pedir confirmação antes de tentar efetuar uma operação que altera um sistema fora do Windows PowerShell:

- [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

Eles fazem-lo ao chamar o [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método, que pede ao utilizador para confirmar a operação com base em como o utilizador invocar o comando.

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
