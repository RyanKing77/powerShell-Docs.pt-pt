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
# <a name="requiring-license-acceptance-for-scripts"></a>Exigir a aceitação de licença para os scripts

Aceitação da licença não é suportada para os scripts. No entanto, o cenário em que um script depende de um módulo que requer a aceitação da licença é suportado.

Script commands(Install-Script/Save-Script/Update-Script) suportar um novo parâmetro - AcceptLicense que se comporta como se o utilizador viu a licença. Se não for especificado - AcceptLicense; o utilizador será mostrado license.txt módulo dependente de e -lhe pedido para aceitar a licença.

## <a name="examples"></a>EXEMPLOS

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Exemplo 1: Script de instalação com as dependências que exigem a aceitação de licença

Script 'ScriptRequireLicenseAcceptance"depende do módulo 'ModuleRequireLicenseAcceptance'. Usuário é solicitado a aceitar a licença.

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Exemplo 2: Script de instalação com as dependências que exigem a aceitação da licença e - AcceptLicense

Script 'ScriptRequireLicenseAcceptance"depende do módulo 'ModuleRequireLicenseAcceptance'. Utilizador não é pedido para aceitar a licença como - AcceptLicense está especificado.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>Obter mais detalhes

- [Necessitar de suporte de aceitação de licença para módulos](module-license-acceptance.md)
- [Precisam de suporte de aceitação da licença no PowerShellGallery](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [Solicitar a Aceitação da Licença ao Implementar a Automatização do Azure](../how-to/working-with-packages/deploy-to-azure-automation.md)
