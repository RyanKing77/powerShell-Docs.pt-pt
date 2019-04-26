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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067880"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="07107-102">How to Invoke Scripts Within a Cmdlet (Como Invocar Scripts num Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="07107-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="07107-103">Este exemplo mostra como invocar um script que é fornecido a um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="07107-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="07107-104">O script é executado pelo cmdlet e os resultados são devolvidos para o cmdlet como uma coleção de [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objetos.</span><span class="sxs-lookup"><span data-stu-id="07107-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="07107-105">Para invocar um bloco de scripts</span><span class="sxs-lookup"><span data-stu-id="07107-105">To invoke a script block</span></span>

1. <span data-ttu-id="07107-106">O comando verifica que um bloco de scripts foi fornecido para o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="07107-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="07107-107">Se um bloco de scripts era fornecido, o comando invoca o bloco de scripts com os respetivos parâmetros necessários.</span><span class="sxs-lookup"><span data-stu-id="07107-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

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

2. <span data-ttu-id="07107-108">Em seguida, o script percorre a coleção retornada de [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objetos e executar as operações necessárias.</span><span class="sxs-lookup"><span data-stu-id="07107-108">Then, the script iterates through the returned collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="07107-109">Veja Também</span><span class="sxs-lookup"><span data-stu-id="07107-109">See Also</span></span>

[<span data-ttu-id="07107-110">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="07107-110">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
