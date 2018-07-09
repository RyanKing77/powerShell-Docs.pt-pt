---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Melhorias do mecanismo do PowerShell no WMF 5.1
ms.openlocfilehash: 738f72b910de7d44f48309013237d523d0dd40a4
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892897"
---
# <a name="powershell-engine-improvements"></a><span data-ttu-id="10ed3-103">Melhorias do mecanismo do PowerShell</span><span class="sxs-lookup"><span data-stu-id="10ed3-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="10ed3-104">Os seguintes aprimoramentos para o motor do PowerShell core foram implementados no WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="10ed3-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>

## <a name="performance"></a><span data-ttu-id="10ed3-105">Desempenho</span><span class="sxs-lookup"><span data-stu-id="10ed3-105">Performance</span></span>

<span data-ttu-id="10ed3-106">O desempenho melhorou em algumas áreas importantes:</span><span class="sxs-lookup"><span data-stu-id="10ed3-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="10ed3-107">Arranque</span><span class="sxs-lookup"><span data-stu-id="10ed3-107">Startup</span></span>
- <span data-ttu-id="10ed3-108">Para cmdlets, como o pipelining `ForEach-Object` e `Where-Object` aproximadamente 50% mais rápida</span><span class="sxs-lookup"><span data-stu-id="10ed3-108">Pipelining to cmdlets like `ForEach-Object` and `Where-Object` is approximately 50% faster</span></span>

<span data-ttu-id="10ed3-109">Alguns aperfeiçoamentos de exemplo (os resultados podem variar consoante o hardware):</span><span class="sxs-lookup"><span data-stu-id="10ed3-109">Some example improvements (your results may vary depending on your hardware):</span></span>

| <span data-ttu-id="10ed3-110">Cenário</span><span class="sxs-lookup"><span data-stu-id="10ed3-110">Scenario</span></span> | <span data-ttu-id="10ed3-111">5.0 tempo de (ms)</span><span class="sxs-lookup"><span data-stu-id="10ed3-111">5.0 Time (ms)</span></span> | <span data-ttu-id="10ed3-112">5.1 tempo (ms)</span><span class="sxs-lookup"><span data-stu-id="10ed3-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="10ed3-113">900</span><span class="sxs-lookup"><span data-stu-id="10ed3-113">900</span></span> | <span data-ttu-id="10ed3-114">250</span><span class="sxs-lookup"><span data-stu-id="10ed3-114">250</span></span> |
| <span data-ttu-id="10ed3-115">Primeiro nunca executar o PowerShell: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="10ed3-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="10ed3-116">30000</span><span class="sxs-lookup"><span data-stu-id="10ed3-116">30000</span></span> | <span data-ttu-id="10ed3-117">13000</span><span class="sxs-lookup"><span data-stu-id="10ed3-117">13000</span></span> |
| <span data-ttu-id="10ed3-118">Cache de análise de um comando incorporado: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="10ed3-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="10ed3-119">7000</span><span class="sxs-lookup"><span data-stu-id="10ed3-119">7000</span></span> | <span data-ttu-id="10ed3-120">520</span><span class="sxs-lookup"><span data-stu-id="10ed3-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="10ed3-121">1400</span><span class="sxs-lookup"><span data-stu-id="10ed3-121">1400</span></span> | <span data-ttu-id="10ed3-122">750</span><span class="sxs-lookup"><span data-stu-id="10ed3-122">750</span></span> |

> [!Note]
> <span data-ttu-id="10ed3-123">Uma alteração relacionada à inicialização pode afetar alguns cenários não suportados.</span><span class="sxs-lookup"><span data-stu-id="10ed3-123">One change related to startup might impact some unsupported scenarios.</span></span>
> <span data-ttu-id="10ed3-124">PowerShell já não lê os arquivos `$pshome\*.ps1xml` - - esses arquivos foram convertidos em c# para evitar alguns ficheiros e sobrecarga de CPU de processamento XML ficheiros.</span><span class="sxs-lookup"><span data-stu-id="10ed3-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span>
> <span data-ttu-id="10ed3-125">Os arquivos ainda existem para suporte V2 lado a lado, para que se alterar o conteúdo do arquivo, ele não terá qualquer efeito para V5, apenas V2.</span><span class="sxs-lookup"><span data-stu-id="10ed3-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span>
> <span data-ttu-id="10ed3-126">Tenha em atenção que a alteração do conteúdo desses arquivos nunca foi um cenário suportado.</span><span class="sxs-lookup"><span data-stu-id="10ed3-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="10ed3-127">Outra alteração visível é como PowerShell coloca em cache os comandos exportados e outras informações para módulos que estão instalados num sistema.</span><span class="sxs-lookup"><span data-stu-id="10ed3-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span>
<span data-ttu-id="10ed3-128">Anteriormente, esta cache foi armazenado no diretório `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span><span class="sxs-lookup"><span data-stu-id="10ed3-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span>
<span data-ttu-id="10ed3-129">No WMF 5.1, a cache é um único arquivo `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="10ed3-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="10ed3-130">Ver [Cache de análise de módulo](scenarios-features.md#module-analysis-cache) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="10ed3-130">See [Module Analysis Cache](scenarios-features.md#module-analysis-cache) for more details.</span></span>