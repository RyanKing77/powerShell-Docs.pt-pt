---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 46a278b83edb9d8e3d75b0874603710d416be3b5
ms.sourcegitcommit: f4247d3f91d06ec392c4cd66921ce7d0456a2bd9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/05/2018
ms.locfileid: "50998525"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a>Palavra-chave de Import-DscResource suporta o parâmetro - ModuleVersion

Adicionámos um novo parâmetro para o `Import-DscResource` palavra-chave dynamic disponível durante a criação de configurações de DSC. Podem especificar exatamente qual versão do módulo para carregar os recursos de DSC de autores de configuração. A nova sintaxe da palavra-chave é:

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* **Nome**: nomes de um ou mais recursos para importar.
* **ModuleName**: nomes de módulos ou ModuleSpecification objetos de um ou mais módulos para importar.
* **ModuleVersion**: versão do módulo para importar. Se for utilizado, ModuleName têm de representar apenas um módulo por nome.

No ISE do Windows PowerShell, esta é apresentada com o IntelliSense:

![](../images/Import-DscResource-Modversion.jpg)

**Tenha em atenção**: a `–ModuleVersion` parâmetro só pode ser utilizado em combinação com o `–ModuleName` parâmetro. Não pode ser utilizado com nomes de recursos utilizando apenas a `–Name` parâmetro.

Antes disto, a única forma de especificar a versão do módulo, ao carregar os recursos de DSC era usando o objeto de especificação de módulo p. ex.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`
