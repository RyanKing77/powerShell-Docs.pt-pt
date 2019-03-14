---
title: Declaração de atributo de credenciais | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 1513d340cdadc5cb7622e791cc3c163ff39dfe1d
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795407"
---
# <a name="credential-attribute-declaration"></a>Credential Attribute Declaration (Declaração do Atributo Credential)

O atributo de credencial é um atributo opcional que pode ser utilizado com parâmetros de credencial do tipo [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) para que uma cadeia de caracteres também pode ser passada como um argumento para o parâmetro. Quando esse atributo é adicionado a uma declaração de parâmetro, o Windows PowerShell converte a entrada de cadeia de caracteres num [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto. Por exemplo, o [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet utiliza este atributo para ter o PowerShell de Windows gerar a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto devolvido pelo cmdlet.

## <a name="syntax"></a>Sintaxe

```csharp
[Credential]
```

## <a name="remarks"></a>Observações

- Normalmente, este atributo é utilizado por parâmetros do tipo [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) para que uma cadeia de caracteres também pode ser passada como um argumento para o parâmetro. Quando um [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto é passado para o parâmetro, o Windows PowerShell não faz nada.

- Ao criar o [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto, o Windows PowerShell utiliza o anfitrião atual para exibir as instruções adequadas para o usuário. Por exemplo, a predefinição o Host apresenta um aviso para um nome de utilizador e palavra-passe quando este atributo é utilizado. No entanto, se está a ser utilizado um host personalizado que define uma linha de comandos diferente, em seguida, seria exibida nessa linha de comandos.

- Este atributo é utilizado com o atributo de parâmetro. Para obter mais informações sobre esse atributo, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).

- O atributo de credencial é definido pela [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) classe.

## <a name="see-also"></a>Veja Também

[Aliases de parâmetro](./parameter-aliases.md)

[Declaração de atributo de parâmetro](./parameter-attribute-declaration.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
