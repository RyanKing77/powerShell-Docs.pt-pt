---
title: Nomenclatura dos ficheiros de ajuda | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795356"
---
# <a name="naming-help-files"></a>Naming Help Files (Atribuir Nomes a Ficheiros de Ajuda)

Este tópico explica como atribuir um nome um arquivo de ajuda baseados em XML para que o [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet pode encontrá-lo. Os requisitos de nome diferem para cada tipo de comando.

## <a name="cmdlet-help-files"></a>Arquivos de ajuda do cmdlet

O ficheiro de ajuda para um C# cmdlet deve ser nomeado para o assembly no qual o cmdlet está definido. Utilize o seguinte formato de nome de ficheiro:

```
<AssemblyName>.dll-help.xml
```

O formato de nome de assemblagem é necessário, mesmo quando o assembly é um módulo aninhado.

Por exemplo, o [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet é definido no Microsoft.PowerShell.Diagnostics.dll assembly. O `Get-Help` cmdlet procura um tópico de ajuda para o `Get-WinEvent` cmdlet apenas no ficheiro Microsoft.PowerShell.Diagnostics.dll help.xml no diretório de módulo.

## <a name="provider-help-files"></a>Arquivos de ajuda do fornecedor

O ficheiro de ajuda para um fornecedor de Windows PowerShell tem de ser o nome para o assembly no qual o fornecedor é definido. Utilize o seguinte formato de nome de ficheiro:

```
<AssemblyName>.dll-help.xml
```

O formato de nome de assemblagem é necessário, mesmo quando o assembly é um módulo aninhado.

Por exemplo, o fornecedor do certificado é definido no Microsoft.PowerShell.Security.dll assembly. O `Get-Help` cmdlet vai para um tópico de ajuda para o fornecedor de certificados apenas no ficheiro Microsoft.PowerShell.Security.dll help.xml no diretório de módulo.

## <a name="function-help-files"></a>Arquivos de ajuda de função

As funções podem ser documentadas com o [ajuda baseada no comentário](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) ou documentados num arquivo de ajuda do XML. Quando a função está documentada num arquivo XML, a função tem de ter um `.ExternalHelp` comentar a palavra-chave que associa a função com o arquivo XML. Caso contrário, o `Get-Help` cmdlet não é possível localizar o ficheiro de ajuda.

Não existem não requisitos técnicos para o nome de um arquivo de ajuda de função. No entanto, uma prática recomendada é nomear o arquivo de ajuda para o módulo de script em que a função é definida. Por exemplo, a seguinte função é definida no ficheiro MyModule.psm1.

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>Arquivos de ajuda do comando CIM

O ficheiro de ajuda para um comando CIM tem de ser o nome do ficheiro de CDXML no qual o comando CIM é definido. Utilize o seguinte formato de nome de ficheiro:

```
<FileName>.cdxml-help.xml
```

Comandos CIM são definidos em ficheiros CDXML que podem ser incluídos nos módulos como módulos aninhados. Quando o comando CIM é importado para a sessão como uma função, o Windows PowerShell adiciona uma `.ExternalHelp` comentário palavra-chave para a definição de função que associa a função com uma ajuda XML do ficheiro que tem o nome do ficheiro de CDXML no qual o comando CIM é definido.

## <a name="script-workflow-help-files"></a>Arquivos de ajuda do fluxo de trabalho de script

Os fluxos de trabalho de script que estão incluídos nos módulos podem ser documentados em arquivos de ajuda baseados em XML. Não existem não requisitos técnicos para o nome de ficheiro de ajuda. No entanto, uma prática recomendada é nomear o arquivo de ajuda para o módulo de script no qual o fluxo de trabalho do script é definido. Por exemplo:

```
<ScriptModule>.psm1-help.xml
```

Ao contrário de outros comandos de script, fluxos de trabalho de script não requerem um `.ExternalHelp` comentar a palavra-chave para associá-las com um arquivo de ajuda. Em vez disso, o Windows PowerShell os subdiretórios específicos da cultura da interface do Usuário do diretório de módulo para arquivos de ajuda baseados em XML de pesquisa e procura de ajuda para o fluxo de trabalho de script em todos os ficheiros. `.ExternalHelp` Confirmar palavra-chave são ignorados.

Uma vez que o `.ExternalHelp` palavra-chave de comentário é ignorada, a `Get-Help` cmdlet pode encontrar ajuda para fluxos de trabalho de script apenas quando eles são incluídos nos módulos.