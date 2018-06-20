---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: ce5afc2f90f78433b64bf5b41946fc7506c43504
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219655"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a>Palavra-chave de importação DscResource suporta o parâmetro - ModuleVersion

Foi adicionado um novo parâmetro para o `Import-DscResource` dinâmica palavra-chave disponível durante a criação de configurações de DSC. Os autores de configuração podem agora especificar exatamente que versão do módulo para carregar os recursos de DSC de. A nova sintaxe da palavra-chave é:

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* **Nome**: os nomes de um ou mais recursos para importar.
* **ModuleName**: os nomes de módulo ou ModuleSpecification objetos de um ou mais módulos para importar.
* **ModuleVersion**: versão de importação do módulo olocar. Se utilizados, ModuleName tem de representar apenas um módulo de por nome.

No ISE do Windows PowerShell, aparece com IntelliSense:

![](../images/Import-DscResource-Modversion.jpg)

**Tenha em atenção**: o `–ModuleVersion` parâmetro só pode ser utilizado em combinação com o `–ModuleName` parâmetro. Não pode ser utilizado com os nomes de recursos com apenas o `–Name` parâmetro.

Antes desta ação, a única forma de especificar a versão do módulo ao carregar os recursos de DSC foi, utilizando o objeto de especificação do módulo por ex.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`
