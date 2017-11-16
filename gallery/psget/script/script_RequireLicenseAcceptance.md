---
ms.date: 2017-06-09
schema: 2.0.0
keywords: PowerShell
title: RequireLicenseAcceptanceScript
ms.openlocfilehash: 7092fb2e63b9e2b1eca59cd418317631bff8b172
ms.sourcegitcommit: cd66d4f49ea762a31887af2c72d087b219ddbe10
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/11/2017
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="37d96-103">Exigir a aceitação de licença para os Scripts</span><span class="sxs-lookup"><span data-stu-id="37d96-103">Requiring License Acceptance for Scripts</span></span>

<span data-ttu-id="37d96-104">Aceitação de licença não é suportada para os scripts.</span><span class="sxs-lookup"><span data-stu-id="37d96-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="37d96-105">No entanto, o cenário em que um script depende de um módulo que requer a aceitação de licença é suportado.</span><span class="sxs-lookup"><span data-stu-id="37d96-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="37d96-106">Script commands(Install-Script/Save-Script/Update-Script) suportar um novo parâmetro - AcceptLicense que funciona como se o utilizador vimos a licença.</span><span class="sxs-lookup"><span data-stu-id="37d96-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="37d96-107">Se não for especificado - AcceptLicense; o utilizador será apresentado license.txt para o módulo dependente e pedido para aceitar a licença.</span><span class="sxs-lookup"><span data-stu-id="37d96-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="37d96-108">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="37d96-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="37d96-109">Exemplo 1: O Script de instalação com as dependências de exigir a aceitação de licença</span><span class="sxs-lookup"><span data-stu-id="37d96-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>
<span data-ttu-id="37d96-110">Script 'ScriptRequireLicenseAcceptance' depende do módulo 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="37d96-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="37d96-111">Solicitadas ao utilizador para aceitar licença.</span><span class="sxs-lookup"><span data-stu-id="37d96-111">User is prompted to Accept License.</span></span>
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance

License Acceptance
MIT License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): 
```

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="37d96-112">Exemplo 2: O Script de instalação com as dependências de exigir a aceitação de licença e - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="37d96-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>
<span data-ttu-id="37d96-113">Script 'ScriptRequireLicenseAcceptance' depende do módulo 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="37d96-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="37d96-114">Não é pedido ao utilizador para aceitar licença como - AcceptLicense está especificado.</span><span class="sxs-lookup"><span data-stu-id="37d96-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="37d96-115">obter mais detalhes</span><span class="sxs-lookup"><span data-stu-id="37d96-115">More details</span></span>
### <a name="require-license-acceptance-support-for-modulesmodulerequirelicenseacceptancemd"></a>[<span data-ttu-id="37d96-116">Precisar do suporte de aceitação de licença para módulos</span><span class="sxs-lookup"><span data-stu-id="37d96-116">Require License Acceptance support for Modules</span></span>](../module/RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[<span data-ttu-id="37d96-117">Precisam de suporte de aceitação de licença no PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="37d96-117">Require License Acceptance support on PowerShellGallery</span></span>](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[<span data-ttu-id="37d96-118">Solicite a aceitação de licença implementar na automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="37d96-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)
