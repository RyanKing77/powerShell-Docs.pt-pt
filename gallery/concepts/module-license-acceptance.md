---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Módulos que Exigem a Aceitação da Licença
ms.openlocfilehash: 93f92f6e83bcf18a40c3d89eb39a154e16ca5063
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893115"
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="4cc5e-103">Módulos que Exigem a Aceitação da Licença</span><span class="sxs-lookup"><span data-stu-id="4cc5e-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="4cc5e-104">SINOPSE</span><span class="sxs-lookup"><span data-stu-id="4cc5e-104">SYNOPSIS</span></span>

<span data-ttu-id="4cc5e-105">Os departamentos jurídicos para alguns editores de módulo exigem que os clientes explicitamente têm de aceitar a licença antes de instalar o módulo da galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="4cc5e-106">Se um utilizador instala, atualiza ou guarda um módulo com o PowerShellGet, quer diretamente ou como uma dependência para outro item, e esse módulo exige que o utilizador aceitar uma licença, o utilizador tem de indicar aceitarem a licença ou a operação falhar.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another item, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="4cc5e-107">Publicar os requisitos para módulos</span><span class="sxs-lookup"><span data-stu-id="4cc5e-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="4cc5e-108">Módulos que gostariam de exigir que os utilizadores aceitar a licença devem cumprir seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="4cc5e-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>

- <span data-ttu-id="4cc5e-109">Secção de PSData do manifesto do módulo deve incluir RequireLicenseAcceptance = $True.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="4cc5e-110">Módulo deve conter license.txt ficheiro no diretório de raiz.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="4cc5e-111">Manifesto do módulo deve conter o Uri de licença.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="4cc5e-112">Módulo deve ser publicado com o PowerShellGet formato versão 2.0 e superior.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="4cc5e-113">Impacto sobre a instalação/Save/atualização-Module</span><span class="sxs-lookup"><span data-stu-id="4cc5e-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="4cc5e-114">Cmdlets de instalação/Save/atualização irá suportar um novo parâmetro – AcceptLicense que irão comportar-se como se o utilizador viu a licença.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-114">Install/Save/Update cmdlets will support a new parameter –AcceptLicense that will behave as though the user saw the license.</span></span>
- <span data-ttu-id="4cc5e-115">Se RequiredLicenseAcceptance é verdadeiro e – AcceptLicense não for especificado, o utilizador será mostrado o license.txt e lhe for pedido com: &quot;aceita estes termos (Sim/não/YesToAll/NoToAll) de licenciamento&quot;.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-115">If RequiredLicenseAcceptance is True and –AcceptLicense is not specified, the user will be shown the license.txt, and prompted with: &quot;Do you accept these license terms (Yes/No/YesToAll/NoToAll)&quot;.</span></span>
  - <span data-ttu-id="4cc5e-116">Se a licença é aceite</span><span class="sxs-lookup"><span data-stu-id="4cc5e-116">If the license is accepted</span></span>
    - <span data-ttu-id="4cc5e-117">**Save-Module:** o módulo será copiado para o utilizador&#39;sistema s</span><span class="sxs-lookup"><span data-stu-id="4cc5e-117">**Save-Module:** the module will be copied to the user&#39;s system</span></span>
    - <span data-ttu-id="4cc5e-118">**Install-Module:** o módulo será copiado para o utilizador&#39;sistema s para a pasta adequada (com base no escopo)</span><span class="sxs-lookup"><span data-stu-id="4cc5e-118">**Install-Module:** the module will be copied to the user&#39;s system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="4cc5e-119">**Atualização-Module:** o módulo será atualizado.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-119">**Update-Module:** the module will be updated.</span></span>
  - <span data-ttu-id="4cc5e-120">Se a licença será recusada.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-120">If the license is declined.</span></span>
    - <span data-ttu-id="4cc5e-121">Será possível cancelar a operação.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-121">Operation will be cancelled.</span></span>
    - <span data-ttu-id="4cc5e-122">Todos os cmdlets verificará os metadados (requireLicenseAcceptance e versão do formato) que indica que uma aceitação de licença é necessária</span><span class="sxs-lookup"><span data-stu-id="4cc5e-122">All cmdlets will check for the metadata(requireLicenseAcceptance and Format Version) that says a license acceptance is required</span></span>
    - <span data-ttu-id="4cc5e-123">Se a versão de formato do cliente é anterior 2.0, a operação irá falhar e pedir ao utilizador para atualizar o cliente.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-123">If format version of client is older than 2.0, operation will fail and ask the user to update the client.</span></span>
    - <span data-ttu-id="4cc5e-124">Se o módulo foi publicado com a versão de formato mais antigo do que a 2.0, o sinalizador de requireLicenseAcceptance será ignorado.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag will be ignored.</span></span>

## <a name="module-dependencies"></a><span data-ttu-id="4cc5e-125">Dependências do módulo</span><span class="sxs-lookup"><span data-stu-id="4cc5e-125">Module Dependencies</span></span>

- <span data-ttu-id="4cc5e-126">Durante a instalação/Save/atualizar a operação, se um módulo dependente (outra coisa depende o módulo) requer a aceitação da licença, em seguida, o comportamento de aceitação de licença (acima) será necessária.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) will be required.</span></span>
- <span data-ttu-id="4cc5e-127">Se a versão do módulo já está listada no catálogo do local, como a ser instalado no sistema, podemos poderia ignorar a verificação de licença.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="4cc5e-128">Durante a operação de instalação/Save/atualização, se um módulo dependente requer uma licença e a aceitação de licença não ocorre, a operação irá falhar e siga processos normais para o item não foi possível guardar/instalação/atualização.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation will fail and follow normal processes for the item failed to install/save/update.</span></span>

