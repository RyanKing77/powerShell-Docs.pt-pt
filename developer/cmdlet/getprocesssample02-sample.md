---
title: Exemplo de GetProcessSample02 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 481f557d-3344-4d33-b2da-4736a0165181
caps.latest.revision: 7
ms.openlocfilehash: fa4cd8a724793e71b615c84a5c5a833aa92c93fc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849512"
---
# <a name="getprocesssample02-sample"></a>GetProcessSample02 Sample (Exemplo GetProcessSample02)

Este exemplo mostra como escrever um cmdlet que obtém os processos no computador local. Ele fornece um `Name` parâmetro que pode ser utilizado para especificar os processos a serem obtidas. Este cmdlet é uma versão simplificada do `Get-Process` cmdlet fornecido pelo Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Como criar o exemplo com o Visual Studio.

1. Windows PowerShell 2.0 SDK instalado, navegue para a pasta de GetProcessSample02. A localização predefinida é C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.

2. Faça duplo clique no ícone para o ficheiro de solução (. sln). Esta ação abre o projeto de exemplo no Visual Studio.

3. Na **crie** menu, selecione **compilar solução**.

    A biblioteca para o exemplo será criada nas pastas de \bin ou \bin\debug do padrão.

### <a name="how-to-run-the-sample"></a>Como executar o exemplo

1. Crie a seguinte pasta de módulo:

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. Copie o assembly de exemplo para a pasta de módulo.

3. Inicie o Windows PowerShell.

4. Execute o seguinte comando para carregar o assembly para o Windows PowerShell:

    `import-module getprossessample02`

5. Execute o seguinte comando para executar o cmdlet:

    `get-proc`

## <a name="requirements"></a>Requisitos

Este exemplo requer o Windows PowerShell 2.0.

## <a name="demonstrates"></a>Demonstra

Este exemplo demonstra o seguinte.

- Declarar uma classe cmdlet usando o atributo de Cmdlet.

- Declarar um parâmetro de cmdlet usando o atributo de parâmetro.

- Especificando a posição do parâmetro.

- Declarar um atributo de validação para o parâmetro de entrada.

## <a name="example"></a>Exemplo

Este exemplo mostra uma implementação do cmdlet Get-Proc que inclui um `Name` parâmetro.

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;     // Windows PowerShell namespace

  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes retrieved by the cmdlet.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
    [ValidateNotNullOrEmpty]
    public string[] Name
    {
      get { return this.processNames; }
      set { this.processNames = value; }
    }

    #endregion Parameters

    #region Cmdlet Overrides

    /// <summary>
    /// The ProcessRecord method calls the Process.GetProcesses
    /// method to retrieve the processes specified by the Name
    /// parameter. Then, the WriteObject method writes the
    /// associated process objects to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames...).
    } // End ProcessRecord.
    #endregion Cmdlet Overrides
  } // End GetProcCommand class.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
