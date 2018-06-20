---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Criar recursos de configuração do estado pretendido do PowerShell de personalizada do Windows
ms.openlocfilehash: f1ac626c5ef18b7ed14f3754ab39139db2a2a2d7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222375"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="e533a-103">Criar recursos de configuração do estado pretendido do PowerShell de personalizada do Windows</span><span class="sxs-lookup"><span data-stu-id="e533a-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="e533a-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e533a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e533a-105">Configuração de estado pretendido do Windows PowerShell (DSC) tem recursos incorporados que pode utilizar para configurar o ambiente.</span><span class="sxs-lookup"><span data-stu-id="e533a-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="e533a-106">(Para obter mais informações, consulte [incorporada Windows PowerShell pretendido estado configuração recursos](builtInResource.md).) Este tópico fornece uma descrição geral do desenvolvimento de recursos e ligações para tópicos com informações específicas e exemplos.</span><span class="sxs-lookup"><span data-stu-id="e533a-106">(For more information, see [Built-In Windows PowerShell Desired State Configuration Resources](builtInResource.md).) This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="e533a-107">Componentes de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="e533a-107">DSC resource components</span></span>

<span data-ttu-id="e533a-108">Um recurso de DSC é um módulo do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e533a-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="e533a-109">O módulo contém o esquema (a definição das propriedades configuráveis) e a implementação (o código que suporta o trabalho real uma configuração especificado) para o recurso.</span><span class="sxs-lookup"><span data-stu-id="e533a-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="e533a-110">Um esquema de recursos de DSC pode ser definido num ficheiro MOF e a implementação é efetuada por um módulo de script.</span><span class="sxs-lookup"><span data-stu-id="e533a-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="e533a-111">A partir do suporte de classes do PowerShell na versão 5, o esquema e de implementação podem ambos ser definidos numa classe.</span><span class="sxs-lookup"><span data-stu-id="e533a-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="e533a-112">Os tópicos seguintes descrevem como criar recursos de DSC mais detalhadamente.</span><span class="sxs-lookup"><span data-stu-id="e533a-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="e533a-113">Escrever um recurso personalizado de DSC com MOF</span><span class="sxs-lookup"><span data-stu-id="e533a-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="e533a-114">Implementar um recurso de DSC em c#</span><span class="sxs-lookup"><span data-stu-id="e533a-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="e533a-115">Escrever um recurso personalizado de DSC com classes de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e533a-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* [<span data-ttu-id="e533a-116">Recursos compostos: utilizar uma configuração de DSC como um recurso</span><span class="sxs-lookup"><span data-stu-id="e533a-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
* [<span data-ttu-id="e533a-117">Utilizar a ferramenta do Designer de recursos</span><span class="sxs-lookup"><span data-stu-id="e533a-117">Using the Resource Designer tool</span></span>](authoringResourceMofDesigner.md)