---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Módulos que Exigem a Aceitação da Licença
ms.openlocfilehash: fe197ea271e18580a221ad4d5245b685bd81775b
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34049094"
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="811e9-103">Módulos que Exigem a Aceitação da Licença</span><span class="sxs-lookup"><span data-stu-id="811e9-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="811e9-104">RESUMO</span><span class="sxs-lookup"><span data-stu-id="811e9-104">SYNOPSIS</span></span>

<span data-ttu-id="811e9-105">Departamentos jurídicos para algumas editores de módulo exigem que os clientes têm de aceitar explicitamente a licença antes de instalar o respetivo módulo a partir da galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="811e9-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="811e9-106">Se um utilizador instala, atualiza ou guarda um módulo com o PowerShellGet, quer diretamente ou como uma dependência de outro item e esse módulo exige que o utilizador aceitar uma licença, o utilizador tem de indicar que aceitarem a licença ou a operação falhar.</span><span class="sxs-lookup"><span data-stu-id="811e9-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another item, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="811e9-107">Publicar os requisitos para módulos</span><span class="sxs-lookup"><span data-stu-id="811e9-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="811e9-108">Módulos que gostaria para exigir que os utilizadores aceitem licença devem satisfazer os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="811e9-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>

- <span data-ttu-id="811e9-109">PSData secção do manifesto de módulo de deve incluir RequireLicenseAcceptance = $True.</span><span class="sxs-lookup"><span data-stu-id="811e9-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="811e9-110">Módulo deve conter o ficheiro de license.txt no diretório de raiz.</span><span class="sxs-lookup"><span data-stu-id="811e9-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="811e9-111">O manifesto de módulo deve conter o Uri de licença.</span><span class="sxs-lookup"><span data-stu-id="811e9-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="811e9-112">Módulo deve ser publicado com PowerShellGet formato versão 2.0 e superior.</span><span class="sxs-lookup"><span data-stu-id="811e9-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="811e9-113">Impacto na instalação/Save/atualização-Module</span><span class="sxs-lookup"><span data-stu-id="811e9-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="811e9-114">Cmdlets de instalação/Save/atualização irá suportar um novo parâmetro – AcceptLicense que irão comportar-se como se o utilizador vimos a licença.</span><span class="sxs-lookup"><span data-stu-id="811e9-114">Install/Save/Update cmdlets will support a new parameter –AcceptLicense that will behave as though the user saw the license.</span></span>
- <span data-ttu-id="811e9-115">Se RequiredLicenseAcceptance for True e – AcceptLicense não for especificado, o utilizador será apresentado o license.txt e apresentado: &quot;aceita estes termos (Sim/não/YesToAll/NoToAll) de licenciamento&quot;.</span><span class="sxs-lookup"><span data-stu-id="811e9-115">If RequiredLicenseAcceptance is True and –AcceptLicense is not specified, the user will be shown the license.txt, and prompted with: &quot;Do you accept these license terms (Yes/No/YesToAll/NoToAll)&quot;.</span></span>
  - <span data-ttu-id="811e9-116">Se a licença é aceite</span><span class="sxs-lookup"><span data-stu-id="811e9-116">If the license is accepted</span></span>
    - <span data-ttu-id="811e9-117">**Guardar-Module:** o módulo será copiado para o utilizador&#39;sistema s</span><span class="sxs-lookup"><span data-stu-id="811e9-117">**Save-Module:** the module will be copied to the user&#39;s system</span></span>
    - <span data-ttu-id="811e9-118">**Módulo de instalação:** o módulo será copiado para o utilizador&#39;sistema s para a pasta adequada (com base no âmbito)</span><span class="sxs-lookup"><span data-stu-id="811e9-118">**Install-Module:** the module will be copied to the user&#39;s system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="811e9-119">**Módulo de atualização:** o módulo será atualizado.</span><span class="sxs-lookup"><span data-stu-id="811e9-119">**Update-Module:** the module will be updated.</span></span>
  - <span data-ttu-id="811e9-120">Se a licença for recusada.</span><span class="sxs-lookup"><span data-stu-id="811e9-120">If the license is declined.</span></span>
    - <span data-ttu-id="811e9-121">Será possível cancelar a operação.</span><span class="sxs-lookup"><span data-stu-id="811e9-121">Operation will be cancelled.</span></span>
