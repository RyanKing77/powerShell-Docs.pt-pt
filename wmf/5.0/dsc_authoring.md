---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 3b2c268cd10d7c421b3d1fc73a7bbeaa4714f5fc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="authoring-improvements-using-powershell-ise"></a><span data-ttu-id="3fd72-102">Melhorias na Criação com o ISE do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3fd72-102">Authoring Improvements using PowerShell ISE</span></span>

<span data-ttu-id="3fd72-103">Criação de configurações de DSC no ISE do Windows PowerShell é muito mais fácil, obrigado para os seguintes melhoramentos:</span><span class="sxs-lookup"><span data-stu-id="3fd72-103">Authoring DSC configurations in Windows PowerShell ISE is much easier, thanks to the following improvements:</span></span>

- <span data-ttu-id="3fd72-104">Listar todos os recursos de DSC dentro de um **configuração** bloco ou **nó** bloco introduzindo **Ctrl + espaço** numa linha em branco dentro da mesma.</span><span class="sxs-lookup"><span data-stu-id="3fd72-104">List all DSC resources within a **configuration** block or **node** block by entering **Ctrl+Space** on a blank line within it.</span></span>
- <span data-ttu-id="3fd72-105">A conclusão automática no recurso as propriedades do **enumeração** tipo.</span><span class="sxs-lookup"><span data-stu-id="3fd72-105">Automatic completion on resource properties that are of the **enumeration** type.</span></span>
- <span data-ttu-id="3fd72-106">A conclusão automática no **DependsOn** propriedade dos recursos de DSC, com base nas outras instâncias de recurso na configuração.</span><span class="sxs-lookup"><span data-stu-id="3fd72-106">Automatic completion on the **DependsOn** property of DSC resources, based on other resource instances in the configuration.</span></span>
- <span data-ttu-id="3fd72-107">Conclusão de separador melhor dos valores de propriedade de recurso.</span><span class="sxs-lookup"><span data-stu-id="3fd72-107">Better tab completion of resource property values.</span></span>

<span data-ttu-id="3fd72-108">**Nota:** tem de ter uma cadeia vazia para valores de propriedade de recurso antes de poder utilizar Ctrl + espaço para listar as opções.</span><span class="sxs-lookup"><span data-stu-id="3fd72-108">**Note:** You must have an empty string for resource property values before you can use Ctrl+Space to list the options.</span></span> <span data-ttu-id="3fd72-109">Premir **separador** percorre opções.</span><span class="sxs-lookup"><span data-stu-id="3fd72-109">Pressing **Tab** cycles through options.</span></span>