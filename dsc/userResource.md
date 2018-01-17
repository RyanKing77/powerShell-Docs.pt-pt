---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recurso de utilizador de DSC
ms.openlocfilehash: c1b8487d9adc899950d185036ada3a2fa3747417
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
#<a name="dsc-user-resource"></a>Recursos de DSC utilizador #

 
>Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0


O __utilizador__ recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir contas de utilizador local no nó de destino.


##<a name="syntax"></a>Sintaxe # #

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
| UserName| Indica o nome de conta para o qual pretende garantir um estado específico.| 
| Descrição| Indica a descrição que pretende utilizar para a conta de utilizador.| 
| Desativado| Indica se a conta está ativada. Defina esta propriedade como __$true__ para se certificar de que esta conta está desativada e defina-o como __$false__ para se certificar de que está ativada.| 
| Certifique-se| Indica se a conta existe. Definir esta propriedade para "Presente" para garantir que a conta existe e defina-o para "Ausente", certifique-se de que a conta não existe.| 
| FullName| Representa uma cadeia com o nome completo que pretende utilizar para a conta de utilizador.| 
| Palavra-passe| Indica a palavra-passe que pretende utilizar para esta conta. | 
| PasswordChangeNotAllowed| Indica se o utilizador pode alterar a palavra-passe. Defina esta propriedade como __$true__ para se certificar de que o utilizador não é possível alterar a palavra-passe e defina-o como __$false__ para permitir ao utilizador alterar a palavra-passe. O valor predefinido é __$false__.| 
| PasswordChangeRequired| Indica se o utilizador tem de alterar a palavra-passe no próximo início de sessão. Defina esta propriedade como __$true__ se o utilizador tem de alterar a palavra-passe. O valor predefinido é __$true__.| 
| PasswordNeverExpires| Indica se a palavra-passe expira. Para se certificar de que a palavra-passe para esta conta nunca irá expirar, defina esta propriedade como __$true__e defina-o como __$false__ se a palavra-passe expira. O valor predefinido é __$false__.| 
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.| 

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

