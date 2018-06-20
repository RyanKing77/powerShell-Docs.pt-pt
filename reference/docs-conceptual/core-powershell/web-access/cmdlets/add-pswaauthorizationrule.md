---
ms.topic: reference
keywords: PowerShell, o cmdlet
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: b8020f8b034ab24d79a96da3908e9b63bf017cd9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190388"
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="0cef3-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="0cef3-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="0cef3-104">RESUMO</span><span class="sxs-lookup"><span data-stu-id="0cef3-104">SYNOPSIS</span></span>

<span data-ttu-id="0cef3-105">Adiciona uma nova regra de autorização para o conjunto de regras de autorização de acesso de Web do Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="0cef3-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="0cef3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0cef3-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="0cef3-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="0cef3-107">UserGroupNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="0cef3-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="0cef3-108">UserGroupNameComputerName</span></span>
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="0cef3-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="0cef3-109">UserNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="0cef3-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="0cef3-110">UserNameComputerName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="0cef3-111">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="0cef3-111">DESCRIPTION</span></span>

<span data-ttu-id="0cef3-112">O **Add-PswaAuthorizationRule** cmdlet adiciona uma nova regra de autorização para o conjunto de regras de autorização de acesso de Web do Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="0cef3-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="0cef3-113">Tem de especificar os utilizadores, computadores e pontos finais do Windows PowerShell para esta regra.</span><span class="sxs-lookup"><span data-stu-id="0cef3-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="0cef3-114">Pode especificar utilizadores e computadores, contas de utilizador individuais e nomes de computador ou ao especificar os grupos.</span><span class="sxs-lookup"><span data-stu-id="0cef3-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="0cef3-115">Para um computador que está associado a um domínio do Active Directory, o cmdlet utiliza o identificador de segurança (SID) do computador para criar a regra.</span><span class="sxs-lookup"><span data-stu-id="0cef3-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="0cef3-116">Isto permite-lhe utilizar um nome abreviado de um nome de domínio completamente qualificado (FQDN) ou um endereço IP para o **nome do computador** campo na página de início de sessão.</span><span class="sxs-lookup"><span data-stu-id="0cef3-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="0cef3-117">Para um computador que não está associado a um domínio do Active Directory, o cmdlet cria a regra ao utilizar o nome do computador fornecido pelo administrador.</span><span class="sxs-lookup"><span data-stu-id="0cef3-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="0cef3-118">Ligar com êxito a esta máquina, o utilizador final tem de fornecer o nome do computador exatamente conforme aparece na regra.</span><span class="sxs-lookup"><span data-stu-id="0cef3-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="0cef3-119">Se existirem vários computadores com o mesmo nome na rede, pode resolver nome abreviado a mais do que um computador.</span><span class="sxs-lookup"><span data-stu-id="0cef3-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="0cef3-120">Isto pode levar a ambiguidade quando estabelecer uma ligação.</span><span class="sxs-lookup"><span data-stu-id="0cef3-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="0cef3-121">Por exemplo, se existe uma regra para o computador de grupo de trabalho com o nome "*servidor1*" e um novo computador com o nome *server1.contoso.com* está associado à rede, utilizando as regras de autorização de validação é concluída com êxito e Acesso Web Windows PowerShell tenta estabelecer uma ligação ao computador com o nome "*servidor1*".</span><span class="sxs-lookup"><span data-stu-id="0cef3-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="0cef3-122">Não é garantido que a ligação é estabelecida com o computador de grupo de trabalho especificado; a tentativa de foi possível estabelecer o grupo de trabalho ou o computador de domínio com o nome "*servidor1*".</span><span class="sxs-lookup"><span data-stu-id="0cef3-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="0cef3-123">Para reduzir a ambiguidade, é recomendado que utilize o FQDN para o computador de destino, sempre que possível criar uma regra de autorização.</span><span class="sxs-lookup"><span data-stu-id="0cef3-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="0cef3-124">As regras de autorização avaliar a credencial primária início de sessão dos utilizadores de acesso Web Windows PowerShell, não as credenciais alternativas (o segundo conjunto de credenciais encontrado no **definições de ligação opcionais** secção a início de sessão página).</span><span class="sxs-lookup"><span data-stu-id="0cef3-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="0cef3-125">Para obter um exemplo disto, consulte o exemplo 6.</span><span class="sxs-lookup"><span data-stu-id="0cef3-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="0cef3-126">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0cef3-126">Parameters</span></span>

