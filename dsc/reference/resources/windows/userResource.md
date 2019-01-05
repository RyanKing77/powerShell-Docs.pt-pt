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
# <a name="dsc-user-resource"></a><span data-ttu-id="2100e-103">Recurso de utilizador de DSC</span><span class="sxs-lookup"><span data-stu-id="2100e-103">DSC User Resource</span></span>

<span data-ttu-id="2100e-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2100e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="2100e-105">O **utilizador** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir contas de utilizador local no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="2100e-105">The **User** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="2100e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2100e-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="2100e-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="2100e-107">Properties</span></span>

|  <span data-ttu-id="2100e-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="2100e-108">Property</span></span>  |  <span data-ttu-id="2100e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="2100e-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="2100e-110">UserName</span><span class="sxs-lookup"><span data-stu-id="2100e-110">UserName</span></span>| <span data-ttu-id="2100e-111">Indica o nome da conta para o qual pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="2100e-111">Indicates the account name for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="2100e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="2100e-112">Description</span></span>| <span data-ttu-id="2100e-113">Indica a descrição que pretende utilizar para a conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="2100e-113">Indicates the description you want to use for the user account.</span></span>|
| <span data-ttu-id="2100e-114">Desativada</span><span class="sxs-lookup"><span data-stu-id="2100e-114">Disabled</span></span>| <span data-ttu-id="2100e-115">Indica se a conta está ativada.</span><span class="sxs-lookup"><span data-stu-id="2100e-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="2100e-116">Defina esta propriedade como `$true` para se certificar de que esta conta está desativada e defini-lo como `$false` para se certificar de que está ativada.</span><span class="sxs-lookup"><span data-stu-id="2100e-116">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span>|
| <span data-ttu-id="2100e-117">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="2100e-117">Ensure</span></span>| <span data-ttu-id="2100e-118">Indica se a conta existe.</span><span class="sxs-lookup"><span data-stu-id="2100e-118">Indicates if the account exists.</span></span> <span data-ttu-id="2100e-119">Definir esta propriedade para "Presente" para se certificar de que a conta existe e defini-lo como "Ausente", certifique-se de que a conta não existe.</span><span class="sxs-lookup"><span data-stu-id="2100e-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="2100e-120">FullName</span><span class="sxs-lookup"><span data-stu-id="2100e-120">FullName</span></span>| <span data-ttu-id="2100e-121">Representa uma cadeia de caracteres com o nome completo que pretende utilizar para a conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="2100e-121">Represents a string with the full name you want to use for the user account.</span></span>|
| <span data-ttu-id="2100e-122">Palavra-passe</span><span class="sxs-lookup"><span data-stu-id="2100e-122">Password</span></span>| <span data-ttu-id="2100e-123">Indica a palavra-passe que pretende utilizar para esta conta.</span><span class="sxs-lookup"><span data-stu-id="2100e-123">Indicates the password you want to use for this account.</span></span> |
| <span data-ttu-id="2100e-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="2100e-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="2100e-125">Indica se o utilizador pode alterar a palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="2100e-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="2100e-126">Defina esta propriedade como `$true` para se certificar de que o utilizador não é possível alterar a palavra-passe e defini-lo como `$false` para permitir que o utilizador altere a palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="2100e-126">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="2100e-127">O valor predefinido é `$false`.</span><span class="sxs-lookup"><span data-stu-id="2100e-127">The default value is `$false`.</span></span>|
| <span data-ttu-id="2100e-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="2100e-128">PasswordChangeRequired</span></span>| <span data-ttu-id="2100e-129">Indica se o utilizador tem de alterar a palavra-passe no próximo início de sessão.</span><span class="sxs-lookup"><span data-stu-id="2100e-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="2100e-130">Defina esta propriedade como `$true` se o utilizador tem de alterar a palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="2100e-130">Set this property to `$true` if the user must change the password.</span></span> <span data-ttu-id="2100e-131">O valor predefinido é `$true`.</span><span class="sxs-lookup"><span data-stu-id="2100e-131">The default value is `$true`.</span></span>|
| <span data-ttu-id="2100e-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="2100e-132">PasswordNeverExpires</span></span>| <span data-ttu-id="2100e-133">Indica se a palavra-passe irá expirar.</span><span class="sxs-lookup"><span data-stu-id="2100e-133">Indicates if the password will expire.</span></span> <span data-ttu-id="2100e-134">Para se certificar de que a palavra-passe para esta conta nunca irá expirar, defina esta propriedade como `$true`e defina-o como `$false` se a palavra-passe expirar.</span><span class="sxs-lookup"><span data-stu-id="2100e-134">To ensure that the password for this account will never expire, set this property to `$true`, and set it to `$false` if the password will expire.</span></span> <span data-ttu-id="2100e-135">O valor predefinido é `$false`.</span><span class="sxs-lookup"><span data-stu-id="2100e-135">The default value is `$false`.</span></span>|
| <span data-ttu-id="2100e-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="2100e-136">DependsOn</span></span> | <span data-ttu-id="2100e-137">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="2100e-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2100e-138">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será **ResourceName** e seu tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="2100e-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="2100e-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2100e-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```