---
ms.date: 2017-06-09
schema: 2.0.0
keywords: PowerShell
title: RequireLicenseAcceptance
ms.openlocfilehash: 260ccc1ee52d09a640e88203c5644f20f9723d6f
ms.sourcegitcommit: cd66d4f49ea762a31887af2c72d087b219ddbe10
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/11/2017
---
# <a name="modules-requiring-license-acceptance"></a>Exigir a aceitação de licença de módulos

## <a name="synopsis"></a>RESUMO
Departamentos jurídicos para algumas editores de módulo exigem que os clientes têm de aceitar explicitamente a licença antes de instalar o respetivo módulo a partir da galeria do PowerShell. Se um utilizador instala, atualiza ou guarda um módulo com o PowerShellGet, quer diretamente ou como uma dependência de outro item e esse módulo exige que o utilizador aceitar uma licença, o utilizador tem de indicar que aceitarem a licença ou a operação falhar.

## <a name="publish-requirements-for-modules"></a>Publicar os requisitos para módulos

Módulos que gostaria para exigir que os utilizadores aceitem licença devem satisfazer os seguintes requisitos:
    
- PSData secção do manifesto de módulo de deve incluir RequireLicenseAcceptance = $True.
- Módulo deve conter o ficheiro de license.txt no diretório de raiz.
- O manifesto de módulo deve conter o Uri de licença.
- Módulo deve ser publicado com PowerShellGet formato versão 2.0 e superior.

## <a name="impact-on-installsaveupdate-module"></a>Impacto na instalação/Save/atualização-Module

- Cmdlets de instalação/Save/atualização irá suportar um novo parâmetro – AcceptLicense que irão comportar-se como se o utilizador vimos a licença.
- Se RequiredLicenseAcceptance for True e – AcceptLicense não for especificado, o utilizador será apresentado o license.txt e apresentado: &quot;aceita estes termos (Sim/não/YesToAll/NoToAll) de licenciamento&quot;.
  - Se a licença é aceite
    - **Guardar-Module:** o módulo será copiado para o utilizador &#39; sistema s
    - **Módulo de instalação:** o módulo será copiado para o utilizador &#39; sistema s para a pasta adequada (com base no âmbito)
    - **Módulo de atualização:** o módulo será atualizado.
  - Se a licença for recusada. 
    - Será possível cancelar a operação.
- Todos os cmdlets irá verificar os metadados (requireLicenseAcceptance e versão de formato) que indica a que aceitação de licença é necessária
  - Se a versão do formato do cliente é anterior ao 2.0, operação falharão e pedir ao utilizador para atualizar o cliente.
  - Se o módulo foi publicado com a versão de formato mais antigo do que 2.0, requireLicenseAcceptance sinalizador será ignorado.

    
 ## <a name="module-dependencies"></a>Dependências de módulo
- Durante a instalação/Save/atualização, será necessária operação, se necessitar de um módulo dependente (autorize depende do módulo) aceitação de licença, em seguida, o comportamento de aceitação de licença (acima).
- Se a versão do módulo já está listado no catálogo do local, como a ser instalados no sistema, iremos seria ignorar a verificação de licença.
- Durante a operação de guardar/instalação/atualização, se um módulo dependente é necessária uma licença e a aceitação de licença não ocorre, a operação irá falhar e seguir os processos normais para o item não foi possível guardar/instalação/atualização.

 ## <a name="impact-on--force"></a>Impacto no - Force

Especificar – Force não é suficiente para aceitar uma licença. – AcceptLicense é necessária permissão instalar. Se – Force não for especificado, RequiredLicenseAcceptance for True e – AcceptLicense não for especificada, a operação falhará.

## <a name="examples"></a>EXEMPLOS

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a>Exemplo 1: O manifesto de módulo de atualização para exigir a aceitação de licença
```PowerShell
PS C:\> Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance

PrivateData = @{

    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable
    
 } # End of PrivateData hashtable
```
Este comando atualiza o ficheiro de manifesto e define o sinalizador de RequireLicenseAcceptance como true.
### <a name="example-2-install-module-requiring-license-acceptance"></a>Exemplo 2: Aceitação de licença que exigem que instalar módulo
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance

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
Este comando mostra a licença do ficheiro de license.txt e pede ao utilizador para aceitar a licença.

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a>Exemplo 3: Aceitação de licença de necessitando de módulo de instalação com - AcceptLicense
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```
Módulo é instalado sem qualquer linha de comandos para aceitar a licença.

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a>Exemplo 4: Aceitação de licença de necessitando de módulo de instalação com - Force
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance -Force
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a>Exemplo 5: Instalar módulo com dependências exigir a aceitação de licença
Módulo 'ModuleWithDependency' depende do módulo 'ModuleRequireLicenseAcceptance'. Solicitadas ao utilizador para aceitar licença.
```PowerShell
PS C:\> Install-Module -Name ModuleWithDependency

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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Exemplo 6: Instalar módulo com dependências exigir a aceitação de licença e - AcceptLicense
Módulo 'ModuleWithDependency' depende do módulo 'ModuleRequireLicenseAcceptance'. Não é pedido ao utilizador para aceitar licença como - AcceptLicense está especificado.
```PowerShell
PS C:\>  Install-Module -Name ModuleWithDependency -AcceptLicense
```
### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a>Exemplo 7: Instalar o módulo de exigir a aceitação de licença num cliente anterior ao PSGetFormatVersion 2.0
```PowerShell
PS C:\windows\system32> Install-Module -Name ModuleRequireLicenseAcceptance

WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.

```
### <a name="example-8-save-module-requiring-license-acceptance"></a>Exemplo 8: Guardar módulo exigir a aceitação de licença
```PowerShell
PS C:\> Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved

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
Este comando mostra a licença do ficheiro de license.txt e pede ao utilizador para aceitar a licença.

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a>Exemplo 9: Guardar módulo exigir a aceitação de licença com - AcceptLicense
```PowerShell
PS C:\> Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```
Módulo é guardado sem qualquer linha de comandos para aceitar a licença.

### <a name="example-10-update-module-requiring-license-acceptance"></a>Exemplo 10: Aceitação de licença de necessitando de módulo de atualização
```PowerShell
PS C:\> Update-Module -Name ModuleRequireLicenseAcceptance

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
Este comando mostra a licença do ficheiro de license.txt e pede ao utilizador para aceitar a licença.

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a>Exemplo 11: Aceitação de licença de necessitando de módulo de atualização com - AcceptLicense
```PowerShell
PS C:\> Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```
Módulo é atualizado sem qualquer linha de comandos para aceitar a licença.

## <a name="more-details"></a>obter mais detalhes
### <a name="require-license-acceptance-for-scriptsscriptscriptrequirelicenseacceptancemd"></a>[Solicite a aceitação de licença para os Scripts](../script/script_RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[Precisam de suporte de aceitação de licença no PowerShellGallery](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[Solicite a aceitação de licença implementar na automatização do Azure](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)
