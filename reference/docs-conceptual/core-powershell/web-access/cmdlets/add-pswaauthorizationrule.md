---
ms.topic: reference
keywords: PowerShell, o cmdlet
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: a8904ac36f7fd9fe3c649ad4ca709a98c31b63c3
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094233"
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="59340-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="59340-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="59340-104">SINOPSE</span><span class="sxs-lookup"><span data-stu-id="59340-104">SYNOPSIS</span></span>

<span data-ttu-id="59340-105">Adiciona uma nova regra de autorização para o conjunto de regras de autorização do Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="59340-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="59340-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59340-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="59340-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="59340-107">UserGroupNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="59340-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="59340-108">UserGroupNameComputerName</span></span>

```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="59340-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="59340-109">UserNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="59340-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="59340-110">UserNameComputerName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="59340-111">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="59340-111">DESCRIPTION</span></span>

<span data-ttu-id="59340-112">O **Add-PswaAuthorizationRule** cmdlet adiciona uma nova regra de autorização para o conjunto de regras de autorização do Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="59340-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="59340-113">Tem de especificar os utilizadores, computadores e pontos de extremidade do Windows PowerShell para esta regra.</span><span class="sxs-lookup"><span data-stu-id="59340-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="59340-114">Pode especificar utilizadores e computadores, contas de utilizador individuais e nomes de computador ou ao especificar grupos.</span><span class="sxs-lookup"><span data-stu-id="59340-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="59340-115">Para um computador que está associado a um domínio do Active Directory, o cmdlet utiliza o identificador de segurança (SID) do computador para criar a regra.</span><span class="sxs-lookup"><span data-stu-id="59340-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="59340-116">Isto permite-lhe utilizar um nome abreviado, um nome de domínio completamente qualificado (FQDN) ou um endereço IP para o **nome do computador** campo na página de início de sessão.</span><span class="sxs-lookup"><span data-stu-id="59340-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="59340-117">Para um computador que não está associado a um domínio do Active Directory, o cmdlet cria a regra com o nome do computador fornecido pelo administrador.</span><span class="sxs-lookup"><span data-stu-id="59340-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="59340-118">Para ligar com êxito a esta máquina, o utilizador final tem de fornecer o nome do computador exatamente como aparece na regra.</span><span class="sxs-lookup"><span data-stu-id="59340-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="59340-119">Se existirem vários computadores com o mesmo nome na rede, pode resolver nome abreviado para mais de um computador.</span><span class="sxs-lookup"><span data-stu-id="59340-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="59340-120">Isto pode levar a ambigüidade durante o estabelecimento de uma ligação.</span><span class="sxs-lookup"><span data-stu-id="59340-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="59340-121">Por exemplo, se existe uma regra para o computador de grupo de trabalho com o nome "*servidor1*" e um novo computador com o nome *server1.contoso.com* está associado à rede, usando as regras de autorização de validação é bem-sucedida e Windows PowerShell Web Access tenta estabelecer uma ligação para o computador com o nome "*servidor1*".</span><span class="sxs-lookup"><span data-stu-id="59340-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="59340-122">Não é garantido que a ligação é estabelecida com o computador de grupo de trabalho especificado; a tentativa de foi possível estabelecer o grupo de trabalho ou o computador de domínio com o nome "*servidor1*".</span><span class="sxs-lookup"><span data-stu-id="59340-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="59340-123">Para reduzir a ambiguidade, recomenda-se que utilize o FQDN para o computador de destino sempre que possível criar uma regra de autorização.</span><span class="sxs-lookup"><span data-stu-id="59340-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="59340-124">As regras de autorização avaliar a credencial primária início de sessão dos utilizadores do Windows PowerShell Web Access, não as credenciais alternativas (o segundo conjunto de credenciais encontrado no **definições de ligação opcionais** secção a página de entrada).</span><span class="sxs-lookup"><span data-stu-id="59340-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="59340-125">Para obter um exemplo disto, consulte o exemplo 6.</span><span class="sxs-lookup"><span data-stu-id="59340-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="59340-126">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="59340-126">Parameters</span></span>

### <a name="-computergroupname-string"></a><span data-ttu-id="59340-127">-ComputerGroupName \<cadeia\></span><span class="sxs-lookup"><span data-stu-id="59340-127">-ComputerGroupName \<String\></span></span>

<span data-ttu-id="59340-128">Especifica o nome de um grupo de computadores em serviços de domínio do Active Directory (AD DS) ou grupos locais para a qual esta regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="59340-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="59340-129">Aliases</span><span class="sxs-lookup"><span data-stu-id="59340-129">Aliases</span></span>                              | <span data-ttu-id="59340-130">nenhum</span><span class="sxs-lookup"><span data-stu-id="59340-130">none</span></span>                                 |
| <span data-ttu-id="59340-131">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="59340-131">Required?</span></span>                            | <span data-ttu-id="59340-132">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="59340-132">true</span></span>                                 |
| <span data-ttu-id="59340-133">Posição?</span><span class="sxs-lookup"><span data-stu-id="59340-133">Position?</span></span>                            | <span data-ttu-id="59340-134">com o nome</span><span class="sxs-lookup"><span data-stu-id="59340-134">named</span></span>                                |
| <span data-ttu-id="59340-135">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="59340-135">Default Value</span></span>                        | <span data-ttu-id="59340-136">nenhum</span><span class="sxs-lookup"><span data-stu-id="59340-136">none</span></span>                                 |
| <span data-ttu-id="59340-137">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="59340-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="59340-138">TRUE (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="59340-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="59340-139">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="59340-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="59340-140">falso</span><span class="sxs-lookup"><span data-stu-id="59340-140">false</span></span>                                |

### <a name="-computername-string"></a><span data-ttu-id="59340-141">-ComputerName \<cadeia\></span><span class="sxs-lookup"><span data-stu-id="59340-141">-ComputerName \<String\></span></span>

<span data-ttu-id="59340-142">Especifica o nome do computador ao qual esta regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="59340-142">Specifies the computer name to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="59340-143">Aliases</span><span class="sxs-lookup"><span data-stu-id="59340-143">Aliases</span></span>                              | <span data-ttu-id="59340-144">nenhum</span><span class="sxs-lookup"><span data-stu-id="59340-144">none</span></span>                                 |
| <span data-ttu-id="59340-145">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="59340-145">Required?</span></span>                            | <span data-ttu-id="59340-146">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="59340-146">true</span></span>                                 |
| <span data-ttu-id="59340-147">Posição?</span><span class="sxs-lookup"><span data-stu-id="59340-147">Position?</span></span>                            | <span data-ttu-id="59340-148">com o nome</span><span class="sxs-lookup"><span data-stu-id="59340-148">named</span></span>                                |
| <span data-ttu-id="59340-149">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="59340-149">Default Value</span></span>                        | <span data-ttu-id="59340-150">nenhum</span><span class="sxs-lookup"><span data-stu-id="59340-150">none</span></span>                                 |
| <span data-ttu-id="59340-151">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="59340-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="59340-152">TRUE (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="59340-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="59340-153">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="59340-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="59340-154">falso</span><span class="sxs-lookup"><span data-stu-id="59340-154">false</span></span>                                |

### <a name="-configurationname-string"></a><span data-ttu-id="59340-155">-ConfigurationName \<cadeia\></span><span class="sxs-lookup"><span data-stu-id="59340-155">-ConfigurationName \<String\></span></span>

<span data-ttu-id="59340-156">Especifica o nome da configuração de sessão do Windows PowerShell, também conhecido como espaço de execução, ao qual esta regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="59340-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="59340-157">Aliases</span><span class="sxs-lookup"><span data-stu-id="59340-157">Aliases</span></span>                              | <span data-ttu-id="59340-158">nenhum</span><span class="sxs-lookup"><span data-stu-id="59340-158">none</span></span>                                 |
| <span data-ttu-id="59340-159">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="59340-159">Required?</span></span>                            | <span data-ttu-id="59340-160">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="59340-160">true</span></span>                                 |
| <span data-ttu-id="59340-161">Posição?</span><span class="sxs-lookup"><span data-stu-id="59340-161">Position?</span></span>                            | <span data-ttu-id="59340-162">com o nome</span><span class="sxs-lookup"><span data-stu-id="59340-162">named</span></span>                                |
| <span data-ttu-id="59340-163">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="59340-163">Default Value</span></span>                        | <span data-ttu-id="59340-164">nenhum</span><span class="sxs-lookup"><span data-stu-id="59340-164">none</span></span>                                 |
| <span data-ttu-id="59340-165">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="59340-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="59340-166">TRUE (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="59340-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="59340-167">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="59340-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="59340-168">falso</span><span class="sxs-lookup"><span data-stu-id="59340-168">false</span></span>                                |

### <a name="-credential--pscredential"></a><span data-ttu-id="59340-169">-Credential \<PSCredential\></span><span class="sxs-lookup"><span data-stu-id="59340-169">-Credential  \<PSCredential\></span></span>

<span data-ttu-id="59340-170">Especifica um **PSCredential** objeto para uma conta de utilizador que pretende utilizar para alterar as regras de autorização do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="59340-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="59340-171">Se não adicionar este parâmetro, o cmdlet utiliza a conta de utilizador com sessão atualmente iniciada.</span><span class="sxs-lookup"><span data-stu-id="59340-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="59340-172">Para obter um **PSCredential** objeto, que é necessário para adicionar regras de autorização remotamente, execute o [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="59340-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="59340-173">Aliases</span><span class="sxs-lookup"><span data-stu-id="59340-173">Aliases</span></span>                              | <span data-ttu-id="59340-174">nenhum</span><span class="sxs-lookup"><span data-stu-id="59340-174">none</span></span>                                 |
| <span data-ttu-id="59340-175">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="59340-175">Required?</span></span>                            | <span data-ttu-id="59340-176">falso</span><span class="sxs-lookup"><span data-stu-id="59340-176">false</span></span>                                |
| <span data-ttu-id="59340-177">Posição?</span><span class="sxs-lookup"><span data-stu-id="59340-177">Position?</span></span>                            | <span data-ttu-id="59340-178">com o nome</span><span class="sxs-lookup"><span data-stu-id="59340-178">named</span></span>                                |
| <span data-ttu-id="59340-179">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="59340-179">Default Value</span></span>                        | <span data-ttu-id="59340-180">nenhum</span><span class="sxs-lookup"><span data-stu-id="59340-180">none</span></span>                                 |
| <span data-ttu-id="59340-181">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="59340-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="59340-182">falso</span><span class="sxs-lookup"><span data-stu-id="59340-182">false</span></span>                                |
| <span data-ttu-id="59340-183">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="59340-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="59340-184">falso</span><span class="sxs-lookup"><span data-stu-id="59340-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="59340-185">-Force</span><span class="sxs-lookup"><span data-stu-id="59340-185">-Force</span></span>

<span data-ttu-id="59340-186">Força o comando ser executado sem solicitar a confirmação do utilizador. \\</span><span class="sxs-lookup"><span data-stu-id="59340-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="59340-187">Além disso, ele também solicita a confirmação ao introduzir um nome de computador simples ou curto (como um nome que não é um nome de domínio ou não é totalmente qualificado).</span><span class="sxs-lookup"><span data-stu-id="59340-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="59340-188">Confirmação é solicitada por motivos de segurança, para que possa utilizar o nome simple para adicionar um computador apenas se o computador está num grupo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="59340-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||
|-|-|
| <span data-ttu-id="59340-189">Aliases</span><span class="sxs-lookup"><span data-stu-id="59340-189">Aliases</span></span>                              | <span data-ttu-id="59340-190">nenhum</span><span class="sxs-lookup"><span data-stu-id="59340-190">none</span></span>                                 |
| <span data-ttu-id="59340-191">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="59340-191">Required?</span></span>                            | <span data-ttu-id="59340-192">falso</span><span class="sxs-lookup"><span data-stu-id="59340-192">false</span></span>                                |
| <span data-ttu-id="59340-193">Posição?</span><span class="sxs-lookup"><span data-stu-id="59340-193">Position?</span></span>                            | <span data-ttu-id="59340-194">com o nome</span><span class="sxs-lookup"><span data-stu-id="59340-194">named</span></span>                                |
| <span data-ttu-id="59340-195">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="59340-195">Default Value</span></span>                        | <span data-ttu-id="59340-196">nenhum</span><span class="sxs-lookup"><span data-stu-id="59340-196">none</span></span>                                 |
| <span data-ttu-id="59340-197">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="59340-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="59340-198">falso</span><span class="sxs-lookup"><span data-stu-id="59340-198">false</span></span>                                |
| <span data-ttu-id="59340-199">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="59340-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="59340-200">falso</span><span class="sxs-lookup"><span data-stu-id="59340-200">false</span></span>                                |

### <a name="-rulename-string"></a><span data-ttu-id="59340-201">-RuleName \<cadeia\></span><span class="sxs-lookup"><span data-stu-id="59340-201">-RuleName \<String\></span></span>

<span data-ttu-id="59340-202">Especifica o nome amigável para esta regra.</span><span class="sxs-lookup"><span data-stu-id="59340-202">Specifies the friendly name for this rule.</span></span>

|||
|-|-|
| <span data-ttu-id="59340-203">Aliases</span><span class="sxs-lookup"><span data-stu-id="59340-203">Aliases</span></span>                              | <span data-ttu-id="59340-204">nenhum</span><span class="sxs-lookup"><span data-stu-id="59340-204">none</span></span>                                 |
| <span data-ttu-id="59340-205">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="59340-205">Required?</span></span>                            | <span data-ttu-id="59340-206">falso</span><span class="sxs-lookup"><span data-stu-id="59340-206">false</span></span>                                |
| <span data-ttu-id="59340-207">Posição?</span><span class="sxs-lookup"><span data-stu-id="59340-207">Position?</span></span>                            | <span data-ttu-id="59340-208">com o nome</span><span class="sxs-lookup"><span data-stu-id="59340-208">named</span></span>                                |
| <span data-ttu-id="59340-209">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="59340-209">Default Value</span></span>                        | <span data-ttu-id="59340-210">nenhum</span><span class="sxs-lookup"><span data-stu-id="59340-210">none</span></span>                                 |
| <span data-ttu-id="59340-211">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="59340-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="59340-212">TRUE (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="59340-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="59340-213">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="59340-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="59340-214">falso</span><span class="sxs-lookup"><span data-stu-id="59340-214">false</span></span>                                |

### <a name="-usergroupname-string"></a><span data-ttu-id="59340-215">-UserGroupName \<cadeia\[\]\></span><span class="sxs-lookup"><span data-stu-id="59340-215">-UserGroupName \<String\[\]\></span></span>

<span data-ttu-id="59340-216">Especifica o nome de um ou mais grupos de utilizadores no AD DS ou grupos locais para a qual esta regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="59340-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="59340-217">Aliases</span><span class="sxs-lookup"><span data-stu-id="59340-217">Aliases</span></span>                              | <span data-ttu-id="59340-218">nenhum</span><span class="sxs-lookup"><span data-stu-id="59340-218">none</span></span>                                 |
| <span data-ttu-id="59340-219">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="59340-219">Required?</span></span>                            | <span data-ttu-id="59340-220">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="59340-220">true</span></span>                                 |
| <span data-ttu-id="59340-221">Posição?</span><span class="sxs-lookup"><span data-stu-id="59340-221">Position?</span></span>                            | <span data-ttu-id="59340-222">com o nome</span><span class="sxs-lookup"><span data-stu-id="59340-222">named</span></span>                                |
| <span data-ttu-id="59340-223">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="59340-223">Default Value</span></span>                        | <span data-ttu-id="59340-224">nenhum</span><span class="sxs-lookup"><span data-stu-id="59340-224">none</span></span>                                 |
| <span data-ttu-id="59340-225">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="59340-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="59340-226">TRUE (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="59340-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="59340-227">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="59340-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="59340-228">falso</span><span class="sxs-lookup"><span data-stu-id="59340-228">false</span></span>                                |

### <a name="-username-string"></a><span data-ttu-id="59340-229">-UserName \<cadeia\[\]\></span><span class="sxs-lookup"><span data-stu-id="59340-229">-UserName \<String\[\]\></span></span>

<span data-ttu-id="59340-230">Especifica um ou mais utilizadores ao qual esta regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="59340-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="59340-231">O nome de utilizador pode ser uma conta de utilizador local no computador gateway ou um utilizador no AD DS.</span><span class="sxs-lookup"><span data-stu-id="59340-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="59340-232">O formato é `domain\user` ou `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="59340-232">The format is `domain\user` or `computer\user`.</span></span>

