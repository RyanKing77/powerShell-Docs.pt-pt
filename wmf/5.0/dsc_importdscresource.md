---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 46a278b83edb9d8e3d75b0874603710d416be3b5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085745"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a><span data-ttu-id="3b2a2-102">Palavra-chave de Import-DscResource suporta o parâmetro - ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="3b2a2-102">Import-DscResource keyword supports -ModuleVersion parameter</span></span>

<span data-ttu-id="3b2a2-103">Adicionámos um novo parâmetro para o `Import-DscResource` palavra-chave dynamic disponível durante a criação de configurações de DSC.</span><span class="sxs-lookup"><span data-stu-id="3b2a2-103">We have added a new parameter to the `Import-DscResource` dynamic keyword available when authoring DSC configurations.</span></span> <span data-ttu-id="3b2a2-104">Podem especificar exatamente qual versão do módulo para carregar os recursos de DSC de autores de configuração.</span><span class="sxs-lookup"><span data-stu-id="3b2a2-104">Configuration authors can now specify exactly which module version to load the DSC resources from.</span></span> <span data-ttu-id="3b2a2-105">A nova sintaxe da palavra-chave é:</span><span class="sxs-lookup"><span data-stu-id="3b2a2-105">The new syntax of the keyword is:</span></span>

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* <span data-ttu-id="3b2a2-106">**Nome**: Nomes de um ou mais recursos para importar.</span><span class="sxs-lookup"><span data-stu-id="3b2a2-106">**Name**: Names of one or more resources to import.</span></span>
* <span data-ttu-id="3b2a2-107">**ModuleName**: Nomes de módulos ou ModuleSpecification objetos de um ou mais módulos para importar.</span><span class="sxs-lookup"><span data-stu-id="3b2a2-107">**ModuleName**: Module names or ModuleSpecification objects of one or more modules to import.</span></span>
* <span data-ttu-id="3b2a2-108">**ModuleVersion**: Versão do módulo para importar.</span><span class="sxs-lookup"><span data-stu-id="3b2a2-108">**ModuleVersion**: Version of module to import.</span></span> <span data-ttu-id="3b2a2-109">Se for utilizado, ModuleName têm de representar apenas um módulo por nome.</span><span class="sxs-lookup"><span data-stu-id="3b2a2-109">If used, ModuleName must represent only one module by name.</span></span>

<span data-ttu-id="3b2a2-110">No ISE do Windows PowerShell, esta é apresentada com o IntelliSense:</span><span class="sxs-lookup"><span data-stu-id="3b2a2-110">In the Windows PowerShell ISE, it shows up with IntelliSense:</span></span>

![](../images/Import-DscResource-Modversion.jpg)

<span data-ttu-id="3b2a2-111">**Tenha em atenção**: a `–ModuleVersion` parâmetro só pode ser utilizado em combinação com o `–ModuleName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3b2a2-111">**Note**: the `–ModuleVersion` parameter can only be used in combination with the `–ModuleName` parameter.</span></span> <span data-ttu-id="3b2a2-112">Não pode ser utilizado com nomes de recursos utilizando apenas a `–Name` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3b2a2-112">It cannot be used with resource names using only the `–Name` parameter.</span></span>

<span data-ttu-id="3b2a2-113">Antes disto, a única forma de especificar a versão do módulo, ao carregar os recursos de DSC era usando o objeto de especificação de módulo p. ex.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span><span class="sxs-lookup"><span data-stu-id="3b2a2-113">Before this, the only way to specify the module version when loading DSC resources was by using the Module specification object e.g.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span></span>
