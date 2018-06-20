---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Exigir a aceitação de licença para os scripts
ms.openlocfilehash: 6374c8c8536dd0c8f27580a5b8895b8db18424f9
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34049016"
---
# <a name="requiring-license-acceptance-for-scripts"></a>Exigir a aceitação de licença para os scripts

Aceitação de licença não é suportada para os scripts. No entanto, o cenário em que um script depende de um módulo que requer a aceitação de licença é suportado.

Script commands(Install-Script/Save-Script/Update-Script) suportar um novo parâmetro - AcceptLicense que funciona como se o utilizador vimos a licença. Se não for especificado - AcceptLicense; o utilizador será apresentado license.txt para o módulo dependente e pedido para aceitar a licença.

## <a name="examples"></a>EXEMPLOS

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Exemplo 1: O Script de instalação com as dependências de exigir a aceitação de licença

Script 'ScriptRequireLicenseAcceptance' depende do módulo 'ModuleRequireLicenseAcceptance'. Solicitadas ao utilizador para aceitar licença.

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Exemplo 2: O Script de instalação com as dependências de exigir a aceitação de licença e - AcceptLicense

Script 'ScriptRequireLicenseAcceptance' depende do módulo 'ModuleRequireLicenseAcceptance'. Não é pedido ao utilizador para aceitar licença como - AcceptLicense está especificado.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>obter mais detalhes

- [Precisar do suporte de aceitação de licença para módulos](module-license-acceptance.md)
- [Precisam de suporte de aceitação de licença no PowerShellGallery](../how-to/working-with-items/items-that-require-license-acceptance.md)
- [Solicitar a Aceitação da Licença ao Implementar a Automatização do Azure](../how-to/working-with-items/deploy-to-azure-automation.md)