- <span data-ttu-id="811e9-122">Todos os cmdlets irá verificar os metadados (requireLicenseAcceptance e versão de formato) que indica a que aceitação de licença é necessária</span><span class="sxs-lookup"><span data-stu-id="811e9-122">All cmdlets will check for the metadata(requireLicenseAcceptance and Format Version) that says a license acceptance is required</span></span>
  - <span data-ttu-id="811e9-123">Se a versão do formato do cliente é anterior ao 2.0, operação falharão e pedir ao utilizador para atualizar o cliente.</span><span class="sxs-lookup"><span data-stu-id="811e9-123">If format version of client is older than 2.0, operation will fail and ask the user to update the client.</span></span>
  - <span data-ttu-id="811e9-124">Se o módulo foi publicado com a versão de formato mais antigo do que 2.0, requireLicenseAcceptance sinalizador será ignorado.</span><span class="sxs-lookup"><span data-stu-id="811e9-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag will be ignored.</span></span>


 ## <a name="module-dependencies"></a><span data-ttu-id="811e9-125">Dependências de módulo</span><span class="sxs-lookup"><span data-stu-id="811e9-125">Module Dependencies</span></span>
- <span data-ttu-id="811e9-126">Durante a instalação/Save/atualização, será necessária operação, se necessitar de um módulo dependente (autorize depende do módulo) aceitação de licença, em seguida, o comportamento de aceitação de licença (acima).</span><span class="sxs-lookup"><span data-stu-id="811e9-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) will be required.</span></span>
- <span data-ttu-id="811e9-127">Se a versão do módulo já está listado no catálogo do local, como a ser instalados no sistema, iremos seria ignorar a verificação de licença.</span><span class="sxs-lookup"><span data-stu-id="811e9-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="811e9-128">Durante a operação de guardar/instalação/atualização, se um módulo dependente é necessária uma licença e a aceitação de licença não ocorre, a operação irá falhar e seguir os processos normais para o item não foi possível guardar/instalação/atualização.</span><span class="sxs-lookup"><span data-stu-id="811e9-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation will fail and follow normal processes for the item failed to install/save/update.</span></span>

 ## <a name="impact-on--force"></a><span data-ttu-id="811e9-129">Impacto no - Force</span><span class="sxs-lookup"><span data-stu-id="811e9-129">Impact on -Force</span></span>

<span data-ttu-id="811e9-130">Especificar – Force não é suficiente para aceitar uma licença.</span><span class="sxs-lookup"><span data-stu-id="811e9-130">Specifying –Force is NOT sufficient to accept a license.</span></span> <span data-ttu-id="811e9-131">– AcceptLicense é necessária permissão instalar.</span><span class="sxs-lookup"><span data-stu-id="811e9-131">–AcceptLicense is required for permission to install.</span></span> <span data-ttu-id="811e9-132">Se – Force não for especificado, RequiredLicenseAcceptance for True e – AcceptLicense não for especificada, a operação falhará.</span><span class="sxs-lookup"><span data-stu-id="811e9-132">If –Force is specified, RequiredLicenseAcceptance is True, and –AcceptLicense is NOT specified, the operation will fail.</span></span>

## <a name="examples"></a><span data-ttu-id="811e9-133">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="811e9-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="811e9-134">Exemplo 1: O manifesto de módulo de atualização para exigir a aceitação de licença</span><span class="sxs-lookup"><span data-stu-id="811e9-134">Example 1: Update Module Manifest to require license acceptance</span></span>

```PowerShell
PS> Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance

PrivateData = @{

    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

<span data-ttu-id="811e9-135">Este comando atualiza o ficheiro de manifesto e define o sinalizador de RequireLicenseAcceptance como true.</span><span class="sxs-lookup"><span data-stu-id="811e9-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>

### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="811e9-136">Exemplo 2: Aceitação de licença que exigem que instalar módulo</span><span class="sxs-lookup"><span data-stu-id="811e9-136">Example 2: Install Module requiring license acceptance</span></span>

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):

```

