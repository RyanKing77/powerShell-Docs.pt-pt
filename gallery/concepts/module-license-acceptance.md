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
# <a name="modules-requiring-license-acceptance"></a>Módulos que Exigem a Aceitação da Licença

## <a name="synopsis"></a>SINOPSE

Os departamentos jurídicos para alguns editores de módulo exigem que os clientes explicitamente têm de aceitar a licença antes de instalar o módulo da galeria do PowerShell. Se um utilizador instala, atualiza ou guarda um módulo com o PowerShellGet, quer diretamente ou como uma dependência para outro item, e esse módulo exige que o utilizador aceitar uma licença, o utilizador tem de indicar aceitarem a licença ou a operação falhar.

## <a name="publish-requirements-for-modules"></a>Publicar os requisitos para módulos

Módulos que gostariam de exigir que os utilizadores aceitar a licença devem cumprir seguintes requisitos:

- Secção de PSData do manifesto do módulo deve incluir RequireLicenseAcceptance = $True.
- Módulo deve conter license.txt ficheiro no diretório de raiz.
- Manifesto do módulo deve conter o Uri de licença.
- Módulo deve ser publicado com o PowerShellGet formato versão 2.0 e superior.

## <a name="impact-on-installsaveupdate-module"></a>Impacto sobre a instalação/Save/atualização-Module

- Cmdlets de instalação/Save/atualização irá suportar um novo parâmetro – AcceptLicense que irão comportar-se como se o utilizador viu a licença.
- Se RequiredLicenseAcceptance é verdadeiro e – AcceptLicense não for especificado, o utilizador será mostrado o license.txt e lhe for pedido com: &quot;aceita estes termos (Sim/não/YesToAll/NoToAll) de licenciamento&quot;.
  - Se a licença é aceite
    - **Save-Module:** o módulo será copiado para o utilizador&#39;sistema s
    - **Install-Module:** o módulo será copiado para o utilizador&#39;sistema s para a pasta adequada (com base no escopo)
    - **Atualização-Module:** o módulo será atualizado.
  - Se a licença será recusada.
    - Será possível cancelar a operação.
    - Todos os cmdlets verificará os metadados (requireLicenseAcceptance e versão do formato) que indica que uma aceitação de licença é necessária
    - Se a versão de formato do cliente é anterior 2.0, a operação irá falhar e pedir ao utilizador para atualizar o cliente.
    - Se o módulo foi publicado com a versão de formato mais antigo do que a 2.0, o sinalizador de requireLicenseAcceptance será ignorado.

## <a name="module-dependencies"></a>Dependências do módulo

- Durante a instalação/Save/atualizar a operação, se um módulo dependente (outra coisa depende o módulo) requer a aceitação da licença, em seguida, o comportamento de aceitação de licença (acima) será necessária.
- Se a versão do módulo já está listada no catálogo do local, como a ser instalado no sistema, podemos poderia ignorar a verificação de licença.
- Durante a operação de instalação/Save/atualização, se um módulo dependente requer uma licença e a aceitação de licença não ocorre, a operação irá falhar e siga processos normais para o item não foi possível guardar/instalação/atualização.

## <a name="impact-on--force"></a>Impacto no - Force

Especificar `–Force` não é suficiente para aceitar uma licença. `–AcceptLicense` é necessária permissão instalar. Se `–Force` for especificado, RequiredLicenseAcceptance for True, e `–AcceptLicense` não for especificada, a operação falhará.

## <a name="examples"></a>EXEMPLOS

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a>Exemplo 1: O manifesto de módulo de atualização para exigir a aceitação da licença

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

Este comando atualiza o arquivo de manifesto e define o sinalizador de RequireLicenseAcceptance como true.

### <a name="example-2-install-module-requiring-license-acceptance"></a>Exemplo 2: Aceitação da licença que exigem que o módulo de instalação

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

Este comando mostra a licença do ficheiro de license.txt e solicita ao utilizador para aceitar a licença.

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a>Exemplo 3: Instalar módulo exigir aceitação da licença com - AcceptLicense

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Módulo é instalado sem qualquer pedido para aceitar a licença.

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a>Exemplo 4: Instalar módulo exigir aceitação da licença com - Force

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

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a>Exemplo 5: Install Module com dependências que exigem a aceitação de licença

Módulo 'ModuleWithDependency"depende do módulo 'ModuleRequireLicenseAcceptance'. Usuário é solicitado a aceitar a licença.

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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Exemplo 6: Install Module com dependências que exigem a aceitação da licença e - AcceptLicense

Módulo 'ModuleWithDependency"depende do módulo 'ModuleRequireLicenseAcceptance'. Utilizador não é pedido para aceitar a licença como - AcceptLicense está especificado.

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a>Exemplo 7: Instalar o módulo que exigem a aceitação de licença num cliente mais antigo do que PSGetFormatVersion 2.0

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a>Exemplo 8: Guardar o módulo que exigem a aceitação de licença

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

Este comando mostra a licença do ficheiro de license.txt e solicita ao utilizador para aceitar a licença.

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a>Exemplo 9: Guardar o módulo que exigem a aceitação de licença com - AcceptLicense

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

Módulo é guardado sem qualquer pedido para aceitar a licença.

### <a name="example-10-update-module-requiring-license-acceptance"></a>Exemplo 10: Aceitação da licença que exigem que o módulo de atualização

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

Este comando mostra a licença do ficheiro de license.txt e solicita ao utilizador para aceitar a licença.

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a>Exemplo 11: Atualização módulo exigir aceitação da licença com - AcceptLicense

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Módulo é atualizado sem qualquer pedido para aceitar a licença.

## <a name="more-details"></a>Obter mais detalhes

[Exigir a Aceitação da Licença para os Scripts](./script-license-acceptance.md)

[Precisam de suporte de aceitação da licença no PowerShellGallery](../how-to/working-with-items/items-that-require-license-acceptance.md)

[Solicitar a Aceitação da Licença ao Implementar a Automatização do Azure](../how-to/working-with-items/deploy-to-azure-automation.md)