## <a name="impact-on--force"></a><span data-ttu-id="4cc5e-129">Impacto no - Force</span><span class="sxs-lookup"><span data-stu-id="4cc5e-129">Impact on -Force</span></span>

<span data-ttu-id="4cc5e-130">Especificar `–Force` não é suficiente para aceitar uma licença.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-130">Specifying `–Force` is NOT sufficient to accept a license.</span></span> <span data-ttu-id="4cc5e-131">`–AcceptLicense` é necessária permissão instalar.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-131">`–AcceptLicense` is required for permission to install.</span></span> <span data-ttu-id="4cc5e-132">Se `–Force` for especificado, RequiredLicenseAcceptance for True, e `–AcceptLicense` não for especificada, a operação falhará.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-132">If `–Force` is specified, RequiredLicenseAcceptance is True, and `–AcceptLicense` is NOT specified, the operation will fail.</span></span>

## <a name="examples"></a><span data-ttu-id="4cc5e-133">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="4cc5e-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="4cc5e-134">Exemplo 1: O manifesto de módulo de atualização para exigir a aceitação da licença</span><span class="sxs-lookup"><span data-stu-id="4cc5e-134">Example 1: Update Module Manifest to require license acceptance</span></span>

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

<span data-ttu-id="4cc5e-135">Este comando atualiza o arquivo de manifesto e define o sinalizador de RequireLicenseAcceptance como true.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>

### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="4cc5e-136">Exemplo 2: Aceitação da licença que exigem que o módulo de instalação</span><span class="sxs-lookup"><span data-stu-id="4cc5e-136">Example 2: Install Module requiring license acceptance</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
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

<span data-ttu-id="4cc5e-137">Este comando mostra a licença do ficheiro de license.txt e solicita ao utilizador para aceitar a licença.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-137">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="4cc5e-138">Exemplo 3: Instalar módulo exigir aceitação da licença com - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="4cc5e-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="4cc5e-139">Módulo é instalado sem qualquer pedido para aceitar a licença.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="4cc5e-140">Exemplo 4: Instalar módulo exigir aceitação da licença com - Force</span><span class="sxs-lookup"><span data-stu-id="4cc5e-140">Example 4: Install Module requiring license acceptance with -Force</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -Force
```

```output
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="4cc5e-141">Exemplo 5: Install Module com dependências que exigem a aceitação de licença</span><span class="sxs-lookup"><span data-stu-id="4cc5e-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>

<span data-ttu-id="4cc5e-142">Módulo 'ModuleWithDependency"depende do módulo 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-142">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="4cc5e-143">Usuário é solicitado a aceitar a licença.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-143">User is prompted to Accept License.</span></span>

```powershell
Install-Module -Name ModuleWithDependency
```

```output
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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="4cc5e-144">Exemplo 6: Install Module com dependências que exigem a aceitação da licença e - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="4cc5e-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="4cc5e-145">Módulo 'ModuleWithDependency"depende do módulo 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-145">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="4cc5e-146">Utilizador não é pedido para aceitar a licença como - AcceptLicense está especificado.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-146">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="4cc5e-147">Exemplo 7: Instalar o módulo que exigem a aceitação de licença num cliente mais antigo do que PSGetFormatVersion 2.0</span><span class="sxs-lookup"><span data-stu-id="4cc5e-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="4cc5e-148">Exemplo 8: Guardar o módulo que exigem a aceitação de licença</span><span class="sxs-lookup"><span data-stu-id="4cc5e-148">Example 8: Save Module requiring license acceptance</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved
```

```output
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

<span data-ttu-id="4cc5e-149">Este comando mostra a licença do ficheiro de license.txt e solicita ao utilizador para aceitar a licença.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-149">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="4cc5e-150">Exemplo 9: Guardar o módulo que exigem a aceitação de licença com - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="4cc5e-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

<span data-ttu-id="4cc5e-151">Módulo é guardado sem qualquer pedido para aceitar a licença.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="4cc5e-152">Exemplo 10: Aceitação da licença que exigem que o módulo de atualização</span><span class="sxs-lookup"><span data-stu-id="4cc5e-152">Example 10: Update Module requiring license acceptance</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance
```

```output
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

<span data-ttu-id="4cc5e-153">Este comando mostra a licença do ficheiro de license.txt e solicita ao utilizador para aceitar a licença.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-153">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="4cc5e-154">Exemplo 11: Atualização módulo exigir aceitação da licença com - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="4cc5e-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="4cc5e-155">Módulo é atualizado sem qualquer pedido para aceitar a licença.</span><span class="sxs-lookup"><span data-stu-id="4cc5e-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="4cc5e-156">Obter mais detalhes</span><span class="sxs-lookup"><span data-stu-id="4cc5e-156">More details</span></span>

[<span data-ttu-id="4cc5e-157">Exigir a Aceitação da Licença para os Scripts</span><span class="sxs-lookup"><span data-stu-id="4cc5e-157">Require License Acceptance for Scripts</span></span>](./script-license-acceptance.md)

[<span data-ttu-id="4cc5e-158">Precisam de suporte de aceitação da licença no PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="4cc5e-158">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-items/items-that-require-license-acceptance.md)

[<span data-ttu-id="4cc5e-159">Solicitar a Aceitação da Licença ao Implementar a Automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="4cc5e-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-items/deploy-to-azure-automation.md)