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
#<a name="powershell-engine-improvements"></a>Melhoramentos do motor de PowerShell

Os seguintes melhoramentos para o motor de PowerShell core têm sido implementados em WMF 5.1:


## <a name="performance"></a>Desempenho ##

Desempenho melhorou em algumas áreas importantes:

- Arranque
- Pipelines para cmdlets, como ForEach-Object e Where-Object é aproximadamente 50% mais rápido 

Alguns melhoramentos de exemplo (os resultados podem variar consoante o hardware): 

| Cenário | 5.0 tempo de (ms) | 5.1 tempo (ms) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Primeiro alguma vez execução de PowerShell:`powershell -command "Unknown-Command"` | 30000 | 13000 |
| Cache de análise de comandos incorporada:`powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |
  
> Tenha em atenção, uma alteração relacionados com o arranque pode afetar alguns não suportado cenários. 
> PowerShell já não lê os ficheiros `$pshome\*.ps1xml` – estes ficheiros tem sido convertidos em c# para evitar alguns ficheiros e CPU sobrecarga de processamento XML ficheiros. 
Os ficheiros continuarão a existir para suportar V2 lado lado a lado, para que o se alterar o conteúdo do ficheiro, não terá qualquer efeito para V5, apenas V2. 
Tenha em atenção que o conteúdo desses ficheiros a alteração nunca foi um cenário suportado.

Outra alteração visível é como PowerShell coloca em cache os comandos exportados e outras informações para módulos que são instaladas num sistema. Anteriormente, esta cache foi armazenado no diretório `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`. WMF 5.1, a cache é um ficheiro único `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Consulte [módulo Analysis Cache](scenarios-features.md#module-analysis-cache) para obter mais detalhes.

