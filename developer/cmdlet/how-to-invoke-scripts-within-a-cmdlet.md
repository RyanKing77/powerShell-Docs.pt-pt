---
title: Como invocar Scripts dentro de um Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 7dcb8bc20ab56225764854f9dc6fdfd858ed7451
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055789"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>How to Invoke Scripts Within a Cmdlet (Como Invocar Scripts num Cmdlet)

Este exemplo mostra como invocar um script que é fornecido a um cmdlet. O script é executado pelo cmdlet e os resultados são devolvidos para o cmdlet como uma coleção de [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objetos.

## <a name="to-invoke-a-script-block"></a>Para invocar um bloco de scripts

1. O comando verifica que um bloco de scripts foi fornecido para o cmdlet. Se um bloco de scripts era fornecido, o comando invoca o bloco de scripts com os respetivos parâmetros necessários.

    ```csharp
    if (script != null)
    {
      WriteDebug("Executing script block.");

      // Invoke the script block with the required arguments.
      Collection<PSObject> PSObjects =
                     script.Invoke(
                                   line,
                                   simpleMatch,
                                   caseSensitive
                                  );
    ```

2. Em seguida, o script percorre a coleção retornada de [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objetos e executar as operações necessárias.

    ```c
    foreach (PSObject psObject in psObjects)
    {
      if (LanguagePrimitives.IsTrue(psObject))
      {
        result = new MatchInfo();
        result.Line = line;
        result.IgnoreCase = !caseSensitive;

        break;
      }
    }

    ```

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
