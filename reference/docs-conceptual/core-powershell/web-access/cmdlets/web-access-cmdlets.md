---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, o cmdlet
ms.date: 2016-12-12
title: cmdlets de acesso Web
ms.technology: powershell
ms.openlocfilehash: daebe2fe2cbccaf8d3f41d265d23dc45d3bb99b6
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="windows-powershell-web-access-cmdlets"></a><span data-ttu-id="097aa-103">Cmdlets do Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="097aa-103">Windows PowerShell Web Access Cmdlets</span></span>

<span data-ttu-id="097aa-104">Esta referência fornece sintaxe e descrições de cmdlet para todos os cmdlets do Windows PowerShell® Web acesso específico.</span><span class="sxs-lookup"><span data-stu-id="097aa-104">This reference provides cmdlet descriptions and syntax for all Windows PowerShell® Web Access-specific cmdlets.</span></span> <span data-ttu-id="097aa-105">Lista os cmdlets por ordem alfabética baseados no verbo no início do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="097aa-105">It lists the cmdlets in alphabetical order based on the verb at the beginning of the cmdlet.</span></span>

## <a name="add-pswaauthorizationruleadd-pswaauthorizationrulemd"></a>[<span data-ttu-id="097aa-106">Adicionar-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="097aa-106">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)

<span data-ttu-id="097aa-107">Adiciona uma nova regra de autorização para o conjunto de regras de autorização de acesso de Web do Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="097aa-107">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="get-pswaauthorizationruleget-pswaauthorizationrulemd"></a>[<span data-ttu-id="097aa-108">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="097aa-108">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)

<span data-ttu-id="097aa-109">Devolve um conjunto de regras de autorização de acesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="097aa-109">Returns a set of the Windows PowerShell Web Access authorization rules.</span></span>

## <a name="install-pswawebapplicationinstall-pswawebapplicationmd"></a>[<span data-ttu-id="097aa-110">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="097aa-110">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)

<span data-ttu-id="097aa-111">Configura a aplicação web do acesso Web Windows PowerShell no IIS.</span><span class="sxs-lookup"><span data-stu-id="097aa-111">Configures the Windows PowerShell Web Access web application in IIS.</span></span>

## <a name="remove-pswaauthorizationruleremove-pswaauthorizationrulemd"></a>[<span data-ttu-id="097aa-112">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="097aa-112">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)

<span data-ttu-id="097aa-113">Remove uma regra de autorização especificada do acesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="097aa-113">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="test-pswaauthorizationruletest-pswaauthorizationrulemd"></a>[<span data-ttu-id="097aa-114">Teste-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="097aa-114">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)

<span data-ttu-id="097aa-115">Os testes de regras de autorização para validar que um determinado utilizador, computador, o pedido de acesso de ponto final está autorizado.</span><span class="sxs-lookup"><span data-stu-id="097aa-115">Tests authorization rules to validate that a particular user, computer, endpoint access request is authorized.</span></span>

## <a name="uninstall-pswawebapplicationuninstall-pswawebapplicationmd"></a>[<span data-ttu-id="097aa-116">Desinstalar-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="097aa-116">Uninstall-PswaWebApplication</span></span>](uninstall-pswawebapplication.md)

<span data-ttu-id="097aa-117">Desinstala a aplicação web do Windows PowerShell a partir do IIS.</span><span class="sxs-lookup"><span data-stu-id="097aa-117">Uninstalls the Windows PowerShell web application from IIS.</span></span>

><span data-ttu-id="097aa-118">**Tenha em atenção**:</span><span class="sxs-lookup"><span data-stu-id="097aa-118">**Note**:</span></span>
>
><span data-ttu-id="097aa-119">Para listar todos os cmdlets que estão disponíveis, utilize o:</span><span class="sxs-lookup"><span data-stu-id="097aa-119">To list all the cmdlets that are available, use the:</span></span>
>
> <span data-ttu-id="097aa-120">`Get-Command –Module PowerShellWebAccess`cmdlet.</span><span class="sxs-lookup"><span data-stu-id="097aa-120">`Get-Command –Module PowerShellWebAccess` cmdlet.</span></span>

<span data-ttu-id="097aa-121">Para obter mais informações ou para a sintaxe de qualquer um dos cmdlets, utilize:</span><span class="sxs-lookup"><span data-stu-id="097aa-121">For more information about, or for the syntax of, any of the cmdlets, use:</span></span>  
<span data-ttu-id="097aa-122">`Get-Help `*&lt;nome do cmdlet&gt;*</span><span class="sxs-lookup"><span data-stu-id="097aa-122">`Get-Help `*&lt;cmdlet name&gt;*</span></span>  
<span data-ttu-id="097aa-123">onde  *&lt;nome do cmdlet&gt;*  é o nome do cmdlet que pretende pesquisar.</span><span class="sxs-lookup"><span data-stu-id="097aa-123">where *&lt;cmdlet name&gt;* is the name of the cmdlet that you want to research.</span></span>

<span data-ttu-id="097aa-124">Para informações mais detalhadas, pode executar um dos cmdlets seguintes:</span><span class="sxs-lookup"><span data-stu-id="097aa-124">For more detailed information, you can run any of the following cmdlets:</span></span>

- <span data-ttu-id="097aa-125">`Get-Help `*&lt;nome do cmdlet&gt;*` -Detailed`</span><span class="sxs-lookup"><span data-stu-id="097aa-125">`Get-Help `*&lt;cmdlet name&gt;*` -Detailed`</span></span>
- <span data-ttu-id="097aa-126">`Get-Help `*&lt;nome do cmdlet&gt;*` -Examples`</span><span class="sxs-lookup"><span data-stu-id="097aa-126">`Get-Help `*&lt;cmdlet name&gt;*` -Examples`</span></span>
- <span data-ttu-id="097aa-127">`Get-Help `*&lt;nome do cmdlet&gt;*` -Full`</span><span class="sxs-lookup"><span data-stu-id="097aa-127">`Get-Help `*&lt;cmdlet name&gt;*` -Full`</span></span>

### <a name="more-information"></a><span data-ttu-id="097aa-128">Mais Informações</span><span class="sxs-lookup"><span data-stu-id="097aa-128">More Information</span></span>

<span data-ttu-id="097aa-129">Para obter mais informações sobre o acesso Web do PowerShell, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="097aa-129">For more information about PowerShell Web Access, see the following:</span></span>

- [<span data-ttu-id="097aa-130">Instalar e utilizar o acesso Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="097aa-130">Install and Use Windows PowerShell Web Access</span></span>](../install-and-use-windows-powershell-web-access.md)