<span data-ttu-id="811e9-137">Este comando mostra a licença do ficheiro de license.txt e pede ao utilizador para aceitar a licença.</span><span class="sxs-lookup"><span data-stu-id="811e9-137">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="811e9-138">Exemplo 3: Aceitação de licença de necessitando de módulo de instalação com - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="811e9-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="811e9-139">Módulo é instalado sem qualquer linha de comandos para aceitar a licença.</span><span class="sxs-lookup"><span data-stu-id="811e9-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="811e9-140">Exemplo 4: Aceitação de licença de necessitando de módulo de instalação com - Force</span><span class="sxs-lookup"><span data-stu-id="811e9-140">Example 4: Install Module requiring license acceptance with -Force</span></span>

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance -Force
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="811e9-141">Exemplo 5: Instalar módulo com dependências exigir a aceitação de licença</span><span class="sxs-lookup"><span data-stu-id="811e9-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>

<span data-ttu-id="811e9-142">Módulo 'ModuleWithDependency' depende do módulo 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="811e9-142">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="811e9-143">Solicitadas ao utilizador para aceitar licença.</span><span class="sxs-lookup"><span data-stu-id="811e9-143">User is prompted to Accept License.</span></span>

```PowerShell
PS> Install-Module -Name ModuleWithDependency

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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="811e9-144">Exemplo 6: Instalar módulo com dependências exigir a aceitação de licença e - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="811e9-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="811e9-145">Módulo 'ModuleWithDependency' depende do módulo 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="811e9-145">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="811e9-146">Não é pedido ao utilizador para aceitar licença como - AcceptLicense está especificado.</span><span class="sxs-lookup"><span data-stu-id="811e9-146">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS>  Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="811e9-147">Exemplo 7: Instalar o módulo de exigir a aceitação de licença num cliente anterior ao PSGetFormatVersion 2.0</span><span class="sxs-lookup"><span data-stu-id="811e9-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>

```PowerShell
PS C:\windows\system32> Install-Module -Name ModuleRequireLicenseAcceptance

WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.

```

### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="811e9-148">Exemplo 8: Guardar módulo exigir a aceitação de licença</span><span class="sxs-lookup"><span data-stu-id="811e9-148">Example 8: Save Module requiring license acceptance</span></span>

```PowerShell
PS> Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="811e9-149">Este comando mostra a licença do ficheiro de license.txt e pede ao utilizador para aceitar a licença.</span><span class="sxs-lookup"><span data-stu-id="811e9-149">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="811e9-150">Exemplo 9: Guardar módulo exigir a aceitação de licença com - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="811e9-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>

```PowerShell
PS> Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

<span data-ttu-id="811e9-151">Módulo é guardado sem qualquer linha de comandos para aceitar a licença.</span><span class="sxs-lookup"><span data-stu-id="811e9-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="811e9-152">Exemplo 10: Aceitação de licença de necessitando de módulo de atualização</span><span class="sxs-lookup"><span data-stu-id="811e9-152">Example 10: Update Module requiring license acceptance</span></span>

```PowerShell
PS> Update-Module -Name ModuleRequireLicenseAcceptance

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="811e9-153">Este comando mostra a licença do ficheiro de license.txt e pede ao utilizador para aceitar a licença.</span><span class="sxs-lookup"><span data-stu-id="811e9-153">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="811e9-154">Exemplo 11: Aceitação de licença de necessitando de módulo de atualização com - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="811e9-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>

```PowerShell
PS> Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="811e9-155">Módulo é atualizado sem qualquer linha de comandos para aceitar a licença.</span><span class="sxs-lookup"><span data-stu-id="811e9-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="811e9-156">obter mais detalhes</span><span class="sxs-lookup"><span data-stu-id="811e9-156">More details</span></span>

### <a name="require-license-acceptance-for-scriptsscript-license-acceptancemd"></a>[<span data-ttu-id="811e9-157">Exigir a Aceitação da Licença para os Scripts</span><span class="sxs-lookup"><span data-stu-id="811e9-157">Require License Acceptance for Scripts</span></span>](./script-license-acceptance.md)

### <a name="require-license-acceptance-support-on-powershellgalleryhow-toworking-with-itemsitems-that-require-license-acceptancemd"></a>[<span data-ttu-id="811e9-158">Precisam de suporte de aceitação de licença no PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="811e9-158">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-items/items-that-require-license-acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationhow-toworking-with-itemsdeploy-to-azure-automationmd"></a>[<span data-ttu-id="811e9-159">Solicitar a Aceitação da Licença ao Implementar a Automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="811e9-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-items/deploy-to-azure-automation.md)