---
title: Exemplo de GetProcessSample04 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2aa4c4-3457-4601-806a-801afe3dcc80
caps.latest.revision: 6
ms.openlocfilehash: 095bebf868efd00f8eeaec979a5606f140714cb1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068033"
---
# <a name="getprocesssample04-sample"></a>GetProcessSample04 Sample (Exemplo GetProcessSample04)

Este exemplo mostra como implementar um cmdlet que obtém os processos no computador local. Gera um erro de não terminação se ocorrer um erro ao obter um processo. Este cmdlet é uma versão simplificada do `Get-Process` cmdlet fornecido pelo Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Como criar o exemplo com o Visual Studio.

1. Windows PowerShell 2.0 SDK instalado, navegue para a pasta de GetProcessSample04. A localização predefinida é C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.

2. Faça duplo clique no ícone para o ficheiro de solução (. sln). Esta ação abre o projeto de exemplo no Visual Studio.

3. Na **crie** menu, selecione **compilar solução**.

    A biblioteca para o exemplo será criada nas pastas de \bin ou \bin\debug do padrão.

### <a name="how-to-run-the-sample"></a>Como executar o exemplo

1. Crie a seguinte pasta de módulo:

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. Copie o assembly de exemplo para a pasta de módulo.

3. Inicie o Windows PowerShell.

4. Execute o seguinte comando para carregar o assembly para o Windows PowerShell:

    `Import-module getprossessample04`

5. Execute o seguinte comando para executar o cmdlet:

    `get-proc`

## <a name="requirements"></a>Requisitos

Este exemplo requer o Windows PowerShell 2.0.

## <a name="demonstrates"></a>Demonstra

Este exemplo demonstra o seguinte.

- Declarar uma classe cmdlet usando o atributo de Cmdlet.

- Declarar um parâmetro de cmdlet usando o atributo de parâmetro.

- Especificando a posição do parâmetro.

- Especificando-se de que o parâmetro pega a entrada do pipeline. A entrada pode ser realizada a partir de um objeto ou um valor de uma propriedade de um objeto cujo nome de propriedade é o mesmo que o nome do parâmetro.

- Declarar um atributo de validação para o parâmetro de entrada.

- Interceptando um erro de não terminação e escrever uma mensagem de erro no fluxo de erro.

## <a name="example"></a>Exemplo

Este exemplo mostra como criar um cmdlet que manipula erros de não terminação e escreve mensagens de erro para a sequência de erro.

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Diagnostics;
    using System.Management.Automation;      // Windows PowerShell namespace.
   #region GetProcCommand

   /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Parameters

       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         Position = 0,
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true)]
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
      /// associated processes to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
          // If no process names are passed to cmdlet, get all
          // processes.
          if (this.processNames == null)
          {
              WriteObject(Process.GetProcesses(), true);
          }
          else
          {
              // If process names are passed to the cmdlet, get and write
              // the associated processes.
              // If a nonterminating error occurs while retrieving processes,
              // call the WriteError method to send an error record to the
              // error stream.
              foreach (string name in this.processNames)
              {
                  Process[] processes;

                  try
                  {
                      processes = Process.GetProcessesByName(name);
                  }
                  catch (InvalidOperationException ex)
                  {
                      WriteError(new ErrorRecord(
                         ex,
                         "UnableToAccessProcessByName",
                         ErrorCategory.InvalidOperation,
                         name));
                      continue;
                  }

                  WriteObject(processes, true);
              } // foreach (string name...
          } // else
      } // ProcessRecord

      #endregion Overrides
    } // End GetProcCommand class.

   #endregion GetProcCommand
}
```

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
