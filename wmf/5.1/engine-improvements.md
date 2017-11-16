---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
title: Melhoramentos de motor do PowerShell no WMF 5.1
ms.openlocfilehash: 6c8000ccfc59ab46de95dc4f67161e12a5a41199
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
#<a name="powershell-engine-improvements"></a><span data-ttu-id="85dcb-103">Melhoramentos do motor de PowerShell</span><span class="sxs-lookup"><span data-stu-id="85dcb-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="85dcb-104">Os seguintes melhoramentos para o motor de PowerShell core têm sido implementados em WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="85dcb-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>


## <a name="performance"></a><span data-ttu-id="85dcb-105">Desempenho</span><span class="sxs-lookup"><span data-stu-id="85dcb-105">Performance</span></span> ##

<span data-ttu-id="85dcb-106">Desempenho melhorou em algumas áreas importantes:</span><span class="sxs-lookup"><span data-stu-id="85dcb-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="85dcb-107">Arranque</span><span class="sxs-lookup"><span data-stu-id="85dcb-107">Startup</span></span>
- <span data-ttu-id="85dcb-108">Pipelines para cmdlets, como ForEach-Object e Where-Object é aproximadamente 50% mais rápido</span><span class="sxs-lookup"><span data-stu-id="85dcb-108">Pipelining to cmdlets like ForEach-Object and Where-Object is approximately 50% faster</span></span> 

<span data-ttu-id="85dcb-109">Alguns melhoramentos de exemplo (os resultados podem variar consoante o hardware):</span><span class="sxs-lookup"><span data-stu-id="85dcb-109">Some example improvements (your results may vary depending on your hardware):</span></span> 

| <span data-ttu-id="85dcb-110">Cenário</span><span class="sxs-lookup"><span data-stu-id="85dcb-110">Scenario</span></span> | <span data-ttu-id="85dcb-111">5.0 tempo de (ms)</span><span class="sxs-lookup"><span data-stu-id="85dcb-111">5.0 Time (ms)</span></span> | <span data-ttu-id="85dcb-112">5.1 tempo (ms)</span><span class="sxs-lookup"><span data-stu-id="85dcb-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="85dcb-113">900</span><span class="sxs-lookup"><span data-stu-id="85dcb-113">900</span></span> | <span data-ttu-id="85dcb-114">250</span><span class="sxs-lookup"><span data-stu-id="85dcb-114">250</span></span> |
| <span data-ttu-id="85dcb-115">Primeiro alguma vez execução de PowerShell:`powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="85dcb-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="85dcb-116">30000</span><span class="sxs-lookup"><span data-stu-id="85dcb-116">30000</span></span> | <span data-ttu-id="85dcb-117">13000</span><span class="sxs-lookup"><span data-stu-id="85dcb-117">13000</span></span> |
| <span data-ttu-id="85dcb-118">Cache de análise de comandos incorporada:`powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="85dcb-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="85dcb-119">7000</span><span class="sxs-lookup"><span data-stu-id="85dcb-119">7000</span></span> | <span data-ttu-id="85dcb-120">520</span><span class="sxs-lookup"><span data-stu-id="85dcb-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="85dcb-121">1400</span><span class="sxs-lookup"><span data-stu-id="85dcb-121">1400</span></span> | <span data-ttu-id="85dcb-122">750</span><span class="sxs-lookup"><span data-stu-id="85dcb-122">750</span></span> |
  
> <span data-ttu-id="85dcb-123">Tenha em atenção, uma alteração relacionados com o arranque pode afetar alguns não suportado cenários.</span><span class="sxs-lookup"><span data-stu-id="85dcb-123">Note One change related to startup might impact some unsupported scenarios.</span></span> 
> <span data-ttu-id="85dcb-124">PowerShell já não lê os ficheiros `$pshome\*.ps1xml` – estes ficheiros tem sido convertidos em c# para evitar alguns ficheiros e CPU sobrecarga de processamento XML ficheiros.</span><span class="sxs-lookup"><span data-stu-id="85dcb-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span> 
<span data-ttu-id="85dcb-125">Os ficheiros continuarão a existir para suportar V2 lado lado a lado, para que o se alterar o conteúdo do ficheiro, não terá qualquer efeito para V5, apenas V2.</span><span class="sxs-lookup"><span data-stu-id="85dcb-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span> 
<span data-ttu-id="85dcb-126">Tenha em atenção que o conteúdo desses ficheiros a alteração nunca foi um cenário suportado.</span><span class="sxs-lookup"><span data-stu-id="85dcb-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="85dcb-127">Outra alteração visível é como PowerShell coloca em cache os comandos exportados e outras informações para módulos que são instaladas num sistema.</span><span class="sxs-lookup"><span data-stu-id="85dcb-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span> <span data-ttu-id="85dcb-128">Anteriormente, esta cache foi armazenado no diretório `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span><span class="sxs-lookup"><span data-stu-id="85dcb-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span> <span data-ttu-id="85dcb-129">WMF 5.1, a cache é um ficheiro único `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="85dcb-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="85dcb-130">Consulte [módulo Analysis Cache](scenarios-features.md#module-analysis-cache) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="85dcb-130">See [Module Analysis Cache](scenarios-features.md#module-analysis-cache) for more details.</span></span>

