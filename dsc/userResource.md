---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Recurso de utilizador de DSC
ms.openlocfilehash: 1c3efa8e3bf945c45834cbea7ddb0a6c3ffc5f45
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
#<a name="dsc-user-resource"></a><span data-ttu-id="7f0d1-103">Recursos de DSC utilizador #</span><span class="sxs-lookup"><span data-stu-id="7f0d1-103">DSC User Resource#</span></span>


><span data-ttu-id="7f0d1-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7f0d1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="7f0d1-105">O __utilizador__ recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir contas de utilizador local no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="7f0d1-105">The __User__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>


##<a name="syntax"></a><span data-ttu-id="7f0d1-106">Sintaxe # #</span><span class="sxs-lookup"><span data-stu-id="7f0d1-106">Syntax##</span></span>

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

## <a name="properties"></a><span data-ttu-id="7f0d1-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="7f0d1-107">Properties</span></span>
|  <span data-ttu-id="7f0d1-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="7f0d1-108">Property</span></span>  |  <span data-ttu-id="7f0d1-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f0d1-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="7f0d1-110">UserName</span><span class="sxs-lookup"><span data-stu-id="7f0d1-110">UserName</span></span>| <span data-ttu-id="7f0d1-111">Indica o nome de conta para o qual pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="7f0d1-111">Indicates the account name for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="7f0d1-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f0d1-112">Description</span></span>| <span data-ttu-id="7f0d1-113">Indica a descrição que pretende utilizar para a conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="7f0d1-113">Indicates the description you want to use for the user account.</span></span>|
| <span data-ttu-id="7f0d1-114">Desativado</span><span class="sxs-lookup"><span data-stu-id="7f0d1-114">Disabled</span></span>| <span data-ttu-id="7f0d1-115">Indica se a conta está ativada.</span><span class="sxs-lookup"><span data-stu-id="7f0d1-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="7f0d1-116">Defina esta propriedade como __$true__ para se certificar de que esta conta está desativada e defina-o como __$false__ para se certificar de que está ativada.</span><span class="sxs-lookup"><span data-stu-id="7f0d1-116">Set this property to __$true__ to ensure that this account is disabled, and set it to __$false__ to ensure that it is enabled.</span></span>|
| <span data-ttu-id="7f0d1-117">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="7f0d1-117">Ensure</span></span>| <span data-ttu-id="7f0d1-118">Indica se a conta existe.</span><span class="sxs-lookup"><span data-stu-id="7f0d1-118">Indicates if the account exists.</span></span> <span data-ttu-id="7f0d1-119">Definir esta propriedade para "Presente" para garantir que a conta existe e defina-o para "Ausente", certifique-se de que a conta não existe.</span><span class="sxs-lookup"><span data-stu-id="7f0d1-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="7f0d1-120">FullName</span><span class="sxs-lookup"><span data-stu-id="7f0d1-120">FullName</span></span>| <span data-ttu-id="7f0d1-121">Representa uma cadeia com o nome completo que pretende utilizar para a conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="7f0d1-121">Represents a string with the full name you want to use for the user account.</span></span>|
| <span data-ttu-id="7f0d1-122">Palavra-passe</span><span class="sxs-lookup"><span data-stu-id="7f0d1-122">Password</span></span>| <span data-ttu-id="7f0d1-123">Indica a palavra-passe que pretende utilizar para esta conta.</span><span class="sxs-lookup"><span data-stu-id="7f0d1-123">Indicates the password you want to use for this account.</span></span> |
| <span data-ttu-id="7f0d1-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="7f0d1-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="7f0d1-125">Indica se o utilizador pode alterar a palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="7f0d1-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="7f0d1-126">Defina esta propriedade como __$true__ para se certificar de que o utilizador não é possível alterar a palavra-passe e defina-o como __$false__ para permitir ao utilizador alterar a palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="7f0d1-126">Set this property to __$true__ to ensure that the user cannot change the password, and set it to __$false__ to allow the user to change the password.</span></span> <span data-ttu-id="7f0d1-127">O valor predefinido é __$false__.</span><span class="sxs-lookup"><span data-stu-id="7f0d1-127">The default value is __$false__.</span></span>|
| <span data-ttu-id="7f0d1-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="7f0d1-128">PasswordChangeRequired</span></span>| <span data-ttu-id="7f0d1-129">Indica se o utilizador tem de alterar a palavra-passe no próximo início de sessão.</span><span class="sxs-lookup"><span data-stu-id="7f0d1-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="7f0d1-130">Defina esta propriedade como __$true__ se o utilizador tem de alterar a palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="7f0d1-130">Set this property to __$true__ if the user must change the password.</span></span> <span data-ttu-id="7f0d1-131">O valor predefinido é __$true__.</span><span class="sxs-lookup"><span data-stu-id="7f0d1-131">The default value is __$true__.</span></span>|
| <span data-ttu-id="7f0d1-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="7f0d1-132">PasswordNeverExpires</span></span>| <span data-ttu-id="7f0d1-133">Indica se a palavra-passe expira.</span><span class="sxs-lookup"><span data-stu-id="7f0d1-133">Indicates if the password will expire.</span></span> <span data-ttu-id="7f0d1-134">Para se certificar de que a palavra-passe para esta conta nunca irá expirar, defina esta propriedade como __$true__e defina-o como __$false__ se a palavra-passe expira.</span><span class="sxs-lookup"><span data-stu-id="7f0d1-134">To ensure that the password for this account will never expire, set this property to __$true__, and set it to __$false__ if the password will expire.</span></span> <span data-ttu-id="7f0d1-135">O valor predefinido é __$false__.</span><span class="sxs-lookup"><span data-stu-id="7f0d1-135">The default value is __$false__.</span></span>|
| <span data-ttu-id="7f0d1-136">dependsOn</span><span class="sxs-lookup"><span data-stu-id="7f0d1-136">DependsOn</span></span> | <span data-ttu-id="7f0d1-137">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="7f0d1-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7f0d1-138">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="7f0d1-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="7f0d1-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f0d1-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```