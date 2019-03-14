---
title: A carregar e exportar dados de formatação | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 86a0e8b7e8967280daa57faf5c323efcd3b1368b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794200"
---
# <a name="loading-and-exporting-formatting-data"></a>Loading and Exporting Formatting Data (Carregar e Exportar Dados de Formatação)

Assim que tiver criado o ficheiro de formatação, terá de atualizar os dados do formato da sessão com o carregamento de ficheiros para a sessão atual. (Os arquivos de formatação fornecidos pelo Windows PowerShell são carregados por snap-ins que estão registados quando é aberta a sessão atual.) Depois dos dados do formato da sessão atual são atualizados, o Windows PowerShell usa esses dados para apresentar os objetos .NET associados com as vistas definidas nos ficheiros de formatação de carregá-lo. Não existe nenhum limite para o número de arquivos de formatação que pode ser carregado para a sessão atual. Além de atualizar os dados de formatação, pode exportar os dados do formato na sessão atual para um ficheiro de formatação.

## <a name="loading-format-data"></a>Ao carregar dados de formato

Arquivos de formatação podem ser carregados para a sessão atual utilizando os seguintes métodos:

- Pode importar o ficheiro de formatação para a sessão atual da linha de comando. Utilize o [FormatData atualização](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet, conforme descrito no procedimento seguinte.

- Pode criar um manifesto de módulo que referencia o ficheiro de formatação. Módulos permitem-lhe que ficheiros para a distribuição de formatação do pacote. Utilize o [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet para criar o manifesto e o [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet para carregar o módulo na sessão atual. Para obter mais informações sobre os módulos, consulte [escrever um módulo do Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- Pode criar um snap-in que referencia o ficheiro de formatação. Utilize o [System.Management.Automation.Pssnapin.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) para referenciar os ficheiros de formatação. É vivamente recomendado que utilize módulos aos cmdlets de pacote e formatação associadas e ficheiros de tipos para distribuição. Para obter mais informações sobre os módulos, consulte [escrever um módulo do Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- Se está a invocar comandos por meio de programação, pode adicionar uma entrada de ficheiro de formatação para o estado de sessão inicial do espaço de execução em que os comandos são executados. Para obter mais informações sobre o tipo de .NET usado para adicionar o arquivo de formatação, consulte o [System.Management.Automation.Runspaces.Sessionstateformatentry? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) classe.

Quando um ficheiro de formatação é carregado, é adicionado a uma lista interna que o Windows PowerShell usa para determinar que ver a utilizar ao apresentar os objetos na linha de comandos. Pode preceder o ficheiro de formatação para o início da lista ou pode acrescentá-lo ao final da lista. É importante se estiver a carregar o ficheiro de formatação que define uma vista para um objeto que tem uma vista existente definida, por exemplo, quando quiser alterar a forma como um objeto que é devolvido por um cmdlet de núcleo do Windows PowerShell é saber onde o ficheiro de formatação é adicionado a esta lista  apresentada. Se estiver a carregar um ficheiro de formatação que define o modo de exibição apenas para um objeto, pode usar qualquer um dos métodos descritos anteriormente.  Se estiver a carregar um ficheiro de formatação que define a outra exibição para um objeto, tem de utilizar o [FormatData atualização](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet e anteceder o ficheiro para o início da lista.

## <a name="storing-your-formatting-file"></a>Armazenar o ficheiro de formatação

Não existe nenhum requisito para onde os seus arquivos de formatação são armazenados no disco. No entanto, é altamente aconselhável armazená-los na seguinte pasta: `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>A carregar um ficheiro de formato com FormatData de importação

1. Store seu arquivo de formatação para o disco.

2. Executar o [FormatData atualização](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet através de um dos seguintes comandos.

   Para adicionar a sua formatação ficheiro para a frente da lista, utilize este comando. Utilize este comando, se estiver a mudar a forma como um objeto é apresentado.

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   Para adicionar a sua formatação ficheiro para o final da lista, utilize este comando.

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   Depois de adicionar um ficheiro com o [FormatData atualização](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet, não é possível remover o ficheiro da lista enquanto a sessão está aberta. Tem de fechar a sessão para remover o arquivo de formatação a partir da lista.

## <a name="exporting-format-data"></a>Exportar dados de formato

Insira o corpo da secção aqui.
