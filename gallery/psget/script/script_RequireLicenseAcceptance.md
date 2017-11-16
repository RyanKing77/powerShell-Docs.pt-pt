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
# <a name="requiring-license-acceptance-for-scripts"></a>Exigir a aceitação de licença para os Scripts

Aceitação de licença não é suportada para os scripts. No entanto, o cenário em que um script depende de um módulo que requer a aceitação de licença é suportado.

Script commands(Install-Script/Save-Script/Update-Script) suportar um novo parâmetro - AcceptLicense que funciona como se o utilizador vimos a licença. Se não for especificado - AcceptLicense; o utilizador será apresentado license.txt para o módulo dependente e pedido para aceitar a licença.

## <a name="examples"></a>EXEMPLOS

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Exemplo 1: O Script de instalação com as dependências de exigir a aceitação de licença
Script 'ScriptRequireLicenseAcceptance' depende do módulo 'ModuleRequireLicenseAcceptance'. Solicitadas ao utilizador para aceitar licença.
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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Exemplo 2: O Script de instalação com as dependências de exigir a aceitação de licença e - AcceptLicense
Script 'ScriptRequireLicenseAcceptance' depende do módulo 'ModuleRequireLicenseAcceptance'. Não é pedido ao utilizador para aceitar licença como - AcceptLicense está especificado.
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>obter mais detalhes
### <a name="require-license-acceptance-support-for-modulesmodulerequirelicenseacceptancemd"></a>[Precisar do suporte de aceitação de licença para módulos](../module/RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[Precisam de suporte de aceitação de licença no PowerShellGallery](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[Solicite a aceitação de licença implementar na automatização do Azure](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)