|||
|-|-|
| <span data-ttu-id="59340-233">Aliases</span><span class="sxs-lookup"><span data-stu-id="59340-233">Aliases</span></span>                              | <span data-ttu-id="59340-234">nenhum</span><span class="sxs-lookup"><span data-stu-id="59340-234">none</span></span>                                 |
| <span data-ttu-id="59340-235">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="59340-235">Required?</span></span>                            | <span data-ttu-id="59340-236">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="59340-236">true</span></span>                                 |
| <span data-ttu-id="59340-237">Posição?</span><span class="sxs-lookup"><span data-stu-id="59340-237">Position?</span></span>                            | <span data-ttu-id="59340-238">1</span><span class="sxs-lookup"><span data-stu-id="59340-238">1</span></span>                                    |
| <span data-ttu-id="59340-239">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="59340-239">Default Value</span></span>                        | <span data-ttu-id="59340-240">nenhum</span><span class="sxs-lookup"><span data-stu-id="59340-240">none</span></span>                                 |
| <span data-ttu-id="59340-241">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="59340-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="59340-242">TRUE (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="59340-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="59340-243">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="59340-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="59340-244">falso</span><span class="sxs-lookup"><span data-stu-id="59340-244">false</span></span>                                |

###  <a name="commonparameters"></a><span data-ttu-id="59340-245">\<CommonParameters\></span><span class="sxs-lookup"><span data-stu-id="59340-245">\<CommonParameters\></span></span>

