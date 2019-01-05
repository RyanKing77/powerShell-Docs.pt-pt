---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso de utilizador de DSC
ms.openlocfilehash: 04543351df19160a2da05ccea96e5d392d8c55bf
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048817"
---
# <a name="dsc-user-resource"></a>Recurso de utilizador de DSC

Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O **utilizador** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir contas de utilizador local no nó de destino.

## <a name="syntax"></a>Sintaxe

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| UserName| Indica o nome da conta para o qual pretende garantir um estado específico.|
| Descrição| Indica a descrição que pretende utilizar para a conta de utilizador.|
| Desativada| Indica se a conta está ativada. Defina esta propriedade como `$true` para se certificar de que esta conta está desativada e defini-lo como `$false` para se certificar de que está ativada.|
| Certifique-se| Indica se a conta existe. Definir esta propriedade para "Presente" para se certificar de que a conta existe e defini-lo como "Ausente", certifique-se de que a conta não existe.|
| FullName| Representa uma cadeia de caracteres com o nome completo que pretende utilizar para a conta de utilizador.|
| Palavra-passe| Indica a palavra-passe que pretende utilizar para esta conta. |
| PasswordChangeNotAllowed| Indica se o utilizador pode alterar a palavra-passe. Defina esta propriedade como `$true` para se certificar de que o utilizador não é possível alterar a palavra-passe e defini-lo como `$false` para permitir que o utilizador altere a palavra-passe. O valor predefinido é `$false`.|
| PasswordChangeRequired| Indica se o utilizador tem de alterar a palavra-passe no próximo início de sessão. Defina esta propriedade como `$true` se o utilizador tem de alterar a palavra-passe. O valor predefinido é `$true`.|
| PasswordNeverExpires| Indica se a palavra-passe irá expirar. Para se certificar de que a palavra-passe para esta conta nunca irá expirar, defina esta propriedade como `$true`e defina-o como `$false` se a palavra-passe expirar. O valor predefinido é `$false`.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será **ResourceName** e seu tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exemplo

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```