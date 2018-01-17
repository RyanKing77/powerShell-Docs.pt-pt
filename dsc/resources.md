---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos de DSC
ms.openlocfilehash: 0994616673b5e447c69c09154bfdb9b9126a88c8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-resources"></a><span data-ttu-id="06eab-103">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="06eab-103">DSC Resources</span></span>

><span data-ttu-id="06eab-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="06eab-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="06eab-105">Pretendido que recursos de configuração de estado (DSC) fornecem os blocos modulares para uma configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="06eab-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="06eab-106">Um recurso expõe propriedades que podem ser configurada (esquema) e contém as funções de script do PowerShell que chama o Gestor de configuração Local (MMC) para "torná-lo,".</span><span class="sxs-lookup"><span data-stu-id="06eab-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="06eab-107">Um recurso pode modelo algo como genérica como um ficheiro ou uma definição de servidor IIS tão específico.</span><span class="sxs-lookup"><span data-stu-id="06eab-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="06eab-108">Grupos de como recursos são combinados para um módulo de DSC, que organiza todos os ficheiros necessários na uma estrutura que é portátil e inclui os metadados para identificar a forma como os recursos destinam-se a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="06eab-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>  

<span data-ttu-id="06eab-109">Os tópicos seguintes descrevem os recursos de DSC:</span><span class="sxs-lookup"><span data-stu-id="06eab-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="06eab-110">Recursos de DSC incorporados</span><span class="sxs-lookup"><span data-stu-id="06eab-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="06eab-111">Criar recursos de DSC personalizados</span><span class="sxs-lookup"><span data-stu-id="06eab-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="06eab-112">Recursos de DSC incorporados para Linux</span><span class="sxs-lookup"><span data-stu-id="06eab-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)