<span data-ttu-id="59340-246">Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="59340-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="59340-247">Para obter mais informações, consulte [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="59340-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="59340-248">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="59340-248">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="59340-249">Cadeia</span><span class="sxs-lookup"><span data-stu-id="59340-249">String</span></span>

<span data-ttu-id="59340-250">Este cmdlet aceita uma cadeia de caracteres ou uma matriz de cadeias de caracteres como entrada.</span><span class="sxs-lookup"><span data-stu-id="59340-250">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="59340-251">Cadeia de caracteres\[\]</span><span class="sxs-lookup"><span data-stu-id="59340-251">String\[\]</span></span>

<span data-ttu-id="59340-252">Este cmdlet aceita uma cadeia de caracteres ou uma matriz de cadeias de caracteres como entrada.</span><span class="sxs-lookup"><span data-stu-id="59340-252">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="59340-253">Saídas</span><span class="sxs-lookup"><span data-stu-id="59340-253">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="59340-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="59340-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="59340-255">Este cmdlet devolve a um objeto de regra de autorização.</span><span class="sxs-lookup"><span data-stu-id="59340-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="59340-256">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="59340-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="59340-257">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="59340-257">EXAMPLE 1</span></span>

<span data-ttu-id="59340-258">Neste exemplo concede acesso à configuração de sessão _PSWAEndpoint_, um restritas espaço de execução, na _srv2_ para utilizadores no _SMAdmins_ grupo.</span><span class="sxs-lookup"><span data-stu-id="59340-258">This example grants access to the session configuration _PSWAEndpoint_, a restricted runspace, on _srv2_ for users in the _SMAdmins_ group.</span></span>