### <a name="-computergroupnameltstringgt"></a><span data-ttu-id="0cef3-127">-ComputerGroupName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="0cef3-127">-ComputerGroupName&lt;String&gt;</span></span>

<span data-ttu-id="0cef3-128">Especifica o nome de um grupo de computador nos serviços de domínio do Active Directory (AD DS) ou grupos locais para o qual esta regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="0cef3-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="0cef3-129">Aliases</span><span class="sxs-lookup"><span data-stu-id="0cef3-129">Aliases</span></span>                              | <span data-ttu-id="0cef3-130">nenhum</span><span class="sxs-lookup"><span data-stu-id="0cef3-130">none</span></span>                                 |
| <span data-ttu-id="0cef3-131">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="0cef3-131">Required?</span></span>                            | <span data-ttu-id="0cef3-132">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="0cef3-132">true</span></span>                                 |
| <span data-ttu-id="0cef3-133">Posição?</span><span class="sxs-lookup"><span data-stu-id="0cef3-133">Position?</span></span>                            | <span data-ttu-id="0cef3-134">com o nome</span><span class="sxs-lookup"><span data-stu-id="0cef3-134">named</span></span>                                |
| <span data-ttu-id="0cef3-135">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="0cef3-135">Default Value</span></span>                        | <span data-ttu-id="0cef3-136">nenhum</span><span class="sxs-lookup"><span data-stu-id="0cef3-136">none</span></span>                                 |
| <span data-ttu-id="0cef3-137">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="0cef3-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0cef3-138">VERDADEIRO (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0cef3-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="0cef3-139">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="0cef3-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0cef3-140">falso</span><span class="sxs-lookup"><span data-stu-id="0cef3-140">false</span></span>                                |

### <a name="-computernameltstringgt"></a><span data-ttu-id="0cef3-141">-ComputerName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="0cef3-141">-ComputerName&lt;String&gt;</span></span>

<span data-ttu-id="0cef3-142">Especifica o nome do computador ao qual esta regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="0cef3-142">Specifies the computer name to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="0cef3-143">Aliases</span><span class="sxs-lookup"><span data-stu-id="0cef3-143">Aliases</span></span>                              | <span data-ttu-id="0cef3-144">nenhum</span><span class="sxs-lookup"><span data-stu-id="0cef3-144">none</span></span>                                 |
| <span data-ttu-id="0cef3-145">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="0cef3-145">Required?</span></span>                            | <span data-ttu-id="0cef3-146">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="0cef3-146">true</span></span>                                 |
| <span data-ttu-id="0cef3-147">Posição?</span><span class="sxs-lookup"><span data-stu-id="0cef3-147">Position?</span></span>                            | <span data-ttu-id="0cef3-148">com o nome</span><span class="sxs-lookup"><span data-stu-id="0cef3-148">named</span></span>                                |
| <span data-ttu-id="0cef3-149">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="0cef3-149">Default Value</span></span>                        | <span data-ttu-id="0cef3-150">nenhum</span><span class="sxs-lookup"><span data-stu-id="0cef3-150">none</span></span>                                 |
| <span data-ttu-id="0cef3-151">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="0cef3-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0cef3-152">VERDADEIRO (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0cef3-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="0cef3-153">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="0cef3-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0cef3-154">falso</span><span class="sxs-lookup"><span data-stu-id="0cef3-154">false</span></span>                                |

### <a name="-configurationnameltstringgt"></a><span data-ttu-id="0cef3-155">-ConfigurationName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="0cef3-155">-ConfigurationName&lt;String&gt;</span></span>

<span data-ttu-id="0cef3-156">Especifica o nome da configuração de sessão do Windows PowerShell, também conhecido como espaço de execução, ao qual esta regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="0cef3-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="0cef3-157">Aliases</span><span class="sxs-lookup"><span data-stu-id="0cef3-157">Aliases</span></span>                              | <span data-ttu-id="0cef3-158">nenhum</span><span class="sxs-lookup"><span data-stu-id="0cef3-158">none</span></span>                                 |
| <span data-ttu-id="0cef3-159">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="0cef3-159">Required?</span></span>                            | <span data-ttu-id="0cef3-160">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="0cef3-160">true</span></span>                                 |
| <span data-ttu-id="0cef3-161">Posição?</span><span class="sxs-lookup"><span data-stu-id="0cef3-161">Position?</span></span>                            | <span data-ttu-id="0cef3-162">com o nome</span><span class="sxs-lookup"><span data-stu-id="0cef3-162">named</span></span>                                |
| <span data-ttu-id="0cef3-163">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="0cef3-163">Default Value</span></span>                        | <span data-ttu-id="0cef3-164">nenhum</span><span class="sxs-lookup"><span data-stu-id="0cef3-164">none</span></span>                                 |
| <span data-ttu-id="0cef3-165">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="0cef3-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0cef3-166">VERDADEIRO (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0cef3-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="0cef3-167">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="0cef3-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0cef3-168">falso</span><span class="sxs-lookup"><span data-stu-id="0cef3-168">false</span></span>                                |

### <a name="-credentialltpscredentialgt"></a><span data-ttu-id="0cef3-169">-Credential&lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="0cef3-169">-Credential&lt;PSCredential&gt;</span></span>

<span data-ttu-id="0cef3-170">Especifica um **PSCredential** objeto para uma conta de utilizador que pretende utilizar para alterar as regras de autorização de acesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0cef3-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="0cef3-171">Se não adicionar este parâmetro, o cmdlet utiliza a conta de utilizador atualmente com sessão iniciada.</span><span class="sxs-lookup"><span data-stu-id="0cef3-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="0cef3-172">Para obter um **PSCredential** objeto, que é necessário para adicionar regras de autorização remotamente, execute o [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0cef3-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="0cef3-173">Aliases</span><span class="sxs-lookup"><span data-stu-id="0cef3-173">Aliases</span></span>                              | <span data-ttu-id="0cef3-174">nenhum</span><span class="sxs-lookup"><span data-stu-id="0cef3-174">none</span></span>                                 |
| <span data-ttu-id="0cef3-175">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="0cef3-175">Required?</span></span>                            | <span data-ttu-id="0cef3-176">falso</span><span class="sxs-lookup"><span data-stu-id="0cef3-176">false</span></span>                                |
| <span data-ttu-id="0cef3-177">Posição?</span><span class="sxs-lookup"><span data-stu-id="0cef3-177">Position?</span></span>                            | <span data-ttu-id="0cef3-178">com o nome</span><span class="sxs-lookup"><span data-stu-id="0cef3-178">named</span></span>                                |
| <span data-ttu-id="0cef3-179">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="0cef3-179">Default Value</span></span>                        | <span data-ttu-id="0cef3-180">nenhum</span><span class="sxs-lookup"><span data-stu-id="0cef3-180">none</span></span>                                 |
| <span data-ttu-id="0cef3-181">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="0cef3-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0cef3-182">falso</span><span class="sxs-lookup"><span data-stu-id="0cef3-182">false</span></span>                                |
| <span data-ttu-id="0cef3-183">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="0cef3-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0cef3-184">falso</span><span class="sxs-lookup"><span data-stu-id="0cef3-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="0cef3-185">-Force</span><span class="sxs-lookup"><span data-stu-id="0cef3-185">-Force</span></span>

<span data-ttu-id="0cef3-186">Força o comando a executar sem pedir confirmação do utilizador. \\</span><span class="sxs-lookup"><span data-stu-id="0cef3-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="0cef3-187">Além disso, este também solicita a confirmação ao introduzir um nome de computador simples ou curto (como um nome que não é um nome de domínio ou não está completamente qualificado).</span><span class="sxs-lookup"><span data-stu-id="0cef3-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="0cef3-188">Confirmação solicitada por motivos de segurança, para que possa utilizar o nome simple para adicionar um computador apenas se o computador está num grupo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0cef3-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||
|-|-|
| <span data-ttu-id="0cef3-189">Aliases</span><span class="sxs-lookup"><span data-stu-id="0cef3-189">Aliases</span></span>                              | <span data-ttu-id="0cef3-190">nenhum</span><span class="sxs-lookup"><span data-stu-id="0cef3-190">none</span></span>                                 |
| <span data-ttu-id="0cef3-191">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="0cef3-191">Required?</span></span>                            | <span data-ttu-id="0cef3-192">falso</span><span class="sxs-lookup"><span data-stu-id="0cef3-192">false</span></span>                                |
| <span data-ttu-id="0cef3-193">Posição?</span><span class="sxs-lookup"><span data-stu-id="0cef3-193">Position?</span></span>                            | <span data-ttu-id="0cef3-194">com o nome</span><span class="sxs-lookup"><span data-stu-id="0cef3-194">named</span></span>                                |
| <span data-ttu-id="0cef3-195">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="0cef3-195">Default Value</span></span>                        | <span data-ttu-id="0cef3-196">nenhum</span><span class="sxs-lookup"><span data-stu-id="0cef3-196">none</span></span>                                 |
| <span data-ttu-id="0cef3-197">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="0cef3-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0cef3-198">falso</span><span class="sxs-lookup"><span data-stu-id="0cef3-198">false</span></span>                                |
| <span data-ttu-id="0cef3-199">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="0cef3-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0cef3-200">falso</span><span class="sxs-lookup"><span data-stu-id="0cef3-200">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="0cef3-201">-RuleName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="0cef3-201">-RuleName&lt;String&gt;</span></span>

<span data-ttu-id="0cef3-202">Especifica o nome amigável para esta regra.</span><span class="sxs-lookup"><span data-stu-id="0cef3-202">Specifies the friendly name for this rule.</span></span>

|||
|-|-|
| <span data-ttu-id="0cef3-203">Aliases</span><span class="sxs-lookup"><span data-stu-id="0cef3-203">Aliases</span></span>                              | <span data-ttu-id="0cef3-204">nenhum</span><span class="sxs-lookup"><span data-stu-id="0cef3-204">none</span></span>                                 |
| <span data-ttu-id="0cef3-205">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="0cef3-205">Required?</span></span>                            | <span data-ttu-id="0cef3-206">falso</span><span class="sxs-lookup"><span data-stu-id="0cef3-206">false</span></span>                                |
| <span data-ttu-id="0cef3-207">Posição?</span><span class="sxs-lookup"><span data-stu-id="0cef3-207">Position?</span></span>                            | <span data-ttu-id="0cef3-208">com o nome</span><span class="sxs-lookup"><span data-stu-id="0cef3-208">named</span></span>                                |
| <span data-ttu-id="0cef3-209">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="0cef3-209">Default Value</span></span>                        | <span data-ttu-id="0cef3-210">nenhum</span><span class="sxs-lookup"><span data-stu-id="0cef3-210">none</span></span>                                 |
| <span data-ttu-id="0cef3-211">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="0cef3-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0cef3-212">VERDADEIRO (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0cef3-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="0cef3-213">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="0cef3-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0cef3-214">falso</span><span class="sxs-lookup"><span data-stu-id="0cef3-214">false</span></span>                                |

### <a name="-usergroupnameltstringgt"></a><span data-ttu-id="0cef3-215">-UserGroupName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="0cef3-215">-UserGroupName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="0cef3-216">Especifica o nome de um ou mais grupos de utilizador no AD DS ou grupos locais para o qual esta regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="0cef3-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="0cef3-217">Aliases</span><span class="sxs-lookup"><span data-stu-id="0cef3-217">Aliases</span></span>                              | <span data-ttu-id="0cef3-218">nenhum</span><span class="sxs-lookup"><span data-stu-id="0cef3-218">none</span></span>                                 |
| <span data-ttu-id="0cef3-219">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="0cef3-219">Required?</span></span>                            | <span data-ttu-id="0cef3-220">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="0cef3-220">true</span></span>                                 |
| <span data-ttu-id="0cef3-221">Posição?</span><span class="sxs-lookup"><span data-stu-id="0cef3-221">Position?</span></span>                            | <span data-ttu-id="0cef3-222">com o nome</span><span class="sxs-lookup"><span data-stu-id="0cef3-222">named</span></span>                                |
| <span data-ttu-id="0cef3-223">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="0cef3-223">Default Value</span></span>                        | <span data-ttu-id="0cef3-224">nenhum</span><span class="sxs-lookup"><span data-stu-id="0cef3-224">none</span></span>                                 |
| <span data-ttu-id="0cef3-225">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="0cef3-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0cef3-226">VERDADEIRO (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0cef3-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="0cef3-227">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="0cef3-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0cef3-228">falso</span><span class="sxs-lookup"><span data-stu-id="0cef3-228">false</span></span>                                |

### <a name="-usernameltstringgt"></a><span data-ttu-id="0cef3-229">-UserName&lt;cadeia\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="0cef3-229">-UserName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="0cef3-230">Especifica um ou mais utilizadores ao qual esta regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="0cef3-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="0cef3-231">O nome de utilizador pode ser uma conta de utilizador local no computador gateway ou um utilizador no AD DS.</span><span class="sxs-lookup"><span data-stu-id="0cef3-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="0cef3-232">O formato é `domain\user` ou `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="0cef3-232">The format is `domain\user` or `computer\user`.</span></span>

|||
|-|-|
| <span data-ttu-id="0cef3-233">Aliases</span><span class="sxs-lookup"><span data-stu-id="0cef3-233">Aliases</span></span>                              | <span data-ttu-id="0cef3-234">nenhum</span><span class="sxs-lookup"><span data-stu-id="0cef3-234">none</span></span>                                 |
| <span data-ttu-id="0cef3-235">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="0cef3-235">Required?</span></span>                            | <span data-ttu-id="0cef3-236">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="0cef3-236">true</span></span>                                 |
| <span data-ttu-id="0cef3-237">Posição?</span><span class="sxs-lookup"><span data-stu-id="0cef3-237">Position?</span></span>                            | <span data-ttu-id="0cef3-238">1</span><span class="sxs-lookup"><span data-stu-id="0cef3-238">1</span></span>                                    |
| <span data-ttu-id="0cef3-239">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="0cef3-239">Default Value</span></span>                        | <span data-ttu-id="0cef3-240">nenhum</span><span class="sxs-lookup"><span data-stu-id="0cef3-240">none</span></span>                                 |
| <span data-ttu-id="0cef3-241">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="0cef3-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0cef3-242">VERDADEIRO (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0cef3-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="0cef3-243">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="0cef3-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0cef3-244">falso</span><span class="sxs-lookup"><span data-stu-id="0cef3-244">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="0cef3-245">&lt;Parâmetroscomuns&gt;</span><span class="sxs-lookup"><span data-stu-id="0cef3-245">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="0cef3-246">Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="0cef3-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="0cef3-247">Para obter mais informações, consulte [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="0cef3-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="0cef3-248">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="0cef3-248">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="0cef3-249">Cadeia</span><span class="sxs-lookup"><span data-stu-id="0cef3-249">String</span></span>

<span data-ttu-id="0cef3-250">Este cmdlet aceita uma cadeia ou uma matriz de cadeias como entrada.</span><span class="sxs-lookup"><span data-stu-id="0cef3-250">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="0cef3-251">Cadeia\[\]</span><span class="sxs-lookup"><span data-stu-id="0cef3-251">String\[\]</span></span>

<span data-ttu-id="0cef3-252">Este cmdlet aceita uma cadeia ou uma matriz de cadeias como entrada.</span><span class="sxs-lookup"><span data-stu-id="0cef3-252">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="0cef3-253">Saídas</span><span class="sxs-lookup"><span data-stu-id="0cef3-253">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="0cef3-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="0cef3-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="0cef3-255">Este cmdlet devolve a um objeto de regra de autorização.</span><span class="sxs-lookup"><span data-stu-id="0cef3-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="0cef3-256">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="0cef3-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="0cef3-257">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="0cef3-257">EXAMPLE 1</span></span>

<span data-ttu-id="0cef3-258">Neste exemplo concede acesso à configuração de sessão *PSWAEndpoint*, um restrito espaço de execução, no *srv2* para os utilizadores a *SMAdmins* grupo. \\</span><span class="sxs-lookup"><span data-stu-id="0cef3-258">This example grants access to the session configuration *PSWAEndpoint*, a restricted runspace, on *srv2* for users in the *SMAdmins* group.\\</span></span>
<span data-ttu-id="0cef3-259">**Tenha em atenção**: O nome do computador tem de ser um nome de domínio completamente qualificado (FQDN).</span><span class="sxs-lookup"><span data-stu-id="0cef3-259">**Note**: The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="0cef3-260">Os administradores definem uma configuração de sessão restritas ou um espaço de execução, o que é um intervalo limitado de cmdlets e tarefas que os utilizadores finais podem ser executados.</span><span class="sxs-lookup"><span data-stu-id="0cef3-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="0cef3-261">Definir um espaço de execução restrito pode impedir que os utilizadores acedam a outros computadores que são não num espaço de execução permitido do Windows PowerShell®, oferecendo assim uma ligação mais segura.</span><span class="sxs-lookup"><span data-stu-id="0cef3-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="0cef3-262">Para obter mais informações sobre configurações de sessão, consulte [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) ou [instalar e utilizar o acesso Web Windows PowerShell](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="0cef3-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="0cef3-263">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="0cef3-263">EXAMPLE 2</span></span>

<span data-ttu-id="0cef3-264">Neste exemplo concede acesso à configuração de sessão predefinida do Windows PowerShell, `Microsoft.PowerShell`, no *srv2* para utilizadores nos utilizadores com o nome contoso\\user1, contoso\\Utilizador2 e contoso\\user3.</span><span class="sxs-lookup"><span data-stu-id="0cef3-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named contoso\\user1, contoso\\user2, and contoso\\user3.</span></span> <span data-ttu-id="0cef3-265">Este cmdlet cria três regras (1 por pessoa).</span><span class="sxs-lookup"><span data-stu-id="0cef3-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="0cef3-266">EXEMPLO 3</span><span class="sxs-lookup"><span data-stu-id="0cef3-266">EXAMPLE 3</span></span>

<span data-ttu-id="0cef3-267">Este exemplo ilustra como valores de nome de utilizador através do pipeline de entrada.</span><span class="sxs-lookup"><span data-stu-id="0cef3-267">This example illustrates how to input user name values via the pipeline.</span></span>

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="0cef3-268">EXEMPLO 4</span><span class="sxs-lookup"><span data-stu-id="0cef3-268">EXAMPLE 4</span></span>

<span data-ttu-id="0cef3-269">Este exemplo ilustra a forma como todos os parâmetros tirar valores de pipeline ao nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="0cef3-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````PowerShell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="0cef3-270">EXEMPLO 5</span><span class="sxs-lookup"><span data-stu-id="0cef3-270">EXAMPLE 5</span></span>

<span data-ttu-id="0cef3-271">Este exemplo adiciona uma regra para permitir ao utilizador local com o nome *PswaServer\\ChrisLocal* acesso ao servidor com o nome *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="0cef3-271">This example adds a rule to allow the local user named *PswaServer\\ChrisLocal* access to the server named *srv1.contoso.com*.</span></span>

<span data-ttu-id="0cef3-272">Este exemplo ilustra um cenário em que o gateway está num grupo de trabalho e o computador de destino está num domínio.</span><span class="sxs-lookup"><span data-stu-id="0cef3-272">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="0cef3-273">Se aplica a regra de autorização para utilizadores locais no gateway.</span><span class="sxs-lookup"><span data-stu-id="0cef3-273">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="0cef3-274">O acesso Web Windows PowerShell-na página sessão, para autenticar com êxito, o utilizador tem de fornecer um segundo conjunto de credenciais no **definições de ligação opcionais** área.</span><span class="sxs-lookup"><span data-stu-id="0cef3-274">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="0cef3-275">O servidor de gateway utiliza o conjunto de credenciais adicionais para autenticar o utilizador no computador de destino, um servidor com o nome *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="0cef3-275">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="0cef3-276">EXEMPLO 6</span><span class="sxs-lookup"><span data-stu-id="0cef3-276">EXAMPLE 6</span></span>

<span data-ttu-id="0cef3-277">Este exemplo permite que todos os utilizadores acesso a todos os pontos finais em todos os computadores.</span><span class="sxs-lookup"><span data-stu-id="0cef3-277">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="0cef3-278">Isto essencialmente desativa a regras de autorização. \\</span><span class="sxs-lookup"><span data-stu-id="0cef3-278">This essentially turns off authorization rules.\\</span></span>
<span data-ttu-id="0cef3-279">**Tenha em atenção**: utilizar o `*` caráter universal não é recomendada para implementações de segurança confidenciais e deve apenas ser considerado para ambientes de teste ou utilizado em implementações em que pode ser flexibilizada segurança.</span><span class="sxs-lookup"><span data-stu-id="0cef3-279">**Note**: Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="0cef3-280">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="0cef3-280">See Also</span></span>

- <span data-ttu-id="0cef3-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="0cef3-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span></span>
- <span data-ttu-id="0cef3-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="0cef3-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span></span>
- <span data-ttu-id="0cef3-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="0cef3-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span></span>
- <span data-ttu-id="0cef3-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="0cef3-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span></span>
- [<span data-ttu-id="0cef3-285">Adicionar membros</span><span class="sxs-lookup"><span data-stu-id="0cef3-285">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)
- [<span data-ttu-id="0cef3-286">New-Object</span><span class="sxs-lookup"><span data-stu-id="0cef3-286">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)
- [<span data-ttu-id="0cef3-287">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="0cef3-287">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)