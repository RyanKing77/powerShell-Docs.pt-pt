---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Exigir a aceitação de licença para os scripts
ms.openlocfilehash: e7101eb6a480dd87965b7b9be9d49583042b603f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084679"
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="93b18-103">Exigir a aceitação de licença para os scripts</span><span class="sxs-lookup"><span data-stu-id="93b18-103">Requiring license acceptance for scripts</span></span>

<span data-ttu-id="93b18-104">Aceitação da licença não é suportada para os scripts.</span><span class="sxs-lookup"><span data-stu-id="93b18-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="93b18-105">No entanto, o cenário em que um script depende de um módulo que requer a aceitação da licença é suportado.</span><span class="sxs-lookup"><span data-stu-id="93b18-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="93b18-106">Script commands(Install-Script/Save-Script/Update-Script) suportar um novo parâmetro - AcceptLicense que se comporta como se o utilizador viu a licença.</span><span class="sxs-lookup"><span data-stu-id="93b18-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="93b18-107">Se não for especificado - AcceptLicense; o utilizador será mostrado license.txt módulo dependente de e -lhe pedido para aceitar a licença.</span><span class="sxs-lookup"><span data-stu-id="93b18-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="93b18-108">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="93b18-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="93b18-109">Exemplo 1: Script de instalação com as dependências que exigem a aceitação de licença</span><span class="sxs-lookup"><span data-stu-id="93b18-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>

<span data-ttu-id="93b18-110">Script 'ScriptRequireLicenseAcceptance"depende do módulo 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="93b18-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="93b18-111">Usuário é solicitado a aceitar a licença.</span><span class="sxs-lookup"><span data-stu-id="93b18-111">User is prompted to Accept License.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="93b18-112">Exemplo 2: Script de instalação com as dependências que exigem a aceitação da licença e - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="93b18-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="93b18-113">Script 'ScriptRequireLicenseAcceptance"depende do módulo 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="93b18-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="93b18-114">Utilizador não é pedido para aceitar a licença como - AcceptLicense está especificado.</span><span class="sxs-lookup"><span data-stu-id="93b18-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="93b18-115">Obter mais detalhes</span><span class="sxs-lookup"><span data-stu-id="93b18-115">More details</span></span>

- [<span data-ttu-id="93b18-116">Necessitar de suporte de aceitação de licença para módulos</span><span class="sxs-lookup"><span data-stu-id="93b18-116">Require License Acceptance support for Modules</span></span>](module-license-acceptance.md)
- [<span data-ttu-id="93b18-117">Precisam de suporte de aceitação da licença no PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="93b18-117">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [<span data-ttu-id="93b18-118">Solicitar a Aceitação da Licença ao Implementar a Automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="93b18-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-packages/deploy-to-azure-automation.md)
