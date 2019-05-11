---
title: Como escrever um módulo de PowerShell binário | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229329"
---
# <a name="how-to-write-a-powershell-binary-module"></a>How to Write a PowerShell Binary Module (Como Escrever um Módulo Binário do PowerShell)

Um módulo binário pode ser qualquer assembly (. dll) que contém as classes de cmdlet. Por predefinição, todos os cmdlets no assembly são importados quando o módulo de binário for importado. No entanto, pode restringir os cmdlets que são importados através da criação de um manifesto de módulo módulo cuja raiz é o assembly. (Por exemplo, a chave de CmdletsToExport do manifesto pode ser usada para exportar apenas esses cmdlets que são necessários.) Além disso, um módulo binário pode conter ficheiros adicionais, uma estrutura de diretório e outras partes de informações de gerenciamento bastante úteis que não é um cmdlet único.

O procedimento seguinte descreve como criar e instalar um módulo de binário do PowerShell.

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>Como criar e instalar um módulo de binário do PowerShell

1. Criar uma solução de PowerShell binária (por exemplo, um cmdlet escrito em C#), com as capacidades necessárias e certifique-se de que é executado apropriadamente.

   Da perspectiva do código, o núcleo de um módulo de binário é simplesmente um assembly de cmdlet. Na verdade, o PowerShell irão tratar um cmdlet único assembly como um módulo, em termos de carregamento e descarregamento, sem esforço adicional por parte do desenvolvedor. Para obter mais informações sobre como escrever um cmdlet, consulte [escrever um Cmdlet do Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).

2. Se necessário, crie o resto da sua solução: (cmdlets adicionais, arquivos XML e assim por diante) e descrevê-los com um manifesto de módulo.

   Além de descrever os assemblies de cmdlet na sua solução, um manifesto de módulo possa descrever como pretende que o seu módulo exportados e importados, quais cmdlets serão expostos e o que os ficheiros adicionais irão entrar no módulo.
   Conforme indicado anteriormente no entanto, o PowerShell pode tratar um cmdlet binário, como um módulo sem esforço adicional.
   Como tal, um manifesto de módulo é útil principalmente para combinar vários arquivos num único pacote ou, para controlar explicitamente a publicação de um determinado assembly.
   Para obter mais informações, consulte [como escrever um manifesto de módulo de PowerShell](how-to-write-a-powershell-module-manifest.md).

   O código a seguir é um extremamente simples C# bloco de código que contém três cmdlets no mesmo ficheiro que pode ser utilizado como um módulo.

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. Empacotar a sua solução e guardar o pacote em algum lugar no caminho do módulo do PowerShell.

   O `PSModulePath` variável de ambiente global descreve os caminhos predefinidos que o PowerShell irá utilizar para localizar seu módulo. Por exemplo, seria um caminho comum para guardar um módulo num sistema `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`. Se não utilizar os caminhos predefinidos, terá de indicar explicitamente a localização do seu módulo durante a instalação. Certifique-se de que crie uma pasta para guardar o seu módulo, pois talvez tenha a pasta para armazenar vários assemblies e arquivos para a sua solução.

   Tenha em atenção que tecnicamente não terá de instalar o módulo em qualquer lugar no `PSModulePath` -são simplesmente as localizações predefinidas que será a aparência de seu módulo PowerShell. No entanto, é considerado uma prática recomendada para fazê-lo, a menos que tenha um bom motivo para armazenar seu módulo em algum lugar. Para obter mais informações, consulte [instalar um módulo do PowerShell](./installing-a-powershell-module.md) e [modificar o caminho de instalação do módulo de PowerShell](./modifying-the-psmodulepath-installation-path.md).

4. Importe o módulo para PowerShell com uma chamada para [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).

   Chamada para [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) carregará seu módulo na memória do Active Directory. Se estiver a utilizar o PowerShell 3.0 e mais tarde, basta chamar o nome do seu módulo no código serão também importá-lo. Para obter mais informações, consulte [importar um módulo do PowerShell](./importing-a-powershell-module.md).

## <a name="importing-snap-in-assemblies-as-modules"></a>Importar Snap-in de Assemblies como módulos

Cmdlets e provedores que existem no snap-in de assemblies podem ser carregados como módulos binários. Quando os snap-in de assemblies são carregados como módulos binários, os cmdlets e fornecedores no snap-in estão disponíveis ao usuário, mas a classe de snap-in no assembly é ignorada e o snap-in não está registado. Como resultado, os cmdlets do snap-in fornecidos pelo Windows PowerShell não é possível detetar o snap-in, apesar dos cmdlets e provedores estão disponíveis para a sessão.

Além disso, a formatação ou tipos de ficheiros que são referenciados pelo snap-in não não possível importar como parte de um módulo de binário.
Para importar os ficheiros de formatação e tipos tem de criar um manifesto de módulo.
Ver, [como escrever um manifesto de módulo do PowerShell](how-to-write-a-powershell-module-manifest.md).

## <a name="see-also"></a>Veja Também

[Escrever um módulo do Windows PowerShell](./writing-a-windows-powershell-module.md)
