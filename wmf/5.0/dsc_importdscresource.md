---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: b839b476bb4ef7f8d73b158d61f0e8cbc1265e60
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a><span data-ttu-id="4d301-102">Palavra-chave de importação DscResource suporta o parâmetro - ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="4d301-102">Import-DscResource keyword supports -ModuleVersion parameter</span></span>

<span data-ttu-id="4d301-103">Foi adicionado um novo parâmetro para o `Import-DscResource` dinâmica palavra-chave disponível durante a criação de configurações de DSC.</span><span class="sxs-lookup"><span data-stu-id="4d301-103">We have added a new parameter to the `Import-DscResource` dynamic keyword available when authoring DSC configurations.</span></span> <span data-ttu-id="4d301-104">Os autores de configuração podem agora especificar exatamente que versão do módulo para carregar os recursos de DSC de.</span><span class="sxs-lookup"><span data-stu-id="4d301-104">Configuration authors can now specify exactly which module version to load the DSC resources from.</span></span> <span data-ttu-id="4d301-105">A nova sintaxe da palavra-chave é:</span><span class="sxs-lookup"><span data-stu-id="4d301-105">The new syntax of the keyword is:</span></span>

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* <span data-ttu-id="4d301-106">**Nome**: os nomes de um ou mais recursos para importar.</span><span class="sxs-lookup"><span data-stu-id="4d301-106">**Name**: Names of one or more resources to import.</span></span>
* <span data-ttu-id="4d301-107">**ModuleName**: os nomes de módulo ou ModuleSpecification objetos de um ou mais módulos para importar.</span><span class="sxs-lookup"><span data-stu-id="4d301-107">**ModuleName**: Module names or ModuleSpecification objects of one or more modules to import.</span></span>
* <span data-ttu-id="4d301-108">**ModuleVersion**: versão de importação do módulo olocar.</span><span class="sxs-lookup"><span data-stu-id="4d301-108">**ModuleVersion**: Version of module ot import.</span></span> <span data-ttu-id="4d301-109">Se utilizados, ModuleName tem de representar apenas um módulo de por nome.</span><span class="sxs-lookup"><span data-stu-id="4d301-109">If used, ModuleName must represent only one module by name.</span></span> 

<span data-ttu-id="4d301-110">No ISE do Windows PowerShell, aparece com IntelliSense:</span><span class="sxs-lookup"><span data-stu-id="4d301-110">In the Windows PowerShell ISE, it shows up with IntelliSense:</span></span>

![](../images/Import-DscResource-Modversion.jpg)

<span data-ttu-id="4d301-111">**Tenha em atenção**: o `–ModuleVersion` parâmetro só pode ser utilizado em combinação com o `–ModuleName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4d301-111">**Note**: the `–ModuleVersion` parameter can only be used in combination with the `–ModuleName` parameter.</span></span> <span data-ttu-id="4d301-112">Não pode ser utilizado com os nomes de recursos com apenas o `–Name` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4d301-112">It cannot be used with resource names using only the `–Name` parameter.</span></span>

<span data-ttu-id="4d301-113">Antes desta ação, a única forma de especificar a versão do módulo ao carregar os recursos de DSC foi, utilizando o objeto de especificação do módulo por ex.:`–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span><span class="sxs-lookup"><span data-stu-id="4d301-113">Before this, the only way to specify the module version when loading DSC resources was by using the Module specification object e.g.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span></span>