> [!NOTE]
> <span data-ttu-id="59340-259">O nome do computador tem de ser um nome de domínio completamente qualificado (FQDN).</span><span class="sxs-lookup"><span data-stu-id="59340-259">The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="59340-260">Os administradores de definir uma configuração de sessão restritas ou espaço de execução, o que é um intervalo limitado de cmdlets e tarefas que os utilizadores finais podem ser executadas.</span><span class="sxs-lookup"><span data-stu-id="59340-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="59340-261">Definir um espaço de execução restrito pode impedir que os utilizadores acedam a outros computadores que não estiver num espaço de execução permitido do Windows PowerShell®, portanto, oferecendo uma conexão mais segura.</span><span class="sxs-lookup"><span data-stu-id="59340-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="59340-262">Para obter mais informações sobre configurações de sessão, consulte [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) ou o [instalar e utilizar o acesso Web Windows PowerShell](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="59340-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="59340-263">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="59340-263">EXAMPLE 2</span></span>

<span data-ttu-id="59340-264">Neste exemplo concede acesso para a configuração de sessão do Windows PowerShell padrão `Microsoft.PowerShell`, no *srv2* aos utilizadores dos utilizadores com o nome `contoso\user1`, `contoso\user2`, e `contoso\user3`.</span><span class="sxs-lookup"><span data-stu-id="59340-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named `contoso\user1`, `contoso\user2`, and `contoso\user3`.</span></span> <span data-ttu-id="59340-265">Este cmdlet cria três regras (1 por pessoa).</span><span class="sxs-lookup"><span data-stu-id="59340-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="59340-266">EXEMPLO 3</span><span class="sxs-lookup"><span data-stu-id="59340-266">EXAMPLE 3</span></span>

<span data-ttu-id="59340-267">Este exemplo ilustra como valores de nome de utilizador através do pipeline de entrada.</span><span class="sxs-lookup"><span data-stu-id="59340-267">This example illustrates how to input user name values via the pipeline.</span></span>

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="59340-268">EXEMPLO 4</span><span class="sxs-lookup"><span data-stu-id="59340-268">EXAMPLE 4</span></span>

<span data-ttu-id="59340-269">Este exemplo ilustra como todos os parâmetros tirar valores do pipeline por nome de propriedade.</span><span class="sxs-lookup"><span data-stu-id="59340-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````PowerShell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="59340-270">EXEMPLO 5</span><span class="sxs-lookup"><span data-stu-id="59340-270">EXAMPLE 5</span></span>

<span data-ttu-id="59340-271">Este exemplo adiciona uma regra para permitir que o usuário local chamado `PswaServer\ChrisLocal` acesso ao servidor com o nome **srv1.contoso.com**.</span><span class="sxs-lookup"><span data-stu-id="59340-271">This example adds a rule to allow the local user named `PswaServer\ChrisLocal` access to the server named **srv1.contoso.com**.</span></span>

<span data-ttu-id="59340-272">Este exemplo ilustra um cenário onde o gateway está num grupo de trabalho e o computador de destino está num domínio.</span><span class="sxs-lookup"><span data-stu-id="59340-272">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="59340-273">Se aplica a regra de autorização para os utilizadores locais no gateway.</span><span class="sxs-lookup"><span data-stu-id="59340-273">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="59340-274">Na página do Windows PowerShell Web Access início de sessão, para autenticar com êxito, o utilizador tem de fornecer um segundo conjunto de credenciais no **definições de ligação opcionais** área.</span><span class="sxs-lookup"><span data-stu-id="59340-274">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="59340-275">O servidor de gateway utiliza o conjunto de credenciais adicional para autenticar o utilizador no computador de destino, um servidor com o nome *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="59340-275">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````powershell
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="59340-276">EXEMPLO 6</span><span class="sxs-lookup"><span data-stu-id="59340-276">EXAMPLE 6</span></span>

<span data-ttu-id="59340-277">Este exemplo permite todos os utilizadores o acesso a todos os pontos finais em todos os computadores.</span><span class="sxs-lookup"><span data-stu-id="59340-277">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="59340-278">Essencialmente, isso se desligar as regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="59340-278">This essentially turns off authorization rules.</span></span>

> [!NOTE]
> <span data-ttu-id="59340-279">Utilizar o `*` caráter universal não é recomendada para implementações de protegida e deve apenas ser considerado para ambientes de teste ou utilizado em implementações em que pode ser Relaxada segurança.</span><span class="sxs-lookup"><span data-stu-id="59340-279">Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="59340-280">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="59340-280">See Also</span></span>

<span data-ttu-id="59340-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="59340-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span></span>

<span data-ttu-id="59340-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="59340-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span></span>

<span data-ttu-id="59340-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="59340-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span></span>

<span data-ttu-id="59340-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="59340-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span></span>

[<span data-ttu-id="59340-285">Adicionar membros</span><span class="sxs-lookup"><span data-stu-id="59340-285">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[<span data-ttu-id="59340-286">New-Object</span><span class="sxs-lookup"><span data-stu-id="59340-286">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[<span data-ttu-id="59340-287">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="59340-287">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)