---
title: Exemplo de GetProcessSample01 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b48bf80-cbf0-4cb1-8d5b-3b8d06196598
caps.latest.revision: 10
ms.openlocfilehash: 00190c7350cb0f1cfc5c389b56e48e9397480446
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068067"
---
# <a name="getprocesssample01-sample"></a>GetProcessSample01 Sample (Exemplo GetProcessSample01)

Este exemplo mostra como implementar um cmdlet que obtém os processos no computador local. Este cmdlet é uma versão simplificada do `Get-Process` cmdlet fornecido pelo Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Como criar o exemplo com o Visual Studio.

1. Windows PowerShell 2.0 SDK instalado, navegue para a pasta de GetProcessSample01. A localização predefinida é C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.

2. Faça duplo clique no ícone para o ficheiro de solução (. sln). Esta ação abre o projeto de exemplo no Microsoft Visual Studio.

3. Na **crie** menu, selecione **compilar solução**.

  A biblioteca para o exemplo será criada nas pastas de \bin ou \bin\debug do padrão.

### <a name="how-to-run-the-sample"></a>Como executar o exemplo

1. Abra uma janela da Linha de Comandos.

2. Navegue para o diretório que contém o ficheiro. dll de exemplo.

3. Execute installutil "GetProcessSample01.dll".

4. Inicie o Windows PowerShell.

5. Execute o seguinte comando para adicionar o snap-in para o shell.

   `Add-PSSnapin GetProcPSSnapIn01`

6. Introduza o seguinte comando para executar o cmdlet. `get-proc`

   `get-proc`

   Esta é uma saída de exemplo que resulta da seguindo estes passos.

   ```output
   Id              Name            State      HasMoreData     Location             Command
   --              ----            -----      -----------     --------             -------
   1               26932870-d3b... NotStarted False                                 Write-Host "A f...

   ```

   ```powershell
   Set-Content $env:temp\test.txt "This is a test file"
   ```

   ```output
   A file was created in the TEMP directory
   ```

## <a name="requirements"></a>Requisitos

Este exemplo requer o Windows PowerShell 1.0 ou posterior.

## <a name="demonstrates"></a>Demonstra

Este exemplo demonstra o seguinte.

- A criação de um cmdlet de exemplo básico.

- Definir uma classe de cmdlet, utilizando o atributo de Cmdlet.

- Criação de um snap-in que funciona com o Windows PowerShell 1.0 e o Windows PowerShell 2.0. Exemplos de subsequentes utilizam módulos em vez de snap-ins para que eles necessitam do Windows PowerShell 2.0.

## <a name="example"></a>Exemplo

Este exemplo mostra como criar um cmdlet simples e seu snap-in.

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{

   #region GetProcCommand

   /// <summary>
   /// This class implements the Get-Proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes of the local computer.
      /// Then, the WriteObject method writes the associated processes
      /// to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         // Retrieve the current processes.
         Process[] processes = Process.GetProcesses();

         // Write the processes to the pipeline to make them available
         // to the next cmdlet. The second argument (true) tells Windows
         // PowerShell to enumerate the array and to send one process
         // object at a time to the pipeline.
         WriteObject(processes, true);
      }

      #endregion Overrides

   } //GetProcCommand

   #endregion GetProcCommand

   #region PowerShell snap-in

   /// <summary>
   /// Create this sample as an PowerShell snap-in
   /// </summary>
   [RunInstaller(true)]
   public class GetProcPSSnapIn01 : PSSnapIn
   {
       /// <summary>
       /// Create an instance of the GetProcPSSnapIn01
       /// </summary>
       public GetProcPSSnapIn01()
           : base()
       {
       }

       /// <summary>
       /// Get a name for this PowerShell snap-in. This name will be used in registering
       /// this PowerShell snap-in.
       /// </summary>
       public override string Name
       {
           get
           {
               return "GetProcPSSnapIn01";
           }
       }

       /// <summary>
       /// Vendor information for this PowerShell snap-in.
       /// </summary>
       public override string Vendor
       {
           get
           {
               return "Microsoft";
           }
       }

       /// <summary>
       /// Gets resource information for vendor. This is a string of format:
       /// resourceBaseName,resourceName.
       /// </summary>
       public override string VendorResource
       {
           get
           {
               return "GetProcPSSnapIn01,Microsoft";
           }
       }

       /// <summary>
       /// Description of this PowerShell snap-in.
       /// </summary>
       public override string Description
       {
           get
           {
               return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
           }
       }
   }

   #endregion PowerShell snap-in
}
```

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)