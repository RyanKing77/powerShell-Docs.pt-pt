---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Melhorias do mecanismo do PowerShell no WMF 5.1
ms.openlocfilehash: a0af702832c0a90c994650e25918ecacdc33fc4b
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856183"
---
# <a name="powershell-engine-improvements"></a>Melhorias do mecanismo do PowerShell

Os seguintes aprimoramentos para o motor do PowerShell core foram implementados no WMF 5.1:

## <a name="performance"></a>Desempenho

O desempenho melhorou em algumas áreas importantes:

- Arranque
- Para cmdlets, como o pipelining `ForEach-Object` e `Where-Object` aproximadamente 50% mais rápida

Alguns aperfeiçoamentos de exemplo (os resultados podem variar consoante o hardware):

| Cenário | 5.0 tempo de (ms) | 5.1 tempo (ms) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Primeiro nunca executar o PowerShell: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| Cache de análise de um comando incorporado: `powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |

> [!NOTE]
> Uma alteração relacionada à inicialização pode afetar alguns cenários não suportados. PowerShell já não lê os arquivos `$pshome\*.ps1xml` – estes ficheiros foram convertidos para C# para evitar alguns ficheiros e a sobrecarga da CPU de processar os arquivos XML. Os arquivos ainda existem para suporte V2 lado a lado, para que se alterar o conteúdo do arquivo, ele não terá qualquer efeito para V5, apenas V2. Tenha em atenção que a alteração do conteúdo desses arquivos nunca foi um cenário suportado.

Outra alteração visível é como PowerShell coloca em cache os comandos exportados e outras informações para módulos que estão instalados num sistema. Anteriormente, esta cache foi armazenado no diretório `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`. No WMF 5.1, a cache é um único arquivo `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`. Ver [Cache de análise de módulo](release-notes.md#module-analysis-cache) para obter mais detalhes.