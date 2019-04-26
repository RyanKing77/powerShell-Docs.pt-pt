---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5919a68c87ae8827a1b97befc653bb74713f33fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085784"
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="07d0a-102">Criar Tipos Personalizados com as Classes do PowerShell</span><span class="sxs-lookup"><span data-stu-id="07d0a-102">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="07d0a-103">Melhorámos a linguagem do PowerShell para definir as classes e outros tipos definidos pelo utilizador através da utilização de sintaxe formal e a semântica que é semelhante a outras linguagens de programação orientada a objeto.</span><span class="sxs-lookup"><span data-stu-id="07d0a-103">We’ve improved the PowerShell language for defining classes and other user-defined types by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="07d0a-104">O objetivo é permitir que desenvolvedores e profissionais de TI a adotar o PowerShell para um maior número de casos de utilização, simplificar o desenvolvimento de artefatos de PowerShell (como recursos de DSC) e acelerar a cobertura de superfícies de gestão.</span><span class="sxs-lookup"><span data-stu-id="07d0a-104">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="07d0a-105">Cenários suportados nesta versão</span><span class="sxs-lookup"><span data-stu-id="07d0a-105">Supported scenarios in this release</span></span>

-   <span data-ttu-id="07d0a-106">Definir os recursos de DSC e seus tipos associado através da linguagem do PowerShell</span><span class="sxs-lookup"><span data-stu-id="07d0a-106">Define DSC resources and their associated types by using the PowerShell language</span></span>
-   <span data-ttu-id="07d0a-107">Defina tipos personalizados no PowerShell com o familiares e orientada a objeto construções de programação, como classes, propriedades, métodos, etc.</span><span class="sxs-lookup"><span data-stu-id="07d0a-107">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
-   <span data-ttu-id="07d0a-108">Suporte de herança com a classe no PowerShell e a classe base recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="07d0a-108">Inheritance support with class in PowerShell and class base DSC resource</span></span>
-   <span data-ttu-id="07d0a-109">Tipos de depuração através da linguagem do PowerShell</span><span class="sxs-lookup"><span data-stu-id="07d0a-109">Debug types by using the PowerShell language</span></span>
-   <span data-ttu-id="07d0a-110">Gerar e manipular exceções, utilizando os mecanismos formais e no nível certo</span><span class="sxs-lookup"><span data-stu-id="07d0a-110">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>
