---
title: Os utilizadores pedir confirmação | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067226"
---
# <a name="users-requesting-confirmation"></a>Users Requesting Confirmation (Confirmação Pedida por Utilizadores)

Quando especificar um valor de `true` para o `SupportsShouldProcess` parâmetro da declaração de atributo do Cmdlet, os utilizadores podem especificar o `Confirm` parâmetro no prompt de comando.

No ambiente predefinido, os utilizadores podem especificar a `Confirm` parâmetro ou `"-Confirm:$true` , de modo a que for solicitada a confirmação quando o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método é chamado. Isso ignora [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) pedidos de confirmação, mesmo para operações de alto impacto.

Se `Confirm` não for especificado, o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamada pede a confirmação se o `$ConfirmPreference` variável de preferência é igual ou maior do que o `ConfirmImpact` definição do cmdlet ou o fornecedor. A predefinição de `$ConfirmPreference` é alta. Portanto, no ambiente predefinido, apenas cmdlets e fornecedores que especificam uma ação de alto impacto pedir confirmação.

Se `Confirm` for false ou se `"-Confirm:$false` for especificado, o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamada pede a confirmação do usuário e o `$ConfirmPreference` variável de shell é ignorada.

## <a name="remarks"></a>Observações

- Para cmdlets e fornecedores que especificam `SupportsShouldProcess`, mas não `ConfirmImpact`, essas ações são processadas como ações de "impacto intermédio", e eles não pedirá por predefinição. O nível de impacto é menor do que a predefinição do `$ConfirmPreference` variável de preferência.

- Se o usuário especificar a `Verbose` parâmetro, este serão notificado de que a operação, mesmo que não são pedidas a confirmação.

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
