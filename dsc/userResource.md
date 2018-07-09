---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso de utilizador de DSC
ms.openlocfilehash: 04543351df19160a2da05ccea96e5d392d8c55bf
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892530"
---
# <a name="dsc-user-resource"></a><span data-ttu-id="9ee47-103">Recurso de utilizador de DSC</span><span class="sxs-lookup"><span data-stu-id="9ee47-103">DSC User Resource</span></span>

<span data-ttu-id="9ee47-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9ee47-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="9ee47-105">O **utilizador** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir contas de utilizador local no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="9ee47-105">The **User** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="9ee47-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ee47-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="9ee47-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="9ee47-107">Properties</span></span>

|  <span data-ttu-id="9ee47-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="9ee47-108">Property</span></span>  |  <span data-ttu-id="9ee47-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ee47-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="9ee47-110">UserName</span><span class="sxs-lookup"><span data-stu-id="9ee47-110">UserName</span></span>| <span data-ttu-id="9ee47-111">Indica o nome da conta para o qual pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="9ee47-111">Indicates the account name for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="9ee47-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ee47-112">Description</span></span>| <span data-ttu-id="9ee47-113">Indica a descrição que pretende utilizar para a conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="9ee47-113">Indicates the description you want to use for the user account.</span></span>|
| <span data-ttu-id="9ee47-114">Desativado</span><span class="sxs-lookup"><span data-stu-id="9ee47-114">Disabled</span></span>| <span data-ttu-id="9ee47-115">Indica se a conta está ativada.</span><span class="sxs-lookup"><span data-stu-id="9ee47-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="9ee47-116">Defina esta propriedade como `$true` para se certificar de que esta conta está desativada e defini-lo como `$false` para se certificar de que está ativada.</span><span class="sxs-lookup"><span data-stu-id="9ee47-116">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span>|
| <span data-ttu-id="9ee47-117">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="9ee47-117">Ensure</span></span>| <span data-ttu-id="9ee47-118">Indica se a conta existe.</span><span class="sxs-lookup"><span data-stu-id="9ee47-118">Indicates if the account exists.</span></span> <span data-ttu-id="9ee47-119">Definir esta propriedade para "Presente" para se certificar de que a conta existe e defini-lo como "Ausente", certifique-se de que a conta não existe.</span><span class="sxs-lookup"><span data-stu-id="9ee47-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="9ee47-120">FullName</span><span class="sxs-lookup"><span data-stu-id="9ee47-120">FullName</span></span>| <span data-ttu-id="9ee47-121">Representa uma cadeia de caracteres com o nome completo que pretende utilizar para a conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="9ee47-121">Represents a string with the full name you want to use for the user account.</span></span>|
| <span data-ttu-id="9ee47-122">Palavra-passe</span><span class="sxs-lookup"><span data-stu-id="9ee47-122">Password</span></span>| <span data-ttu-id="9ee47-123">Indica a palavra-passe que pretende utilizar para esta conta.</span><span class="sxs-lookup"><span data-stu-id="9ee47-123">Indicates the password you want to use for this account.</span></span> |
| <span data-ttu-id="9ee47-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="9ee47-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="9ee47-125">Indica se o utilizador pode alterar a palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="9ee47-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="9ee47-126">Defina esta propriedade como `$true` para se certificar de que o utilizador não é possível alterar a palavra-passe e defini-lo como `$false` para permitir que o utilizador altere a palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="9ee47-126">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="9ee47-127">O valor predefinido é `$false`.</span><span class="sxs-lookup"><span data-stu-id="9ee47-127">The default value is `$false`.</span></span>|
| <span data-ttu-id="9ee47-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="9ee47-128">PasswordChangeRequired</span></span>| <span data-ttu-id="9ee47-129">Indica se o utilizador tem de alterar a palavra-passe no próximo início de sessão.</span><span class="sxs-lookup"><span data-stu-id="9ee47-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="9ee47-130">Defina esta propriedade como `$true` se o utilizador tem de alterar a palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="9ee47-130">Set this property to `$true` if the user must change the password.</span></span> <span data-ttu-id="9ee47-131">O valor predefinido é `$true`.</span><span class="sxs-lookup"><span data-stu-id="9ee47-131">The default value is `$true`.</span></span>|
| <span data-ttu-id="9ee47-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="9ee47-132">PasswordNeverExpires</span></span>| <span data-ttu-id="9ee47-133">Indica se a palavra-passe irá expirar.</span><span class="sxs-lookup"><span data-stu-id="9ee47-133">Indicates if the password will expire.</span></span> <span data-ttu-id="9ee47-134">Para se certificar de que a palavra-passe para esta conta nunca irá expirar, defina esta propriedade como `$true`e defina-o como `$false` se a palavra-passe expirar.</span><span class="sxs-lookup"><span data-stu-id="9ee47-134">To ensure that the password for this account will never expire, set this property to `$true`, and set it to `$false` if the password will expire.</span></span> <span data-ttu-id="9ee47-135">O valor predefinido é `$false`.</span><span class="sxs-lookup"><span data-stu-id="9ee47-135">The default value is `$false`.</span></span>|
| <span data-ttu-id="9ee47-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="9ee47-136">DependsOn</span></span> | <span data-ttu-id="9ee47-137">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="9ee47-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="9ee47-138">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será **ResourceName** e seu tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="9ee47-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="9ee47-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ee47-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```