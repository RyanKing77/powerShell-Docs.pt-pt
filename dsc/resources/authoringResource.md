---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Criar recursos do Windows personalizados do PowerShell Desired State Configuration
ms.openlocfilehash: 882b6efed4564d2354183d7472b301e1e1758335
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684592"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="3c72d-103">Criar recursos do Windows personalizados do PowerShell Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="3c72d-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="3c72d-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3c72d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="3c72d-105">Windows PowerShell Desired State Configuration (DSC) tem recursos incorporados que pode utilizar para configurar o ambiente.</span><span class="sxs-lookup"><span data-stu-id="3c72d-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="3c72d-106">Este tópico fornece uma visão geral do desenvolvimento de recursos e ligações para tópicos com informações específicas e exemplos.</span><span class="sxs-lookup"><span data-stu-id="3c72d-106">This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="3c72d-107">Componentes de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="3c72d-107">DSC resource components</span></span>

<span data-ttu-id="3c72d-108">Um recurso de DSC é um módulo do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3c72d-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="3c72d-109">O módulo contém o esquema (a definição das propriedades configuráveis) e a implementação (o código que faz o trabalho real de uma configuração especificado) para o recurso.</span><span class="sxs-lookup"><span data-stu-id="3c72d-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="3c72d-110">Um esquema de recursos de DSC pode ser definido num ficheiro MOF e a implementação é executada por um módulo de script.</span><span class="sxs-lookup"><span data-stu-id="3c72d-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="3c72d-111">A partir do suporte de classes do PowerShell na versão 5, o esquema e de implementação podem ser definidas numa classe.</span><span class="sxs-lookup"><span data-stu-id="3c72d-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="3c72d-112">Os tópicos seguintes descrevem mais pormenorizadamente como criar recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="3c72d-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="3c72d-113">Escrever um recurso personalizado do DSC com o MOF</span><span class="sxs-lookup"><span data-stu-id="3c72d-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="3c72d-114">Implementar um recurso de DSCC#</span><span class="sxs-lookup"><span data-stu-id="3c72d-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="3c72d-115">Escrever um recurso personalizado do DSC com classes do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c72d-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* [<span data-ttu-id="3c72d-116">Recursos compostos: Utilizar uma configuração de DSC como um recurso</span><span class="sxs-lookup"><span data-stu-id="3c72d-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
* [<span data-ttu-id="3c72d-117">Usando a ferramenta de Designer de recursos</span><span class="sxs-lookup"><span data-stu-id="3c72d-117">Using the Resource Designer tool</span></span>](../authoringResourceMofDesigner.md)
