---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: RequireLicenseAcceptanceScript
ms.openlocfilehash: 4a2dc39c2b6c380fb4ca94f9fd071ed9cdb35049
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="b9d5d-103">Exigir a aceitação de licença para os Scripts</span><span class="sxs-lookup"><span data-stu-id="b9d5d-103">Requiring License Acceptance for Scripts</span></span>

<span data-ttu-id="b9d5d-104">Aceitação de licença não é suportada para os scripts.</span><span class="sxs-lookup"><span data-stu-id="b9d5d-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="b9d5d-105">No entanto, o cenário em que um script depende de um módulo que requer a aceitação de licença é suportado.</span><span class="sxs-lookup"><span data-stu-id="b9d5d-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="b9d5d-106">Script commands(Install-Script/Save-Script/Update-Script) suportar um novo parâmetro - AcceptLicense que funciona como se o utilizador vimos a licença.</span><span class="sxs-lookup"><span data-stu-id="b9d5d-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="b9d5d-107">Se não for especificado - AcceptLicense; o utilizador será apresentado license.txt para o módulo dependente e pedido para aceitar a licença.</span><span class="sxs-lookup"><span data-stu-id="b9d5d-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="b9d5d-108">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="b9d5d-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="b9d5d-109">Exemplo 1: O Script de instalação com as dependências de exigir a aceitação de licença</span><span class="sxs-lookup"><span data-stu-id="b9d5d-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>
<span data-ttu-id="b9d5d-110">Script 'ScriptRequireLicenseAcceptance' depende do módulo 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="b9d5d-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="b9d5d-111">Solicitadas ao utilizador para aceitar licença.</span><span class="sxs-lookup"><span data-stu-id="b9d5d-111">User is prompted to Accept License.</span></span>
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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="b9d5d-112">Exemplo 2: O Script de instalação com as dependências de exigir a aceitação de licença e - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="b9d5d-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>
<span data-ttu-id="b9d5d-113">Script 'ScriptRequireLicenseAcceptance' depende do módulo 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="b9d5d-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="b9d5d-114">Não é pedido ao utilizador para aceitar licença como - AcceptLicense está especificado.</span><span class="sxs-lookup"><span data-stu-id="b9d5d-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="b9d5d-115">obter mais detalhes</span><span class="sxs-lookup"><span data-stu-id="b9d5d-115">More details</span></span>
### <a name="require-license-acceptance-support-for-modulesmodulerequirelicenseacceptancemd"></a>[<span data-ttu-id="b9d5d-116">Precisar do suporte de aceitação de licença para módulos</span><span class="sxs-lookup"><span data-stu-id="b9d5d-116">Require License Acceptance support for Modules</span></span>](../module/RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[<span data-ttu-id="b9d5d-117">Precisam de suporte de aceitação de licença no PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="b9d5d-117">Require License Acceptance support on PowerShellGallery</span></span>](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[<span data-ttu-id="b9d5d-118">Solicitar a Aceitação da Licença ao Implementar a Automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="b9d5d-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)